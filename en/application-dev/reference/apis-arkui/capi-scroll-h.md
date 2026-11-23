# scroll.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @shengu_lancer; @rongShao-Z-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=1cc42747daac90c755c0f02f6c0c084e7424b7af translatedAt=2026-11-18T09:18:47.765Z pushedAt=2026-11-20T03:33:15.855Z nl=1 -->

## Overview

Defines the enumerations related to the **Scroll** component, such as the scrolling direction, edge effect, scrollbar state, content clipping, nested scrolling, scrolling state, and scroll source, which are used to configure and listen for the behavior of the **Scroll** component and related scrollable components.

**File to include:** <arkui/node_attributes/scroll.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[ScrollableNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ScrollableNDK)<!--RP1End-->

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_EdgeEffect](#arkui_edgeeffect) | ArkUI_EdgeEffect | Enumerates the effects used at the edges of the component when the boundary of the scrollable content is reached.|
| [ArkUI_BarState](#arkui_barstate) | ArkUI_BarState | Enumerates the scrollbar states of the **TextArea** and **TextEditor** components. |
| [ArkUI_EffectEdge](#arkui_effectedge) | ArkUI_EffectEdge | Enumerates the edges for which the effect takes effect when the boundary of the scrollable content is reached.|
| [ArkUI_ScrollDirection](#arkui_scrolldirection) | ArkUI_ScrollDirection | Enumerates the scrolling directions of the [Scroll](../apis-arkui/arkui-ts/ts-container-scroll.md) component.|
| [ArkUI_ScrollSnapAlign](#arkui_scrollsnapalign) | ArkUI_ScrollSnapAlign | Enumerates the alignment modes of list items when scrolling ends.|
| [ArkUI_ScrollBarDisplayMode](#arkui_scrollbardisplaymode) | ArkUI_ScrollBarDisplayMode | Enumerates the scrollbar display modes.|
| [ArkUI_ContentClipMode](#arkui_contentclipmode) | ArkUI_ContentClipMode | Enumerates the content clipping modes of scrollable components.|
| [ArkUI_ScrollNestedMode](#arkui_scrollnestedmode) | ArkUI_ScrollNestedMode | Enumerates nested scrolling modes.|
| [ArkUI_ScrollEdge](#arkui_scrolledge) | ArkUI_ScrollEdge | Enumerates the edges to which the component scrolls.|
| [ArkUI_ScrollAlignment](#arkui_scrollalignment) | ArkUI_ScrollAlignment | Enumerates how the list item to scroll to is aligned with the container.|
| [OH_ArkUI_FastScrollMode](#oh_arkui_fastscrollmode) | OH_ArkUI_FastScrollMode | Defines the fast scroll mode used when scrolling to a specified index, which is used to set the **.value[4]?.i32** parameter of [NODE_LIST_SCROLL_TO_INDEX](capi-native-node-h-nodeattributetype-scrollablecontainer.md#node_list_scroll_to_index) or [NODE_WATER_FLOW_SCROLL_TO_INDEX](capi-native-node-h-nodeattributetype-scrollablecontainer.md#node_water_flow_scroll_to_index). It takes effect only when **.value[1]?.i32** is set to **1** (enable animation). For **WaterFlow**, the [ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW](capi-water-flow-h.md#arkui_waterflowlayoutmode) layout mode is also required. |
| [ArkUI_ScrollState](#arkui_scrollstate) | ArkUI_ScrollState | Enumerates the scrolling states.|
| [ArkUI_ScrollSource](#arkui_scrollsource) | ArkUI_ScrollSource | Enumerates scroll sources.|
| [ArkUI_ScrollSnapAnimationSpeed](#arkui_scrollsnapanimationspeed) | ArkUI_ScrollSnapAnimationSpeed | Enumerates scroll snap animation speeds for list components.|

## Enum Description

### ArkUI_EdgeEffect

```c
enum ArkUI_EdgeEffect
```

**Description**


Enumerates the effects used at the edges of the component when the boundary of the scrollable content is reached. The default value is **ARKUI_EDGE_EFFECT_NONE** for the **Grid**, **Scroll**, and **WaterFlow** components, and **ARKUI_EDGE_EFFECT_SPRING** for the **List** component.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_EDGE_EFFECT_SPRING = 0 | Spring effect. When at one of the edges, the component can move beyond the bounds based on the initial speed or through touches, and produces a bounce effect when the user releases their finger.|
| ARKUI_EDGE_EFFECT_FADE = 1 | Fade effect. When at one of the edges, the component produces a fade effect.|
| ARKUI_EDGE_EFFECT_NONE = 2 | No effect when the component is at one of the edges.|

### ArkUI_BarState

```c
enum ArkUI_BarState
```

**Description**


Enumerates the scrollbar states of the **TextArea** and **TextEditor** components.

**Since:** 22

| Value| Description|
| -- | -- |
| ARKUI_BAR_STATE_OFF = 0 | Not displayed.|
| ARKUI_BAR_STATE_AUTO = 1 | Displayed on demand (The scrollbar is displayed when being touched and disappears 2 seconds later.)|
| ARKUI_BAR_STATE_ON = 2 | Always displayed.|

### ArkUI_EffectEdge

```c
enum ArkUI_EffectEdge
```

**Description**


Enumerates the edges for which the effect takes effect when the boundary of the scrollable content is reached.

**Since:** 18

| Value| Description                   |
| -- |-----------------------|
| ARKUI_EFFECT_EDGE_START = 1 | Start edge.               |
| ARKUI_EFFECT_EDGE_END = 2 | End edge.               |

### ArkUI_ScrollDirection

```c
enum ArkUI_ScrollDirection
```

**Description**


Enumerates the scrolling directions of the [Scroll](../apis-arkui/arkui-ts/ts-container-scroll.md) component.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_DIRECTION_VERTICAL = 0 | Vertical scrolling only.|
| ARKUI_SCROLL_DIRECTION_HORIZONTAL = 1 | Horizontal scrolling only.|
| ARKUI_SCROLL_DIRECTION_NONE = 3 | Scrolling disabled.|
| ARKUI_SCROLL_DIRECTION_FREE = 4 | Free scrolling. This value supports both vertical and horizontal scrolling, and is available only in the **Scroll** component.<br>**Since:** 20 |

### ArkUI_ScrollSnapAlign

```c
enum ArkUI_ScrollSnapAlign
```

**Description**


Enumerates the alignment modes of list items when scrolling ends.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_SNAP_ALIGN_NONE = 0 | No alignment mode.|
| ARKUI_SCROLL_SNAP_ALIGN_START = 1 | The first item in the view is aligned at the start of the list.|
| ARKUI_SCROLL_SNAP_ALIGN_CENTER = 2 | The middle items in the view are aligned in the center of the list.|
| ARKUI_SCROLL_SNAP_ALIGN_END = 3 | The last item in the view is aligned at the end of the list.|

### ArkUI_ScrollBarDisplayMode

```c
enum ArkUI_ScrollBarDisplayMode
```

**Description**


Enumerates the scrollbar display modes.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF = 0 | Not displayed.|
| ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO = 1 | Displayed on demand (displayed when the screen is touched and hidden after 2s). |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_ON = 2 | Always displayed.|

### ArkUI_ContentClipMode

```c
enum ArkUI_ContentClipMode
```

**Description**


Enumerates the content clipping modes of scrollable components.

**Since:** 18

| Value| Description|
| -- | -- |
| ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY = 0 | Clip to the content area only.|
| ARKUI_CONTENT_CLIP_MODE_BOUNDARY = 1 | Clip to the component's boundary area.|
| ARKUI_CONTENT_CLIP_MODE_SAFE_AREA = 2 | Clip to the [safe area](./arkui-ts/ts-universal-attributes-expand-safe-area.md) configured for the component.|

### ArkUI_ScrollNestedMode

```c
enum ArkUI_ScrollNestedMode
```

**Description**


Enumerates nested scrolling modes.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_NESTED_MODE_SELF_ONLY = 0 | The scrolling is contained within the component, and no scroll chaining occurs, that is, the parent component does not scroll when the component scrolling reaches the boundary.|
| ARKUI_SCROLL_NESTED_MODE_SELF_FIRST = 1 | The component scrolls first, and when it hits the boundary, the parent component scrolls. When the parent component hits the boundary, its edge effect is displayed. If no edge effect is specified for the parent component, the edge effect of the child component is displayed instead.|
| ARKUI_SCROLL_NESTED_MODE_PARENT_FIRST = 2 | The parent component scrolls first, and when it hits the boundary, the component scrolls. When the component hits the boundary, its edge effect is displayed. If no edge effect is specified for the component, the edge effect of the parent component is displayed instead.|
| ARKUI_SCROLL_NESTED_MODE_PARALLEL = 3 | The component and its parent component scroll at the same time. When both the component and its parent component hit the boundary, the edge effect of the component is displayed. If no edge effect is specified for the component, the edge effect of the parent component is displayed instead.|

### ArkUI_ScrollEdge

```c
enum ArkUI_ScrollEdge
```

**Description**


Enumerates the edges to which the component scrolls.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_EDGE_TOP = 0 | Top edge in the vertical direction.|
| ARKUI_SCROLL_EDGE_BOTTOM = 1 | Bottom edge in the vertical direction.|
| ARKUI_SCROLL_EDGE_START = 2 | Start position in the horizontal direction.|
| ARKUI_SCROLL_EDGE_END = 3 | End position in the horizontal direction.|

### ArkUI_ScrollAlignment

```c
enum ArkUI_ScrollAlignment
```

**Description**


Enumerates how the list item to scroll to is aligned with the container.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_ALIGNMENT_START = 0 | The start edge of the list item is flush with the start edge of the container.|
| ARKUI_SCROLL_ALIGNMENT_CENTER = 1 | The list item is centered along the main axis of the container.|
| ARKUI_SCROLL_ALIGNMENT_END = 2 | The end edge of the list item is flush with the end edge of the container.|
| ARKUI_SCROLL_ALIGNMENT_AUTO = 3 | The list item is automatically aligned. If the item is fully contained within the display area, no adjustment is performed. Otherwise, the item is aligned so that its start or end edge is flush with the start or end edge of the container, whichever requires a shorter scrolling distance.|

### OH_ArkUI_FastScrollMode

```c
enum OH_ArkUI_FastScrollMode
```

**Description**

Defines the fast scroll mode used when scrolling to a specified index, which is used to set the **.value[4]?.i32** parameter of [NODE_LIST_SCROLL_TO_INDEX](capi-native-node-h-nodeattributetype-scrollablecontainer.md#node_list_scroll_to_index) or [NODE_WATER_FLOW_SCROLL_TO_INDEX](capi-native-node-h-nodeattributetype-scrollablecontainer.md#node_water_flow_scroll_to_index). It takes effect only when **.value[1]?.i32** is set to **1** (enable animation). For **WaterFlow**, the [ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW](capi-water-flow-h.md#arkui_waterflowlayoutmode) layout mode is also required.

> **NOTE**
>
> - When the scroll distance is large and a jump is triggered, the component usually scrolls continuously for about two screens from the start position, then jumps to a position about two screens away from the final stop position, and continues scrolling to the final position. One screen refers to the length of the visible area of the scrollable component in the scroll direction.
> - Skipping creation or measurement applies only to the scroll path that is skipped as described above. The child components that need to be displayed in the two continuous scroll segments before and after the jump are still created and measured on demand. The actual range of creation and measurement is also affected by factors such as the alignment mode, extra offset, and child component size, and is not fixed at four screens.
> - Fast scroll does not guarantee that every child component on the scroll path is traversed and displayed.
> - When a value not defined in this enumeration is passed to **NODE_LIST_SCROLL_TO_INDEX** or **NODE_WATER_FLOW_SCROLL_TO_INDEX**, it is processed as **OH_ARKUI_FAST_SCROLL_MODE_NONE**, and the fast scroll optimization is not enabled. Other scroll parameters still take effect according to the original rules.

**Since**: 26.1.0

| Value | Description |
| -- | -- |
| OH_ARKUI_FAST_SCROLL_MODE_NONE = 0 | The fast scroll optimization is not enabled, and the behavior is the same as when the fast scroll mode parameter is not set. When an animation is enabled, all child components on the scroll path are created and measured before the animation starts. |
| OH_ARKUI_FAST_SCROLL_MODE_SKIP_MEASURE = 1 | The measurement of intermediate child components is skipped, but they are still created to confirm the type and the target row. This mode applies to the scenario where a multi-column **List** contains both **ListItem** and **ListItemGroup**: a **ListItem** occupies one column of a row, while a **ListItemGroup** occupies an entire row, so the target row must be determined based on the child component type. |
| OH_ARKUI_FAST_SCROLL_MODE_SKIP_CREATE_AND_MEASURE = 2 | The creation and measurement of intermediate child components are skipped to further reduce overhead.<br/>**NOTE**<br/>This mode does not apply to the scenario where a multi-column **List** contains both **ListItem** and **ListItemGroup**. Using this mode in that scenario causes abnormal **List** layout and scrolling. Use **OH_ARKUI_FAST_SCROLL_MODE_SKIP_MEASURE** instead.<br/>This mode is recommended for the **WaterFlow** component. In the [ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW](capi-water-flow-h.md#arkui_waterflowlayoutmode) layout mode, locating the target **FlowItem** in **WaterFlow** does not depend on intermediate child components. **OH_ARKUI_FAST_SCROLL_MODE_SKIP_MEASURE** still creates the intermediate child components along the path, incurring unnecessary creation overhead. |

### ArkUI_ScrollState

```c
enum ArkUI_ScrollState
```

**Description**


Enumerates the scrolling states.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_STATE_IDLE = 0 | Idle. The container enters this state when an API in the controller is used to scroll the container or when the scrollbar is dragged.|
| ARKUI_SCROLL_STATE_SCROLL = 1 | Scrolling. The container enters this state when the user drags the container to scroll.|
| ARKUI_SCROLL_STATE_FLING = 2 | Inertia scrolling. The container enters this state when inertia scrolling occurs after a quick swipe is released and when sliding to the edge and bouncing back. |

### ArkUI_ScrollSource

```c
enum ArkUI_ScrollSource
```

**Description**


Enumerates scroll sources.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_SOURCE_DRAG = 0 | Finger dragging.|
| ARKUI_SCROLL_SOURCE_FLING = 1 | Inertia scrolling after finger dragging.|
| ARKUI_SCROLL_SOURCE_EDGE_EFFECT = 2 | [EdgeEffect.Spring](../apis-arkui/arkui-ts/ts-appendix-enums.md#edgeeffect) for boundary crossing.|
| ARKUI_SCROLL_SOURCE_OTHER_USER_INPUT = 3 | User input other than dragging, such as mouse wheel and keyboard events.|
| ARKUI_SCROLL_SOURCE_SCROLL_BAR = 4 | Scrollbar dragging.|
| ARKUI_SCROLL_SOURCE_SCROLL_BAR_FLING = 5 | Inertia scrolling after scrollbar dragging.|
| ARKUI_SCROLL_SOURCE_SCROLLER = 6 | Scrolling by the scroll controller (without animation).|
| ARKUI_SCROLL_SOURCE_ANIMATION = 7 | Scrolling by the scroll controller (with animation).|

### ArkUI_ScrollSnapAnimationSpeed

```c
enum ArkUI_ScrollSnapAnimationSpeed
```

**Description**


Enumerates scroll snap animation speeds for list components.

**Since:** 22

| Value| Description|
| -- | -- |
| ARKUI_SCROLL_SNAP_ANIMATION_NORMAL = 0 | Normal scroll snap animation speed.|
| ARKUI_SCROLL_SNAP_ANIMATION_SLOW = 1 | Slow scroll snap animation speed.|
