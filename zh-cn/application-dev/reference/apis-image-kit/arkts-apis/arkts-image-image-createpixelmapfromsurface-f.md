# createPixelMapFromSurface

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

<a id="createpixelmapfromsurface"></a>
## createPixelMapFromSurface

```TypeScript
function createPixelMapFromSurface(surfaceId: string, region: Region): Promise<PixelMap>
```

Creates a PixelMap object from surface id.

**起始版本：** 11

<!--Device-image-function createPixelMapFromSurface(surfaceId: string, region: Region): Promise<PixelMap>--><!--Device-image-function createPixelMapFromSurface(surfaceId: string, region: Region): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | surface id. |
| region | [Region](arkts-image-image-region-i.md) | 是 | The region to surface. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | Returns the instance if the operation is successful;Otherwise, an exception will be thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | If the image parameter invalid. |
| [62980105](../errorcode-image.md#62980105-图片获取数据错误) | Failed to get the data. |
| [62980178](../errorcode-image.md#62980178-pixelmap创建失败) | Failed to create the PixelMap. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromSurface(surfaceId: string) {
  let region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  image.createPixelMapFromSurface(surfaceId, region).then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in creating the PixelMap from Surface.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the PixelMap from Surface. Code: ${err.code}, message: ${err.message}`);
  });
} 

```


<a id="createpixelmapfromsurface-1"></a>
## createPixelMapFromSurface

```TypeScript
function createPixelMapFromSurface(surfaceId: string): Promise<PixelMap>
```

Creates a PixelMap object from surface id.

**起始版本：** 15

<!--Device-image-function createPixelMapFromSurface(surfaceId: string): Promise<PixelMap>--><!--Device-image-function createPixelMapFromSurface(surfaceId: string): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | surface id. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | Returns the instance if the operation is successful;Otherwise, an exception will be thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980105](../errorcode-image.md#62980105-图片获取数据错误) | Failed to get the data. |
| [62980178](../errorcode-image.md#62980178-pixelmap创建失败) | Failed to create the PixelMap. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromSurface(surfaceId: string) {
  image.createPixelMapFromSurface(surfaceId).then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in creating the PixelMap from Surface.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the PixelMap from Surface. Code: ${err.code}, message: ${err.message}`);
  });
} 

```

