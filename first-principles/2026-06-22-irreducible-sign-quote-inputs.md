# Spike: What is the irreducible information set required to generate a sign quote without human intervention?

**Date:** 2026-06-22
**Category:** novel
**Confidence:** 0.78

---

## The Question

Automating sign quoting is a core Construct goal for Brand 9 Signs. Before building
a quote engine, you need to know: what is the *minimum* set of facts a customer must
supply before a price can be computed without any human in the loop?

---

## Step 2 — First-Principles Derivation

### Start at the object

A sign is a physical object that communicates information. To produce one you need:
material (what it's made of), a production process (how it's made), a substrate or
structure (what it mounts to), and sometimes an installer (who puts it up). Each of
these has a cost function. Price = Σ(cost functions) × markup.

### Decompose each cost function

| Cost line | Driven by |
|---|---|
| Material | Type × area (sq ft) |
| Ink/vinyl | Type × coverage area |
| Production labor | Method × complexity × time |
| Hardware | Mount type × quantity |
| Installation labor | Install type × site conditions × height |
| Permitting | Jurisdiction × sign class |
| Rush premium | Turnaround relative to shop capacity |

### Identify which drivers are *independent variables* (inputs) vs. derivable

- **Area** — must be supplied (W × H). Cannot be defaulted without a range that
  makes the quote meaningless.
- **Sign type** — must be supplied. Encodes material + production method together.
  e.g. "cut vinyl on aluminum dibond" vs. "channel letters with LED returns."
- **Quantity** — must be supplied. Unit economics change nonlinearly with runs.
- **Install type** — can be defaulted to "none / pickup" with a stated assumption,
  but a bundled quote requires it.
- **Jurisdiction** — can be defaulted to "no permit included" with a stated
  assumption.
- **Turnaround** — can be defaulted to "standard lead time."

### The hard minimum

The strictly *required* set — below which any number returned is not a price but a
guess — is **two dimensions**:

1. Sign type (encodes material + method)
2. Size (width × height or square footage)

Everything else can be defaulted and stated explicitly in the quote. A quote with
defaults is still a defensible automated quote as long as the assumptions are surfaced.

### The defensible minimum (for a quote customers will act on)

Six dimensions:

1. Sign type
2. Size
3. Quantity
4. Install type
5. Turnaround
6. Location / jurisdiction (for permit cost)

### The key structural insight

Today, sign shops have human intake coordinators not because pricing arithmetic is
complex — that's solved software — but because **customers do not arrive with the
six dimensions pre-specified**. "I need a sign for my business" has zero of the six.

The automation bottleneck is therefore not the **quote engine** (pricing math).
It is the **intake disambiguation engine**: a structured conversation layer that
extracts the six dimensions from natural-language customer input.

**Corollary:** An AI-native quoting flow should front-load intake disambiguation via
conversational UI, then pass the structured 6-tuple to a deterministic pricing
engine. The LLM's job is extraction and confirmation, not calculation.

---

## Step 3 — Corpus Answer

Sign estimating software (EstiMate, shopVox, printplanr, GraphixCalc, STACK) accepts:
- Material type
- Dimensions
- Mounting / install details
- Complexity factors (character count, font style for channel letters)
- Labor rates and overhead (shop-configured)
- Quantity

Industry sources (isasign.com, blinksigns.com) describe "bundled" quotes that include
design, permitting, fabrication, and installation — and flag that the biggest cost
swings come from sign height, site access, electrical requirements, and permit
complexity.

The corpus consensus: "precision pricing requires precision input" — implying a
human intake step is assumed, not questioned.

---

## Step 4 — Delta Analysis

| Dimension | First-principles | Corpus | Match? |
|---|---|---|---|
| Core variable list (size, type, install, permits, qty, turnaround) | Yes | Yes | ✓ rediscovered |
| Distinction between hard-required vs. defaultable inputs | Yes | No | partial novel |
| Identification of intake disambiguation as the true bottleneck | Yes | No | **novel** |
| Prescription to separate disambiguation layer from pricing engine | Yes | No | **novel** |

**Category: novel**

The corpus treats human intake as a given and focuses on what the pricing engine
computes. It does not frame the problem as "what is the minimum required set" nor
does it identify the LLM-layer / conversation-layer as the missing piece that makes
autonomous quoting possible.

---

## Commentary

The variables were all rediscovered correctly — the reasoning chain was sound.
The value of this spike is the structural reframe: the hard problem is not pricing,
it's structured input extraction. Building a quote engine without first building
an intake disambiguation engine produces a tool that requires human pre-processing,
which defeats the automation goal.

**Durable rule:** When you want to automate a quoting or estimation workflow, always
ask "who is currently doing the input structuring?" before asking "who is doing the
calculation?" The calculation is usually already solvable; the structuring is where
the human is actually deployed.
