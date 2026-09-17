# createMediaSourceWithUrl

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createMediaSourceWithUrl

```TypeScript
function createMediaSourceWithUrl(url: string, headers?: Record<string, string>): MediaSource
```

Creates a media source for streaming media to be pre-downloaded.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the media source. The following streaming media formats are supported: HLS, HTTP- FLV, DASH, and HTTPS.<br> - FD path of the local M3U8 file. |
| headers | Record&lt;string, string&gt; | No | HTTP header customized for streaming media pre-download. If this parameter is not passed, the default HTTP header of the network request is used.<br>**Since:** 13 |

**Return value:**

| Type | Description |
| --- | --- |
| [MediaSource](arkts-media-media-mediasource-i.md) | MediaSource instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. |
