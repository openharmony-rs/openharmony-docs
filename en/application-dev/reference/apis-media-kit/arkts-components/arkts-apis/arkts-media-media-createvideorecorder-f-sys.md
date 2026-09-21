# createVideoRecorder (System API)

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createVideoRecorder

```TypeScript
function createVideoRecorder(callback: AsyncCallback<VideoRecorder>): void
```

The maintenance of this interface has been stopped since version api 9. Please use AVRecorder Creates an VideoRecorder instance.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.VideoRecorder

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[VideoRecorder](arkts-media-media-videorecorder-i-sys.md)&gt; | Yes | used to return AudioPlayer instance if the operation is successful; returns null otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by callback. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App.<br>**Applicable version:** 12 and later |

**Examples**

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

The maintenance of this interface has been stopped since version api 9. Please use AVRecorder Creates an VideoRecorder instance.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.VideoRecorder

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[VideoRecorder](arkts-media-media-videorecorder-i-sys.md)&gt; | A Promise instance used to return VideoRecorder instance if the operation is successful; returns null otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by promise. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App.<br>**Applicable version:** 12 and later |

**Examples**

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
