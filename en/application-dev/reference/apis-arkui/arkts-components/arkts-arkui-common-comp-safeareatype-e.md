# SafeAreaType

```TypeScript
declare enum SafeAreaType
```

Enumerates the types for expanding layout safe areas.

**Since:** 10

<!--Device-unnamed-declare enum SafeAreaType--><!--Device-unnamed-declare enum SafeAreaType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SYSTEM

```TypeScript
SYSTEM = 0
```

Default non-safe area of the system, including the status bar and navigation bar.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SafeAreaType-SYSTEM = 0--><!--Device-SafeAreaType-SYSTEM = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CUTOUT

```TypeScript
CUTOUT = 1
```

The non-safe area of the device, for example, the notch or punch-hole area. The CUTOUT type does not take effect when no Metadata configuration item is added.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SafeAreaType-CUTOUT = 1--><!--Device-SafeAreaType-CUTOUT = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## KEYBOARD

```TypeScript
KEYBOARD = 2
```

Soft keyboard area.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SafeAreaType-KEYBOARD = 2--><!--Device-SafeAreaType-KEYBOARD = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
