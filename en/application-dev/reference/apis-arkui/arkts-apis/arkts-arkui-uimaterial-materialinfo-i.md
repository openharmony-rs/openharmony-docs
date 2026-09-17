# MaterialInfo

Provides material configuration information, including the material enabling state and material type.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## state

```TypeScript
state: MaterialState
```

Material enabling state.

**Type:** [MaterialState](arkts-arkui-uimaterial-materialstate-e.md)

**Default:** MaterialState.DEFAULT

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: MaterialType
```

Material type ID, indicating the material type corresponding to the current configuration. The value is used only for type identification and does not map to underlying features.

**Type:** [MaterialType](arkts-arkui-uimaterial-materialtype-e.md)

**Default:** MaterialType.IMMERSIVE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
