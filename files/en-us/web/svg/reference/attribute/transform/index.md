---
title: transform
slug: Web/SVG/Reference/Attribute/transform
page-type: svg-attribute
browser-compat: svg.global_attributes.transform
sidebar: svgref
---

The **`transform`** attribute defines a list of transform definitions that are applied to an element and the element's children.

> [!NOTE]
> As a presentation attribute, `transform` also has a CSS property counterpart: {{cssxref("transform")}}. When both are specified, the CSS property takes priority. Note that there are some differences in syntax between the CSS property and the attribute!

## Elements

In SVG 2, you can use the `transform` attribute on any element, including the {{SVGElement('svg')}} root.
Note that using `transform` on the `<svg>` root is a newer feature, and you should check [browser compatibility](#browser_compatibility) for support.
Using `transform` on the `<svg>` root is convenient for applying transforms to an entire SVG image without the need for extra wrapper elements or CSS workarounds.

In SVG 1.1, only these 16 elements were allowed to have a `transform` applied: {{SVGElement('a')}}, {{SVGElement('circle')}}, {{SVGElement('clipPath')}}, {{SVGElement('defs')}}, {{SVGElement('ellipse')}}, {{SVGElement('foreignObject')}}, {{SVGElement('g')}}, {{SVGElement('image')}}, {{SVGElement('line')}}, {{SVGElement('path')}}, {{SVGElement('polygon')}}, {{SVGElement('polyline')}}, {{SVGElement('rect')}}, {{SVGElement('switch')}}, {{SVGElement('text')}}, and {{SVGElement('use')}}.

Also, as a legacy from SVG 1.1, {{SVGElement('linearGradient')}} and {{SVGElement('radialGradient')}} support the `gradientTransform` attribute, and {{SVGElement('pattern')}} supports the `patternTransform` attribute, both of which behave exactly like the `transform` attribute.

## Value

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">Value</th>
      <td>
        <strong
          ><a href="/en-US/docs/Web/SVG/Guides/Content_type#transform-list"
            ><code>&#x3C;transform-list></code></a
          ></strong
        >
      </td>
    </tr>
    <tr>
      <th scope="row">Default value</th>
      <td><em>none</em></td>
    </tr>
    <tr>
      <th scope="row">Animatable</th>
      <td>Yes</td>
    </tr>
  </tbody>
</table>

## Examples

### Apply a transform to a single SVG element

In this example, we apply a `transform` to a single {{svgelement("g")}} element inside an SVG document:

```css hidden live-sample___transform-single-element live-sample___transform-svg-document
html,
body,
svg {
  height: 100%;
}
```

```html live-sample___transform-single-element
<svg
  viewBox="-40 0 150 100"
  xmlns="http://www.w3.org/2000/svg"
  xmlns:xlink="http://www.w3.org/1999/xlink">
  <g
    fill="grey"
    transform="rotate(-10 50 100)
               translate(-36 45.5)
               skewX(40)
               scale(1 0.5)">
    <path
      id="heart"
      d="M 10,30 A 20,20 0,0,1 50,30 A 20,20 0,0,1 90,30 Q 90,60 50,90 Q 10,60 10,30 z" />
  </g>

  <use href="#heart" fill="none" stroke="red" />
</svg>
```

{{EmbedLiveSample("transform-single-element", '100%', 200)}}

### Apply a transform to an entire SVG document

In this example, we apply a `transform` to the {{svgelement("svg")}} root element, meaning that the transform is applied to the entire SVG document:

```html live-sample___transform-svg-document
<svg
  viewBox="-40 0 150 100"
  xmlns="http://www.w3.org/2000/svg"
  xmlns:xlink="http://www.w3.org/1999/xlink"
  transform="rotate(-10 50 100)
               translate(-36 15.5)
               skewX(40)
               scale(1 0.5)">
  <g fill="grey">
    <path
      id="heart"
      d="M 10,30 A 20,20 0,0,1 50,30 A 20,20 0,0,1 90,30 Q 90,60 50,90 Q 10,60 10,30 z" />
  </g>

  <use href="#heart" fill="none" stroke="red" />
</svg>
```

{{EmbedLiveSample("transform-svg-document", '100%', 200)}}

## Transform functions

The following transform functions can be used by the `transform` attribute `<transform-list>`.

> [!WARNING]
> As per the spec, you should be able to also use CSS [transform functions](/en-US/docs/Web/CSS/transform-function). However, the compatibility isn't guaranteed.

### Matrix

The `matrix(<a> <b> <c> <d> <e> <f>)` transform function specifies a transformation in the form of a transformation matrix of six values. `matrix(a,b,c,d,e,f)` is equivalent to applying the transformation matrix:

<!-- prettier-ignore-start -->
<math display="block">
  <semantics><mrow><mo>(</mo><mtable rowspacing="0.5ex"><mtr><mtd><mi>a</mi></mtd><mtd><mi>c</mi></mtd><mtd><mi>e</mi></mtd></mtr><mtr><mtd><mi>b</mi></mtd><mtd><mi>d</mi></mtd><mtd><mi>f</mi></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow><annotation encoding="TeX">\begin{pmatrix} a & c & e \\ b & d & f \\ 0 & 0 & 1 \end{pmatrix}</annotation></semantics>
</math>
<!-- prettier-ignore-end -->

Which maps coordinates from a previous coordinate system into a new coordinate system by the following matrix equalities:

<!-- prettier-ignore-start -->
<math display="block">
  <semantics><mrow><mrow><mo>(</mo><mtable rowspacing="0.5ex"><mtr><mtd><msub><mi>x</mi><mstyle mathvariant="normal"><mrow><mi>newCoordSys</mi></mrow></mstyle></msub></mtd></mtr><mtr><mtd><msub><mi>y</mi><mstyle mathvariant="normal"><mrow><mi>newCoordSys</mi></mrow></mstyle></msub></mtd></mtr><mtr><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow><mo>=</mo><mrow><mo>(</mo><mtable rowspacing="0.5ex"><mtr><mtd><mi>a</mi></mtd><mtd><mi>c</mi></mtd><mtd><mi>e</mi></mtd></mtr><mtr><mtd><mi>b</mi></mtd><mtd><mi>d</mi></mtd><mtd><mi>f</mi></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow><mrow><mo>(</mo><mtable rowspacing="0.5ex"><mtr><mtd><msub><mi>x</mi><mstyle mathvariant="normal"><mrow><mi>prevCoordSys</mi></mrow></mstyle></msub></mtd></mtr><mtr><mtd><msub><mi>y</mi><mstyle mathvariant="normal"><mrow><mi>prevCoordSys</mi></mrow></mstyle></msub></mtd></mtr><mtr><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow><mo>=</mo><mrow><mo>(</mo><mtable rowspacing="0.5ex"><mtr><mtd><mi>a</mi><msub><mi>x</mi><mstyle mathvariant="normal"><mrow><mi>prevCoordSys</mi></mrow></mstyle></msub><mo>+</mo><mi>c</mi><msub><mi>y</mi><mstyle mathvariant="normal"><mrow><mi>prevCoordSys</mi></mrow></mstyle></msub><mo>+</mo><mi>e</mi></mtd></mtr><mtr><mtd><mi>b</mi><msub><mi>x</mi><mstyle mathvariant="normal"><mrow><mi>prevCoordSys</mi></mrow></mstyle></msub><mo>+</mo><mi>d</mi><msub><mi>y</mi><mstyle mathvariant="normal"><mrow><mi>prevCoordSys</mi></mrow></mstyle></msub><mo>+</mo><mi>f</mi></mtd></mtr><mtr><mtd><mn>1</mn></mtd></mtr></mtable><mo>)</mo></mrow></mrow><annotation encoding="TeX"> \begin{pmatrix} x_{\mathrm{newCoordSys}} \\ y_{\mathrm{newCoordSys}} \\ 1 \end{pmatrix} = \begin{pmatrix} a & c & e \\ b & d & f \\ 0 & 0 & 1 \end{pmatrix} \begin{pmatrix} x_{\mathrm{prevCoordSys}} \\ y_{\mathrm{prevCoordSys}} \\ 1 \end{pmatrix} = \begin{pmatrix} a x_{\mathrm{prevCoordSys}} + c y_{\mathrm{prevCoordSys}} + e \\ b x_{\mathrm{prevCoordSys}} + d y_{\mathrm{prevCoordSys}} + f \\ 1 \end{pmatrix}</annotation></semantics>
</math>
<!-- prettier-ignore-end -->

#### Example

```css hidden
html,
body,
svg {
  height: 100%;
}
```

```html
<svg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
  <rect x="10" y="10" width="30" height="20" fill="green" />

  <!--
  In the following example we are applying the matrix:
  [a c e]    [3 -1 30]
  [b d f] => [1  3 40]
  [0 0 1]    [0  0  1]

  which transform the rectangle as such:

  top left corner: oldX=10 oldY=10
  newX = a * oldX + c * oldY + e = 3 * 10 - 1 * 10 + 30 = 50
  newY = b * oldX + d * oldY + f = 1 * 10 + 3 * 10 + 40 = 80

  top right corner: oldX=40 oldY=10
  newX = a * oldX + c * oldY + e = 3 * 40 - 1 * 10 + 30 = 140
  newY = b * oldX + d * oldY + f = 1 * 40 + 3 * 10 + 40 = 110

  bottom left corner: oldX=10 oldY=30
  newX = a * oldX + c * oldY + e = 3 * 10 - 1 * 30 + 30 = 30
  newY = b * oldX + d * oldY + f = 1 * 10 + 3 * 30 + 40 = 140

  bottom right corner: oldX=40 oldY=30
  newX = a * oldX + c * oldY + e = 3 * 40 - 1 * 30 + 30 = 120
  newY = b * oldX + d * oldY + f = 1 * 40 + 3 * 30 + 40 = 170
  -->
  <rect
    x="10"
    y="10"
    width="30"
    height="20"
    fill="red"
    transform="matrix(3 1 -1 3 30 40)" />
</svg>
```

{{EmbedLiveSample('Matrix', '100%', 200)}}

### Translate

The `translate(<x> [<y>])` transform function moves the object by `x` and `y`. If `y` is not provided, it is assumed to be `0`.

In other words:

```plain
xNew = xOld + <x>
yNew = yOld + <y>
```

#### Example

```css hidden
html,
body,
svg {
  height: 100%;
}
```

```html
<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <!-- No translation -->
  <rect x="5" y="5" width="40" height="40" fill="green" />

  <!-- Horizontal translation -->
  <rect
    x="5"
    y="5"
    width="40"
    height="40"
    fill="blue"
    transform="translate(50)" />

  <!-- Vertical translation -->
  <rect
    x="5"
    y="5"
    width="40"
    height="40"
    fill="red"
    transform="translate(0 50)" />

  <!-- Both horizontal and vertical translation -->
  <rect
    x="5"
    y="5"
    width="40"
    height="40"
    fill="yellow"
    transform="translate(50 50)" />
</svg>
```

{{EmbedLiveSample('Example_3', '100%', 200)}}

### Scale

The `scale(<x> [<y>])` transform function specifies a scale operation by `x` and `y`. If `y` is not provided, it is assumed to be equal to `x`.

#### Example

```css hidden
html,
body,
svg {
  height: 100%;
}
```

```html
<svg viewBox="-50 -50 100 100" xmlns="http://www.w3.org/2000/svg">
  <!-- uniform scale -->
  <circle cx="0" cy="0" r="10" fill="red" transform="scale(4)" />

  <!-- vertical scale -->
  <circle cx="0" cy="0" r="10" fill="yellow" transform="scale(1, 4)" />

  <!-- horizontal scale -->
  <circle cx="0" cy="0" r="10" fill="pink" transform="scale(4, 1)" />

  <!-- No scale -->
  <circle cx="0" cy="0" r="10" fill="black" />
</svg>
```

{{EmbedLiveSample('Scale', '100%', 200)}}

### Rotate

The `rotate(<a> [<x> <y>])` transform function specifies a rotation by `a` degrees about a given point. If optional parameters `x` and `y` are not supplied, the rotation is about the origin of the current user coordinate system. If optional parameters `x` and `y` are supplied, the rotation is about the point `(x, y)`.

#### Example

```css hidden
html,
body,
svg {
  height: 100%;
}
```

```html
<svg viewBox="-12 -2 34 14" xmlns="http://www.w3.org/2000/svg">
  <rect x="0" y="0" width="10" height="10" />

  <!-- rotation is done around the point 0,0 -->
  <rect x="0" y="0" width="10" height="10" fill="red" transform="rotate(100)" />

  <!-- rotation is done around the point 10,10 -->
  <rect
    x="0"
    y="0"
    width="10"
    height="10"
    fill="green"
    transform="rotate(100, 10, 10)" />
</svg>
```

{{EmbedLiveSample('Rotate', '100%', 200)}}

### SkewX

The `skewX(<a>)` transform function specifies a skew transformation along the x axis by `a` degrees.

#### Example

```css hidden
html,
body,
svg {
  height: 100%;
}
```

```html
<svg viewBox="-5 -5 10 10" xmlns="http://www.w3.org/2000/svg">
  <rect x="-3" y="-3" width="6" height="6" />

  <rect x="-3" y="-3" width="6" height="6" fill="red" transform="skewX(30)" />
</svg>
```

{{EmbedLiveSample('SkewX', '100%', 200)}}

### SkewY

The `skewY(<a>)` transform function specifies a skew transformation along the y axis by `a` degrees.

#### Example

```css hidden
html,
body,
svg {
  height: 100%;
}
```

```html
<svg viewBox="-5 -5 10 10" xmlns="http://www.w3.org/2000/svg">
  <rect x="-3" y="-3" width="6" height="6" />

  <rect x="-3" y="-3" width="6" height="6" fill="red" transform="skewY(30)" />
</svg>
```

{{EmbedLiveSample('SkewY', '100%', 200)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- CSS {{cssxref("transform")}} property
