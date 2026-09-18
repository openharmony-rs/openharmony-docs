# KeyItem

Enumerates other key information. This refers to the information of other keys that have been pressed when the current [KeyCode](arkts-mdm-systemmanager-keycode-e.md) event occurs.

**Since:** 23

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## downTime

```TypeScript
downTime: number
```

Time when the key action occurs. The value is a microsecond-level timestamp after the system is powered on. Navigation keys do not support combination expansion, so their occurrence time is displayed as 0.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## keyCode

```TypeScript
keyCode: KeyCode
```

Key code.

**Type:** [KeyCode](arkts-mdm-systemmanager-keycode-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## pressed

```TypeScript
pressed: boolean
```

Key action. It indicates whether the key is pressed: **true** for pressed; **false** for released.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
