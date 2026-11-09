# GenerateTextTaskPartialResult（系统接口）

```TypeScript
interface GenerateTextTaskPartialResult
```

AI生成文本任务的配置流结果。

**起始版本：** 23

<!--Device-imageGeneration-interface GenerateTextTaskPartialResult--><!--Device-imageGeneration-interface GenerateTextTaskPartialResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## content

```TypeScript
content?: string
```

AI生成文本任务的最终数据，在部分结果下可使用。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateTextTaskPartialResult-content?: string--><!--Device-GenerateTextTaskPartialResult-content?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## partialFail

```TypeScript
partialFail?: BusinessError
```

与AI生成文本任务对应的部分错误信息，可在部分错误结果中获取。

**类型：** [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateTextTaskPartialResult-partialFail?: BusinessError--><!--Device-GenerateTextTaskPartialResult-partialFail?: BusinessError-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## reasoningContent

```TypeScript
reasoningContent?: string
```

思考AI生成文本任务中的信息，在部分结果下可使用。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateTextTaskPartialResult-reasoningContent?: string--><!--Device-GenerateTextTaskPartialResult-reasoningContent?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: PartialResultType
```

用于AI生成文本任务的类型信息。

**类型：** [PartialResultType](arkts-arkui-imagegeneration-partialresulttype-e-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateTextTaskPartialResult-type: PartialResultType--><!--Device-GenerateTextTaskPartialResult-type: PartialResultType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
