# FolderStack properties/events

```TypeScript
declare class FolderStackAttribute extends CommonMethod<FolderStackAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported.

> **NOTE:** 
> 
> Setting the **offset** and **margin** attributes may cause the upper and lower screens to obscure the fold crease
> area. This is not recommended.

**Inheritance/Implementation:** FolderStackAttribute extends CommonMethod<FolderStackAttribute>

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent(value: Alignment)
```

Sets the alignment of child components in the container. After this attribute is set, child components are arranged in the container according to the specified alignment. When both this attribute and [align](arkts-arkui-common-comp-commonmethod-c.md#align) are set, whichever is set last takes effect.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) | Yes | Alignment of the child component in the container. The value can be **TopStart**, **Top**, **TopEnd**, **Start**, **Center**, **End**, **BottomStart**, **Bottom**, or **BottomEnd**.<br>Default value: **Alignment.Center** <br>If an illegal value is set, the default value is used. |

## autoHalfFold

```TypeScript
autoHalfFold(value: boolean)
```

Sets whether to enable auto-rotation for the **FolderStack** component in half-fold status. When the system auto- rotate switch is turned off, this attribute controls whether **FolderStack** performs auto-rotation in half-fold status.

Typical usage: When the user has turned off the auto-rotate function in system settings, the app layout orientation can still be automatically adjusted based on the fold status when the foldable device is in half-fold status.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable auto rotation.<br>Default value: **true**. When set to **true**, **FolderStack** automatically rotates during layout in the half-fold status (see FoldStatus). When set to **false**, FolderStack does not automatically rotate in the half-fold status. This attribute takes effect only when system auto rotation is disabled. When system auto rotation is enabled, this attribute does not take effect, and **FolderStack** follows the system rotation behavior. This parameter takes effect only on dual-fold devices. When the parent component of **FolderStack** is an if/else conditional rendering node, this parameter becomes invalid. <br>Illegal value: processed as the default value. |

## enableAnimation

```TypeScript
enableAnimation(value: boolean)
```

Sets whether to use the default animation effect. After this attribute is set, the default hover animation effect of **FolderStack** is enabled or disabled.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to use the default animation effect.<br>Default value: **true**, which means the default animation effect is used; **false** means the default animation effect is not used. <br>If an illegal value is set, the default value is used. |

## onFolderStateChange

```TypeScript
onFolderStateChange(callback: OnFoldStatusChangeCallback)
```

Triggered when the fold status of the current device changes &lt;!--RP3--&gt;(This callback takes effect only in landscape mode.)&lt;!--RP3End--&gt;.

Typical usage: Adjust the app layout based on the fold status, for example, displaying a two-column layout in the expanded state and adjusting the content distribution between the upper and lower screens in the half-fold status.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnFoldStatusChangeCallback](arkts-arkui-folderstack-comp-onfoldstatuschangecallback-t.md) | Yes | Callback invoked when the fold state of the device changes.<br>**Since:** 18 |

## onHoverStatusChange

```TypeScript
onHoverStatusChange(handler: OnHoverStatusChangeCallback)
```

Triggered when the hover status of the current device changes.

Typical usage: Adjust the app layout and interaction logic based on the hover status, for example, optimizing the content display on the upper and lower screens in hover mode.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnHoverStatusChangeCallback](arkts-arkui-folderstack-comp-onhoverstatuschangecallback-t.md) | Yes | Callback invoked when the hover state of the device changes.<br>**Since:** 18 |
