# AccessibilityEvent

辅助事件信息。

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## elementId

```TypeScript
elementId?: number
```

主动聚焦的组件ID。默认值为0。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## eventType

```TypeScript
eventType: accessibility.EventType | accessibility.WindowUpdateType |
        TouchGuideType | GestureType | PageUpdateType
```

具体事件类型。

EventType：无障碍事件类型；

WindowUpdateType：窗口变化类型；

TouchGuideType：触摸浏览事件类型；

GestureType：手势事件类型；

PageUpdateType：页面刷新类型。

**类型：** accessibility.EventType | accessibility.WindowUpdateType | TouchGuideType | GestureType | PageUpdateType

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## extraInfo

```TypeScript
extraInfo?: string
```

针对TextArea、TextInput、SearchField、RichEdit组件，当文本内容有新增或删除时，携带的文本内容。根据实际场景设置，无特殊限制。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## target

```TypeScript
target?: AccessibilityElement
```

发生事件的目标组件。

**类型：** AccessibilityElement

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## textAnnouncedForAccessibility

```TypeScript
textAnnouncedForAccessibility?: string
```

主动播报的内容。当应用需要主动播报时根据实际场景设置播报内容，无特殊限制。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## timeStamp

```TypeScript
timeStamp?: number
```

事件时间戳，单位是毫秒。默认值为0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

