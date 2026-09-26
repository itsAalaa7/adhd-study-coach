# The evidence behind this agent

This document exists so nothing in `agents/adhd-study-coach.md` is "science-based" by assertion only. For every behavior the agent has, this page says what research it's based on and how strong that evidence actually is — including the places where the honest answer is "plausible, not proven."

> **Note on sourcing:** this was compiled through AI-assisted literature research (web search over published papers, meta-analyses, and clinical-guideline summaries), not by a domain expert independently pulling primary sources. A second pass on 2026-09-26 checked the main citations against publisher, PubMed and index pages (see "Verification status" at the bottom); that pass found and fixed several wrong or unconfirmed numbers. Treat this as a well-sourced starting point, not a systematic review — verify before citing it academically or clinically, and please open an issue/PR if you spot an error.

## The one honest sentence this whole project rests on

General learning science has strong, repeatedly-replicated evidence for *what* works: retrieval practice and spaced review, above almost everything else. ADHD research mostly explains *why it's hard to keep doing the thing that works* — weak working memory, unreliable internal sense of time, a nervous system that responds poorly to delayed reward, and a lot of accumulated shame around not finishing things. This agent's actual job is removing those specific barriers to a well-proven method, not inventing an ADHD-specific study technique from scratch. Where a study exists that *directly* tests a technique on ADHD learners specifically, that's called out below — and it's rare.

## A. General learning science (strong foundation, general population)

| Technique | Key citation(s) | Evidence strength | What the agent does with it |
|---|---|---|---|
| Retrieval practice / testing effect | Roediger & Karpicke (2006), *Psychological Science* — repeated testing beat repeated re-study a week later (61% vs. 40% recall). Adesope, Trevisan & Sundararajan (2017), *Review of Educational Research* — meta-analysis of 272 independent effect sizes; practice testing beat restudy (weighted mean g ≈ 0.51) and beat no-activity/filler conditions (g ≈ 0.93). | **Strong** (meta-analysis) | Every review moment (MODE 1) is a quiz attempt, never a re-read of notes. |
| Spacing / distributed practice | Cepeda, Pashler, Vul, Wixted & Rohrer (2006), *Psychological Bulletin* — meta-analysis of 317 experiments (839 effects); optimal spacing scales with how long you need to remember it. | **Strong** (meta-analysis) | Growing-interval review schedule (1→3→7→16→35→90 days) in `review-schedule.json`. |
| Ranking of study-technique utility | Dunlosky, Rawson, Marsh, Nathan & Willingham (2013), *Psychological Science in the Public Interest*, 14(1) — practice testing and distributed practice rated **high utility**; elaborative interrogation, self-explanation, interleaving rated **moderate**; highlighting, re-reading, and summarizing rated **low utility**. | **Strong** (systematic review) | The agent actively redirects a learner away from highlighting/re-reading/summarizing as their *primary* strategy, toward testing + spacing. |
| Interleaving vs. blocked practice | Rohrer & Taylor (2007), *Instructional Science* — college students given mixed (shuffled) math practice scored far higher than blocked-practice students on a test one week later. Brunmair & Richter (2019), *Psychological Bulletin* — meta-analysis of 59 studies: interleaving helps inductive learning (e.g. category learning), but the effect for math tasks was small, with primary studies ranging from strongly negative to positive. | **Moderate** — real, but domain-dependent and weaker than testing/spacing | Warm-ups mix 2+ due topics rather than finishing one before starting the next, framed to the learner as a real-but-lighter-evidence technique. |
| Cognitive load theory / worked examples | Sweller (1988) and subsequent instructional-design research — working memory is limited; worked examples reduce load while a schema is being built, but should fade as skill grows (the "expertise-reversal effect"). | **Strong** (foundational, widely replicated) | Worked examples on first exposure to a concept; deliberately less hand-holding on repeat exposure. |
| Desirable difficulties | Bjork & Bjork — difficulties that slow initial learning (testing, spacing, interleaving, generation) improve long-term retention even though they feel harder in the moment. | **Strong** (well-replicated framework) | The agent explicitly tells the learner *why* something is supposed to feel harder, rather than only making it harder. |
| Self-explanation / generation effect | Rated moderate-utility in Dunlosky et al. (2013); consistent line of research on explaining material in one's own words improving comprehension and transfer. | **Moderate** | The end-of-session teach-back interview (MODE 3). |

## B. ADHD-specific research

