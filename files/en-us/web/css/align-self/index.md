---
title: align-self
slug: Web/CSS/align-self
page-type: css-property
browser-compat: css.properties.align-self
sidebar: cssref
---

The **`align-self`** [CSS](/en-US/docs/Web/CSS) property overrides a grid or flex item's {{cssxref("align-items")}} value. In grid, it aligns the item inside the {{glossary("Grid Areas", "grid area")}}. In flexbox, it aligns the item on the {{glossary("cross axis")}}.

{{InteractiveExample("CSS Demo: align-self")}}

```css interactive-example-choice
align-self: stretch;
```

```css interactive-example-choice
align-self: center;
```

```css interactive-example-choice
align-self: start;
```

```css interactive-example-choice
align-self: end;
```

```html interactive-example
<section class="default-example" id="default-example">
  <div class="example-container">
    <div class="transition-all" id="example-element">One</div>
    <div>Two</div>
    <div>Three</div>
  </div>
</section>
```

```css interactive-example
.example-container {
  border: 1px solid #c5c5c5;
  display: grid;
  width: 200px;
  grid-template-columns: 1fr 1fr;
  grid-auto-rows: 80px;
  grid-gap: 10px;
}

.example-container > div {
  background-color: rgb(0 0 255 / 0.2);
  border: 3px solid blue;
}
```

The property doesn't apply to block-level boxes, or to table cells. If a flexbox item's cross-axis margin is `auto`, then `align-self` is ignored.

## Syntax

```css
/* Keyword values */
align-self: auto;
align-self: normal;

/* Positional alignment */
/* align-self does not take left and right values */
align-self: center; /* Put the item around the center */
align-self: start; /* Put the item at the start */
align-self: end; /* Put the item at the end */
align-self: self-start; /* Align the item flush at the start */
align-self: self-end; /* Align the item flush at the end */
align-self: flex-start; /* Put the flex item at the start */
align-self: flex-end; /* Put the flex item at the end */
align-self: anchor-center;

/* Baseline alignment */
align-self: baseline;
align-self: first baseline;
align-self: last baseline;
align-self: stretch; /* Stretch 'auto'-sized items to fit the container */

/* Overflow alignment */
align-self: safe center;
align-self: unsafe center;

/* Global values */
align-self: inherit;
align-self: initial;
align-self: revert;
align-self: revert-layer;
align-self: unset;
```

### Values

- `auto`
  - : Computes to the parent's {{cssxref("align-items")}} value.
- `normal`
  - : The effect of this keyword is dependent of the layout mode we are in:
    - In absolutely-positioned layouts, the keyword behaves like `start` on _replaced_ absolutely-positioned boxes, and as `stretch` on _all other_ absolutely-positioned boxes.
    - In static position of absolutely-positioned layouts, the keyword behaves as `stretch`.
    - For flex items, the keyword behaves as `stretch`.
    - For grid items, this keyword leads to a behavior similar to the one of `stretch`, except for boxes with an {{glossary("aspect ratio")}} or an intrinsic size where it behaves like `start`.
    - The property doesn't apply to block-level boxes, and to table cells.

- `self-start`
  - : Aligns the items to be flush with the edge of the alignment container corresponding to the item's start side in the cross axis.
- `self-end`
  - : Aligns the items to be flush with the edge of the alignment container corresponding to the item's end side in the cross axis.
- `flex-start`
  - : The cross-start margin edge of the flex item is flushed with the cross-start edge of the line.
- `flex-end`
  - : The cross-end margin edge of the flex item is flushed with the cross-end edge of the line.
- `center`
  - : The flex item's margin box is centered within the line on the cross-axis. If the cross-size of the item is larger than the flex container, it will overflow equally in both directions.
- `baseline`, `first baseline`, `last baseline`
  - : Specifies participation in first- or last-baseline alignment: aligns the alignment baseline of the box's first or last baseline set with the corresponding baseline in the shared first or last baseline set of all the boxes in its baseline-sharing group.
    The fallback alignment for `first baseline` is `start`, the one for `last baseline` is `end`.
- `stretch`
  - : If the combined size of the items along the cross axis is less than the size of the alignment container and the item is `auto`-sized, its size is increased equally (not proportionally), while still respecting the constraints imposed by {{cssxref("max-height")}}/{{cssxref("max-width")}} (or equivalent functionality), so that the combined size of all `auto`-sized items exactly fills the alignment container along the cross axis.
- `anchor-center`
  - : In the case of [anchor-positioned](/en-US/docs/Web/CSS/CSS_anchor_positioning) elements, aligns the item to the center of the associated anchor element in the block direction. See [Centering on the anchor using `anchor-center`](/en-US/docs/Web/CSS/CSS_anchor_positioning/Using#centering_on_the_anchor_using_anchor-center).
- `safe`
  - : If the size of the item overflows the alignment container, the item is instead aligned as if the alignment mode were `start`.
- `unsafe`
  - : Regardless of the relative sizes of the item and alignment container, the given alignment value is honored.

## Formal definition

{{CSSInfo}}

## Formal syntax

{{csssyntax}}

## Examples

### HTML

```html
<section>
  <div>Item #1</div>
  <div>Item #2</div>
  <div>Item #3</div>
</section>
```

### CSS

```css
section {
  display: flex;
  align-items: center;
  height: 120px;
  background: beige;
}

div {
  height: 60px;
  background: cyan;
  margin: 5px;
}

div:nth-child(3) {
  align-self: flex-end;
  background: pink;
}
```

### Result

{{EmbedLiveSample('Examples')}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Basic concepts of flexbox](/en-US/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox)
- [Aligning items in a flex container](/en-US/docs/Web/CSS/CSS_flexible_box_layout/Aligning_items_in_a_flex_container)
- [Box alignment in grid layout](/en-US/docs/Web/CSS/CSS_box_alignment/Box_alignment_in_grid_layout)
- [CSS box alignment](/en-US/docs/Web/CSS/CSS_box_alignment)
- {{cssxref("align-items")}}
- {{cssxref("justify-self")}}
- {{cssxref("place-self")}}
