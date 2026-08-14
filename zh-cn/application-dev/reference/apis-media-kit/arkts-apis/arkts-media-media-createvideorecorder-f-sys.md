# createVideoRecorder（系统接口）

## createVideoRecorder

```TypeScript
function createVideoRecorder(callback: AsyncCallback<VideoRecorder>): void
```

该接口自API version 9起停止维护，建议使用AVRecorder。 创建视频录制实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-media-function createVideoRecorder(callback: AsyncCallback<VideoRecorder>): void--><!--Device-media-function createVideoRecorder(callback: AsyncCallback<VideoRecorder>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[VideoRecorder](arkts-media-multimedia-media-videorecorder-i-sys.md)&gt; | 是 | 回调函数，返回VideoRecorder实例，失败时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

## 示例

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


## createVideoRecorder

```TypeScript
function createVideoRecorder(callback: AsyncCallback<VideoRecorder | undefined>): void
```

该接口自API version 9起停止维护，建议使用AVRecorder。 创建视频录制实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-media-function createVideoRecorder(callback: AsyncCallback<VideoRecorder | undefined>): void--><!--Device-media-function createVideoRecorder(callback: AsyncCallback<VideoRecorder | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[VideoRecorder](arkts-media-multimedia-media-videorecorder-i-sys.md) \| undefined&gt; | 是 | 回调函数，返回VideoRecorder实例，失败时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |


## createVideoRecorder

```TypeScript
function createVideoRecorder(): Promise<VideoRecorder>
```

该接口自API version 9起停止维护，建议使用AVRecorder。 创建视频录制实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-media-function createVideoRecorder(): Promise<VideoRecorder>--><!--Device-media-function createVideoRecorder(): Promise<VideoRecorder>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[VideoRecorder](arkts-media-multimedia-media-videorecorder-i-sys.md)&gt; | Promise对象，返回VideoRecorder实例，失败时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

## 示例

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


## createVideoRecorder

```TypeScript
function createVideoRecorder(): Promise<VideoRecorder | undefined>
```

该接口自API version 9起停止维护，建议使用AVRecorder。 创建视频录制实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-media-function createVideoRecorder(): Promise<VideoRecorder | undefined>--><!--Device-media-function createVideoRecorder(): Promise<VideoRecorder | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[VideoRecorder](arkts-media-multimedia-media-videorecorder-i-sys.md) \| undefined&gt; | Promise对象，返回VideoRecorder实例，失败时返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

