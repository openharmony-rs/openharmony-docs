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

<!--Device-media-function createMediaSourceWithDirectory(path: string): Promise< MediaSource | undefined>--><!--Device-media-function createMediaSourceWithDirectory(path: string): Promise< MediaSource | undefined>-End-->

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

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test() {
  media.createMediaSourceWithDirectory("/data/storage/el2/base/media/cache/").then((mediaSource: media.MediaSource | undefined) => {
    if (mediaSource) {
      console.info('Succeeded in creating MediaSource with directory');
    } else {
      console.error('Failed to create MediaSource with directory');
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to create MediaSource with directory, error: ${error}`);
  });
}
```
