# createAVMetadataExtractor

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAVMetadataExtractor

```TypeScript
function createAVMetadataExtractor(): Promise<AVMetadataExtractor>
```

Creates an AVMetadataExtractor instance. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVMetadataExtractor](arkts-media-media-avmetadataextractor-i.md)&gt; | Promise used to return the AVMetadataExtractor instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Returned by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avMetadataExtractor: media.AVMetadataExtractor;
media.createAVMetadataExtractor().then((extractor: media.AVMetadataExtractor) => {
  if (extractor) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
  } else {
    console.error(`Failed to create AVMetadataExtractor`);
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVMetadataExtractor, error message:${error.message}`);
});
```


<a id="createavmetadataextractor-2"></a>

## createAVMetadataExtractor

```TypeScript
function createAVMetadataExtractor(callback: AsyncCallback<AVMetadataExtractor>): void
```

Creates an AVMetadataExtractor instance. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVMetadataExtractor](arkts-media-media-avmetadataextractor-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the AVMetadataExtractor instance created; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Returned by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avMetadataExtractor: media.AVMetadataExtractor;
media.createAVMetadataExtractor((error: BusinessError, extractor: media.AVMetadataExtractor) => {
  if (extractor) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
  } else {
    console.error(`Failed to create AVMetadataExtractor, error message:${error.message}`);
  }
});
```
