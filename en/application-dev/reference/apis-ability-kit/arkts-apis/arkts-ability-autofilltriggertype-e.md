# AutoFillTriggerType

```TypeScript
export enum AutoFillTriggerType
```

This module specifies how the autofill service is triggered, based on different user gestures.

**Since:** 26.0.0

<!--Device-unnamed-export enum AutoFillTriggerType--><!--Device-unnamed-export enum AutoFillTriggerType-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## AUTO_REQUEST

```TypeScript
AUTO_REQUEST = 0
```

Automatically triggers the auto-fill service. It can be automatically triggered after a TextInput component gains focus.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-AutoFillTriggerType-AUTO_REQUEST = 0--><!--Device-AutoFillTriggerType-AUTO_REQUEST = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## MANUAL_REQUEST

```TypeScript
MANUAL_REQUEST = 1
```

Manually triggers the auto-fill service. It can be triggered by long-pressing any input component to bring up a secondary menu, selecting auto-fill, and triggering the auto-fill service.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-AutoFillTriggerType-MANUAL_REQUEST = 1--><!--Device-AutoFillTriggerType-MANUAL_REQUEST = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## PASTE_REQUEST

```TypeScript
PASTE_REQUEST = 2
```

Triggers the auto-fill service via paste. It is only triggered after the user has already long-pressed a username or password in the password vault to select secure copy, and then long-presses any input component to bring up a secondary menu and selects paste.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-AutoFillTriggerType-PASTE_REQUEST = 2--><!--Device-AutoFillTriggerType-PASTE_REQUEST = 2-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore
