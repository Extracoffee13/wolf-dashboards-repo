# First-Principles Spike — 2026-08-20

## Question

**Where does a drawdown circuit breaker belong in an autonomous trading agent, and what
sets its threshold — derived from primitives rather than from convention?**

Chosen because WOLF is running one live in this repo (daily gate 3%, weekly gate 7%) and
no one in the Construct has ever derived those numbers — they were chosen, not computed.

---

## Part 1 — First-principles answer (no retrieval)

### Primitives assumed

1. The agent trades capital. Equity follows a path `E(t)`.
2. There is an absorbing barrier. Below it the agent cannot continue — either
   mathematically (capital gone) or practically (the operator loses nerve and shuts it
   off). The practical barrier is *higher* and is therefore the binding one.
3. Any strategy with positive expectancy still has variance. Over enough draws, a losing
   run of any finite length occurs with probability approaching 1.
4. Losses have exactly two causes: **(a)** ordinary variance of an edge that is still
   valid, or **(b)** the edge is dead, inverted, or the agent is broken (stale data, bug,
   regime shift).
5. At the moment of loss, (a) and (b) are indistinguishable from the P&L alone.

### Step 1 — The breaker is not a detector

Primitive 5 is the whole game. A circuit breaker cannot tell you *why* you are losing, so
it cannot be designed as a regime-change detector. Its only honest job is to **bound the
cost of being wrong about which case you're in.** That reframe determines everything
downstream.

### Step 2 — A statistically justified threshold is provably useless

Suppose we demanded the breaker fire only once losses were significant evidence the edge
was gone. Distinguishing "no edge" from "small edge" requires a sample on the order of
`(σ/μ)²` trades — hundreds to thousands. By the time that evidence exists, the capital is
already gone.

**Therefore the breaker must fire long before there is evidence to justify firing.** The
overwhelming majority of firings will be false positives *by design*. That is the
specification, not a defect. Raising the threshold to "reduce false alarms" destroys the
instrument.

### Step 3 — The level is set by a cost balance, not a p-value

Two opposing costs:

- **Firing too early** costs forgone expectancy: the positive-EV trades not taken during
  the halt, roughly `edge_per_unit_time × halt_duration × firing_frequency`. Firing
  frequency climbs steeply as the threshold descends toward ordinary daily noise — mild
  until ~1σ, then explosive.
- **Firing too late** costs recovery convexity. Recovering a drawdown `d` requires a gain
  of `d/(1-d)`: 5% → 5.3%, 10% → 11.1%, 20% → 25%, 50% → 100%. Near-linear while small,
  explosive past ~20%. And what's lost isn't just capital — it's all future compounding
  on that capital.

The crossing point sits **just above the noise band of ordinary daily variation**:
`threshold ≈ k·σ_daily`, `k ≈ 2–3`. Not 1 (fires on noise), not 10 (never fires in time).

### Step 4 — A second, independent derivation lands in the same place

Forget variance. Ask what preserves the ability to keep playing. Let `D_max` be the total
drawdown past which the *practical* barrier trips — the operator kills the system. Human
behavior in any capital-allocation setting puts that near 20%; past it, confidence is gone
regardless of the math. Demand that a genuinely bad run be survivable for `N = 10`
consecutive breaker-hit days. Then:

```
threshold ≤ D_max / N = 20% / 10 = 2% per day
```

Two derivations from unrelated starting points — one from variance structure, one from
operator tolerance — converge on ~2%/day. The convergence is itself the evidence: it
suggests the number is a property of the problem, not of either model.

### Step 5 — One breaker is structurally insufficient

A single daily gate is defeated by a slow bleed: ten days at −1.9% against a −2% limit
never fires and still costs 17.4%. The breaker must be a **hierarchy across timescales**
(daily / weekly / monthly), and the limits must be **sublinear** in time — for roughly
independent returns the dispersion of an n-day sum scales as `√n`, not `n`. A
variance-neutral weekly limit is therefore `√5 ≈ 2.24×` the daily limit, *not* `5×`. Any
hierarchy scaling limits linearly with time has a weekly gate that is dead weight: it can
never bind before the daily one does.

### Step 6 — The reset rule matters more than the threshold

