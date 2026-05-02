# Invitation Card — Nexora Holdings

An animated digital invitation card built with vanilla HTML, CSS, and JavaScript. No build tools or dependencies required.

## Features

- Clickable envelope with animated flap opening
- Cinematic interlude overlay with expanding ring animations
- Invitation card reveal with confetti effect
- RSVP form with attendance confirmation
- Fully responsive — works on mobile and desktop
- Dark luxury theme

## Project Structure

```
invitation-card/
├── index.html   # markup and JavaScript
├── style.css    # all styles and animations
└── README.md
```

## Usage

Open `index.html` directly in a browser — no server or build step needed.

## Customisation

All event details are hard-coded in `index.html`. To adapt this for a different event, update the following in the card markup:

| Field | Location |
|---|---|
| Guest name | `.guest-name` element |
| Event title | `.event-name` element |
| Date & time | first `.detail-value` |
| Venue | second `.detail-value` |
| Dress code | third `.detail-value` |
| RSVP deadline | `.rsvp-deadline span` |
| Contact info | `.card-footer` |
| Company name | `.company-label`, `.g-company`, and page `<title>` |

## Deployment

Host the two files (`index.html` + `style.css`) on any static file server such as GitHub Pages or Vercel. No environment variables or backend required.
