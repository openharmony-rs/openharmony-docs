# ArcAlphabetIndexerInitInfo

Initialization parameters for the **ArcAlphabetIndexer** component.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcAlphabetIndexer, ArcAlphabetIndexerAttribute } from '@kit.ArkUI';
```

## arrayValue

```TypeScript
arrayValue: string[]
```

Array of alphabet index strings. It cannot be set to empty.

**Type:** string[]

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## selected

```TypeScript
selected: number
```

Index of the initial selected item. If the value is out of range, the default value **0** is used.

This parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
