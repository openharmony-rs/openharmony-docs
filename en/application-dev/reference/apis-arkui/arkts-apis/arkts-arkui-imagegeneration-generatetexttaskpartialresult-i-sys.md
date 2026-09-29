# GenerateTextTaskPartialResult (System API)

```TypeScript
interface GenerateTextTaskPartialResult
```

Configuration stream result for AI-generated text tasks.

@interface GenerateTextTaskPartialResult

**Since:** 23

<!--Device-imageGeneration-interface GenerateTextTaskPartialResult--><!--Device-imageGeneration-interface GenerateTextTaskPartialResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## content

```TypeScript
content?: string
```

Final data in AI-generated text task, available in partial result.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GenerateTextTaskPartialResult-content?: string--><!--Device-GenerateTextTaskPartialResult-content?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## partialFail

```TypeScript
partialFail?: BusinessError
```

Information of the partial error corresponding to AI-generated text task, available in partial error result.

**Type:** [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GenerateTextTaskPartialResult-partialFail?: BusinessError--><!--Device-GenerateTextTaskPartialResult-partialFail?: BusinessError-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## reasoningContent

```TypeScript
reasoningContent?: string
```

Think information in AI-generated text task, available in partial result.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GenerateTextTaskPartialResult-reasoningContent?: string--><!--Device-GenerateTextTaskPartialResult-reasoningContent?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## type

```TypeScript
type: PartialResultType
```

The type information used for AI-generated text task.

**Type:** [PartialResultType](arkts-arkui-imagegeneration-partialresulttype-e-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GenerateTextTaskPartialResult-type: PartialResultType--><!--Device-GenerateTextTaskPartialResult-type: PartialResultType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
