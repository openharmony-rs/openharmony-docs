# createAVTranscoder

## createAVTranscoder

```TypeScript
function createAVTranscoder(): Promise<AVTranscoder>
```

创建视频转码实例。使用Promise异步回调。

> **说明：**
>
> 可创建的视频转码实例不能超过2个。

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AVTranscoder&gt; | Promise对象。异步返回AVTranscoder实例，失败时返回null。可用于视频转码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

**示例：**

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

