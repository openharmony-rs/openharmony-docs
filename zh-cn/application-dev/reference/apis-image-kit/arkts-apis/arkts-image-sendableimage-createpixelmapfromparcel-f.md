# createPixelMapFromParcel

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## createPixelMapFromParcel

```TypeScript
function createPixelMapFromParcel(sequence: rpc.MessageSequence): PixelMap
```

从MessageSequence中反序列化并获取PixelMap。

> **说明：** 
> 
> 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-sendableimage-pixelmap-i.md#release)方法及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 12

<!--Device-sendableImage-function createPixelMapFromParcel(sequence: rpc.MessageSequence): PixelMap--><!--Device-sendableImage-function createPixelMapFromParcel(sequence: rpc.MessageSequence): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sequence | [rpc.MessageSequence](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-messagesequence-c.md) | 是 | 保存了PixelMap序列化数据的MessageSequence。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-sendableimage-pixelmap-i.md) | 返回创建的PixelMap对象，接口调用失败时会抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-操作失败) | Operation failed. |
| [62980097](../errorcode-image.md#62980097-pixelmap序列化传输失败) | IPC error. |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | Invalid input parameter. |
| [62980105](../errorcode-image.md#62980105-图片获取数据错误) | Failed to get the data. |
| [62980177](../errorcode-image.md#62980177-api环境异常) | Abnormal API environment. |
| [62980178](../errorcode-image.md#62980178-pixelmap创建失败) | Failed to create the PixelMap. |
| [62980179](../errorcode-image.md#62980179-缓冲区大小异常) | Abnormal buffer size. |
| [62980180](../errorcode-image.md#62980180-文件描述符映射失败) | FD mapping failed. |
| [62980246](../errorcode-image.md#62980246-读取pixelmap失败) | Failed to read the PixelMap. |

**示例**

```TypeScript
// EntryAbility.ets
import { image } from '@kit.ImageKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MySequence implements rpc.Parcelable {
  pixelMap: sendableImage.PixelMap;
  constructor(pixelMap: sendableImage.PixelMap) {
    this.pixelMap = pixelMap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixelMap.marshalling(messageSequence);
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    try {
      this.pixelMap = sendableImage.createPixelMapFromParcel(messageSequence);
    } catch (e) {
      const err = e as BusinessError;
      console.error(`Failed to create the PixelMap from parcel. Code: ${err.code}, message: ${err.message}`);
      return false;
    }
    return true;
  }
}

async function createPixelMapFromParcel() {
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
  };
  const pixelMap: sendableImage.PixelMap | undefined = await sendableImage.createPixelMap(color, opts);
  if (pixelMap != undefined) {
    // 序列化。
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // 反序列化rpc获取到data。
    let seq: MySequence = new MySequence(pixelMap);
    data.readParcelable(seq);

    // 获取到PixelMap。
    let newPixelMap = seq.pixelMap;
    if (newPixelMap != undefined) {
      console.info('Succeeded in getting the PixelMap.');
    }
  }
}
```
