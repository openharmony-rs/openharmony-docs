# createMediaSourceWithDirectory

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createMediaSourceWithDirectory

```TypeScript
function createMediaSourceWithDirectory(path: string): Promise< MediaSource | undefined>
```

Create a MediaSource object from the given directory.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Buffer path information for creating a media source. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[MediaSource](arkts-media-media-mediasource-i.md) &#124; undefined&gt; | If success, a MediaSource is returned. Otherwise returns null. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5411007](../errorcode-media.md#5411007-no-resource-available) | The directory specified by the path parameter does not exist or inaccessible. |
