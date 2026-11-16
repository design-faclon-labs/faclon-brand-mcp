# Naming conventions

One element, one name. One name, one meaning. Figma is the source of every name: tokens, text styles and components keep the names they have there, and every skill, rule and guideline uses them. This file defines the words once; it does not repeat the design system. When a skill needs a new word, add it here first.

## How names are written

| Kind | Form | Examples |
|---|---|---|
| Token | lowercase, slash, as in Figma and `get_tokens` | `text/heading`, `container/primary`, `border-width/md`, `radius/3xl`, `spacing/24`, `gap/grid`, `padding/container` |
| Text style (Figma) | Figma capitalisation in prose; lowercase in token and rule data | `Display/LG Bold`, `Heading/H2`, `Body/24`; in data `display/lg` with `weight` 700 |
| Text role | `Role/` plus Title Case in Figma and prose; lowercase in token data | `Role/Label`, `Role/Button`; in data `label`, `button` |
| Component | exactly its Figma name | Card base, Stat tile, Icon Card, Contact Pill |
| Rule, guardrail, decision id | lowercase, hyphens | `no-ai-slop`, `stretched-cards`, `deck-density` |
| Format id | singular | `deck`, `document`, `newsletter`, `architecture`, `social` |
| Outcome folder and Figma page | plural or full name | `decks`, `a4-documents`, `newsletters`, `architectures`, `social-media` |

Spelling: prose uses "colour". Identifiers keep `color` (token key, folder `color`, rule ids `color.*`, Figma Semantic Colors collection names). Copy written for the brand follows the voice section (US spelling).

## Typography

Four text styles, nothing else:

| Name | Meaning |
|---|---|
| Display | large, prominent text: covers, hero sections, major statements |
| Heading | titles that organise pages, sections and content |
| Body | regular paragraph and content text |
| Caption | small supporting text, labels and references |

Usage names, not styles:

| Name | Means | Style |
|---|---|---|
| Subtitle | the supporting line below a Display or Heading | its own purpose, set in the style its format gives it; never subheader, subheadline, subline, intro or standfirst |
| Footnote | references, sources and additional information | Caption |
| Footer | repeated information at the bottom of a page, such as page numbers or document details | Caption, unless a documented design says otherwise (the A4 footer is Body/XS Medium) |

Figma defines the style families (Display, Heading, Body, Eyebrow) and the Text Roles (eyebrow, title, subtitle, body, caption, label, label-md, label-lg, button, metric, tag; each resolves by format and breakpoint). Those names stay as they are in Figma. In prose say "eyebrow" (the small line above a heading), "body text" and "CTA" only for the purpose; Button is the component and text role.

Text elements in a skill's `rules.json` (`typography.styles`) are keyed by the Figma style they are set in:

`[text style]_[size or level]_[weight if required]`

| Figma style | Key |
|---|---|
| Display/LG | `display_lg` |
| Heading/H1 | `heading_h1` |
| Heading/H1 Bold | `heading_h1_bold` |
| Body/24 | `body_24` |
| Body/24 Medium | `body_24_medium` |
| Body/24 Semi Bold | `body_24_semibold` |
| Body/24 Bold | `body_24_bold` |

- The base weight has no suffix (Display: Bold; Heading H1 to H4: Semi Bold; Heading H5 and H6: Medium; Body: Regular). Add `_medium`, `_semibold` or `_bold` when the weight differs, using the Figma weight name. Do not add weights Figma does not have.
- The key follows the style assigned in Figma, not the purpose of the text. The purpose is in the entry's `use` line.
- Elements set in the same Figma style share one entry; differences in colour, position or content are documented in `use` or in the component rules.
- Subtitle is a usage name for the supporting line below a Display or Heading, written in `use`. It is not a key and not a style.
- Footer and Footnote are usage names too: they use an existing style with their approved lighter treatment, with no weight variants of their own.
- Newsletter elements use purpose names (`card_title`, `card_body`, `card_button`, `card_caption`); the Text Roles mode sets their size.

