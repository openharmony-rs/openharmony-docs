# PixelMap

Sendable PixelMap instance.

**继承/实现关系：** PixelMap extends [ISendable](arkts-image-sendableimage-isendable-t.md)

**起始版本：** 12

<!--Device-sendableImage-interface PixelMap--><!--Device-sendableImage-interface PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## applyColorSpace

```TypeScript
applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>
```

Apply color space of pixelmap, the pixels will be changed by input color space. This method uses a promise to return the result. This method is used to change color space of PixelMap. Pixel data will be changed by calling this method. If you want to set the colorspace property of PixelMap only, use method {@Link #setColorSpace(colorSpaceManager.ColorSpaceManager)}.

**起始版本：** 12

<!--Device-PixelMap-applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>--><!--Device-PixelMap-applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetColorSpace | colorSpaceManager.ColorSpaceManager | 是 | The color space for pixelmap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Failed to initialize the internal object. |
| [62980108](../errorcode-image.md#62980108-图片颜色转换错误) | Failed to convert the color space. |

**示例**

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

function applyColorSpace(pixelMap: sendableImage.PixelMap) {
  const colorSpaceName = colorSpaceManager.ColorSpace.SRGB;
  const targetColorSpace: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
  pixelMap.applyColorSpace(targetColorSpace).then(() => {
    console.info('Succeeded in applying color space.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to apply color space. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## createAlphaPixelmap

```TypeScript
createAlphaPixelmap(): Promise<PixelMap>
```

Obtains new pixelmap with alpha information. This method uses a promise to return the information.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-createAlphaPixelmap(): Promise<PixelMap>--><!--Device-PixelMap-createAlphaPixelmap(): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | A Promise instance used to return the new image pixelmap. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createAlphaPixelmap(pixelMap: sendableImage.PixelMap) {
  pixelMap.createAlphaPixelmap().then((alphaPixelMap: sendableImage.PixelMap) => {
    console.info('Succeeded in creating alpha PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## createAlphaPixelmapSync

```TypeScript
createAlphaPixelmapSync(): PixelMap
```

Obtains new pixelmap with alpha information.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-createAlphaPixelmapSync(): PixelMap--><!--Device-PixelMap-createAlphaPixelmapSync(): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | return the new image pixelmap. If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createAlphaPixelmapSync(pixelMap: sendableImage.PixelMap) {
  try {
    let alphaPixelMap: sendableImage.PixelMap = pixelMap.createAlphaPixelmapSync();
    if (alphaPixelMap == undefined) {
      console.error(`Failed to create alpha PixelMap.`);
      return;
    }
    console.info('Succeeded in creating alpha PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## crop

```TypeScript
crop(region: image.Region): Promise<void>
```

Crop the image. This method uses a promise to return the result.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-crop(region: image.Region): Promise<void>--><!--Device-PixelMap-crop(region: image.Region): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | image.Region | 是 | The region to crop. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function crop(pixelMap: sendableImage.PixelMap) {
  const region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  pixelMap.crop(region).then(() => {
    console.info('Succeeded in cropping the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## cropSync

```TypeScript
cropSync(region: image.Region): void
```

Crop the image.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-cropSync(region: image.Region): void--><!--Device-PixelMap-cropSync(region: image.Region): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | image.Region | 是 | The region to crop. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function cropSync(pixelMap: sendableImage.PixelMap) {
  const region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  try {
    pixelMap.cropSync(region);
    console.info('Succeeded in cropping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## flip

```TypeScript
flip(horizontal: boolean, vertical: boolean): Promise<void>
```

Image flipping. This method uses a promise to return the result.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-flip(horizontal: boolean, vertical: boolean): Promise<void>--><!--Device-PixelMap-flip(horizontal: boolean, vertical: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Is flip in horizontal. |
| vertical | boolean | 是 | Is flip in vertical. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function flip(pixelMap: sendableImage.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  pixelMap.flip(horizontal, vertical).then(() => {
    console.info('Succeeded in flipping the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## flipSync

```TypeScript
flipSync(horizontal: boolean, vertical: boolean): void
```

Image flipping.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-flipSync(horizontal: boolean, vertical: boolean): void--><!--Device-PixelMap-flipSync(horizontal: boolean, vertical: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Is flip in horizontal. |
| vertical | boolean | 是 | Is flip in vertical. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function flipSync(pixelMap: sendableImage.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  try {
    pixelMap.flipSync(horizontal, vertical);
    console.info('Succeeded in flipping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## getBytesNumberPerRow

```TypeScript
getBytesNumberPerRow(): number
```

Obtains the number of bytes in each line of the image pixelmap.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-getBytesNumberPerRow(): number--><!--Device-PixelMap-getBytesNumberPerRow(): number-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Number of bytes in each line. |

**示例**

```TypeScript
function getBytesNumberPerRow(pixelMap: sendableImage.PixelMap) {
  let rowBytes: number = pixelMap.getBytesNumberPerRow();
}
```

## getColorSpace

```TypeScript
getColorSpace(): colorSpaceManager.ColorSpaceManager
```

Get color space of pixelmap.

**起始版本：** 12

<!--Device-PixelMap-getColorSpace(): colorSpaceManager.ColorSpaceManager--><!--Device-PixelMap-getColorSpace(): colorSpaceManager.ColorSpaceManager-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| colorSpaceManager.ColorSpaceManager | If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | If the image parameter invalid. |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | If the image data abnormal. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | If the image data unsupport. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getColorSpace(pixelMap: sendableImage.PixelMap) {
  try {
    const csm = pixelMap.getColorSpace();
    console.info(`Succeeded in getting color space: ${csm.getColorSpaceName()}.`);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to get color space. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## getDensity

```TypeScript
getDensity(): number
```

Obtains the density of the image pixelmap.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-getDensity(): number--><!--Device-PixelMap-getDensity(): number-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | The number of density, in ppi. |

**示例**

```TypeScript
function getDensity(pixelMap: sendableImage.PixelMap) {
  let density: number = pixelMap.getDensity();
}
```

## getImageInfo

```TypeScript
getImageInfo(): Promise<image.ImageInfo>
```

Obtains pixelmap information about this image. This method uses a promise to return the information.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-getImageInfo(): Promise<image.ImageInfo>--><!--Device-PixelMap-getImageInfo(): Promise<image.ImageInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.ImageInfo&gt; | A Promise instance used to return the image pixelmap information. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function getImageInfo(pixelMap: sendableImage.PixelMap) {
  pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
    console.info(`Succeeded in obtaining information of the PixelMap with size ${imageInfo.size} and pixel format ${imageInfo.pixelFormat}.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain information of the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## getImageInfoSync

```TypeScript
getImageInfoSync(): image.ImageInfo
```

Get image information from image source.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-getImageInfoSync(): image.ImageInfo--><!--Device-PixelMap-getImageInfoSync(): image.ImageInfo-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.ImageInfo | the image information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function getImageInfoSync(pixelMap: sendableImage.PixelMap) {
  try {
    let imageInfo: image.ImageInfo = pixelMap.getImageInfoSync();
    console.info(`Succeeded in obtaining information of the PixelMap with size ${imageInfo.size} and pixel format ${imageInfo.pixelFormat}.`);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to obtain information of the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## getPixelBytesNumber

```TypeScript
getPixelBytesNumber(): number
```

Obtains the total number of bytes of the image pixelmap.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-getPixelBytesNumber(): number--><!--Device-PixelMap-getPixelBytesNumber(): number-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Total number of bytes. |

**示例**

```TypeScript
function getPixelBytesNumber(pixelMap: sendableImage.PixelMap) {
  let pixelBytesNumber: number = pixelMap.getPixelBytesNumber();
}
```

## marshalling

```TypeScript
marshalling(sequence: rpc.MessageSequence): void
```

Marshalling PixelMap and write into MessageSequence.

**起始版本：** 12

<!--Device-PixelMap-marshalling(sequence: rpc.MessageSequence): void--><!--Device-PixelMap-marshalling(sequence: rpc.MessageSequence): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequence | rpc.MessageSequence | 是 | rpc.MessageSequence parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |

**示例**

```TypeScript
// EntryAbility.ets
import { image } from '@kit.ImageKit';
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  pixelMap: sendableImage.PixelMap;
  constructor(pixelMap: sendableImage.PixelMap) {
    this.pixelMap = pixelMap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixelMap.marshalling(messageSequence);
    console.info('Marshalled the PixelMap.');
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    sendableImage.createPixelMap(new ArrayBuffer(96), {size: { height: 4, width: 6 }}).then((pixelParcel: sendableImage.PixelMap) => {
      pixelParcel.unmarshalling(messageSequence).then(async (pixelMap: sendableImage.PixelMap) => {
        this.pixelMap = pixelMap;
        pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
          console.info(`Unmarshalled information: height = ${imageInfo.size.height}, width = ${imageInfo.size.width}.`);
        });
      });
    });
    return true;
  }
}

async function marshal() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: image.PixelMapFormat.BGRA_8888,
    size: { height: 4, width: 6 },
    alphaType: image.AlphaType.UNPREMUL
  }
  let pixelMap: sendableImage.PixelMap | undefined = await sendableImage.createPixelMap(color, opts);
  if (pixelMap != undefined) {
    // 序列化。
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // 反序列化rpc获取到data。
    let seq: MySequence = new MySequence(pixelMap);
    data.readParcelable(seq);
  }
}
```

## opacity

```TypeScript
opacity(rate: number): Promise<void>
```

Set the transparent rate of pixelmap. This method uses a promise to return the result.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-opacity(rate: number): Promise<void>--><!--Device-PixelMap-opacity(rate: number): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | The value of transparent rate. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function opacity(pixelMap: sendableImage.PixelMap) {
  const rate: number = 0.5;
  pixelMap.opacity(rate).then(() => {
    console.info('Succeeded in setting opacity.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## opacitySync

```TypeScript
opacitySync(rate: number): void
```

Set the transparent rate of pixelmap.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-opacitySync(rate: number): void--><!--Device-PixelMap-opacitySync(rate: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | The value of transparent rate. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function opacitySync(pixelMap: sendableImage.PixelMap) {
  const rate: number = 0.5;
  try {
    pixelMap.opacitySync(rate);
    console.info('Succeeded in setting opacity.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## readPixels

```TypeScript
readPixels(area: image.PositionArea): Promise<void>
```

Reads image pixelmap data in an area. This method uses a promise to return the data read.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-readPixels(area: image.PositionArea): Promise<void>--><!--Device-PixelMap-readPixels(area: image.PositionArea): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | image.PositionArea | 是 | Area from which the image pixelmap data will be read. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsRGBA(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8为需要创建的像素缓冲区大小，取值为：width * height * 4。
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area).then(() => {
    console.info('Succeeded in reading the image data in the area from the specified area.');
    console.info('BGRA data: ', new Uint8Array(area.pixels));
  }).catch((err: BusinessError) => {
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}

function readPixelsYUV(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6),  // 6为需要创建的像素缓冲区大小，取值为：width * height * 1.5。
    offset: 0,
    stride: 8,
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area).then(() => {
    console.info('Succeeded in reading the image data in the area from the specified area.');
    console.info('YUV data: ', new Uint8Array(area.pixels));
  }).catch((err: BusinessError) => {
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## readPixelsSync

```TypeScript
readPixelsSync(area: image.PositionArea): void
```

Reads image pixelmap data in an area.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-readPixelsSync(area: image.PositionArea): void--><!--Device-PixelMap-readPixelsSync(area: image.PositionArea): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | image.PositionArea | 是 | Area from which the image pixelmap data will be read. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsSync(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8),
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  try {
    pixelMap.readPixelsSync(area);
    console.info('Succeeded in reading the image data from the specified area.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## readPixelsToBuffer

```TypeScript
readPixelsToBuffer(dst: ArrayBuffer): Promise<void>
```

Reads image pixelmap data and writes the data to an ArrayBuffer. This method uses a promise to return the result.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-readPixelsToBuffer(dst: ArrayBuffer): Promise<void>--><!--Device-PixelMap-readPixelsToBuffer(dst: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | ArrayBuffer | 是 | A buffer to which the image pixelmap data will be written. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToBuffer(pixelMap: sendableImage.PixelMap) {
  const readBuffer: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  pixelMap.readPixelsToBuffer(readBuffer).then(() => {
    console.info('Succeeded in reading image pixel data.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to read image pixel data. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## readPixelsToBufferSync

```TypeScript
readPixelsToBufferSync(dst: ArrayBuffer): void
```

Reads image pixelmap data and writes the data to an ArrayBuffer.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-readPixelsToBufferSync(dst: ArrayBuffer): void--><!--Device-PixelMap-readPixelsToBufferSync(dst: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | ArrayBuffer | 是 | A buffer to which the image pixelmap data will be written. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToBufferSync(pixelMap: sendableImage.PixelMap) {
  const readBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  try {
    pixelMap.readPixelsToBufferSync(readBuffer);
    console.info('Succeeded in reading image pixel data.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read image pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## release

```TypeScript
release(): Promise<void>
```

Releases this PixelMap object. This method uses a promise to return the result.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-release(): Promise<void>--><!--Device-PixelMap-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the instance release result. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function release(pixelMap: sendableImage.PixelMap) {
  pixelMap.release().then(() => {
    console.info('Succeeded in releasing the PixelMap object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to release the PixelMap object. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## rotate

```TypeScript
rotate(angle: number): Promise<void>
```

Image rotation. This method uses a promise to return the result.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-rotate(angle: number): Promise<void>--><!--Device-PixelMap-rotate(angle: number): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | The rotation angle, in degrees. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function rotate(pixelMap: sendableImage.PixelMap) {
  const angle: number = 90.0;
  pixelMap.rotate(angle).then(() => {
    console.info('Succeeded in rotating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## rotateSync

```TypeScript
rotateSync(angle: number): void
```

Image rotation.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-rotateSync(angle: number): void--><!--Device-PixelMap-rotateSync(angle: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | The rotation angle, in degrees. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function rotateSync(pixelMap: sendableImage.PixelMap) {
  const angle: number = 90.0;
  try {
    pixelMap.rotateSync(angle);
    console.info('Succeeded in rotating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## scale

```TypeScript
scale(x: number, y: number): Promise<void>
```

Image zoom in width and height. This method uses a promise to return the result.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-scale(x: number, y: number): Promise<void>--><!--Device-PixelMap-scale(x: number, y: number): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The zoom value of width. |
| y | number | 是 | The zoom value of height. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scale(pixelMap: sendableImage.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  pixelMap.scale(scaleX, scaleY).then(() => {
    console.info('Succeeded in scaling the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## scaleSync

```TypeScript
scaleSync(x: number, y: number): void
```

Image zoom in width and height.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-scaleSync(x: number, y: number): void--><!--Device-PixelMap-scaleSync(x: number, y: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The zoom value of width. |
| y | number | 是 | The zoom value of height. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scaleSync(pixelMap: sendableImage.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  try {
    pixelMap.scaleSync(scaleX, scaleY);
    console.info('Succeeded in scaling the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## setColorSpace

```TypeScript
setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void
```

Set color space of pixelmap. This method is only used to set the colorspace property of PixelMap, while all pixel data remains the same after calling this method. If you want to change colorspace for all pixels, use method {@Link #applyColorSpace(colorSpaceManager.ColorSpaceManager)}.

**起始版本：** 12

<!--Device-PixelMap-setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void--><!--Device-PixelMap-setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpace | colorSpaceManager.ColorSpaceManager | 是 | The color space for pixelmap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | If the image parameter invalid. |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | If the operation invalid. |

**示例**

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

function setColorSpace(pixelMap: sendableImage.PixelMap) {
  const colorSpaceName = colorSpaceManager.ColorSpace.SRGB;
  const csm: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
  try {
    pixelMap.setColorSpace(csm);
    console.info('Succeeded in setting color space.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set color space. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## translate

```TypeScript
translate(x: number, y: number): Promise<void>
```

Image position transformation. This method uses a promise to return the result.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-translate(x: number, y: number): Promise<void>--><!--Device-PixelMap-translate(x: number, y: number): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The position value of width, in px. |
| y | number | 是 | The position value of height, in px. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function translate(pixelMap: sendableImage.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  pixelMap.translate(translateX, translateY).then(() => {
    console.info('Succeeded in translating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## translateSync

```TypeScript
translateSync(x: number, y: number): void
```

Image position transformation.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-translateSync(x: number, y: number): void--><!--Device-PixelMap-translateSync(x: number, y: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The position value of width, in px. |
| y | number | 是 | The position value of height, in px. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function translateSync(pixelMap: sendableImage.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  try {
    pixelMap.translateSync(translateX, translateY);
    console.info('Succeeded in translating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## unmarshalling

```TypeScript
unmarshalling(sequence: rpc.MessageSequence): Promise<PixelMap>
```

Creates a PixelMap object based on MessageSequence parameter.

**起始版本：** 12

<!--Device-PixelMap-unmarshalling(sequence: rpc.MessageSequence): Promise<PixelMap>--><!--Device-PixelMap-unmarshalling(sequence: rpc.MessageSequence): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequence | rpc.MessageSequence | 是 | rpc.MessageSequence parameter. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | A Promise instance used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |

**示例**

```TypeScript
// EntryAbility.ets
import { image } from '@kit.ImageKit';
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  pixelMap: sendableImage.PixelMap;
  constructor(pixelMap: sendableImage.PixelMap) {
    this.pixelMap = pixelMap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixelMap.marshalling(messageSequence);
    console.info('Marshalled the PixelMap.');
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    sendableImage.createPixelMap(new ArrayBuffer(96), {size: { height: 4, width: 6 }}).then((pixelParcel: sendableImage.PixelMap) => {
      pixelParcel.unmarshalling(messageSequence).then(async (pixelMap: sendableImage.PixelMap) => {
        this.pixelMap = pixelMap;
        pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
          console.info(`Unmarshalled information: height = ${imageInfo.size.height}, width = ${imageInfo.size.width}.`);
        });
      });
    });
    return true;
  }
}

async function unmarshal() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: image.PixelMapFormat.BGRA_8888,
    size: { height: 4, width: 6 },
    alphaType: image.AlphaType.UNPREMUL
  }
  let pixelMap: sendableImage.PixelMap | undefined = await sendableImage.createPixelMap(color, opts);
  if (pixelMap != undefined) {
    // 序列化。
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // 反序列化rpc获取到data。
    let seq: MySequence = new MySequence(pixelMap);
    data.readParcelable(seq);
  }
}
```

## writeBufferToPixels

```TypeScript
writeBufferToPixels(src: ArrayBuffer): Promise<void>
```

Reads image data in an ArrayBuffer and writes the data to a PixelMap object. This method uses a promise to return the result.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-writeBufferToPixels(src: ArrayBuffer): Promise<void>--><!--Device-PixelMap-writeBufferToPixels(src: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ArrayBuffer | 是 | A buffer from which the image data will be read. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeBufferToPixels(pixelMap: sendableImage.PixelMap) {
  const color: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writeBufferToPixels(color).then(() => {
    console.info('Succeeded in writing data from the buffer to the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write data from the buffer to the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## writeBufferToPixelsSync

```TypeScript
writeBufferToPixelsSync(src: ArrayBuffer): void
```

Reads image data in an ArrayBuffer and writes the data to a PixelMap object.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-writeBufferToPixelsSync(src: ArrayBuffer): void--><!--Device-PixelMap-writeBufferToPixelsSync(src: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ArrayBuffer | 是 | A buffer from which the image data will be read. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeBufferToPixelsSync(pixelMap: sendableImage.PixelMap) {
  const color: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  try {
    pixelMap.writeBufferToPixelsSync(color);
    console.info('Succeeded in writing data from the buffer to the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write data from the buffer to the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## writePixels

```TypeScript
writePixels(area: image.PositionArea): Promise<void>
```

Writes image pixelmap data to the specified area. This method uses a promise to return the operation result.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-writePixels(area: image.PositionArea): Promise<void>--><!--Device-PixelMap-writePixels(area: image.PositionArea): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | image.PositionArea | 是 | Area to which the image pixelmap data will be written. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsRGBA(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8为需要创建的像素缓冲区大小，取值为：width * height * 4。
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area).then(() => {
    console.info('Succeeded in writing pixels into the specified area.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}

function writePixelsYUV(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6), // 6为需要创建的像素缓冲区大小，取值为：width * height * 1.5。
    offset: 0,
    stride: 8, // PixelMap为YUV格式时，writePixels函数不使用该变量。
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area).then(() => {
    console.info('Succeeded in writing pixels into the specified area.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## writePixelsSync

```TypeScript
writePixelsSync(area: image.PositionArea): void
```

Writes image pixelmap data to the specified area.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-writePixelsSync(area: image.PositionArea): void--><!--Device-PixelMap-writePixelsSync(area: image.PositionArea): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | image.PositionArea | 是 | Area to which the image pixelmap data will be written. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsSync(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8),
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  try {
    pixelMap.writePixelsSync(area);
    console.info('Succeeded in writing pixels into the specified area.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## isEditable

```TypeScript
readonly isEditable: boolean
```

Whether the image pixelmap can be edited.

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PixelMap-readonly isEditable: boolean--><!--Device-PixelMap-readonly isEditable: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## isStrideAlignment

```TypeScript
readonly isStrideAlignment: boolean
```

Is it stride Alignment

**类型：** boolean

**起始版本：** 12

<!--Device-PixelMap-readonly isStrideAlignment: boolean--><!--Device-PixelMap-readonly isStrideAlignment: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

