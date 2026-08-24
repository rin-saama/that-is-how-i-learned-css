# CSS Practice: Box Model + Selectors

## Rules for every task

**Allowed CSS you can use:**
- Selectors: universal (`*`), type (`div`, `p`, `a`...), class (`.name`), ID (`#name`), attribute (`[type="text"]`), grouping (`.a, .b, #c`)
- Box model properties: `width`, `height`, `padding`, `border`, `margin`, `box-sizing`
- Display values: `inline`, `inline-block`, `block`

**Not allowed (even if you already know them):**
- Descendant/child/sibling selectors (`.card p`, `.card > p`, `.card + p`)
- Pseudo-classes/elements (`:hover`, `::before`, `:first-child`)
- Flexbox, Grid, `position`, `float`

This constraint is intentional — without descendant selectors, every element you want to style individually needs its **own** class, ID, or attribute. That's the actual challenge here: thinking about *how* you'll reach an element, not just what style to give it.

Build each task as a separate HTML file with its own CSS (inline `<style>` or linked file, your choice). Use a browser + DevTools to check your box model math as you go.

---

## Task 1: Profile Card — Box Model Basics

**Goal:** Build a single profile card and get comfortable with the four box areas (content, padding, border, margin) and the two `box-sizing` modes.

**HTML must include:**
- One outer container with `id="profile-card"`
- An `<img>` inside it (any placeholder image or a colored `<div>` if you don't have one)
- An `<h2>` for a name
- A `<p>` for a short bio
- A `<span class="tag" data-role="student">Learning CSS</span>` at the bottom

**CSS requirements:**
1. Style `#profile-card` using the **ID selector**: give it a `width`, `padding`, and a visible `border`.
2. Set `#profile-card` to `box-sizing: content-box`.
3. Style the `<img>` using the **type selector**: give it its own `width`, `padding`, and `border` — different colors from the card, so you can visually tell the two boxes apart.
4. Style `.tag` using the **class selector** and give it `box-sizing: border-box`.
5. Style `[data-role="student"]` using the **attribute selector** — add a distinct `background` or `border` color, separate from `.tag`. (Both rules will apply to the same element — that's intentional; notice which properties "win.")

**Challenge question to answer in a code comment:**
Your `#profile-card` is `content-box` with `width: 300px`, `padding: 20px`, `border: 5px solid`. What is its actual total rendered width? Write the math out, then confirm it in DevTools.

---

## Task 2: Inline vs. Inline-Block Button Row

**Goal:** Prove to yourself, visually, why `inline` elements ignore `width`/`height`/vertical `margin`, and `inline-block` doesn't.

**HTML must include:**
- A row of four `<a href="#">` elements acting as buttons, with the classes: `.btn-default`, `.btn-a`, `.btn-a`, `.btn-b` (yes, two elements share `.btn-a`)

**CSS requirements:**
1. Use the **universal selector** to set `box-sizing: border-box` on everything (this is the one time `*` is allowed — as a global reset).
2. Style `.btn-default` (**class selector**) with a `width`, `height`, `padding`, and `border` — but do **not** change its `display`. Observe that width/height are ignored.
3. Use a **grouping selector** to give `.btn-a` and `.btn-b` shared base styling in one rule (`padding`, `border`, `margin`).
4. Then, separately, give `.btn-a` (on its own) `display: inline-block` plus an explicit `width` and `height`.
5. Leave `.btn-b` as-is (still inline) for comparison.

**Challenge question to answer in a code comment:**
Both `.btn-a` elements got the same class rules. Are they identical on the page? Why or why not — what's different between them and how they were declared?

---

## Task 3: Attribute-Only Contact Form

**Goal:** Style a form almost entirely through **attribute selectors**, since form inputs naturally carry useful attributes (`type`, `required`, `placeholder`).

**HTML must include:**
- A `<form>` with:
    - `<input type="text" placeholder="Your name">`
    - `<input type="email" placeholder="Your email" required>`
    - `<textarea placeholder="Your message"></textarea>`
    - `<input type="submit" value="Send">`

**CSS requirements:**
1. Style `input[type="text"]` and `input[type="email"]` using a **grouped attribute selector** rule — shared `padding`, `border`, `width`, `box-sizing: border-box`.
2. Add a **separate** rule for `input[required]` (attribute selector, presence-only, no value needed) that adds something extra — e.g. a thicker or different-colored `border`. (This will stack on top of rule 1 for the email field — notice both apply.)
3. Style `input[type="submit"]` on its own — different `padding`, `border`, `margin`, and a `background-color`.
4. Style `textarea` using the **type selector** — give it a fixed `width`, `height`, and `padding`, and explicitly set `box-sizing: border-box`.

**Challenge question to answer in a code comment:**
Why did the `<textarea>` need `box-sizing: border-box` specifically pointed out here, if you already reset it globally in Task 2's `*` rule? (Hint: is this the same file/page as Task 2?)

---

## Task 4: Tag List with ID + Class + Attribute Together

**Goal:** Practice deciding *which* selector type is the right tool for a given job, in one layout.

**HTML must include:**
- A container `<div id="tag-list">`
- Five `<span>` elements inside it, all with `class="tag"`, but each with a different attribute:
    - `data-type="new"`
    - `data-type="sale"`
    - `data-type="sale"`
    - `data-type="limited"`
    - (no `data-type` attribute at all on the 5th one)

**CSS requirements:**
1. Style `#tag-list` (**ID selector**): `padding`, `border`, a fixed `width`, `box-sizing: border-box`.
2. Style `.tag` (**class selector**): this is the shared base — `display: inline-block`, `padding`, `margin`, `border`, consistent `box-sizing`.
3. Style `[data-type="sale"]` (**attribute selector**): override just the `border` color or `background`.
4. Style `[data-type="limited"]` (**attribute selector**): a different override again.
5. Do **not** write any rule targeting the 5th tag (the one with no `data-type`) directly — it should simply fall back to whatever `.tag` gives it.

**Challenge question to answer in a code comment:**
List, in order, every CSS rule that applies to the "sale" tags. Which one wins if two rules set the same property, and why?

---

## Task 5: Content-Box vs. Border-Box, Side by Side

**Goal:** A focused, visual proof of the single most important box-sizing concept — same declared numbers, different rendered size.

**HTML must include:**
- Two `<div>` elements sitting next to each other: `id="box-content"` and `id="box-border"`
- Put the same short text inside both, e.g. "300px wide, 20px padding, 5px border"

**CSS requirements:**
1. Use a **grouping selector** to give both `#box-content` and `#box-border` identical `width: 300px`, `padding: 20px`, `border: 5px solid black`, and `display: inline-block` (so they sit side by side and you can see both at once).
2. Then, in two **separate** rules, set `#box-content { box-sizing: content-box; }` and `#box-border { box-sizing: border-box; }`.

**Challenge question to answer in a code comment:**
Measure both boxes in DevTools. Write the exact rendered width of each, and explain in one sentence why they differ despite having identical CSS values for `width`, `padding`, and `border`.

---

## Suggested order

Do them in order (1 → 5) — each one reuses a concept from the previous task while adding one new wrinkle, so skipping ahead will make the "challenge questions" harder to reason about.