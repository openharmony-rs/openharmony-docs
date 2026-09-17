# getMaterialInfo

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## getMaterialInfo

```TypeScript
function getMaterialInfo(): MaterialInfo
```

Obtains the material configuration information of this application. The returned configuration information comes from the metadata configured in the [module.json5](../../../quick-start/module-configuration-file.md) file of the application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [MaterialInfo](arkts-arkui-uimaterial-materialinfo-i.md) | Material configuration information of this application, including the material enabling state and material type. |
