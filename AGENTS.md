# AGENTS.md

## Workspace Purpose

This repository is used to draft, revise, package, and archive Chinese long-form公众号 articles and their supporting assets.

The default unit of work is one article package.

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
- `notes.md` for extra research or outline notes if needed

## Naming Rules

- Use ISO date format: `YYYY-MM-DD`
- Use a short English slug for the folder name
- Keep filenames stable inside the folder so future automation can reuse them
- Prefer lowercase ASCII names for folders and asset files

## Writing Rules

- Default language is Simplified Chinese
- Prefer a natural, human tone over stiff AI-style phrasing
- Keep paragraphs short enough for mobile reading
- When preparing公众号 versions, include:
  - title options
  - recommended title
  - short导语
  - body copy
  - optional closing quote or金句
  - references if factual claims depend on them

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
