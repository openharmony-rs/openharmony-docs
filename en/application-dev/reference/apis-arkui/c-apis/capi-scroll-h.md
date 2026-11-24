# scroll.h

## Overview

Defines the enumerations related to the **Scroll** component, such as the scrolling direction, edge effect, scrollbar state, content clipping, nested scrolling, scrolling state, and scrolling source, which are used to configure and listen for the behavior of the **Scroll** component and related scrollable components.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_EdgeEffect](#arkui_edgeeffect) | ArkUI_EdgeEffect | Enumerates the effects used at the edges of the component when the boundary of the scrollable content is reached. The default value is **ARKUI_EDGE_EFFECT_NONE** for the **Grid**, **Scroll**, and **WaterFlow** components, and **ARKUI_EDGE_EFFECT_SPRING** for the **List** component. |
| [ArkUI_BarState](#arkui_barstate) | ArkUI_BarState | Enumerates the scrollbar states of the **TextArea** and **TextEditor** components. |
| [ArkUI_EffectEdge](#arkui_effectedge) | ArkUI_EffectEdge | Enumerates the edges for which the effect takes effect when the boundary of the scrollable content is reached. |
| [ArkUI_ScrollDirection](#arkui_scrolldirection) | ArkUI_ScrollDirection | Enumerates the scrolling directions of the Scroll component. |
| [ArkUI_ScrollSnapAlign](#arkui_scrollsnapalign) | ArkUI_ScrollSnapAlign | Enumerates the alignment modes of list items when scrolling ends. |
| [ArkUI_ScrollSnapAnimationSpeed](#arkui_scrollsnapanimationspeed) | ArkUI_ScrollSnapAnimationSpeed | Enumerates scroll snap animation speeds for list components. |
| [ArkUI_ScrollBarDisplayMode](#arkui_scrollbardisplaymode) | ArkUI_ScrollBarDisplayMode | Enumerates the scrollbar display modes. |
| [ArkUI_ContentClipMode](#arkui_contentclipmode) | ArkUI_ContentClipMode | Enumerates the content clipping modes of scrollable components. |
| [ArkUI_ScrollNestedMode](#arkui_scrollnestedmode) | ArkUI_ScrollNestedMode | Enumerates nested scrolling modes. |
| [ArkUI_ScrollEdge](#arkui_scrolledge) | ArkUI_ScrollEdge | Enumerates the edges to which the component scrolls. |
| [ArkUI_ScrollAlignment](#arkui_scrollalignment) | ArkUI_ScrollAlignment | Enumerates how the list item to scroll to is aligned with the container. |
| [ArkUI_ScrollState](#arkui_scrollstate) | ArkUI_ScrollState | Enumerates the scrolling states. |
| [ArkUI_ScrollSource](#arkui_scrollsource) | ArkUI_ScrollSource | Enumerates scroll sources. |
| [OH_ArkUI_FastScrollMode](#oh_arkui_fastscrollmode) | OH_ArkUI_FastScrollMode | Enumerates the fast scroll modes for scrolling to a specified index. |

## Enum type description

### ArkUI_EdgeEffect

```c
enum ArkUI_EdgeEffect
```

**Description**

Enumerates the effects used at the edges of the component when the boundary of the scrollable content is reached. The default value is **ARKUI_EDGE_EFFECT_NONE** for the **Grid**, **Scroll**, and **WaterFlow** components, and **ARKUI_EDGE_EFFECT_SPRING** for the **List** component.

<!--Device-enum ArkUI_EdgeEffect--><!--Device-enum ArkUI_EdgeEffect-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_EDGE_EFFECT_SPRING = 0 | Spring effect. When at one of the edges, the component can move beyond the bounds based on the initial speed or through touches, and produces a bounce effect when the user releases their finger.<br><!--Device-ARKUI_EDGE_EFFECT_SPRING = 0--><!--Device-ARKUI_EDGE_EFFECT_SPRING = 0-End--> |
| ARKUI_EDGE_EFFECT_FADE | Fade effect. When at one of the edges, the component produces a fade effect.<br><!--Device-ARKUI_EDGE_EFFECT_FADE--><!--Device-ARKUI_EDGE_EFFECT_FADE-End--> |
| ARKUI_EDGE_EFFECT_NONE | No effect when the component is at one of the edges.<br><!--Device-ARKUI_EDGE_EFFECT_NONE--><!--Device-ARKUI_EDGE_EFFECT_NONE-End--> |

### ArkUI_BarState

```c
enum ArkUI_BarState
```

**Description**

Enumerates the scrollbar states of the **TextArea** and **TextEditor** components.

<!--Device-enum ArkUI_BarState--><!--Device-enum ArkUI_BarState-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

| Enum item | Description |
| -- | -- |
| ARKUI_BAR_STATE_OFF = 0 | Not displayed.<br><!--Device-ARKUI_BAR_STATE_OFF = 0--><!--Device-ARKUI_BAR_STATE_OFF = 0-End--> |
| ARKUI_BAR_STATE_AUTO = 1 | Displayed on demand (The scrollbar is displayed when being touched and disappears 2 seconds later.)<br><!--Device-ARKUI_BAR_STATE_AUTO = 1--><!--Device-ARKUI_BAR_STATE_AUTO = 1-End--> |
| ARKUI_BAR_STATE_ON = 2 | Always displayed.<br><!--Device-ARKUI_BAR_STATE_ON = 2--><!--Device-ARKUI_BAR_STATE_ON = 2-End--> |

### ArkUI_EffectEdge

```c
enum ArkUI_EffectEdge
```

**Description**

Enumerates the edges for which the effect takes effect when the boundary of the scrollable content is reached.

<!--Device-enum ArkUI_EffectEdge--><!--Device-enum ArkUI_EffectEdge-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

| Enum item | Description |
| -- | -- |
| ARKUI_EFFECT_EDGE_START = 1 | Start edge.<br><!--Device-ARKUI_EFFECT_EDGE_START = 1--><!--Device-ARKUI_EFFECT_EDGE_START = 1-End--> |
| ARKUI_EFFECT_EDGE_END = 2 | End edge.<br><!--Device-ARKUI_EFFECT_EDGE_END = 2--><!--Device-ARKUI_EFFECT_EDGE_END = 2-End--> |

### ArkUI_ScrollDirection

```c
enum ArkUI_ScrollDirection
```

**Description**

Enumerates the scrolling directions of the Scroll component.

<!--Device-enum ArkUI_ScrollDirection--><!--Device-enum ArkUI_ScrollDirection-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SCROLL_DIRECTION_VERTICAL = 0 | Vertical scrolling only.<br><!--Device-ARKUI_SCROLL_DIRECTION_VERTICAL = 0--><!--Device-ARKUI_SCROLL_DIRECTION_VERTICAL = 0-End--> |
| ARKUI_SCROLL_DIRECTION_HORIZONTAL | Horizontal scrolling only.<br><!--Device-ARKUI_SCROLL_DIRECTION_HORIZONTAL--><!--Device-ARKUI_SCROLL_DIRECTION_HORIZONTAL-End--> |
| ARKUI_SCROLL_DIRECTION_NONE = 3 | Scrolling disabled.<br><!--Device-ARKUI_SCROLL_DIRECTION_NONE = 3--><!--Device-ARKUI_SCROLL_DIRECTION_NONE = 3-End--> |
| ARKUI_SCROLL_DIRECTION_FREE = 4 | Free scrolling. This value supports both vertical and horizontal scrolling, and is available only in the **Scroll** component.<br>**Since**: 20<br><!--Device-ARKUI_SCROLL_DIRECTION_FREE = 4--><!--Device-ARKUI_SCROLL_DIRECTION_FREE = 4-End--> |

### ArkUI_ScrollSnapAlign

```c
enum ArkUI_ScrollSnapAlign
```

**Description**

Enumerates the alignment modes of list items when scrolling ends.

<!--Device-enum ArkUI_ScrollSnapAlign--><!--Device-enum ArkUI_ScrollSnapAlign-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SCROLL_SNAP_ALIGN_NONE = 0 | No alignment mode.<br><!--Device-ARKUI_SCROLL_SNAP_ALIGN_NONE = 0--><!--Device-ARKUI_SCROLL_SNAP_ALIGN_NONE = 0-End--> |
| ARKUI_SCROLL_SNAP_ALIGN_START | The first item in the view is aligned at the start of the list.<br><!--Device-ARKUI_SCROLL_SNAP_ALIGN_START--><!--Device-ARKUI_SCROLL_SNAP_ALIGN_START-End--> |
| ARKUI_SCROLL_SNAP_ALIGN_CENTER | The middle items in the view are aligned in the center of the list.<br><!--Device-ARKUI_SCROLL_SNAP_ALIGN_CENTER--><!--Device-ARKUI_SCROLL_SNAP_ALIGN_CENTER-End--> |
| ARKUI_SCROLL_SNAP_ALIGN_END | The last item in the view is aligned at the end of the list.<br><!--Device-ARKUI_SCROLL_SNAP_ALIGN_END--><!--Device-ARKUI_SCROLL_SNAP_ALIGN_END-End--> |

### ArkUI_ScrollSnapAnimationSpeed

```c
enum ArkUI_ScrollSnapAnimationSpeed
```

**Description**

Enumerates scroll snap animation speeds for list components.

<!--Device-enum ArkUI_ScrollSnapAnimationSpeed--><!--Device-enum ArkUI_ScrollSnapAnimationSpeed-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

| Enum item | Description |
| -- | -- |
| ARKUI_SCROLL_SNAP_ANIMATION_NORMAL = 0 | Normal scroll snap animation speed.<br><!--Device-ARKUI_SCROLL_SNAP_ANIMATION_NORMAL = 0--><!--Device-ARKUI_SCROLL_SNAP_ANIMATION_NORMAL = 0-End--> |
| ARKUI_SCROLL_SNAP_ANIMATION_SLOW = 1 | Slow scroll snap animation speed.<br><!--Device-ARKUI_SCROLL_SNAP_ANIMATION_SLOW = 1--><!--Device-ARKUI_SCROLL_SNAP_ANIMATION_SLOW = 1-End--> |

### ArkUI_ScrollBarDisplayMode

```c
enum ArkUI_ScrollBarDisplayMode
```

**Description**

Enumerates the scrollbar display modes.

<!--Device-enum ArkUI_ScrollBarDisplayMode--><!--Device-enum ArkUI_ScrollBarDisplayMode-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF = 0 | Not displayed.<br><!--Device-ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF = 0--><!--Device-ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF = 0-End--> |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO | Displayed when the screen is touched and hidden after 2s.<br><!--Device-ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO--><!--Device-ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO-End--> |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_ON | Always displayed.<br><!--Device-ARKUI_SCROLL_BAR_DISPLAY_MODE_ON--><!--Device-ARKUI_SCROLL_BAR_DISPLAY_MODE_ON-End--> |

### ArkUI_ContentClipMode

```c
enum ArkUI_ContentClipMode
```

**Description**

Enumerates the content clipping modes of scrollable components.

<!--Device-enum ArkUI_ContentClipMode--><!--Device-enum ArkUI_ContentClipMode-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 18

| Enum item | Description |
| -- | -- |
| ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY = 0 | Clip to the content area only.<br><!--Device-ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY = 0--><!--Device-ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY = 0-End--> |
| ARKUI_CONTENT_CLIP_MODE_BOUNDARY | Clip to the component's boundary area.<br><!--Device-ARKUI_CONTENT_CLIP_MODE_BOUNDARY--><!--Device-ARKUI_CONTENT_CLIP_MODE_BOUNDARY-End--> |
| ARKUI_CONTENT_CLIP_MODE_SAFE_AREA | Clip to the safe area configured for the component.<br><!--Device-ARKUI_CONTENT_CLIP_MODE_SAFE_AREA--><!--Device-ARKUI_CONTENT_CLIP_MODE_SAFE_AREA-End--> |

### ArkUI_ScrollNestedMode

```c
enum ArkUI_ScrollNestedMode
```

**Description**

Enumerates nested scrolling modes.

<!--Device-enum ArkUI_ScrollNestedMode--><!--Device-enum ArkUI_ScrollNestedMode-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SCROLL_NESTED_MODE_SELF_ONLY = 0 | The scrolling is contained within the component, and no scroll chaining occurs, that is, the parent component does not scroll when the component scrolling reaches the boundary.<br><!--Device-ARKUI_SCROLL_NESTED_MODE_SELF_ONLY = 0--><!--Device-ARKUI_SCROLL_NESTED_MODE_SELF_ONLY = 0-End--> |
| ARKUI_SCROLL_NESTED_MODE_SELF_FIRST | The component scrolls first, and when it hits the boundary, the parent component scrolls. When the parent component hits the boundary, its edge effect is displayed. If no edge effect is specified for the parent component, the edge effect of the child component is displayed instead.<br><!--Device-ARKUI_SCROLL_NESTED_MODE_SELF_FIRST--><!--Device-ARKUI_SCROLL_NESTED_MODE_SELF_FIRST-End--> |
| ARKUI_SCROLL_NESTED_MODE_PARENT_FIRST | The parent component scrolls first, and when it hits the boundary, the component scrolls. When the component hits the boundary, its edge effect is displayed. If no edge effect is specified for the component, the edge effect of the parent component is displayed instead.<br><!--Device-ARKUI_SCROLL_NESTED_MODE_PARENT_FIRST--><!--Device-ARKUI_SCROLL_NESTED_MODE_PARENT_FIRST-End--> |
| ARKUI_SCROLL_NESTED_MODE_PARALLEL | The component and its parent component scroll at the same time. When both the component and its parent component hit the boundary, the edge effect of the component is displayed. If no edge effect is specified for the component, the edge effect of the parent component is displayed instead.<br><!--Device-ARKUI_SCROLL_NESTED_MODE_PARALLEL--><!--Device-ARKUI_SCROLL_NESTED_MODE_PARALLEL-End--> |

### ArkUI_ScrollEdge

```c
enum ArkUI_ScrollEdge
```

**Description**

Enumerates the edges to which the component scrolls.

<!--Device-enum ArkUI_ScrollEdge--><!--Device-enum ArkUI_ScrollEdge-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SCROLL_EDGE_TOP = 0 | Top edge in the vertical direction.<br><!--Device-ARKUI_SCROLL_EDGE_TOP = 0--><!--Device-ARKUI_SCROLL_EDGE_TOP = 0-End--> |
| ARKUI_SCROLL_EDGE_BOTTOM | Bottom edge in the vertical direction.<br><!--Device-ARKUI_SCROLL_EDGE_BOTTOM--><!--Device-ARKUI_SCROLL_EDGE_BOTTOM-End--> |
| ARKUI_SCROLL_EDGE_START | Start position in the horizontal direction.<br><!--Device-ARKUI_SCROLL_EDGE_START--><!--Device-ARKUI_SCROLL_EDGE_START-End--> |
| ARKUI_SCROLL_EDGE_END | End position in the horizontal direction.<br><!--Device-ARKUI_SCROLL_EDGE_END--><!--Device-ARKUI_SCROLL_EDGE_END-End--> |

### ArkUI_ScrollAlignment

```c
enum ArkUI_ScrollAlignment
```

**Description**

Enumerates how the list item to scroll to is aligned with the container.

<!--Device-enum ArkUI_ScrollAlignment--><!--Device-enum ArkUI_ScrollAlignment-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SCROLL_ALIGNMENT_START = 0 | The start edge of the list item is flush with the start edge of the container.<br><!--Device-ARKUI_SCROLL_ALIGNMENT_START = 0--><!--Device-ARKUI_SCROLL_ALIGNMENT_START = 0-End--> |
| ARKUI_SCROLL_ALIGNMENT_CENTER | The list item is centered along the main axis of the container.<br><!--Device-ARKUI_SCROLL_ALIGNMENT_CENTER--><!--Device-ARKUI_SCROLL_ALIGNMENT_CENTER-End--> |
| ARKUI_SCROLL_ALIGNMENT_END | The end edge of the list item is flush with the end edge of the container.<br><!--Device-ARKUI_SCROLL_ALIGNMENT_END--><!--Device-ARKUI_SCROLL_ALIGNMENT_END-End--> |
| ARKUI_SCROLL_ALIGNMENT_AUTO | The list item is automatically aligned. If the item is fully contained within the display area, no adjustment is performed. Otherwise, the item is aligned so that its start or end edge is flush with the start or end edge of the container, whichever requires a shorter scrolling distance.<br><!--Device-ARKUI_SCROLL_ALIGNMENT_AUTO--><!--Device-ARKUI_SCROLL_ALIGNMENT_AUTO-End--> |

### ArkUI_ScrollState

```c
enum ArkUI_ScrollState
```

**Description**

Enumerates the scrolling states.

<!--Device-enum ArkUI_ScrollState--><!--Device-enum ArkUI_ScrollState-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SCROLL_STATE_IDLE = 0 | Idle. The container enters this state when an API in the controller is used to scroll the container or when the scrollbar is dragged.<br><!--Device-ARKUI_SCROLL_STATE_IDLE = 0--><!--Device-ARKUI_SCROLL_STATE_IDLE = 0-End--> |
| ARKUI_SCROLL_STATE_SCROLL | Scrolling. The container enters this state when the user drags the container to scroll.<br><!--Device-ARKUI_SCROLL_STATE_SCROLL--><!--Device-ARKUI_SCROLL_STATE_SCROLL-End--> |
| ARKUI_SCROLL_STATE_FLING | Inertial scrolling. The container enters this state when inertial scrolling occurs or when the container bounces back after being released from a fling.<br><!--Device-ARKUI_SCROLL_STATE_FLING--><!--Device-ARKUI_SCROLL_STATE_FLING-End--> |

### ArkUI_ScrollSource

```c
enum ArkUI_ScrollSource
```

**Description**

Enumerates scroll sources.

<!--Device-enum ArkUI_ScrollSource--><!--Device-enum ArkUI_ScrollSource-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SCROLL_SOURCE_DRAG = 0 | Finger dragging.<br><!--Device-ARKUI_SCROLL_SOURCE_DRAG = 0--><!--Device-ARKUI_SCROLL_SOURCE_DRAG = 0-End--> |
| ARKUI_SCROLL_SOURCE_FLING | Inertia scrolling after finger dragging.<br><!--Device-ARKUI_SCROLL_SOURCE_FLING--><!--Device-ARKUI_SCROLL_SOURCE_FLING-End--> |
| ARKUI_SCROLL_SOURCE_EDGE_EFFECT | EdgeEffect.Spring for boundary crossing.<br><!--Device-ARKUI_SCROLL_SOURCE_EDGE_EFFECT--><!--Device-ARKUI_SCROLL_SOURCE_EDGE_EFFECT-End--> |
| ARKUI_SCROLL_SOURCE_OTHER_USER_INPUT | User input other than dragging, such as mouse wheel and keyboard events.<br><!--Device-ARKUI_SCROLL_SOURCE_OTHER_USER_INPUT--><!--Device-ARKUI_SCROLL_SOURCE_OTHER_USER_INPUT-End--> |
| ARKUI_SCROLL_SOURCE_SCROLL_BAR | Scrollbar dragging.<br><!--Device-ARKUI_SCROLL_SOURCE_SCROLL_BAR--><!--Device-ARKUI_SCROLL_SOURCE_SCROLL_BAR-End--> |
| ARKUI_SCROLL_SOURCE_SCROLL_BAR_FLING | Inertial scrolling after scrollbar dragging.<br><!--Device-ARKUI_SCROLL_SOURCE_SCROLL_BAR_FLING--><!--Device-ARKUI_SCROLL_SOURCE_SCROLL_BAR_FLING-End--> |
| ARKUI_SCROLL_SOURCE_SCROLLER | Scrolling by the scroll controller (without animation).<br><!--Device-ARKUI_SCROLL_SOURCE_SCROLLER--><!--Device-ARKUI_SCROLL_SOURCE_SCROLLER-End--> |
| ARKUI_SCROLL_SOURCE_ANIMATION | Scrolling by the scroll controller (with animation).<br><!--Device-ARKUI_SCROLL_SOURCE_ANIMATION--><!--Device-ARKUI_SCROLL_SOURCE_ANIMATION-End--> |

### OH_ArkUI_FastScrollMode

```c
enum OH_ArkUI_FastScrollMode
```

**Description**

Enumerates the fast scroll modes for scrolling to a specified index.

<!--Device-enum OH_ArkUI_FastScrollMode--><!--Device-enum OH_ArkUI_FastScrollMode-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_FAST_SCROLL_MODE_NONE = 0 | No fast scroll optimization. All intermediate items are created and measured before the animation starts.<br>**Since**: 26.1.0<br><!--Device-OH_ARKUI_FAST_SCROLL_MODE_NONE = 0--><!--Device-OH_ARKUI_FAST_SCROLL_MODE_NONE = 0-End--> |
| OH_ARKUI_FAST_SCROLL_MODE_SKIP_MEASURE = 1 | Fast scroll optimization with skipping intermediate item measurement. Intermediate items are created but not measured. This mode is suitable for scenarios where the list has multiple columns and both ListItem and ListItemGroup exist. In this case, ListItem occupies only one column in a row, but ListItemGroup occupies an entire row. Therefore, the List needs to create all intermediate items to obtain the types of these items and calculate the row position of the target index.<br>**Since**: 26.1.0<br><!--Device-OH_ARKUI_FAST_SCROLL_MODE_SKIP_MEASURE = 1--><!--Device-OH_ARKUI_FAST_SCROLL_MODE_SKIP_MEASURE = 1-End--> |
| OH_ARKUI_FAST_SCROLL_MODE_SKIP_CREATE_AND_MEASURE = 2 | Fast scroll optimization with skipping intermediate item creation and measurement. Intermediate items are neither created nor measured. This mode provides maximum performance optimization. However, this mode is not suitable for the scenarios where the list has multiple columns and both ListItem and ListItemGroup exist. In this scenario, use OH_ARKUI_FAST_SCROLL_MODE_SKIP_MEASURE.<br>**Since**: 26.1.0<br><!--Device-OH_ARKUI_FAST_SCROLL_MODE_SKIP_CREATE_AND_MEASURE = 2--><!--Device-OH_ARKUI_FAST_SCROLL_MODE_SKIP_CREATE_AND_MEASURE = 2-End--> |


