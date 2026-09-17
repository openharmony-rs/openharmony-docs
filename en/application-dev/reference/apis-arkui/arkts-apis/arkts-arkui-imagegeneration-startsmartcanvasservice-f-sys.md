# startSmartCanvasService (System API)

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## startSmartCanvasService

```TypeScript
function startSmartCanvasService(
    context: common.ServiceExtensionContext | common.UIAbilityContext | common.UIExtensionContext): Promise<void>
```

Start the smart canvas service.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [common.ServiceExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-serviceextensioncontext-t-sys.md) &#124; [common.UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) &#124; [common.UIExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiextensioncontext-t.md) | Yes | different ability context. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
