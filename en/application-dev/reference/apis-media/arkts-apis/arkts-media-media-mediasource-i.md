# MediaSource

```TypeScript
interface MediaSource
```

The MediaSource class defines the media data information, which is from [createMediaSourceWithUrl](arkts-media-media-createmediasourcewithurl-f.md#createmediasourcewithurl-1).

**Since:** 12

<!--Device-media-interface MediaSource--><!--Device-media-interface MediaSource-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## Modules to Import

```TypeScript
```

## enableOfflineCache

```TypeScript
enableOfflineCache(enable: boolean): void
```

Sets whether to enable offline caching during video playback.

**Since:** 23

<!--Device-MediaSource-enableOfflineCache(enable: boolean): void--><!--Device-MediaSource-enableOfflineCache(enable: boolean): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable offline caching during video playback. **true** to enable, **false** otherwise. |

## getID

```TypeScript
getID(): string
```

Gets the identifier of the media source.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MediaSource-getID(): string--><!--Device-MediaSource-getID(): string-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Identifier of the media source. Empty string means call failed. |

## getTrackSelectionFilter

```TypeScript
getTrackSelectionFilter(): TrackSelectionFilter | undefined
```

Obtains the configured audio and video feature filtering values.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-MediaSource-getTrackSelectionFilter(): TrackSelectionFilter | undefined--><!--Device-MediaSource-getTrackSelectionFilter(): TrackSelectionFilter | undefined-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Return value:**

| Type | Description |
| --- | --- |
| [TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md) &#124; undefined | If the TrackSelectionFilter object exists, the TrackSelectionFilter object is returned. Otherwise, the TrackSelectionFilter object is returned. |

## setMediaResourceLoaderDelegate

```TypeScript
setMediaResourceLoaderDelegate(resourceLoader: MediaSourceLoader): void
```

Sets a MediaSourceLoader object, which is used to help the player request media data.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-MediaSource-setMediaResourceLoaderDelegate(resourceLoader: MediaSourceLoader): void--><!--Device-MediaSource-setMediaResourceLoaderDelegate(resourceLoader: MediaSourceLoader): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceLoader | [MediaSourceLoader](arkts-media-media-mediasourceloader-i.md) | Yes | **MediaSourceLoader** object used to obtain media data for the player. |

**Examples**

```TypeScript
import { HashMap } from '@kit.ArkTS';
import { media } from '@kit.MediaKit';

let headers: Record<string, string> = {"User-Agent" : "User-Agent-Value"};
let mediaSource : media.MediaSource = media.createMediaSourceWithUrl("http://xxx",  headers);
let uuid: number = 1;
let requests: HashMap<number, media.MediaSourceLoadingRequest> = new HashMap();

let sourceOpenCallback: media.SourceOpenCallback = (request: media.MediaSourceLoadingRequest) => {
  console.info(`Opening resource: ${request.url}`);
  // Open the resource and return a unique handle, ensuring the mapping between the UUID and request.
  uuid += 1;
  requests.set(uuid, request);
  return uuid;
};

let sourceReadCallback: media.SourceReadCallback = (uuid: number, requestedOffset: number, requestedLength: number) => {
  console.info(`Reading resource with handle ${uuid}, offset: ${requestedOffset}, length: ${requestedLength}`);
  // Check whether the UUID is valid and store the read request. Avoid blocking the request while pushing data and header information.
};

let sourceCloseCallback: media.SourceCloseCallback = (uuid: number) => {
  console.info(`Closing resource with handle ${uuid}`);
  // Clear resources related to the current UUID.
  requests.remove(uuid);
};

// Implemented by applications as required.
let resourceLoader: media.MediaSourceLoader = {
  open: sourceOpenCallback,
  read: sourceReadCallback,
  close: sourceCloseCallback
};

mediaSource.setMediaResourceLoaderDelegate(resourceLoader);
```

## setMimeType

```TypeScript
setMimeType(mimeType: AVMimeTypes): void
```

Sets the MIME type to help the player process extended media sources.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MediaSource-setMimeType(mimeType: AVMimeTypes): void--><!--Device-MediaSource-setMimeType(mimeType: AVMimeTypes): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mimeType | [AVMimeTypes](arkts-media-media-avmimetypes-e.md) | Yes | MIME type. |

## setRetrieveKey

```TypeScript
setRetrieveKey(key: string): void
```

Sets the matching character string of the MediaSource during retrieval. After a resource corresponding to the MediaSource is cached to the local host, the resource is played again, The CDN path may change. As a result, the matching fails. You can set the matching character string to solve this problem.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-MediaSource-setRetrieveKey(key: string): void--><!--Device-MediaSource-setRetrieveKey(key: string): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key value set for the MediaSource to match in the loacl cache. |

## setTrackSelectionFilter

```TypeScript
setTrackSelectionFilter(filter: TrackSelectionFilter): void
```

Set the audio and video feature filtering items of the MediaSource, After the user defines the audio and video filtering items of the MediaSource, When playing or downloading MediaSource data offline, Preferentially perform a corresponding operation in the filtering feature.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-MediaSource-setTrackSelectionFilter(filter: TrackSelectionFilter): void--><!--Device-MediaSource-setTrackSelectionFilter(filter: TrackSelectionFilter): void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md) | Yes | Specifies the audio and video features of the pre-downloaded streaming media. |
