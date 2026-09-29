# LiveFormInfo

```TypeScript
export interface LiveFormInfo
```

Provides information about a live form. @typedef { LiveFormInfo }

**Since:** 20

<!--Device-unnamed-export interface LiveFormInfo--><!--Device-unnamed-export interface LiveFormInfo-End-->

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { LiveFormExtensionAbility, LiveFormInfo } from '@kit.FormKit';
```

## borderRadius

```TypeScript
borderRadius: number
```

The form border radius. Unit: vp, The value must be greater than or equal to 0.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-LiveFormInfo-borderRadius: double--><!--Device-LiveFormInfo-borderRadius: double-End-->

**System capability:** SystemCapability.Ability.Form

## formId

```TypeScript
formId: string
```

The form id of the live form.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-LiveFormInfo-formId: string--><!--Device-LiveFormInfo-formId: string-End-->

**System capability:** SystemCapability.Ability.Form

## rect

```TypeScript
rect: formInfo.Rect
```

The live form display area.

**Type:** [formInfo.Rect](arkts-form-forminfo-rect-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-LiveFormInfo-rect: formInfo.Rect--><!--Device-LiveFormInfo-rect: formInfo.Rect-End-->

**System capability:** SystemCapability.Ability.Form
