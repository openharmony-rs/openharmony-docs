# Interface (MediaAssetProgressHandler)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=be269217f26d60860ab36c5c04ebfa42dad4f573 translatedAt=2026-11-10T03:50:33.692Z pushedAt=2026-11-10T07:12:27.418Z nl=1 -->

The **MediaAssetProgressHandler** interface is used to obtain the media asset processing progress.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 15.

## Modules to Import

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## onProgress<sup>15+</sup>

onProgress(progress: number): void

Called when the progress of the requested media asset is returned.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name | Type   | Mandatory| Description                      |
| ------- | ------- | ---- | -------------------------- |
| progress | number | Yes  | Progress in percentage. The Value range is [0, 100].|

**Example**

For details about how to create a **phAccessHelper** instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { dataSharePredicates } from '@kit.ArkData';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function requestVideoWithProgress(
  phAccessHelper: photoAccessHelper.PhotoAccessHelper,
  context: common.Context
) {
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> | null = null;
  try {
    // Query a video resource.
    const predicates = new dataSharePredicates.DataSharePredicates();
    predicates.equalTo(photoAccessHelper.PhotoKeys.PHOTO_TYPE, photoAccessHelper.PhotoType.VIDEO);
    predicates.limit(1, 0);

    const fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: ['title', 'size', 'subtype'],
      predicates: predicates,
    };

    fetchResult = await phAccessHelper.getAssets(fetchOptions);
    const asset = await fetchResult.getFirstObject();

    // Progress handler, valid only in API version 15 and later.
    const progressHandler: photoAccessHelper.MediaAssetProgressHandler = {
      onProgress: (progress: number) => {
        console.info(`Video request progress: ${progress}%`);
      },
    };

    const requestOptions: photoAccessHelper.RequestOptions = {
      deliveryMode: photoAccessHelper.DeliveryMode.FAST_MODE,
      compatibleMode: photoAccessHelper.CompatibleMode.COMPATIBLE_FORMAT_MODE,
      mediaAssetProgressHandler: progressHandler,
    };

    const destUri = `${context.cacheDir}/output.mp4`;

    const dataHandler: photoAccessHelper.MediaAssetDataHandler<boolean> = {
      onDataPrepared: (data: boolean | undefined) => {
        console.info(`Video data preparation completed: ${data}`);
      },
    };

    const taskId = await photoAccessHelper.MediaAssetManager.requestVideoFile(
      context, asset, requestOptions, destUri, dataHandler
    );
    console.info(`requestVideoFile taskId: ${taskId}`);
  } catch (err) {
    const error = err as BusinessError;
    console.error(`requestVideoFile failed: ${error.code}, ${error.message}`);
  } finally {
    if (fetchResult !== null) {
      fetchResult.close();
    }
  }
}
```