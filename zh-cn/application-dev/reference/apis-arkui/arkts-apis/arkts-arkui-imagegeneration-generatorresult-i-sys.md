# GeneratorResult（系统接口）

```TypeScript
interface GeneratorResult
```

AI生成图像的结果

**起始版本：** 23

<!--Device-imageGeneration-interface GeneratorResult--><!--Device-imageGeneration-interface GeneratorResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## image

```TypeScript
image?: image.PixelMap
```

AI生成图像的解码数据。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorResult-image?: image.PixelMap--><!--Device-GeneratorResult-image?: image.PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## statistic

```TypeScript
statistic: TaskStatistic
```

AI生成图像任务的统计数据。

**类型：** [TaskStatistic](arkts-arkui-imagegeneration-taskstatistic-i-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorResult-statistic: TaskStatistic--><!--Device-GeneratorResult-statistic: TaskStatistic-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## url

```TypeScript
url?: string
```

AI生成图像的路径信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorResult-url?: string--><!--Device-GeneratorResult-url?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
