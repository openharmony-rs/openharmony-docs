# PixelMap

```TypeScript
interface PixelMap extends ISendable
```

图像像素类，用于读取或写入图像数据以及获取图像信息，同时支持图像变换（缩放、平移、旋转、翻转、裁剪）、设置不透明度、提取Alpha通道、色彩空间设置等操作，适用于图像处理、图像编辑、图像显示等需要进行像素级数据操作的场景。在调用PixelMap的方法前，需要先通过[sendableImage.createPixelMap](arkts-image-sendableimage-createpixelmap-f.md)传入像素数据创建一个PixelMap对象。目前PixelMap序列化大小最大为128MiB，超过会渲染失败。PixelMap大小的计算方式为：宽 \* 高 \* 每像素占用字节数（详情请参考[PixelMapFormat](arkts-image-image-pixelmapformat-e.md)）。

sendableImage下的PixelMap支持Sendable属性，支持Worker线程共享。sendableImage下的PixelMap可以利用[sendableImage.convertToPixelMap](arkts-image-sendableimage-converttopixelmap-f.md)方法与image下的PixelMap进行互相转换。转换后，原对象的方法均不允许再调用，否则将报错501无法调用接口。跨线程处理PixelMap时，需要考虑多线程竞争问题。

图像占用的内存往往较大，当PixelMap对象使用完成后，应主动调用[release](#release)方法及时释放内存。释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**继承/实现关系：** PixelMap extends [ISendable](arkts-image-sendableimage-isendable-t.md)

**起始版本：** 12

<!--Device-sendableImage-interface PixelMap extends ISendable--><!--Device-sendableImage-interface PixelMap extends ISendable-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## applyColorSpace

```TypeScript
applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>
```

根据输入的目标色彩空间对图像的像素颜色进行色彩空间转换。使用Promise异步回调。

> **说明：** 
> 
> 本接口仅执行色彩空间之间的数学转换，不包含HDR到SDR的色调映射。当源图像为HDR色彩空间（传输函数为HLG或PQ，例如BT2020_HLG、BT2020_PQ、P3_HLG、P3_PQ等）且目标为SDR色彩空间 （传输函数为sRGB gamma，例如SRGB、DISPLAY_P3、DCI_P3、ADOBE_RGB_1998等）时，直接调用本接口会导致图像整体偏亮、泛白、高光细节丢失。

**起始版本：** 12

<!--Device-PixelMap-applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>--><!--Device-PixelMap-applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetColorSpace | [colorSpaceManager.ColorSpaceManager](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md) | 是 | 目标色彩空间，支持SRGB、DCI_P3、DISPLAY_P3、ADOBE_RGB_1998。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Failed to initialize the internal object. |
| [62980108](../errorcode-image.md#62980108-图片颜色转换错误) | Failed to convert the color space. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |

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

根据Alpha通道的信息，生成一个仅包含Alpha通道信息的ALPHA_8格式的PixelMap，生成的新PixelMap不可编辑，可用于阴影效果。使用Promise异步回调。

> **说明：** 
> 
> - YUV格式不支持此接口。
> - 如果原PixelMap的格式是ALPHA_F16，则新生成的PixelMap将维持ALPHA_F16格式。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](#release) 方法及时释放内存。释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-createAlphaPixelmap(): Promise<PixelMap>--><!--Device-PixelMap-createAlphaPixelmap(): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-sendableimage-pixelmap-i.md)&gt; | Promise对象，返回仅包含Alpha通道信息的ALPHA_8格式的PixelMap。 |

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

根据Alpha通道的信息，生成一个仅包含Alpha通道信息的ALPHA_8格式的PixelMap，生成的新PixelMap不可编辑，可用于阴影效果。同步返回结果。

> **说明：** 
> 
> - YUV格式不支持此接口。
> - 如果原PixelMap的格式是ALPHA_F16，则新生成的PixelMap将维持ALPHA_F16格式。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](#release) 方法及时释放内存。释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-createAlphaPixelmapSync(): PixelMap--><!--Device-PixelMap-createAlphaPixelmapSync(): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-sendableimage-pixelmap-i.md) | 成功同步返回仅包含Alpha通道信息的ALPHA_8格式的PixelMap对象，失败抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Parameter verification failed. |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

根据输入的区域信息对图片进行裁剪。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-crop(region: image.Region): Promise<void>--><!--Device-PixelMap-crop(region: image.Region): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [image.Region](arkts-image-image-region-i.md) | 是 | 裁剪的区域，包含起始坐标和宽高。取值范围不能超过图片的宽高。单位：像素（px）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

根据输入的区域信息对图片进行裁剪。同步返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-cropSync(region: image.Region): void--><!--Device-PixelMap-cropSync(region: image.Region): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | [image.Region](arkts-image-image-region-i.md) | 是 | 裁剪的区域，包含起始坐标和宽高。取值范围不能超过图片的宽高。单位：像素（px）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

根据输入的水平或垂直翻转条件对图片进行翻转。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-flip(horizontal: boolean, vertical: boolean): Promise<void>--><!--Device-PixelMap-flip(horizontal: boolean, vertical: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | true表示进行水平翻转，false表示不进行水平翻转。 |
| vertical | boolean | 是 | true表示进行垂直翻转，false表示不进行垂直翻转。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

根据输入的水平或垂直翻转条件对图片进行翻转。同步返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-flipSync(horizontal: boolean, vertical: boolean): void--><!--Device-PixelMap-flipSync(horizontal: boolean, vertical: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontal | boolean | 是 | true表示进行水平翻转，false表示不进行水平翻转。 |
| vertical | boolean | 是 | true表示进行垂直翻转，false表示不进行垂直翻转。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

获取图像每行像素的字节数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-getBytesNumberPerRow(): number--><!--Device-PixelMap-getBytesNumberPerRow(): number-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 图像像素的行字节数。单位：字节（Byte）。 |

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

获取图像的色彩空间。

**起始版本：** 12

<!--Device-PixelMap-getColorSpace(): colorSpaceManager.ColorSpaceManager--><!--Device-PixelMap-getColorSpace(): colorSpaceManager.ColorSpaceManager-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [colorSpaceManager.ColorSpaceManager](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md) | 图像色彩空间信息。如果图像不含色彩空间信息，则会抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980101](../errorcode-image.md#62980101-图片输入数据错误) | If the image data abnormal. |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | If the image data unsupport. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | If the image parameter invalid. |

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

获取图像的像素密度。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-getDensity(): number--><!--Device-PixelMap-getDensity(): number-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 图像的像素密度，单位：ppi（像素/英寸）。 |

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

获取图像像素信息。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-getImageInfo(): Promise<image.ImageInfo>--><!--Device-PixelMap-getImageInfo(): Promise<image.ImageInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[image.ImageInfo](arkts-image-image-imageinfo-i.md)&gt; | Promise对象，返回图像像素信息。 |

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

获取图像像素信息。同步返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-getImageInfoSync(): image.ImageInfo--><!--Device-PixelMap-getImageInfoSync(): image.ImageInfo-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [image.ImageInfo](arkts-image-image-imageinfo-i.md) | 图像像素信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

获取图像所有像素占用的总字节数，不包含内存对齐填充字节。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-getPixelBytesNumber(): number--><!--Device-PixelMap-getPixelBytesNumber(): number-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 图像像素的总字节数。单位：字节（Byte）。 |

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

将PixelMap序列化后写入MessageSequence。

**起始版本：** 12

<!--Device-PixelMap-marshalling(sequence: rpc.MessageSequence): void--><!--Device-PixelMap-marshalling(sequence: rpc.MessageSequence): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequence | [rpc.MessageSequence](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-messagesequence-c.md) | 是 | 新创建的MessageSequence。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. |

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

设置PixelMap的不透明度，指定的不透明度值将被应用于所有像素，不受原图不透明度的影响。使用Promise异步回调。

> **说明：** 
> 
> YUV格式的图像不支持设置不透明度。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-opacity(rate: number): Promise<void>--><!--Device-PixelMap-opacity(rate: number): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | 不透明度的值，取值范围是(0.0, 1.0]。1.0表示完全不透明，数值越接近0.0则透明度越高。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

设置PixelMap的不透明度，指定的不透明度值将被应用于所有像素，不受原图不透明度的影响。同步返回结果。

> **说明：** 
> 
> YUV格式的图像不支持设置不透明度。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-opacitySync(rate: number): void--><!--Device-PixelMap-opacitySync(rate: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | 不透明度的值，取值范围是(0.0, 1.0]。1.0表示完全不透明，数值越接近0.0则透明度越高。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

读取PixelMap指定区域内的像素数据并存入缓冲区。如果PixelMap的像素格式为YUV类型，则按照PixelMap的像素格式存入缓冲区，否则按照BGRA_8888格式存入缓冲区。使用Promise异步回调。

> **说明：** 
> 
> 可使用公式计算PositionArea需要申请的缓冲区大小。
> 
> - RGBA的区域计算公式：读取区域像素数量（Region.size {width * height}）* 4（1倍R分量 + 1倍G分量 + 1倍B分量 + 1倍A分量）
> - YUV的区域计算公式：读取区域像素数量（Region.size {width * height}）* 1.5（1倍Y分量 + 0.25倍U分量 + 0.25倍V分量）

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-readPixels(area: image.PositionArea): Promise<void>--><!--Device-PixelMap-readPixels(area: image.PositionArea): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [image.PositionArea](arkts-image-image-positionarea-i.md) | 是 | 读取的区域数据。<br>该区域由[PositionArea](arkts-image-image-positionarea-i.md).region指定，获取的像素数据会被拷贝至[PositionArea](arkts-image-image-positionarea-i.md).pixels缓冲区。如果PixelMap的像素格式为YUV类型，则获取的像素数据格式与PixelMap相同，否则会被转换为BGRA_8888格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

读取PixelMap指定区域内的像素数据并存入缓冲区。如果PixelMap的像素格式为YUV类型，则按照PixelMap的像素格式存入缓冲区，否则按照BGRA_8888格式存入缓冲区。同步返回结果。

> **说明：** 
> 
> 可使用公式计算PositionArea需要申请的缓冲区大小。
> 
> - RGBA的区域计算公式：读取区域像素数量（Region.size {width * height}）* 4（1倍R分量 + 1倍G分量 + 1倍B分量 + 1倍A分量）
> - YUV的区域计算公式：读取区域像素数量（Region.size {width * height}）* 1.5（1倍Y分量 + 0.25倍U分量 + 0.25倍V分量）

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-readPixelsSync(area: image.PositionArea): void--><!--Device-PixelMap-readPixelsSync(area: image.PositionArea): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [image.PositionArea](arkts-image-image-positionarea-i.md) | 是 | 读取的区域数据。<br>该区域由[PositionArea](arkts-image-image-positionarea-i.md).region指定，获取的像素数据会被拷贝至[PositionArea](arkts-image-image-positionarea-i.md).pixels缓冲区。如果PixelMap的像素格式为YUV类型，则获取的像素数据格式与PixelMap相同，否则会被转换为BGRA_8888格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

读取整个PixelMap的像素数据，并按照PixelMap的像素格式存入缓冲区。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-readPixelsToBuffer(dst: ArrayBuffer): Promise<void>--><!--Device-PixelMap-readPixelsToBuffer(dst: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | ArrayBuffer | 是 | 目标缓冲区，获取的像素数据会被拷贝至该缓冲区。缓冲区内像素的格式与PixelMap相同，不包含内存对齐填充字节。缓冲区的大小由[getPixelBytesNumber](#getpixelbytesnumber)接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

读取整个PixelMap的像素数据，并按照PixelMap的像素格式存入缓冲区。同步返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-readPixelsToBufferSync(dst: ArrayBuffer): void--><!--Device-PixelMap-readPixelsToBufferSync(dst: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | ArrayBuffer | 是 | 目标缓冲区，获取的像素数据会被拷贝至该缓冲区。缓冲区内像素的格式与PixelMap相同，不包含内存对齐填充字节。缓冲区的大小由[getPixelBytesNumber](#getpixelbytesnumber)接口获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

释放PixelMap对象。释放后，任何访问该对象内部数据的方法调用都会失败。使用Promise异步回调。

图片使用的内存往往较大，在PixelMap对象使用完成后，应主动调用该方法及时释放内存。

释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

> **注意：**
> 
> 释放指的是ArkTS对象释放与之关联的native对象的管理权。仅当所有管理该native对象的ArkTS对象都被释放时，native对象占用的内存才会被回收。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-release(): Promise<void>--><!--Device-PixelMap-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

根据输入的角度对图片进行旋转。使用Promise异步回调。

> **说明：** 
> 
> - YUV格式仅支持90°倍数的旋转角。
> - 图像旋转的角度取值范围：[0, 360]。超出取值范围时，根据圆周360°自动矫正。例如，-100°与260°效果相同。
> - 如果图片旋转的角度不是90的整数倍，旋转后图片的尺寸会发生改变。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-rotate(angle: number): Promise<void>--><!--Device-PixelMap-rotate(angle: number): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | 图像旋转的角度。方向为正数顺时针，负数逆时针。单位：角度（°）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

根据输入的角度对图片进行旋转。同步返回结果。

> **说明：** 
> 
> - YUV格式仅支持90°倍数的旋转角。
> - 图像旋转的角度取值范围：[0, 360]。超出取值范围时，根据圆周360°自动矫正。例如，-100°与260°效果相同。
> - 如果图片旋转的角度不是90的整数倍，旋转后图片的尺寸会发生改变。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-rotateSync(angle: number): void--><!--Device-PixelMap-rotateSync(angle: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | 图像旋转的角度。方向为正数顺时针，负数逆时针。单位：角度（°）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

根据输入的宽高缩放倍数对图片进行缩放。使用Promise异步回调。

> **说明：** 
> 
> 缩放倍数 = 缩放后的图像尺寸 / 缩放前的图像尺寸。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-scale(x: number, y: number): Promise<void>--><!--Device-PixelMap-scale(x: number, y: number): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 宽度的缩放倍数。<br>取值不能为0，建议取正数，否则会产生翻转效果。 |
| y | number | 是 | 高度的缩放倍数。<br>取值不能为0，建议取正数，否则会产生翻转效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

根据输入的宽高缩放倍数对图片进行缩放。同步返回结果。

> **说明：** 
> 
> 缩放倍数 = 缩放后的图像尺寸 / 缩放前的图像尺寸。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-scaleSync(x: number, y: number): void--><!--Device-PixelMap-scaleSync(x: number, y: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 宽度的缩放倍数。<br>取值不能为0，建议取正数，否则会产生翻转效果。 |
| y | number | 是 | 高度的缩放倍数。<br>取值不能为0，建议取正数，否则会产生翻转效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

设置图像的色彩空间。如需同时对图像的像素颜色进行色彩空间转换，请使用[applyColorSpace](#applycolorspace)。

**起始版本：** 12

<!--Device-PixelMap-setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void--><!--Device-PixelMap-setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpace | [colorSpaceManager.ColorSpaceManager](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md) | 是 | 图像色彩空间信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980111](../errorcode-image.md#62980111-图片源数据不完整) | If the operation invalid. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | If the image parameter invalid. |

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

根据输入的坐标对图片进行位置变换。使用Promise异步回调。

> **说明：** 
> 
> 平移后的图像尺寸将变为：宽度 = 原宽度 + x，高度 = 原高度 + y。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-translate(x: number, y: number): Promise<void>--><!--Device-PixelMap-translate(x: number, y: number): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 横向平移的距离。方向为正数向右，负数向左。取值范围是(-图像宽度, +∞)。单位：像素（px）。<br>取值为负数时，平移的效果等同于裁剪掉自图像左侧起的x列像素。 |
| y | number | 是 | 纵向平移的距离。方向为正数向下，负数向上。取值范围是(-图像高度, +∞)。单位：像素（px）。<br>取值为负数时，平移的效果等同于裁剪掉自图像上方起的y行像素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

根据输入的坐标对图片进行位置变换。同步返回结果。

> **说明：** 
> 
> 平移后的图像尺寸将变为：宽度 = 原宽度 + x，高度 = 原高度 + y。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-translateSync(x: number, y: number): void--><!--Device-PixelMap-translateSync(x: number, y: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 横向平移的距离。方向为正数向右，负数向左。取值范围是(-图像宽度, +∞)。单位：像素（px）。<br>取值为负数时，平移的效果等同于裁剪掉自图像左侧起的x列像素。 |
| y | number | 是 | 纵向平移的距离。方向为正数向下，负数向上。取值范围是(-图像高度, +∞)。单位：像素（px）。<br>取值为负数时，平移的效果等同于裁剪掉自图像上方起的y行像素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

从MessageSequence中反序列化并获取PixelMap。使用Promise异步回调。

> **说明：** 
> 
> 如需使用同步方式反序列化并创建PixelMap可使用[createPixelMapFromParcel](arkts-image-sendableimage-createpixelmapfromparcel-f.md)。

**起始版本：** 12

<!--Device-PixelMap-unmarshalling(sequence: rpc.MessageSequence): Promise<PixelMap>--><!--Device-PixelMap-unmarshalling(sequence: rpc.MessageSequence): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequence | [rpc.MessageSequence](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-messagesequence-c.md) | 是 | 保存有PixelMap信息的MessageSequence。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-sendableimage-pixelmap-i.md)&gt; | Promise对象，返回反序列化后的PixelMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid image parameter. |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. |
| [62980096](../errorcode-image.md#62980096-操作失败) | The operation failed. |

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

将缓冲区内的像素数据写入整个PixelMap。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-writeBufferToPixels(src: ArrayBuffer): Promise<void>--><!--Device-PixelMap-writeBufferToPixels(src: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ArrayBuffer | 是 | 源数据缓冲区，该缓冲区内的图像像素数据会被写入PixelMap。缓冲区内的像素数据必须是整个PixelMap的像素数据，且像素格式需与PixelMap相同，不包含内存对齐填充字节。缓冲区的大小可通过[getPixelBytesNumber](#getpixelbytesnumber)接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

将缓冲区内的像素数据写入整个PixelMap。同步返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-writeBufferToPixelsSync(src: ArrayBuffer): void--><!--Device-PixelMap-writeBufferToPixelsSync(src: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ArrayBuffer | 是 | 源数据缓冲区，该缓冲区内的图像像素数据会被写入PixelMap。缓冲区内的像素数据必须是整个PixelMap的像素数据，且像素格式需与PixelMap相同，不包含内存对齐填充字节。缓冲区的大小可通过[getPixelBytesNumber](#getpixelbytesnumber)接口获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

将缓冲区内的像素数据写入PixelMap的指定区域。如果PixelMap的像素格式为YUV类型，则缓冲区内的数据会按照PixelMap的像素格式解析，否则按照BGRA_8888格式解析。使用Promise异步回调。

> **说明：** 
> 
> 可使用公式计算PositionArea需要申请的缓冲区大小。
> 
> - RGBA的区域计算公式：写入区域像素数量（Region.size {width * height}）* 4（1倍R分量 + 1倍G分量 + 1倍B分量 + 1倍A分量）
> - YUV的区域计算公式：写入区域像素数量（Region.size {width * height}）* 1.5（1倍Y分量 + 0.25倍U分量 + 0.25倍V分量）

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-writePixels(area: image.PositionArea): Promise<void>--><!--Device-PixelMap-writePixels(area: image.PositionArea): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [image.PositionArea](arkts-image-image-positionarea-i.md) | 是 | 写入的区域数据。<br>该区域由[PositionArea](arkts-image-image-positionarea-i.md).region指定，[PositionArea](arkts-image-image-positionarea-i.md).pixels缓冲区内的像素数据会被写入PixelMap的该区域。如果PixelMap的像素格式为YUV类型，则缓冲区内的像素数据格式需与PixelMap相同，否则需要为BGRA_8888格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

将缓冲区内的像素数据写入PixelMap的指定区域。如果PixelMap的像素格式为YUV类型，则缓冲区内的数据会按照PixelMap的像素格式解析，否则按照BGRA_8888格式解析。同步返回结果。

> **说明：** 
> 
> 可使用公式计算PositionArea需要申请的缓冲区大小。
> 
> - RGBA的区域计算公式：写入区域像素数量（Region.size {width * height}）* 4（1倍R分量 + 1倍G分量 + 1倍B分量 + 1倍A分量）
> - YUV的区域计算公式：写入区域像素数量（Region.size {width * height}）* 1.5（1倍Y分量 + 0.25倍U分量 + 0.25倍V分量）

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-writePixelsSync(area: image.PositionArea): void--><!--Device-PixelMap-writePixelsSync(area: image.PositionArea): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | [image.PositionArea](arkts-image-image-positionarea-i.md) | 是 | 写入的区域数据。<br>该区域由[PositionArea](arkts-image-image-positionarea-i.md).region指定，[PositionArea](arkts-image-image-positionarea-i.md).pixels缓冲区内的像素数据会被写入PixelMap的该区域。如果PixelMap的像素格式为YUV类型，则缓冲区内的像素数据格式需与PixelMap相同，否则需要为BGRA_8888格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../../errorcode-universal.md#501-资源被其他线程占用访问被拒绝) | The resource is unavailable as it is occupied by another thread. |

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

图像像素是否可被编辑。true表示可被编辑，false表示不可被编辑。为false时，图像的渲染和传输性能更好。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-PixelMap-readonly isEditable: boolean--><!--Device-PixelMap-readonly isEditable: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## isStrideAlignment

```TypeScript
readonly isStrideAlignment: boolean
```

图像的行数据是否已进行内存对齐。true表示已进行内存对齐，每行数据的末尾有空白填充字节以满足对齐要求（如果数据本身已满足对齐要求，则不会有填充字节）；false表示未进行内存对齐，每行数据紧密排列，末尾无空白填充字节。

**类型：** boolean

**起始版本：** 12

<!--Device-PixelMap-readonly isStrideAlignment: boolean--><!--Device-PixelMap-readonly isStrideAlignment: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core
