# MaterialOptions (System API)

```TypeScript
interface MaterialOptions
```

System material options.

**Since:** 23

<!--Device-uiMaterial-interface MaterialOptions--><!--Device-uiMaterial-interface MaterialOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## type

```TypeScript
type?: MaterialType
```

Material type. Select MaterialType.NONE when no material effect is needed, and MaterialType.SEMI_TRANSPARENT when a semi-transparent background effect is needed.

Default value: MaterialType.NONE

**Type:** [MaterialType](arkts-arkui-uimaterial-materialtype-e.md)

**Default:** uiMaterial.MaterialType.NONE

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-MaterialOptions-type?: MaterialType--><!--Device-MaterialOptions-type?: MaterialType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
