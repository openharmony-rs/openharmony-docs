# Material

System material object on the UI.

**Since:** 26.0.0

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [MaterialOptions](arkts-arkui-uimaterial-materialoptions-i-sys.md) | No | System material options, including the material type.<br>Default value: **{type:MaterialType.NONE}**. |
