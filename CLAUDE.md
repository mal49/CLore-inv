# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-file animated digital invitation card (`index.html`). No build tools, no package manager, no framework — just vanilla HTML, CSS, and JavaScript in one self-contained file.

Open `index.html` directly in a browser to run it. No server or build step required.

## Architecture

Everything lives in `index.html` (~240 lines):

- **Lines 2–66**: Embedded `<style>` — dark luxury theme with CSS custom properties (`--font-sans`, `--font-serif`), keyframe animations (twinkle, shimmer, rise-up, confetti), and component styles.
- **Lines 68–164**: HTML markup — star particle background (40 elements), envelope component, invitation card, RSVP form, and success screen.
- **Lines 166–239**: Embedded `<script>` — four interaction functions with no external dependencies.

### UI State Model

Visibility is managed by toggling CSS classes on DOM elements:

| Class | Effect |
|---|---|
| `.open` | Animates envelope flap open |
| `.hidden` | Hides seal element |
| `.visible` | Shows RSVP form |

### Key JavaScript Functions

- `openEnvelope()` — multi-step envelope open sequence, calls `spawnConfetti()`
- `spawnConfetti()` — spawns 28 animated confetti particles via `requestAnimationFrame`
- `showForm()` / `showDecline()` — toggle between Accept/Decline states
- `showSuccess()` — replaces RSVP form with confirmation screen

## Content

All event details are hard-coded in the HTML. To customize for a different event, edit the relevant text nodes in the card markup section (lines ~90–160): guest name, event title, date/time/venue, RSVP deadline, and contact info.

## Deployment

Host the single `index.html` on any static file server (GitHub Pages, Vercel static, etc.). No environment variables or backend required.
