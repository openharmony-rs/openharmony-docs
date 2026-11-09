# GenerateImageTaskPartialResult（系统接口）

```TypeScript
interface GenerateImageTaskPartialResult
```

AI生成图像任务的配置流结果。

**起始版本：** 23

<!--Device-imageGeneration-interface GenerateImageTaskPartialResult--><!--Device-imageGeneration-interface GenerateImageTaskPartialResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## imageData

```TypeScript
imageData?: string
```

与AI生成图像任务对应的图像的图像数据，部分结果可用。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskPartialResult-imageData?: string--><!--Device-GenerateImageTaskPartialResult-imageData?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## imageIndex

```TypeScript
imageIndex?: number
```

AI生成图像任务对应的图片序号，部分结果中可用。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskPartialResult-imageIndex?: int--><!--Device-GenerateImageTaskPartialResult-imageIndex?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## partialFail

```TypeScript
partialFail?: BusinessError
```

与AI生成图像任务对应的部分误差信息，可在部分误差结果中获取。

**类型：** [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskPartialResult-partialFail?: BusinessError--><!--Device-GenerateImageTaskPartialResult-partialFail?: BusinessError-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## totalCount

```TypeScript
totalCount?: number
```

AI生成图像任务对应的图像总数，可在完成结果中查看。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskPartialResult-totalCount?: int--><!--Device-GenerateImageTaskPartialResult-totalCount?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: PartialResultType
```

用于AI生成图像任务的类型信息。

**类型：** [PartialResultType](arkts-arkui-imagegeneration-partialresulttype-e-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskPartialResult-type: PartialResultType--><!--Device-GenerateImageTaskPartialResult-type: PartialResultType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
