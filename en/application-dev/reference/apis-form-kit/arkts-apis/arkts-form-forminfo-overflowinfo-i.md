# OverflowInfo

Provides OverflowInfo about funInteraction or sceneAnimation form

@typedef { OverflowInfo }

**Since:** 20

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## area

```TypeScript
area: Rect
```

The overflow animation area

**Type:** [Rect](arkts-form-forminfo-rect-i.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.Form

## duration

```TypeScript
duration: number
```

The overflow animation duration, unit is ms Unit: milliseconds, The value must be an integer within [0,3500].

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.Form

## useDefaultAnimation

```TypeScript
useDefaultAnimation?: boolean
```

Whether use default animation, default is true

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.Form
