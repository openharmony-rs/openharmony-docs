# FolderStack properties/events

In addition to the [universal events](arkts-arkui-commonmethod-c.md), the following events are supported.

**Inheritance/Implementation:** FolderStackAttribute extends CommonMethod<FolderStackAttribute>

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent(value: Alignment)
```

Sets the alignment of child components in the container. When both this attribute and the align attribute are set, whichever is set last takes effect.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) | Yes | Alignment of child components in the container.<br>Default value: **Alignment.Center**. <br>Invalid values are treated as the default value. |

## autoHalfFold

```TypeScript
autoHalfFold(value: boolean)
```

Sets whether to enable auto rotation. This attribute is effective only when auto rotation is disabled in device system settings.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable auto rotation. <br>Default value: **true**. **true**: Enable auto rotation when the **FolderStack** component is in [half-folded state](../../../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#foldstatus11). **false**: Disable auto rotation. This setting applies uniformly across all device types. <br>Invalid values are treated as the default value. |

## enableAnimation

```TypeScript
enableAnimation(value: boolean)
```

Sets whether to enable the default animation.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable the default animation.<br>Default value: **true**. **true**: Enable the default animation. **false**: Disable the default animation. <br>Invalid values are treated as the default value. |

## onFolderStateChange

```TypeScript
onFolderStateChange(callback: OnFoldStatusChangeCallback)
```

Triggered when the fold state of the device changes. This API takes effect only in landscape mode.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnFoldStatusChangeCallback](arkts-arkui-onfoldstatuschangecallback-t.md) | Yes | Callback invoked when the fold state of the device changes.<br>**Since:** 18 |

## onHoverStatusChange

```TypeScript
onHoverStatusChange(handler: OnHoverStatusChangeCallback)
```

Triggered when the hover state of the device changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnHoverStatusChangeCallback](arkts-arkui-onhoverstatuschangecallback-t.md) | Yes | Callback invoked when the hover state of the device changes.<br>**Since:** 18 |
