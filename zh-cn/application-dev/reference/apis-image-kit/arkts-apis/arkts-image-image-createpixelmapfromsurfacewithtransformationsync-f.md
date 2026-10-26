# createPixelMapFromSurfaceWithTransformationSync

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPixelMapFromSurfaceWithTransformationSync

```TypeScript
function createPixelMapFromSurfaceWithTransformationSync(surfaceId: string, transformEnabled: boolean): PixelMap
```

通过Surface的ID创建一个预览流画面的PixelMap对象。该Surface可能携带旋转或翻转的变换信息。同步返回结果。

> **说明：** 
> 
> - 在API版本23之前，如果要获取无变换效果的PixelMap，可使用 [@ohos.arkui.componentSnapshot (组件截图)](../../apis-arkui/arkts-apis/arkts-arkui-arkui-componentsnapshot.md)能力，或者使用[image.createPixelMapFromSurfaceSync](arkts-image-image-createpixelmapfromsurfacesync-f.md)截取后再调用[rotateSync](arkts-image-image-pixelmap-i.md#rotatesync)/[flipSync](arkts-image-image-pixelmap-i.md#flipsync)手动校正方向。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-image-function createPixelMapFromSurfaceWithTransformationSync(surfaceId: string, transformEnabled: boolean): PixelMap--><!--Device-image-function createPixelMapFromSurfaceWithTransformationSync(surfaceId: string, transformEnabled: boolean): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 对应Surface的ID，可通过预览组件获取，如[XComponent](../../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)组件。 |
| transformEnabled | boolean | 是 | 是否对携带变换信息的Surface预先进行逆变换来消除PixelMap的旋转或翻转效果，即是否进行方向校正。如果Surface未携带变换信息，则本参数不生效。<br>true表示进行逆变换，变换的角度与Surface携带的角度一致且方向相反，输出的PixelMap无旋转或翻转效果。<br>false表示不进行逆变换，输出的PixelMap会根据Surface中的变换信息而带有旋转或翻转效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | 返回创建的PixelMap对象，接口调用失败时会抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-获取图像数据失败) | Failed to get the data from Surface. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation, e.g. on cross-platform. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. |
| [7600305](../errorcode-image.md#7600305-创建pixelmap失败) | Failed to create the PixelMap. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromSurfaceWithTransformationSync(surfaceId: string, transformEnabled: boolean) {
  try {
    const pixelMap: image.PixelMap = image.createPixelMapFromSurfaceWithTransformationSync(surfaceId, transformEnabled);
    console.info('Succeeded in creating the PixelMap from Surface.');
  } catch (error) {
    const err = error as BusinessError;
    console.error(`Failed to create the PixelMap from Surface. Code: ${err.code}, message: ${err.message}`);
  }
}
```
