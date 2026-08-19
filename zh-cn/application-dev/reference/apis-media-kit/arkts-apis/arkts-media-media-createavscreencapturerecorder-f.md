# createAVScreenCaptureRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAVScreenCaptureRecorder

```TypeScript
function createAVScreenCaptureRecorder(): Promise<AVScreenCaptureRecorder>
```

创建屏幕录制实例，使用Promise异步回调。

**起始版本：** 12

<!--Device-media-function createAVScreenCaptureRecorder(): Promise<AVScreenCaptureRecorder>--><!--Device-media-function createAVScreenCaptureRecorder(): Promise<AVScreenCaptureRecorder>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVScreenCaptureRecorder](arkts-media-multimedia-media-avscreencapturerecorder-i.md)&gt; | Promise对象，返回AVScreenCaptureRecorder实例，失败时返回null。可用于进行屏幕录制。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avScreenCaptureRecorder: media.AVScreenCaptureRecorder;
media.createAVScreenCaptureRecorder().then((captureRecorder: media.AVScreenCaptureRecorder) => {
  if (captureRecorder) {
    avScreenCaptureRecorder = captureRecorder;
    console.info('Succeeded in createAVScreenCaptureRecorder');
  } else {
    console.error('Failed to createAVScreenCaptureRecorder');
  }
}).catch((error: BusinessError) => {
  console.error(`createAVScreenCaptureRecorder catchCallback, error message:${error.message}`);
});
```


## createAVScreenCaptureRecorder

```TypeScript
function createAVScreenCaptureRecorder(): Promise<AVScreenCaptureRecorder | undefined>
```

Creates an **AVScreenCaptureRecorder** instance. This API uses a promise to return the result.

**起始版本：** 23

<!--Device-media-function createAVScreenCaptureRecorder(): Promise<AVScreenCaptureRecorder | undefined>--><!--Device-media-function createAVScreenCaptureRecorder(): Promise<AVScreenCaptureRecorder | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVScreenCaptureRecorder](arkts-media-multimedia-media-avscreencapturerecorder-i.md) \| undefined&gt; | Promise used to return the result. If the operation is successful, an **AVScreenCaptureRecorder** instance is returned; otherwise, **null** is returned. The instance can be used for screen capture. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

