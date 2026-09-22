# XComponent properties/events

```TypeScript
declare class XComponentAttribute extends CommonMethod<XComponentAttribute>
```

In addition to universal attributes, the following attributes are supported.

Since API version 12, the [universal events](arkts-arkui-common-comp.md#common) are supported when **type** is set to **SURFACE** or **TEXTURE**.

**Inheritance/Implementation:** XComponentAttribute extends CommonMethod<XComponentAttribute>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the AI image analyzer.<br>**true**: enable; **false**: disable<br> Default value: **false**. |

## enableSecure

```TypeScript
enableSecure(isSecure: boolean)
```

Sets whether to enable the secure surface to protect the content rendered within the component from being captured or recorded.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isSecure | boolean | Yes | Whether to enable the secure surface.<br>The value **true** means to enable the secure surface, and **false** means the opposite.<br>Default value: **false**. |

## hdrBrightness

```TypeScript
hdrBrightness(brightness: number)
```

Sets the brightness of HDR video playback for the component.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brightness | number | Yes | Brightness of HDR video playback.<br>Value range: 0.0 to 1.0. Values less than 0.0 are equivalent to 0.0, and values greater than 1.0 are equivalent to 1.0. **0.0** indicates the brightness of the SDR video, and **1.0** indicates the brightness of the HDR video.<br>Default value: **1.0**. |

<a id="hdrbrightness-1"></a>

## hdrBrightness

```TypeScript
hdrBrightness(brightness: number, type?: HdrType)
```

Set hdrBrightness for XComponent.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brightness | number | Yes | control the brightness of HDR video. |
| type | [HdrType](arkts-arkui-xcomponent-comp-hdrtype-e.md) | No | the HDR type of the XComponent. |

## onDestroy

```TypeScript
onDestroy(event: VoidCallback)
```

Triggered when the plugin is destroyed.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback triggered after **XComponent** is destroyed.<br>**Since:** 18 |

## onLoad

```TypeScript
onLoad(callback: OnNativeLoadCallback)
```

Triggered when the plugin is loaded.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnNativeLoadCallback](arkts-arkui-xcomponent-comp-onnativeloadcallback-t.md) | Yes | Callback triggered after the surface held by **XComponent** is created.<br>**Since:** 18 |
