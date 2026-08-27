# First-Principles Spike — 2026-08-27

## Question

In illuminated channel-letter and cabinet signage, why has the industry
standardized on wiring LED light-engine modules in **parallel** off a
constant-voltage DC rail (12V/24V), rather than wiring them in **series**?
What do circuit theory, failure-mode reasoning, and manufacturing economics
predict from first principles — and does the real design match?

Picked by self-generation: `first-principles-backlog.md` was empty on first
run, so this question was chosen as relevant to current Construct work
(Brand 9 Signs is a sign fabricator; this is load-bearing operational
knowledge, not trivia).

## First-principles answer (derived before any search)

**Primitives on the table:** an LED is a diode — nonlinear V/I relationship,
characterized by a forward voltage Vf (roughly 3.0–3.4V for a white
sign-grade LED) rather than a fixed resistance. Two ways to combine N of
them: series (same current through every element, voltages add — KVL) or
parallel (same voltage across every branch, currents add — KCL).

**1. Voltage budget forces the topology, before "preference" even enters.**
Sign wiring is built on low-voltage Class 2 DC rails (12V or 24V), chosen
for a reason upstream of LEDs entirely: low-voltage wiring inside a metal
channel-letter can, handled by installers and technicians in the field,
avoids the shock/fire/code burden of line-voltage wiring in that
environment. Given a 24V rail and Vf≈3.2V, a single series string tops out
around 6-7 modules before you run out of headroom. Real channel letters and
cabinets need anywhere from a handful to dozens of LEDs. So even if series
wiring were otherwise preferable, the voltage budget forces the design into
multiple *parallel groups* of short series strings, or straight parallel of
individually-limited modules — series-only doesn't scale to sign sizes at
low voltage. This is the primary, non-negotiable constraint.

**2. Failure-mode reasoning favors parallel independent of the voltage
constraint.** In series, KCL guarantees identical current through every
element in the loop — if one module fails open (a real, common outdoor
failure mode: bond-wire fatigue, moisture ingress, thermal cycling over a
5-10 year outdoor service life), the entire string goes dark, not just that
module. A single point failure blacks out an entire row or segment — highly
visible, brand-damaging, and expensive to service (emergency truck-roll vs.
scheduled maintenance). In parallel, a failed module drops out of its own
branch only; the rest of the sign stays lit. Given module failure over a
long outdoor lifespan is a near-certainty for *some* fraction of units
across a large installed base, a topology that isolates single failures to
single dark points is strictly better for both the client's brand exposure
and the fabricator's warranty/service economics.

**3. Manufacturing/SKU economics reinforce it.** If topology were
series-based, string length (module count) would need to be pre-calculated
per sign size to hit the voltage budget exactly — every job needs a custom
string count, complicating inventory and installation. A parallel topology
off a fixed-voltage rail lets a single standardized module SKU be strung to
any length simply by adding more parallel branches — cut-to-length modules
on a reel, wired however many are needed, fed by the same 12V/24V driver
regardless of sign size. This is a big win for a manufacturer selling
modules across thousands of different sign jobs.

**4. Prediction this forces about internal module design.** Parallel
branches off a shared constant-voltage rail expose LED nonlinearity: small
manufacturing variance in Vf between branches means a slightly-lower-Vf
branch would try to hog disproportionate current (steep V/I curve near
Vf), risking thermal runaway in that branch. So each module *must* carry
its own current-limiting element (resistor or equivalent) so it can safely
share a voltage rail with other modules without hand-matching or balancing.
This should show up in real module designs as a design necessity, not an
optional extra.

**Predicted answer, before searching:** modules are wired in parallel off
a constant-voltage 12V/24V DC rail, each carrying its own current-limiting
element, specifically because (a) the safe low-voltage rail can't fit
enough series-strung LEDs to span real sign sizes, (b) parallel isolates
single-module failure to a single dark point instead of a dead string, and
(c) it lets one module SKU serve any sign size just by adding branches.

## Corpus / orthodox answer (searched after the above was written)

Confirmed directly:

- Constant-voltage (12V/24V) LED drivers are the sign-industry standard
  specifically *because* they only support parallel-connected loads — "LED
  modules with constant voltage can only be connected in parallel."
  ([LEDYi, "A Complete Guide to LED Drivers"](https://www.ledyilighting.com/a-complete-guide-to-led-drivers/))
- The failure-isolation reasoning is named explicitly as the "single point
  of failure" property of parallel wiring, and the standard industry
  mitigation for large installs is to split into multiple circuits with
  independent feeds so no single failure (or maintenance event) takes down
  the whole run. ([LED Signboard Power Supply Guide](https://electronics.alibaba.com/buyingguides/led-signboard-power-supply-guide-how-to-choose-right))
- Real sign LED module patents describe exactly the predicted per-module
  current-limiting element — though the specific circuit is more refined
  than a plain resistor: production designs use a **shunt (often Zener)
  voltage-limiting element plus a series current-limiting resistor per
  module**, which additionally protects against over-voltage transients
  on the shared rail, not just current-sharing. ([US Patent 8,305,717 —
  "LED Modules for Sign Channel Letters and Driving Circuit"](https://patents.justia.com/patent/8305717))
- One nuance not fully derived above: **24V is preferred over 12V** in
  practice mainly to cut resistive (I²R) losses and copper cost in the
  wiring harness — at fixed power, doubling the rail voltage halves the
  current, which cuts voltage-drop and heating in the feed wires for long
  runs / large cabinets. I gestured at "voltage budget" but didn't
  explicitly reason through the copper-cost/current tradeoff that pushes
  larger jobs toward 24V (and even 48V) over 12V.

## Delta category: **rediscovered**

The core answer — parallel topology forced by a safety-driven low-voltage
rail, chosen further for failure isolation and single-SKU manufacturing
economics — was derived independently from circuit theory (KVL/KCL),
outdoor-reliability reasoning, and supply-chain economics, and matches the
corpus's stated rationale point-for-point, including the specific
"single point of failure" framing.

One real gap: the corpus's reason for preferring 24V over 12V (I²R/copper
economics at fixed power) wasn't in my derived answer — I had the
qualitative direction (voltage headroom) but not the quantitative reason
higher voltage rails are chosen at scale. Not a corpus error, just an
incompleteness in my first pass. Also useful: production current-limiting
is a shunt+resistor pair (over-voltage protection), a level of detail my
reasoning arrived at only qualitatively ("some current-limiting element"),
which is exactly what "reasoning derives the *shape* of a mechanism, search
fills in the specific engineering that has already been optimized" looks
like in practice.

## Commentary

This is close to the ideal outcome for the spike: independent derivation
gets the *structure* of the standard answer right (forced topology from a
safety constraint, reinforced by failure-mode and economic reasoning) but
under-specifies the *quantitative* tradeoff (why 24V over 12V) and the
*implementation* detail (Zener shunt vs plain resistor) that only shows up
once you look at what's actually been built and iterated on in the field.
Reasoning from primitives is good at finding *why a constraint exists*;
search is good at finding *which of several ways to satisfy it, someone
has already tried and kept*.
