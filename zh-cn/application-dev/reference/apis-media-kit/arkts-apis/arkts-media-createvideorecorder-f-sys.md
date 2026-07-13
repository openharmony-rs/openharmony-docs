# createVideoRecorder（系统接口）

## createVideoRecorder

```TypeScript
function createVideoRecorder(callback: AsyncCallback<VideoRecorder>): void
```

The maintenance of this interface has been stopped since version api 9. Please use AVRecorder
Creates an VideoRecorder instance.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;VideoRecorder&gt; | 是 | used to return AudioPlayer instance if the operation issuccessful; returns null otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

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
function createVideoRecorder(): Promise<VideoRecorder>
```

The maintenance of this interface has been stopped since version api 9. Please use AVRecorder
Creates an VideoRecorder instance.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;VideoRecorder&gt; | A Promise instance used to return VideoRecorder instance if the operation issuccessful; returns null otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

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

