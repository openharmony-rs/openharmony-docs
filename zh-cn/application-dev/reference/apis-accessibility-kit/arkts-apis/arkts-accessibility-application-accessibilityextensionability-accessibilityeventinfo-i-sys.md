# AccessibilityEventInfo（系统接口）

无障碍事件信息。

**起始版本：** 23

<!--Device-unnamed-export declare interface AccessibilityEventInfo--><!--Device-unnamed-export declare interface AccessibilityEventInfo-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { AccessibilityExtensionAbility, AccessibilityElement, AccessibilityExtensionContext, ElementAttributeKeys, ElementAttributeValues, FocusDirection, FocusType, Rect, WindowType, AccessibilityEvent, AccessibilityEventInfo, Parameter, FocusRule, FocusCondition, FocusMoveResult, AccessibilityVirtualNode, TouchPosition } from '@kit.AccessibilityKit';
import { AccessibilityExtensionAbility, AccessibilityElement, AccessibilityExtensionContext, FocusDirection, Rect, WindowType, AccessibilityEventInfo, Parameter, FocusRule, FocusCondition, FocusMoveResult, AccessibilityVirtualNode, TouchPosition } from '@kit.AccessibilityKit';
```

## eventType

```TypeScript
eventType: AccessibilityEventType
```

无障碍事件类型。

**类型：** [AccessibilityEventType](arkts-accessibility-accessibility-accessibilityeventtype-e-sys.md)

**起始版本：** 23

<!--Device-AccessibilityEventInfo-eventType: AccessibilityEventType--><!--Device-AccessibilityEventInfo-eventType: AccessibilityEventType-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## extraInfo

```TypeScript
extraInfo?: string
```

针对TextArea、TextInput、SearchField、RichEdit组件，当组件文本内容发生增删变化时，此属性表示增删的具体文本内容。默认值为空字符串。

**类型：** string

**起始版本：** 23

<!--Device-AccessibilityEventInfo-extraInfo?: string--><!--Device-AccessibilityEventInfo-extraInfo?: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## target

```TypeScript
target?: AccessibilityElement
```

发生事件的目标组件。当无障碍事件涉及具体组件时，此属性包含该组件信息。

**类型：** [AccessibilityElement](arkts-accessibility-accessibilityelement-t.md)

**起始版本：** 23

<!--Device-AccessibilityEventInfo-target?: AccessibilityElement--><!--Device-AccessibilityEventInfo-target?: AccessibilityElement-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp?: long
```

事件时间戳，单位为毫秒，默认值为0。

**类型：** long

**起始版本：** 23

<!--Device-AccessibilityEventInfo-timestamp?: long--><!--Device-AccessibilityEventInfo-timestamp?: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