The default implementation is "halt, resume tomorrow." But by primitive 4, if the true
cause was **(b)**, tomorrow it fires again. And the day after. **A time-based re-arm
converts a circuit breaker into a slow leak metered at exactly the threshold rate.** It
has not bounded the loss; it has only *scheduled* it.

The re-arm must be asymmetric with the trip. Tripping: automatic, fast, evidence-free
(Step 2). Re-arming: must require something that is *not* the passage of time — an
operator review, a positive out-of-sample signal, a fresh paper-validation run. Time is
the one re-arm condition carrying zero information about whether you are in (a) or (b),
which makes it precisely the condition you must not use.

### Step 7 — Firing frequency is a sizing alarm, not a risk event

Position sizing and the circuit breaker are the same instrument at different frequencies;
both cap loss per unit time. If sizing is right, the breaker is a rare tail event. A
breaker firing weekly isn't working well — it is **reporting that positions are too
large.** Trip frequency should feed back into the sizing rule. A system that trips
constantly and counts each trip as a save is misreading a chronic condition as a series of
emergencies.

### Step 8 — Measure against the right denominator

Dollars are wrong (no de-risking as capital shrinks). Percent of **current equity**
auto-de-risks as you lose (good, anti-martingale) but permits unbounded slow bleed, since
each new lower equity resets the allowance. Percent of **high-water mark** is the only one
bounding what's actually at stake: recovery convexity and operator confidence. So:
current-equity for the fast daily gate, high-water-mark for the master kill.

### Derived design

- Threshold ≈ 2–3× daily σ ≈ **2% of equity** — deliberately inside the noise band.
- Hierarchical gates scaling as `√t`, not `t` (weekly ≈ 2.2× daily).
- Daily gate on current equity; master kill on high-water mark.
- Automatic trip, **non-time-based re-arm**.
- Trip frequency monitored as a position-sizing feedback signal.

---

## Part 2 — Corpus answer (after retrieval)

- **Numbers.** Orthodoxy is 1–2% risk per trade, **3–5% daily loss limits**, ~10% max
  drawdown, and professionals targeting max DD below **20%**. My 2%/day and 20% `D_max`
  land inside the standard band.
- **The tuning tradeoff** is stated explicitly: limits set too tightly "produce false
  alarms during normal noise," too loosely "fail during real stress." Same tradeoff as my
  Step 3 — but the corpus treats false alarms as a cost to *minimize*, never as the
  design intent.
- **Recovery convexity** (`d/(1-d)`) is textbook.
- **Hierarchical limits** (daily / weekly / monthly / overall) are standard practice.
- **√T scaling** exists in the corpus — but as **VaR horizon scaling** (`VaR_T = VaR_1·√T`),
  a separate discipline from loss-limit setting. I found no source applying it to fix the
  *ratio between a daily and a weekly loss limit*.
- **Re-arm.** Practice largely matches my conclusion: kill switches "lock the account for
  the remainder of the trading day" and many "block new entries until manual reset." But
  the stated rationale is a **behavioral cool-down for a human trader**, not an
  information requirement for an autonomous agent.
- **Trip frequency as a sizing alarm** is explicitly orthodox: trigger frequency "is a
  strong indicator that your position sizing may be too aggressive," and "most prop firm
  challenge failures are position sizing failures, not strategy failures." Step 7 is
  fully rediscovered.
- **Denominator.** Static vs. trailing high-water-mark drawdown is a well-developed
  corpus distinction; daily gates run on balance/equity while the max gate trails the
  HWM. Step 8 is rediscovered.
- **A genuine contradiction.** The prop-firm industry is *moving away* from daily loss
  limits toward a single trailing/static max drawdown (Apex removed DLL on most products
  post-March 2026; TPT removed it across all phases in January 2025). That cuts against
  my Step 5.
- **A confirmed gap.** A targeted search for the critique that a daily loss limit merely
  spreads a losing strategy's losses across days returned nothing addressing it.

---

## Part 3 — Delta

**Category: `novel`** — novel *framing* over largely *rediscovered* substance.

Six of eight steps were rediscovered, several of them exactly: the threshold band, the
20% practical barrier, recovery convexity, hierarchical gates, trip-frequency-as-sizing-
alarm, and the equity-vs-high-water-mark denominator split. Two derivations converging on
2%/day landed precisely on industry convention from a standing start. That is a strong
validation of the reasoning.

