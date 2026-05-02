# Invitation Card — CLore Sdn. Bhd.

An animated digital invitation card built with vanilla HTML, CSS, and JavaScript. No build tools or dependencies required.

## Features

- Clickable envelope with animated flap opening
- Cinematic interlude overlay with expanding ring animations
- Invitation card reveal with confetti effect
- RSVP form with attendance confirmation (Accept / Decline)
- Guest name personalization via `?guest=` URL parameter
- Google Sheets integration for RSVP responses
- PIN-protected admin panel for guest list management
- Fully responsive — works on mobile and desktop
- Dark luxury theme

## Project Structure

```
invitation-card/
├── index.html       # invitation card (markup + JavaScript)
├── style.css        # all styles and animations
├── admin.html       # PIN-protected guest manager
├── RSVP.gs          # Google Apps Script for RSVP submissions
├── Code.gs          # Google Apps Script for guest list CRUD
├── public/
│   └── clore-logo.png
└── README.md
```

## Usage

Open `index.html` directly in a browser — no server or build step needed.

### Guest Name Parameter

Pass a guest name via URL to personalize the invitation:
```
index.html?guest=Dato%27%20Ahmad%20Faris
```

## Customisation

All event details are hard-coded in `index.html`. To adapt this for a different event, update the following in the card markup:

| Field | Location |
|---|---|
| Guest name | `GUEST_NAME` fallback in `<script>` |
| Event title | `.movie-title` element |
| Event label | `.event-label` element |
| Date & time | `.event-detail-row` (lines ~61–62) |
| Venue | `.event-detail-row` (line ~63) |
| RSVP deadline | `.rsvp-deadline span` |
| Company name | `.g-company`, `.admin-company`, and page `<title>` |
| Logo | `public/clore-logo.png` |

## Google Sheets Integration

### 1. RSVP Responses

1. Open your Google Sheet → **Extensions → Apps Script**
2. Paste the contents of **`RSVP.gs`** into the editor
3. Click **Deploy → New deployment → Web app**
   - **Execute as:** Me
   - **Who has access:** Anyone
4. Copy the deployment URL and paste it into `index.html` on line 108 (`RSVP_URL`)

The script will create a sheet tab named **`GuestName`** with columns:
- **A:** Name | **B:** Phone Number | **C:** Number of Guests | **D:** Status

Both "Accept" and "Unable to Attend" responses are saved.

### 2. Admin Panel / Guest List

1. Paste the contents of **`Code.gs`** into a new Apps Script project (or the same sheet)
2. Deploy as a Web app (same settings as above)
3. Copy the deployment URL and paste it into `admin.html` on line 551 (`SCRIPT_URL`)
4. Open `admin.html` in a browser and enter the PIN (default: `2026`)

The admin panel lets you add guests, copy personalized invitation links, and remove guests. The script stores guest names in a sheet tab named **`Guests`**.

## Deployment

Host the static files (`index.html`, `style.css`, `admin.html`, and the `public/` folder) on any static file server such as GitHub Pages, Vercel, or Netlify. The Apps Script URLs in `index.html` and `admin.html` are the only configuration needed.
