# SaveOccasionFlag

```TypeScript
enum SaveOccasionFlag
```

Enumerates the scenarios for saving the application state. This enum is used as an input parameter of [enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md).

**Since:** 9

<!--Device-appRecovery-enum SaveOccasionFlag--><!--Device-appRecovery-enum SaveOccasionFlag-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## SAVE_WHEN_ERROR

```TypeScript
SAVE_WHEN_ERROR = 0x0001
```

Saving the application state when an application fault occurs.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-SaveOccasionFlag-SAVE_WHEN_ERROR = 0x0001--><!--Device-SaveOccasionFlag-SAVE_WHEN_ERROR = 0x0001-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## SAVE_WHEN_BACKGROUND

```TypeScript
SAVE_WHEN_BACKGROUND = 0x0002
```

Saving the application state when the application is switched to the background.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-SaveOccasionFlag-SAVE_WHEN_BACKGROUND = 0x0002--><!--Device-SaveOccasionFlag-SAVE_WHEN_BACKGROUND = 0x0002-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
