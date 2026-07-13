# PixelMap

Sendable PixelMap instance.

**继承/实现关系：** PixelMap extends [ISendable](arkts-image-isendable-t.md)

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## applyColorSpace

```TypeScript
applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>
```

Apply color space of pixelmap, the pixels will be changed by input color space.
This method uses a promise to return the result.

This method is used to change color space of PixelMap.
Pixel data will be changed by calling this method.
If you want to set the colorspace property of PixelMap only,
use method {@Link #setColorSpace(colorSpaceManager.ColorSpaceManager)}.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetColorSpace | colorSpaceManager.ColorSpaceManager | 是 | The color space for pixelmap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Failed to initialize the internal object. |
| [62980108](../errorcode-image.md#62980108-图片颜色转换错误) | Failed to convert the color space. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { colorSpaceManager } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

async function ApplyColorSpace(pixelMap : sendableImage.PixelMap) {
    let colorSpaceName = colorSpaceManager.ColorSpace.SRGB; // colorSpaceManager.ColorSpace该对象当前仅支持2in1/PC设备使用。
    let targetColorSpace: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
    pixelMap.applyColorSpace(targetColorSpace).then(() => {
        console.info('Succeeded in applying color space for pixelmap object.');
    }).catch((error: BusinessError) => {
        console.error(`Failed to apply color space for pixelmap object. code is ${error.code}, message is ${error.message}`); 
    })
}

```

## createAlphaPixelmap

```TypeScript
createAlphaPixelmap(): Promise<PixelMap>
```

Obtains new pixelmap with alpha information. This method uses a promise to return the information.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | A Promise instance used to return the new image pixelmap.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function CreateAlphaPixelmap(pixelMap : sendableImage.PixelMap) {
  if (pixelMap != undefined) {
    pixelMap.createAlphaPixelmap().then((alphaPixelMap: sendableImage.PixelMap) => {
      console.info('Succeeded in creating alpha pixelmap.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to create alpha pixelmap. code is ${error.code}, message is ${error.message}`);
    })
  }
}

```

## createAlphaPixelmapSync

```TypeScript
createAlphaPixelmapSync(): PixelMap
```

Obtains new pixelmap with alpha information.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | return the new image pixelmap.If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function CreateAlphaPixelmapSync(pixelMap : sendableImage.PixelMap) {
  let resPixelMap : sendableImage.PixelMap = pixelMap.createAlphaPixelmapSync();
  return resPixelMap;
}

```

## crop

```TypeScript
crop(region: image.Region): Promise<void>
```

