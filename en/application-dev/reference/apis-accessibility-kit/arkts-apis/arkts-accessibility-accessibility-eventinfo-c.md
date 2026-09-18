# EventInfo

Defines the accessibility event information, which describes UI changes or interaction events. It is used as a parameter of [sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md) to define the event type and trigger action. The sent accessibility event will be distributed by the system to registered accessibility applications that match the event type for response. For details, see [sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md).

**Since:** 7

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## constructor

```TypeScript
constructor(jsonObject: Object)
```

Constructor, which is used to construct an EventInfo instance using a JSON object.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jsonObject | Object | Yes | JSON object containing three fields: type, bundleName, and triggerAction. For details, see the example. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

let eventInfo = new accessibility.EventInfo({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});
```

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

// The parameters are, in order: type, bundleName, triggerAction.
let eventInfo = new accessibility.EventInfo('click', 'com.example.MyApplication', 'click');
```

## constructor

```TypeScript
constructor(type: EventType, bundleName: string, triggerAction: Action)
```

Constructor, which is used to construct an EventInfo instance using independent parameters.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [EventType](arkts-accessibility-accessibility-eventtype-t.md) | Yes | Accessibility event types. |
| bundleName | string | Yes | Bundle name of the target app. |
| triggerAction | [Action](arkts-accessibility-accessibility-action-t.md) | Yes | Action that triggers the event. |

**Examples**

See [constructor](#constructor)

## beginIndex

```TypeScript
beginIndex?: number
```

Start index. The default value is **0**.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the target app. This parameter is mandatory.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## componentType

```TypeScript
componentType?: string
```

It should correspond to the event source component type, and the default value is empty.

Example:

- Button type - &gt; 'Button'  
- Image type - &gt; 'Image'

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## contents

```TypeScript
contents?: Array<string>
```

Content list, which is set according to the actual scenario with no special restrictions. The default value is empty.

**Type:** Array&lt;string&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## currentIndex

```TypeScript
currentIndex?: number
```

Current index. The default value is **0**.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## customId

```TypeScript
customId?: string
```

Component ID for proactive focus. Set this parameter based on the actual scenario when the app needs to proactively focus. The default value is empty.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## description

```TypeScript
description?: string
```

Event description, which is customized by the developer based on service requirements. There is no special restriction. The default value is empty.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## elementId

```TypeScript
elementId?: number
```

Element ID of the component. The default value is **0**.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## endIndex

```TypeScript
endIndex?: number
```

End index. The default value is **0**.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## itemCount

```TypeScript
itemCount?: number
```

Total number of items. The default value is **0**.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## lastContent

```TypeScript
lastContent?: string
```

Latest content, which is set according to the actual scenario with no special restrictions. The default value is empty.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## pageId

```TypeScript
pageId ?: number
```

ID of the page where the event occurs. The default value is **0**.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## textAnnouncedForAccessibility

```TypeScript
textAnnouncedForAccessibility?: string
```

Content for auto-broadcasting. When the application needs to proactively broadcast, set the broadcast content according to the actual scenario with no special restrictions, and the default value is empty.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## textMoveUnit

```TypeScript
textMoveUnit?: TextMoveUnit
```

Text moving granularity. The default value is char.

**Type:** [TextMoveUnit](arkts-accessibility-accessibility-textmoveunit-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## textResourceAnnouncedForAccessibility

```TypeScript
textResourceAnnouncedForAccessibility?: Resource
```

Content for proactive announcement, which supports the Resource type. The Resource can only reference string resources (for example, &#36;r('app.string.xxx')).

**Type:** [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## triggerAction

```TypeScript
triggerAction: Action
```

Action that triggers the event (mandatory).

**Type:** [Action](arkts-accessibility-accessibility-action-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## type

```TypeScript
type: EventType
```

Accessibility event type (mandatory).

**Type:** [EventType](arkts-accessibility-accessibility-eventtype-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## windowUpdateType

```TypeScript
windowUpdateType?: WindowUpdateType
```

Window update type.

**Type:** [WindowUpdateType](arkts-accessibility-accessibility-windowupdatetype-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core
