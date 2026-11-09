# GenerateImageTaskParams（系统接口）

```TypeScript
interface GenerateImageTaskParams
```

AI生成图像任务的配置参数选项。

**起始版本：** 23

<!--Device-imageGeneration-interface GenerateImageTaskParams--><!--Device-imageGeneration-interface GenerateImageTaskParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## imageCount

```TypeScript
imageCount?: number
```

一项任务中生成的AI图像数量。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskParams-imageCount?: int--><!--Device-GenerateImageTaskParams-imageCount?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## images

```TypeScript
images: Array<ImageItem>
```

用于AI生成图像任务的图片信息。

**类型：** Array&lt;[ImageItem](arkts-arkui-imagegeneration-imageitem-i-sys.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskParams-images: Array<ImageItem>--><!--Device-GenerateImageTaskParams-images: Array<ImageItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## imageSize

```TypeScript
imageSize: image.Size
```

请求AI生图图片的大小信息。

**类型：** [image.Size](../../apis-image-kit/arkts-apis/arkts-image-image-size-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskParams-imageSize: image.Size--><!--Device-GenerateImageTaskParams-imageSize: image.Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## positionImage

```TypeScript
positionImage?: image.PixelMap
```

多图像生成任务的布局信息参考图。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskParams-positionImage?: image.PixelMap--><!--Device-GenerateImageTaskParams-positionImage?: image.PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## prompt

```TypeScript
prompt: string
```

AI生成图像任务的描述信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskParams-prompt: string--><!--Device-GenerateImageTaskParams-prompt: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## selectPath

```TypeScript
selectPath?: Array<common2D.Point>
```

AI生成图像任务中套索选择的路径信息。

**类型：** Array&lt;[common2D.Point](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-common2d-point-i.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskParams-selectPath?: Array<common2D.Point>--><!--Device-GenerateImageTaskParams-selectPath?: Array<common2D.Point>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## style

```TypeScript
style?: string
```

一种任务中的AI生成图像风格。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GenerateImageTaskParams-style?: string--><!--Device-GenerateImageTaskParams-style?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