Crop the image. This method uses a promise to return the result.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | image.Region | 是 | The region to crop. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function Crop(pixelMap : sendableImage.PixelMap) {
  let region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  if (pixelMap != undefined) {
    pixelMap.crop(region).then(() => {
      console.info('Succeeded in cropping pixelmap.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to crop pixelmap. code is ${err.code}, message is ${err.message}`);

    });
  }
}

```

## cropSync

```TypeScript
cropSync(region: image.Region): void
```

Crop the image.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | image.Region | 是 | The region to crop. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';

async function CropSync(pixelMap : sendableImage.PixelMap) {
  let region : image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  if (pixelMap != undefined) {
    pixelMap.cropSync(region);
  }
}

```

## flip

```TypeScript
flip(horizontal: boolean, vertical: boolean): Promise<void>
```

Image flipping. This method uses a promise to return the result.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Is flip in horizontal. |
| vertical | boolean | 是 | Is flip in vertical. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function Flip(pixelMap : sendableImage.PixelMap) {
  let horizontal: boolean = true;
  let vertical: boolean = false;
  if (pixelMap != undefined) {
    pixelMap.flip(horizontal, vertical).then(() => {
      console.info('Succeeded in flipping pixelmap.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to flip pixelmap. code is ${err.code}, message is ${err.message}`);

    })
  }
}

```

## flipSync

```TypeScript
flipSync(horizontal: boolean, vertical: boolean): void
```

Image flipping.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | Is flip in horizontal. |
| vertical | boolean | 是 | Is flip in vertical. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function FlipSync(pixelMap : sendableImage.PixelMap) {
  let horizontal : boolean = true;
  let vertical : boolean = false;
  if (pixelMap != undefined) {
    pixelMap.flipSync(horizontal, vertical);
  }
}

```

## getBytesNumberPerRow

```TypeScript
getBytesNumberPerRow(): number
```

Obtains the number of bytes in each line of the image pixelmap.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Number of bytes in each line. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function GetBytesNumberPerRow(pixelMap : sendableImage.PixelMap) {
  let rowCount: number = pixelMap.getBytesNumberPerRow();
}

```

## getColorSpace

```TypeScript
getColorSpace(): colorSpaceManager.ColorSpaceManager
```

Get color space of pixelmap.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| colorSpaceManager.ColorSpaceManager | If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | If the image data abnormal. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | If the image data unsupport. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | If the image parameter invalid. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function GetColorSpace(pixelMap : sendableImage.PixelMap) {
  if (pixelMap != undefined) {
    let csm = pixelMap.getColorSpace();
  }
}

```

## getDensity

```TypeScript
getDensity(): number
```

Obtains the density of the image pixelmap.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | The number of density, in ppi. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function GetDensity(pixelMap : sendableImage.PixelMap) {
  let getDensity: number = pixelMap.getDensity();
}

```

## getImageInfo

```TypeScript
getImageInfo(): Promise<image.ImageInfo>
```

Obtains pixelmap information about this image. This method uses a promise to return the information.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.ImageInfo&gt; | A Promise instance used to return the image pixelmap information.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageInfo(pixelMap : sendableImage.PixelMap) {
  if (pixelMap != undefined) {
    pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
      if (imageInfo != undefined) {
        console.info("Succeeded in obtaining the image pixel map information."+ imageInfo.size.height);
      }
    }).catch((error: BusinessError) => {
      console.error(`Failed to obtain the image pixel map information. code is ${error.code}, message is ${error.message}`);
    })
  }
}

```

## getImageInfoSync

```TypeScript
getImageInfoSync(): image.ImageInfo
```

Get image information from image source.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.ImageInfo | the image information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { sendableImage } from '@kit.ImageKit';

async function GetImageInfoSync(pixelMap : sendableImage.PixelMap) {
  if (pixelMap != undefined) {
    let imageInfo : image.ImageInfo = pixelMap.getImageInfoSync();
  }
}

```

## getPixelBytesNumber

```TypeScript
getPixelBytesNumber(): number
```

Obtains the total number of bytes of the image pixelmap.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Total number of bytes. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function GetPixelBytesNumber(pixelMap : sendableImage.PixelMap) {
  let pixelBytesNumber: number = pixelMap.getPixelBytesNumber();
}

```

## marshalling

```TypeScript
marshalling(sequence: rpc.MessageSequence): void
```

Marshalling PixelMap and write into MessageSequence.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequence | rpc.MessageSequence | 是 | rpc.MessageSequence parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. |

**示例：**

```TypeScript
// EntryAbility.ets
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  pixel_map: sendableImage.PixelMap;
  constructor(conPixelMap : sendableImage.PixelMap) {
    this.pixel_map = conPixelMap;
  }
  marshalling(messageSequence : rpc.MessageSequence) {
    this.pixel_map.marshalling(messageSequence);
    console.info('Succeeded in marshalling a PixelMap.');
    return true;
  }
  unmarshalling(messageSequence : rpc.MessageSequence) {
    sendableImage.createPixelMap(new ArrayBuffer(96), {size: { height:4, width: 6}}).then((pixelParcel: sendableImage.PixelMap) => {
      pixelParcel.unmarshalling(messageSequence).then(async (pixelMap: sendableImage.PixelMap) => {
        this.pixel_map = pixelMap;
        pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
          console.info(`Succeeded in unmarshalling a PixelMap. Height: ${imageInfo.size.height}, width: ${imageInfo.size.width}.`);
        })
      })
    });
    return true;
  }
}

async function Marshalling() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: 4,
    size: { height: 4, width: 6 },
    alphaType: 3
  }
  let pixelMap: sendableImage.PixelMap | undefined = undefined;
  await sendableImage.createPixelMap(color, opts).then((srcPixelMap: sendableImage.PixelMap) => {
    pixelMap = srcPixelMap;
  })
  if (pixelMap != undefined) {
    // 序列化。
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // 反序列化rpc获取到data。
    let ret: MySequence = new MySequence(pixelMap);
    data.readParcelable(ret);
  }
}

```

## opacity

```TypeScript
opacity(rate: number): Promise<void>
```

Set the transparent rate of pixelmap. This method uses a promise to return the result.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | The value of transparent rate. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function Opacity(pixelMap : sendableImage.PixelMap) {
  let rate: number = 0.5;
  if (pixelMap != undefined) {
    pixelMap.opacity(rate).then(() => {
      console.info('Succeeded in setting opacity.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to set opacity. code is ${err.code}, message is ${err.message}`);
    })
  }
}

```

## opacitySync

```TypeScript
opacitySync(rate: number): void
```

Set the transparent rate of pixelmap.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | The value of transparent rate. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function OpacitySync(pixelMap : sendableImage.PixelMap) {
  let rate : number = 0.5;
  if (pixelMap != undefined) {
    pixelMap.opacitySync(rate);
  }
}

```

## readPixels

```TypeScript
readPixels(area: image.PositionArea): Promise<void>
```

Reads image pixelmap data in an area. This method uses a promise to return the data read.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | image.PositionArea | 是 | Area from which the image pixelmap data will be read. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadPixels(pixelMap : sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8),
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  if (pixelMap != undefined) {
    pixelMap.readPixels(area).then(() => {
      console.info('Succeeded in reading the image data in the area.'); // 符合条件则进入。
    }).catch((error: BusinessError) => {
      console.error(`Failed to read the image data in the area. code is ${error.code}, message is ${error.message}`);// 不符合条件则进入。
    })
  }
}

```

## readPixelsSync

```TypeScript
readPixelsSync(area: image.PositionArea): void
```

Reads image pixelmap data in an area.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | image.PositionArea | 是 | Area from which the image pixelmap data will be read. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';

async function ReadPixelsSync(pixelMap : sendableImage.PixelMap) {
  const area : image.PositionArea = {
    pixels: new ArrayBuffer(8),
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  if (pixelMap != undefined) {
    pixelMap.readPixelsSync(area);
  }
}

```

## readPixelsToBuffer

```TypeScript
readPixelsToBuffer(dst: ArrayBuffer): Promise<void>
```

Reads image pixelmap data and writes the data to an ArrayBuffer. This method uses
a promise to return the result.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | ArrayBuffer | 是 | A buffer to which the image pixelmap data will be written. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sendableImage } from '@kit.ImageKit';

async function ReadPixelsToBuffer(pixelMap : sendableImage.PixelMap) {
  const readBuffer: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素buffer大小，取值为：height * width *4。
  if (pixelMap != undefined) {
    pixelMap.readPixelsToBuffer(readBuffer).then(() => {
      console.info('Succeeded in reading image pixel data.'); // 符合条件则进入。 
    }).catch((error: BusinessError) => {
      console.error(`Failed to read image pixel data. code is ${error.code}, message is ${error.message}`);// 不符合条件则进入。
    })
  }
}

```

## readPixelsToBufferSync

```TypeScript
readPixelsToBufferSync(dst: ArrayBuffer): void
```

Reads image pixelmap data and writes the data to an ArrayBuffer.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | ArrayBuffer | 是 | A buffer to which the image pixelmap data will be written. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function ReadPixelsToBufferSync(pixelMap: sendableImage.PixelMap) {
  const bufferSize = pixelMap.getPixelBytesNumber();
  const readBuffer: ArrayBuffer = new ArrayBuffer(bufferSize);
  if (pixelMap != undefined) {
    pixelMap.readPixelsToBufferSync(readBuffer);
  }
}

```

## release

```TypeScript
release(): Promise<void>
```

Releases this PixelMap object. This method uses a promise to return the result.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the instance release result.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sendableImage } from '@kit.ImageKit';

