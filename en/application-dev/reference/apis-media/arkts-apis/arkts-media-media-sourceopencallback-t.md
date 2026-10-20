# SourceOpenCallback

```TypeScript
type SourceOpenCallback = (request: MediaSourceLoadingRequest) => number
```

This callback function is implemented by applications to handle resource open requests and return a unique handle for the opened resource.

> **NOTE:** 
> 
> The client must return the handle immediately after processing the request.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-media-type SourceOpenCallback = (request: MediaSourceLoadingRequest) => long--><!--Device-media-type SourceOpenCallback = (request: MediaSourceLoadingRequest) => long-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [MediaSourceLoadingRequest](arkts-media-media-mediasourceloadingrequest-i.md) | Yes | Parameters for the resource open request, including detailed information about the requested resource and the data push method. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Handle for the current resource open request. A value greater than 0 means the request is successful, whereas a value less than or equal to 0 means it fails. <br> - The handle for the request object is unique. |

**Examples**

```TypeScript
import { HashMap } from '@kit.ArkTS';
import { media } from '@kit.MediaKit';

let uuid: number = 1;
let requests: HashMap<number, media.MediaSourceLoadingRequest> = new HashMap();

let sourceOpenCallback: media.SourceOpenCallback = (request: media.MediaSourceLoadingRequest) => {
  console.info(`Opening resource: ${request.url}`);
  // Open the resource and return a unique handle, ensuring the mapping between the UUID and request.
  uuid += 1;
  requests.set(uuid, request);
  return uuid;
};
```
