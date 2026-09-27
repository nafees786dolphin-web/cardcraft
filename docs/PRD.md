# CardCraft – Business Card Designer PRD

Sep 26, 2026 · @nafees

## 1. Overview

CardCraft (working name) is a free, browser-based app that lets a business professional design and download a print-ready business card in under 5 minutes, with no design skills or sign-up.

**Problem.** Consultants, sales reps and freelancers need a clean card quickly, but today's options are either too complex (Canva, Illustrator), cluttered with upsells, or produce amateur-looking results. Most users just want to type their details, pick a tasteful style, and download.

**Vision.** The fastest path from "I need a card" to a professional, print-ready file. Fewer choices, better defaults: every template looks good no matter what the user types.

**Status.** Draft for review. Scope below is a proposal; sections 9 and 10 list decisions needed before build.

## 2. Goals, non-goals and success metrics

The product succeeds if a first-time, non-technical user downloads a card they are happy to print in under 5 minutes.

**Goals**

- Card created and downloaded in under 5 minutes, first try, no instructions
- Professional output by default: no template can produce an ugly or unreadable card
- Print-ready files a local print shop or online printer accepts without rework
- Works on laptop and phone browsers, no install, no account
- Zero running cost: free to build, host and use

**Non-goals (for MVP)**

- A free-form design canvas like Canva (drag anything anywhere)
- Ordering or printing cards inside the app
- Team/brand management, logins, or cloud storage
- Digital/NFC card sharing (considered for later, section 9)

**Success metrics**

| Metric | Target | How measured |
| --- | --- | --- |
| Time to first download | Median under 5 min, 90% under 8 min | Usability test with 5–8 target users |
| Task completion | 90%+ finish without help | Usability test |
| Output quality | 80%+ rate card "would print as-is" | Post-test question |
| Print acceptance | PDF passes a print shop check (bleed, 300 DPI) | Test print at 1–2 printers |
| Ease | Average 4/5 or higher on "easy to use" | Post-test question |

## 3. Target users and personas

The primary user is an individual professional who meets clients face to face and wants to look credible, not a designer or a marketing team.

| Persona | Context | Needs most | Frustration today |
| --- | --- | --- | --- |
| Independent consultant | Solo or small practice, networking events, client meetings | Premium, understated look; logo optional | Design tools take an evening to learn |
| Sales representative | Field or B2B sales, high card volume | Speed; phone, email, LinkedIn prominent; company logo | Company cards take weeks, or none provided |
| Freelancer / small business owner | Accountant, coach, agent, designer-adjacent roles | Affordable, looks established, QR to website | Templates look generic or cheap |

**Shared traits:** low to moderate tech comfort, time-poor, often on a phone, will abandon if asked to sign up or pay before seeing a result.

## 4. User journey: the 5-minute flow

The whole app is one screen with four guided steps, a live card preview always visible, and a time budget of about 4 minutes.

| Step | What the user does | Time budget |
| --- | --- | --- |
| 0. Land | Opens the link, sees a sample card and one button: "Create my card" | 10 sec |
| 1. Your details | Fills a short form: name, job title, company, phone, email, website, LinkedIn, address (only name required) | 90 sec |
| 2. Pick a style | Taps one of 6–8 template thumbnails, each already showing their own details | 30 sec |
| 3. Personalise | Optional: upload logo, pick accent colour (8 curated swatches), font pairing (3 options), add QR code | 60 sec |
| 4. Download | Reviews front and back, chooses PDF (print) or PNG (digital), downloads | 30 sec |

**Flow rules**

- The preview updates as the user types; no "generate" button
- Steps can be revisited in any order; nothing is lost
- Progress is kept in the browser so a refresh does not wipe the form
- No sign-up, pop-up or payment at any point

## 5. Functional requirements

P0 items make up the MVP; P1 are strong candidates if time allows; P2 are later. Priorities are proposals for review.

| ID | Requirement | Priority |
| --- | --- | --- |
| F1 | Details form: name (required), title, company, phone, email, website, LinkedIn, address, tagline | P0 |
| F2 | Live preview of front (and back when used) updating on every keystroke | P0 |
| F3 | 6–8 professional templates (horizontal); switching keeps all entered data | P0 |
| F4 | Logo upload (PNG/JPG/SVG, max 5 MB), auto-scaled to fit the template's logo zone | P0 |
| F5 | Curated accent colours (8 swatches) plus one custom colour picker | P0 |
| F6 | Font pairings: 3 curated options (e.g. classic serif, modern sans, geometric) | P0 |
| F7 | Auto-fit text: long names/titles shrink within limits, warning if too long to read | P0 |
| F8 | Download print-ready PDF and high-res PNG (see section 7) | P0 |
| F9 | Double-sided cards: back side with logo, tagline or QR | P0 |
| F10 | Auto-save progress in the browser; "Start over" button | P0 |
| F11 | QR code linking to website, LinkedIn or a vCard (contact auto-saves on scan) | P1 |
| F12 | Show/hide toggles per field and icons for phone/email/web | P1 |
| F13 | Vertical card orientation | P1 |
| F14 | Regional sizes: US 3.5×2 in, EU 85×55 mm, India/Asia 90×54 mm | P1 |
| F15 | Download vCard (.vcf) file for email signatures and sharing | P2 |
| F16 | Print sheet: 10 cards on A4/Letter with crop marks for home printing | P2 |
| F17 | Save/share a design via link (encoded in URL, no server) | P2 |

## 6. Design and UX principles

