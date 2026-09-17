# openGeneratorNodeGraph (System API)

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## openGeneratorNodeGraph

```TypeScript
function openGeneratorNodeGraph(uiContext: UIContext, options?: GeneratorNodeGraphOptions): Promise<void>
```

Open the AI node graph Sheet.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | the context of dialog for ui display. |
| options | [GeneratorNodeGraphOptions](arkts-arkui-imagegeneration-generatornodegraphoptions-i-sys.md) | No | node graph task parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Returns the result. |
