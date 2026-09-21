# MediaSourceLoadingRequest

```TypeScript
interface MediaSourceLoadingRequest
```

The MediaSourceLoadingRequest class defines a loading request object. Applications use this object to obtain the location of the requested resource and to interact with the player for data exchange.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Media.Core

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## finishLoading

```TypeScript
finishLoading(uuid: number, state: LoadingRequestError): void
```

Notifies the player of the current request status. After pushing all the data for a single resource, the application should send the **LOADING_ERROR_SUCCESS** state to notify the player that the resource push is complete.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uuid | number | Yes | ID for the resource handle. The source is [SourceOpenCallback](arkts-media-media-sourceopencallback-t.md). |
| state | [LoadingRequestError](arkts-media-media-loadingrequesterror-e.md) | Yes | Request status. |

**Examples**

```TypeScript
import { HashMap } from '@kit.ArkTS';

let requests: HashMap<number, media.MediaSourceLoadingRequest> = new HashMap();
let uuid = 1;

let request = requests.get(uuid);
let loadingError = media.LoadingRequestError.LOADING_ERROR_SUCCESS;
request?.finishLoading(uuid, loadingError);
```

## respondData

```TypeScript
respondData(uuid: number, offset: number, buffer: ArrayBuffer): number
```

Sends data to the player.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uuid | number | Yes | ID for the resource handle. The source is [SourceOpenCallback](arkts-media-media-sourceopencallback-t.md). |
| offset | number | Yes | Offset of the current media data relative to the start of the resource. The value cannot be less than 0. |
| buffer | ArrayBuffer | Yes | Media data sent to the player.<br>**Note:**  Do not transmit irrelevant data, as it can affect normal data parsing and playback. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of bytes received by the server.<br>- A return value less than 0 indicates failure. <br>- A return value of -2 indicates that the player no longer needs the current data, and the client should stop the current read process. <br>- A return value of -3 indicates that the player's buffer is full, and the client should wait for the next read. |

**Examples**

```TypeScript
import { HashMap } from '@kit.ArkTS';
let requests: HashMap<number, media.MediaSourceLoadingRequest> = new HashMap();
let uuid = 1;

let request = requests.get(uuid);
let offset = 0; // Offset of the current media data relative to the start of the resource.
let buf = new ArrayBuffer(0); // Data defined by the application and pushed to the player.
let num = request?.respondData(uuid, offset, buf);
```

## respondHeader

```TypeScript
respondHeader(uuid: number, header?: Record<string, string>, redirectUrl?: string): void
```

Sends response header information to the player. This API must be called before the first call to [respondData](#responddata).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uuid | number | Yes | ID for the resource handle. The source is [SourceOpenCallback](arkts-media-media-sourceopencallback-t.md). |
| header | Record&lt;string, string&gt; | No | Header information in the HTTP response. The application can intersect the header fields with the fields supported by the underlying layer for parsing or directly pass in all corresponding header information.<br> - The following fields need to be parsed by the underlying player: Transfer-Encoding, Location, Content-Type, Content-Range, Content-Encode, Accept-Ranges, and content-length. |
| redirectUrl | string | No | Redirect URL in the HTTP response. |

**Examples**

```TypeScript
import { HashMap } from '@kit.ArkTS';
let requests: HashMap<number, media.MediaSourceLoadingRequest> = new HashMap();
let uuid = 1;

// The application fills this in as needed.
let header:Record<string, string> = {
  'Transfer-Encoding':'xxx',
  'Location' : 'xxx',
  'Content-Type' : 'xxx',
  'Content-Range' : 'xxx',
  'Content-Encode' : 'xxx',
  'Accept-Ranges' : 'xxx',
  'content-length' : 'xxx'
};
let request = requests.get(uuid);
request?.respondHeader(uuid, header);
```

## header

```TypeScript
header?: Record<string, string>
```

HTTP request header. If the header exists, the application should set the header information in the HTTP request when downloading data.

**Type:** Record&lt;string, string&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.Core

## url

```TypeScript
url: string
```

Resource URL, which is the path to the resource that the application needs to open.

**Type:** string

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.Core