All five formats follow this. Architecture keys its entries per density (dense, medium, open): entries with the same style and weight share one key, and their colours and uses are listed per usage. Regular never takes a suffix, so social `display_xl` and `display_lg` (Regular) share keys with the deck's Bold ones; each entry's `weight` says which.

## Colour

| Word | Means | Not |
|---|---|---|
| Background | the page or slide fill: `background/*` tokens | a card fill |
| Container | the fill of a card or box: `container/*` tokens | the page fill |
| Text | text colour: `text/*` tokens | |
| Border | edge colour: `border/*` tokens | border width, which is `border-width/*` |
| Surface | the word for whatever a text or icon sits on, background or container. Not a token | a token name or a synonym for container |
| Canvas | the page or slide area: its size (`canvas` in a format profile) and its fill (`background/primary`) | the colour alone |
| Brand blue | brand/500, #1655F2, the one primary colour | Faclon blue, primary blue |
| Intent | Positive, Negative, Information, Neutral, Primary: the meaning a status colour carries | status colour, semantic colour |
| Theme | how a page or slide looks: light, dark or brand | mode |
| Mode | a token switch: Light and Dark for colour, Desktop and Mobile for type and spacing, Document, Newsletter and Deck for text roles | theme |

## Components

Use the Figma name. Components that look alike but are different things:

| Name | Is | Is not |
|---|---|---|
| Card | a content card; every other card is built on Card base | a panel or tile |
| Chip | small square-cornered label inside a card | Badge |
| Badge | colour-coded metadata label with a pill radius | Chip |
| Tag | the statement tag component | the architecture `node_tag` text role |
| Contact Pill | a contact or fact pill | a radius |
| Stat tile, Metric Card | one big number; one KPI with label and optional chip. Stat tile keeps its Figma name; "tile" is not used for anything else | each other |
| Blocks | the eight blocks designed on 2026-10-27 (Stat tile to Cover block) | any group of content |
| Design elements | the dot-particle form, light streak and dot wave (asset category `design-elements`) | shapes; the Figma page that holds them is called Graphic elements |

## Layout and spacing

| Word | Means | Not |
|---|---|---|
| Canvas | see Colour | |
| Safe area | the distance kept clear on every edge of the canvas | margin; padding |
| Content area | the canvas inside the safe area | |
| Section | a larger area that groups related content | panel |
| Card | a self-contained block of information, built on Card base | panel, tile |
| Grid, column | the 12-column grid of a format and its columns | |
| Gutter | the gap between grid columns (`gap/grid`, or the format's `spacing/NN`) | |
| Gap | space between items: `gap/inline`, `gap/stack`, `gap/grid` | padding |
| Padding | space inside a container or section: `padding/container`, `padding/section` | the safe area |
| Radius | the token (`radius/3xl`); "corner" is how it looks | |
| Border width | the token (`border-width/md`) for a box edge | stroke |
| Stroke | the line of an icon, a chart line or a diagram line | border |

## Layers of guidance

Rule: one check in `validator-rules.json`. Guardrail: a profile's must-not, avoid and design-direction items, each grounded in a rule, default or decision. Guideline: any section served by `get_brand_guidelines`. Outcome: what the user asks for. Format profile: the technical id behind an outcome.

## Not yet decided

Waiting for the brand team; do not settle these in a skill:

- Where a documented design sets a footnote or footer outside Caption: the A4 footer (Body/XS Medium) and the social footnote (Body/2XS, 10px).
- The newsletter `card_body` and `card_caption` keys also cover non-card text (paragraphs, meta text, footer, legal); their `use` lines say so.
- `panel` in the locked validator rules and the architecture pill-radius rule; whether Stat tile is renamed.
- Component capitalisation in Figma (Title Case and sentence case are both used).
- The Figma Decks, Newsletter and Architecture rules frames still show the old element names until they are updated there.
