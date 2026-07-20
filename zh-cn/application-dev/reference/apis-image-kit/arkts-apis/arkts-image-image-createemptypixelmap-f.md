# createEmptyPixelMap

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

<a id="createemptypixelmap"></a>
## createEmptyPixelMap

```TypeScript
function createEmptyPixelMap(param: InitializationOptions): PixelMap
```

Creates an empty PixelMap.

The following pixel format is not supported for PixelMap creation: ASTC_4x4.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createEmptyPixelMap(param: InitializationOptions): PixelMap--><!--Device-image-function createEmptyPixelMap(param: InitializationOptions): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | 是 | Initialization options for the PixelMap.If InitializationOptions.pixelFormat is set to ASTC_4x4, it will be reset to the default value RGBA_8888. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | The new PixelMap created. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory.Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |
| [7600305](../errorcode-image.md#7600305-创建pixelmap失败) | Failed to create the PixelMap.Possible cause: Internal data is corrupted. Please check the logs for detailed information. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createEmptyPixelMap() {
  const config: image.InitializationOptions = {
    size: { width: 6, height: 4 },
    pixelFormat: image.PixelMapFormat.RGBA_1010102, // 新创建的PixelMap的像素格式。
    editable: true
  };

  try {
    const pixelMap = image.createEmptyPixelMap(config);
    console.info('Succeeded in creating the empty PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the empty PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}

```

