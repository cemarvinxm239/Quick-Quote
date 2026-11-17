# Quick Quote — quotes & invoices, built in your own Claude

Fast, simple quotes and invoices for makers, trades and side businesses. Works on your phone at a craft show or on your computer at home. Your data stays private in your own Claude account.

## What you need

- **A paid Claude plan** — Pro, Max, Team or Enterprise. Quick Quote saves your quotes and invoices in your Claude account, and that saved-data feature isn't part of the free plan. (On the free plan the app still opens, but it can only save in one browser on one device.)
- **Code execution and file creation** switched on in Claude's **Settings → Capabilities** (on Team and Enterprise, your admin controls this).
- Claude on the web, the desktop app, or your phone's web browser.

## Start here

1. **Download and unzip** `Quick-Quote-v1.0.zip`. Inside are two files: `QUICK-QUOTE.md` (this guide) and `quick-quote.html` (the app).
2. Open a **new chat** in Claude (claude.ai or the Claude app).
3. **Attach both files** to the chat.
4. Type: **Build my Quick Quote**

Claude will ask you to describe your business in your own words — as much or as little as you like — and suggest a setup to match. You'll adjust it together, then Claude builds your app and gives you a link. About five minutes.

**Using it day to day.** Your app opens straight to two big buttons — **+ New quote** and **+ New invoice** — with your recent quotes and invoices underneath (tap one to open it, or turn a quote into an invoice). To get to it fast:

- **In Claude:** it's pinned in your sidebar.
- **On your computer:** open the link and bookmark it.
- **On your phone:** open the link in your browser and choose **Add to Home Screen** — it gets its own icon, like an app.

Stay signed in to Claude in that browser — that's what keeps your quotes private to you and the same on every device.

**Got a new version later?** Attach the new files in a chat and type **Update my Quick Quote**. Your quotes, invoices and settings are kept.

---

## Instructions for Claude

You are setting up **Quick Quote**, a finished, tested web app, in the user's own Claude account. Follow these steps in order. Keep your messages short, warm and free of jargon — the user is a small-business owner, not a developer.

### Ground rules

- `quick-quote.html` is the complete app. **Do not rewrite, restyle, shorten or "improve" it**, and never retype or summarize its code.
- The **only** change you make is replacing the marker `/*@@STARTER@@*/{}` (it appears exactly once) with the user's starter settings (see *Starter settings* below).
- If `quick-quote.html` isn't attached, ask the user to attach it and stop there.
- Quick Quote is designed for **paid Claude plans** (Pro, Max, Team, Enterprise), which can save app data to the user's account. If the user says they're on the free plan, or saving can't be switched on in Step 3, tell them plainly before they rely on it: the app will work, but quotes save only in that one browser, won't appear on their other devices, and can be lost if browser data is cleared — so they should download backups often. Let them decide whether to go ahead.
- Don't promise tax or legal accuracy. When you suggest a tax rate, say it's a starting point to check with their state or local tax office.

### Step 1 — Open with one warm, open question

This should feel like talking with someone who knows small businesses, not filling in a form. Open with something like:

> Let's get your Quick Quote set up — I'll do most of the work. **What's your business called, and tell me about it in your own words:** what you do or make, where you work or sell, and anything about how you price things. As much or as little as you like.

Then let them talk. Ask at most one gentle follow-up if something important is missing (usually *where* they do business, which decides sales tax, or the business name). If they give you very little, work with what you have.

### Step 2 — Do the legwork, then propose a setup

From what they told you, work out what kind of business it is and what it usually needs on a quote. Then:

- **Sales tax.** If you can search the web, look up the sales tax for where they do business, broken into its pieces (state, county or city, any regional add-on), and note the source. If you can't search, ask them for the rate. If the kind of business they run often isn't taxed, or they sell mostly online across state lines, ask rather than assume.
- **Products & services.** Suggest the 4–8 things a business like theirs most often puts on a quote — the services, products, fees and adjustments that fit their trade. A plumber might get labor, a trip charge, an evening/weekend rate and common parts; a laser engraver might get engraving time per piece, setup fees, blanks and a volume discount; a baker might get cakes by size, delivery and a rush fee.
- **Prices.** Use any prices they gave you. **Don't invent prices** for the rest — show those as "your price?" and leave them blank if they don't fill them in. Blank items still appear in their list; they type the price each time or set it later in Settings.

Map each item onto one of these types:

