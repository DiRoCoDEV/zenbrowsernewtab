# Zen New Tab

A simple, single-file “new tab” page with:

- Glassmorphism UI over a radial gradient background
- Smart greeting based on the current time
- Live clock (24h)
- URL/search bar with history suggestions stored in `localStorage`
- Basic navigation rules:
  - If the query looks like a domain (contains `.` and no spaces) it navigates to `https://<query>`
  - If it starts with `http`, it navigates directly
  - Otherwise it searches via Google

## Files

- `newtab.html` — the main new tab page (HTML/CSS/JS)
- `zen-browser-dark.svg` — favicon/icon used by `newtab.html`

## How it works

1. **Language detection**: uses `navigator.language` (two-letter prefix) to pick greeting + placeholder text.
2. **Greeting**: chooses a message based on local hour (morning/afternoon/evening).
3. **Clock**: updates every second using `toLocaleTimeString`.
4. **History**:
   - Stored under `localStorage` key: `zen_history`
   - Keeps up to 10 entries
   - Displayed in a `<datalist>` under the input
5. **Navigation**:
   - Submitting the form redirects the browser based on the query format.

## Usage

This is intended for **Zen Browser**.

### Setup

1. Copy `newtab.html` into Zen Browser’s new tab page location (or configure Zen Browser to load it—depending on your Zen Browser version).
2. Keep `zen-browser-dark.svg` next to `newtab.html` so the favicon loads correctly.



## Customization

- **Greetings & placeholder**: edit the `i18n` object inside `newtab.html`.
- **Search provider**: replace the Google URL in the submit handler.
- **History limit**: change `history.slice(0, 10)`.
- **Time format / locale**: edit `toLocaleTimeString('es-ES', { ... })`.

