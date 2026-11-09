# TaskStatistic（系统接口）

```TypeScript
interface TaskStatistic
```

与AI图像生成任务相关的统计数据。

**起始版本：** 23

<!--Device-imageGeneration-interface TaskStatistic--><!--Device-imageGeneration-interface TaskStatistic-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## generationTime

```TypeScript
generationTime: number
```

AI图像生成任务所需时间（秒）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TaskStatistic-generationTime: double--><!--Device-TaskStatistic-generationTime: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## imageCount

```TypeScript
imageCount: number
```

用于AI图像生成任务的图像数量。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TaskStatistic-imageCount: int--><!--Device-TaskStatistic-imageCount: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## isSticker

```TypeScript
isSticker: boolean
```

图像AI生成任务是否为贴纸生成任务。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TaskStatistic-isSticker: boolean--><!--Device-TaskStatistic-isSticker: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## style

```TypeScript
style: string
```

AI图像生成任务中使用的风格。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TaskStatistic-style: string--><!--Device-TaskStatistic-style: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
