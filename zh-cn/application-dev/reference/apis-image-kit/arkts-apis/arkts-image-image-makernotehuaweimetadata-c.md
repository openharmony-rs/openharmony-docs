# MakerNoteHuaweiMetadata

MakerNoteHuaweiMetadata implements Metadata

来自Huawei相机的照片元数据。

**继承/实现关系：** MakerNoteHuaweiMetadata implements [Metadata](arkts-image-image-metadata-i.md)

**起始版本：** 23

<!--Device-image-class MakerNoteHuaweiMetadata implements Metadata--><!--Device-image-class MakerNoteHuaweiMetadata implements Metadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## clone

```TypeScript
clone(): Promise<MakerNoteHuaweiMetadata>
```

对[MakerNoteHuaweiMetadata](arkts-image-image-makernotehuaweimetadata-c.md)元数据进行克隆。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-clone(): Promise<MakerNoteHuaweiMetadata>--><!--Device-MakerNoteHuaweiMetadata-clone(): Promise<MakerNoteHuaweiMetadata>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;MakerNoteHuaweiMetadata&gt; | Promise对象，当成功获取元数据时返回MakerNoteHuaweiMetadata元数据实例。 |

## createInstance

```TypeScript
static createInstance(): MakerNoteHuaweiMetadata
```

返回[MakerNoteHuaweiMetadata](arkts-image-image-makernotehuaweimetadata-c.md)的空实例。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-static createInstance(): MakerNoteHuaweiMetadata--><!--Device-MakerNoteHuaweiMetadata-static createInstance(): MakerNoteHuaweiMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MakerNoteHuaweiMetadata](arkts-image-image-makernotehuaweimetadata-c.md) | 返回MakerNoteHuaweiMetadata的空实例。 |

## getAllProperties

```TypeScript
getAllProperties(): Promise<Record<string, string | null>>
```

获取图片中所有元数据的属性和值。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-getAllProperties(): Promise<Record<string, string | null>>--><!--Device-MakerNoteHuaweiMetadata-getAllProperties(): Promise<Record<string, string | null>>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, string \| null&gt;&gt; | Promise对象，返回元数据中定义的所有键值对。 |

## getBlob

```TypeScript
getBlob(): Promise<ArrayBuffer>
```

以二进制数据的形式获取元数据。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-getBlob(): Promise<ArrayBuffer>--><!--Device-MakerNoteHuaweiMetadata-getBlob(): Promise<ArrayBuffer>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise对象，返回元数据的二进制数据。 |

## getProperties

```TypeScript
getProperties(key: Array<string>): Promise<Record<string, string | null>>
```

获取图像中属性的值。使用Promise异步回调。