async function Release(pixelMap: sendableImage.PixelMap) {
  if (pixelMap != undefined) {
    await pixelMap.release().then(() => {
      console.info('Succeeded in releasing pixelmap object.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to release pixelmap object. code is ${error.code}, message is ${error.message}`);
    })
  }
}

```

## rotate

```TypeScript
rotate(angle: number): Promise<void>
```

Image rotation. This method uses a promise to return the result.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | The rotation angle, in degrees. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function Rotate(pixelMap : sendableImage.PixelMap) {
  let angle: number = 90.0;
  if (pixelMap != undefined) {
    pixelMap.rotate(angle).then(() => {
      console.info('Succeeded in rotating pixelmap.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to rotate pixelmap. code is ${err.code}, message is ${err.message}`);
    })
  }
}

```

## rotateSync

```TypeScript
rotateSync(angle: number): void
```

Image rotation.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | The rotation angle, in degrees. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function RotateSync(pixelMap : sendableImage.PixelMap) {
  let angle : number = 90.0;
  if (pixelMap != undefined) {
    pixelMap.rotateSync(angle);
  }
}

```

## scale

```TypeScript
scale(x: number, y: number): Promise<void>
```

Image zoom in width and height. This method uses a promise to return the result.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The zoom value of width. |
| y | number | 是 | The zoom value of height. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function Scale(pixelMap : sendableImage.PixelMap) {
  let scaleX: number = 2.0;
  let scaleY: number = 1.0;
  if (pixelMap != undefined) {
    pixelMap.scale(scaleX, scaleY).then(() => {
      console.info('Succeeded in scaling pixelmap.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to scale pixelmap. code is ${err.code}, message is ${err.message}`);

    })
  }
}

```

## scaleSync

```TypeScript
scaleSync(x: number, y: number): void
```

Image zoom in width and height.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The zoom value of width. |
| y | number | 是 | The zoom value of height. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function ScaleSync(pixelMap : sendableImage.PixelMap) {
  let scaleX: number = 2.0;
  let scaleY: number = 1.0;
  if (pixelMap != undefined) {
    pixelMap.scaleSync(scaleX, scaleY);
  }
}

```

## setColorSpace

```TypeScript
setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void
```

Set color space of pixelmap.

This method is only used to set the colorspace property of PixelMap,
while all pixel data remains the same after calling this method.
If you want to change colorspace for all pixels, use method
{@Link #applyColorSpace(colorSpaceManager.ColorSpaceManager)}.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpace | colorSpaceManager.ColorSpaceManager | 是 | The color space for pixelmap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | If the operation invalid. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | If the image parameter invalid. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { colorSpaceManager } from '@kit.ArkGraphics2D';

async function SetColorSpace(pixelMap : sendableImage.PixelMap) {
  let colorSpaceName = colorSpaceManager.ColorSpace.SRGB; // colorSpaceManager.ColorSpace该对象当前仅支持2in1/PC设备使用。
  let csm: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
  if (pixelMap != undefined) {
    pixelMap.setColorSpace(csm);
  }
}

```

## translate

```TypeScript
translate(x: number, y: number): Promise<void>
```

Image position transformation. This method uses a promise to return the result.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The position value of width, in px. |
| y | number | 是 | The position value of height, in px. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function Translate(pixelMap : sendableImage.PixelMap) {
  let translateX: number = 50.0;
  let translateY: number = 10.0;
  if (pixelMap != undefined) {
    pixelMap.translate(translateX, translateY).then(() => {
      console.info('Succeeded in translating pixelmap.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to translate pixelmap. code is ${err.code}, message is ${err.message}`);
    })
  }
}

