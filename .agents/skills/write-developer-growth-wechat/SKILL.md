---
name: write-developer-growth-wechat
description: Create, revise, or package Simplified-Chinese WeChat public-account articles for developers using strong topic selection, benefit-led titles, progressive technical explanation, code or experiment evidence, and a repeatable follow-conversion structure. Use for AI tools, Agent workflows, programming tutorials, source-code deep dives, technical news analysis, tool roundups, interview-style explainers, and requests to benchmark the content mechanics of 程序员成长指北 without copying its wording.
---

# Write Developer Growth WeChat

Build articles with a high-click outer layer and a trustworthy technical core. Adapt the mechanics to the author's real experience; never imitate sentences, anecdotes, identity, or unverifiable claims.

## Load resources

- Read [references/benchmark.md](references/benchmark.md) when selecting a content mode, title pattern, or article structure.
- Copy and fill [assets/article-template.md](assets/article-template.md) when creating a new article package.

## Workflow

### 1. Read the workspace and source material

1. Read repository instructions and the target article folder.
2. Read supplied notes, links, screenshots, code, tests, and prior related articles.
3. If the topic is current, disputed, technical, or factual, research primary sources before outlining.
4. Record the source date and product or library version. Treat stale claims as hypotheses until verified.

### 2. Choose one content mode

Choose exactly one primary mode:

| Mode | Use it for | Required original value |
|---|---|---|
| Fast signal | Releases, policy changes, new tools | Explain who should care, what changes, and what to do next |
| Practical tutorial | A concrete developer problem | Reproducible steps, code, limitations, and verification |
| Source deep dive | Agent, framework, or library internals | Architecture, data flow, key code, and transferable lessons |
| Scenario explainer | Concepts that feel abstract | A realistic interview, incident, or debugging scenario |
| Curated stack | Tool or ecosystem overview | Selection criteria, trade-offs, and a recommended path |

Reject a topic if it has no clear target reader, no timely or durable value, or no original increment beyond source summary.

### 3. Score the topic

Score each dimension from 0 to 5:

- Audience pain × 25%
- Freshness or search durability × 15%
- Original increment × 25%
- Proof availability × 25%
- Series potential × 10%

Proceed at 3.5/5 or higher. If proof availability or original increment is below 3, research or test before drafting.

### 4. Build the one-page brief

Write these fields before writing prose:

- Target reader
- One problem
- One promised result
- Why now
- Main conclusion
- Original increment
- Proof assets: code, screenshots, logs, timing, cost, comparison, or source excerpts
- One follow-up article
- One natural call to action

Keep one article focused on one primary promise.

### 5. Create and score titles

Generate at least 10 options across four patterns:

1. Familiar tool + surprising change
2. Pain + concrete result
3. Number or constraint + strong benefit
4. Question or interview scene + underlying principle

Score each title from 0 to 2 on clarity, audience fit, concrete benefit, curiosity, and evidence match. Recommend the highest-scoring title.

Do not use `重磅`, `炸裂`, `史上最强`, `彻底`, or absolute rankings unless the body proves the claim. Never promise a result the article does not deliver.

### 6. Draft the article

Use this sequence unless the content mode requires a small adjustment:

1. Open with a concrete situation, friction, result, or contradiction in 80–160 Chinese characters.
2. State why the reader should care and preview the conclusion.
3. Move from the smallest useful answer to deeper explanation.
4. Add evidence at every major claim: runnable code, screenshot, output, source, table, or explicit reasoning.
5. Explain edge cases, cost, risk, and who should not use the approach.
6. End with a short decision summary or checklist.
7. Use a specific next-issue CTA. Invite discussion or following naturally; never require sharing, likes, or `在看` in exchange for materials.

Keep paragraphs short for mobile reading. Prefer direct verbs, concrete nouns, and first-hand observations. Remove generic scene-setting, inflated claims, repetitive transitions, and motivational filler.

### 7. Verify the technical core

Before packaging:

- Confirm every version, benchmark, price, date, API, and product capability against a primary source.
- Run code or clearly label it as illustrative and unverified.
- Separate official claims, third-party measurements, and the author's inference.
- Check that screenshots and code support the stated conclusion.
- Add attribution for translations, adapted tutorials, and quoted ideas.
- Declare AI-generated or AI-edited media when current platform rules require it.

### 8. Package the deliverables

Follow the workspace article-package rules. Produce:

- `full-article.md`: complete source draft
- `summary.md`: thesis, structure, and reusable lines
- `wechat-ready.md`: title options, recommended title, lead, body, optional closing line, and references
- `images/`: article-specific assets using relative Markdown paths
- HTML only when a confirmation or exported document is requested by workspace rules

Also provide two朋友圈 introductions and one 30–60 second video outline when growth distribution is in scope.

## Final quality gate

Do not finish until all answers are yes:

- Can a developer identify within 10 seconds whether this article is for them?
- Does the first screen contain a concrete problem or result?
- Is there at least one piece of evidence that cannot be produced by generic rewriting?
- Does the article explain both how and why?
- Are limitations and unsuitable cases present?
- Does the title accurately match the body?
- Is the text recognizably this author's experience rather than another account's persona?
- Are sources and reused ideas attributed?
