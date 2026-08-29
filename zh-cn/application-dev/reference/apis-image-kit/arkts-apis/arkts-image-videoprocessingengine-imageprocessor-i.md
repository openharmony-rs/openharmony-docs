# ImageProcessor

提供ImageProcessor类型，包括图像处理功能。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

## 导入模块

```TypeScript
import { videoProcessingEngine } from '@kit.ImageKit';
```

## enhanceDetail

```TypeScript
enhanceDetail(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): Promise<image.PixelMap>
```

根据指定的宽度和高度对源图像进行必要的缩放处理，生成目标图像。 提供不同质量等级的缩放方式，用于平衡处理性能和图像质量。该方法使用Promise返回处理结果。

**起始版本：** 18

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceImage | image.PixelMap | 是 | 源PixelMap。 |
| width | number | 是 | 缩放后的宽度。 |
| height | number | 是 | 缩放后的高度。 |
| level | QualityLevel | 否 | 处理质量等级。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;image.PixelMap&gt; | Promise对象，用于返回处理后的PixelMap对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该能力。由于设备能力受限，enhanceDetail函数无法正常工作。 |
| [29200007](../errorcode-videoprocessingengine.md#29200007-内存不足) | 内存不足。 |
| [29200009](../errorcode-videoprocessingengine.md#29200009-值无效) | 输入参数无效。以下情况会返回该错误： 1 - 输入或输出图像缓冲区无效，例如图像缓冲区的宽度或高度过大，或者色彩空间不正确。 2 - 参数无效，例如细节增强质量等级不正确。 |

**示例**

```TypeScript
import { image, videoProcessingEngine } from '@kit.ImageKit';

async function enhanceDetail(sourceImage: image.PixelMap, width: number, height: number) {
  await videoProcessingEngine.initializeEnvironment();
  let imageProcessor = videoProcessingEngine.create() as videoProcessingEngine.ImageProcessor;
  // 示例：width可配置为1024，height可配置为1280。
  let enhancedPixelMap: Promise<image.PixelMap> =
    imageProcessor.enhanceDetail(sourceImage, width, height, videoProcessingEngine.QualityLevel.HIGH);
}
```

## enhanceDetail

```TypeScript
enhanceDetail(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): Promise<image.PixelMap>
```

根据指定的缩放比例对源图像进行必要的缩放处理，生成目标图像。 提供不同质量等级的缩放方式，用于平衡处理性能和图像质量。该方法使用Promise返回处理结果。

**起始版本：** 18

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceImage | image.PixelMap | 是 | 源PixelMap。 |
| scale | number | 是 | 缩放比例。 |
| level | QualityLevel | 否 | 处理质量等级。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;image.PixelMap&gt; | Promise对象，用于返回处理后的PixelMap对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该能力。由于设备能力受限，enhanceDetail函数无法正常工作。 |
| [29200007](../errorcode-videoprocessingengine.md#29200007-内存不足) | 内存不足。 |
| [29200009](../errorcode-videoprocessingengine.md#29200009-值无效) | 输入参数无效。以下情况会返回该错误： 1 - 输入或输出图像缓冲区无效，例如图像缓冲区的宽度或高度过大，或者色彩空间不正确。 2 - 参数无效，例如细节增强质量等级不正确。 |

**示例**

```TypeScript
import { image, videoProcessingEngine } from '@kit.ImageKit';

async function enhanceDetail(sourceImage: image.PixelMap, scale: number) {
  await videoProcessingEngine.initializeEnvironment();
  let imageProcessor = videoProcessingEngine.create() as videoProcessingEngine.ImageProcessor;
  // 示例：scale可配置为2.0。
  let enhancedPixelMap: Promise<image.PixelMap> =
    imageProcessor.enhanceDetail(sourceImage, scale, videoProcessingEngine.QualityLevel.HIGH);
}
```

## enhanceDetailSync

```TypeScript
enhanceDetailSync(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): image.PixelMap
```

根据指定的宽度和高度对源图像进行必要的缩放处理，生成目标图像。 提供不同质量等级的缩放方式，用于平衡处理性能和图像质量。

**起始版本：** 18

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceImage | image.PixelMap | 是 | 源PixelMap。 |
| width | number | 是 | 缩放后的宽度。 |
| height | number | 是 | 缩放后的高度。 |
| level | QualityLevel | 否 | 处理质量等级。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | 操作成功时返回处理后的PixelMap对象，否则返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该能力。由于设备能力受限，enhanceDetailSync函数无法正常工作。 |
| [29200004](../errorcode-videoprocessingengine.md#29200004-处理失败) | 图像缓冲区处理失败。例如，处理超时。 |
| [29200007](../errorcode-videoprocessingengine.md#29200007-内存不足) | 内存不足。 |
| [29200009](../errorcode-videoprocessingengine.md#29200009-值无效) | 输入参数无效。以下情况会返回该错误： 1 - 输入或输出图像缓冲区无效，例如图像缓冲区的宽度或高度过大，或者色彩空间不正确。 2 - 参数无效，例如细节增强质量等级不正确。 |

**示例**

```TypeScript
import { image, videoProcessingEngine } from '@kit.ImageKit';

sync function enhanceDetailSync(sourceImage: image.PixelMap, width: number, height: number) {
  videoProcessingEngine.initializeEnvironment();
  let imageProcessor = videoProcessingEngine.create() as videoProcessingEngine.ImageProcessor;
  // 示例：width可配置为1024，height可配置为1280。
  let enhancedPixelMap: image.PixelMap = imageProcessor.enhanceDetailSync(
    sourceImage, width, height, videoProcessingEngine.QualityLevel.HIGH);
}
```

## enhanceDetailSync

```TypeScript
enhanceDetailSync(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): image.PixelMap
```

根据指定的缩放比例对源图像进行必要的缩放处理，生成目标图像。 提供不同质量等级的缩放方式，用于平衡处理性能和图像质量。

**起始版本：** 18

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceImage | image.PixelMap | 是 | 源PixelMap。 |
| scale | number | 是 | 缩放比例。 |
| level | QualityLevel | 否 | 处理质量等级。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | 操作成功时返回处理后的PixelMap对象，否则返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 不支持该能力。由于设备能力受限，enhanceDetailSync函数无法正常工作。 |
| [29200004](../errorcode-videoprocessingengine.md#29200004-处理失败) | 图像缓冲区处理失败。例如，处理超时。 |
| [29200007](../errorcode-videoprocessingengine.md#29200007-内存不足) | 内存不足。 |
| [29200009](../errorcode-videoprocessingengine.md#29200009-值无效) | 输入参数无效。以下情况会返回该错误： 1 - 输入或输出图像缓冲区无效，例如图像缓冲区的宽度或高度过大，或者色彩空间不正确。 2 - 参数无效，例如细节增强质量等级不正确。 |

**示例**

```TypeScript
import { image, videoProcessingEngine } from '@kit.ImageKit';

sync function enhanceDetailSync(sourceImage: image.PixelMap, scale: number) {
  videoProcessingEngine.initializeEnvironment();
  let imageProcessor = videoProcessingEngine.create() as videoProcessingEngine.ImageProcessor;
  // 示例：scale可配置为2.0。
  let enhancedPixelMap: image.PixelMap = imageProcessor.enhanceDetailSync(
    sourceImage, scale, videoProcessingEngine.QualityLevel.HIGH);
}
```
