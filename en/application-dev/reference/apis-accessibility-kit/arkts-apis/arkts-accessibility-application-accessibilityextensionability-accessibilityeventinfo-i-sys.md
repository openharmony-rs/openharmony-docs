# AccessibilityEventInfo (System API)

Describes the accessibility event information.

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { AccessibilityExtensionAbility, AccessibilityElement, AccessibilityExtensionContext, ElementAttributeKeys, ElementAttributeValues, FocusDirection, FocusType, Rect, WindowType, AccessibilityEvent, AccessibilityEventInfo, Parameter, FocusRule, FocusCondition, FocusMoveResult, AccessibilityVirtualNode, TouchPosition } from '@kit.AccessibilityKit';
```

## eventType

```TypeScript
eventType: AccessibilityEventType
```

Accessibility event type.

**Type:** [AccessibilityEventType](arkts-accessibility-accessibility-accessibilityeventtype-e-sys.md)

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## extraInfo

```TypeScript
extraInfo?: string
```

For TextArea, TextInput, SearchField, and RichEdit components, when text content is added or deleted, this property indicates the specific text content added or deleted. The default value is an empty string.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## target

```TypeScript
target?: AccessibilityElement
```

Target component where the event occurs. When the accessibility event involves a specific component, this property contains the component information.

**Type:** [AccessibilityElement](arkts-accessibility-accessibilityelement-t.md)

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## timestamp

```TypeScript
timestamp?: number
```

Event timestamp, in milliseconds. The default value is **0**.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.
