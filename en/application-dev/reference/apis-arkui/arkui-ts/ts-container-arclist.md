# ArcList

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z; @wind_-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=a1851c4d823f8d0aa6d877d6e720d89b0f7206a1 translatedAt=2026-08-21T02:21:01.411Z pushedAt=2026-08-21T06:17:14.538Z -->

An arc list consists of a series of list items arranged along an arc, suitable for circular screen devices. It is ideal for continuously presenting multiple rows of similar data, such as images and text.

> **NOTE**
>
> - This component is supported since API version 18. Updates will be marked with a superscript to indicate their earliest API version.
> - This component can be used on phones, PCs, 2-in-1 devices, tablets, TVs, and wearables. In API version 22 and earlier versions, a compilation warning will be reported when this component is used on phones, PCs, 2-in-1 devices, tablets, and TVs, but the component can still run properly.

## Modules to Import

> **NOTE**
>
> - **ArcListAttribute** is essential for configuring the **ArcList** component. In API version 21 and earlier, you must manually import **ArcListAttribute** after importing the **ArcList** component. Otherwise, a compilation error is reported. However, starting from API version 22, the compilation toolchain automatically imports **ArcListAttribute** when it detects the **ArcList** component, so manual import is no longer necessary.
>
> - If you manually import **ArcListAttribute**, DevEco Studio shows it as disabled (grayed out). In API version 21 and earlier, removing this import causes a compilation error. But from API version 22 onward, removing it does not affect the functionality.

API version 21 and earlier:

```ts
import { ArcList, ArcListAttribute } from '@kit.ArkUI';
```

API version 22 and later:

```ts
import { ArcList } from '@kit.ArkUI';
```

## Child Components

Only the [ArcListItem](ts-container-arclistitem.md) component is supported.

