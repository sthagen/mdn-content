---
title: ascent
slug: Web/SVG/Reference/Attribute/ascent
page-type: svg-attribute
status:
  - deprecated
browser-compat: svg.elements.font-face.ascent
sidebar: svgref
---

{{deprecated_header}}

The **`ascent`** attribute defines the maximum unaccented height of the font within the font coordinate system.

If the attribute is not specified, the effect is as if the attribute were set to the difference between the {{SVGAttr("units-per-em")}} value and the {{SVGAttr("vert-origin-y")}} value for the corresponding font.

You can use this attribute with the following SVG elements:

- {{SVGElement("font-face")}}

## font-face

For {{SVGElement("font-face")}}, `ascent` defines the maximum unaccented height of the font within the font coordinate system.

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">Value</th>
      <td>
        <a href="/en-US/docs/Web/SVG/Guides/Content_type#number">&#x3C;number></a>
      </td>
    </tr>
    <tr>
      <th scope="row">Default value</th>
      <td>
        Difference between {{SVGAttr("units-per-em")}} and
        {{SVGAttr("vert-origin-y")}}
      </td>
    </tr>
    <tr>
      <th scope="row">Animatable</th>
      <td>No</td>
    </tr>
  </tbody>
</table>

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
