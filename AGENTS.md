# AGENTS.md

## Workspace Purpose

This repository is used to draft, revise, package, and archive Chinese long-form公众号 articles and their supporting assets.

The default unit of work is one article package.

## Account Goal

The account is 「说点AI」. Its primary goal is to grow into a trusted developer-focused account with at least 10,000 genuine followers.

Growth must come from useful, verifiable content rather than inflated claims, copied narratives, engagement bait, or low-quality high-frequency publishing. Optimize for both reach and long-term trust.

Use these account-level priorities when making editorial decisions:

1. Serve developers who use AI tools, coding agents, and automation in real work.
2. Publish original experiments, reproducible tutorials, workflow analysis, and informed technical judgments.
3. Build recognizable series so one strong article leads naturally to the next.
4. Improve click-through, completion, sharing, saves, follows, and returning readership without sacrificing accuracy.
5. Turn post-publication data and reader questions into the next editorial iteration.

Treat 10,000 followers as the milestone, not the editorial shortcut. Do not claim that a single article will become viral or guarantee follower growth.

## Growth Operating Rules

- Before drafting, define the target reader, one reader problem, one promised outcome, the original evidence, and the article's role in an ongoing series.
- Prefer topics that combine a real developer pain point with first-hand tests, code, logs, screenshots, comparisons, or primary sources.
- Every article must deliver standalone value before asking readers to follow.
- A publish-ready article should normally support 8–12 minutes of reading when the topic warrants depth. Quick news or focused answers may be shorter; source analysis and tutorials may be longer. Never pad to reach a word count.
- For substantial tutorials, workflow reviews, and source analysis, aim for roughly 3,500–5,500 Chinese characters in the publish-ready body unless the material justifies another length.
- Add length through evidence, examples, reasoning, tradeoffs, failure cases, and decision guidance—not repeated conclusions or generic background.
- End with a specific next article or reader question that fits the current topic. Do not use resource giveaways to induce sharing, likes, or follows.
- When publication metrics are available, record impressions, opens, completion or read depth, shares, saves, follows, unfollows, traffic sources, and meaningful comments in `notes.md`. Never invent missing metrics.

## Article Package Structure

Each article should live in its own folder using this pattern:

`YYYY-MM-DD-topic-slug/`

Example:

`2026-06-21-loop-engineering/`

Inside each article folder, use this structure when applicable:

- `full-article.md` for the complete long-form draft
- `summary.md` for the condensed summary
- `wechat-ready.md` for the publish-ready公众号排版稿
- `full-article.html` for exported HTML if one exists
- `images/` for illustrations, hand-drawn inserts, cover assets, and related media
- `notes.md` for extra research, outline notes, and post-publication review when performance data becomes available

## Naming Rules

- Use ISO date format: `YYYY-MM-DD`
- Use a short English slug for the folder name
- Keep filenames stable inside the folder so future automation can reuse them
- Prefer lowercase ASCII names for folders and asset files

## Writing Rules

- Default language is Simplified Chinese
- Prefer a natural, human tone over stiff AI-style phrasing
- Keep paragraphs short enough for mobile reading
- Lead with a concrete problem, result, conflict, or observation; reveal the core conclusion early
- Explain both how something works and why the reader should choose it
- Support major technical claims with first-hand evidence or primary sources
- Include limitations, costs, failure cases, and who should not use the approach
- Prefer useful depth over arbitrary length; do not publish a thin outline as a long-form article
- When preparing公众号 versions, include:
  - title options
  - recommended title
  - short导语
  - body copy
  - optional closing quote or金句
  - references if factual claims depend on them
  - a specific series continuation or discussion prompt

## Visual Asset Rules

- Store all article-specific images inside that article folder's `images/` directory
- Prefer editable formats such as `svg` for diagram-like hand-drawn inserts
- Match the article tone when generating visuals
- When inserting images into Markdown, use relative paths from the article file

## Archiving Rules

- Do not leave article drafts scattered in the repository root
- After a topic stabilizes, move related drafts, exports, and images into its article folder
- Keep root-level files limited to workspace-wide docs and config

## Root-Level Files

The repository root should generally contain only:

- `AGENTS.md`
- `README.md`
- tooling or lock files
- hidden config directories such as `.agents/`, `.claude/`, and `.git/`
- article package folders named by date and topic

## Working Preference

When creating a new article package:

1. create the dated folder
2. add or move the article files into it
3. create an `images/` subfolder if visuals are needed
4. keep related files together from that point onward
