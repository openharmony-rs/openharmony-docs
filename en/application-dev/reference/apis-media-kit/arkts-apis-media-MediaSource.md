# Interface (MediaSource)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @chennotfound-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=0bd395dcbeb77e8ec46ae0213e44260f827e1500 translatedAt=2026-11-09T06:24:35.532Z pushedAt=2026-11-09T08:21:57.468Z nl=1 -->

The MediaSource class defines the media data information, which is from [createMediaSourceWithUrl](arkts-apis-media-f.md#mediacreatemediasourcewithurl12).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 12.

## Modules to Import

```ts
import { media } from '@kit.MediaKit';
```

## setMimeType<sup>12+</sup>

setMimeType(mimeType: AVMimeTypes): void

Sets the MIME type to help the player process extended media sources.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Media.Core

**Parameters**

| Name  | Type    | Mandatory| Description                |
| -------- | -------- | ---- | -------------------- |
| mimeType | [AVMimeTypes](arkts-apis-media-e.md#avmimetypes12) | Yes  | MIME type.|

## setMediaResourceLoaderDelegate<sup>18+</sup>

setMediaResourceLoaderDelegate(resourceLoader: MediaSourceLoader): void

Sets a **MediaSourceLoader** object, which is used to help the player request media data.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Multimedia.Media.Core

**Parameters**

| Name  | Type    | Mandatory| Description                |
| -------- | -------- | ---- | -------------------- |
| resourceLoader | [MediaSourceLoader](arkts-apis-media-i.md#mediasourceloader18) | Yes  | **MediaSourceLoader** object used to obtain media data for the player.|

**Example**

```ts
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

## enableOfflineCache<sup>23+</sup>

enableOfflineCache(enable: boolean): void

Sets whether to enable offline caching during video playback.

**System capability**: SystemCapability.Multimedia.Media.Core

**Parameters**

| Name  | Type    | Mandatory| Description                |
| -------- | -------- | ---- | -------------------- |
| enable | boolean | Yes  | Whether to enable offline caching during video playback. **true** to enable, and **false** otherwise.|

## getID

getID(): string

Obtains the ID of a media source.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Media.Core

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| string | ID of the media source. If the operation fails, an empty string is returned.|

## setTrackSelectionFilter

setTrackSelectionFilter(filter: TrackSelectionFilter): void

Sets the track selection filter criteria of the media source. After the user defines the track selection filter criteria of the media source, the corresponding operations are performed based on the filter criteria first when playing or downloading media source data offline.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------------------- |
| filter | [TrackSelectionFilter](arkts-apis-media-i.md#trackselectionfilter) | Yes | Track selection filter criteria for pre-downloading streaming media. |

## setRetrieveKey

setRetrieveKey(key: string): void

Sets the matching string used by the media source during retrieval. After the resource corresponding to the media source is cached locally, the media resource URL provided by the content delivery network may change when the resource is played again, causing a matching failure. This problem can be resolved by setting a matching string.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------------------- |
| key | string | Yes | Key value set for MediaSource to match in the local cache. |

## getTrackSelectionFilter

getTrackSelectionFilter(): TrackSelectionFilter | undefined

Obtains the configured track selection filter criteria.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Return value**

| Type                            | Description                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| [TrackSelectionFilter](arkts-apis-media-i.md#trackselectionfilter) \| undefined | The TrackSelectionFilter object if it exists; otherwise, undefined. |