要查询的属性的具体信息请参考[PropertyKey](arkts-image-image-propertykey-e.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-getProperties(key: Array<string>): Promise<Record<string, string | null>>--><!--Device-MakerNoteHuaweiMetadata-getProperties(key: Array<string>): Promise<Record<string, string | null>>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | Array&lt;string&gt; | 是 | 要获取其值的属性的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, string \| null&gt;&gt; | Promise对象，返回元数据要获取的属性的值，如获取失败则返回错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: unsupported metadata type. |

## setBlob

```TypeScript
setBlob(blob: ArrayBuffer): Promise<void>
```

使用二进制数据替换当前元数据。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-setBlob(blob: ArrayBuffer): Promise<void>--><!--Device-MakerNoteHuaweiMetadata-setBlob(blob: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blob | ArrayBuffer | 是 | 要替换的二进制数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible causes: The blob is empty or has a length of 0. |

## setProperties

```TypeScript
setProperties(records: Record<string, string | null>): Promise<void>
```

批量设置图片元数据中的指定属性的值。使用Promise异步回调。

要查询的属性的具体信息请参考[PropertyKey](arkts-image-image-propertykey-e.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-setProperties(records: Record<string, string | null>): Promise<void>--><!--Device-MakerNoteHuaweiMetadata-setProperties(records: Record<string, string | null>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| records | Record&lt;string, string \| null&gt; | 是 | 包含要修改的MakerNoteHuaweiMetadata对象属性键值对的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: unsupported metadata type. |

## burstNumber

```TypeScript
burstNumber?: number
```

连拍数量。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-burstNumber?: int--><!--Device-MakerNoteHuaweiMetadata-burstNumber?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## captureMode

```TypeScript
captureMode?: number
```

捕获模式。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-captureMode?: int--><!--Device-MakerNoteHuaweiMetadata-captureMode?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## cloudLabel

```TypeScript
cloudLabel?: string
```

云增强标签。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-cloudLabel?: string--><!--Device-MakerNoteHuaweiMetadata-cloudLabel?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## faceConfidences

```TypeScript
faceConfidences?: number[]
```

对指定数量的面孔置信度。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-faceConfidences?: int[]--><!--Device-MakerNoteHuaweiMetadata-faceConfidences?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## faceCount

```TypeScript
faceCount?: number
```

人脸数。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-faceCount?: int--><!--Device-MakerNoteHuaweiMetadata-faceCount?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## faceSmileScores

```TypeScript
faceSmileScores?: number[]
```

特定数量面孔的微笑得分。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-faceSmileScores?: int[]--><!--Device-MakerNoteHuaweiMetadata-faceSmileScores?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## focusMode

```TypeScript
focusMode?: FocusMode
```

镜头对焦控制策略，决定相机如何调整焦距。

**类型：** FocusMode

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-focusMode?: FocusMode--><!--Device-MakerNoteHuaweiMetadata-focusMode?: FocusMode-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## isCloudEnhanced

```TypeScript
isCloudEnhanced?: boolean
```

图像是否存在云端增强。true表示存在，false表示不存在。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-isCloudEnhanced?: boolean--><!--Device-MakerNoteHuaweiMetadata-isCloudEnhanced?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## isFrontCamera

```TypeScript
isFrontCamera?: boolean
```

是否使用前置摄像头。true表示使用，false表示不使用。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-isFrontCamera?: boolean--><!--Device-MakerNoteHuaweiMetadata-isFrontCamera?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## isWindSnapshot

```TypeScript
isWindSnapshot?: boolean
```

是否采用风快照模式拍摄。true表示采用，false表示不采用。

该模式是针对拍摄快速移动物体或容易产生模糊场景（如大风中、抓拍运动物体）的专门摄影。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-isWindSnapshot?: boolean--><!--Device-MakerNoteHuaweiMetadata-isWindSnapshot?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## isXmageSupported

```TypeScript
isXmageSupported?: boolean
```

是否支持XMAGE。true表示支持，false表示不支持。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-isXmageSupported?: boolean--><!--Device-MakerNoteHuaweiMetadata-isXmageSupported?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## physicalAperture

```TypeScript
physicalAperture?: number
```

物理光圈值。单位是fNumber。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-physicalAperture?: int--><!--Device-MakerNoteHuaweiMetadata-physicalAperture?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## pitchAngle

```TypeScript
pitchAngle?: number
```

俯仰角度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-pitchAngle?: int--><!--Device-MakerNoteHuaweiMetadata-pitchAngle?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## rollAngle

```TypeScript
rollAngle?: number
```

左右滚动角度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-rollAngle?: int--><!--Device-MakerNoteHuaweiMetadata-rollAngle?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneBeachConfidence

```TypeScript
sceneBeachConfidence?: number
```

拍摄场景：海滩置信度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-sceneBeachConfidence?: int--><!--Device-MakerNoteHuaweiMetadata-sceneBeachConfidence?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneBlueSkyConfidence

```TypeScript
sceneBlueSkyConfidence?: number
```

拍摄场景：蓝天置信度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-sceneBlueSkyConfidence?: int--><!--Device-MakerNoteHuaweiMetadata-sceneBlueSkyConfidence?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneFlowersConfidence

```TypeScript
sceneFlowersConfidence?: number
```

拍摄场景：花卉置信度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-sceneFlowersConfidence?: int--><!--Device-MakerNoteHuaweiMetadata-sceneFlowersConfidence?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneFoodConfidence

```TypeScript
sceneFoodConfidence?: number
```

拍摄场景：美食置信度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-sceneFoodConfidence?: int--><!--Device-MakerNoteHuaweiMetadata-sceneFoodConfidence?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneGreenPlantConfidence

```TypeScript
sceneGreenPlantConfidence?: number
```

拍摄场景：绿色植物置信度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-sceneGreenPlantConfidence?: int--><!--Device-MakerNoteHuaweiMetadata-sceneGreenPlantConfidence?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneNightConfidence

```TypeScript
sceneNightConfidence?: number
```

拍摄场景：夜景置信度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-sceneNightConfidence?: int--><!--Device-MakerNoteHuaweiMetadata-sceneNightConfidence?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneSnowConfidence

```TypeScript
sceneSnowConfidence?: number
```

拍摄场景：雪景置信度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-sceneSnowConfidence?: int--><!--Device-MakerNoteHuaweiMetadata-sceneSnowConfidence?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneStageConfidence

```TypeScript
sceneStageConfidence?: number
```

拍摄场景：舞台演出置信度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-sceneStageConfidence?: int--><!--Device-MakerNoteHuaweiMetadata-sceneStageConfidence?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneSunsetConfidence

```TypeScript
sceneSunsetConfidence?: number
```

拍摄场景：日落置信度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-sceneSunsetConfidence?: int--><!--Device-MakerNoteHuaweiMetadata-sceneSunsetConfidence?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneTextConfidence

```TypeScript
sceneTextConfidence?: number
```

拍摄场景：文本置信度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-sceneTextConfidence?: int--><!--Device-MakerNoteHuaweiMetadata-sceneTextConfidence?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneVersion

```TypeScript
sceneVersion?: number
```

场景识别算法版本号。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-sceneVersion?: int--><!--Device-MakerNoteHuaweiMetadata-sceneVersion?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## xmageBottom

```TypeScript
xmageBottom?: number
```

当照片包含XMAGE水印时，原始图片上，有效内容区域（不含水印覆盖范围）的下边界（相对于图片左上角原点）的垂直坐标。单位为像素（px）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-xmageBottom?: int--><!--Device-MakerNoteHuaweiMetadata-xmageBottom?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## xmageColorMode

```TypeScript
xmageColorMode?: XmageColorMode
```

XMAGE颜色模式。

**类型：** XmageColorMode

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-xmageColorMode?: XmageColorMode--><!--Device-MakerNoteHuaweiMetadata-xmageColorMode?: XmageColorMode-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## xmageLeft

```TypeScript
xmageLeft?: number
```

当照片包含XMAGE水印时，原始图片上，有效内容区域（不含水印覆盖范围）的左边界（相对于图片左上角原点）的水平坐标。单位为像素（px）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-xmageLeft?: int--><!--Device-MakerNoteHuaweiMetadata-xmageLeft?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## xmageRight

```TypeScript
xmageRight?: number
```

当照片包含XMAGE水印时，原始图片上，有效内容区域（不含水印覆盖范围）的右边界（相对于图片左上角原点）的水平坐标。单位为像素（px）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-xmageRight?: int--><!--Device-MakerNoteHuaweiMetadata-xmageRight?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## xmageTop

```TypeScript
xmageTop?: number
```

当照片包含XMAGE水印时，原始图片上，有效内容区域（不含水印覆盖范围）的上边界（相对于图片左上角原点）的垂直坐标。单位为像素（px）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-xmageTop?: int--><!--Device-MakerNoteHuaweiMetadata-xmageTop?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## xmageWatermarkMode

```TypeScript
xmageWatermarkMode?: number
```

XMAGE水印模式。具体取值请参考[Constants](arkts-multimedia-image.md)。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MakerNoteHuaweiMetadata-xmageWatermarkMode?: int--><!--Device-MakerNoteHuaweiMetadata-xmageWatermarkMode?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

