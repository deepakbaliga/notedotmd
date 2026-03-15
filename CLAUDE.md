# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

- `pnpm dev` — start dev server (http://localhost:3000)
- `pnpm build` — production build
- `pnpm lint` — run ESLint

## Stack

Next.js 16 (App Router), React 19, TypeScript, Tailwind CSS 4, pnpm.

## Product: note.md

A free, minimal, markdown-native web publishing tool. Write markdown, publish, share a link. Nothing more.

### Core design principles

- **Monochrome only** — black, white, gray. No brand color. The only color comes from user content (images, syntax-highlighted code).
- **Typography-driven** — bold, modern typefaces do all the visual heavy lifting. No decorative elements, icons, or illustrations.
- **Dark mode via system preference only** — no manual toggle. Both modes are fully designed, not inverted.
- **No social mechanics** — no likes, comments, followers, analytics, notifications, feed, or algorithm. Ever.
- **Free forever** — no ads, no premium tiers, no paywalls.

### Key pages and routes

Public: `/` (landing/manifesto), `/@user/note-title` (reading view), `/@user` (author profile), `/login` (magic link input).
Authenticated: `/dashboard`, `/editor/:id`, `/trash`, `/settings`.

### Auth model

Magic link only. No passwords, no OAuth. Sign-up and login are the same flow (enter email → click link). Username chosen on first login becomes the namespace (`/@username`).

### Editor behavior

Typora-style inline live preview — markdown renders in place as you type. No toolbar, no edit/preview toggle. Auto-save continuously, no save button. Supported markdown: headings, bold, italic, links, lists, blockquotes, inline code, fenced code blocks with syntax highlighting, images, horizontal rules. Tables, task lists, footnotes, math, strikethrough are deliberately excluded.

### Publishing model

Two states only: draft and published. Publishing generates a slug from the title. Slug never changes even if title is edited later. Editing a published note updates it live immediately. Unpublishing returns to draft, URL 404s, re-publishing restores the same URL.

### Media

Images via drag-and-drop upload or external URL. YouTube/tweet URLs on their own line auto-embed. Code blocks get syntax highlighting with language auto-detection.

### Deletion

Soft delete to trash. 30-day auto-purge. Restore returns to draft state, not published.

### What this product will never build

Discovery feed, likes/reactions, comments, followers, analytics, notifications, algorithmic recommendations, ads, premium tiers, native apps, team/collaboration features, newsletters, paywalls, AI writing assistance.
