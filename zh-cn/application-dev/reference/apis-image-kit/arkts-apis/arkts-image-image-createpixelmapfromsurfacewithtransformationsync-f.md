# createPixelMapFromSurfaceWithTransformationSync

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

<a id="createpixelmapfromsurfacewithtransformationsync"></a>
## createPixelMapFromSurfaceWithTransformationSync

```TypeScript
function createPixelMapFromSurfaceWithTransformationSync(surfaceId: string, transformEnabled: boolean): PixelMap
```

Creates a PixelMap object based on the ID of a Surface with transformation.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-image-function createPixelMapFromSurfaceWithTransformationSync(surfaceId: string, transformEnabled: boolean): PixelMap--><!--Device-image-function createPixelMapFromSurfaceWithTransformationSync(surfaceId: string, transformEnabled: boolean): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | ID of the Surface. |
| transformEnabled | boolean | 是 | Whether to inverse transform the PixelMap to cancel out the transformation from the Surface.If true, the PixelMap will be transformed by the same amount from the Surface but in a reversed direction;if false, the PixelMap will not be transformed. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | A PixelMap instance if the operation is successful.Otherwise, an exception will be thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get the data from Surface. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation, e.g. on cross-platform. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600305](../errorcode-image.md#7600305-创建pixelmap失败) | Failed to create the PixelMap. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromSurfaceWithTransformationSync(surfaceId: string, transformEnabled: boolean) {
  try {
    const pixelMap: image.PixelMap = image.createPixelMapFromSurfaceWithTransformationSync(surfaceId, transformEnabled);
    console.info('Succeeded in creating the PixelMap from Surface.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap from Surface. Code: ${err.code}, message: ${err.message}`);
  }
}

```

