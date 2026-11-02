# createAVAdsController

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAVAdsController

```TypeScript
function createAVAdsController(player: AVPlayer): Promise<AVAdsController | undefined>
```

Creates an ad playback controller associated with a player instance. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-media-function createAVAdsController(player: AVPlayer): Promise<AVAdsController | undefined>--><!--Device-media-function createAVAdsController(player: AVPlayer): Promise<AVAdsController | undefined>-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| player | [AVPlayer](arkts-media-media-avplayer-i.md) | Yes | Player instance created. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVAdsController](arkts-media-media-avadscontroller-i.md) &#124; undefined&gt; | Promise used to return the result. An **AVAdsController** instance is returned if the operation is successful; **undefined** is returned otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | The player object corresponding to player does not exist or is invalid. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test() {
  let player: media.AVPlayer = await media.createAVPlayer();
  media.createAVAdsController(player).then((adsController: media.AVAdsController | undefined) => {
    if (adsController) {
      console.info('Succeeded in creating AVAdsController');
    } else {
      console.error('Failed to create AVAdsController');
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to create AVAdsController, error: ${error}`);
  });
}
```
