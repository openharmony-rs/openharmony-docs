# @ohos.accessibility (Accessibility) (System API)

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=5afea8900a93c1d5d53117a86ba6b7c5d998328d translatedAt=2026-08-03T09:39:08.062Z pushedAt=2026-08-07T10:41:03.882Z -->

The **Accessibility** module provides accessibility event types and operations executable on accessibility nodes.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This page contains only the system APIs of this module. For other public APIs, see [@ohos.accessibility](js-apis-accessibility.md).

## Modules to Import

```ts
import { accessibility } from '@kit.AccessibilityKit';
```

## AccessibilityEventType

Enumerates accessibility event types.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                    | Value                   |Description|
| ---------------------------------------- | ---- | ---------------------- |
| TYPE_ACCESSIBILITY_FOCUS                 | 0    | Event of gaining an accessibility focus.            |
| TYPE_ACCESSIBILITY_FOCUS_CLEAR           | 1    | Event of clearing an accessibility focus.            |
| TYPE_CLICK                               | 2    | Event of clicking a component.               |
| TYPE_LONG_CLICK                          | 3    | Long press component.              |
| TYPE_SELECT                              | 4    | Event of selecting a component.               |
| TYPE_HOVER_ENTER                         | 5    | Event indicating the mouse pointer enters a component.             |
| TYPE_HOVER_EXIT                          | 6    | Event indicating the mouse pointer exits a component.             |
| TYPE_FOCUS                               | 7    | Event indicating the component gains a focus.             |
| TYPE_TEXT_UPDATE                         | 8    | Event indicating the component text has been updated.            |
| TYPE_TEXT_SELECTION_UPDATE               | 9    | Event indicating the selected text has been updated. |
| TYPE_SCROLL                              | 10   | Event of scrolling the view.               |
| TYPE_REQUEST_FOCUS_FOR_ACCESSIBILITY     | 11   | Event of auto-focusing.               |
| TYPE_ANNOUNCE_FOR_ACCESSIBILITY          | 12   | Event of auto-broadcasting.               |
| TYPE_REQUEST_FOCUS_FOR_ACCESSIBILITY_NOT_INTERRUPT | 13   | Active focus, and the focus request will not be interrupted.             |
| TYPE_ANNOUNCE_FOR_ACCESSIBILITY_NOT_INTERRUPT | 14   | Active announcement, and the announcement will not be interrupted.             |
| TYPE_ELEMENT_INFO_CHANGE                 | 15   | Event indicating the component information changes.             |
| TYPE_SCROLLING                           | 16   | Event indicating an item is scrolled out of the screen.    |
| TYPE_WINDOW_ADD                          | 17   | Event of adding windows.               |
| TYPE_WINDOW_REMOVE                       | 18   | Event of deleting windows.               |
| TYPE_WINDOW_BOUNDS                       | 19   | Event indicating the window boundary changes.             |
| TYPE_WINDOW_ACTIVE                       | 20   | Window active state changed.            |
| TYPE_WINDOW_FOCUS                        | 21   | Event indicating the window focus changes.           |
| TYPE_WINDOW_PROPERTY                     | 22   | Event indicating the window properties change, such as opacity, size, and so on.|
| TYPE_WINDOW_LAYER                        | 23   | Event indicating the window layer changes.             |
| TYPE_TOUCH_BEGIN                         | 24   | Event indicating a touch begins.           |
| TYPE_TOUCH_END                           | 25   | Event indicating a touch ends.           |
| TYPE_PAGE_CONTENT_UPDATE  |26| Page content updated.|
| TYPE_PAGE_STATE_UPDATE  |27| Page state updated.|
| TYPE_PAGE_OPEN  |28| Event of opening a page.|
| TYPE_PAGE_CLOSE  |29| Event of closing a page.|
| TYPE_SWIPE_LEFT           |30| Swipe left gesture.    |
| TYPE_SWIPE_LEFT_THEN_RIGHT  |31|  Event indicating the swipe-left-then-right gesture.|
| TYPE_SWIPE_LEFT_THEN_UP     |32| Event indicating the swipe-left-then-up gesture.|
| TYPE_SWIPE_LEFT_THEN_DOWN   |33| Event indicating the swipe-left-then-down gesture.|
| TYPE_SWIPE_RIGHT          |34| Swipe right gesture.    |
| TYPE_SWIPE_RIGHT_THEN_LEFT  |35| Event indicating the swipe-right-then-left gesture.|
| TYPE_SWIPE_RIGHT_THEN_UP    |36| Event indicating the swipe-right-then-up gesture.|
| TYPE_SWIPE_RIGHT_THEN_DOWN  |37| Event indicating the swipe-right-then-down gesture.|
| TYPE_SWIPE_UP             |38| Swipe up gesture.   |
| TYPE_SWIPE_UP_THEN_LEFT     |39| Event indicating the swipe-up-then-left gesture.|
| TYPE_SWIPE_UP_THEN_RIGHT    |40| Event indicating the swipe-up-then-right gesture.|
| TYPE_SWIPE_UP_THEN_DOWN     |41| Event indicating the swipe-up-then-down gesture.|
| TYPE_SWIPE_DOWN           |42| Swipe down gesture.    |
| TYPE_SWIPE_DOWN_THEN_LEFT   |43| Event indicating the swipe-down-then-left gesture.|
| TYPE_SWIPE_DOWN_THEN_RIGHT  |44| Event indicating the swipe-down-then-right gesture.|
| TYPE_SWIPE_DOWN_THEN_UP     |45| Event indicating the swipe-down-then-up gesture.|
| TYPE_TWO_FINGER_SINGLE_TAP   |46| Event indicating the two-finger single-tap gesture.|
| TYPE_TWO_FINGER_DOUBLE_TAP   |47|  Event indicating the two-finger double-tap gesture.|
| TYPE_TWO_FINGER_DOUBLE_TAP_AND_HOLD      | 48   | Event indicating the two-finger double-tap-and-hold gesture.         |
| TYPE_TWO_FINGER_TRIPLE_TAP   |49| Event indicating the two-finger triple-tap gesture.|
| TYPE_TWO_FINGER_TRIPLE_TAP_AND_HOLD      | 50   | Event indicating the two-finger triple-tap-and-hold gesture.         |
| TYPE_THREE_FINGER_SINGLE_TAP  |51| Event indicating the three-finger single-tap gesture.|
| TYPE_THREE_FINGER_DOUBLE_TAP  |52| Event indicating the three-finger double-tap gesture.|
| TYPE_THREE_FINGER_DOUBLE_TAP_AND_HOLD    | 53   | Event indicating the three-finger double-tap-and-hold gesture.         |
| TYPE_THREE_FINGER_TRIPLE_TAP  |54| Event indicating the three-finger triple-tap gesture.|
| TYPE_THREE_FINGER_TRIPLE_TAP_AND_HOLD    | 55   | Event indicating the three-finger triple-tap-and-hold gesture.         |
| TYPE_FOUR_FINGER_SINGLE_TAP  |56| Event indicating the four-finger single-tap gesture.|
| TYPE_FOUR_FINGER_DOUBLE_TAP  |57| Event indicating the four-finger double-tap gesture.|
| TYPE_FOUR_FINGER_DOUBLE_TAP_AND_HOLD     | 58   | Event indicating the four-finger double-tap-and-hold gesture.         |
| TYPE_FOUR_FINGER_TRIPLE_TAP  |59| Event indicating the four-finger triple-tap gesture.|
| TYPE_FOUR_FINGER_TRIPLE_TAP_AND_HOLD     | 60   | Event indicating the four-finger triple-tap-and-hold gesture.         |
| TYPE_THREE_FINGER_SWIPE_UP   |61| Event indicating the three-finger swipe-up gesture.|
| TYPE_THREE_FINGER_SWIPE_DOWN  |62| Event indicating the three-finger swipe-down gesture.|
| TYPE_THREE_FINGER_SWIPE_LEFT  |63|  Event indicating the three-finger swipe-left gesture.|
| TYPE_THREE_FINGER_SWIPE_RIGHT  |64| Event indicating the three-finger swipe-right gesture.|
| TYPE_FOUR_FINGER_SWIPE_UP    |65| Event indicating the four-finger swipe-up gesture.|
| TYPE_FOUR_FINGER_SWIPE_DOWN  |66| Event indicating the four-finger swipe-down gesture.|
| TYPE_FOUR_FINGER_SWIPE_LEFT  |67| Event indicating the four-finger swipe-left gesture.|
| TYPE_FOUR_FINGER_SWIPE_RIGHT  |68| Event indicating the four-finger swipe-right gesture.|
| TYPE_PAGE_ACTIVE<sup>23+</sup> |69| Page active state changed. |
| TYPE_NOTIFICATION_UPDATE |70| Notification content or state updated.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| TYPE_FOCUS_INVISIBLE |71| Focus becomes invisible.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| TYPE_ONE_FINGER_DOUBLE_TAP |72| Single-finger double tap gesture.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| TYPE_TOUCH_GUIDE_GESTURE |73| Touch browsing gesture event.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |

