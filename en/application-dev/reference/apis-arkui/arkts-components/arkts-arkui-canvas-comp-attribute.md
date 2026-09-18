# Canvas properties/events

In addition to the universal attributes, the following attributes are supported.

The universal events are supported.

**Inheritance/Implementation:** CanvasAttribute extends CommonMethod<CanvasAttribute>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean)
```

Sets whether to enable the AI image analyzer, which supports subject recognition, text recognition, and object lookup.

For the settings to take effect, this attribute must be used together with [startImageAnalyzer](arkts-arkui-canvasrenderingcontext2d-c.md#startimageanalyzer) and [stopImageAnalyzer](arkts-arkui-canvasrenderingcontext2d-c.md#stopimageanalyzer) of CanvasRenderingContext2D.

This attribute cannot be used together with the overlay attribute. If they are set at the same time, the **CustomBuilder** attribute in **overlay** has no effect. This feature depends on device capabilities.

> **NOTE:** 
> 
> This API can be called within
> attributeModifier
> since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the AI image analyzer for subject recognition, text recognition, and object lookup within the component content.<br>**true**: Enable the AI image analyzer. **false**: Disable the AI analyzer. <br>The **null** and **undefined** values are handled as the default value. <br>Default value: **false** |

## onReady

```TypeScript
onReady(event: VoidCallback)
```

Triggered when the **Canvas** component is initialized or when its size changes.

When this event is triggered, the canvas is cleared. The width and height of the **Canvas** component are then determined and can be obtained, allowing you to use APIs related to the **Canvas** component for drawing. If only the position of the canvas changes, only the [onAreaChange](arkts-arkui-commonmethod-c.md#onareachange) event is triggered, not the **onReady** event. The [onAreaChange](arkts-arkui-commonmethod-c.md#onareachange) event is triggered after the **onReady** event.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Triggered when the **Canvas** component is initialized or when its size changes. |

## onReady

```TypeScript
onReady(event: Callback<DrawingRenderingContext | undefined> | undefined)
```

Triggered when the **Canvas** component is initialized or when its size changes.

When this event is triggered, the canvas is cleared. The width and height of the **Canvas** component are then determined and can be obtained, allowing you to use APIs related to the **Canvas** component for drawing. If only the position of the canvas changes, only the [onAreaChange](arkts-arkui-commonmethod-c.md#onareachange) event is triggered, not the **onReady** event. The [onAreaChange](arkts-arkui-commonmethod-c.md#onareachange) event is triggered after the **onReady** event.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[DrawingRenderingContext](arkts-arkui-drawingrenderingcontext-c.md) &#124; undefined&gt; &#124; undefined | Yes | Triggered when the **Canvas** component is initialized or when its size changes. <br>Constraints on input parameters of the Callback&lt;DrawingRenderingContext &#124; undefined&gt; type: <br>1. Only **Canvas** components created using [CanvasParams](arkts-arkui-canvasparams-i.md) will return a **DrawingRenderingContext** object in this callback; otherwise, **undefined** is returned. <br>2. The **DrawingRenderingContext** object returned by this callback must not be used as a parameter to create **Canvas** components, as doing so will cause the application to crash. |
