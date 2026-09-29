# Material

```TypeScript
class Material
```

Base class for system material objects.

**Since:** 26.0.0

<!--Device-uiMaterial-class Material--><!--Device-uiMaterial-class Material-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: MaterialOptions)
```

A constructor used to create a **Material** object.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-Material-constructor(options?: MaterialOptions)--><!--Device-Material-constructor(options?: MaterialOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [MaterialOptions](arkts-arkui-uimaterial-materialoptions-i-sys.md) | No | System material configuration option, including the material type. Pass this parameter when a material type (such as translucency effect) needs to be specified. If not passed, the default material configuration `{type:MaterialType.NONE}` is used, that is, no system material effect. |
