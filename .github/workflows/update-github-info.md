---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine: copilot
model: gpt-4.1-mini
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    draft: false
    max: 1
---

# Update GitHub Info

Keep the GitHub Info website current with concise, practical updates for developers.

1. Read `notes/mona-notes.md` and `site/content/github-info.md` before making changes.
2. Use the web-fetch tool to fetch `https://github.blog/latest/`.
3. Use the web-fetch tool to fetch `https://github.blog/changelog/`.
4. Use the web-fetch tool to fetch `https://awesome-copilot.github.com/workflows/`.
5. Use the GitHub repository API tools for repository reads, including any additional repository guidance or reference files you need. Do not use terminal, CLI, or sandboxed commands for GitHub API reads.
6. Based on the official GitHub Blog, Changelog, and Awesome Copilot workflows sources, update `site/content/github-info.md` with short, practical, source-linked information. Preserve the existing editorial angle and avoid unsupported claims.
7. Open one pull request containing the content change so Mona can review it. Include a concise title and body that summarize the updates and cite the official sources.