## AccessibilityAction

Enumerates executable actions for accessibility node elements.

An accessibility node element refers to a component on the UI that can perform accessibility operations, such as a button or text input box.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                        | Value   | Description                      |
| -------------------------- | ---- | ------------------------ |
| ACCESSIBILITY_FOCUS        | 0    | Gains accessibility focus. The [Parameter](js-apis-inner-application-accessibilityExtensionContext-sys.md#parameter20).accessibilityFocusScene parameter must be configured, with the parameter value being the accessibility focus scenario type.               |
| CLEAR_ACCESSIBILITY_FOCUS | 1    | Clear an accessibility focus.              |
| FOCUS                      | 2    | Gain a focus for a component.               |
| CLEAR_FOCUS                | 3    | Clear a focus for a component.               |
| CLICK                      | 4    | Click a component.                 |
| LONG_CLICK                 | 5    | Long-presses a component.                |
| CUT                        | 6    | Cut the content of a component.               |
| COPY                       | 7    | Copy the content of a component.                |
| PASTE                      | 8    | Paste the content into a component.               |
| SELECT                     | 9    | Select a component.                  |
| SET_TEXT                   | 10   | Sets the text of a component. The [Parameter](js-apis-inner-application-accessibilityExtensionContext-sys.md#parameter20).setText parameter must be configured, with the parameter value being the text content to set.               |
| SCROLL_FORWARD             | 11   | Scrolls a component forward (toward the end of the content). The [Parameter](js-apis-inner-application-accessibilityExtensionContext-sys.md#parameter20).scrollType parameter must be configured, with the parameter value being 'fullScreen' or 'halfScreen'.                 |
| SCROLL_BACKWARD            | 12   | Scrolls a component backward (toward the beginning of the content). The [Parameter](js-apis-inner-application-accessibilityExtensionContext-sys.md#parameter20).scrollType parameter must be configured, with the parameter value being 'fullScreen' or 'halfScreen'.                |
| SET_SELECTION              | 13   | Selects a text range within a component. The [Parameter](js-apis-inner-application-accessibilityExtensionContext-sys.md#parameter20).selectTextBegin, [Parameter](js-apis-inner-application-accessibilityExtensionContext-sys.md#parameter20).selectTextEnd, and [Parameter](js-apis-inner-application-accessibilityExtensionContext-sys.md#parameter20).selectTextInForWard parameters must be configured, with the parameter values being the start coordinate, end coordinate of the selected text, and whether to select forward.             |
| SET_CURSOR_POSITION        | 14   | Sets the cursor position within a component. The [Parameter](js-apis-inner-application-accessibilityExtensionContext-sys.md#parameter20).offset parameter must be configured, with the parameter value being the character offset of the cursor.             |
| HOME                       | 15   | Performs the operation of returning to the home screen.<br>**Usage constraint:** This operation takes effect only on the main screen in multi-screen scenarios.              |
| BACK                       | 16   | Return to the previous screen.              |
| RECENT_TASK                | 17   | Displays recent tasks.                  |
| NOTIFICATION_CENTER        | 18   | Displays the notification center.                  |
| CONTROL_CENTER             | 19   | Displays the control center.                  |
| SPAN_CLICK                 | 20   | Performs a click operation on partial text. The [Parameter](js-apis-inner-application-accessibilityExtensionContext-sys.md#parameter20).spanId parameter must be configured, with the parameter value being the hyperlink text ID.             |
| INJECT_ACTION              | 21   | Injects an action that simulates a user operation. The [Parameter](js-apis-inner-application-accessibilityExtensionContext-sys.md#parameter20).injectActionType parameter must be configured, with the parameter value being the injection action type.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.|
| EXECUTE_CUSTOM_ACTION      | 22   | Executes a custom action. The [Parameter](js-apis-inner-application-accessibilityExtensionContext-sys.md#parameter20).customAction parameter must be configured, with the parameter value being the name of the custom action.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.    |

## FocusMoveResultCode<sup>23+</sup>

Enumerates the result codes returned by the focusable node query.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                        | Value   | Description                      |
| -------------------------- | ---- | ------------------------ |
| NOT_SUPPORTED                             | -1 | Query is not supported.             |
| SEARCH_SUCCESS                            | 0  | The node is queried successfully.        |
| SEARCH_SUCCESS_NEXT_BYPASS_DESCENDANTS    | 1  | The node query is successful. It is recommended to use the parameter bypassSelfDescendants in the next query to improve query efficiency.   |
| SEARCH_FAILURE                            | 2  | Failed to query the node. The current page has no focusable node.             |
| SEARCH_FAILURE_IN_CHILD_TREE              | 3  | Failed to query the node. The current container has no focusable node.            |
| SEARCH_FAILURE_LOST_NODE                  | 4  | Failed to query the node. The start node is not found.                |
| SEARCH_NEXT                               | 5  | The returned node is not focusable. Continue to query from the returned node.              |
| DOUBLE_CHECK_CHILD_PROPERTY               | 6  | The returned node is not focusable. Continue to query from all descendants of the returned node.   |
| DOUBLE_CHECK_CHILD_PROPERTY_AND_GET_LAST  | 7  | The returned node is not focusable. Continue to query from the last child node of the returned node. |
| SEARCH_FAILURE_IN_SCROLL                  | 8  | Failed to query the node in the scrollable component.       |

## InjectActionType

Enumerates injection actions.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                        | Value   | Description                  |
| -------------------------- | ---- | ------------------------ |
| CLICK                      | 1    | Injects a click action.        |
| DOUBLE_CLICK               | 2    | Injects a double-click action.        |
| LONG_CLICK                 | 3    | Injects a long-click action.        |

## AccessibilityFocusScene

Enumerates the focus scenarios for accessibility.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                        | Value   | Description                     |
| -------------------------- | ---- | ------------------------ |
| HOVER_FOCUS                |  1 | The current focus scenario is tap focus.         |
| SWIPE_FOCUS                |  2 | The current focus scenario is swipe focus.         |
| SCROLL_FOCUS               |  3 | The current focus scenario is scroll focus.         |

## FocusRuleType

Enumerates the focus rule types.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                         | Value    | Description                       |
| -------------------------- | ---- | ------------------------ |
| DEFAULT                    | 1    | Default focus type. Nodes are not filtered by a specific type, and all nodes can be focus targets.   |
| FOCUS_BY_LINK              | 2    | Focus by link type, for example, elements on a web page that can be tapped to navigate.                |
| FOCUS_BY_TITLE             | 3    | Focus by title type, for example, heading elements at various levels on a page.                |

## OperateVirtualNodeResult

Enumerates the result types of operating virtual nodes for accessibility.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                        | Value   | Description                     |
| -------------------------- | ---- | ------------------------ |
| SUCCESS                            |  0 | The operation is successful.            |
| ACCESSIBILITY_ELEMENT_NOT_EXIST    |  1 | The node to be operated does not exist. |
| CANNOT_MODIFY_ROOT_NODE            |  2 | The current root node cannot be modified. |
| ACCESSIBILITY_PROPERTY_IS_EMPTY    |  3 | The accessibility node property is empty.   |
| ALLOCATE_ID_FAILED                 |  4 | Failed to allocate a virtual node ID.   |
| VIRTUAL_NODE_PARAMETER_IS_EMPTY    |  5 | The array of newly added virtual nodes is empty. |
| INTERNAL_ERROR                     |  6 | System exception.            |
| VIRTUAL_NODE_NOT_SUPPORTED         |  7 | Virtual node operations are not supported.   |

## AccessibilitySourceType

Enumerates the source types of accessibility nodes.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Name                        | Value   | Description                     |
| -------------------------- | ---- | ------------------------ |
| DEFAULT                                   |  1 | Default node type.             |
| ADDED_FROM_ACCESSIBILITY_VIRTUAL_NODE     |  2 | The current node is a newly added virtual node.  |
| UPDATED_FROM_ACCESSIBILITY_VIRTUAL_NODE   |  3 | The current node is a node with modified properties.|