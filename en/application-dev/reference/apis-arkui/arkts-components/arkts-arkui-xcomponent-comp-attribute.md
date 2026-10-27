# XComponent properties/events

```TypeScript
declare class XComponentAttribute extends CommonMethod<XComponentAttribute>
```

In addition to universal attributes, the following attributes are supported.

Since API version 12, the [universal events](arkts-arkui-common-comp.md) are supported when **type** is set to **SURFACE** or **TEXTURE**.

**Inheritance/Implementation:** XComponentAttribute extends CommonMethod&lt;XComponentAttribute&gt;

**Since:** 8

<!--Device-unnamed-declare class XComponentAttribute extends CommonMethod<XComponentAttribute>--><!--Device-unnamed-declare class XComponentAttribute extends CommonMethod<XComponentAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## bufferQueueCount

```TypeScript
bufferQueueCount(count: number)
```

Sets the buffer queue count for the XComponent. Only takes effect for XComponent of type SURFACE or TEXTURE. If the value is greater than 5, it is clamped to 5; if the value is less than 2, it is clamped to 2; if a non-integer value is passed, the default value 5 is used. Modifying the buffer queue count during buffer rotation may cause frame drops.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-XComponentAttribute-bufferQueueCount(count: number): XComponentAttribute--><!--Device-XComponentAttribute-bufferQueueCount(count: number): XComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Buffer queue count. The value ranges from 2 to 5. <br>Default value: **5**. |

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean)
```

Sets whether to enable the AI image analyzer, which supports subject recognition, text recognition, and object lookup.

For the settings to take effect, this attribute must be used together with [StartImageAnalyzer](arkts-arkui-xcomponent-comp-xcomponentcontroller-c.md#startimageanalyzer) and [StopImageAnalyzer](arkts-arkui-xcomponent-comp-xcomponentcontroller-c.md#stopimageanalyzer) of **XComponentController**.

This feature cannot be used together with the [overlay](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-overlay.md#overlay) attribute. If they are set at the same time, the **CustomBuilder** attribute in **overlay** has no effect. This feature depends on device capabilities.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentAttribute-enableAnalyzer(enable: boolean): XComponentAttribute--><!--Device-XComponentAttribute-enableAnalyzer(enable: boolean): XComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the AI analysis feature.<br>true: enables AI analysis; false: disables AI analysis.<br>Default value: false |

## enableSecure

```TypeScript
enableSecure(isSecure: boolean)
```

Sets whether to enable the secure surface to protect the content rendered within the component from being captured or recorded.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-XComponentAttribute-enableSecure(isSecure: boolean): XComponentAttribute--><!--Device-XComponentAttribute-enableSecure(isSecure: boolean): XComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isSecure | boolean | Yes | Whether to enable the privacy layer mode.<br>true: enables the privacy layer mode; false: disables the privacy layer mode.<br>Default value: false |

## hdrBrightness

```TypeScript
hdrBrightness(brightness: number)
```

Sets the brightness of HDR video playback for the component.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-XComponentAttribute-hdrBrightness(brightness: number): XComponentAttribute--><!--Device-XComponentAttribute-hdrBrightness(brightness: number): XComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brightness | number | Yes | Brightness of the HDR video.<br>Default value: **1.0**<br>Value range: [0.0, 1.0]. Values less than 0.0 are treated as 0.0, values greater than 1.0 are treated as 1.0, and other abnormal values are treated as 1.0.<br>0.0 indicates that the video is displayed at SDR brightness, and 1.0 indicates that the video is displayed at the highest HDR brightness currently allowed. |

## hdrBrightness

```TypeScript
hdrBrightness(brightness: number, type?: HdrType)
```

Adjusts the brightness when the component displays HDR content.<br> When the parameter **type** is set to a value other than [HdrType](arkts-arkui-xcomponent-comp-hdrtype-e.md).DEFAULT, before calling this API, check whether the **hdrFormats** attribute of [Display](../arkts-apis/arkts-arkui-display-display-i.md) contains the corresponding [HDRFormat](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-hdrcapability-hdrformat-e.md).<br>Only when **hdrFormats** contains the corresponding HDRFormat does the current device support the corresponding HDR type and the parameter setting take effect; otherwise, the default value [HdrType](arkts-arkui-xcomponent-comp-hdrtype-e.md).DEFAULT is used.<br> The mapping is as follows:

| Value of type | HDRFormat that hdrFormats must contain |  
| -------- | -------- |  
| [HdrType](arkts-arkui-xcomponent-comp-hdrtype-e.md).AIHDR | [HDRFormat](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-hdrcapability-hdrformat-e.md).VIDEO_AIHDR |

> **NOTE:** 

> - This API takes effect only when **type** in the XComponent constructor parameters is [XComponentType](../arkts-apis/arkts-arkui-xcomponenttype-e.md).SURFACE. Otherwise, it does not take effect.
> 
> - XComponent components created through the [ArkUI NDK APIs](../../../ui/ndk-build-ui-overview.md) are not supported.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-XComponentAttribute-hdrBrightness(brightness: number, type?: HdrType): XComponentAttribute--><!--Device-XComponentAttribute-hdrBrightness(brightness: number, type?: HdrType): XComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brightness | number | Yes | Brightness of the HDR content.<br>Default value: **1.0**<br>Value range: [0.0, 1.0]. Values less than 0.0 are treated as 0.0, values greater than 1.0 are treated as 1.0, and other abnormal values are treated as 1.0.<br>**0.0** indicates that the content is displayed at SDR brightness, and **1.0** indicates that the content is displayed at the maximum HDR brightness currently allowed. |
| type | [HdrType](arkts-arkui-xcomponent-comp-hdrtype-e.md) | No | HDR type used when displaying HDR content.<br>Default value: **HdrType.DEFAULT** |

## onDestroy

```TypeScript
onDestroy(event: VoidCallback)
```

Callback event triggered when native unloading is complete. Difference from [onSurfaceDestroyed](arkts-arkui-xcomponent-comp-xcomponentcontroller-c.md#onsurfacedestroyed): **onDestroy** applies to the scenario where the **libraryname** parameter is set, and the callback has no parameters; **onSurfaceDestroyed** applies to the scenario where the **libraryname** parameter is not set, and the callback parameter is **surfaceId**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentAttribute-onDestroy(event: VoidCallback): XComponentAttribute--><!--Device-XComponentAttribute-onDestroy(event: VoidCallback): XComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback invoked when the native component is unloaded.<br>**Since:** 18 |

## onLoad

```TypeScript
onLoad(callback: OnNativeLoadCallback)
```

Callback event triggered when native loading is complete.

> **NOTE:** 

> This callback is triggered only when the **libraryname** parameter is set for the **XComponent**. If the
> **libraryname** parameter is not set, use callbacks such as
> [onSurfaceCreated](arkts-arkui-xcomponent-comp-xcomponentcontroller-c.md#onsurfacecreated).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentAttribute-onLoad(callback: OnNativeLoadCallback): XComponentAttribute--><!--Device-XComponentAttribute-onLoad(callback: OnNativeLoadCallback): XComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnNativeLoadCallback](arkts-arkui-xcomponent-comp-onnativeloadcallback-t.md) | Yes | Callback invoked when the native content is loaded, used to obtain the context of the XComponent instance.<br>**Since:** 18 |
