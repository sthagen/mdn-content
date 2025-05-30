---
title: "SpeechRecognition: start event"
short-title: start
slug: Web/API/SpeechRecognition/start_event
page-type: web-api-event
browser-compat: api.SpeechRecognition.start_event
---

{{APIRef("Web Speech API")}}

The **`start`** event of the [Web Speech API](/en-US/docs/Web/API/Web_Speech_API) {{domxref("SpeechRecognition")}} object is fired when the speech recognition service has begun listening to incoming audio with intent to recognize grammars associated with the current `SpeechRecognition`.

## Syntax

Use the event name in methods like {{domxref("EventTarget.addEventListener", "addEventListener()")}}, or set an event handler property.

```js-nolint
addEventListener("start", (event) => { })

onstart = (event) => { }
```

## Event type

A generic {{DOMxRef("Event")}} with no added properties.

## Examples

You can use the `start` event in an [`addEventListener`](/en-US/docs/Web/API/EventTarget/addEventListener) method:

```js
const recognition = new (SpeechRecognition || webkitSpeechRecognition)();

recognition.addEventListener("start", () => {
  console.log("Speech recognition service has started");
});
```

Or use the `onstart` event handler property:

```js
recognition.onstart = () => {
  console.log("Speech recognition service has started");
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Web Speech API](/en-US/docs/Web/API/Web_Speech_API)
