# createPixelMapFromSurfaceSync

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

<a id="createpixelmapfromsurfacesync"></a>
## createPixelMapFromSurfaceSync

```TypeScript
function createPixelMapFromSurfaceSync(surfaceId: string, region: Region): PixelMap
```

Creates a PixelMap object from surface id.

**起始版本：** 12

<!--Device-image-function createPixelMapFromSurfaceSync(surfaceId: string, region: Region): PixelMap--><!--Device-image-function createPixelMapFromSurfaceSync(surfaceId: string, region: Region): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | surface id. |
| region | [Region](arkts-image-image-region-i.md) | 是 | The region to surface. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | Returns the instance if the operation is successful;Otherwise, an exception will be thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980105](../errorcode-image.md#62980105-图片获取数据错误) | Failed to get the data. |
| [62980178](../errorcode-image.md#62980178-pixelmap创建失败) | Failed to create the PixelMap. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromSurfaceSync(surfaceId: string) {
  let region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  try {
    let pixelMap: image.PixelMap = image.createPixelMapFromSurfaceSync(surfaceId, region);
    console.info('Succeeded in creating the PixelMap from Surface.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap from Surface. Code: ${err.code}, message: ${err.message}`);
  }
}

```


<a id="createpixelmapfromsurfacesync-1"></a>
## createPixelMapFromSurfaceSync

```TypeScript
function createPixelMapFromSurfaceSync(surfaceId: string): PixelMap
```

Creates a PixelMap object from surface id.

**起始版本：** 15

<!--Device-image-function createPixelMapFromSurfaceSync(surfaceId: string): PixelMap--><!--Device-image-function createPixelMapFromSurfaceSync(surfaceId: string): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | surface id. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | Returns the instance if the operation is successful;Otherwise, an exception will be thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980105](../errorcode-image.md#62980105-图片获取数据错误) | Failed to get the data. |
| [62980178](../errorcode-image.md#62980178-pixelmap创建失败) | Failed to create the PixelMap. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromSurfaceSync(surfaceId: string) {
  try {
    let pixelMap: image.PixelMap = image.createPixelMapFromSurfaceSync(surfaceId);
    console.info('Succeeded in creating the PixelMap from Surface.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap from Surface. Code: ${err.code}, message: ${err.message}`);
  }
}

```