Both the app and every card follow one rule: restraint. Generous white space, one accent colour, two fonts at most.

**App interface**

- Neutral palette (white, warm grey, charcoal) with a single deep accent (e.g. navy or ink blue)
- One clean sans-serif UI font; large, readable labels and inputs (16px+)
- Layout: form on the left, large preview on the right (desktop); stacked with sticky preview (mobile)
- Plain-language labels ("Your job title", not "Designation field"); helpful placeholder examples
- Accessible: WCAG AA contrast, keyboard usable, clear focus states

**Card templates (proposed set of 6–8)**

| Template | Look | Best for |
| --- | --- | --- |
| Classic | Centred name, serif, thin rule | Consultants, advisors |
| Modern Left | Left-aligned, sans, accent bar | Sales, tech |
| Monogram | Large initials on back, minimal front | Personal brands |
| Bold Band | Colour band on one edge | Sales reps, agencies |
| Split | Logo side / details side | Company-branded cards |
| Minimal Mono | Black and white only, type-led | Premium, understated |
| Corporate | Logo top, structured contact block | Established firms |
| QR Focus | QR prominent on back | Digital-first users |

**Quality guardrails:** fixed safe margins, minimum 7pt text, locked hierarchy (name > title > contacts), and colour contrast checked automatically so users cannot pick unreadable combinations.

## 7. Download and export

One click produces a file a print shop accepts; the user never has to know what "bleed" means.

| Format | Use | Spec | Priority |
| --- | --- | --- | --- |
| PDF (print) | Send to a print shop or online printer | Front and back as 2 pages, 3 mm bleed, crop marks optional, vector text, 300 DPI images | P0 |
| PNG (digital) | WhatsApp, email, LinkedIn, phone wallpaper | 1050×600 px or larger (300 DPI at US size), front and back as separate files | P0 |
| Print sheet PDF | Home/office printing on A4 or Letter | 10 cards per sheet with cut guides | P2 |
| vCard (.vcf) | Import contact into phones and email | Standard vCard 3.0 | P2 |

**Rules**

- Downloaded file names use the person's name, e.g. `Priya-Sharma-business-card.pdf`
- A short "Printing tips" note appears after download (paper weight, matte vs gloss)
- Everything is generated in the browser; no user data is uploaded anywhere
- Default size is chosen from the user's region, changeable before download

## 8. Non-functional requirements and technical approach

The app is a single web page that runs entirely in the browser, so it costs nothing to host and needs no server, database or login.

**Non-functional requirements**

| Area | Requirement |
| --- | --- |
| Performance | Loads in under 2 seconds on 4G; total page size under 1 MB |
| Devices | Latest Chrome, Safari, Edge, Firefox; desktop, tablet, phone (360px+) |
| Privacy | No accounts, no tracking of personal details, nothing leaves the device |
| Reliability | Works offline after first load (nice to have) |
| Accessibility | WCAG 2.1 AA for the app interface |
| Cost | 0 for build, hosting, domain optional |

**Proposed technical approach (no coding needed from you)**

- One self-contained HTML file (HTML, CSS, JavaScript) built by Claude
- Cards drawn as SVG so text stays sharp at any size
- Free open-source libraries for PDF export, PNG export and QR codes
- Progress saved in the browser's local storage
- Hosting options, all free: a published Claude artifact link (simplest), GitHub Pages, Netlify or Cloudflare Pages
- You can review, test and request changes in plain English; no developer tools required

## 9. Scope phasing

Proposed: build the MVP (all P0) first, test it with a few real users, then add P1 items in one quick follow-up.

| Phase | Includes | Outcome |
| --- | --- | --- |
| MVP (v1) | F1–F10: details form, live preview, 6–8 templates, logo, colours, fonts, double-sided, PDF + PNG download, auto-save | A working, downloadable card maker ready to share |
| v1.1 | F11–F14: QR code, field toggles and icons, vertical cards, regional sizes | Covers most real-world requests |
| v2 (later) | F15–F17: vCard download, print sheet, shareable design link | Convenience and repeat use |

**Out of scope**

- User accounts, saved design libraries, payments
- Free-form drag-and-drop editing or custom layouts
- In-app print ordering
- Team/company brand kits and bulk card generation
- NFC or digital card hosting pages

## 10. Risks, assumptions and open questions

**Risks**

| Risk | Impact | Mitigation |
| --- | --- | --- |
| PDF not accepted by some printers | Users must redo the file | Standard bleed and 300 DPI; test with 1–2 real printers before launch |
| Long names or many fields overflow the card | Messy, unprofessional cards | Auto-fit text, field limits, visible warnings |
| Low-quality logo uploads look blurry in print | Poor output | Warn when logo resolution is too low; recommend SVG/PNG |
| Too many options slow users down | Misses the 5-minute goal | Curated choices only; everything optional after step 1 |

**Assumptions**

- Users are happy with a curated template set rather than full design freedom
- Browser-only (no server) is acceptable, meaning designs live on the user's device
- English-only interface for MVP

**Open questions for review**

- [ ] Is "CardCraft" the name, or do you have one in mind?
- [ ] Confirm MVP scope: all P0 items, or trim/add any?
- [ ] Should QR code (F11) move into the MVP?
- [ ] Default card size: India/Asia 90×54 mm, US 3.5×2 in, or EU 85×55 mm?
- [ ] Any preferred app accent colour or style reference?
- [ ] Where should it live: Claude artifact link, or GitHub Pages/Netlify with your own link?
