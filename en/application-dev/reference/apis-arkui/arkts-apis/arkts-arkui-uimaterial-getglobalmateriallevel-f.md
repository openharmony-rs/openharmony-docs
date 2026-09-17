# getGlobalMaterialLevel

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## getGlobalMaterialLevel

```TypeScript
function getGlobalMaterialLevel(): MaterialLevel
```

Obtains the global material level, which is related to the device computing power. This configuration item is defined by the device and cannot be modified.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [MaterialLevel](arkts-arkui-uimaterial-materiallevel-e.md) | Material level of the device. |
