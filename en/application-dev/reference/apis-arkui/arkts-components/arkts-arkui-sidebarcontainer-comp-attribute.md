# SideBarContainer properties/events

```TypeScript
declare class SideBarContainerAttribute extends CommonMethod<SideBarContainerAttribute>
```

In addition to the universal attributes, the following attributes are supported.

In addition to the universal events, the following events are supported.

**Inheritance/Implementation:** SideBarContainerAttribute extends CommonMethod<SideBarContainerAttribute>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoHide

```TypeScript
autoHide(value: boolean)
```

Specifies whether to automatically hide the sidebar when it is dragged to be smaller than the minimum width. The value is subject to the **minSideBarWidth** attribute method. If it is not set in **minSideBarWidth**, the default value is used.

Whether the sidebar should be hidden is determined when it is being dragged. When it is dragged to be smaller than the minimum width, the damping effect is required to trigger hiding (a distance out of range).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to automatically hide the sidebar when it is dragged to be smaller than the minimum width.<br>**true**: The sidebar is automatically hidden.<br>**false**: The sidebar is not automatically hidden.<br>Default value: **true** |

## controlButton

```TypeScript
controlButton(value: ButtonStyle)
```

Sets the attributes of the sidebar control button.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ButtonStyle](arkts-arkui-sidebarcontainer-comp-buttonstyle-i.md) | Yes | Attributes of the sidebar control button. |

## divider

```TypeScript
divider(value: DividerStyle | null)
```

Sets the divider style.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DividerStyle](arkts-arkui-sidebarcontainer-comp-dividerstyle-i.md) &#124; null | Yes | Divider style.<br>- **DividerStyle** (default): The divider is displayed.<br>- **null** or **undefined**: No action is taken, and the divider style remains consistent with the default.<br>**NOTE:** <br>In API version 11 and earlier versions, **null** results in the divider not being displayed. |

## maxSideBarWidth

```TypeScript
maxSideBarWidth(value: number)
```

Sets the maximum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead.

**maxSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **maxWidth** of the sidebar child components.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Maximum width of the sidebar.<br>Default value: **280vp**<br>Unit: vp<br>Value range: [0, +∞). |

<a id="maxsidebarwidth-1"></a>

## maxSideBarWidth

```TypeScript
maxSideBarWidth(value: Length)
```

Sets the maximum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead. Compared with [maxSideBarWidth](#maxsidebarwidth), this API supports percentage strings and other pixel units for the **value** parameter.

**maxSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **maxWidth** of the sidebar child components.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Maximum width of the sidebar.<br>Default value: **280vp**<br>Unit: vp<br>Value range: [0, +∞). |

## minContentWidth

```TypeScript
minContentWidth(value: Dimension)
```

Sets the minimum content area width of the sidebar container.

If this attribute is set to a value less than 0, the default value **360vp** will be used. If this attribute is not set, the width of the content area can shrink to 0.

In Embed mode, when the component size is increased, only the content area is enlarged;

when the component size is decreased, the content area is shrunk until its width reaches the value defined by **minContentWidth**; if the component size is further decreased, while respecting the **minContentWidth** settings, the sidebar is shrunk

until its width reaches the value defined by **minSideBarWidth**; if the component size is further decreased, then:

- If [autoHide](#autohide) is set to **false**, while retaining the [minSideBarWidth](#minsidebarwidth) and **minContentWidth** settings, the content area has its content clipped.  
- If **autoHide** is set to **true**, the sidebar is hidden first, and then the content area is shrunk. After its  
width reaches the value defined by **minContentWidth**, the content area has its content clipped.

**minContentWidth** takes precedence over the [maxSideBarWidth](#maxsidebarwidth) and **sideBarWidth** attributes of the sidebar. If **minContentWidth** is not set, **minSideBarWidth** and **maxSideBarWidth** take precedence over its default value.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Minimum content area width of the sidebar container.<br>Default value: **360vp**<br> Unit: vp |

## minSideBarWidth

```TypeScript
minSideBarWidth(value: number)
```

Sets the minimum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead.

**minSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **minWidth** of the sidebar child components.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Minimum width of the sidebar.<br>Unit: vp. Value range: [0, +∞). Default value: In API version 9 and earlier versions, the default value is **200vp**. |

<a id="minsidebarwidth-1"></a>

## minSideBarWidth

```TypeScript
minSideBarWidth(value: Length)
```

Sets the minimum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead. Compared to [minSideBarWidth](#minsidebarwidth), this API supports percentage strings and other pixel units for the **value** parameter.

**minSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **minWidth** of the sidebar child components.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Minimum width of the sidebar.<br>Default value: In API version 9 and earlier versions, the default value is **200vp**. In API version 10, the default value is **240vp**.<br>Value range: [0, +∞). |

## onChange

```TypeScript
onChange(callback: (value: boolean) => void)
```

Triggered when the status of the sidebar switches between shown and hidden.

This event is triggered when any of the following conditions is met:

1. The value of the **showSideBar** attribute changes.
2. The adaptation of the **showSideBar** attribute changes.
3. [autoHide](#autohide) is triggered upon divider dragging.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: boolean) =&gt; void | Yes | **true**: The sidebar is shown. **false**: The sidebar is hidden. |

## showControlButton

```TypeScript
showControlButton(value: boolean)
```

Specifies whether to display the sidebar control button.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the sidebar control button.<br>**true**: The sidebar control button is displayed.<br>**false**: The sidebar control button is not displayed.<br>Default value: **true** |

## showSideBar

```TypeScript
showSideBar(value: boolean)
```

Specifies whether to display the sidebar.

Since API version 10, this attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the sidebar.<br>**true**: The sidebar is displayed.<br>**false**: The sidebar is not displayed.<br>Default value: **true** |

## showSideBarWithGesture

```TypeScript
showSideBarWithGesture(value: boolean)
```

Specifies whether sideBar can be presented or dismissed by gesture.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Indicates whether the sidebar can be presented or dismissed by gesture.<br>Default value: **false**. **true**: Sidebar can be presented or dismissed by gesture. **false**: Sidebar cannot be presented or dismissed by gesture. |

## sideBarPosition

```TypeScript
sideBarPosition(value: SideBarPosition)
```

Sets the position of the sidebar.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SideBarPosition](arkts-arkui-sidebarcontainer-comp-sidebarposition-e.md) | Yes | Position of the sidebar.<br>Default value: **SideBarPosition.Start** |

## sideBarWidth

```TypeScript
sideBarWidth(value: number)
```

Sets the width of the sidebar. If a value less than 0 is set, the default value is used. The value must comply with the width constraints. If it is not within the valid range, the valid value closest to the set one is used.

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Width of the sidebar.<br>Default value: **240vp**<br>Unit: vp<br>Value range: [0, +∞).<br>**NOTE:** <br>In API version 9 and earlier versions, the default value is **200vp**. In API version 10, the default value is **240vp**. |

<a id="sidebarwidth-1"></a>

## sideBarWidth

```TypeScript
sideBarWidth(value: Length)
```

Sets the width of the sidebar. If a value less than 0 is set, the default value is used. The value must comply with the width constraints. If it is not within the valid range, the valid value closest to the set one is used. Compared to [sideBarWidth](#sidebarwidth), this API supports percentage strings and other pixel units for the **value** parameter.

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width of the sidebar.<br>Default value: **240vp**<br>Unit: vp<br>Value range: [0, +∞).<br>**NOTE:** <br>The default value is **200vp** in API version 9 and **240vp** in API version 10. |
