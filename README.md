# ContentStudio

A one stop platform to generate content of different types.

Content Studio is a self-contained AI writing workspace. It is a single HTML page (no build step, no frameworks) that uses Claude to draft and refine content such as blog posts, social posts, emails and product descriptions.

## Features

- **Content types and templates** with tone, length, language and creativity controls
- **Quick actions:** Improve writing, Rewrite, Summarize, Expand, Shorten, Humanize, Repurpose, Brainstorm
- **Improve my prompt:** turns a rough request into a clearer brief; you choose whether to use it
- **Refinement:** one-click chips and custom instructions, applied to a text selection or the whole document
- **Brand kit** applied to generated content
- **History, favorites and search**
- **Page preview, inline editing, fullscreen, copy, print and download**
- **Autosave and draft recovery,** with a save status indicator
- **Unsaved-change protection:** Save & Continue, Discard Changes or Cancel when starting a new document
- Light and dark themes

## Getting started

1. Open `index.html` in a browser.
2. Pick a content type or a quick action, and describe what you need.
3. Select **Generate**, then refine, edit and export.

## Important: AI generation

Generation uses Claude through the Claude artifact runtime. It works when the app is opened from its claude.ai link. If you host the file elsewhere (for example GitHub Pages), the page loads and everything except AI generation works. To generate content outside claude.ai you would need to connect your own AI backend. Keep any API key on a server, never in the page.

## Privacy

- **Stored in your browser:** drafts, history, favorites, brand kit and preferences
- **Sent to Claude:** your request, chosen settings, the brand kit if enabled, and any text you ask it to refine
- **Not stored:** API keys or secrets

## Documentation

- [Full documentation](docs/DOCUMENTATION.md)
- [Prompts used to build the app](docs/PROMPTS.md)

## Roadmap

Conversational mode, repurposing hub, versions with side-by-side comparison, projects, prompt library, SEO assistant, content quality analysis, more export formats (Markdown, HTML, JSON, DOCX), onboarding, and mobile and accessibility improvements.
