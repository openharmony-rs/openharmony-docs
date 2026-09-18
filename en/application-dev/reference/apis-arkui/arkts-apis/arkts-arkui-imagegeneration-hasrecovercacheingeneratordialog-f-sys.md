# hasRecoverCacheInGeneratorDialog (System API)

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## hasRecoverCacheInGeneratorDialog

```TypeScript
function hasRecoverCacheInGeneratorDialog(uiContext: UIContext): boolean
```

Check whether cache files that can be restored exist in GeneratorDialog. The persistent cache file is used to store configuration parameters for AI image generation.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | the context of dialog for ui display. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if cache can be recovered in GeneratorDialog, false otherwise. |
