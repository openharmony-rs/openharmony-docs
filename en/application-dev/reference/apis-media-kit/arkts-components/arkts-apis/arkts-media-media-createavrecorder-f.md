# createAVRecorder

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAVRecorder

```TypeScript
function createAVRecorder(callback: AsyncCallback<AVRecorder>): void
```

Creates an AVRecorder instance. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> An application can create multiple AVRecorder instances. However, because the device shares a common audio
> channel, only one instance can record audio at a time. Any attempt to create the second instance for audio
> recording fails due to audio channel conflicts.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVRecorder](arkts-media-media-avrecorder-i.md)&gt; | Yes | Callback function, which returns an **AVRecorder** instance for recording audio and video. Otherwise, **null** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let avRecorder: media.AVRecorder;

media.createAVRecorder((error: BusinessError, recorder: media.AVRecorder) => {
  if (recorder) {
    avRecorder = recorder;
    console.info('Succeeded in creating AVRecorder');
  } else {
    console.error(`Failed to create AVRecorder, error message:${error.message}`);
  }
});
```


<a id="createavrecorder-2"></a>

## createAVRecorder

```TypeScript
function createAVRecorder(): Promise<AVRecorder>
```

Creates an AVRecorder instance. This API uses a promise to return the result.

> **NOTE:** 
> 
> An application can create multiple AVRecorder instances. However, because the device shares a common audio
> channel, only one instance can record audio at a time. Any attempt to create the second instance for audio
> recording fails due to audio channel conflicts.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVRecorder](arkts-media-media-avrecorder-i.md)&gt; | Promise used to return an **AVRecorder** instance, which can be used to record audio and video. Otherwise, **null** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let avRecorder: media.AVRecorder;
media.createAVRecorder().then((recorder: media.AVRecorder) => {
  if (recorder) {
    avRecorder = recorder;
    console.info('Succeeded in creating AVRecorder');
  } else {
    console.error('Failed to create AVRecorder');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVRecorder, error message:${error.message}`);
});
```
