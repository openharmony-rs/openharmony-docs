# AccessibilityEventInfo（系统接口）

无障碍事件信息。

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## eventType

```TypeScript
eventType: AccessibilityEventType
```

无障碍事件类型。

**类型：** AccessibilityEventType

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## extraInfo

```TypeScript
extraInfo?: string
```

针对TextArea、TextInput、SearchField、RichEdit组件， 组件文本内容有新增或删除时，新增或删除的文本内容。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## target

```TypeScript
target?: AccessibilityElement
```

发生事件的目标组件。

**类型：** AccessibilityElement

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp?: number
```

事件时间戳，单位是毫秒。默认值为0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

