# GenerateImageTaskPartialResult (System API)

```TypeScript
interface GenerateImageTaskPartialResult
```

Configuration stream result for AI-generated image tasks.

@interface GenerateImageTaskPartialResult

**Since:** 23

<!--Device-imageGeneration-interface GenerateImageTaskPartialResult--><!--Device-imageGeneration-interface GenerateImageTaskPartialResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## imageData

```TypeScript
imageData?: string
```

Image data of the image corresponding to AI-generated image task, available in partial result.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GenerateImageTaskPartialResult-imageData?: string--><!--Device-GenerateImageTaskPartialResult-imageData?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## imageIndex

```TypeScript
imageIndex?: number
```

Sequence number of the image corresponding to AI-generated image task, available in partial and partial error result.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GenerateImageTaskPartialResult-imageIndex?: int--><!--Device-GenerateImageTaskPartialResult-imageIndex?: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## partialFail

```TypeScript
partialFail?: BusinessError
```

Information of the partial error corresponding to AI-generated image task, available in partial error result.

**Type:** [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GenerateImageTaskPartialResult-partialFail?: BusinessError--><!--Device-GenerateImageTaskPartialResult-partialFail?: BusinessError-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## totalCount

```TypeScript
totalCount?: number
```

Total number of the image corresponding to AI-generated image task, available in completed result.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GenerateImageTaskPartialResult-totalCount?: int--><!--Device-GenerateImageTaskPartialResult-totalCount?: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## type

```TypeScript
type: PartialResultType
```

The type information used for AI-generated image task.

**Type:** [PartialResultType](arkts-arkui-imagegeneration-partialresulttype-e-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-GenerateImageTaskPartialResult-type: PartialResultType--><!--Device-GenerateImageTaskPartialResult-type: PartialResultType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
