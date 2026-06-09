# Your link page — editing guide

This guide walks you through customizing **testing.html**, a single-page “links” site (like Linktree). You do not need to know how to code. You only need a text editor and a web browser.

**Files you care about:**

| File                               | What it is                                                   |
| ---------------------------------- | ------------------------------------------------------------ |
| `testing.html`                     | Your page — open this to edit everything                     |
| `profile.jpg` (or `.png`, `.webp`) | Optional profile photo — same folder as `testing.html`       |
| `fonts/`                           | Optional folder for a custom font (create it if you use one) |
| `testing-RUNBOOK.md`               | This guide                                                   |

---

## Before you start

1. **Make a copy** of `testing.html` (and the `fonts` folder if you have one) before big changes. If something breaks, you can go back.
2. **Use a plain text editor** — TextEdit (Plain Text mode), Notepad, VS Code, etc. Do not use Word or Google Docs; they add hidden formatting.
3. **Preview in a browser** — double-click `testing.html`, or drag it into Chrome, Safari, or Firefox. After each save, refresh the browser tab to see changes.

---

## What the page looks like (map)

```
┌─────────────────────────────────┐
│  [photo or YN]  ← profile image │
│  Your Name  ← title             │
│  Description...  ← subtitle     │
│                                 │
│  Website    ← link button       │
│  Listen                         │
│  Shop                           │
│  Contact                        │
│  Archive                        │
│                                 │
│  © 2026 Your Name  ← footer     │
└─────────────────────────────────┘
```

Everything inside the big card is in one HTML file. Colors and fonts are set near the top in a `<style>` block.

---

## Step 1 — Change your name and text

Open `testing.html` and scroll to the bottom (the part that looks like normal writing, not code with `{` and `}`).

| What you see                              | Change it to                                               |
| ----------------------------------------- | ---------------------------------------------------------- |
| `<title>Your Name</title>` (near the top) | Your name — this is the browser tab title                  |
| `YN` inside `<div class="avatar">`        | 1–2 letters when you are **not** using a photo (e.g. `AB`) |
| `<h1>Your Name</h1>`                      | Your display name                                          |
| Text inside `<p class="subtitle">...</p>` | Short bio or tagline                                       |
| `© 2026 Your Name` in the footer          | Your copyright line                                        |

**Tip:** Only change the words between the `>` and `<` tags. Leave the tags themselves alone.

---

## Step 1b — Profile photo (optional)

By default the page shows **initials** in a colored square. You can use a **photo** instead.

**Same folder as the page** — the easiest setup:

1. Save your photo next to `testing.html`, e.g. `profile.jpg` (`.png` and `.webp` work too).
2. In `testing.html`, find the avatar block. It looks like this:

   ```html
   <div class="avatar">
     <!-- <img src="./profile.jpg" alt=""> -->
     YN
   </div>
   ```

3. **Uncomment** the image line — remove `<!--` at the start and `-->` at the end so it becomes:

   ```html
   <img src="./profile.jpg" alt="" />
   ```

4. Make sure `src` matches your real filename (e.g. `./photo.png`).
5. You can delete the `YN` line or leave it; once the image loads, the letters are hidden automatically.
6. Save and refresh the browser.

**Serving from the same location** — `./profile.jpg` means “this file, in the same folder as the HTML page.” That works on your computer when you preview, and it works online as long as you upload the image **together with** `testing.html` and keep them in the same folder on the host.

**Subfolder (optional)** — you can also use e.g. `./images/profile.jpg` if you prefer an `images` folder beside `testing.html`. Upload that folder when you go live.

**Photo tips**

- Square or nearly square photos look best (the box crops to a square).
- Aim for at least 200×200 pixels; larger is fine.
- Keep the file reasonably small (under ~500 KB) so the page loads quickly.

**Switch back to initials** — comment out or delete the `<img ...>` line and put your letters back (e.g. `YN`).

---

## Step 2 — Edit, add, or reorder links

Links live in a list that starts with `<ul class="links">`. Each link looks like this:

```html
<li>
  <a href="https://example.com"> Website </a>
</li>
```

**Change a link**

- `href="..."` — the URL people go to when they click (must stay in quotes)
- The word on the next line (e.g. `Website`) — the label on the button

**Add a link**

Copy a whole `<li>...</li>` block, paste it above or below another link, then edit the URL and label.

**Remove a link**

Delete the entire `<li>...</li>` block for that link.

**Reorder links**

Cut a whole `<li>...</li>` block and paste it where you want it in the list. The Archive link is the same as any other — move it like the rest.

**Special URLs**

| Type                        | Example                         |
| --------------------------- | ------------------------------- |
| Website                     | `href="https://yoursite.com"`   |
| Email                       | `href="mailto:you@example.com"` |
| Archive folder on same site | `href="./archive/"`             |

