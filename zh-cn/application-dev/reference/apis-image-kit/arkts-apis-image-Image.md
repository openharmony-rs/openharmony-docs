# Interface (Image)

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTs-Sta。
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 9开始支持。

提供基本的图像操作，包括获取图像信息、读写图像数据。调用[readNextImage](arkts-apis-image-ImageReceiver.md#readnextimage9)和[readLatestImage](arkts-apis-image-ImageReceiver.md#readlatestimage9)接口时会返回image。

Image的属性仅支持在创建时初始化，后续无法再修改，且其属性不对图片内容产生实际影响，请以图片生产者写入的属性为准，即以向[ImageReceiver](./arkts-apis-image-ImageReceiver.md)发送图片数据的发送方实际写入的内容为准。

## 导入模块

```ts
import { image } from '@kit.ImageKit';
```

## 属性

**系统能力：** SystemCapability.Multimedia.Image.Core


| 名称     | 类型               | 只读 | 可选 | 说明                                               |
| -------- | ------------------ | ---- | ---- | -------------------------------------------------- |
| clipRect<sup>9+</sup> | [Region](arkts-apis-image-i.md#region8) | 否   | 否   | 要裁剪的图像区域。</br>**ArkTS-Dyn起始版本：** 9</br>**ArkTS-Sta起始版本：** 23 |
| size<sup>9+</sup>     | [Size](arkts-apis-image-i.md#size)      | 是   | 否   | 图像大小。如果image对象所存储的是相机预览流数据，即YUV图像数据，那么获取到的size中的宽高分别对应YUV图像的宽高； 如果image对象所存储的是相机拍照流数据，即JPEG图像，由于已经是编码后的文件，size中的宽等于JPEG文件大小，高等于1。image对象所存储的数据是预览流还是拍照流，取决于应用将receiver中的surfaceId传给相机的previewOutput还是captureOutput。相机预览与拍照最佳实践请参考[双路预览(ArkTS)](../../media/camera/camera-dual-channel-preview.md)与[拍照实现方案(ArkTS)](../../media/camera/camera-shooting-case.md)。</br>**ArkTS-Dyn起始版本：** 9</br>**ArkTS-Sta起始版本：** 23 |
| format<sup>9+</sup> | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 否   | 图像格式，参考[OH_NativeBuffer_Format](../apis-arkgraphics2d/capi-native-buffer-h.md#oh_nativebuffer_format)。</br>**ArkTS-Dyn起始版本：** 9</br>**ArkTS-Sta起始版本：** 23 |
| timestamp<sup>12+</sup> | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是      | 否   | 图像时间戳。时间戳以纳秒为单位，通常是单调递增的。时间戳的具体含义和基准取决于图像的生产者，在相机预览/拍照场景，生产者就是相机。来自不同生产者的图像的时间戳可能有不同的含义和基准，因此可能无法进行比较。如果要获取某张照片的生成时间，可以通过[getImageProperty](arkts-apis-image-ImageSource.md#getimageproperty11)接口读取相关的EXIF信息。</br>**ArkTS-Dyn起始版本：** 12</br>**ArkTS-Sta起始版本：** 23 |
| colorSpace<sup>23+</sup> | [colorSpaceManager.ColorSpace](../apis-arkgraphics2d/js-apis-colorSpaceManager.md#colorspace) | 是 | 否 | 图像色彩空间，色域枚举类型。</br>**ArkTS-Dyn起始版本：** 23</br>**ArkTS-Sta起始版本：** 23<br />**模型约束：** 此接口仅可在Stage模型下使用。|

## getComponent<sup>9+</sup>

getComponent(componentType: ComponentType, callback: AsyncCallback\<Component>): void

根据图像的组件类型从图像中获取组件缓存。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名        | 类型                                    | 必填 | 说明                 |
| ------------- | --------------------------------------- | ---- | -------------------- |
| componentType | [ComponentType](arkts-apis-image-e.md#componenttype9)        | 是   | 图像的组件类型。（目前仅支持 ComponentType:JPEG，实际返回格式由生产者决定，如相机）    |
| callback      | AsyncCallback<[Component](arkts-apis-image-i.md#component9)> | 是   | 回调函数，当返回组件缓冲区成功，err为undefined，data为获取到的组件缓冲区；否则为错误对象。  |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

img.getComponent(4, (err: BusinessError, component: image.Component) => {
  if (err) {
    console.error(`Failed to get the component.code ${err.code},message is ${err.message}`);
  } else {
    console.info('Succeeded in getting component.');
  }
})
```

ArkTS-Sta示例：
```ts
import { common } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@ohos.base';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
if (context != undefined) {
  let imageObj: image.Image | null = GetImage(context);
  if (imageObj != null) {
    GetComponentFunc(imageObj);
  } else {
    console.error(0x00000, 'GetImage', 'imageObj is null!');
  }
}

function GetImage(context: common.UIAbilityContext): image.Image | null {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let creator: image.ImageCreator = image.createImageCreator(size, image.ImageFormat.JPEG, 8);
    let imageObj: image.Image = await creator.dequeueImage();
    if (imageObj != undefined) {
      console.info(0x00000, 'GetImage', 'GetImage success!');
      return imageObj;
    } else {
      return null;
    }
  } catch (err) {
    console.error(0x00000, 'GetImage', 'GetImage failed: ' + err);
    return null;
  }
}

function GetComponentFunc(img: image.Image): void {
  try {
    img.getComponent(image.ComponentType.JPEG, (err: BusinessError | null, component: image.Component | undefined) =>{
      if (err) {
        console.error(0x00000, 'GetComponentFunc', 'getComponent failed: ' + err);
      } else {
        console.info(0x00000, 'GetComponentFunc', 'getComponent success!');
      }
    })
  } catch (err) {
    console.error(0x00000, 'GetComponentFunc', 'GetComponentFunc failed: ' + err);
  }
}
```

## getComponent<sup>9+</sup>

getComponent(componentType: ComponentType): Promise\<Component>

根据图像的组件类型从图像中获取组件缓存。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名        | 类型                             | 必填 | 说明             |
| ------------- | -------------------------------- | ---- | ---------------- |
| componentType | [ComponentType](arkts-apis-image-e.md#componenttype9) | 是   | 图像的组件类型。（目前仅支持 ComponentType:JPEG，实际返回格式由生产者决定，如相机）。 |

**返回值：**

| 类型                              | 说明                              |
| --------------------------------- | --------------------------------- |
| Promise<[Component](arkts-apis-image-i.md#component9)> | Promise对象，返回组件缓冲区。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

img.getComponent(4).then((component: image.Component) => {
  console.info('Succeeded in getting component.');
}).catch((error: BusinessError) => {
  console.error(`Failed to get the component.code ${error.code},message is ${error.message}`);
})
```

ArkTS-Sta示例：
```ts
import { common } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
if (context != undefined) {
  let imageObj: image.Image | null = GetImage(context);
  if (imageObj != null) {
    GetComponentFunc(imageObj);
  } else {
    console.error(0x00000, 'GetImage', 'imageObj is null!');
  }
}

function GetImage(context: common.UIAbilityContext): image.Image | null {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let creator: image.ImageCreator = image.createImageCreator(size, image.ImageFormat.JPEG, 8);
    let imageObj: image.Image = await creator.dequeueImage();
    if (imageObj != undefined) {
      console.info(0x00000, 'GetImage', 'GetImage success!');
      return imageObj;
    } else {
      return null;
    }
  } catch (err) {
    console.error(0x00000, 'GetImage', 'GetImage failed: ' + err);
    return null;
  }
}

function GetComponentFunc(img: image.Image): void {
  try {
    let component: image.Component = await img.getComponent(image.ComponentType.JPEG);
    console.info(0x00000, 'GetComponentFunc', 'GetComponentFunc success!');
  } catch (err) {
    console.error(0x00000, 'GetComponentFunc', 'GetComponentFunc failed: ' + err);
  }
}
```

## getBufferData<sup>23+</sup>

getBufferData(): ImageBufferData | null

从图像中获取ImageBufferData。
> **注意：**
>
> ImageBufferData中的byteBuffer是对内部缓存的浅拷贝，当Image的生命周期结束时，便不能对byteBuffer做任何操作，否则会导致未定义行为。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                              | 说明                              |
| --------------------------------- | --------------------------------- |
| [ImageBufferData](arkts-apis-image-i.md#imagebufferdata23) \| null | 获取封装图像数据缓冲区的结构体，获取不到时返回空值。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetBufferData(img : image.Image) {
  img.getBufferData().then((bufferData: image.ImageBufferData) => {
    console.info('Succeeded in getting bufferData.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get the bufferData.code ${error.code},message is ${error.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function GetBufferData(img : image.Image) {
  try {
    let bufferData = img.getBufferData()
    if (bufferData) {
      console.info('Succeeded in getting bufferData.');
    }
  } catch (err) {
    console.info('Get bufferData failed.');
  }
}
```

## getMetadata<sup>23+</sup>

getMetadata(key: HdrMetadataKey): HdrMetadataValue | null

根据HDR元数据的类型从图像中获取HDR元数据。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名        | 类型                             | 必填 | 说明             |
| ------------- | -------------------------------- | ---- | ---------------- |
| key | [HdrMetadataKey](arkts-apis-image-e.md#hdrmetadatakey12) | 是   | HDR元数据的关键字，可用于查询对应值。 |

**返回值：**

| 类型                              | 说明                              |
| --------------------------------- | --------------------------------- |
| [HdrMetadataValue](arkts-apis-image-t.md#hdrmetadatavalue12) \| null | 返回关键字对应的HDR元数据的值。如果图像没有HDR元数据，返回空值。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 7600206 | Invalid parameter.          |
| 7600302 | Memory copy failed.         |

**示例：**

ArkTS-Dyn示例：
```ts
async function GetMetadata(img : image.Image) {
  try {
    let staticMetadata = img.getMetadata(image.HdrMetadataKey.HDR_STATIC_METADATA);
    console.info(`getMetadata:${staticMetadata}`);
  } catch (err) {
    console.error('getMetadata failed' + err);
  }
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function GetMetadata(img : image.Image) {
  try {
    let staticMetadata = img.getMetadata(image.HdrMetadataKey.HDR_STATIC_METADATA);
    if (staticMetadata) {
      console.info(`GetMetadata:${staticMetadata}`);
    }
  } catch (err) {
    console.error('GetMetadata failed' + err);
  }
}
```

## release<sup>9+</sup>

release(callback: AsyncCallback\<void>): void

释放当前图像。使用callback异步回调。

在接收另一个图像前必须先释放对应资源。

ArkTS有内存回收机制，Image对象不调用release方法，内存最终也会由系统统一释放。但图片使用的内存往往较大，为尽快释放内存，建议应用在使用完成后主动调用release方法提前释放内存。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明           |
| -------- | -------------------- | ---- | -------------- |
| callback | AsyncCallback\<void> | 是   | 回调函数，当图像释放成功，err为undefined，否则为错误对象。  |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

img.release((err: BusinessError) => {
  if (err) {
    console.error(`Failed to release the image instance.code ${err.code},message is ${err.message}`);
  } else {
    console.info('Succeeded in releasing the image instance.');
  }
})
```

ArkTS-Sta示例：
```ts
import { common } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@ohos.base';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
if (context != undefined) {
  let imageObj: image.Image | null = GetImage(context);
  if (imageObj != null) {
    ReleaseFunc(imageObj);
  } else {
    console.error(0x00000, 'GetImage', 'imageObj is null!');
  }
}

function GetImage(context: common.UIAbilityContext): image.Image | null {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let creator: image.ImageCreator = image.createImageCreator(size, image.ImageFormat.JPEG, 8);
    let imageObj: image.Image = await creator.dequeueImage();
    if (imageObj != undefined) {
      console.info(0x00000, 'GetImage', 'GetImage success!');
      return imageObj;
    } else {
      return null;
    }
  } catch (err) {
    console.error(0x00000, 'GetImage', 'GetImage failed: ' + err);
    return null;
  }
}

function ReleaseFunc(img: image.Image): void {
  try {
    img.release((err: BusinessError | null) => {
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

在接收另一个图像前必须先释放对应资源。

ArkTS有内存回收机制，Image对象不调用release方法，内存最终也会由系统统一释放。但图片使用的内存往往较大，为尽快释放内存，建议应用在使用完成后主动调用release方法提前释放内存。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                  |
| -------------- | --------------------- |
| Promise\<void> |  Promise对象。无返回结果的Promise对象。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

img.release().then(() => {
  console.info('Succeeded in releasing the image instance.');
}).catch((error: BusinessError) => {
  console.error(`Failed to release the image instance.code ${error.code},message is ${error.message}`);
})
```

ArkTS-Sta示例：
```ts
import { common } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
if (context != undefined) {
  let imageObj: image.Image | null = GetImage(context);
  if (imageObj != null) {
    ReleaseFunc(imageObj);
  } else {
    console.error(0x00000, 'GetImage', 'imageObj is null!');
  }
}

function GetImage(context: common.UIAbilityContext): image.Image | null {
  let size: image.Size = { height: 8192, width: 8 };
  try {
    let creator: image.ImageCreator = image.createImageCreator(size, image.ImageFormat.JPEG, 8);
    let imageObj: image.Image = await creator.dequeueImage();
    if (imageObj != undefined) {
      console.info(0x00000, 'GetImage', 'GetImage success!');
      return imageObj;
    } else {
      return null;
    }
  } catch (err) {
    console.error(0x00000, 'GetImage', 'GetImage failed: ' + err);
    return null;
  }
}

function ReleaseFunc(img: image.Image): void {
  try {
    await img.release()
  } catch (err) {
    console.error(0x00000, 'ReleaseFunc', 'ReleaseFunc failed: ' + err);
  }
}
```
