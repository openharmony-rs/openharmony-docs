# Interface (ImageReceiver)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

ImageReceiver类，用于获取组件surface id、接收最新的图片和读取下一张图片以及释放ImageReceiver实例。ImageReceiver作为图片的接收方和消费者，其参数属性实际上不会对接收到的图片产生影响。图片属性的配置应在发送方和生产者上进行，如相机预览流[createPreviewOutput](../apis-camera-kit/arkts-apis-camera-CameraManager.md#createpreviewoutput)。

在调用以下方法前需要先通过[image.createImageReceiver](arkts-apis-image-f.md#imagecreateimagereceiver11)创建ImageReceiver实例。

从API version 23开始，更推荐使用[image.createImageReceiver](arkts-apis-image-f.md#imagecreateimagereceiver23)，通过传入[ImageReceiverOptions](arkts-apis-image-i.md#imagereceiveroptions23)创建ImageReceiver实例。

由于图片占用内存较大，所以当ImageReceiver实例使用完成后，应主动调用[release](#release9)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 9开始支持。

## 导入模块

```ts
import { image } from '@kit.ImageKit';
```

## 属性

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称     | 类型                         | 只读 | 可选 | 说明               |
| -------- | ---------------------------- | ---- | ---- | ------------------ |
| size<sup>9+</sup>     | [Size](arkts-apis-image-i.md#size)  | 是   | 否   | 图片大小。该参数不会影响接收到的图片大小，实际返回大小由生产者决定，如相机。         |
| capacity<sup>9+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int  | 是   | 否   | 同时访问的图像数。该参数仅作为期望值，实际capacity由设备硬件决定。 |
| format<sup>9+</sup>   | [ImageFormat](arkts-apis-image-e.md#imageformat9) | 是   | 否   | 图像格式，取值为[ImageFormat](arkts-apis-image-e.md#imageformat9)常量（目前仅支持 ImageFormat:JPEG，实际返回格式由生产者决定，如相机）。        |

## getReceivingSurfaceId<sup>9+</sup>

getReceivingSurfaceId(callback: AsyncCallback\<string>): void

用于获取一个surface id供Camera或其他组件使用。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明                       |
| -------- | ---------------------- | ---- | -------------------------- |
| callback | AsyncCallback\<string> | 是   | 回调函数，当获取surface id成功，err为undefined，data为获取到的surface id；否则为错误对象。 |

**示例:**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetReceivingSurfaceId(receiver : image.ImageReceiver) {
  receiver.getReceivingSurfaceId((err: BusinessError, id: string) => {
    if (err) {
      console.error(`Failed to get the ReceivingSurfaceId.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in getting the ReceivingSurfaceId.');
    }
  });
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function GetReceivingSurfaceIdFunc(): void {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let receiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
    receiver.getReceivingSurfaceId((err: BusinessError | null, id: string | undefined) => {
      if (err) {
        console.error(0x00000, 'GetReceivingSurfaceIdFunc', 'getReceivingSurfaceId failed: ' + err);
      } else {
        console.info(0x00000, 'GetReceivingSurfaceIdFunc', 'getReceivingSurfaceId success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'GetReceivingSurfaceIdFunc', 'GetReceivingSurfaceIdFunc failed: ' + err);
  }
}
```

## getReceivingSurfaceId<sup>9+</sup>

getReceivingSurfaceId(): Promise\<string>

用于获取一个surface id供Camera或其他组件使用。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型             | 说明                 |
| ---------------- | -------------------- |
| Promise\<string> | Promise对象，返回surface id。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetReceivingSurfaceId(receiver : image.ImageReceiver) {
  receiver.getReceivingSurfaceId().then((id: string) => { 
    console.info('Succeeded in getting the ReceivingSurfaceId.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get the ReceivingSurfaceId.code ${error.code},message is ${error.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
async function GetReceivingSurfaceIdFunc(): Promise<void> {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let receiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
    await receiver.getReceivingSurfaceId();
    console.info(0x00000, 'GetReceivingSurfaceIdFunc', 'getReceivingSurfaceId success!');
  } catch (err) {
    console.error(0x00000, 'GetReceivingSurfaceIdFunc', 'GetReceivingSurfaceIdFunc failed: ' + err);
  }
}
```

## readLatestImage<sup>9+</sup>

readLatestImage(callback: AsyncCallback\<Image>): void

从ImageReceiver读取最新的图片。使用callback异步回调。

> **注意**：
> 此接口需要在[on](#on9)回调触发后调用，才能正常的接收到数据。且此接口返回的[Image](arkts-apis-image-Image.md)对象使用完毕后需要调用[release](arkts-apis-image-Image.md#release9)方法释放，释放后才可以继续接收新的数据。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                            | 必填 | 说明                     |
| -------- | ------------------------------- | ---- | ------------------------ |
| callback | AsyncCallback<[Image](arkts-apis-image-Image.md)> | 是   | 回调函数，当读取最新图片成功，err为undefined，data为获取到的最新图片；否则为错误对象。  |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadLatestImage(receiver : image.ImageReceiver) {
  receiver.readLatestImage((err: BusinessError, img: image.Image) => {
    if (err) {
      console.error(`Failed to read the latest Image.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in reading the latest Image.');
    }
  });
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function ReadLatestImageFunc(): void {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    // 创建imageReceiver实例。
    let receiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
    receiver.readLatestImage((err: BusinessError | null, img: image.Image | undefined) => {
      if (err) {
        console.error(0x00000, 'ReadLatestImageFunc', 'readLatestImage failed: ' + err);
      } else {
        console.info(0x00000, 'ReadLatestImageFunc', 'readLatestImage success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'ReadLatestImageFunc', 'ReadLatestImageFunc failed: ' + err);
  }
}
```

## readLatestImage<sup>9+</sup>

readLatestImage(): Promise\<Image>

从ImageReceiver读取最新的图片。使用Promise异步回调。

> **注意**：
>此接口需要在[on](#on9)回调触发后调用，才能正常的接收到数据。且此接口返回的[Image](arkts-apis-image-Image.md)对象使用完毕后需要调用[release](arkts-apis-image-Image.md#release9)方法释放，释放后才可以继续接收新的数据。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                      | 说明               |
| ------------------------- | ------------------ |
| Promise<[Image](arkts-apis-image-Image.md)> | Promise对象，返回最新图片。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadLatestImage(receiver : image.ImageReceiver) {
  receiver.readLatestImage().then((img: image.Image) => {
    console.info('Succeeded in reading the latest Image.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to read the latest Image.code ${error.code},message is ${error.message}`);
  });
}
```

ArkTS-Sta示例：
```ts
async function ReadLatestImageFunc(): Promise<void> {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let receiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
    await receiver.readLatestImage();
    console.info(0x00000, 'ReadLatestImageFunc', 'readLatestImage success!');
  } catch (err) {
    console.error(0x00000, 'ReadLatestImageFunc', 'ReadLatestImageFunc failed: ' + err);
  }
}
```

## readNextImage<sup>9+</sup>

readNextImage(callback: AsyncCallback\<Image>): void

从ImageReceiver读取下一张图片。使用callback异步回调。

> **注意**：
>此接口需要在[on](#on9)回调触发后调用，才能正常的接收到数据。且此接口返回的[Image](arkts-apis-image-Image.md)对象使用完毕后需要调用[release](arkts-apis-image-Image.md#release9)方法释放，释放后才可以继续接收新的数据。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                       |
| -------- | ------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<[Image](arkts-apis-image-Image.md)> | 是   | 回调函数，当获取下一张图片成功，err为undefined，data为获取到的下一张图片；否则为错误对象。  |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadNextImage(receiver : image.ImageReceiver) {
  receiver.readNextImage((err: BusinessError, img: image.Image) => {
    if (err) {
      console.error(`Failed to read the next Image.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in reading the next Image.');
    }
  });
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function ReadNextImageFunc(): void {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let receiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
    receiver.readNextImage((err: BusinessError | null, img: image.Image | undefined) => {
      if (err) {
        console.error(0x00000, 'ReadNextImageFunc', 'readNextImage failed: ' + err);
      } else {
        console.info(0x00000, 'ReadNextImageFunc', 'ReadNextImageFunc success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'ReadNextImageFunc', 'ReadNextImageFunc failed: ' + err);
  }
}
```

## readNextImage<sup>9+</sup>

readNextImage(): Promise\<Image>

从ImageReceiver读取下一张图片。使用Promise异步回调。

> **注意**：
>此接口需要在[on](#on9)回调触发后调用，才能正常的接收到数据。且此接口返回的[Image](arkts-apis-image-Image.md)对象使用完毕后需要调用[release](arkts-apis-image-Image.md#release9)方法释放，释放后才可以继续接收新的数据。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                      | 说明                 |
| ------------------------- | -------------------- |
| Promise<[Image](arkts-apis-image-Image.md)> | Promise对象，返回下一张图片。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadNextImage(receiver : image.ImageReceiver) {
  receiver.readNextImage().then((img: image.Image) => {
    console.info('Succeeded in reading the next Image.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to read the next Image.code ${error.code},message is ${error.message}`);
  });
}
```

ArkTS-Sta示例：
```ts
async function ReleaseFunc(): Promise<void> {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let receiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
    await receiver.release();
    console.info(0x00000, 'ReleaseFunc', 'release success!');
  } catch (err) {
    console.error(0x00000, 'ReleaseFunc', 'ReleaseFunc failed: ' + err);
  }
}
```

## on<sup>9+</sup>

on(type: 'imageArrival', callback: AsyncCallback\<void>): void

接收图片时注册回调。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onImageArrival](#onimagearrival23)。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型                 | 必填 | 说明                                                   |
| -------- | -------------------- | ---- | ------------------------------------------------------ |
| type     | string               | 是   | 注册事件的类型，固定为'imageArrival'，接收图片到达时触发。 |
| callback | AsyncCallback\<void> | 是   | 回调函数，当注册事件触发成功，err为undefined，否则为错误对象。                                        |

**示例：**

```ts
async function On(receiver : image.ImageReceiver) {
  receiver.on('imageArrival', () => {
    // 接收到图片，实现回调函数逻辑。
  });
}
```

## onImageArrival<sup>23+</sup>

onImageArrival(callback: AsyncCallback\<void>): void

接收图片时注册回调。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on](#on9)。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明                                                   |
| -------- | -------------------- | ---- | ------------------------------------------------------ |
| callback | AsyncCallback\<void> | 是   | 回调函数，当注册事件触发成功，err为undefined，否则为错误对象。                                        |

**示例：**

```ts
import { image } from '@kit.ImageKit';

function OnImageArrivalFunc(): void {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let receiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
    receiver.onImageArrival(() => {
      console.info(0x00000, 'OnFunc', 'on success!');
    });
  } catch (err) {
    console.error(0x00000, 'OnFunc', 'OnFunc failed: ' + err);
  }
}
```

## off<sup>13+</sup>

off(type: 'imageArrival', callback?: AsyncCallback\<void>): void

释放buffer时移除注册回调。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offImageArrival](#offimagearrival23)。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Dyn起始版本：** 13

**参数：**

| 参数名   | 类型                 | 必填 | 说明                                     |
| -------- | -------------------- |----|----------------------------------------|
| type     | string               | 是  | 注册事件的类型，固定为'imageArrival'，释放buffer时触发。 |
| callback | AsyncCallback\<void> | 否  | 移除的回调函数。         |

**示例：**

```ts
async function Off(receiver : image.ImageReceiver) {
  let callbackFunc = ()=>{
      // 实现回调函数逻辑。
  };
  receiver.on('imageArrival', callbackFunc);
  receiver.off('imageArrival', callbackFunc);
}
```

## offImageArrival<sup>23+</sup>

offImageArrival(callback?: AsyncCallback\<void>): void

释放buffer时移除注册回调。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off](#off13)。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明                                     |
| -------- | -------------------- |----|----------------------------------------|
| callback | AsyncCallback\<void> | 否  | 移除的回调函数。         |

**示例：**

```ts
function OffFunc(): void {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let receiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
    receiver.onImageArrival(() => {
      console.info(0x00000, 'OffFunc', 'on success!');
    });
    receiver.offImageArrival(() => {
      console.info(0x00000, 'OffFunc', 'off success!');
    });
  } catch (err) {
    console.error(0x00000, 'OffFunc', 'OffFunc failed: ' + err);
  }
}
```

## release<sup>9+</sup>

release(callback: AsyncCallback\<void>): void

释放ImageReceiver实例。使用callback异步回调。

由于图片占用内存较大，所以当ImageReceiver实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明                     |
| -------- | -------------------- | ---- | ------------------------ |
| callback | AsyncCallback\<void> | 是   | 回调函数，当释放ImageReceiver实例成功，err为undefined，否则为错误对象。  |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(receiver : image.ImageReceiver) {
  receiver.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the receiver.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in releasing the receiver.');
    }
  })
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function ReleaseFunc(): void {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let receiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
    receiver.release((err: BusinessError | null) => {
      if (err) {
        console.error(0x00000, 'ReleaseFunc', 'release failed: ' + err);
      } else {
        console.info(0x00000, 'ReleaseFunc', 'ReleaseFunc success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'ReleaseFunc', 'ReleaseFunc failed: ' + err);
  }
}
```

## release<sup>9+</sup>

release(): Promise\<void>

释放ImageReceiver实例。使用Promise异步回调。

由于图片占用内存较大，所以当ImageReceiver实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明               |
| -------------- | ------------------ |
| Promise\<void> |  Promise对象。无返回结果的Promise对象。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(receiver : image.ImageReceiver) {
  receiver.release().then(() => {
    console.info('Succeeded in releasing the receiver.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the receiver.code ${error.code},message is ${error.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
function ReleaseFunc(): void {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let receiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
    await receiver.release();
    console.info(0x00000, 'ReleaseFunc', 'release success!');
  } catch (err) {
    console.error(0x00000, 'ReleaseFunc', 'ReleaseFunc failed: ' + err);
  }
}
```