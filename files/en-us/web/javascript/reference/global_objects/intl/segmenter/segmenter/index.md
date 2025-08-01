---
title: Intl.Segmenter() constructor
short-title: Intl.Segmenter()
slug: Web/JavaScript/Reference/Global_Objects/Intl/Segmenter/Segmenter
page-type: javascript-constructor
browser-compat: javascript.builtins.Intl.Segmenter.Segmenter
sidebar: jsref
---

The **`Intl.Segmenter()`** constructor creates {{jsxref("Intl.Segmenter")}} objects.

{{InteractiveExample("JavaScript Demo: Intl.Segmenter() constructor")}}

```js interactive-example
const segmenterFr = new Intl.Segmenter("fr", { granularity: "word" });
const string = "Que ma joie demeure";

const iterator = segmenterFr.segment(string)[Symbol.iterator]();

console.log(iterator.next().value.segment);
// Expected output: 'Que'

console.log(iterator.next().value.segment);
// Expected output: ' '
```

## Syntax

```js-nolint
new Intl.Segmenter()
new Intl.Segmenter(locales)
new Intl.Segmenter(locales, options)
```

> [!NOTE]
> `Intl.Segmenter()` can only be constructed with [`new`](/en-US/docs/Web/JavaScript/Reference/Operators/new). Attempting to call it without `new` throws a {{jsxref("TypeError")}}.

### Parameters

- `locales` {{optional_inline}}
  - : A string with a BCP 47 language tag or an {{jsxref("Intl.Locale")}} instance, or an array of such locale identifiers. The runtime's default locale is used when `undefined` is passed or when none of the specified locale identifiers is supported. For the general form and interpretation of the `locales` argument, see [the parameter description on the `Intl` main page](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#locales_argument).
- `options` {{optional_inline}}
  - : An object containing the following properties, in the order they are retrieved (all of them are optional):
    - `localeMatcher`
      - : The locale matching algorithm to use. Possible values are `"lookup"` and `"best fit"`; the default is `"best fit"`. For information about this option, see [Locale identification and negotiation](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#locale_identification_and_negotiation).
    - `granularity`
      - : How granularly should the input be split. Possible values are:
        - `"grapheme"` (default)
          - : Split the input into segments at grapheme cluster (user-perceived character) boundaries, as determined by the locale.
        - `"word"`
          - : Split the input into segments at word boundaries, as determined by the locale.
        - `"sentence"`
          - : Split the input into segments at sentence boundaries, as determined by the locale.

### Return value

A new [`Intl.Segmenter`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Segmenter) instance.

### Exceptions

- {{jsxref("RangeError")}}
  - : Thrown if `locales` or `options` contain invalid values.

## Examples

### Basic usage

The following example shows how to count words in a string using the Japanese language (where splitting the string using `String` methods would have given an incorrect result).

```js
const text = "吾輩は猫である。名前はたぬき。";
const japaneseSegmenter = new Intl.Segmenter("ja-JP", { granularity: "word" });
console.log(
  [...japaneseSegmenter.segment(text)].filter((segment) => segment.isWordLike)
    .length,
);
// 8, as the text is segmented as '吾輩'|'は'|'猫'|'で'|'ある'|'。'|'名前'|'は'|'たぬき'|'。'
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
