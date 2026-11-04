# SystemSoundPlayer (Sound Effect Player)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=24d41a0bca6541c58a989fa09a384d3cf0eeb920 translatedAt=2026-11-03T04:38:19.376Z pushedAt=2026-11-04T03:11:47.066Z nl=1 -->

This module provides the system sound effect playback capability, including loading and unloading of system sounds, and supports the playback of system sound effects such as photo capture and video recording. When standard system notification sounds need to be integrated into an application to improve user experience consistency, use the APIs of this module to complete the related operations.

**SystemSoundPlayer** needs to be used with [@ohos.multimedia.systemSoundManager](js-apis-systemSoundManager.md) to complete the function of managing system sounds.

> **NOTE**
>
> The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { systemSoundManager } from '@kit.AudioKit';
```

## SystemSoundPlayer

**SystemSoundPlayer** provides playback functions for camera shutter and video recording sounds. Before calling the APIs of **SystemSoundPlayer**, you need to create a **SystemSoundPlayer** object through [createSystemSoundPlayer](js-apis-systemSoundManager.md#systemsoundmanagercreatesystemsoundplayer).

### load

load(soundType: systemSoundManager.SystemSoundType): Promise&lt;void&gt;

Loads the system sound effect. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name    | Type                     | Mandatory| Description            |
| ---------- | ------------------------- | ---- | ---------------- |
| soundType | [systemSoundManager.SystemSoundType](js-apis-systemSoundManager.md#systemsoundtype) | Yes | System sound effect type to load. |

**Return value**

| Type   | Description                           |
| ------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the following error codes, see [Media Error Code](../apis-media-kit/errorcode-media.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 5400103 | I/O error. |
| 5400105 | Crash or blocking occurs in system process. |
| 5400108 | Parameter check failed. Returned by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.load(systemSoundManager.SystemSoundType.PHOTO_SHUTTER).then(() => {
  console.info('Succeeded in loading the system sound.');
}).catch((err: BusinessError) => {
  console.error(`Failed to load the system sound. Code: ${err.code}, message: ${err.message}`);
});
```

### play

play(soundType: systemSoundManager.SystemSoundType): Promise&lt;void&gt;

Plays the system sound effect. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name    | Type                     | Mandatory| Description            |
| ---------- | ------------------------- | ---- | ---------------- |
| soundType | [systemSoundManager.SystemSoundType](js-apis-systemSoundManager.md#systemsoundtype) | Yes | Type of the system sound effect to play. |

**Return value**

| Type   | Description                           |
| ------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the following error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 5400103 | I/O error. |
| 5400105 | Crash or blocking occurs in system process. |
| 5400108 | Parameter check failed. Returned by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.play(systemSoundManager.SystemSoundType.PHOTO_SHUTTER).then(() => {
  console.info('Succeeded in playing the system sound.');
}).catch((err: BusinessError) => {
  console.error(`Failed to play the system sound. Code: ${err.code}, message: ${err.message}`);
});
```

### unload

unload(soundType: systemSoundManager.SystemSoundType): Promise&lt;void&gt;

Unloads the system sound effect that has been loaded. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name    | Type                     | Mandatory| Description            |
| ---------- | ------------------------- | ---- | ---------------- |
| soundType | [systemSoundManager.SystemSoundType](js-apis-systemSoundManager.md#systemsoundtype) | Yes | Type of the system sound effect to unload. |

**Return value**

| Type   | Description                           |
| ------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media error codes](../apis-media-kit/errorcode-media.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 5400105 | Crash or blocking occurs in system process. |
| 5400108 | Parameter check failed. Returned by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.unload(systemSoundManager.SystemSoundType.PHOTO_SHUTTER).then(() => {
  console.info('Succeeded in unloading the system sound.');
}).catch((err: BusinessError) => {
  console.error(`Failed to unload the system sound. Code: ${err.code}, message: ${err.message}`);
});
```

### release

release(): Promise&lt;void&gt;

Releases the system sound effect player. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type   | Description                           |
| ------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media error codes](../apis-media-kit/errorcode-media.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 5400105 | Crash or blocking occurs in system process. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.release().then(() => {
  console.info('Succeeded in releasing the system sound player.');
}).catch((err: BusinessError) => {
  console.error(`Failed to release the system sound player. Code: ${err.code}, message: ${err.message}`);
});
```