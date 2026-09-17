# AccessibilityAbilityInfo

Provides information about an accessibility application.

**Since:** 7

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## abilityTypes

```TypeScript
readonly abilityTypes: Array<AbilityType>
```

Accessibility application type.

**Type:** Array&lt;[AbilityType](arkts-accessibility-accessibility-abilitytype-t.md)&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## capabilities

```TypeScript
readonly capabilities: Array<Capability>
```

Capabilities list of the accessibility application.

**Type:** Array&lt;[Capability](arkts-accessibility-accessibility-capability-t.md)&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## description

```TypeScript
readonly description: string
```

Description of the accessibility application.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## eventTypes

```TypeScript
readonly eventTypes: Array<EventType>
```

List of events that the accessibility application focuses on.

**Type:** Array&lt;[EventType](arkts-accessibility-accessibility-eventtype-t.md)&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## id

```TypeScript
readonly id: string
```

Ability ID.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## label

```TypeScript
readonly label: string
```

Name of the accessibility app in the extended service list.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## name

```TypeScript
readonly name: string
```

Ability name.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## needHide

```TypeScript
readonly needHide: boolean
```

Whether the auxiliary application is hidden in the list of installed extended services. The value **true** means the auxiliary application is hidden, and the value **false** means the opposite.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## targetBundleNames

```TypeScript
readonly targetBundleNames: Array<string>
```

Name of the target bundle.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core
