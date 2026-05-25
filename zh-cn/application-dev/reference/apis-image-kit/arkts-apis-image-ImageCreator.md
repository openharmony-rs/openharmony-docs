# Interface (ImageCreator)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

ImageCreator类，作为图片的生产者，用于将图片写入到Surface中。

在调用以下方法前需要先通过[image.createImageCreator](arkts-apis-image-f.md#imagecreateimagecreator11)创建ImageCreator实例，ImageCreator不支持多线程。

由于图片占用内存较大，所以当ImageCreator实例使用完成后，应主动调用[release](#release9)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

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

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称     | 类型                         | 只读 | 可选 | 说明               |
| -------- | ---------------------------- | ---- | ---- | ------------------ |
| capacity<sup>9+</sup> | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 否   | 同时访问的图像数。该参数仅作为期望值，实际capacity由设备硬件决定。|
| format<sup>9+</sup>   | [ImageFormat](arkts-apis-image-e.md#imageformat9) | 是   | 否   | 图像格式。         |

## dequeueImage<sup>9+</sup>

dequeueImage(callback: AsyncCallback\<Image>): void

从空闲队列中获取buffer图片，用于绘制UI内容。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名        | 类型                                    | 必填 | 说明                 |
| ------------- | ---------------------------------------| ---- | -------------------- |
| callback      | AsyncCallback\<[Image](arkts-apis-image-Image.md)>  | 是   | 回调函数，当获取最新图片成功，err为undefined，data为获取到的最新图片；否则为错误对象。  |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function DequeueImage(creator : image.ImageCreator) {
  creator.dequeueImage((err: BusinessError, img: image.Image) => {
    if (err) {
      console.error(`Failed to dequeue the Image.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in dequeuing the Image.');
    }
  });
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function DequeueImageFunc(creator: image.ImageCreator): void {
  try {
    creator.dequeueImage((err: BusinessError | null, img: image.Image | undefined) => {
      if (err) {
        console.error(0x00000, 'DequeueImageFunc', 'dequeueImage failed! err:' + err);
      } else {
        console.info(0x00000, 'DequeueImageFunc', 'dequeueImage success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'DequeueImageFunc', 'DequeueImageFunc failed: ' + err);
  }
}
```

## dequeueImage<sup>9+</sup>

dequeueImage(): Promise\<Image>

从空闲队列中获取buffer图片，用于绘制UI内容。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型             | 说明           |
| --------------- | ------------- |
| Promise\<[Image](arkts-apis-image-Image.md)> | Promise对象，返回最新图片。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function DequeueImage(creator : image.ImageCreator) {
  creator.dequeueImage().then((img: image.Image) => {
    console.info('Succeeded in dequeuing the Image.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to dequeue the Image.code ${error.code},message is ${error.message}`);
  })
```

ArkTS-Sta示例：
```ts
function DequeueImageFunc(creator: image.ImageCreator): void {
  try {
    let image: image.Image = await creator.dequeueImage();
    console.info(0x00000, 'DequeueImageFunc', 'dequeueImage success!');
  } catch (err) {
    console.error(0x00000, 'DequeueImageFunc', 'DequeueImageFunc failed: ' + err);
  }
}
```

## queueImage<sup>9+</sup>

queueImage(image: Image, callback: AsyncCallback\<void>): void

将绘制好的图片放入队列。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名        | 类型                     | 必填 | 说明                 |
| ------------- | -------------------------| ---- | -------------------- |
| image     | [Image](arkts-apis-image-Image.md)                    | 是   | 绘制好的buffer图像。 |
| callback      | AsyncCallback\<void>     | 是   | 回调函数，当将图片放入队列成功，err为undefined，否则为错误对象。  |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function QueueImage(creator : image.ImageCreator) {
  creator.dequeueImage().then((img: image.Image) => {
    // 绘制图片。
    img.getComponent(4).then((component : image.Component) => {
      let bufferArr: Uint8Array = new Uint8Array(component.byteBuffer);
      for (let i = 0; i < bufferArr.length; i += 4) {
        bufferArr[i] = 0; // B
        bufferArr[i + 1] = 0; // G
        bufferArr[i + 2] = 255; // R
        bufferArr[i + 3] = 255; // A
      }
    })
    creator.queueImage(img, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to queue the Image.code ${err.code},message is ${err.message}`);
      } else {
        console.info('Succeeded in queuing the Image.');
      }
    })
  })
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function QueueImageFunc(creator: image.ImageCreator): void {
  try {
    let image: image.Image = await creator.dequeueImage(); // 从空闲队列获取Image对象用于绘制。
    creator.queueImage(image, (err: BusinessError | null) => {
      if (err) {
        console.error(0x00000, 'QueueImageFunc', 'queueImage failed! err:' + err);
      } else {
        console.info(0x00000, 'QueueImageFunc', 'queueImage success!');
      }
    }); // 将绘制完成的Image放入队列供消费者使用。
  } catch (err) {
    console.error(0x00000, 'QueueImageFunc', 'QueueImageFunc failed: ' + err);
  }
}
```

## queueImage<sup>9+</sup>

queueImage(image: Image): Promise\<void>

将绘制好的图片放入队列。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名          | 类型     | 必填 | 说明                |
| ------------- | --------| ---- | ------------------- |
| image     | [Image](arkts-apis-image-Image.md)   | 是   | 绘制好的buffer图像。 |

**返回值：**

| 类型            | 说明           |
| -------------- | ------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function QueueImage(creator : image.ImageCreator) {
  creator.dequeueImage().then((img: image.Image) => {
    // 绘制图片。
    img.getComponent(4).then((component: image.Component) => {
      let bufferArr: Uint8Array = new Uint8Array(component.byteBuffer);
      for (let i = 0; i < bufferArr.length; i += 4) {
        bufferArr[i] = 0; // B
        bufferArr[i + 1] = 0; // G
        bufferArr[i + 2] = 255; // R
        bufferArr[i + 3] = 255; // A
      }
    })
    creator.queueImage(img).then(() => {
      console.info('Succeeded in queuing the Image.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to queue the Image.code ${error.code},message is ${error.message}`);
    })
  })
