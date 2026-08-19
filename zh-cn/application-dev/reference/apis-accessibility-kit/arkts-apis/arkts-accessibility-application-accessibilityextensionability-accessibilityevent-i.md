# AccessibilityEvent

无障碍事件信息。无障碍事件由系统无障碍服务在用户操作或界面变化时生成，通过eventType标识事件类别（包括无障碍事件类型、窗口变化类型、触摸浏览事件类型、手势事件类型、页面更新类型），辅助功能扩展可通过 onAccessibilityEvent回调接收并处理这些事件。

**起始版本：** 9

<!--Device-unnamed-export declare interface AccessibilityEvent--><!--Device-unnamed-export declare interface AccessibilityEvent-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 导入模块

```TypeScript
import { AccessibilityExtensionAbility, AccessibilityElement, AccessibilityExtensionContext, ElementAttributeKeys, ElementAttributeValues, FocusDirection, FocusType, Rect, WindowType, AccessibilityEvent, AccessibilityEventInfo, Parameter, FocusRule, FocusCondition, FocusMoveResult, AccessibilityVirtualNode, TouchPosition } from '@kit.AccessibilityKit';
import { AccessibilityExtensionAbility, AccessibilityElement, AccessibilityExtensionContext, FocusDirection, Rect, WindowType, AccessibilityEventInfo, Parameter, FocusRule, FocusCondition, FocusMoveResult, AccessibilityVirtualNode, TouchPosition } from '@kit.AccessibilityKit';
```

## elementId

```TypeScript
elementId?: long
```

主动聚焦的元素ID。主动聚焦指应用通过无障碍服务主动将焦点聚焦到指定元素上，与用户手动导航聚焦不同。默认值为0。

**类型：** long

**起始版本：** 12

<!--Device-AccessibilityEvent-elementId?: long--><!--Device-AccessibilityEvent-elementId?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## eventType

```TypeScript
eventType: accessibility.EventType | accessibility.WindowUpdateType |
        TouchGuideType | GestureType | PageUpdateType
```

具体事件类型，用于标识当前无障碍事件的类别。 EventType：无障碍事件类型； WindowUpdateType：窗口变化类型； TouchGuideType：触摸浏览事件类型； GestureType：手势事件类型； PageUpdateType：页面更新类型。

**类型：** accessibility.EventType \| accessibility.WindowUpdateType \| [TouchGuideType](arkts-accessibility-touchguidetype-t.md) \| [GestureType](arkts-accessibility-gesturetype-t.md) \| [PageUpdateType](arkts-accessibility-pageupdatetype-t.md)

**起始版本：** 9

<!--Device-AccessibilityEvent-eventType: accessibility.EventType | accessibility.WindowUpdateType |        TouchGuideType | GestureType | PageUpdateType--><!--Device-AccessibilityEvent-eventType: accessibility.EventType | accessibility.WindowUpdateType |        TouchGuideType | GestureType | PageUpdateType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## extraInfo

```TypeScript
extraInfo?: string
```

针对TextArea、TextInput、SearchField、RichEdit组件，当文本内容有新增或删除时，携带新增或删除的文本内容。根据实际场景设置，无特殊限制，默认为空字符串。

**类型：** string

**起始版本：** 20

<!--Device-AccessibilityEvent-extraInfo?: string--><!--Device-AccessibilityEvent-extraInfo?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## target

```TypeScript
target?: AccessibilityElement
```

发生事件的目标元素。当无障碍事件涉及具体元素时，此属性包含该元素信息。

**类型：** [AccessibilityElement](arkts-accessibility-accessibilityelement-t.md)

**起始版本：** 9

<!--Device-AccessibilityEvent-target?: AccessibilityElement--><!--Device-AccessibilityEvent-target?: AccessibilityElement-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textAnnouncedForAccessibility

```TypeScript
textAnnouncedForAccessibility?: string
```

主动播报的内容。当应用需要主动播报时根据实际场景设置播报内容，无特殊限制，默认为空字符串。

**类型：** string

**起始版本：** 12

<!--Device-AccessibilityEvent-textAnnouncedForAccessibility?: string--><!--Device-AccessibilityEvent-textAnnouncedForAccessibility?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## timeStamp

```TypeScript
timeStamp?: long
```

事件时间戳，取值范围为非负整数，单位为毫秒，默认值为0。

**类型：** long

**起始版本：** 9

<!--Device-AccessibilityEvent-timeStamp?: long--><!--Device-AccessibilityEvent-timeStamp?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

