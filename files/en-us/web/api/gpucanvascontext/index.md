---
title: GPUCanvasContext
slug: Web/API/GPUCanvasContext
page-type: web-api-interface
browser-compat: api.GPUCanvasContext
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

The **`GPUCanvasContext`** interface of the {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} represents the WebGPU rendering context of a {{htmlelement("canvas")}} element, returned via an {{domxref("HTMLCanvasElement.getContext()")}} call with a `contextType` of `"webgpu"`.

{{InheritanceDiagram}}

## Instance properties

- {{domxref("GPUCanvasContext.canvas", "canvas")}} {{ReadOnlyInline}}
  - : Returns a reference to the canvas that the context was created from.

## Instance methods

- {{domxref("GPUCanvasContext.configure", "configure()")}}
  - : Configures the context to use for rendering with a given {{domxref("GPUDevice")}} and clears the canvas to transparent black.
- {{domxref("GPUCanvasContext.getConfiguration", "getConfiguration()")}}
  - : Returns the current configuration set for the context.
- {{domxref("GPUCanvasContext.getCurrentTexture", "getCurrentTexture()")}}
  - : Returns the next {{domxref("GPUTexture")}} to be composited to the document by the canvas context.
- {{domxref("GPUCanvasContext.unconfigure", "unconfigure()")}}
  - : Removes any previously-set context configuration, and destroys any textures produced while the canvas context was configured.

## Examples

```js
const canvas = document.querySelector("#gpuCanvas");
const context = canvas.getContext("webgpu");

context.configure({
  device,
  format: navigator.gpu.getPreferredCanvasFormat(),
  alphaMode: "premultiplied",
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- The [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