| They say… | Item `type` | Fields to fill |
|---|---|---|
| a price each ("$12 per mug", "$4.50 per foot") | `each` | `price`; `unit` if not "each" (e.g. `"ft"`, `"set"`) |
| an hourly charge, billed by the hour ("$85/hr labor") | `hours` | `rate` (or leave `""` to use `laborRate`), `hours` default (usually `"1"`) |
| time per piece ("3 minutes a piece at $60/hr") | `time` | `rate` (or `""`), `minutes`, `handling` (extra minutes per piece, `"0"` if none) |
| a fixed fee ("$45 trip charge", "$25 setup") | `flat` | `price` (negative for a fixed discount) |
| a percentage up or down ("rush +25%", "senior −10%") | `pct` | `pct` (e.g. `"25"` or `"-10"`) |

- Give each item a short `name` (shown in their dropdown); add a `desc` only if the customer-facing wording should differ.
- "Parts at cost" or "materials vary" → an `each` or `flat` item with `price: ""`.
- If they mention one hourly rate for all their time, put it in `laborRate` and leave item `rate`s as `""`.

**Propose the setup in one short, friendly message** — about 150 words, easy to scan on a phone:

- one sentence on what you understood about their business;
- the tax location and rate in one line (with "please double-check this with your state's tax office" and a source link);
- their products & services as a short list, with their prices or "price to add";
- one line: *"Nothing here is set in stone — you can rename, delete or add anything later."*

**End with one open invitation, not a list of questions.** This is the moment they can shape their starting point, so make it easy to either refine or go. Don't ask for prices, percentages or other details one by one — they can fill those in from the app's getting-started screen, which opens right after setup. Too many questions in one message get skipped.

In the **same message**, ask permission for the three things the app needs — it was written by someone else, so they decide:

> Your app also needs three permissions to work fully: **save** your quotes and invoices privately in your own Claude account (no one else can see them), **know it's you** so it opens your own data on any device, and **download files** so you can save PDFs and spreadsheets.
>
> **Before I build it — how close is this?** Add, remove or rename anything, share prices you know, or tell me more about how you work. The more I know, the better your starting point. If it looks good and the permissions are OK, just say **go**.

Adjust together for as long as they like — it's a conversation. After each change, show only what changed and repeat the "just say **go**" line. When they say go (or "looks good"), go on to Step 3 without asking again. If they're happy with the setup but say no to the permissions, build it anyway and skip the permissions step (see Step 3).

### Step 3 — Publish their app

1. **Create a new artifact (page)** from the attached `quick-quote.html`, titled `"<Business name> Quick Quote"` (or `"Quick Quote"` if no name). Prefer publishing the file itself rather than pasting its content.
2. **Fill in the starter settings:** replace `/*@@STARTER@@*/{}` with the JSON object from Step 2 (for example with an edit-in-place tool on the new artifact). Valid JSON only — the replacement must start with `{` and end with `}`.
3. **Switch on the permissions they agreed to in Step 2:** declare exactly `{"db": {}, "user": {}, "downloads": {}}` — nothing more. If they said no, skip this and tell them the app will still open but will only save in that one browser and can't download PDFs; they can ask you to switch them on later.

4. **Pin it to their sidebar** on claude.ai (pin the artifact) so they can always find it in Claude.

Do steps 1–3 one after another, not at the same time — each step changes the page, so each must use the latest version returned by the step before it. If anything fails, see *Troubleshooting* — don't improvise a different app.

### Step 4 — Hand it over

Give them the link (or point to the card), then these next steps, briefly:

1. **Open it.** The welcome screen is already filled in from our chat — check it and tap **Start**.
2. **Make it yours** in **Settings**: add your logo, colors, and how customers can pay you (payment link, Venmo, etc.).
3. **Try it:** tap **+ New → Quote**, add a couple of their products or services, then **Save PDF**. If they mentioned taking deposits, tell them it's a per-quote choice: tick **Ask for a deposit** on the quotes that need one (their usual percent fills in).
4. **Keep it handy:** it's pinned in their Claude sidebar. On a computer, bookmark the link. On a phone, open the link in the browser and choose **Add to Home Screen** (Safari: Share button; Chrome: ⋮ menu) so it gets its own icon. They need to stay signed in to Claude in that browser.
5. **Back it up** once you're set up: **Settings → Your data → Download full backup**.

Explain what to expect: until their first quote, the app opens with a **getting-started screen** — three tiles for their products & services, sales tax and making it theirs. Tiles we already started show **Set up · Review & edit**; ask them to open each one and check it, and to add any prices left blank, and remind them that everything we set up is just a head start: in **Settings → Products & services**, the **×** removes an item and **+ Add a product or service** adds one, and on any quote they can edit, remove or reorder lines, or add a blank line for one-offs. After their first quote, it opens straight to **+ New quote** and **+ New invoice**, with recent work underneath — that's the everyday screen. Close with one line: they can come back to this chat anytime to change their setup or ask how something works.

### Updating to a new version ("Update my Quick Quote")

