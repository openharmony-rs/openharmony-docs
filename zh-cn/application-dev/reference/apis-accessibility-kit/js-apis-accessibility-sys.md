# @ohos.accessibility (辅助功能)（系统接口）

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->

本模块提供无障碍事件类型和无障碍节点元素可执行的操作。

> **说明：**
>
> - 本模块首批接口从 API version 20 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 当前页面仅包含本模块的系统接口。其他公开接口参见[@ohos.accessibility](js-apis-accessibility.md)。

## 导入模块

```ts
import { accessibility } from '@kit.AccessibilityKit';
```


## AccessibilityEventType

无障碍事件类型。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core


| 名称                     | 值                    |说明|
| ---------------------------------------- | ---- | ---------------------- |
| TYPE_ACCESSIBILITY_FOCUS                 | 0    | 表示获得无障碍焦点。             |
| TYPE_ACCESSIBILITY_FOCUS_CLEAR           | 1    | 表示清除无障碍焦点。             |
| TYPE_CLICK                               | 2    | 表示点击组件。                |
| TYPE_LONG_CLICK                          | 3    | 表示长按点击组件。              |
| TYPE_SELECT                              | 4    | 表示选择组件。                |
| TYPE_HOVER_ENTER                         | 5    | 表示悬停进入组件。              |
| TYPE_HOVER_EXIT                          | 6    | 表示悬停离开组件。              |
| TYPE_FOCUS                               | 7    | 表示组件获得焦点。              |
| TYPE_TEXT_UPDATE                         | 8    | 表示组件文本已更改。             |
| TYPE_TEXT_SELECTION_UPDATE               | 9    | 表示组件选定文本已更改。  |
| TYPE_SCROLL                              | 10   | 表示滚动视图。                |
| TYPE_REQUEST_FOCUS_FOR_ACCESSIBILITY     | 11   | 表示主动聚焦。                |
| TYPE_ANNOUNCE_FOR_ACCESSIBILITY          | 12   | 表示主动播报。                |
| TYPE_REQUEST_FOCUS_FOR_ACCESSIBILITY_NOT_INTERRUPT | 13   | 表示主动聚焦不打断。             |
| TYPE_ANNOUNCE_FOR_ACCESSIBILITY_NOT_INTERRUPT | 14   | 表示主动播报不打断。             |
| TYPE_ELEMENT_INFO_CHANGE                 | 15   | 表示组件信息改变。              |
| TYPE_SCROLLING                           | 16   | 表示滚动视图中有item被滚出屏幕。     |
| TYPE_WINDOW_ADD                          | 17   | 表示添加窗口。                |
| TYPE_WINDOW_REMOVE                       | 18   | 表示删除窗口。                |
| TYPE_WINDOW_BOUNDS                       | 19   | 表示窗口边界改变。              |
| TYPE_WINDOW_ACTIVE                       | 20   | 表示切换窗口活动状态             |
| TYPE_WINDOW_FOCUS                        | 21   | 表示窗口焦点发生变化。            |
| TYPE_WINDOW_PROPERTY                     | 22   | 表示窗口属性变化事件。例如：透明度、大小等。 |
| TYPE_WINDOW_LAYER                        | 23   | 表示窗口层级变化。              |
| TYPE_TOUCH_BEGIN                         | 24   | 表示开始手指触摸事件。            |
| TYPE_TOUCH_END                           | 25   | 表示结束手指触摸事件。            |
| TYPE_PAGE_CONTENT_UPDATE  |26| 表示页面内容刷新。|
| TYPE_PAGE_STATE_UPDATE  |27| 表示页面状态刷新。|
| TYPE_PAGE_OPEN  |28| 表示页面打开。|
| TYPE_PAGE_CLOSE  |29| 表示页面关闭。|
| TYPE_SWIPE_LEFT           |30| 表示向左的手势。    |
| TYPE_SWIPE_LEFT_THEN_RIGHT  |31|  表示先向左再向右的手势。|
| TYPE_SWIPE_LEFT_THEN_UP     |32| 表示先向左再向上的手势。|
| TYPE_SWIPE_LEFT_THEN_DOWN   |33| 表示先向左再向下的手势。|
| TYPE_SWIPE_RIGHT          |34| 表示向右的手势。    |
| TYPE_SWIPE_RIGHT_THEN_LEFT  |35| 表示先向右再向左的手势。|
| TYPE_SWIPE_RIGHT_THEN_UP    |36| 表示先向右再向上的手势。|
| TYPE_SWIPE_RIGHT_THEN_DOWN  |37| 表示先向右再向下的手势。|
| TYPE_SWIPE_UP             |38| 表示向上的手势。   |
| TYPE_SWIPE_UP_THEN_LEFT     |39| 表示先向上再向左的手势。|
| TYPE_SWIPE_UP_THEN_RIGHT    |40| 表示先向上再向右的手势。|
| TYPE_SWIPE_UP_THEN_DOWN     |41| 表示先向上再向下的手势。|
| TYPE_SWIPE_DOWN           |42| 表示向下的手势。    |
| TYPE_SWIPE_DOWN_THEN_LEFT   |43| 表示先向下再向左的手势。|
| TYPE_SWIPE_DOWN_THEN_RIGHT  |44| 表示先向下再向右的手势。|
| TYPE_SWIPE_DOWN_THEN_UP     |45| 表示先向下再向上的手势。|
| TYPE_TWO_FINGER_SINGLE_TAP   |46| 表示双指单击的手势。|
| TYPE_TWO_FINGER_DOUBLE_TAP   |47|  表示双指双击的手势。|
| TYPE_TWO_FINGER_DOUBLE_TAP_AND_HOLD      | 48   | 表示双指双击且长按的手势。          |
| TYPE_TWO_FINGER_TRIPLE_TAP   |49| 表示双指三击的手势。|
| TYPE_TWO_FINGER_TRIPLE_TAP_AND_HOLD      | 50   | 表示双指三击且长按的手势。          |
| TYPE_THREE_FINGER_SINGLE_TAP  |51| 表示三指单击的手势。|
| TYPE_THREE_FINGER_DOUBLE_TAP  |52| 表示三指双击的手势。|
| TYPE_THREE_FINGER_DOUBLE_TAP_AND_HOLD    | 53   | 表示三指双击且长按的手势。          |
| TYPE_THREE_FINGER_TRIPLE_TAP  |54| 表示三指三击的手势。|
| TYPE_THREE_FINGER_TRIPLE_TAP_AND_HOLD    | 55   | 表示三指三击且长按的手势。          |
| TYPE_FOUR_FINGER_SINGLE_TAP  |56| 表示四指单击的手势。|
| TYPE_FOUR_FINGER_DOUBLE_TAP  |57| 表示四指双击的手势。|
| TYPE_FOUR_FINGER_DOUBLE_TAP_AND_HOLD     | 58   | 表示四指双击且长按的手势。          |
| TYPE_FOUR_FINGER_TRIPLE_TAP  |59| 表示四指三击的手势。|
| TYPE_FOUR_FINGER_TRIPLE_TAP_AND_HOLD     | 60   | 表示四指三击且长按的手势。          |
| TYPE_THREE_FINGER_SWIPE_UP   |61| 表示三指向上滑动的手势。|
| TYPE_THREE_FINGER_SWIPE_DOWN  |62| 表示三指向下滑动的手势。|
| TYPE_THREE_FINGER_SWIPE_LEFT  |63|  表示三指向左滑动的手势。|
| TYPE_THREE_FINGER_SWIPE_RIGHT  |64| 表示三指向右滑动的手势。|
| TYPE_FOUR_FINGER_SWIPE_UP    |65| 表示四指向上滑动的手势。|
| TYPE_FOUR_FINGER_SWIPE_DOWN  |66| 表示四指向下滑动的手势。|
| TYPE_FOUR_FINGER_SWIPE_LEFT  |67| 表示四指向左滑动的手势。|
| TYPE_FOUR_FINGER_SWIPE_RIGHT  |68| 表示四指向右滑动的手势。|

