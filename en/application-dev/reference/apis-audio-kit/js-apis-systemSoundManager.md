# @ohos.multimedia.systemSoundManager (System Sound Management)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=08d7084d49954a340649ac0ffe9cc5abfa73d151 translatedAt=2026-11-10T03:14:26.061Z pushedAt=2026-11-10T04:53:08.635Z nl=1 -->

This module provides system sound management capabilities, including the definition of system sound effect types and the acquisition of system sound effect players. When you need to play system sound effects in an application to unify the use of system preset sound effects and deliver a consistent user experience, use the APIs of this module to perform related operations.

> **Note**:
>
> The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { systemSoundManager } from '@kit.AudioKit';
```

## SystemSoundType

Enumerates the system sound effect types.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name| Value| Description|
| ---- | ------ | ------- |
| PHOTO_SHUTTER | 0 | Camera shutter sound.|
| VIDEO_RECORDING_BEGIN | 1 | Video recording start sound.|
| VIDEO_RECORDING_END | 2 | Video recording end sound.|

## systemSoundManager.createSystemSoundPlayer

createSystemSoundPlayer(): Promise&lt;SystemSoundPlayer | null&gt;

Creates a **SystemSoundPlayer** object. This API uses a promise to return the result.

> **NOTE**
>
> - After calling createSystemSoundPlayer() to create a player, you must call release() to release the player resources when the player is no longer used.
> - For details about the usage and method relationships, see [SystemSoundPlayer (sound effect player)](js-apis-inner-multimedia-systemSoundPlayer.md).

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type                         | Description        |
| ----------------------------- | ------------ |
| Promise&lt;[SystemSoundPlayer](js-apis-inner-multimedia-systemSoundPlayer.md#systemsoundplayer) \| null&gt; | System sound player object used to play system sound effects such as the camera shutter sound and video recording sound if the operation is successful; null otherwise. |

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID| Error Message                      |
| -------- | ------------------------------ |
| 5400101  | No memory. Return by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let systemSoundPlayer: systemSoundManager.SystemSoundPlayer | null = null;

systemSoundManager.createSystemSoundPlayer().then((systemSoundPlayerInstance) => {
  systemSoundPlayer = systemSoundPlayerInstance;
  console.info('Succeeded in creating the system sound player.');
}).catch((err: BusinessError) => {
  console.error(`Failed to create the system sound player. Code: ${err.code}, message: ${err.message}`);
});
```

## SystemSoundPlayer

type SystemSoundPlayer = _SystemSoundPlayer

System sound effect player object, used to play system sound effects such as the camera shutter sound and the video recording sound.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Type             | Description       |
|-----------------|-----------|
| [_SystemSoundPlayer](js-apis-inner-multimedia-systemSoundPlayer.md#systemsoundplayer) | System sound effect player object.|