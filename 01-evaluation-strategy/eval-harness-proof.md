# First LLM-as-a-Judge Eval, Module 1

> Repo file `ai-evals/01-evaluation-strategy/eval-harness-proof.md`. The eval evidence behind the **Eval Results** slide of the final pitch deck (Module 6).
>
> Fill this with the **First Eval Lab** builder, then **Copy markdown** and paste it over this file. The headings below mirror the tool's output exactly.

## Version A, Concise, system prompt used

**Prompt**:
You are an executive briefing assistant.
Summarize in exactly 3 bullet points under 60 words. No preamble, no extra text.

Subject: Q4 Marketing Campaign Update

Hi team,

Social media engagement is up 25% month-over-month due to the new content calendar and paid ad experiments.

Newsletter open rate dropped from 42% to 35%; we'll test new subject lines next week.

The product video campaign is delayed until November, pending legal approval; creative assets are ready.

Please ensure all campaign tracking links are added by Friday.

Best, 
Priya

**Output**:
Social media engagement rose 25% month-over-month, driven by the new content calendar and paid ad experiments.
Newsletter open rate fell from 42% to 35%; new subject lines will be tested next week.
Product video campaign is delayed to November pending legal approval, though creative assets are ready; all tracking links are due Friday.

## Version B, Narrative, system prompt used

**Prompt**:
You are a PR communications assistant.
Write a 100-word narrative summary highlighting wins first, then risks and next steps.
Keep a positive tone. No bullets. Subject: Q4 Marketing Campaign Update

Hi team,

Social media engagement is up 25% month-over-month due to the new content calendar and paid ad experiments.

Newsletter open rate dropped from 42% to 35%; we'll test new subject lines next week.

The product video campaign is delayed until November, pending legal approval; creative assets are ready.

Please ensure all campaign tracking links are added by Friday.

Best, 
Priya

**Output**:
Subject: Q4 Marketing Campaign Update

Hi team,

Q4 is off to an encouraging start. Social media engagement is up 25% month-over-month, driven by our new content calendar and paid ad experiments, which shows real momentum. Our product video creative assets are fully ready, so we're well positioned to launch quickly. Two areas need attention: newsletter open rates slipped from 42% to 35%, and the video launch has moved to November pending legal approval. We'll test fresh subject lines next week to rebuild newsletter performance. To keep us on track, please add all campaign tracking links by Friday.

Best,
Priya


## Eval setup, dataset name + judge model/family

_e.g. dataset `Module1Output`, Conciseness LLM-as-a-Judge, judge from a different model family than the generator (avoids self-preference bias)._

## Cold-start, the prompt you used to seed a starter dataset

_Paste the prompt you gave ChatGPT to generate ~20 example rows._

## Your definition of good vs bad (golden-set criteria) — the graded part, write your own

_What makes a summary genuinely good or bad for THIS product? This is the judgment call that's yours — don't copy the example._

## Screenshots, links or repo paths (optional if you followed the demo)

_2 shots: (1) eval setup (dataset + judge), (2) starter rows. Image links, or paths under `01-evaluation-strategy/screenshots/`._
