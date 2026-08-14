# createAVTranscoder

## createAVTranscoder

```TypeScript
function createAVTranscoder(): Promise<AVTranscoder>
```

创建视频转码实例。使用Promise异步回调。 > **说明：** > > 可创建的视频转码实例不能超过2个。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-media-function createAVTranscoder(): Promise<AVTranscoder>--><!--Device-media-function createAVTranscoder(): Promise<AVTranscoder>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVTranscoder](arkts-media-multimedia-media-avtranscoder-i.md)&gt; | Promise对象。异步返回AVTranscoder实例，失败时返回null。可用于视频转码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avTranscoder: media.AVTranscoder | undefined = undefined;
media.createAVTranscoder().then((transcoder: media.AVTranscoder) => {
  if (transcoder) {
    avTranscoder = transcoder;
    console.info('Succeeded in creating AVTranscoder');
  } else {
    console.error('Failed to create AVTranscoder');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVTranscoder, error message:${error.message}`);
});
```


## createAVTranscoder

```TypeScript
function createAVTranscoder(): Promise<AVTranscoder | undefined>
```

Creates an **AVTranscoder** instance. This API uses a promise to return the result. **NOTE：**A maximum of 2 **AVTranscoder** instances can be created.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-media-function createAVTranscoder(): Promise<AVTranscoder | undefined>--><!--Device-media-function createAVTranscoder(): Promise<AVTranscoder | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVTranscoder](arkts-media-multimedia-media-avtranscoder-i.md) \| undefined&gt; | Promise used to return the result. If the operation is successful, an **AVTranscoder** instance is returned; otherwise, **null** is returned. The instance can be used for video transcoding. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

