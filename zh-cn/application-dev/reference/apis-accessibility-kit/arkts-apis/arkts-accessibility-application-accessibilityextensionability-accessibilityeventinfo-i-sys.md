# AccessibilityEventInfo（系统接口）

无障碍事件信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface AccessibilityEventInfo--><!--Device-unnamed-export declare interface AccessibilityEventInfo-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## eventType

```TypeScript
eventType: AccessibilityEventType
```

无障碍事件类型。

**类型：** [AccessibilityEventType](arkts-accessibility-accessibility-accessibilityeventtype-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AccessibilityEventInfo-eventType: AccessibilityEventType--><!--Device-AccessibilityEventInfo-eventType: AccessibilityEventType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## extraInfo

```TypeScript
extraInfo?: string
```

针对TextArea、TextInput、SearchField、RichEdit组件， 组件文本内容有新增或删除时，新增或删除的文本内容。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AccessibilityEventInfo-extraInfo?: string--><!--Device-AccessibilityEventInfo-extraInfo?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## target

```TypeScript
target?: AccessibilityElement
```

发生事件的目标组件。

**类型：** [AccessibilityElement](arkts-accessibility-accessibilityelement-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AccessibilityEventInfo-target?: AccessibilityElement--><!--Device-AccessibilityEventInfo-target?: AccessibilityElement-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp?: long
```

事件时间戳，单位是毫秒。默认值为0。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AccessibilityEventInfo-timestamp?: long--><!--Device-AccessibilityEventInfo-timestamp?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