```

## translateSync

```TypeScript
translateSync(x: number, y: number): void
```

Image position transformation.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | The position value of width, in px. |
| y | number | 是 | The position value of height, in px. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function TranslateSync(pixelMap : sendableImage.PixelMap) {
  let translateX : number = 50.0;
  let translateY : number = 10.0;
  if (pixelMap != undefined) {
    pixelMap.translateSync(translateX, translateY);
  }
}

```

## unmarshalling

```TypeScript
unmarshalling(sequence: rpc.MessageSequence): Promise<PixelMap>
```

Creates a PixelMap object based on MessageSequence parameter.

**起始版本：** 12

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
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. |

**示例：**

```TypeScript
// EntryAbility.ets
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  pixel_map: sendableImage.PixelMap;
  constructor(conPixelMap: sendableImage.PixelMap) {
    this.pixel_map = conPixelMap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixel_map.marshalling(messageSequence);
    console.info('Succeeded in marshalling a PixelMap.');
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    sendableImage.createPixelMap(new ArrayBuffer(96), {size: { height:4, width: 6}}).then((pixelParcel : sendableImage.PixelMap) => {
      pixelParcel.unmarshalling(messageSequence).then(async (pixelMap : sendableImage.PixelMap) => {
        this.pixel_map = pixelMap;
        pixelMap.getImageInfo().then((imageInfo : image.ImageInfo) => {
          console.info(`Succeeded in unmarshalling a PixelMap. Height: ${imageInfo.size.height}, width: ${imageInfo.size.width}.`);
        })
      })
    });
    return true;
  }
}

async function Unmarshalling() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: 4,
    size: { height: 4, width: 6 },
    alphaType: 3
  }
  let pixelMap: sendableImage.PixelMap | undefined = undefined;
  await sendableImage.createPixelMap(color, opts).then((srcPixelMap : sendableImage.PixelMap) => {
    pixelMap = srcPixelMap;
  })
  if (pixelMap != undefined) {
    // 序列化。
    let parcelable: MySequence = new MySequence(pixelMap);
    let data : rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // 反序列化rpc获取到data。
    let ret : MySequence = new MySequence(pixelMap);
    data.readParcelable(ret);
  }
}

```