> **NOTE**
>
> Rules for calculating the index value of child components in **ArcList**:
>
> - The index value increments sequentially based on the order of child components.
>
> - In an [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) statement, only the child components in the branch where the condition is true participate in index value calculation. Child components in branches where the condition is false are not counted.
>
> - In a [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)/[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) statement, the index values of all expanded child components are calculated.
>
> - When [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), and [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) change, the child component index values are updated.
>
> - Child components of **ArcList** with the [visibility](ts-universal-attributes-visibility.md#visibility) attribute set to **Hidden** or **None** still have their index values calculated.

## APIs

ArcList(options?: ArkListOptions)

Creates an **ArcList** component instance with specified configuration options.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                 | Mandatory| Description               |
| ------- | ----------------------------------------- | ---- | ----------------------- |
| options | [ArkListOptions](#arklistoptions) | No | Configuration options for the arc list, used to set the initial loading position, scroll controller, and header component. |

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported (the [scrollable component common attributes](ts-container-scrollable-common.md#attributes) are not supported):

### digitalCrownSensitivity

digitalCrownSensitivity(sensitivity: Optional\<CrownSensitivity>)

Sets the crown response sensitivity.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name     | Type                                                        | Mandatory| Description                                                        |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensitivity | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[CrownSensitivity](ts-appendix-enums.md#crownsensitivity18)&gt; | Yes | Crown response sensitivity.<br>Default value: **CrownSensitivity.MEDIUM**, which indicates a moderate response speed. |

### space

space(space: Optional\<LengthMetrics>)

Sets the spacing between list child items.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                                        | Mandatory| Description                              |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------------- |
| space | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)&gt; | Yes | Spacing between child components in the list.<br>Default value: **LengthMetrics.vp(0)**<br>When the [visibility](ts-universal-attributes-visibility.md#visibility) attribute of an **ArcList** child component is set to **None**, the child component is not displayed, but the **space** above and below it still takes effect. |

### scrollBar

scrollBar(status: Optional\<BarState>)

Sets the state of the scrollbar.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                                | Mandatory| Description                                    |
| ------ | ---------------------------------------------------- | ---- | ---------------------------------------- |
| status | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[BarState](ts-appendix-enums.md#barstate)&gt; | Yes | Scroll bar status.<br>Default value: **BarState.Auto** |

### cachedCount

cachedCount(count: Optional\<number>)

Sets the number of arc list items to be preloaded (cached). In a lazy loading scenario, only the content equivalent to **cachedCount** outside the visible area of the arc list is preloaded. In a non-lazy loading scenario, all items are loaded at once. For both lazy and non-lazy loading, only the content within the visible area of the arc list plus the content equivalent to **cachedCount** outside the visible area is laid out.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type             | Mandatory| Description                                      |
| ------ | ----------------- | ---- | ------------------------------------------ |
| count  | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<number> | Yes   | Number of **ArcListItem** items to preload.<br>Default value: set based on the number of nodes displayed on the screen, with a maximum of 16.<br>Value range: [0, +∞)<br>If this parameter is set to a negative number, **1** is used. |

### chainAnimation

chainAnimation(enable: Optional\<boolean>)

Sets whether to enable chained animations, which provide a visually connected, or "chained," effect when the **ArcList** component is scrolled or its top or bottom edge is dragged.

The list items are separated with even space, and one item animation starts after the previous animation during basic sliding interactions. The chained animation effect is similar with spring physics.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type              | Mandatory| Description                                                        |
| ------ | ------------------ | ---- | ------------------------------------------------------------ |
| enable | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<boolean> | Yes | Whether to enable the chained linkage effect. The chained linkage effect takes effect only when the edge effect is [EdgeEffect.Spring](ts-appendix-enums.md#edgeeffect).<br>Default value: **false**, the chained linkage is not enabled; **true**, the chained linkage is enabled. |

### enableScrollInteraction

enableScrollInteraction(enable: Optional\<boolean>)

Sets whether to enable scroll gestures.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type              | Mandatory| Description                               |
| ------ | ------------------ | ---- | ----------------------------------- |
| enable | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<boolean> | Yes | Whether to support the scroll gesture. When set to **true**, the list can be scrolled by finger or mouse. When set to **false**, the list cannot be scrolled by finger or mouse, but the scrolling API of the [Scroller](ts-container-scroll.md#scroller) controller is not affected.<br>Default value: **true** |

### fadingEdge

fadingEdge(enable: Optional&lt;boolean&gt;)

Sets whether to enable the edge fading effect.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                             | Mandatory| Description                                                        |
| ------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| enable | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;boolean&gt;                           | Yes   | Whether to enable the edge fading effect.<br>When **fadingEdge** takes effect, it overrides the `.overlay()` attribute of the original component.<br>When **fadingEdge** takes effect, it is recommended not to set background-related attributes on this component, as they may affect the fading display effect.<br>When **fadingEdge** takes effect, the component is clipped to the boundary, and setting the component's [clip](ts-universal-attributes-sharp-clipping.md#clip12) attribute to **false** does not take effect.<br>The value **true** enables the edge fading effect, and **false** disables it.<br>Default value: **false** |

### friction

friction(friction: Optional\<number>)

Sets the friction coefficient, which takes effect when manually swiping the scroll area and only affects the inertial scrolling process. If the value is set to 0 or less, the default value is used.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name  | Type             | Mandatory| Description                        |
| -------- | ----------------- | ---- | ---------------------------- |
| friction | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<number> | Yes | Friction coefficient. It takes effect when manually swiping the scroll area and affects only the inertial scrolling process. If set to a value less than or equal to 0, the default value is used.<br>Default value: **0.8**<br>Value range: (0, +∞) |

### scrollBarWidth

scrollBarWidth(width: Optional\<LengthMetrics>)

Sets the width of the **ArcList** scrollbar in the pressed state. If not set, the pressed state width is **LengthMetrics.vp(24)**. The non-pressed state width is fixed at **LengthMetrics.vp(4)** and is not affected by this attribute.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                       |
| ------ | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| width  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)&gt; | Yes   | Width of the **ArcList** scrollbar in the pressed state.<br>Default value: **LengthMetrics.vp(24)**<br>Width in the unpressed state: **LengthMetrics.vp(4)**<br>If this parameter is set to an abnormal value such as a negative value or **undefined**, the width of the scrollbar in the normal state is used.<br>Unit: vp |

### scrollBarColor

scrollBarColor(color: Optional\<ColorMetrics>)

Sets the color of the scrollbar.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                                        | Mandatory| Description                                    |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------------------- |
| color  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)&gt; | Yes   | Scrollbar color.<br>Default value: **ColorMetrics.numeric(0xA9FFFFFF)**<br>The abnormal values **undefined** and **null** are treated as invalid values, and this setting does not take effect. |

### flingSpeedLimit

flingSpeedLimit(speed: Optional\<number>)

Sets the maximum initial speed for inertial scrolling after a fling gesture. If this attribute is set to a value less than or equal to 0, the default value is used.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type             | Mandatory| Description                           |
| ------ | ----------------- | ---- | ------------------------------- |
| speed  | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<number> | Yes   | Maximum initial speed when the inertial scrolling animation starts. If this parameter is set to a value less than or equal to 0, the default value is used.<br>Default value: **9000**<br>Unit: vp/s<br>Value range: (0, +∞)<br>The abnormal values **undefined** and **null** are treated as invalid values, and this setting does not take effect. |

### childrenMainSize

childrenMainSize(size: Optional\<ChildrenMainSize>)

Sets the size information of the child components of the **ArcList** component along the main axis.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

<!--Table: 10%; auto; 10%; auto-->

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| size   | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[ChildrenMainSize](ts-container-scrollable-common.md#childrenmainsize12)&gt; | Yes   | Provides precise size information of all child components in the main axis direction to the **ArcList** component through the [ChildrenMainSize](ts-container-scrollable-common.md#childrenmainsize12) object. This ensures that the **ArcList** component can maintain the accuracy of its scroll position in scenarios such as inconsistent child component main axis sizes, addition or removal of child components, and when using [scrollToIndex](ts-container-scroll.md#scrolltoindex). It further guarantees that [scrollTo](ts-container-scroll.md#scrollto) can accurately jump to the specified position, [currentOffset](ts-container-scroll.md#currentoffset) or [offset](ts-container-scroll.md#offset23) accurately reflects the current scroll position, and the built-in scrollbar can move smoothly without any jumps or abrupt changes. Since API version 23, the **offset** API is added.<br> **NOTE**<br>The provided main axis size must be consistent with the actual main axis size of the child components. Otherwise, the **ArcList** component may display abnormally. When the main axis size of a child component changes or when child components are added or removed, the **ArcList** component must be notified of the changes by calling the methods of the **ChildrenMainSize** object. Otherwise, the **ArcList** component may display abnormally. |

## Events

### onScrollIndex

onScrollIndex(handler: Optional\<ArcScrollIndexHandler>)

Triggered when a child component enters or leaves the visible area of the **ArcList** component. This event is triggered during initialization of the **ArcList** component and when the index of the first or last child component in the visible area changes, or when the center child component changes.

When the edge effect of **ArcList** is set to the spring effect, the **onScrollIndex** event is not triggered during the process of continuing to swipe after the **ArcList** reaches the edge and during the spring-back process after release.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                                        | Mandatory| Description                                           |
| ------- | ------------------------------------------------------------ | ---- | ----------------------------------------------- |
| handler | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[ArcScrollIndexHandler](#arcscrollindexhandler)&gt; | Yes  | Callback triggered when a child component enters or leaves the visible area of the **ArcList** component.|

### onReachStart

onReachStart(handler: Optional\<VoidCallback>)

Triggered when the list reaches the start position.

This event is triggered during initialization of the **ArcList** component if [initialIndex](#arklistoptions) is set to **0**, and whenever the list scrolls to the start position. If the edge scrolling effect is set to spring, this event is triggered when scrolling past the start position and again when bouncing back to it.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                            | Mandatory| Description                    |
| ------- | ------------------------------------------------ | ---- | ------------------------ |
| handler | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[VoidCallback](ts-types.md#voidcallback12)&gt; | Yes  | Callback triggered when the list reaches the start position.|

### onReachEnd

onReachEnd(handler: Optional\<VoidCallback>)

Triggered when the list reaches the end position.

When the edge effect of **ArcList** is set to the spring effect, this event is triggered once when swiping past the end position, and triggered again when the list springs back to the end position.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                            | Mandatory| Description                    |
| ------- | ------------------------------------------------ | ---- | ------------------------ |
| handler | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[VoidCallback](ts-types.md#voidcallback12)&gt; | Yes  | Callback triggered when the list reaches the end position.|

### onScrollStart

onScrollStart(handler: Optional\<VoidCallback>)

Triggered when the list starts scrolling initiated by the user's finger dragging the list or its scrollbar. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](ts-container-scroll.md#scroller) starts.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                            | Mandatory| Description                |
| ------- | ------------------------------------------------ | ---- | -------------------- |
| handler | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[VoidCallback](ts-types.md#voidcallback12)&gt; | Yes  | Callback triggered when the list starts scrolling.|

### onScrollStop

onScrollStop(handler: Optional\<VoidCallback>)

Triggered when the list stops scrolling after the user's finger leaves the screen. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](ts-container-scroll.md#scroller) stops.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                            | Mandatory| Description                |
| ------- | ------------------------------------------------ | ---- | -------------------- |
| handler | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[VoidCallback](ts-types.md#voidcallback12)&gt; | Yes  | Callback triggered when the list stops scrolling.|

### onWillScroll

onWillScroll(handler: Optional\<OnWillScrollCallback>)

Triggered before each frame during list scrolling. The callback returns the offset amount by which the list will scroll and the current scroll state. The returned offset is a calculated value, not the actual offset.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------|
| handler | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[OnWillScrollCallback](ts-container-scrollable-common.md#onwillscrollcallback12)&gt; | Yes| Callback triggered before each frame during list scrolling.|

> **NOTE**
>
> When [scrollEdge](ts-container-scroll.md#scrolledge) and [scrollToIndex](ts-container-scroll.md#scrolltoindex) without animation are called, **onWillScroll** is not triggered.

### onDidScroll

onDidScroll(handler: Optional\<OnScrollCallback>)

Triggered when the list scrolls. The return value is the offset amount by which the list has scrolled and the current scroll state.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------|
| handler | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[OnScrollCallback](ts-container-scrollable-common.md#onscrollcallback12)&gt; | Yes| Callback triggered when the list scrolls.|

## ArkListOptions

Provides basic parameters for creating an **ArcList** component.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name      | Type                                   | Read-Only| Optional| Description                                                    |
| ------------ | ------------------------------------------- | ---- | --- | ------------------------------------------------------------ |
| initialIndex | number                                      | No   | Yes | Index value of the item displayed at the start position of the viewport when **ArcList** is initially loaded.<br>Default value: **0**<br>**Note:** If the value is set to a negative number or exceeds the index value of the last item in the current **ArcList**, it is considered invalid, and the default value is used. |
| scroller     | [Scroller](ts-container-scroll.md#scroller) | No   | Yes | Controller of the scrollable component. After being bound to **ArcList**, it can be used to control the scrolling of **ArcList**. If not set, no scroll controller is bound.<br>**Note:** It is not allowed to bind the same scroll control object with other scrollable components, such as [List](ts-container-list.md), [Grid](ts-container-grid.md), [Scroll](ts-container-scroll.md), and [WaterFlow](ts-container-waterflow.md). |
| header       | [ComponentContent](../js-apis-arkui-ComponentContent.md)                            | No   | Yes | Header component of **ArcList**, used to display a title or custom content at the top of the list. If not set, no header component is displayed.                                               |

## ArcScrollIndexHandler

type ArcScrollIndexHandler = (start: number, end: number, center: number) => void

Represents the callback triggered when a child component enters or leaves the visible area of the **ArcList** component.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | ----------------------------------------- |
| start  | number | Yes  | Index of the first child component in the visible area of the **ArcList** component.  |
| end    | number | Yes  | Index of the last child component in the visible area of the **ArcList** component.|
| center | number | Yes  | Index of the center child component in the visible area of the **ArcList** component.|

## Example

This example demonstrates an **ArcList** component with a header component and auto-scaling child items.

```ts
// xxx.ets
import { ComponentContent, LengthMetrics, UIContext, CircleShape } from '@kit.ArkUI';
// Starting from API version 22, you do not need to manually import ArcListAttribute and ArcListItemAttribute. For details, refer to the Modules to Import section of the ArcList and ArcListItem reference documents.
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';

@Builder
function buildText() {
  Column() {
    Text('header')
      .fontSize('60px')
      .fontWeight(FontWeight.Bold)
      .fontColor(Color.Black)
  }.margin(0)
}

@Entry
@Component
struct Index {
  @State private numItems: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  private watchSize: string = '466px'; // Default size on wearables: 466*466
  private listSize: string = '414px'; // Item width

  context: UIContext = this.getUIContext();
  headerContent: ComponentContent<Object> = new ComponentContent(this.context, wrapBuilder(buildText));

  @Builder
  buildList() {
    Stack() {
      Column() {
      }
      .justifyContent(FlexAlign.Center)
      .width(this.watchSize)
      .height(this.watchSize)
      .clipShape(new CircleShape({ width: '100%', height: '100%' }))
      .backgroundColor(Color.White)

      ArcList({ initialIndex: 0, header: this.headerContent }) {
        ForEach(this.numItems, (item: number, index: number) => {
          ArcListItem() {
            Button('' + item, { type: ButtonType.Capsule })
              .width(this.listSize)
              .height('100px')
              .fontSize('40px')
              .focusable(true)
              .focusOnTouch(true)
              .backgroundColor(0x17A98D)
          }.align(Alignment.Center)
        }, (item: number, index: number) => (item + index).toString())
      }
      .space(LengthMetrics.px(10))
      .borderRadius(this.watchSize)
      .focusable(true)
      .focusOnTouch(true)
      .defaultFocus(true)
    }
    .align(Alignment.Center)
    .width(this.watchSize)
    .height(this.watchSize)
    .border({color: Color.Black, width: 1})
    .borderRadius(this.watchSize)
  }

  build() {
    Column() {
      this.buildList()
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
    .justifyContent(FlexAlign.Center)
  }
}
```

![arkts-arclist](figures/arkts-arclist.png)