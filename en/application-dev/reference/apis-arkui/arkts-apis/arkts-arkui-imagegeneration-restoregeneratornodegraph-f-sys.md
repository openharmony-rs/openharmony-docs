# restoreGeneratorNodeGraph (System API)

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## restoreGeneratorNodeGraph

```TypeScript
function restoreGeneratorNodeGraph(uiContext: UIContext): Promise<void>
```

Restore the AI node graph Sheet.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | The context of dialog for ui display. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Returns the result of restore operation. |
