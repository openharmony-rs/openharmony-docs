# GenerateTextTaskResult（系统接口）

```TypeScript
interface GenerateTextTaskResult
```

AI生成文本任务的配置结果。

**起始版本：** 23

<!--Device-imageGeneration-interface GenerateTextTaskResult--><!--Device-imageGeneration-interface GenerateTextTaskResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## content

```TypeScript
content: string
```

AI生成文本任务的最终数据。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateTextTaskResult-content: string--><!--Device-GenerateTextTaskResult-content: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## reasoningContent

```TypeScript
reasoningContent: string
```

思考AI生成文本任务中的信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateTextTaskResult-reasoningContent: string--><!--Device-GenerateTextTaskResult-reasoningContent: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
