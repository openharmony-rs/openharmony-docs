# createVideoRecorder（系统接口）

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## createVideoRecorder

```TypeScript
function createVideoRecorder(callback: AsyncCallback<VideoRecorder>): void
```

创建视频录制实例（一台设备只允许创建一个录制实例）。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[VideoRecorder](arkts-media-media-videorecorder-i-sys.md)&gt; | 是 | 回调函数，返回VideoRecorder实例，失败时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by callback. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System App.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let videoRecorder: media.VideoRecorder;
media.createVideoRecorder((error: BusinessError, video: media.VideoRecorder) => {
  if (video != null) {
    videoRecorder = video;
    console.info('video createVideoRecorder success');
  } else {
    console.error(`video createVideoRecorder fail, error message:${error.message}`);
  }
});
```


<a id="createvideorecorder-2"></a>

## createVideoRecorder

```TypeScript
function createVideoRecorder(): Promise<VideoRecorder>
```

创建视频录制实例（一台设备只允许创建一个录制实例）。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[VideoRecorder](arkts-media-media-videorecorder-i-sys.md)&gt; | Promise对象，返回VideoRecorder实例，失败时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System App.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let videoRecorder: media.VideoRecorder;
media.createVideoRecorder().then((video: media.VideoRecorder) => {
  if (video != null) {
    videoRecorder = video;
    console.info('video createVideoRecorder success');
  } else {
    console.error('video createVideoRecorder fail');
  }
}).catch((error: BusinessError) => {
  console.error(`video catchCallback, error message:${error.message}`);
});
```
