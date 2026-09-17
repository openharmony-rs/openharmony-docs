# createAVAdsController

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAVAdsController

```TypeScript
function createAVAdsController(player: AVPlayer): Promise<AVAdsController | undefined>
```

Create an ad playback controller associated with the player instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| player | [AVPlayer](arkts-media-media-avplayer-i.md) | Yes | Created player instance. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVAdsController](arkts-media-media-avadscontroller-i.md) &#124; undefined&gt; | If success, an Controller is returned. Otherwise returns null. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | The player object corresponding to player does not exist or is invalid. |
