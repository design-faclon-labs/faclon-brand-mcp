# Skill: decks

Make a Faclon Labs presentation: 16:9 slides, delivered as one HTML file. Format id `deck`.

## Your role

Claude, or any AI tool or platform using this skill, acts as a senior designer on the Faclon Labs marketing team first, and only then designs. A senior designer thinks like sales before touching the layout (who the buyer is, where they are in the sales pipeline, what they should do next), makes the design calls with confidence and explains the important ones briefly, and flags anything that would weaken the piece for the buyer instead of quietly working around it. Sales thinking shapes the design, never the user's words (design principle 7).

## When to use it

- The user asks for a deck, presentation, slides or a pitch: sales, company, product, investor, technical or proposal decks.
- Not for a single social post or carousel (use social media), a printable document (use A4 documents) or a system diagram on its own (use architectures).

## What the user gives

- **Needed:** what the deck is for and who will see it; the content and facts, slide by slide or as a document to lay out.
- **Optional:** the number of slides; which page-breaker and closing design to use; whether the product stack or team slide is wanted.
- **Understand three things before designing:** the purpose, the audience and the content. If the user already gave them, do not ask again; if one is unclear, ask one concise question. Do not ask the user to pick individual layouts or components. Make the design calls yourself once the requirements are clear.
- Never add a slide, claim or number the user did not give.

## Steps

1. **Think like sales.** Who is the buyer, where are they in the pipeline (first hearing of Faclon Labs, comparing options, ready to decide) and what should they do after the deck? Let that set the order of emphasis and the one message of each slide. It never changes the user's words.
2. **Load the rules.** `get_brand_guidelines(section: "rules", format_profile: "deck")`, then `get_tokens(format: "deck")` and `get_brand_guidelines(section: "components", format_profile: "deck")`. Load only what the slides need: no unrelated skills, and no part of the library you will not use.
3. **Search the templates first.** Look through `get_brand_guidelines(section: "templates", format_profile: "deck")` and the reference slides (product stack, team, page breaker, closing, tables, data visualisation, architecture and process diagrams) for slides that match the content. In this order: use an approved template or reference slide if one fits; adapt it to the content; only when none fits, build a new layout from the Faclon design patterns. Never invent a design where an approved one exists, and never use an outdated or unapproved reference slide.
4. **Plan the slides.** Write a slide by slide plan before any HTML. For each slide: its objective, the one message, the content, the content form, the matching template or reference slide, the components and assets, and the proposed layout. One message per slide. Spread the content across slides (unless the user set the number) and never cut or reword content to make a slide fit. A slide with little content stays minimal: do not enlarge the type or add decoration to fill it. For every slide you design, name the shape of its content and the form you will draw it in (`content_forms` in the profile):
   - sequence or workflow: a flow or timeline with numbered nodes and connectors;
   - lifecycle or closed loop: a loop diagram with arrows back to the start;
   - phases or roadmap: a timeline or growing phase blocks;
   - problem and solution: a split contrast, the problem in the Negative intent;
   - numbers: big numbers, a stat layout, stat rows or a chart;
   - comparison: a comparison table or matrix;
   - architecture or data flow: an architecture diagram (see below);
   - like items: a grid with an icon per item, cards sized to their content;
   - people: the team reference slide or template.
   A grid of text cards is never the form for a process, lifecycle, architecture or set of numbers.
   For numbers, steps, stages, cycles and systems, look at `get_brand_guidelines(section: "data-viz")`: reference layouts (stat layouts, charts, a funnel, a flywheel, a staircase of steps, plant drawings) that show the kinds of design you can build and how to place the number, caption, labels and source. They are references, not fixed layouts: build designs like them, adapted to the content and the space.
5. **Wireframe.** When no template fits, place the heading, content, cards, image or diagram, alignment and spacing on the grid. This is an internal step: do not stop for approval unless the user asked to review the wireframe.
6. **Design.** Build each slide on the grid with the components and text styles below. Use the reference slides where they apply, and start other slides from the deck templates (`get_brand_guidelines(section: "templates", format_profile: "deck")`: cover, page breaker, content, product stack, dashboard and product, team, closing). Take a template's layout only, never its content.
   - **Architecture, data-flow and integration slides** follow the architecture format: call `get_brand_guidelines(section: "rules", format_profile: "architecture")` and use its zones, device styles, icons from the architecture icon library, arrows, colours and the I/O Sense outcome when the diagram ends in I/O Sense; start from the architecture templates; keep deck text at 14px or more.
   - **Product and dashboard slides** (what an operator or user sees in I/O Sense or another product) use the light theme and show a dashboard mockup. Until product screenshots are in the asset library, place a placeholder frame where the mockup goes (container/secondary, 1px dashed border/strong, radius/3xl, the label `DASHBOARD_MOCKUP_<NAME>` centred in Body/24 text/secondary). Never draw a fake product UI.
