# Experiment Results Log

The single source of truth for every concluded Optimizely experiment. Results that used to live in personal SharePoint folders and Slack threads are logged here in one consistent format, so learnings are easy to find, share and build on.

## How results get here

Entries are created automatically by **Mark** when an experiment is concluded:

1. An experiment is set to **Concluded** in Optimizely (or a scheduled run picks it up).
2. Mark pulls the results, segment breakdowns and behavioral insights.
3. Mark fills in the [results template](templates/experiment-result-template.md) and opens a **pull request**.
4. The experiment owner reviews and merges. The entry is added to the [index](INDEX.md).

## Repository structure

```
results/
  {year}/
    {yyyy-mm-dd}-{experiment-slug}.md   # one file per concluded experiment
templates/
  experiment-result-template.md
INDEX.md                                # searchable table of every logged experiment
```

## File naming

`results/{year}/{yyyy-mm-dd}-{experiment-slug}.md`, where the date is the conclusion date and the slug is the experiment name in lowercase with hyphens.

Example: `results/2026/2026-11-20-checkout-express-pay-buttons.md`

## Finding learnings

- Browse or search the [index](INDEX.md) by area, outcome or tag.
- Search the repo for front matter values, for example `outcome: "win"` or `area: "checkout"`.
- Ask Mark, for example: *"What have we learned from checkout tests this year?"*

## Outcomes

| Outcome | Meaning |
|---|---|
| Win | Primary metric improved with statistical significance |
| Loss | Primary metric declined with statistical significance |
| Inconclusive | No significant change on the primary metric |
