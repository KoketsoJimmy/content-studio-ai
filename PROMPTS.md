# Prompts used to build Content Studio

The app was developed with Claude. This file records the prompts used in the improvement round. The original prompts that produced the first version of the app were not available when this file was written.

## 1. Improvement prompt (main specification)

> You are an expert senior frontend engineer, UI/UX designer, product designer, and AI application architect.
>
> I have attached my existing **Content Studio HTML application**. Your task is to significantly improve and modernize the application while preserving all existing functionality that already works.
>
> ## IMPORTANT RULES
>
> 1. DO NOT rebuild the application from scratch.
> 2. Work directly on the existing HTML file.
> 3. Preserve the existing architecture, features, templates, Claude integration, local storage functionality, history, brand kit, settings, keyboard shortcuts, page preview, editing, copying, printing, downloading, and other working functionality.
> 4. Do not remove an existing feature simply because you think there is a better approach.
> 5. Improve the existing implementation progressively.
> 6. Keep the application as a self-contained HTML application unless there is a compelling technical reason otherwise.
> 7. Do not introduce unnecessary frameworks or dependencies.
> 8. Do not replace the Claude integration with another AI provider.
> 9. Do not expose API keys, secrets, authentication tokens, or sensitive information in client-side code.
> 10. Maintain backwards compatibility with existing saved drafts, history, preferences, templates, and brand-kit data where possible.
> 11. The final application must remain usable if the user has no existing content.
> 12. Test every major feature after implementation.
> 13. If a feature cannot be implemented safely without breaking existing functionality, keep the existing implementation and improve it incrementally.
> 14. Prioritize usability, reliability, accessibility, performance, responsive design, and maintainability over adding unnecessary visual effects.
>
> ### PRODUCT VISION
>
> Transform Content Studio from a good AI content-generation tool into a polished **AI Content Workspace**. The ideal workflow should feel like: **Idea → Prompt → Generate → Edit → Refine → Repurpose → Compare → Finalize → Export**. The application should feel modern, intelligent, fast, professional, and easy to use for someone who may not be an expert at prompt engineering.
>
> ### PHASE 1 — CORE EXPERIENCE
>
> **1. AI-first dashboard.** Provide a clear command center with a large input ("Tell me what you want to create..."), example requests (LinkedIn post, 1,000-word blog article, turn an article into 5 social posts, improve an email, product description, rewrite in a professional tone), quick actions (Create Content, Improve Writing, Rewrite, Summarize, Expand, Shorten, Humanize, Repurpose, Brainstorm, Generate Ideas), recent work, a "Continue where you left off" offer for unfinished drafts, and easier template discovery.
>
> **2. Conversational AI mode.** An optional workflow where users keep working with the AI without refilling the form (e.g. "Make it more personal", "Give me three different hooks", "Use the second hook", "Now make it shorter"). It should use conversation history, current document, content type, brand voice, user instructions and previous revisions, with sensible context management so history does not grow indefinitely.
>
> **3. Improve the prompt-building system.** Keep the structured builder; incorporate content type, objective, audience, platform, tone, length, language, creativity, keywords, CTA, brand voice, words to avoid, required phrases, the original request and document context. Remove repetition, prioritize user instructions, separate instructions from content, prevent hallucination, ask for clarification only when necessary, preserve user facts, avoid invented statistics/quotes/sources/claims, and respect language, tone and length.
>
> **4. "Improve My Prompt".** Turn a vague request ("Write something about my business.") into a specific one. Show original prompt, improved prompt, Use Improved Prompt, Edit, Copy. Do not force the user to use it.
>
> **5. Refinement controls.** Quick actions: Improve, Make clearer, Make concise, Expand, Simplify, Professional, Friendly, Persuasive, Humanize, Add examples, Improve flow, Fix grammar, Change tone, Add CTA, Create stronger introduction, Create stronger conclusion. Allow custom instructions. Refine selected text only if text is selected, otherwise the whole document.
>
> ### PHASE 2 — CONTENT REPURPOSING
>
> **6. Content Repurposing Hub.** Turn existing content into LinkedIn post, X/Twitter post, Instagram caption, Facebook post, email newsletter, blog summary, YouTube description, YouTube script, short-form video script, TikTok script, Instagram Reel script, quote cards, key takeaways, FAQ, newsletter, thread, SEO meta description. The original stays untouched; users can select multiple outputs shown in separate cards/tabs with Copy, Edit, Regenerate, Save, Export.
>
> ### PHASE 3 — VERSION CONTROL
>
> **7. Version history.** Every major generation/refinement can create a version showing version number, date/time, action, content type and short preview, with Restore, Rename, Duplicate, Delete, Compare. Use a sensible strategy; do not create hundreds of versions.
>
> **8. Side-by-side comparison.** Compare Current Version | New Version with Keep Current, Use New Version, Merge Manually, Copy Current, Copy New. Highlight meaningful differences where practical. Never overwrite existing content automatically.
>
> ### PHASE 4 — BRAND INTELLIGENCE
>
> **9. Expanded Brand Kit.** Identity (name, description, industry, target audience, website, social links); voice (brand voice, personality, formality, preferred style); language rules (words to use/avoid, phrases to avoid, preferred terminology, spelling preference); content rules (always include, never include, CTA preference, emoji preference, hashtag preference); and examples of preferred writing. Use relevant Brand Kit information automatically when generating.
>
> ### PHASE 5 — PROJECTS AND ORGANIZATION
>
> **10. Projects/Workspaces.** Create, rename, delete and duplicate projects; add documents; search documents. Keep it local-first.
>
> ### PHASE 6 — SEO FEATURES
>
> **11. Optional SEO Assistant** (for blog/article content, in a simple panel): SEO title suggestions, meta description, focus keyword, secondary keywords, search intent, suggested headings, FAQ suggestions, internal linking suggestions, readability suggestions, keyword placement guidance.
>
> ### PHASE 7 — CONTENT QUALITY
>
> **12. Content Quality Analysis ("Analyze").** Check clarity, structure, readability, grammar, tone consistency, audience suitability, repetition, weak sections, missing CTA, unsupported claims, excessive filler. Do not present AI scores as objective truth (label them as estimates). Prefer actionable feedback with a follow-up action such as "Improve Introduction".
>
> ### PHASE 8 — EXPORT
>
> **13. Export options.** Preserve existing downloads. Add TXT, Markdown, HTML, JSON, Print, PDF via the browser print workflow, DOCX if it can be done safely without a large dependency, and "Export Project". Never export secrets or API credentials.
>
> ### PHASE 9 — AUTOSAVE AND DATA SAFETY
>
> **14. Strengthen autosave.** Autosave while typing, debounce writes, save draft state, preserve content after refresh, restore interrupted drafts, show save status ("Saved", "Saving...", "Saved 10 seconds ago"). Use IndexedDB for larger datasets if practical, without destructive migration of existing localStorage data.
>
> **15. Fix unsaved-change detection.** Review the `S.dirty` logic so that changes to title, request, content type, goal, audience, platform, tone, length, language, creativity, keywords, CTA and other form fields count as unsaved. When starting a new document with unsaved changes offer "Save & Continue", "Discard Changes", "Cancel". Never silently lose content.
>
> ### PHASE 10 — UX / UI IMPROVEMENTS
>
> **16. Visual hierarchy.** Keep the design language but make it more premium: spacing, typography, hierarchy, buttons, cards, panels, empty states, inputs, navigation, modals, notifications. Avoid excessive gradients, animations and shadows.
>
> **17. Responsive/mobile.** Work on desktop, laptop, tablet and mobile: collapse navigation, sidebars become drawers, touch-friendly controls, no horizontal overflow, important actions accessible, modals fit the viewport. A deliberate mobile experience, not a shrunken desktop.
>
> **18. Accessibility.** Semantic HTML, labels, keyboard navigation, visible focus, ARIA where needed, contrast, accessible dialogs, dropdowns and notifications, screen-reader-friendly controls; everything usable without a mouse.
>
> ### PHASE 11 — ERROR HANDLING
>
> **19. AI error states with useful actions.** Rate limit ("Claude is temporarily busy" — Retry); offline ("You appear to be offline" — Retry); permission issue ("AI access is unavailable", explained without exposing secrets); generation failure ("Your existing content has been preserved" — Retry, Edit Prompt, Close). Never replace valid content with an error message.
>
> **20. Generation progress.** Meaningful messages ("Understanding your request...", "Creating your draft...", "Polishing the response...", "Almost done...") with no fake percentages, stopping immediately on completion or failure.
>
> ### PHASE 12 — ONBOARDING
>
> **21. First-use experience.** Steps: create content; choose a template or describe what you need; generate; refine; repurpose; export. Include "Skip introduction", do not repeat it, store completion locally.
>
> ### PHASE 13 — PROMPT LIBRARY
>
> **22. Reusable prompts.** Save, edit, delete, duplicate, categorize (Marketing, Social Media, Business, Career, Email, SEO, Education, Writing, Brainstorming) and search prompts; turn the current request into a reusable prompt.
>
> ### PHASE 14 — SMART EMPTY STATES
>
> **23. Actionable empty states** with example prompts instead of blank screens ("No document yet — Start by telling Content Studio what you want to create.").
>
> ### PHASE 15 — SECURITY AND PRIVACY
>
> **24. Security review.** Audit for XSS, unsafe innerHTML, unsafe user-generated HTML, injection, insecure localStorage use, exposure of sensitive data, unsafe links, malformed input and unsafe template rendering. Escape/sanitize user content, never execute user-provided HTML or JavaScript, never store API keys in localStorage. Clearly explain what is stored locally and what is sent to Claude, preserving and clarifying the existing privacy messaging.
>
> ### PHASE 16 — CODE QUALITY
>
> **25. Refactor carefully.** Review for duplicated logic, unused functions, inconsistent naming, fragile DOM manipulation, unnecessary re-rendering, event listener issues, state-management problems, storage errors, race conditions and asynchronous errors. No massive rewrite for style; refactor only where it improves reliability or maintainability.
>
> ### IMPORTANT BUG CHECK
>
> Dirty state: verify `S.dirty` updates for form fields, not only the editor. Refinement controls: resetting preferences must not duplicate refinement controls or other UI. Local storage: handle corrupted JSON, missing keys, quota errors and old formats. History: malformed entries must not break the app. AI generation: prevent multiple simultaneous requests and manage buttons while generating. Existing output: never destroy valid output if regeneration fails.
>
> ### PERFORMANCE
>
> Debounce autosave, avoid unnecessary full-page rendering, minimize DOM operations, avoid duplicated listeners and memory leaks, limit history rendering, lazy-render large panels, prevent unnecessary AI calls, and stay responsive with many documents.
>
> ### DO NOT BREAK EXISTING FEATURES
>
> Content type selection, templates, history, favorites, search, editing, regeneration, copy, print, fullscreen, page preview, downloads, settings, theme, tone, length, language, creativity, Brand Kit, refinement controls, keyboard shortcuts, local autosave, Claude integration, existing prompt construction and existing error handling.
>
> ### UI PRINCIPLE
>
> Use progressive disclosure. The main screen stays simple: **Create → Generate → Edit → Refine**. Advanced functionality lives in panels, drawers, tabs, modals and secondary toolbars.
>
> ### FINAL QUALITY CHECK
>
> Inspect the whole application; understand state management and the Claude integration; reuse existing functions; implement incrementally; check syntax errors, DOM selectors, event listeners and localStorage handling; then test generation, regeneration, editing, copying, history, favorites, templates, settings, Brand Kit, autosave, refresh/recovery, new-document flow, mobile layout, keyboard navigation, error states, empty states and export/download.
>
> ### PRIORITY ORDER
>
> **Priority 1:** AI-first dashboard, conversational workflow, Improve My Prompt, better refinement controls, content repurposing, version history, side-by-side comparison, reliable autosave/dirty state.
> **Priority 2:** expanded Brand Kit, projects/workspaces, Prompt Library, SEO Assistant, Content Quality Analysis, better exports.
> **Priority 3:** onboarding, mobile UX, accessibility, performance, security hardening, code refactoring.
>
> Do not sacrifice the stability of existing features just to implement lower-priority features.
>
> ### FINAL DELIVERABLE
>
> Return the complete updated `Content Studio.html` file (not snippets, nothing omitted), followed by a concise summary: what changed, new features, bugs fixed, existing features preserved, limitations, and recommended next improvements. The result should feel like a **professional AI content creation workspace**, not a collection of additional buttons.

## 2. Follow-up requests

1. Fetch and review the existing Content Studio artifact, then wait for change requests.
2. Apply the improvement prompt above to the app.
3. "Please create a documentation file and presentation for this app."
4. "Please use the same colors which were used on the app for the presentation file."
5. "Please push this app to my GitHub repo."
6. "Please include the prompts used to build this app."

## 3. What was implemented from the improvement prompt

Quick actions, Improve my prompt, expanded refinement chips with selected-text refinement, autosave with save status and output recovery, correct unsaved-change detection with a Save & Continue / Discard / Cancel dialog, and fixes for the duplicated/missing refine chips and the Brand Kit checkbox. The remaining items (conversational mode, repurposing hub, versions and comparison, projects, prompt library, SEO, analysis, extra exports, onboarding, mobile and accessibility passes) are still to do.