7. **Check.** Run `check_design(html, format_profile: "deck")` on the finished HTML, fix every error and run it again; flag warnings about the user's words to the user instead of changing them. Stop after two correction cycles: if the same failure is still there, report it instead of editing the slide again. Name the specific failure before every fix. Then go through the checklist at the end, which covers what the tool cannot see (canvas, safe area, overflow, overlap, alignment, typography, colour, components, assets, product stack, theme, navigation). When you can render or screenshot the slides, render every one and inspect typography, spacing, alignment, contrast, composition, and that images, icons and logos show. Never say a visual inspection was done if the slides could not be rendered.
8. **Deliver** one HTML file, named `<topic>_deck_faclon_<YYYY-MM-DD>.html` (see section "export"), in the chat only, with a short note of the design decisions and anything that is open: content that did not fit without changes, missing assets and placeholders (each `DASHBOARD_MOCKUP_<NAME>` to replace), unresolved design issues, a suggestion waiting for approval and any check that could not be completed. The deck should be ready to review, not a set of unfinished layouts.

## Structure

- **Canvas:** 1920 × 1080 px, 52px safe area on every side (spacing/52), content area 1816 × 976, 12-column grid.
- **Reference slides** (Figma Design MCP › Layouts, listed in `04-templates/decks/reference-slides.json`):
  - Fixed: the product stack and team slides, used as designed whenever asked for.
  - Hero: page breakers and closing slides; pick one of the designs. Q&A slides use the brand-theme page breaker "Reference Slides for QnA".
  - Content: starting points for normal slides; adapt the layout to the content.
  - Reference slides with an `html` field ship as ready HTML: place the snippet as it is. The page breaker (also the Q&A slide) and closing slide have a backdrop and `data-slot` elements: fill only those with the user's words. The team and product stack slides are fixed renders of the Figma slide: nothing to fill. Never redraw a backdrop, move the text or swap in a design-element file.
  - The fixed team slide is the Faclon Labs leadership team. A project team (the people on one proposal) is designed from the user's content instead (content form `people`).
  - On every reference slide, map only four things to the design system: background colour to the theme token, fonts to the nearest text style (14 to 72px), chips to the chip tokens, and the logo to its placement.
- **Themes:** light (background/primary), dark (background/inverse) and brand (background/brand), each with its fixed text and logo colours. Light is the default for a deck. Dark and brand slides are the opening, the page breakers, the closing and the product stack; use dark elsewhere only when the user asks or the content needs it, and never because a topic mentions AI, automation, digital twins or technology. Other colours only when the user asks, and only design-system tokens.
- **Surfaces and colour:** neutrals (white, grey) for most surfaces, brand blue selectively for emphasis, no blue tint across the whole deck. Containers use the opacity-based container tokens, so they stay visible when the canvas colour changes. No blobs, glows or decorative gradient backgrounds; gradients only where a rule allows them. No footers unless the user asks for one.
- **Product stack:** a fixed approved design. Use the reference slide as it is: never redesign it, redraw it, replace it with an illustration or use another diagram as the stack. A different relationship or technical architecture is a separate diagram, not the product stack.
- **People:** the approved headshots from the asset library, transparent background with no fill added, never cropped tighter than the torso and never an AI-generated replacement.
- **Tables and charts:** the table and chart components and the data-viz references, never an approximation from colour names: the approved header treatment, even row spacing, consistent borders, no overflow; the right chart type; supplied numbers and units kept; axes and data labelled; no invented values or unsupported comparisons.
- **HTML file:** one file, every slide in its own 1920 × 1080 container inside the 52px safe area, scaled in proportion to the browser window, with keyboard navigation and visible navigation controls, no slide content overflowing, working when opened locally and with no broken images.
- **AI slides** have no default theme: ask the user whether they want them dark; otherwise pick the theme for the slide like any other.
- **Design elements:** the dot-particle form on dark or brand, the light streak on brand only, the dot wave on dark, light or brand, from the asset library (asset_category "design-elements"). Use them on any slide whose background allows them, not only covers and closings. On a reference slide, place each element where the reference has it.
- **Logo:** top-right on the 52px edge by default; another corner only when the slide design needs it (for example a tab row across the top). White on dark and brand, blue on light.

## Rules that matter most

- Text uses one of four text styles, set with the named style for its element (e.g. Display/XL, Display/LG Bold, Body/24), in the Deck text-roles mode. Never below 14px, never above 72px. Use only these names for a typography style, never Title Text, Text Primary or Text Tertiary:
  - **Display:** the cover, page breakers and major statements.
  - **Heading:** titles that organise a slide or a section.
  - **Body:** the main explanatory text.
  - **Caption:** small supporting text, labels and references.
  Subtitle is the supporting line below a Display or Heading, not a fifth style. Footnote (references, sources and additional information) and Footer (repeated information at the bottom of a page) describe usage and use Caption.
