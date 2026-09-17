# createAVTranscoder

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAVTranscoder

```TypeScript
function createAVTranscoder(): Promise<AVTranscoder>
```

Creates an AVTranscoder instance. This API uses a promise to return the result.

> **NOTE:** 
> 
> A maximum of 2 AVTranscoder instances can be created.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVTranscoder](arkts-media-media-avtranscoder-i.md)&gt; | Promise used to return the result. If the operation is successful, an AVTranscoder instance is returned; otherwise, **null** is returned. The instance can be used for video transcoding. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by promise. |

**Examples**

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
