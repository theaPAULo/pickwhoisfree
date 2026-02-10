# PickWho Website â Project Notes

**Last updated:** February 9, 2026
**Owner:** Mike (badformyback@gmail.com)
**Live site:** https://pickwhoisfree.com
**GitHub repo:** https://github.com/theaPAULo/pickwhoisfree
**Hosting:** Vercel (auto-deploys from main branch)

---

## What is PickWho?

PickWho is a **free-to-play sports prediction app** â the free alternative to big gambling. Users pick winners across sports every week with no deposits, no losses, and no predatory mechanics. Just fans competing for fun and real prizes.

- **Company:** Soni Digital LLC
- **App Store:** https://apps.apple.com/app/id6755406814
- **Google Play:** https://play.google.com/store/apps/details?id=com.startwho.pickwho

---

## Website Structure

The site is a simple static HTML site deployed on Vercel via GitHub.

### Files in the repo:

| File | Description |
|------|-------------|
| `index.html` | Main homepage (~334 lines) |
| `sponsors/index.html` | Sponsors landing page with tier cards (~726 lines) |
| `demo.mp4` | App demo video (402KB, 400px wide, CRF 30, compressed from .mov) |
| `SESSION_NOTES.md` | This file |

### Pages:

1. **Homepage** (`pickwhoisfree.com`)
   - Hero with PICKWHO logo + teal checkmark
   - "The Free Alternative to Big Gambling" tagline
   - App Store + Google Play download buttons
   - "Sports Should Be Fun, Not Predatory" mission section
   - "See It In Action" section with autoplay/muted/looping demo video
   - "Support the Mission" CTA linking to sponsors page
   - Footer: Â© 2026 PickWho Â· Soni Digital LLC

2. **Sponsors page** (`pickwhoisfree.com/sponsors`)
   - Hero with "Support the Alternative to Big Gambling"
   - Three sponsorship tier cards:
     - **Special Thanks** â $10 (name, social media, brand description)
     - **Powered By** â $25 (everything in Special Thanks + leaderboard branding + weekly placement)
     - **Named Contest** â $50 (everything in Powered By + contest named after brand + ad shown 50% of time + funds that week's prize)
   - Contact section with mailto link to info@pickwhoisfree.com
   - Includes extensive print/PDF styles (@media print) for generating PDF sponsor packets

---

## Brand / Design System

- **Primary color (teal):** #00E6CA (`--teal-primary`)
- **Teal dark:** #00B89E
- **Teal light:** #33FFDD
- **Dark navy background:** #0A1E1B (`--dark-navy`)
- **Dark teal gray:** #132E2A
- **Light teal gray:** #1B3D37
- **Gold (champion tier):** #FFD700
- **Text primary:** #FFFFFF
- **Text secondary:** #B0BEC5
- **Text disabled:** #607D8B
- **Font:** Inter (weights: 400, 500, 600, 700, 900) via Google Fonts
- **Style:** Dark gradient backgrounds with subtle animated teal glows, rounded corners (12-24px), glass-morphism cards

---

## Email Setup

- **Email:** info@pickwhoisfree.com
- **Service:** ImprovMX (free email forwarding)
- **Forwards to:** startwhofantasy@gmail.com
- **ImprovMX account login:** startwhofantasy@gmail.com
- **ImprovMX dashboard:** https://app.improvmx.com
- **Status:** Active and working (as of Feb 9, 2026)
- **MX Records:** mx1.improvmx.com (priority 10) and mx2.improvmx.com (priority 20)
- **Important:** info@pickwhoisfree.com is a forwarding alias, NOT a mailbox. Emails arrive in the startwhofantasy@gmail.com inbox. To reply AS info@pickwhoisfree.com, either upgrade ImprovMX to Premium ($9/month for SMTP) or set up a "Send mail as" alias in Gmail settings.

---

## Domain & DNS

- **Domain:** pickwhoisfree.com
- **DNS managed via:** (check domain registrar â likely Namecheap or similar)
- **Vercel DNS:** Configured for website hosting
- **MX Records:** Pointing to ImprovMX for email forwarding

---

## Deployment

- **Platform:** Vercel
- **Auto-deploy:** Yes, from `main` branch on GitHub
- **Typical deploy time:** ~15 seconds after push
- **No build step** â it's static HTML, served directly

---

## How to Edit the Site

The site is edited directly through GitHub's web editor since the local folder is not a git repository (it's a synced copy). The workflow:

1. Navigate to the file on GitHub (e.g., `https://github.com/theaPAULo/pickwhoisfree/edit/main/index.html`)
2. Make edits in the CodeMirror 6 (CM6) editor
3. Click "Commit changes..." and commit to main
4. Vercel auto-deploys within ~15 seconds

### Important CM6 Editor Notes (for Claude agents editing via browser):

- GitHub uses **CodeMirror 6**, NOT CodeMirror 5
- Access editor via `.cm-editor` and `.cm-content` selectors (NOT `.CodeMirror`)
- To access the EditorView programmatically: `document.querySelector('.cm-content').cmTile.view`
- For targeted find-and-replace, use CM6's `view.dispatch({ changes: { from, to, insert } })`
- For full file replacement: `document.execCommand('selectAll')` then `document.execCommand('insertText', false, newContent)`
- Keyboard shortcuts like Cmd+H do NOT work in the browser â they type characters instead
- The editor virtualizes content â only visible lines exist in the DOM. Use `view.state.doc` to access the full document.

---

## CSS Class Naming Note

The "Support the Mission" section on the homepage uses `.support-cta`, `.support-box`, and `.support-link` class names. These were originally `.sponsor-cta`, `.sponsor-box`, `.sponsor-link` but were renamed because **ad blockers** were hiding elements with "sponsor" in the class name. Do NOT rename these back to "sponsor-*".

---

## Completed Work (Chronological)

1. Created the initial homepage (index.html) with hero, mission section, app store links
2. Created the sponsors landing page (sponsors/index.html) with three tier cards
3. Generated a PDF version of the sponsor page for sharing
4. Deployed the site to Vercel via GitHub
5. Set up DNS records for email forwarding (MX records pointing to ImprovMX)
6. Various UI fixes: spacing, mobile logo sizing, navigation, font weights
7. Replaced "How It Works" step cards with an autoplay demo video section
8. Converted .mov video to compressed .mp4 (402KB, 400px wide, CRF 30)
9. Fixed ad blocker issue by renaming `.sponsor-*` CSS classes to `.support-*`
10. Changed nav link colors to white (#FFFFFF) on both pages (was `var(--text-secondary)` / #B0BEC5)
11. Set up ImprovMX account and configured info@pickwhoisfree.com â startwhofantasy@gmail.com forwarding

---

## Known Issues / Future Considerations

- The Google Play link is set but the app listing may still be in review/setup
- No favicon is set up yet
- No meta tags for SEO or social media sharing (Open Graph, Twitter cards)
- No analytics tracking (Google Analytics, Plausible, etc.)
- To reply as info@pickwhoisfree.com, need to either upgrade ImprovMX or configure Gmail "Send mail as"
- The sponsors page contact section references info@pickwhoisfree.com â this is now working
