# Abstract Penguin Development Style Guide

Visit us at abstractpenguin.com
When working with Abstract Penguin, we recommend the following structure:

## BEM and selector structure

- Prefer **strict BEM** selectors with **low specificity**.
- Prefer **`.block__element`** over **`.block .block__element`** (avoid redundant descendant chaining when the element class already identifies the node).
- Use **parent/context scoping** only when intentional — for example Drupal Views wrappers, admin or preview states, utility hooks, or third-party markup you do not control.
- In SCSS partials, keep **top-level selectors mostly alphabetical** within the file (for example `.application-note*` before `.article*`), with **related exceptions** kept adjacent when it helps (media queries, state variants).
- **Nest pseudo- and state selectors** under the base selector with `&` when possible (`&:hover`, `&:focus-visible`, `&::before`) instead of repeating long selector chains at the top level.

### State and content flags (not BEM-prefixed)

Use **short, reusable classes** for cross-cutting conditions instead of long BEM modifier chains:

- Examples: `.has-image`, `.has-sidebar`, `.is-expanded`, `.is-active`.

**Markup:** Keep **structure** in BEM (for example `card__media`, `application-note__column--industry-rail`) and **add the state class alongside** on the same element when appropriate.

**SCSS:** Bind the state to the intended block with a **chained** selector so rules stay low-specificity and do not leak globally — for example `.application-note__column--industry-rail.has-image`, or nest `&.has-image` under the BEM block.

---

## Margin and padding — logical axes (`-inline`, `-block`)

When **left and right** (or **top and bottom**) are meant to match, prefer **logical properties** instead of physical pairs or ambiguous shorthands:

- **Symmetric horizontal spacing:** `margin-inline`, `padding-inline` — not `margin-left` + `margin-right`, `padding-left` + `padding-right`, nor a `margin` / `padding` shorthand used only to set both horizontal sides.
- **Symmetric vertical spacing:** `margin-block`, `padding-block` — not `margin-top` + `margin-bottom`, `padding-top` + `padding-bottom`, nor the same idea for vertical-only pairs.

When **start and end differ** on one axis, use `margin-inline-start` / `margin-inline-end`, `padding-block-start` / `padding-block-end`, etc., as appropriate.

Use **physical** sides (`margin-left`, `padding-top`, …) only when the offset is intentionally tied to a fixed direction (for example a one-sided gutter in an LTR-only layout) or when matching third-party markup that is explicitly physical.
