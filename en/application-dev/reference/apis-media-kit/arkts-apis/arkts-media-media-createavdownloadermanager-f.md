# createAVDownloaderManager

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAVDownloaderManager

```TypeScript
function createAVDownloaderManager(): Promise<AVDownloaderManager>
```

Creates an offline download task manager instance. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-media-function createAVDownloaderManager(): Promise<AVDownloaderManager>--><!--Device-media-function createAVDownloaderManager(): Promise<AVDownloaderManager>-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVDownloaderManager](arkts-media-media-avdownloadermanager-i.md)&gt; | Promise used to return an offline download task manager instance. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test() {
  media.createAVDownloaderManager().then((downloaderManager: media.AVDownloaderManager) => {
    console.info('Succeeded in creating AVDownloaderManager');
  }).catch((error: BusinessError) => {
    console.error(`Failed to create AVDownloaderManager, error: ${error}`);
  });
}
```
