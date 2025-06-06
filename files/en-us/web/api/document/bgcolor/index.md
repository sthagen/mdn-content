---
title: "Document: bgColor property"
short-title: bgColor
slug: Web/API/Document/bgColor
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.bgColor
---

{{APIRef("DOM")}} {{Deprecated_Header}}

The deprecated `bgColor` property gets or sets the background color of the
current document.

## Value

A string representing the color as a word (e.g., `"red"`) or hexadecimal value (e.g., `"#ff0000"`).

When set to the `null` value, that `null` value is converted to the empty string (`""`), so `document.bgColor = null` is equivalent to `document.bgColor = ""`.

## Examples

```js
document.bgColor = "darkblue";
```

## Notes

The default value for this property in Firefox is white (`#ffffff` in
hexadecimal).

`document.bgColor` is deprecated in [the HTML specification](https://html.spec.whatwg.org/multipage/obsolete.html#dom-document-bgcolor). The recommended alternative is use of the CSS style
{{Cssxref("background-color")}} which can be accessed through the DOM with
`document.body.style.backgroundColor`.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
