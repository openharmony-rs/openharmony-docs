# SideBarContainer properties/events

```TypeScript
declare class SideBarContainerAttribute extends CommonMethod<SideBarContainerAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

**Inheritance/Implementation:** SideBarContainerAttribute extends CommonMethod&lt;SideBarContainerAttribute&gt;

**Since:** 8

<!--Device-unnamed-declare class SideBarContainerAttribute extends CommonMethod<SideBarContainerAttribute>--><!--Device-unnamed-declare class SideBarContainerAttribute extends CommonMethod<SideBarContainerAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoHide

```TypeScript
autoHide(value: boolean)
```

Sets whether to automatically hide the sidebar when it is dragged to be smaller than the minimum width. The value is subject to the **minSideBarWidth** attribute method. If the **minSideBarWidth** attribute method is not set, the default value is used. After the sidebar is automatically hidden, the **showSideBar** attribute value is synchronously updated to **false**, and the **onChange** event is triggered.

Determines whether to automatically hide the sidebar during dragging. When the sidebar is dragged to be smaller than the minimum width, it must be dragged beyond the boundary by a certain distance (the specific distance is determined by the system implementation) to trigger automatic hiding, which provides a damping effect to avoid accidental operations.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-autoHide(value: boolean): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-autoHide(value: boolean): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to automatically hide the sidebar when it is dragged to be smaller than the minimum width.<br>**true**: The sidebar is automatically hidden. <br>**false**: The sidebar is not automatically hidden. <br>Default value: **true** |

## controlButton

```TypeScript
controlButton(value: ButtonStyle)
```

Sets the attributes of the sidebar control button. The control button is used to switch the sidebar between the shown and hidden states.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-controlButton(value: ButtonStyle): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-controlButton(value: ButtonStyle): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ButtonStyle](arkts-arkui-sidebarcontainer-comp-buttonstyle-i.md) | Yes | Style of the sidebar control button, used to configure the position, size, and icon of the control button. |

## divider

```TypeScript
divider(value: DividerStyle | null)
```

Sets the divider style.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-divider(value: DividerStyle | null): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-divider(value: DividerStyle | null): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DividerStyle](arkts-arkui-sidebarcontainer-comp-dividerstyle-i.md) &#124; null | Yes | Style of the divider.<br>The default value is **DividerStyle**, which displays the divider.<br>- **null** or **undefined**: The divider style remains the default value and is not changed.<br>**Note:** <br>In API version 11 and earlier, **null** means that the divider is not displayed. |

<a id="maxsidebarwidth1"></a>

## maxSideBarWidth

```TypeScript
maxSideBarWidth(value: number)
```

Sets the maximum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead.

**maxSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **maxWidth** of the sidebar child components.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-maxSideBarWidth(value: number): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-maxSideBarWidth(value: number): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Maximum width of the sidebar.<br>Default value: **280vp**<br>Unit: vp<br>Value range: [0, +∞)<br>The default value is used when an invalid value is set.<br>The value cannot exceed the width of the sidebar container itself. If it does, the width of the sidebar container itself is used. |

<a id="maxsidebarwidth2"></a>

## maxSideBarWidth

```TypeScript
maxSideBarWidth(value: Length)
```

Sets the maximum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead. Compared with [maxSideBarWidth](#maxsidebarwidth1), this API supports percentage strings and other [pixel units](arkts-arkui-common-comp.md) for the **value** parameter.

**maxSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **maxWidth** of the sidebar child components.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-maxSideBarWidth(value: Length): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-maxSideBarWidth(value: Length): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Maximum width of the sidebar.<br>Default value: **280vp**<br>Unit: vp<br>Value range: [0, +∞)<br>The default value is used when an exception occurs.<br> The value cannot exceed the width of the sidebar container itself. If it does, the width of the sidebar container itself is used. |

## minContentWidth

```TypeScript
minContentWidth(value: Dimension)
```

Sets the minimum content area width of the sidebar container.

If this attribute is set to a value less than 0, the default value **360vp** will be used. If this attribute is not set, the width of the content area can shrink to 0.

In Embed mode, when the component size is increased, only the content area is enlarged;

when the component size is decreased, the content area is shrunk until its width reaches the value defined by **minContentWidth**; if the component size is further decreased, while respecting the **minContentWidth** settings, the sidebar is shrunk

until its width reaches the value defined by **minSideBarWidth**; if the component size is further decreased, then:

- If [autoHide](#autohide) is set to **false**, while retaining the [minSideBarWidth](#minsidebarwidth1) and **minContentWidth** settings, the content area has its content clipped.  
- If **autoHide** is set to **true**, the sidebar is hidden first, and then the content area is shrunk. After its  
width reaches the value defined by **minContentWidth**, the content area has its content clipped.

**minContentWidth** takes precedence over the [maxSideBarWidth](#maxsidebarwidth1) and **sideBarWidth** attributes of the sidebar. If **minContentWidth** is not set, **minSideBarWidth** and **maxSideBarWidth** take precedence over its default value.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-minContentWidth(value: Dimension): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-minContentWidth(value: Dimension): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Minimum width of the content area of the **SideBarContainer** component.<br>Default value: **360vp**<br>Value range: [0, +∞)<br>If the value is less than 0, the default value is used. |

<a id="minsidebarwidth1"></a>

## minSideBarWidth

```TypeScript
minSideBarWidth(value: number)
```

Sets the minimum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead.

**minSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **minWidth** of the sidebar child components.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-minSideBarWidth(value: number): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-minSideBarWidth(value: number): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Minimum width of the sidebar.<br>Default value: **200vp** for API version 9 and earlier, and **240vp** for API version 10 and later.<br>Unit: vp<br>Value range: [0, +∞)<br>The default value is used when an invalid value is set. |

<a id="minsidebarwidth2"></a>

## minSideBarWidth

```TypeScript
minSideBarWidth(value: Length)
```

Sets the minimum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead. Compared to [minSideBarWidth](#minsidebarwidth1), this API supports percentage strings and other [pixel units](arkts-arkui-common-comp.md) for the **value** parameter.

**minSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **minWidth** of the sidebar child components.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-minSideBarWidth(value: Length): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-minSideBarWidth(value: Length): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Minimum width of the sidebar.<br>Default value: **200vp** for API version 9 and earlier, and **240vp** for API version 10 and later.<br>Unit: vp<br>Value range: [0, +∞)<br>The default value is used when an invalid value is set. |

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

<!--Device-SideBarContainerAttribute-onChange(callback: (value: boolean) => void): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-onChange(callback: (value: boolean) => void): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: boolean) =&gt; void | Yes | **true**: The sidebar is shown. **false**: The sidebar is hidden. |

## showControlButton

```TypeScript
showControlButton(value: boolean)
```

Sets whether to display the control button. The control button is used to toggle the **showSideBar** attribute. Tapping it shows or hides the sidebar and updates the **showSideBar** attribute value.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-showControlButton(value: boolean): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-showControlButton(value: boolean): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the sidebar control button.<br>**true**: The sidebar control button is displayed. <br>**false**: The sidebar control button is not displayed. <br>Default value: **true** |

## showSideBar

```TypeScript
showSideBar(value: boolean)
```

Sets whether to display the sidebar. Setting this attribute triggers the show/hide animation of the sidebar.

When the **showSideBar** attribute is not set, the sidebar is automatically displayed based on the component size: it is hidden by default when the size is smaller than [minSideBarWidth](#minsidebarwidth1) + [minContentWidth](#mincontentwidth), and displayed by default when the size is greater than or equal to that value.

Since API version 10, this attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-showSideBar(value: boolean): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-showSideBar(value: boolean): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the sidebar.<br>**true**: The sidebar is displayed. <br>**false**: The sidebar is not displayed. <br>Default value: **true** |

## showSideBarWithGesture

```TypeScript
showSideBarWithGesture(value: boolean)
```

Sets whether the sidebar can be displayed or hidden by swiping. If this API is not called, the sidebar cannot be displayed or hidden by swiping.

> **NOTE:** 
> 
> - The swipe gesture takes effect on the sidebar and content area (excluding the divider). When the swiping distance reaches 100 vp, the sidebar is displayed or hidden. The maximum swiping distance is equal to the width of the sidebar.
> 
> - When the sidebar is on the left of the container:
> 
> - You can swipe right to expand the sidebar when it is hidden.
> 
> - You can swipe left to close the sidebar when it is displayed.
> 
> - When the sidebar is on the right of the container:
> 
> - You can swipe left to expand the sidebar when it is hidden.
> 
> - You can swipe right to close the sidebar when it is displayed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SideBarContainerAttribute-showSideBarWithGesture(value: boolean): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-showSideBarWithGesture(value: boolean): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to support showing or hiding the sidebar through gesture swiping.<br>**true**: gesture swiping is supported.<br>**false**: gesture swiping is not supported.<br>Default value: **false** |

## sideBarPosition

```TypeScript
sideBarPosition(value: SideBarPosition)
```

Sets the position of the sidebar.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-sideBarPosition(value: SideBarPosition): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-sideBarPosition(value: SideBarPosition): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SideBarPosition](arkts-arkui-sidebarcontainer-comp-sidebarposition-e.md) | Yes | Position of the sidebar.<br>Default value: **SideBarPosition.Start** |

<a id="sidebarwidth1"></a>

## sideBarWidth

```TypeScript
sideBarWidth(value: number)
```

Sets the width of the sidebar. If a value less than 0 is set, the default value is used. The value is subject to the **minSideBarWidth** and **maxSideBarWidth** constraints. If it is not within the valid range, the closest boundary value is used.

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-sideBarWidth(value: number): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-sideBarWidth(value: number): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Width of the sidebar.<br>Default value: **240vp**<br>Unit: vp<br>Value range: [0, +∞)<br>The default value is used when an invalid value is set.<br>**NOTE:** <br> The default value is **200vp** for API versions earlier than 10, and **240vp** for API version 10 and later. |

<a id="sidebarwidth2"></a>

## sideBarWidth

```TypeScript
sideBarWidth(value: Length)
```

Sets the width of the sidebar. If a value less than 0 is set, the default value is used. The value is subject to the **minSideBarWidth** and **maxSideBarWidth** constraints. If it is not within the valid range, the closest boundary value is used. Compared with [sideBarWidth](#sidebarwidth1), the **value** parameter additionally supports percentage strings and other [pixel units](arkts-arkui-common-comp.md).

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SideBarContainerAttribute-sideBarWidth(value: Length): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-sideBarWidth(value: Length): SideBarContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width of the sidebar.<br>Default value: **240vp**<br>Unit: vp<br>Value range: [0, +∞)<br>If the value is abnormal, the default value is used.<br> **NOTE:** <br>The default value is **200vp** since API version 9, and **240vp** since API version 10. |