| Finding | Key citation(s) | Evidence strength | What the agent does with it |
|---|---|---|---|
| ADHD as an executive-function / self-regulation disorder | Barkley (1997), *Psychological Bulletin*, and later work — reframes ADHD around behavioral inhibition, working memory, and self-regulation rather than "attention deficit" alone. Includes "time blindness" — a reduced ability to sense elapsed/remaining time. | **Strong** for the general framework; **strong-to-moderate** for time blindness specifically (well-established clinically, less isolated experimentally) | Time is stated factually at checkpoints by default, rather than left to the learner's internal sense of it. |
| Working memory deficits in ADHD | Kasper, Alderson & Hudec (2012), *Clinical Psychology Review* (children); Alderson, Kasper, Hudec & Patros (2013), *Neuropsychology* (adults, 38 studies) — both meta-analyses found significant working-memory deficits vs. controls (the children's meta-analysis reports large effect sizes; the adult effect sizes were not re-checked here). | **Strong** (meta-analyses, both age groups) | Harder caps on chunk size / new-concepts-per-section than a tutor built for a neurotypical default would use. |
| Delay aversion / reward sensitivity | Sonuga-Barke (2003), *Neuroscience & Biobehavioral Reviews* — the dual-pathway model — alongside executive dysfunction, a separate pathway of altered reward sensitivity drives strong preference for immediate over delayed reward. | **Moderate-to-strong** (one of two major, well-replicated causal models in the field) | Immediate feedback after every attempt; a one-line visible progress summary (solid/shaky counts, streaks) at the end of each warm-up rather than "trust me, it helps later." |
| Task-initiation difficulty | Popularized clinically as the "Wall of Awful" (Brendan Mahan); consistent with executive-function research showing task-initiation is specifically impaired in ADHD. | **Weak-to-moderate** (clinical/coaching framework, not itself an experimentally isolated construct) | Sessions open with one tiny action, never a full scope overview. |
| Rejection Sensitive Dysphoria | Term from William Dodson (clinical observation); not in the DSM or ICD, has no validated instrument of its own, and direct research is very limited (mostly anecdotal reports and small studies). | **Weak** (clinical consensus / small case series, not experimentally validated) | The strict never-shame, never-"wrong" language rules — framed honestly as good clinical practice, not an RCT finding. |
| Body doubling | Working alongside another person for accountability. | **Anecdotal / mixed** — the evidence base is mostly anecdotal accounts. A few recent HCI studies are just starting to test it directly, with mixed results: a qualitative study with neurodivergent participants (ACM TACCESS 2024), a virtual-reality study (2025), and a small brain-computer-interface study that found no significant effect on performance or focus. | Offered only as an optional, clearly-labeled low-evidence feature — never presented alongside the strong-evidence techniques as equivalent. |
| Gamification tested directly in an ADHD population | An 8-week RCT (2025, *Frontiers in Education*, n=80 children aged 6–12 with clinically diagnosed ADHD) found a gamified app group improved significantly on sustained attention, reaction time, and academic scores vs. non-gamified controls. | **Moderate** (single RCT, pediatric — generalizing to adult self-directed study is an inference) | Lightweight visible gamification (streaks, session counts), explicitly caveated as extrapolated from a pediatric study. |
| Clinical guidance on tool activation | CHADD and NICE materials on adult ADHD note that supports requiring self-initiated activation tend to be underused, because initiating use of the support is itself an executive-function demand. | **Moderate** (clinical consensus, not a controlled trial of a specific tool) | The agent auto-runs its warm-up/review and its periodic self check-in — neither depends on the learner remembering to ask. |

## The gap, stated plainly

There is very little direct experimental research on spaced repetition, retrieval practice, or AI tutoring *specifically validated in ADHD populations*. Almost everything in section A is general-population cognitive psychology; almost everything in section B explains why the *barriers to using it consistently* are real, not that the technique itself works differently in an ADHD brain. This agent is built on the position that this is fine — and honest: the techniques in section A are strongly proven, and the ADHD research tells you exactly which barriers to design around so a person can actually keep using them.

## Not a clinical tool

This project is a study-methodology aid, not a diagnostic, therapeutic, or medical device, and it does not replace clinical care for ADHD. If you're looking for treatment, talk to a clinician.

## Verification status (checked 2026-09-26)

Checked against publisher, PubMed and index pages:

| Citation | Status |
|---|---|
| Roediger & Karpicke (2006), *Psychological Science* 17, 249–255; 61% vs 40% after one week | ✅ Confirmed |
| Cepeda et al. (2006), *Psychological Bulletin* 132, 354–380; 317 experiments, 839 assessments | ✅ Confirmed |
| Dunlosky et al. (2013), *Psych Science in the Public Interest* 14(1), 4–58 | ✅ Article confirmed (utility ratings match the paper's published conclusions) |
| Barkley (1997), *Psychological Bulletin* 121(1), 65–94 | ✅ Confirmed |
| Kasper, Alderson & Hudec (2012), *Clinical Psychology Review* 32(7), 605–617 — large effect sizes | ✅ Confirmed |
| Alderson et al. (2013), *Neuropsychology* 27(3), 287–302 | ✅ Exists, 38 studies; effect sizes not re-checked |
| Sonuga-Barke (2003), *Neurosci. Biobehav. Rev.* 27(7), 593–604 | ✅ Confirmed |
| Dai, Wufue & Zhang (2025), *Frontiers in Education*, gamified app RCT, n=80, ages 6–12, 8 weeks | ✅ Confirmed |
| Brunmair & Richter (2019), *Psychological Bulletin*, 59 studies | ✅ Confirmed |
| Rohrer & Taylor (2007), *Instructional Science* 35, 481–498 | ✅ Exists; earlier "doubled next-day scores" was wrong (test was one week later) and was corrected |
| Adesope et al. (2017), *Review of Educational Research* | ⚠️ Exists; earlier "217 studies, g = 0.61" could not be confirmed and was replaced with figures found in secondary sources (272 effect sizes, g ≈ 0.51 / 0.93). Check the paper's abstract before quoting the exact numbers |
| Sweller (1988), Bjork & Bjork, CHADD/NICE guidance, "Wall of Awful" (Brendan Mahan), Dodson on RSD | ❔ Not re-checked in this pass |