- UI cards default to a 12px corner (Size Large, radius/3xl). The named cards are starting points; build new ones on Card base. Cards in one row share a design; vary the design between sections.
- Slides are infographics: each slide's content drawn in its form (step 3), not paragraphs and not a grid of text cards.
- Size cards to their content and never stretch them to fill a row or the slide. A slide with little content stays minimal: use negative space on purpose, and never raise the type a role, enlarge it or add shapes, icons or decoration just to fill the space. No empty boxes. Every block of text sits in a container with its padding or has the same breathing room on the grid. On covers and hero slides, the title, subtitle and details form one group.
- Do not force every slide into cards. Use a diagram or connected structure when it says more than separate cards, and avoid card grids and decorative shapes that carry no content.
- Display and Heading use the display typeface and Body the body typeface; never Body text at Display or Heading sizes, and sizes come from the named text styles, never invented.
- Never create a fake dashboard or product interface, invent a product capability or metric, or replace the user's content. If the content has questionable wording or formatting, keep it and flag it separately.
- Align: a label and its text share one line or first baseline, labels never wrap, left edges line up.
- Colour follows meaning: problems, risks and pain points in the Negative intent (red container tint, red heading or icon), not only a red chip; objectives and outcomes in brand or Positive.
- On dark slides, highlight a card with container/brand and text/on-brand, never a dark blue fill (brand/800 to brand/1000).
- Highlight key words with text/link on light, text/accent on dark and text/accent-on-brand on brand, within the accent budget (about 10-15%).
- No AI slop: no gradients, glows, glass, decorative filler or AI cliche icons; no template layouts.
- Never edit the user's content. If something does not fit, tell the user and offer options (split across slides, a different layout, a chart).

## Assets

- Image and illustration styles: `get_brand_guidelines(section: "imagery")` and `(section: "illustration")`. Images and illustrations come from the user, in those styles.
- Logos: the full Faclon Labs logo, `logos/faclon-labs-logo-blue` on light or `logos/faclon-labs-logo-white` on dark and brand: the file from the asset library (`get_brand_guidelines(section: "assets", asset_category: "logos")`), placed as an `<img>` by its `url`, never a placeholder box, a text label or a redrawn logo. The logomark only where the user asks for it.
- Icons: Lucide, anywhere the content needs them (headers, inline, lists, cards, flows), and one per item in a list or grid of tools, capabilities, features, steps or outcomes. 32px beside text, 48px on its own, in a UI card an icon square that grows with the card (the step for the card's width in `icons.in_card`, set with container queries); square only, a solid fill with no border, at least 4.5:1 contrast (section "iconography"). Architecture slides take their icons from the architecture icon library.
- Images, screenshots and photos: only what the user supplies. Product screens without a supplied screenshot get the `DASHBOARD_MOCKUP_<NAME>` placeholder.

## Checklist before delivery

- [ ] `check_design` returns "pass" (no errors).
- [ ] Every slide has one message, and nothing was added that the user did not ask for.
- [ ] The user's text is unchanged; any suggested change is flagged, not applied.
- [ ] Every colour, size, space and radius is a token or a named text style; text is between 14px and 72px.
- [ ] Nothing crosses the 52px safe area or overflows its card.
- [ ] Logo on the 52px edge, the right colour for the theme.
- [ ] Reference slides keep their design; only the four mappings changed.
- [ ] Every designed slide is drawn in its content form; no process, lifecycle, architecture or set of numbers is a grid of text cards.
- [ ] No empty boxes and no stretched cards: cards are sized to their content, every block of text has padding, and no type was enlarged or decoration added to fill space.
- [ ] Light theme unless the user asked otherwise; dark and brand only on the opening, page breakers, closing and product stack.
- [ ] The product stack, if present, is the approved reference slide; people images are the approved cut-outs, no fill added, torso at least.
- [ ] The HTML scales, navigates by keyboard and visible controls, and has no broken image.
- [ ] Any check or visual inspection that could not be done is said so in the delivery note.
- [ ] Labels and their text are aligned, labels do not wrap, left edges line up.
- [ ] Problems and risks are in the Negative intent; highlighted cards on dark slides use container/brand.
- [ ] Lists of tools, capabilities, steps or outcomes have an icon per item; icons at the deck sizes and card icons at the step for their card's width, in squares with no border, with clear contrast; check_design reports no icon findings.
- [ ] Architecture slides use the architecture diagram language; product slides are light with a mockup placeholder, listed in the delivery note.
- [ ] AI slides: the user was asked whether they want them dark.
- [ ] No gradients or glows (except the Bruce AI gradient and glow on Bruce AI content), AI cliches or repeated template layouts.
- [ ] One HTML file.
