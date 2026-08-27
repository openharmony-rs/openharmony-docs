# SideBarContainer

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @tsj_20201-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=4c495f520711bb7a7c0f878dd925391606600e97 translatedAt=2026-08-19T07:21:47.194Z pushedAt=2026-08-20T10:45:03.054Z -->

Provides a container that allows the sidebar to be shown and hidden. The sidebar and content area are defined by child components, with the first child component representing the sidebar and the second representing the content area. It supports sidebar navigation layout scenarios, where the sidebar can be shown or hidden through a control button or gesture, improving app navigation efficiency.

>  **NOTE**
>
>  The APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.

## Child Components

Supported

>  **NOTE**
>
>  - Allowed child component types: built-in and custom components, excluding rendering control types ([if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), and [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)).
>  - This component must contain two child components.
>  - If there are three or more child components, only the first and second child components are displayed. If there is only one child component, the sidebar is displayed, and the content area is blank.
>  - The focus navigation is performed in the content area and then in the sidebar of the **SideBarContainer** component.

## APIs

SideBarContainer( type?: SideBarContainerType )

Creates a sidebar container.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | [SideBarContainerType](#sidebarcontainertype) | No| Display type of the sidebar.<br>Default value: **SideBarContainerType.Embed**|

## SideBarContainerType

Enumerates the sidebar types of the container.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- |-------- |
| Embed | 0 | The sidebar is embedded in the component and displayed side by side with the content area. This mode applies to scenarios where both the sidebar and the content area need to be displayed.<br/>When the overall container size remains unchanged, showing the sidebar shrinks the content area, and hiding the sidebar expands the content area.<br/>When the component size is smaller than [minContentWidth](#mincontentwidth10) + [minSideBarWidth](#minsidebarwidth) and **showSideBar** is not set, the sidebar is not displayed by default.<br/>When the **showSideBar** attribute is set, the value set by the **showSideBar** attribute prevails.<br/>When [minSideBarWidth](#minsidebarwidth) or [minContentWidth](#mincontentwidth10) is not set, the default value of the corresponding API is used for calculation.<br/>After the component is automatically hidden, if the sidebar is brought up by tapping the control button, the sidebar floats over the content area.<br/>**Atomic service API:** This API can be used in atomic services since API version 11.|
| Overlay | 1 | The sidebar floats over the content area and does not affect the size of the content area. This mode applies to scenarios where the sidebar needs to be displayed temporarily.<br/>When the component size is smaller than [minContentWidth](#mincontentwidth10), the content area is displayed in a truncated manner.<br/>**Atomic service API:** This API can be used in atomic services since API version 11.|
| AUTO<sup>10+</sup> | 2 |When the component size is greater than or equal to [minSideBarWidth](#minsidebarwidth) + [minContentWidth](#mincontentwidth10), the Embed mode is used for display.<br/>When the component size is smaller than [minSideBarWidth](#minsidebarwidth) + [minContentWidth](#mincontentwidth10), the Overlay mode is used for display. This mode applies to scenarios that require responsive layout or multi-device adaptation.<br/>When [minSideBarWidth](#minsidebarwidth) or [minContentWidth](#mincontentwidth10) is not set, the default value of the unset API is used for calculation. If the calculated value is smaller than 600 vp, 600 vp is used as the threshold for mode switching.<br/>**Atomic service API:** This API can be used in atomic services since API version 11.<br/>**Model restriction:** This API can be used only in the stage model.|
| DISPLACE | 3 | The sidebar and the content area are displayed in parallel, and the overflow part of the content area is moved outside the component. When the sidebar is expanded, the content area is displayed with a gray overlay (color: #33000000) and events are disabled. You can tap the content area to collapse the sidebar.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.|

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### showSideBar

showSideBar(value: boolean)

Sets whether to display the sidebar. Setting this attribute triggers the show/hide animation of the sidebar.

When the **showSideBar** attribute is not set, the sidebar is automatically displayed based on the component size: it is hidden by default when the size is smaller than [minSideBarWidth](#minsidebarwidth) + [minContentWidth](#mincontentwidth10), and displayed by default when the size is greater than or equal to that value.

Since API version 10, this attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | boolean | Yes  | Whether to display the sidebar.<br>**true**: The sidebar is displayed.<br>**false**: The sidebar is not displayed.<br>Default value: **true**|

### controlButton

controlButton(value: ButtonStyle)

Sets the attributes of the sidebar control button. The control button is used to switch the sidebar between the shown and hidden states.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                               | Mandatory| Description                  |
| ------ | ----------------------------------- | ---- | ---------------------- |
| value  | [ButtonStyle](#buttonstyle) | Yes   | Style of the sidebar control button, used to configure the position, size, and icon of the control button. |

### showControlButton

showControlButton(value: boolean)

Sets whether to display the control button. The control button is used to toggle the **showSideBar** attribute. Tapping it shows or hides the sidebar and updates the **showSideBar** attribute value.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | boolean | Yes  | Whether to display the sidebar control button.<br>**true**: The sidebar control button is displayed.<br>**false**: The sidebar control button is not displayed.<br>Default value: **true**|

> **NOTE**
>
> The sidebar display or hiding animation is triggered when the sidebar is displayed or hidden by clicking the sidebar control button.

### sideBarWidth

sideBarWidth(value: number)

Sets the width of the sidebar. If a value less than 0 is set, the default value is used. The value is subject to the **minSideBarWidth** and **maxSideBarWidth** constraints. If it is not within the valid range, the closest boundary value is used.

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | number | Yes   | Width of the sidebar.<br/>Default value: **240vp**<br/>Unit: vp<br/>Value range: [0, +∞)<br/>The default value is used when an invalid value is set.<br/>**NOTE**<br/>The default value is **200vp** for API versions earlier than 10, and **240vp** for API version 10 and later. |

### sideBarWidth<sup>9+</sup>

sideBarWidth(value: Length)

Sets the width of the sidebar. If a value less than 0 is set, the default value is used. The value is subject to the **minSideBarWidth** and **maxSideBarWidth** constraints. If it is not within the valid range, the closest boundary value is used. Compared with [sideBarWidth](#sidebarwidth), the **value** parameter additionally supports percentage strings and other [pixel units](ts-pixel-units.md).

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [Length](ts-types.md#length) | Yes   | Width of the sidebar.<br/>Default value: **240vp**<br/>Unit: vp<br/>Value range: [0, +∞)<br/>If the value is abnormal, the default value is used.<br/>**NOTE**<br/>The default value is **200vp** since API version 9, and **240vp** since API version 10. |

### minSideBarWidth

minSideBarWidth(value: number)

Sets the minimum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead.

**minSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **minWidth** of the sidebar child components.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | number | Yes   | Minimum width of the sidebar.<br/>Default value: **200vp** for API version 9 and earlier, and **240vp** for API version 10 and later.<br/>Unit: vp<br/>Value range: [0, +∞)<br/>The default value is used when an invalid value is set. |

### minSideBarWidth<sup>9+</sup>

minSideBarWidth(value: Length)

Sets the minimum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead. Compared to [minSideBarWidth](#minsidebarwidth), this API supports percentage strings and other [pixel units](ts-pixel-units.md) for the **value** parameter.

**minSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **minWidth** of the sidebar child components.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [Length](ts-types.md#length) | Yes   | Minimum width of the sidebar.<br/>Default value: **200vp** for API version 9 and earlier, and **240vp** for API version 10 and later.<br/>Unit: vp<br/>Value range: [0, +∞)<br/>The default value is used when an invalid value is set. |

### maxSideBarWidth

maxSideBarWidth(value: number)

Sets the maximum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead.

**maxSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **maxWidth** of the sidebar child components.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                               |
| ------ | ------------------------------------------------------------ | ---- | --------------------------------------------------- |
| value  | number | Yes   | Maximum width of the sidebar.<br/>Default value: **280vp**<br/>Unit: vp<br/>Value range: [0, +∞)<br/>The default value is used when an invalid value is set.<br/>The value cannot exceed the width of the sidebar container itself. If it does, the width of the sidebar container itself is used. |

### maxSideBarWidth<sup>9+</sup>

maxSideBarWidth(value: Length)

Sets the maximum width of the sidebar. If a value less than 0 is set, the default value is used. The value cannot exceed the width of the sidebar container. If the specified value exceeds the sidebar container width, the container width is used instead. Compared with [maxSideBarWidth](#maxsidebarwidth), this API supports percentage strings and other [pixel units](ts-pixel-units.md) for the **value** parameter.

**maxSideBarWidth**, whether it is specified or kept at the default value, takes precedence over **maxWidth** of the sidebar child components.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                               |
| ------ | ------------------------------------------------------------ | ---- | --------------------------------------------------- |
| value  | [Length](ts-types.md#length) | Yes   | Maximum width of the sidebar.<br/>Default value: **280vp**<br/>Unit: vp<br/>Value range: [0, +∞)<br/>The default value is used when an exception occurs.<br/>The value cannot exceed the width of the sidebar container itself. If it does, the width of the sidebar container itself is used. |

### autoHide<sup>9+</sup>

autoHide(value: boolean)

Sets whether to automatically hide the sidebar when it is dragged to be smaller than the minimum width. The value is subject to the **minSideBarWidth** attribute method. If the **minSideBarWidth** attribute method is not set, the default value is used. After the sidebar is automatically hidden, the **showSideBar** attribute value is synchronously updated to **false**, and the **onChange** event is triggered.

Determines whether to automatically hide the sidebar during dragging. When the sidebar is dragged to be smaller than the minimum width, it must be dragged beyond the boundary by a certain distance (the specific distance is determined by the system implementation) to trigger automatic hiding, which provides a damping effect to avoid accidental operations.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | boolean | Yes  | Whether to automatically hide the sidebar when it is dragged to be smaller than the minimum width.<br>**true**: The sidebar is automatically hidden.<br>**false**: The sidebar is not automatically hidden.<br>Default value: **true**|

### sideBarPosition<sup>9+</sup>

sideBarPosition(value: SideBarPosition)

Sets the position of the sidebar.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                        | Mandatory| Description                                              |
| ------ | -------------------------------------------- | ---- | -------------------------------------------------- |
| value  | [SideBarPosition](#sidebarposition9) | Yes  | Position of the sidebar.<br>Default value: **SideBarPosition.Start**|

### divider<sup>10+</sup>

divider(value: DividerStyle | null)

Sets the divider style.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                     | Mandatory| Description                                                        |
| ------ | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [DividerStyle](#dividerstyle10)&nbsp;\|&nbsp;null | Yes   | Style of the divider.<br/>The default value is **DividerStyle**, which displays the divider.<br/>- **null** or **undefined**: The divider style remains the default value and is not changed.<br/>**Note:** <br/>In API version 11 and earlier, **null** means that the divider is not displayed.|

### minContentWidth<sup>10+</sup>

minContentWidth(value: Dimension)

Sets the minimum content area width of the sidebar container.

If this attribute is set to a value less than 0, the default value **360vp** will be used. If this attribute is not set, the width of the content area can shrink to 0.

In Embed mode, when the component size is increased, only the content area is enlarged;

when the component size is decreased, the content area is shrunk until its width reaches the value defined by **minContentWidth**; if the component size is further decreased, while respecting the **minContentWidth** settings, the sidebar is shrunk

until its width reaches the value defined by **minSideBarWidth**; if the component size is further decreased, then:

- If [autoHide](#autohide9) is set to **false**, while retaining the [minSideBarWidth](#minsidebarwidth) and **minContentWidth** settings, the content area has its content clipped.

- If **autoHide** is set to **true**, the sidebar is hidden first, and then the content area is shrunk. After its width reaches the value defined by **minContentWidth**, the content area has its content clipped.

**minContentWidth** takes precedence over the [maxSideBarWidth](#maxsidebarwidth) and **sideBarWidth** attributes of the sidebar. If **minContentWidth** is not set, **minSideBarWidth** and **maxSideBarWidth** take precedence over its default value.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                | Mandatory| Description                                                        |
| ------ | ------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [Dimension](ts-types.md#dimension10) | Yes   | Minimum width of the content area of the **SideBarContainer** component.<br/>Default value: **360vp**<br/>Value range: [0, +∞)<br/>If the value is less than 0, the default value is used. |

### showSideBarWithGesture

showSideBarWithGesture(value: boolean)

Sets whether the sidebar can be displayed or hidden by swiping. If this API is not called, the sidebar cannot be displayed or hidden by swiping.

> **NOTE**
>
> - The swipe gesture takes effect on the sidebar and content area (excluding the divider). When the swiping distance reaches 100 vp, the sidebar is displayed or hidden. The maximum swiping distance is equal to the width of the sidebar.
>
> - When the sidebar is on the left of the container:
>   - You can swipe right to expand the sidebar when it is hidden.
>   - You can swipe left to close the sidebar when it is displayed.
>
> - When the sidebar is on the right of the container:
>   - You can swipe left to expand the sidebar when it is hidden.
>   - You can swipe right to close the sidebar when it is displayed.
>

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name| Type                                | Mandatory| Description                                                        |
| ------ | ------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | boolean | Yes   | Whether to support showing or hiding the sidebar through gesture swiping.<br/>**true**: gesture swiping is supported.<br/>**false**: gesture swiping is not supported.<br/>Default value: **false** |

## ButtonStyle

Describes the style of the sidebar control button.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| left | number | No | Yes | Distance between the sidebar control button and the left edge of the container.<br/>Default value: **16vp**<br/>Unit: vp<br/>Value range: [0, +∞)<br/>The default value is used when an invalid value is set. |
| top | number | No| Yes| Spacing between the sidebar control button and the top of the container.<br>Default value: **48vp**<br>Unit: vp<br>Value range: [0, +∞).<br>If the value is abnormal, the default value is used.|
| width | number | No| Yes| Width of the sidebar control button.<br>Default value:<br>API version 9 and earlier versions: **32vp**<br>API version 10 and later versions: **24vp**<br>Unit: vp<br>Value range: [0, +∞).<br>If the value is abnormal, the default value is used.|
| height | number | No| Yes| Height of the sidebar control button.<br>Default value:<br>API version 9 and earlier versions: **32vp**<br>API version 10 and later versions: **24vp**<br>Unit: vp<br>Value range: [0, +∞).<br>If the value is abnormal, the default value is used.|
| icons | [ButtonIconOptions<sup>18+</sup>](#buttoniconoptions18) | No| Yes| Icons of the sidebar control button.<br>If the resource fails to be obtained or this attribute is not set, the default icon is used.|

## ButtonIconOptions<sup>18+</sup>

Describes the icons of the sidebar control button.

> **NOTE**
>
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18. While historical version information is preserved for anonymous objects, there may be cases where the outer element's @since version number is higher than inner elements'. This does not affect interface usability.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                          | Read-Only| Optional| Description                                       |
| --------- | ------------------------------- | ---- | ---- | ------------------------------------------ |
| shown<sup>8+</sup>     | string&nbsp;\|&nbsp;[PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md)&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | No| No  | Icon of the control button when the sidebar is displayed.<br>**Atomic service API**: This API can be used in atomic services since API version 11.             |
| hidden<sup>8+</sup>    | string&nbsp;\|&nbsp;[PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md)&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | No| No  | Icon of the control button when the sidebar is hidden.<br>**Atomic service API**: This API can be used in atomic services since API version 11.             |
| switching<sup>8+</sup> | string&nbsp;\|&nbsp;[PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md)&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | No| Yes  | Icon of the control button when the sidebar is switching between the shown and hidden states.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|

## SideBarPosition<sup>9+</sup>

Enumerates the positions of the sidebar.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | ---- | -------- |
| Start | 0 | The sidebar is on the left side of the container.|
| End | 1 | The sidebar is on the right side of the container.|

## DividerStyle<sup>10+</sup>

Sets the divider style.

>  **NOTE**
>
>  When [width](ts-universal-attributes-size.md#width) and [height](ts-universal-attributes-size.md#height) are set for the sidebar child component, neither takes effect.
>
>  When [width](ts-universal-attributes-size.md#width) and [height](ts-universal-attributes-size.md#height) are set for the sidebar content area, neither takes effect. By default, the content area occupies the remaining space of the **SideBarContainer**.
>
>  When the [showSideBar](#showsidebar) attribute is not set, the sidebar is displayed automatically based on the component size:
>
>  - Smaller than [minSideBarWidth](#minsidebarwidth) + [minContentWidth](#mincontentwidth10): the sidebar is not displayed by default.
>
>  - Greater than or equal to [minSideBarWidth](#minsidebarwidth) + [minContentWidth](#mincontentwidth10): the sidebar is displayed by default.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                          | Read-Only| Optional| Description                                       |
| --------- | ------------------------------- | ---- | ---- | ------------------------------------------ |
| strokeWidth | [Length](ts-types.md#length)        | No  | No   | Width of the divider.<br/>Default value: **1vp**<br/>Unit: vp<br/>Value range: [0, +∞)<br/>The default value is used when an abnormal value is set.<br/>**NOTE**<br/>The width of the divider does not support percentage settings. It has a lower priority than the [common attribute height](ts-universal-attributes-size.md#height). If the width exceeds the size set by the common attribute, it is clipped according to the common attribute. On some devices, the divider may not be displayed due to 1-pixel rounding in hardware. 2 px is recommended. |
| color       | [ResourceColor](ts-types.md#resourcecolor) | No| Yes  | Color of the divider.<br>Default value: **#000000**, 3%, black.  |
| startMargin | [Length](ts-types.md#length)        | No| Yes  | Distance between the divider and the top of the sidebar.<br>Default value: **0**<br>Unit: vp<br>Value range: [0, +∞).<br>If the value is abnormal, the default value is used.|
| endMargin   | [Length](ts-types.md#length)        | No| Yes  | Distance between the divider and the bottom of the sidebar.<br>Default value: **0**<br>Unit: vp<br>Value range: [0, +∞).<br>If the value is abnormal, the default value is used.|

## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onChange

onChange(callback: (value: boolean) =&gt; void)

Triggered when the status of the sidebar switches between shown and hidden.

This event is triggered when any of the following conditions is met:

1. The value of the **showSideBar** attribute changes.

2. The adaptation of the **showSideBar** attribute changes.

3. [autoHide](#autohide9) is triggered upon divider dragging.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                         |
| ------ | ------- | ---- | ----------------------------- |
| value | boolean | Yes | Whether the sidebar is displayed. The value **true** means to display the sidebar, and **false** means to hide it. |

## Example

This example demonstrates how to use the **SideBarContainer** component and implement the page layout.

```ts
// xxx.ets
@Entry
@Component
struct SideBarContainerExample {
  // Replace $r('app.media.icon') with the image resource file required.
  normalIcon: Resource = $r('app.media.icon');
  selectedIcon: Resource = $r('app.media.icon');
  @State menuItems: number[] = [1, 2, 3];
  @State selectedItemId: number = 1;

  build() {
    SideBarContainer(SideBarContainerType.Embed) {
      Column() {
        ForEach(this.menuItems, (item: number) => {
          Column({ space: 5 }) {
            Image(this.selectedItemId === item ? this.selectedIcon : this.normalIcon).width(64).height(64)
            Text('Index0' + item)
              .fontSize(25)
              .fontColor(this.selectedItemId === item ? '#0A59F7' : '#999')
              .fontFamily('source-sans-pro,cursive,sans-serif')
          }
          .onClick(() => {
            this.selectedItemId = item;
          })
        }, (item: number) => item.toString())
      }.width('100%')
      .justifyContent(FlexAlign.SpaceEvenly)
      .backgroundColor('#19000000')

      Column() {
        Text('SideBarContainer content text1').fontSize(25)
        Text('SideBarContainer content text2').fontSize(25)
      }
      .margin({ top: 50, left: 20, right: 30 })
    }
    .controlButton({
      icons: {
        // Replace $r('app.media.drawer') with the image resource file you use.
        hidden: $r('app.media.drawer'),
        shown: $r('app.media.drawer'),
        switching: $r('app.media.drawer')
      }
    })
    .sideBarWidth(150)
    .minSideBarWidth(50)
    .maxSideBarWidth(300)
    .minContentWidth(0)
    .onChange((value: boolean) => {
      console.info('status:' + value);
    })
    .divider({ strokeWidth: '1vp', color: Color.Gray, startMargin: '4vp', endMargin: '4vp' })
  }
}
```

![](figures/sidebarcontainer.png)