## AccessibilityAction

表示无障碍节点元素可执行的操作枚举。

无障碍节点元素是指，UI界面上可执行无障碍操作的一些组件，例如：按钮、文本输入框等组件。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

| 名称                         | 值    | 说明                       |
| -------------------------- | ---- | ------------------------ |
| ACCESSIBILITY_FOCUS        | 0    | 表示获得无障碍焦点。               |
| CLEAR_ACCESSIBILITY_FOCUS | 1    | 表示清除无障碍焦点。               |
| FOCUS                      | 2    | 表示组件获得焦点。                |
| CLEAR_FOCUS                | 3    | 表示清除组件焦点。                |
| CLICK                      | 4    | 表示点击组件。                  |
| LONG_CLICK                 | 5    | 表示长按点击组件。                |
| CUT                        | 6    | 表示剪切组件内容。                |
| COPY                       | 7    | 表示拷贝组件内容。                 |
| PASTE                      | 8    | 表示粘贴内容到组件。                |
| SELECT                     | 9    | 表示选择组件。                   |
| SET_TEXT                   | 10   | 表示设置组件的文本。               |
| SCROLL_FORWARD             | 11   | 表示向前滚动组件。                 |
| SCROLL_BACKWARD            | 12   | 表示向后滚动组件。                |
| SET_SELECTION              | 13   | 表示选定组件内文本范围。             |
| SET_CURSOR_POSITION        | 14   | 表示设置组件内的光标位置。             |
| HOME                       | 15   | 表示组件返回首页操作。              |
| BACK                       | 16   | 表示执行返回操作。               |
| RECENT_TASK                | 17   | 显示最近任务。                  |
| NOTIFICATION_CENTER        | 18   | 显示通知中心。                  |
| CONTROL_CENTER             | 19   | 显示控制中心。                  |
| SPAN_CLICK                 | 20   | 对局部文本进行点击操作。             |

## FocusMoveResultCode<sup>23+</sup>

表示查询无障碍节点返回结果类型的枚举。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

| 名称                         | 值    | 说明                       |
| -------------------------- | ---- | ------------------------ |
| NOT_SUPPORTED                             | -1 | 当前节点不支持查询操作。              |
| SEARCH_SUCCESS                            | 0  | 节点查询成功。         |
| SEARCH_SUCCESS_NEXT_BYPASS_DESCENDANTS    | 1  | 节点查询成功，建议下一次查询使用参数bypassSelfDescendants可更快获取结果。   |
| SEARCH_FAILURE                            | 2  | 节点查询失败，当前节点所在页面内无可聚焦节点。              |
| SEARCH_FAILURE_IN_CHILD_TREE              | 3  | 节点查询失败，当前节点所在容器内无可聚焦节点。             |
| SEARCH_FAILURE_LOST_NODE                  | 4  | 节点查询失败，未找到起始节点。                 |
| SEARCH_NEXT                               | 5  | 返回节点不具备可聚焦属性，继续使用返回节点查询。               |
| DOUBLE_CHECK_CHILD_PROPERTY               | 6  | 返回节点不具备可聚焦属性，需要使用返回节点的所有子节点继续查询。    |
| DOUBLE_CHECK_CHILD_PROPERTY_AND_GET_LAST  | 7  | 返回节点不具备可聚焦属性，需要使用返回节点的子节点列表中的最后一个节点继续查询。  |
| SEARCH_FAILURE_IN_SCROLL                  | 8  | 节点在滚动组件内查询失败。        |

