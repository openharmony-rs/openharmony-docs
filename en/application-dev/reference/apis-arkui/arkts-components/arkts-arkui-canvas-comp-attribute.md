# Canvas properties/events

```TypeScript
declare class CanvasAttribute extends CommonMethod<CanvasAttribute>
```

In addition to the universal attributes, the following attributes are supported.

The universal events are supported.

**Inheritance/Implementation:** CanvasAttribute extends CommonMethod<CanvasAttribute>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean)
```

Sets whether to enable the AI image analyzer, which supports subject recognition, text recognition, and object lookup. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

This API must be used together with [startImageAnalyzer](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md#startimageanalyzer) and [stopImageAnalyzer](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md#stopimageanalyzer) in [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md).

This attribute cannot be used together with the [overlay](arkts-arkui-common-comp-commonmethod-c.md#overlay) attribute. If they are set at the same time, the **CustomBuilder** attribute in **overlay** will become invalid. This feature depends on the device capability. You can use the [ImageAnalyzerController.getImageAnalyzerSupportTypes](../arkts-apis/arkts-arkui-imageanalyzercontroller-c.md#getimageanalyzersupporttypes) API to query the analysis types supported by the device.

> **NOTE:** 
> 
> This API can be called within
> [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)
> since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the AI analysis function for the component. When enabled, the component content must support subject recognition, text recognition, or object search.<br>When set to **true**, the component can perform AI analysis; when set to **false**, the component cannot perform AI analysis. <br>Abnormal values **null** and **undefined** are processed as **false**. <br>Default value: **false** |

## onReady

```TypeScript
onReady(event: VoidCallback)
```

Triggered when the **Canvas** component is initialized or when its size changes. Dynamic attribute setting using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) is supported.

When this event is triggered, the canvas is cleared. The width and height of the **Canvas** component are then determined and can be obtained, allowing you to use APIs related to the **Canvas** component for drawing. If only the position of the canvas changes, only the [onAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onareachange) event is triggered, not the **onReady** event. The [onAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onareachange) event is triggered after the **onReady** event.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback event triggered when the **Canvas** component initialization is complete or when its size changes. |

<a id="onready-1"></a>

## onReady

```TypeScript
onReady(event: Callback<DrawingRenderingContext | undefined> | undefined)
```

Triggered when the **Canvas** component is initialized or when its size changes. Dynamic attribute setting using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) is supported.

When this event is triggered, the canvas is cleared. The width and height of the **Canvas** component are then determined and can be obtained, allowing you to use APIs related to the **Canvas** component for drawing. If only the position of the canvas changes, only the [onAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onareachange) event is triggered, not the **onReady** event. The [onAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onareachange) event is triggered after the **onReady** event.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[DrawingRenderingContext](arkts-arkui-canvas-comp-drawingrenderingcontext-c.md) &#124; undefined&gt; &#124; undefined | Yes | Callback invoked when the **Canvas** component initialization is complete or when its size changes. <br>Regarding the input parameter of the **Callback&lt;DrawingRenderingContext &#124; undefined&gt;** type: <br>1. Only the **Canvas** component created using [CanvasParams](arkts-arkui-canvas-comp-canvasparams-i.md) returns a **DrawingRenderingContext** object in this callback; otherwise, **undefined** is returned. <br>2. The **DrawingRenderingContext** object returned by this callback must not be used as a parameter to create a **Canvas** component; otherwise, the app will crash. |
