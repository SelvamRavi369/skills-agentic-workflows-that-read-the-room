---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
engine: copilot
strict: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    base-branch: main
    allowed-base-branches:
      - main
    draft: false
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Update `site/content/github-info.md` with concise,
practical updates for readers and include source context for content from the
GitHub Blog, GitHub Changelog, or Awesome Copilot workflows.

Open a pull request for Mona to review. 
Use a pull request title that mentions Mona or GitHub Info. 
Do not write directly to `main`;
rely on `safe-outputs` with `create-pull-request`.

## Process

1. Read `notes/mona-notes.md` and the current `site/content/github-info.md` before drafting.
2. Use web-fetch to read `https://github.blog/latest/`, `https://github.blog/changelog/`, and `https://awesome-copilot.github.com/workflows/` on every run.
3. Select only recent developments that help developers learn or use GitHub, and fit the site's existing themes and Mona's editorial guidance. Verify each detail against its source; do not speculate or repeat existing content without a useful update.
4. Update only `site/content/github-info.md`. Keep the writing short and practical, preserve relevant existing guidance, and link each update to its specific Blog, Changelog, or Awesome Copilot source.
5. Review the diff for accuracy, concise wording, and source links. Do not change any other file.
6. If the content changed, use the configured create-pull-request safe output to open a pull request targeting `main` for Mona to review. Summarize the updates and link the sources in the pull request description. Never push changes directly to `main` or use another write path.
7. If there is no meaningful, verified update, leave the file unchanged and do not open an empty pull request.