1. Find their existing Quick Quote artifact (list their artifacts; the title ends in "Quick Quote"). If there are several, ask which one.
2. Republish the new `quick-quote.html` **to that same artifact**. Their quotes, invoices and settings live in the page's own storage and are kept. Leave the starter marker as `{}` — their saved settings already exist.
3. Make sure the capabilities are still `{"db": {}, "user": {}, "downloads": {}}`. Pin it to their sidebar if it isn't already.
4. Tell them it's updated and to suggest downloading a fresh backup.

### Starter settings reference

Every key is optional. Unknown keys are ignored. Example:

```json
{
  "bizName": "Olson Plumbing",
  "contact": "Springfield, IL · (217) 555-0142 · olsonplumbing@example.com",
  "currency": "$",
  "laborRate": 95,
  "taxDefaultMode": "added",
  "taxLocations": [
    {"name": "Springfield", "taxShip": false, "lines": [
      {"name": "State", "rate": "6.25"},
      {"name": "City", "rate": "2.5"}
    ]}
  ],
  "items": [
    {"name": "Labor (hourly)", "type": "hours", "rate": "", "hours": "1"},
    {"name": "Trip charge", "type": "flat", "price": "45"},
    {"name": "Evening / weekend rate (+50%)", "desc": "Evening / weekend rate", "type": "pct", "pct": "50"},
    {"name": "Copper union", "type": "each", "price": "5"},
    {"name": "Copper pipe (per ft)", "type": "each", "price": "4.50", "unit": "ft"}
  ],
  "payMethods": "Cash, Card, Check, Venmo",
  "trackPayments": false
}
```

| Key | Meaning |
|---|---|
| `bizName`, `tagline`, `contact`, `footerNote`, `taxId` | Text on their PDFs. `taxId` only if they mention a tax/VAT ID. |
| `currency` | Symbol, e.g. `"$"`, `"£"`, `"€"`. |
| `laborRate` | Their standard hourly rate (number), used by hourly/time items with `rate: ""`. |
| `taxDefaultMode` | `"added"` (tax on top), `"included"` (prices already include tax) or `"none"` (they don't collect tax). |
| `taxLocations` | Places they sell, each with `name`, `taxShip` (true if shipping is taxed there) and `lines` (`name` + `rate` in percent). The first is the default. |
| `items` | Their products & services — see the table in Step 2. |
| `payMethods` | Comma-separated payment methods they accept. |
| `payInstructions`, `payLink` | How to pay (printed on invoices); a payment URL (printed as a tappable link and QR code). |
| `yearPrefix` | `true` to put the year in front of numbers (Q-26-001 → invoice 26-001), starting again at 001 each January. Only if they ask for it. |
| `depositPct` | Their usual deposit percent. It is **never added automatically** — it pre-fills when they tick "Ask for a deposit" on a quote. |
| `trackPayments` | `true` if they want to record payments against invoices by hand; default `false`. |
| `numberStyle`, `quotePrefix`, `invoicePrefix`, `startNumber` | Numbering. Defaults: `"linked"`, `"Q-"`, `""`, `1001` (quote Q-1001 becomes invoice 1001). Use `"separate"` if they say their country requires gap-free invoice numbers. |
| `validDays`, `dueDays`, `terms`, `invoiceTerms` | Quote validity, invoice due days, default notes. |

### Troubleshooting

- **You can't create artifacts / pages here:** ask the user to switch on **Code execution and file creation** in **Settings → Capabilities** (on Team or Enterprise, their admin controls it), then try again in a new message. If it still doesn't work, suggest claude.ai in a web browser or the desktop app.
- **The capabilities can't be switched on** (often because the account is on the free plan): the app still works, but saves only in that browser — it shows a "Saving on this device only" note — and may not be able to download PDFs. Tell the user plainly, and that a paid plan fixes it; after upgrading, they can ask you to switch the permissions on.
- **"The PDF tool did not load":** the page loads its PDF and QR tools from jsDelivr (cdn.jsdelivr.net). A blocked or very slow connection stops PDFs; reloading on a good connection fixes it. The page also checks those two files against fixed fingerprints (integrity hashes); if a copy ever doesn't match, the browser refuses to run it and PDFs stop — that's the safety check working, not a bug in their setup.
- **They want to change their products & services later:** they can do it in **Settings → Products & services**, or tell you what to change and you can walk them through it.

---

*Quick Quote v1.0 · Made by Energy Etch LLC, which also makes Scan-n-Pay (an optional payment-link app mentioned once in Settings — Quick Quote works with any payment link). Uses jsPDF and qrcode-generator (both MIT-licensed), loaded from jsDelivr with integrity checks, so the browser refuses any copy that has been altered. Your quotes and invoices are stored privately in your own Claude account — nobody else, including the maker, can see them.*
