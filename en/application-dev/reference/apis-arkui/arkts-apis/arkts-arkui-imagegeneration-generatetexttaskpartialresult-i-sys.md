# GenerateTextTaskPartialResult (System API)

Configuration stream result for AI-generated text tasks.

@interface GenerateTextTaskPartialResult

**Since:** 23

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
