# createPixelMapFromSurface

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## createPixelMapFromSurface

```TypeScript
function createPixelMapFromSurface(surfaceId: string, region: image.Region): Promise<PixelMap>
```

根据Surface ID和区域信息创建一个PixelMap对象。该区域的大小由[Region](arkts-image-image-region-i.md).size指定。使用Promise异步回调。

> **说明：** 
> 
> - 当设备为折叠屏，切换折叠状态时，可能因Surface自带旋转角度导致接口创建失败。需根据Surface的旋转角度相应调整传入的宽高值，如旋转90°或270°时互换宽与高。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-sendableimage-pixelmap-i.md#release)方法及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 12

<!--Device-sendableImage-function createPixelMapFromSurface(surfaceId: string, region: image.Region): Promise<PixelMap>--><!--Device-sendableImage-function createPixelMapFromSurface(surfaceId: string, region: image.Region): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 对应Surface的ID，可通过预览组件获取，如[XComponent](../../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)组件。 |
| region | [image.Region](arkts-image-image-region-i.md) | 是 | 截取的画面区域。仅支持从画面左上角开始截取部分或整个画面，即Region中的x和y必须为0，Region.size中width和height的取值范围分别为[1, 预览流宽度]和[1, 预览流高度]。如需截取任意区域，可先获取整个画面，再使用[crop](arkts-image-sendableimage-pixelmap-i.md#crop)截取所需区域。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-sendableimage-pixelmap-i.md)&gt; | Promise对象，返回创建的PixelMap对象，接口调用失败时会抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | If the image parameter invalid. |
| [62980105](../errorcode-image.md#62980105-图片获取数据错误) | Failed to get the data. |
| [62980178](../errorcode-image.md#62980178-pixelmap创建失败) | Failed to create the PixelMap. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromSurface(surfaceId: string) {
  let region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  sendableImage.createPixelMapFromSurface(surfaceId, region).then((pixelMap: sendableImage.PixelMap) => {
    console.info('Succeeded in creating the PixelMap from Surface.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the PixelMap from Surface. Code: ${err.code}, message: ${err.message}`);
  });
}
```
