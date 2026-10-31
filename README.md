# Paddock Vault — Setup Guide

Thanks for buying Paddock Vault! This guide takes you from download to a live site in about 30 minutes. No coding experience needed.

---

## Quick start

1. Open `index.html` in any browser to see the demo league.
2. Open `index.html` in a plain text editor (VS Code, Notepad, TextEdit in plain-text mode).
3. Scroll to the section marked **CONFIG — EDIT EVERYTHING HERE** near the bottom of the file.
4. Replace the demo content with your league's history.
5. Save, refresh the browser, and check how it looks.
6. Put it online for free (see "Put it online" below).

Everything you need to change is inside the `CONFIG` object. You should never need to touch the code below the line that says **ENGINE**.

---

## Editing rules (read this first)

- Text goes inside double quotes: `title: "Ten seasons in"`.
- Every item in a list is separated by a **comma**. A missing comma is the most common reason for a blank page.
- If your text contains a double quote, use curly quotes (“ ”) instead, or write `\"`.
- Numbers that are used for sorting or bars (like `debut`, `heat` and rivalry stats) must be plain numbers, **without** quotes.
- If the page goes blank after an edit, undo your last change and look for a missing comma, quote or bracket.

---

## 1. Site details — `site`

| Field | What it does |
|---|---|
| `name` | Your league's name. Shown in the header and the browser tab. |
| `tagline` | One sentence under the name. Also used when the link is shared on social media. |
| `footer` | Small text at the bottom of the page. |

## 2. Colours — `theme`

| Field | What it does |
|---|---|
| `accent` | Your main colour as a hex code, e.g. `"#E10600"`. Every glow, button and bar follows it. |
| `background` | The page background, e.g. `"#15151E"`. Dark colours work best. |

## 3. Starting-lights intro — `intro`

| Field | What it does |
|---|---|
| `enabled` | `true` to show the lights animation on load, `false` to skip it. |
| `text` | Text shown when the lights go out. |
| `skipText` | Small hint under the lights. Visitors can tap to skip. |

## 4. Top buttons — `navLinks`

The pill buttons in the top-right corner. Use them for a donation page, Discord invite, merch store or anything else.

| Field | What it does |
|---|---|
| `label` | Text on larger screens. |
| `shortLabel` | Shorter text on phones. |
| `icon` | A Font Awesome icon name, e.g. `"fa-brands fa-discord"`. Browse icons at fontawesome.com/icons. |
| `url` | Your link. If left empty, tapping the button shows a reminder message. |
| `mobile` | Set to `false` to hide the button on phones. |

To remove a button, delete its whole `{ ... }` line, including the comma.

## 5. Newsletter card — `newsletter`

| Field | What it does |
|---|---|
| `enabled` | `false` hides the card completely. |
| `title`, `text`, `placeholder`, `button` | The card's wording. |
| `success`, `successNote` | Message shown after someone signs up. |
| `invalid` | Message shown when the email address is not valid. |
| `formAction` | Leave empty for demo mode (nothing is sent). To collect real signups, paste the form URL from your email provider (Buttondown, Mailchimp, Formspree, etc.). |
| `fieldName` | The name your provider expects for the email field. Usually `"email"`. |

## 6. Header stats — `headerStats`

The small pills under the tagline, e.g. `{ value: "10", label: "seasons" }`. Add or remove as many as you like.

## 7. Interface text — `labels`

Every button, heading and hint on the site lives here, so you can reword anything or translate the whole site. Keep `{n}`, `{total}` and `{q}` where they appear, since they are filled in automatically.

---

## 8. Chapters — `chapters`

Each chapter is one era of your league. It appears as a story bubble, a full chapter card and a slide in the story viewer. You can have as many chapters as you want.

