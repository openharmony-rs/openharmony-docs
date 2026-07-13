# EventType

```TypeScript
type EventType = 'accessibilityFocus' | 'accessibilityFocusClear' |
  'click' | 'longClick' | 'focus' | 'select' | 'hoverEnter' | 'hoverExit' |
  'textUpdate' | 'textSelectionUpdate' | 'scroll' | 'requestFocusForAccessibility' |
  'announceForAccessibility' | 'requestFocusForAccessibilityNotInterrupt' | 
  'announceForAccessibilityNotInterrupt' | 'scrolling' | 'pageActive' | 'notificationUpdate' | 'focusInvisible'
```

无障碍事件类型。

**起始版本：** 7

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

| 类型 | 说明 |
| --- | --- |
| 'accessibilityFocus' | 表示获得无障碍焦点的事件。 |
| 'accessibilityFocusClear' | 表示清除无障碍焦点的事件。 |
| 'click' | 表示点击组件的事件。 |
| 'longClick' | 表示长按组件的事件。 |
| 'focus' | 表示组件获得焦点的事件，当前版本暂不支持。 |
| 'select' | 表示选择组件的事件。 |
| 'hoverEnter' | 表示悬停进入组件的事件。 |
| 'hoverExit' | 表示悬停离开组件的事件。 |
| 'textUpdate' | 表示组件文本已更改的事件。 |
| 'textSelectionUpdate' | 表示选定文本已更改的事件，当前版本暂不支持。 |
| 'scroll' | 表示滚动视图的事件。 |
| 'requestFocusForAccessibility' | 表示主动聚焦的事件。 [since 12] |
| 'announceForAccessibility' | 表示主动播报的事件。 [since 12] |
| 'requestFocusForAccessibilityNotInterrupt' | 表示主动聚焦不打断的事件。 [since 18] |
| 'announceForAccessibilityNotInterrupt' | 表示主动播报不打断的事件。 [since 18] |
| 'scrolling' | 表示滚动视图中有item被滚出屏幕的事件。 [since 18] |
| 'pageActive' | 表示页面变化的事件，值固定为'pageActive'字符串。 [since 23] |
| 'notificationUpdate' | 表示通知变化的事件，值固定为'notificationUpdate'字符串。 [since 26.0.0] |
| 'focusInvisible' | [since 26.0.0] |