What the corpus does not appear to have is the load-bearing frame:

1. **The breaker is a bound on the cost of being wrong, not a detector** — and therefore
   **false positives are the specification, not a defect.** The corpus consistently
   frames false alarms as a tuning cost to be reduced. If false positives are the point,
   the entire "how do I stop my breaker firing so often?" genre is asking the wrong
   question — and Step 7 says the right answer isn't the threshold anyway, it's sizing.
2. **Time-based re-arm meters a leak rather than stopping one.** Practice converges on
   manual reset, but for the *behavioral* reason (cool the human down). For an autonomous
   agent there is no human to cool down, so the behavioral rationale doesn't transfer —
   and if you'd adopted it *only* for that reason you would rationally drop it when
   automating. The information-theoretic reason (time carries zero evidence about
   which failure mode you're in) survives automation intact. Same practice, different
   justification, opposite implication for agent design.
3. **`√t` as the rule fixing the ratio between nested loss limits.** Both halves are
   orthodox in isolation (VaR horizon scaling; hierarchical limits) and I found no source
   joining them.

On the contradiction: the prop-firm retreat from daily loss limits is a commercial move
in a competitive marketing environment, not a risk-theoretic finding. Prop-firm DLLs
exist to cap the *firm's* liability and filter trader behavior — a different objective
from protecting a strategy's compounding. I'm not treating it as refuting Step 5, but it
is the strongest disconfirming evidence found and shouldn't be papered over.

### Actionable finding for WOLF

The live config in `wolf_live_data.json` is **daily 3.0%, weekly 7.0%** — a ratio of
**2.33** against the variance-neutral **√5 ≈ 2.24**. That hierarchy is very nearly
correct already, which was not expected. Two open items:

- The daily gate at 3% sits at the loose end of the derived 2–3% band.
- **The re-arm rule is unverified.** If WOLF re-arms on a calendar rollover, Step 6 says
  the breaker is metering a leak at 3%/day rather than stopping one — the single
  highest-leverage thing to check in the risk stack. Worth an explicit look.

### Commentary

The most useful output here wasn't a number — the numbers were all rediscovered, which is
mostly a check that the reasoning isn't broken. It was noticing that a practice can be
right in the corpus for a reason that **doesn't survive the jump from human trader to
autonomous agent**. Retrieval gives you the practice. Only derivation tells you which
parts of the justification still hold once the context changes — and therefore which
parts you're allowed to drop when you automate.

**Confidence: 0.65.** Four searches failing to surface a framing is weak evidence the
corpus lacks it; the quant risk-management literature is deep and much of it is
proprietary. The `novel` call is on framing only — the substance is honestly
`rediscovered`.

### Sources

- [Reducing Drawdown: 7 Risk-Management Techniques for Algo Traders — Tradetron](https://tradetron.tech/blog/reducing-drawdown-7-risk-management-techniques-for-algo-traders)
- [Understanding Risk of Ruin for Traders — JournalPlus](https://journalplus.co/learn/guides/risk-of-ruin-guide/)
- [Prop Firm Drawdown Rules Explained: Daily vs Max — ThinkCapital](https://www.thinkcapital.com/prop-firm-drawdown-rules/)
- [Prop Firm Drawdown Rules Explained: Daily, Max and Trailing Limits in 2026 — The5ers](https://the5ers.com/prop-firm-drawdown-rules-explained-daily-max-and-trailing-limits-in-2026/)
- [Daily Loss Limits — CrossTrade](https://crosstrade.io/learn/risk-management/daily-loss-limits)
- [Trading Kill Switch: Why You Need One — KillSwitch](https://killswitch.in/blog/trading-kill-switch)
- [Value at Risk (VaR): Formula, Methods & Examples — Ryan O'Connell, CFA](https://ryanoconnellfinance.com/value-at-risk/)
- [V-Lab: Long-Run Value-at-Risk Analysis Documentation — NYU Stern](https://vlab.stern.nyu.edu/docs/lrrisk)
- [Daily Loss Limits Explained — MyFundedFutures](https://myfundedfutures.com/blog/daily-loss-limits-explained-protect-your-account-and-sanity)
- [Position Size Calculator: How to Size Every Trade Correctly (2026) — TradeZella](https://www.tradezella.com/blog/position-size-calculator)
