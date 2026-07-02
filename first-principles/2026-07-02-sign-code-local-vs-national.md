# First-Principles Spike — 2026-07-02

## Question

Why is sign permitting/zoning regulated locally (city/county ordinance) instead
of by a single national code, and what specifically makes a municipal sign
ordinance legally fragile?

Generated fresh (backlog file was missing/empty) as a question relevant to
Brand 9 Signs operations — every install requires a local permit, and permit
friction/legal risk is a recurring line item in sign-company ops.

## Step 2 — First-principles derivation (no retrieval)

**Primitives:**
- A sign is a physical structure conveying information, sited in or visible
  from public space.
- In the US, land-use authority is a "police power" (regulate for health,
  safety, morals, general welfare), reserved to the states by the 10th
  Amendment and delegated downward to municipalities by state enabling acts.
- Some physical hazards are universal (a live 120V wire shocks the same
  person in Ohio or Texas), so those get standardized in national model codes
  (NEC, IBC) that are then locally adopted/enforced. Other hazards/harms are
  context-dependent and don't generalize.
- A sign is also *expression* — it carries a message, which puts it under
  First Amendment scrutiny whenever government treats different messages
  differently.

**Reasoning chain:**

1. Ask what "harm" a sign ordinance is trying to prevent: traffic distraction,
   obstructed sightlines, visual clutter, degraded property values/community
   character. None of these are physics constants — a 40-ft pole sign is
   normal on a highway commercial strip and considered blight in a historic
   downtown two miles away. The harm function is a function of *local built
   environment*, not of the sign itself.
2. Compare to electrical/structural hazards, which *are* physics constants —
   a shock hazard or a wind-load failure mode doesn't care what town it's in.
   That's why those get one national reference code (NEC/IBC) that
   municipalities adopt wholesale, while the "how big, how bright, how many,
   where" questions stay local.
3. This is a subsidiarity/Tiebout-style argument: decision authority should
   sit at the smallest jurisdiction that fully internalizes the externality.
   A sign's visual/traffic impact doesn't cross municipal boundaries, so
   there's no efficiency case for centralizing the decision — and a real cost
   to centralizing it, since one national standard can't encode "acceptable
   here, not acceptable there."
4. Given that, sign law's actual job splits into two categories of rule:
   (a) content-neutral physical attributes — size, height, setback,
   illumination, spacing, structural safety — which map cleanly onto the
   "local, context-dependent harm" logic above and are safe to regulate;
   (b) rules that differentiate by *what the sign says* — e.g., different
   size/duration/permit rules for "political," "temporary event," "real
   estate," "ideological" signs.
5. Category (b) is where ordinances get legally fragile, and the mechanism is
   structural, not incidental: humans naturally write rules by *topic*
   ("political signs get X, real-estate signs get Y") because that's how we
   organize categories in language. But the moment enforcement requires an
   official to read a sign's message to know which size/duration rule
   applies, the rule is a restriction on speech that varies by content. Under
   First Amendment doctrine, content-based speech restrictions get the
   strictest level of judicial review, and almost nothing survives it because
   the government can essentially never show that reading the sign's subject
   matter was *necessary* to protect traffic safety or aesthetics — those
   interests are fully served by content-neutral limits on size/height/etc.
   alone.
6. So the prediction from first principles: (a) local control is structurally
   correct given how localized the externality is, and (b) most sign-code
   litigation losses will trace back to ordinances that unintentionally
   sorted signs by topic rather than by neutral physical attributes — because
   that's the natural (and legally naive) way to draft rules, not because
   towns intended to suppress speech.

## Step 3/4 — Corpus check and delta

Searched: *Reed v. Town of Gilbert* (576 U.S. 155, 2015) and general zoning/
police-power sourcing.

- **Confirmed directly:** Reed v. Town of Gilbert is exactly the doctrine
  predicted in step 5/6. The Court held Gilbert's sign code was
  "content-based on its face" because rules (size, duration, placement)
  depended entirely on the sign's message category (ideological vs. political
  vs. "temporary directional" for a church event), triggering strict
  scrutiny. The Town's stated interests — aesthetics and traffic safety —
  were assumed compelling but the rules weren't narrowly tailored, so the
  ordinance fell. Thomas's opinion explicitly notes content-based rules can
  survive if narrowly tailored to safety (e.g., hazard warning signs, traffic
  signs) — matching the physical/content-neutral vs. topical split derived
  above.
- **Confirmed directly:** zoning authority (including sign codes) is
  standard textbook police power — reserved to states, delegated to
  municipalities by enabling acts, justified as a "nuisance-preventing
  device," exercised locally because "each community has the right to
  determine its own character." No corpus source frames this in Tiebout/
  subsidiarity/harm-locality terms explicitly — that's economic vocabulary
  laid on top of the legal doctrine, not something planning-law sources
  state directly.

**Delta category: rediscovered**, with one **novel** framing on top.

The core mechanism (content-neutral survives, content-based triggers strict
scrutiny and usually dies; sign law is local because land-use police power is
local) was arrived at independently and matches the corpus exactly, down to
predicting *why* ordinances fail before knowing the case name. The
subsidiarity/"harm doesn't generalize across geography, unlike electrical
shock" framing for *why physical zoning is local but electrical code is
national* is not language the corpus sources use — planning-law literature
states the local/state delegation fact but doesn't explain it by contrasting
it against nationally-standardized physical hazard codes. That contrast is a
genuinely useful operating lens for Brand 9 Signs: it predicts which parts of
a new market's sign code are worth negotiating (the local, topic-based
distinctions) versus which are non-negotiable regardless of jurisdiction (UL/
NEC electrical and structural wind-load requirements).

## Commentary

Practical takeaway for ops: when a permit reviewer differentiates fee, size,
or duration by *what kind of sign it is* rather than its physical footprint,
that's the exact fact pattern *Reed* invalidates — worth flagging as a
possible variance/appeal angle rather than treating the ordinance as
immutable. When the friction is about brightness, height, or structural
spec, that's the content-neutral, physics-grounded category, and it's not
worth fighting.
