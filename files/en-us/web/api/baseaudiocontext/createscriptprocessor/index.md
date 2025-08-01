---
title: "BaseAudioContext: createScriptProcessor() method"
short-title: createScriptProcessor()
slug: Web/API/BaseAudioContext/createScriptProcessor
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.BaseAudioContext.createScriptProcessor
---

{{APIRef("Web Audio API")}}{{deprecated_header}}

The `createScriptProcessor()` method of the {{domxref("BaseAudioContext")}} interface
creates a {{domxref("ScriptProcessorNode")}} used for direct audio processing.

> [!NOTE]
> This feature was replaced by [AudioWorklets](/en-US/docs/Web/API/AudioWorklet) and the {{domxref("AudioWorkletNode")}} interface.

## Syntax

```js-nolint
createScriptProcessor(bufferSize, numberOfInputChannels, numberOfOutputChannels)
```

### Parameters

- `bufferSize`
  - : The buffer size in units of sample-frames. If specified, the bufferSize must be one
    of the following values: 256, 512, 1024, 2048, 4096, 8192, 16384. If it's not passed
    in, or if the value is 0, then the implementation will choose the best buffer size for
    the given environment, which will be a constant power of 2 throughout the lifetime of
    the node.

    This value controls how frequently the `audioprocess` event is dispatched
    and how many sample-frames need to be processed each call. Lower values for
    `bufferSize` will result in a lower (better) latency. Higher values will be
    necessary to avoid audio breakup and glitches. It is recommended for authors to not
    specify this buffer size and allow the implementation to pick a good buffer size to
    balance between latency and audio quality.

- `numberOfInputChannels`
  - : Integer specifying the number of channels for this node's input, defaults to 2.
    Values of up to 32 are supported.
- `numberOfOutputChannels`
  - : Integer specifying the number of channels for this node's output, defaults to 2.
    Values of up to 32 are supported.

> [!WARNING]
> WebKit currently (version 31) requires that a valid
> `bufferSize` be passed when calling this method.

> [!NOTE]
> It is invalid for both `numberOfInputChannels` and
> `numberOfOutputChannels` to be zero.

### Return value

A {{domxref("ScriptProcessorNode")}}.

## Examples

### Adding white noise using a script processor

The following example shows how to use a `ScriptProcessorNode` to take a track loaded via {{domxref("BaseAudioContext/decodeAudioData", "AudioContext.decodeAudioData()")}}, process it, adding a bit of white noise to each audio sample of the input track, and play it through the {{domxref("AudioDestinationNode")}}.

For each channel and each sample frame, the script node's {{domxref("ScriptProcessorNode.audioprocess_event", "audioprocess")}} event handler uses the associated `audioProcessingEvent` to loop through each channel of the input buffer, and each sample in each channel, and add a small amount of white noise, before setting that result to be the output sample in each case.

> [!NOTE]
> You can [run the full example live](https://mdn.github.io/webaudio-examples/script-processor-node/), or [view the source](https://github.com/mdn/webaudio-examples/tree/main/script-processor-node).

```js
const myScript = document.querySelector("script");
const myPre = document.querySelector("pre");
const playButton = document.querySelector("button");

// Create AudioContext and buffer source
let audioCtx;

async function init() {
  audioCtx = new AudioContext();
  const source = audioCtx.createBufferSource();

  // Create a ScriptProcessorNode with a bufferSize of 4096 and
  // a single input and output channel
  const scriptNode = audioCtx.createScriptProcessor(4096, 1, 1);

  // Load in an audio track using fetch() and decodeAudioData()
  try {
    const response = await fetch("viper.ogg");
    const arrayBuffer = await response.arrayBuffer();
    source.buffer = await audioCtx.decodeAudioData(arrayBuffer);
  } catch (err) {
    console.error(
      `Unable to fetch the audio file: ${name} Error: ${err.message}`,
    );
  }

  // Give the node a function to process audio events
  scriptNode.addEventListener("audioprocess", (audioProcessingEvent) => {
    // The input buffer is the song we loaded earlier
    let inputBuffer = audioProcessingEvent.inputBuffer;

    // The output buffer contains the samples that will be modified and played
    let outputBuffer = audioProcessingEvent.outputBuffer;

    // Loop through the output channels (in this case there is only one)
    for (let channel = 0; channel < outputBuffer.numberOfChannels; channel++) {
      let inputData = inputBuffer.getChannelData(channel);
      let outputData = outputBuffer.getChannelData(channel);

      // Loop through the 4096 samples
      for (let sample = 0; sample < inputBuffer.length; sample++) {
        // make output equal to the same as the input
        outputData[sample] = inputData[sample];

        // add noise to each output sample
        outputData[sample] += (Math.random() * 2 - 1) * 0.1;
      }
    }
  });

  source.connect(scriptNode);
  scriptNode.connect(audioCtx.destination);
  source.start();

  // When the buffer source stops playing, disconnect everything
  source.addEventListener("ended", () => {
    source.disconnect(scriptNode);
    scriptNode.disconnect(audioCtx.destination);
  });
}

// wire up play button
playButton.addEventListener("click", () => {
  if (!audioCtx) {
    init();
  }
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
