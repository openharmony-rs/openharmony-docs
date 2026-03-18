# @ohos.multimedia.systemSoundManager (System Sound Management)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

This module provides basic capabilities for managing system sound effects, including defining system sound effect types and obtaining system sound effect players.

> **NOTE**
>
> The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { systemSoundManager } from '@kit.AudioKit';
```

## SystemSoundType

Enumerates the system sound effect types.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name| Value| Description|
| ---- | ------ | ------- |
| PHOTO_SHUTTER | 0 | Camera shutter sound.|
| VIDEO_RECORDING_BEGIN | 1 | Video recording start sound.|
| VIDEO_RECORDING_END | 2 | Video recording end sound.|

## systemSoundManager.createSystemSoundPlayer

createSystemSoundPlayer(): Promise&lt;SystemSoundPlayer | null&gt;

Creates a **SystemSoundPlayer** object. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type                         | Description        |
| ----------------------------- | ------------ |
| Promise&lt;[SystemSoundPlayer](js-apis-inner-multimedia-systemSoundPlayer.md#systemsoundplayer) \| null&gt; | Returns the **SystemSoundPlayer** object on success, null on failure.|

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
  console.info('Succeeded in creating the system sound player.');
  systemSoundPlayer = systemSoundPlayerInstance;
}).catch((err: BusinessError) => {
  console.error(`Failed to create the system sound player. Code: ${err.code}, message: ${err.message}`);
});
```

## SystemSoundPlayer

type SystemSoundPlayer = _SystemSoundPlayer

Represents the system sound effect player object.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Type             | Description       |
|-----------------|-----------|
| [_SystemSoundPlayer](js-apis-inner-multimedia-systemSoundPlayer.md#systemsoundplayer) | System sound effect player object.|
