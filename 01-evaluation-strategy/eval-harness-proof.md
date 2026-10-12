# First LLM-as-a-Judge Eval, Module 1

> Repo file `ai-evals/01-evaluation-strategy/eval-harness-proof.md`. The eval evidence behind the **Eval Results** slide of the final pitch deck (Module 6).
>
> Fill this with the **First Eval Lab** builder, then **Copy markdown** and paste it over this file. The headings below mirror the tool's output exactly.

## Version A, Concise, system prompt used

```
You are an executive briefing assistant. Summarize in exactly 3 bullet points under 60 words. No preamble, no extra text.
```

## Version B, Narrative, system prompt used

```
You are a PR communications assistant. Write a 100-word narrative summary highlighting wins first, then risks and next steps. Keep a positive tone. No bullets.
```

## Eval setup, dataset name + judge model/family

- **Dataset:** `Module1Output`, 20 varied internal business emails (marketing results, incident reports, sales updates, finance notes), each mixing wins and risks.
- **Generator:** ChatGPT (OpenAI GPT family), same model for Version A and Version B.
- **Judge:** Conciseness LLM-as-a-Judge, Claude Opus 5.5 (Anthropic). A different model family than the generator, to avoid self-preference bias.
- **Score:** 1 = concise and faithful to the email, 0 = not.

## Cold-start, the prompt you used to seed a starter dataset

```
Generate 20 realistic internal business emails for a B2B analytics company called Ascend Analytics. Return them as a table with columns: id, email_type, email_text.

Requirements:
- Mix the types: 5 marketing results, 5 incident or outage reports, 5 sales pipeline updates, 5 finance or budget notes.
- Vary the length from 80 to 300 words.
- Every email must contain at least one clear win and at least one risk or open problem, with specific numbers (percentages, dollar amounts, dates).
- Write them the way real colleagues write: some well structured, some rambling, some that bury the main point in the last paragraph.
- Do not summarise the emails or add commentary.
```

## Your definition of good vs bad (golden-set criteria) — the graded part, write your own

An Ascend IQ summary is read instead of the source, so the reader acts on it without checking. That sets the order of what matters.

**A summary is good when:**

1. **Every claim traces to the source.** Each number, date, cause and commitment in the summary appears in the email. Nothing is added, including tone: an email that reports a delay is not summarised as "well positioned".
2. **The biggest risk survives.** The item most likely to change a decision (a drop, a delay, a blocker) is stated as plainly as the wins, with its number.
3. **It is clearly shorter than the source.** It holds the format limit and cuts reading time. A summary as long as the email has failed, however accurate it is.
4. **Actions keep their owner and deadline.** If the email asks for something by a date, the summary says so.

**A summary is bad when** it fails any one of the first two, whatever else it does well. Failing 3 or 4 makes it weak, not dangerous.

**Applied to this run:** Version A passes all four, though at 53 words against 57 it barely clears number 3 on an email this short. Version B fails number 1 ("real momentum", "well positioned to launch quickly" are not in the email) and number 3 (90 words against 57). It keeps the risks, so it passes number 2.

## Screenshots, links or repo paths (optional if you followed the demo)

### Input email (57 words in the body)

```
Subject: Q4 Marketing Campaign Update

Hi team,

Social media engagement is up 25% month-over-month due to the new content calendar and paid ad experiments.

Newsletter open rate dropped from 42% to 35%; we'll test new subject lines next week.

The product video campaign is delayed until November, pending legal approval; creative assets are ready.

Please ensure all campaign tracking links are added by Friday.

Best, Priya
```

### Version A output (53 words)

```
Social media engagement rose 25% month-over-month, driven by the new content calendar and paid ad experiments.
Newsletter open rate fell from 42% to 35%; new subject lines will be tested next week.
Product video campaign is delayed to November pending legal approval, though creative assets are ready; all tracking links are due Friday.
```

### Version B output (90 words in the body)

```
Subject: Q4 Marketing Campaign Update

Hi team,

Q4 is off to an encouraging start. Social media engagement is up 25% month-over-month, driven by our new content calendar and paid ad experiments, which shows real momentum. Our product video creative assets are fully ready, so we're well positioned to launch quickly. Two areas need attention: newsletter open rates slipped from 42% to 35%, and the video launch has moved to November pending legal approval. We'll test fresh subject lines next week to rebuild newsletter performance. To keep us on track, please add all campaign tracking links by Friday.

Best, Priya
```

### Judge result (Claude Opus 5.5, 1 = concise and faithful, 0 = not)

| Version | Score | Judge's reason |
|---|---|---|
| A, Concise | 1 | 53 words, inside the 60-word limit. Every number, date and cause matches the email and nothing is added. |
| B, Narrative | 0 | 90 words against a 57-word email, so the summary is longer than its source. It adds claims the email does not make ("encouraging start", "real momentum", "well positioned to launch quickly") and is written as an email from Priya, not as a summary. |

**Winner on this judge: Version A.**
