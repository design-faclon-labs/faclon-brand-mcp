# Colour

Source: Figma "Design MCP", Colours page and variables.

- Colours are layered: **Global Colors** are raw primitives; **Semantic Colors** alias them and switch between Light and Dark modes. Design with semantic tokens.
- **Defaults:** canvas is background/primary with no border; the default container is container/primary with a 1px border/container edge; success and error containers have no border.
- **Text:** headings use text/heading (#0C1927 Light, #F1F5FA Dark), body text uses text/body (#243547 Light, #CBD5E2 Dark), eyebrows text/eyebrow. Body text sits one step lighter than headings, so weight and size carry the hierarchy.
- **Accent** (#68DD68) has its own background, container, text and border tokens; text on accent uses text/on-accent (near black). It highlights on dark surfaces (text/accent).
- **Accent-2** (#B4FF6B) is the highlight on brand blue: text/accent-on-brand. Together the two accents stay within roughly 10-15% of a piece.

## Token usage notes

Short notes for four tokens whose name alone does not say where they go. They repeat the validator rules and the Figma variable descriptions; they add no rule.

- **text/on-strong:** Text on the strong status fills container/info-strong, container/success-strong and container/error-strong (white in both themes). Added for the Badge intents Information, Intense Positive and Intense Negative.
- **text/accent-on-brand:** Highlighted text (a key phrase) on background/brand or container/brand only, e.g. the last item of a proof strip on a page breaker, in lime (#B4FF6B, 4.83:1 on brand/500). Never on light or dark surfaces: there use text/link (light) or text/accent (dark). It counts toward the 10-15% accent budget.
- **container/selected:** The selected or active state of rows, tabs and nav items. Eyebrow text may sit on it.
- **border/container:** The default 1px edge of container/primary (Light: neutral-light/200), very low contrast by design; see the ratios in semantic.css. For a stronger border (inputs, table dividers) use border/primary.