```

ArkTS-Sta示例：
```ts
function QueueImageFunc(creator: image.ImageCreator): void {
  try {
    let image: image.Image = await creator.dequeueImage();
    await creator.queueImage(image);
    console.info(0x00000, 'QueueImageFunc', 'queueImage success!');
  } catch (err) {
    console.error(0x00000, 'QueueImageFunc', 'QueueImageFunc failed: ' + err);
  }
}
```

## on<sup>9+</sup>

on(type: 'imageRelease', callback: AsyncCallback\<void>): void

监听imageRelease事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onImageRelease](#onimagerelease23)。

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名        | 类型                     | 必填 | 说明                 |
| ------------- | -------------------------| ---- | -------------------- |
| type          | string                   | 是   | 监听事件类型，如'imageRelease'。 |
| callback      | AsyncCallback\<void>     | 是   | 回调函数，当监听事件触发成功，err为undefined，否则为错误对象。  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function On(creator : image.ImageCreator) {
  creator.on('imageRelease', (err: BusinessError) => {
    if (err) {
      console.error(`Failed to get the imageRelease callback.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in getting imageRelease callback.');
    }
  })
}
```
## onImageRelease<sup>23+</sup>

onImageRelease(callback: AsyncCallback\<void>): void

监听imageRelease事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on](#on9)。

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名        | 类型                     | 必填 | 说明                 |
| ------------- | -------------------------| ---- | -------------------- |
| callback      | AsyncCallback\<void>     | 是   | 回调函数，当监听事件触发成功，err为undefined，否则为错误对象。  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function OnFunc(creator: image.ImageCreator): void {
  try{
    creator.onImageRelease('imageRelease', (err: BusinessError | null) => {
      if (err) {
        console.error(0x00000, 'OnFunc', 'on failed: ' + err);
      } else {
        console.info(0x00000, 'OnFunc', 'on success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'OnFunc', 'OnFunc failed: ' + err);
  }
}
```

## off<sup>13+</sup>

off(type: 'imageRelease', callback?: AsyncCallback\<void>): void

释放buffer时，移除注册的回调函数。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offImageRelease](#offimagerelease23)。

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**ArkTS-Dyn起始版本：** 13

**参数：**

| 参数名        | 类型                     | 必填 | 说明                                         |
| ------------- | -------------------------|----|--------------------------------------------|
| type          | string                   | 是  | 监听事件类型，如'imageRelease'。                    |
| callback      | AsyncCallback\<void>     | 否  | 回调函数。当移除注册成功时，err返回null，否则为错误对象。 |
**示例：**

```ts
async function Off(creator : image.ImageCreator) {
  let callbackFunc = ()=>{
      // 实现回调函数逻辑。
  }
  creator.on('imageRelease', callbackFunc)
  creator.off('imageRelease', callbackFunc)
}
```

## offImageRelease<sup>23+</sup>

offImageRelease(callback?: AsyncCallback\<void>): void

释放buffer时，移除注册的回调函数。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off](#off13)。

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名        | 类型                     | 必填 | 说明                                         |
| ------------- | -------------------------|----|--------------------------------------------|
| callback      | AsyncCallback\<void>     | 否  | 将被移除的回调函数。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function OffFunc(creator: image.ImageCreator): void {
  try{
    creator.onImageRelease('imageRelease', (err: BusinessError | null) => {
      if (err) {
        console.error(0x00000, 'OffFunc', 'on failed: ' + err);
      } else {
        console.info(0x00000, 'OffFunc', 'on success!');
      }
    });
    // 移除注册的回调函数。
    creator.offImageRelease('imageRelease', (err: BusinessError | null) => {
      if (err) {
        console.error(0x00000, 'OffFunc', 'off failed: ' + err);
      } else {
        console.info(0x00000, 'OffFunc', 'off success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'OffFunc', 'OffFunc failed: ' + err);
  }
}
```

## release<sup>9+</sup>

release(callback: AsyncCallback\<void>): void

释放当前图像。使用callback异步回调。

由于图片占用内存较大，所以当ImageCreator实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                     | 必填 | 说明                 |
| ------------- | -------------------------| ---- | -------------------- |
| callback      | AsyncCallback\<void>     | 是   | 回调函数，当图像释放成功，err为undefined，否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(creator : image.ImageCreator) {
  creator.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the creator.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in releasing creator.');
    }
  });
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function ReleaseFunc(creator: image.ImageCreator): void {
  try {
    creator.release((err: BusinessError | null) => {
      if (err) {
        console.error(0x00000, 'ReleaseFunc', 'release failed: ' + err);
      } else {
        console.info(0x00000, 'ReleaseFunc', 'release success!');
      }
    })
  } catch (err) {
    console.error(0x00000, 'ReleaseFunc', 'ReleaseFunc failed: ' + err);
  }
}
```

## release<sup>9+</sup>

release(): Promise\<void>

释放当前图像。使用Promise异步回调。

由于图片占用内存较大，所以当ImageCreator实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型            | 说明           |
| -------------- | ------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(creator : image.ImageCreator) {
  creator.release().then(() => {
    console.info('Succeeded in releasing creator.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the creator.code ${error.code},message is ${error.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
function ReleaseFunc(creator: image.ImageCreator): void {
  try {
    await creator.release();
  } catch (err) {
    console.error(0x00000, 'ReleaseFunc', 'ReleaseFunc failed: ' + err);
  }
}
```