| Field | What it does |
|---|---|
| `short` | Text inside the story bubble, e.g. `"S1"`. Keep it to 3 characters or fewer. |
| `label` | Name under the bubble, e.g. `"Garage days"`. |
| `years` | Shown as a pill, e.g. `"2016–2017"`. |
| `big` | The large faded background number, e.g. `"2016"`. |
| `title` | The chapter headline. |
| `tagline` | One line under the headline. |
| `body` | The main paragraph. |
| `specs` | Small info chips: `{ label: "Format", value: "30-minute sprints" }`. |
| `stats` | Big number cards: `{ v: "12", l: "drivers on the first grid" }`. Two look best. |
| `list` | A short list: `title`, then `items` as `["2016", "Lena Voss"]` pairs. `empty` is shown if there are no items. |
| `fact` | The "Did you know?" box. Leave as `""` to hide it. |

Each story slide plays for 8 seconds.

## 9. Hall of fame — `people`

| Field | What it does |
|---|---|
| `id` | A unique short name with no spaces, e.g. `"voss"`. |
| `first`, `last` | First and last name. |
| `nick` | Nickname, shown in quotes on the driver's profile. |
| `meta` | Nation or any short detail. |
| `years` | Active years, e.g. `"2016–2021"`. |
| `debut` | Debut year as a number (no quotes). Used for "By debut" sorting. |
| `helmet` | Two colours for the helmet icon: `["#E10600", "#ffffff"]`. |
| `honours` | Championship years as numbers: `[2016, 2018]`. The title count is worked out automatically. Use `[]` for none. |
| `stats` | Three mini stats: `["41", "Wins"]`. |
| `tags` | Teams or groups, shown on the profile. |
| `quote` | Optional: `{ text: "...", ctx: "Where it was said" }`. |
| `moment` | Optional: shown as "Defining moment" if there is no quote. |
| `bio` | A short biography. |

Each driver needs either a `quote` or a `moment` (or neither). If both are filled in, the quote is shown.

**Search tips for your visitors:** names, nicknames, nations, teams and title years all match as typed. Typing `2` or `2 titles` finds drivers with exactly two titles, and `2+` finds drivers with two or more.

## 10. Rivalries — `rivalries`

| Field | What it does |
|---|---|
| `years` | When the rivalry happened. |
| `heat` | How intense it was, from 0 to 10 (number, no quotes). |
| `title` | The rivalry's name. |
| `a`, `b` | The two drivers: `{ first: "Lena", last: "Voss", team: "Voss Motorsport" }`. |
| `context` | One sentence of background. |
| `stats` | Head-to-head bars: `["Wins", 22, 19]`. The two numbers must be plain numbers. |
| `flash` | The flashpoint moment. |
| `outcome` | How it ended. |

---

## Deep links

You can link straight to a section by adding these to the end of your site address:

- `#chapters`, `#hall-of-fame`, `#rivalries`
- `#chapter-3` opens chapter 3 directly. The "Share chapter" button copies these links for you.

---

## Put it online (free)

**GitHub Pages**
1. Create a free account at github.com.
2. Create a new public repository, e.g. `league-history`.
3. Click **Add file → Upload files** and upload `index.html`.
4. Go to **Settings → Pages**, choose the `main` branch and save.
5. After a minute or two, your site is live at `yourusername.github.io/league-history`.

**Netlify Drop**
1. Put `index.html` in a folder.
2. Drag the folder onto app.netlify.com/drop. Your site is live instantly.

Any static web host works, since the whole site is one file.

---

## Good to know

- The site needs an internet connection to load its fonts, icons and styling.
- It works on phones, tablets and desktops, with swipe gestures on touch screens.
- Some browsers show a developer warning in the console about the styling library. Visitors never see it, and it doesn't affect the site.

## Content and rights

The demo league and drivers are fictional. You are responsible for the content you add. Facts about real events are generally fine, but official logos, team branding and photos usually require permission.

## Support

Questions or bugs? Contact me through my Gumroad page: https://mahirfaisali.gumroad.com