## writeBufferToPixels

```TypeScript
writeBufferToPixels(src: ArrayBuffer): Promise<void>
```

Reads image data in an ArrayBuffer and writes the data to a PixelMap object. This method
uses a promise to return the result.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ArrayBuffer | 是 | A buffer from which the image data will be read. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function WriteBufferToPixels(pixelMap : sendableImage.PixelMap) {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素buffer大小，取值为：height * width *4。
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  if (pixelMap != undefined) {
    pixelMap.writeBufferToPixels(color).then(() => {
      console.info("Succeeded in writing data from a buffer to a PixelMap.");
    }).catch((error: BusinessError) => {
      console.error(`Failed to write data from a buffer to a PixelMap. code is ${error.code}, message is ${error.message}`);
    })
  }
}

```

## writeBufferToPixelsSync

```TypeScript
writeBufferToPixelsSync(src: ArrayBuffer): void
```

Reads image data in an ArrayBuffer and writes the data to a PixelMap object.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ArrayBuffer | 是 | A buffer from which the image data will be read. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function WriteBufferToPixelsSync(pixelMap: sendableImage.PixelMap) {
  const bufferSize = pixelMap.getPixelBytesNumber();
  const color : ArrayBuffer = new ArrayBuffer(bufferSize);
  let bufferArr : Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  if (pixelMap != undefined) {
    pixelMap.writeBufferToPixelsSync(color);
  }
}

```

## writePixels

```TypeScript
writePixels(area: image.PositionArea): Promise<void>
```

Writes image pixelmap data to the specified area. This method uses a promise to return
the operation result.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | image.PositionArea | 是 | Area to which the image pixelmap data will be written. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function WritePixels(pixelMap : sendableImage.PixelMap) {
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
  if (pixelMap != undefined) {
    pixelMap.writePixels(area).then(() => {
      console.info('Succeeded to write pixelmap into the specified area.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to write pixelmap into the specified area. code is ${error.code}, message is ${error.message}`);
    })
  }
}

```

## writePixelsSync

```TypeScript
writePixelsSync(area: image.PositionArea): void
```

Writes image pixelmap data to the specified area.

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | image.PositionArea | 是 | Area to which the image pixelmap data will be written. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-无法调用接口) | Resource Unavailable. |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';

async function WritePixelsSync(pixelMap : sendableImage.PixelMap) {
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
  if (pixelMap != undefined) {
    pixelMap.writePixelsSync(area);
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

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## isStrideAlignment

```TypeScript
readonly isStrideAlignment: boolean
```

Is it stride Alignment

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