---

## Step 3 — Change colors

Near the top of the file, find the block labeled **USER THEME**. Each line is one color. Use hex codes like `#ff00aa` (from a color picker) or names like `white` and `black`.

| Setting              | What it controls                                                        |
| -------------------- | ----------------------------------------------------------------------- |
| `--color-bg`         | Background behind the card                                              |
| `--color-surface`    | The main card panel                                                     |
| `--color-link`       | Link button background                                                  |
| `--color-link-hover` | Link button when hovered (desktop)                                      |
| `--color-border`     | Outlines on the card and buttons                                        |
| `--color-accent`     | Accent color (initials badge gradient start, hover border)              |
| `--color-accent-2`   | Second accent (initials badge gradient end; ignored when using a photo) |
| `--shadow`           | Drop shadow under the card — `none` removes it                          |
| `--radius`           | Corner rounding — `0` is square, `8px` is rounder                       |

**Example** — dark purple page with a gray card:

```css
--color-bg: #1a0a2e;
--color-surface: #2d2d3a;
--color-link: #3a3a4a;
--color-link-hover: #4a4a5a;
--color-border: #555566;
--color-accent: #b24bf3;
--color-accent-2: #ff6b9d;
```

Change one color at a time, save, and refresh the browser until it looks right.

---

## Step 4 — Light text or dark text

On **line 2** of the file you will see:

```html
<html lang="en" data-invert-text="1"></html>
```

Change the number:

| Value                  | Effect                     | Best when                  |
| ---------------------- | -------------------------- | -------------------------- |
| `data-invert-text="1"` | **Light** text (off-white) | Dark backgrounds           |
| `data-invert-text="0"` | **Dark** text (near-black) | Light / bright backgrounds |

If your background is pale yellow or white, use `"0"`. If your background is dark, use `"1"`.

You do **not** need to edit the guardrailed section below this — it picks readable text colors for you.

---

## Step 5 — Custom font (optional)

Skip this if you are fine with the system font.

1. Create a folder next to `testing.html` named `fonts`.
2. Put your font file inside (`.woff2` preferred; `.woff` also works).
3. Near the top, in the `@font-face` block, update:
   - `"Custom Font"` — pick a name (use the same name in step 4).
   - `./fonts/custom-font.woff2` — change to your real filename, e.g. `./fonts/MyFont.woff2`.
4. In **USER THEME**, set:
   ```css
   --font-family: "Custom Font", system-ui, sans-serif;
   ```
   Use the same name you chose in quotes.

If the font does not show up, check the filename and that the `fonts` folder sits beside `testing.html`.

---

## What not to change (unless you know why)

Below **USER THEME** there is a **GUARDRAILED** section. It keeps text readable and adds a visible focus ring when someone tabs to a link with the keyboard.

Leave these alone unless you are deliberately tuning accessibility:

- `--color-text`
- `--color-muted`
- `--color-on-accent`
- `--color-focus`

If text is hard to read, try flipping `data-invert-text` first before touching guardrailed colors.

---

## Quick troubleshooting

| Problem               | Try this                                                                                                          |
| --------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Page looks broken     | Restore your backup copy                                                                                          |
| Colors did not change | Save the file, then hard-refresh the browser (Cmd+Shift+R or Ctrl+Shift+R)                                        |
| Text hard to read     | Switch `data-invert-text` between `"1"` and `"0"`                                                                 |
| Link goes nowhere     | Check `href="..."` — URL must include `https://` for external sites                                               |
| Font missing          | Confirm `fonts` folder path and filename match the `@font-face` lines                                             |
| Broken profile image  | Check filename matches `src`, file sits beside `testing.html`, and you removed the `<!--` / `-->` comment markers |

---

## Putting the page online

`testing.html` is a static file. To publish:

1. Upload `testing.html` (rename to `index.html` if your host requires it), your profile image if you use one, any `fonts` folder, and an `archive` folder if you use the Archive link.
2. Keep the same folder structure as on your computer.
3. Your host’s docs will say how to upload — common options are Netlify drag-and-drop, GitHub Pages, or your registrar’s file manager.

For a custom domain, follow your hosting provider’s DNS steps; the HTML file itself does not change.

---

## Checklist before you share the link

- [ ] Name, subtitle, and footer updated
- [ ] Profile photo showing (or initials you want)
- [ ] Every link tested in the browser
- [ ] Colors look good on phone and desktop (resize the browser window)
- [ ] Text is easy to read (`data-invert-text` set correctly)
- [ ] Browser tab title (`<title>`) is correct

---

_Questions about this template? Keep this runbook with your HTML file so you can come back to it anytime._
