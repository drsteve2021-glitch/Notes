# Inkwell — Notes App

A clean, browser-based notes app with create, edit, and delete functionality, plus user accounts. All data is stored in the browser, so no backend or installation is required.

Built for the KGTS Tech Task (Task 1 + Bonus).

**Live demo:** [your-link-here]

---

## Features

**Core (Task 1)**
- Create notes with a title and body.
- Edit any note in place.
- Delete notes (with a confirmation step).
- Search notes by title or content.
- All notes are saved in the browser's **localStorage**, so they persist across page refreshes.

**Bonus (Auth + per-user storage)**
- User registration and login.
- Logout, with automatic session resume on reload.
- Each user's notes are stored separately, so accounts never see each other's notes.

**Extra polish**
- Pin important notes to the top.
- "Time ago" timestamps on each note.
- Helpful empty states (no notes yet / no search matches).
- Responsive layout that works on phone and desktop.

---

## How to Run

No installation or build step required — it's a single self-contained HTML file.

1. Open `index.html` in any modern browser, **or**
2. Visit the live link above.

Then register an account and start adding notes.

---

## How It Works

The app uses a simple, consistent pattern for managing state:

The logged-in user's notes live in a single JavaScript array (`notes`), which is the **single source of truth**. Every action — add, edit, delete, pin — follows the same three steps:

1. Change the `notes` array.
2. Call `persistNotes()` to save it to localStorage.
3. Call `render()` to repaint the screen from the array.

### Storage Model

The app uses three localStorage keys:

- `inkwell_users` — a map of `{ username: passwordHash }` for all registered accounts.
- `inkwell_notes_<username>` — the notes array for each individual user.
- `inkwell_session` — the currently logged-in username, used to resume a session on reload.

Namespacing the notes by username is what keeps each account's data separate.

---

## Known Limitation

The authentication here is **client-side only**. Users and notes are stored in the browser's localStorage, not on a real server, and the password is only lightly obfuscated — so this is **not genuinely secure** and is not meant for real private data. It demonstrates the login/registration flow and per-user data separation on a static-hosted site.

The natural next step for a production version would be a real backend such as **Firebase** or **Supabase**, providing proper authentication and a shared database accessible from any device.

---

## Tech Stack

- **HTML / CSS / JavaScript** — no frameworks, no dependencies.
- **localStorage** for data persistence.

---

## Author

 Steve B — First-year B.Tech, IIT Kharagpur.
