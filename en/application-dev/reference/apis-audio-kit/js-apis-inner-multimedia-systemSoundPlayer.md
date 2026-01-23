# SystemSoundPlayer (Sound Effect Player)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

The sound effect player provides functions for loading, unloading, and playing system sounds.

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

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name    | Type                     | Mandatory| Description            |
| ---------- | ------------------------- | ---- | ---------------- |
| soundType | [systemSoundManager.SystemSoundType](js-apis-systemSoundManager.md#systemsoundtype) | Yes  | System sound effect type.|

**Return value**

| Type   | Description                           |
| ------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 5400103 | I/O error. |
| 5400105 | Crash or blocking occurs in system process. |
| 5400108 | Parameter check failed. Returned by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.load(systemSoundManager.SystemSoundType.PHOTO_SHUTTER).then(() => {
  console.info('Succeeded in calling the load method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to call the load method. Code: ${err.code}, message: ${err.message}`);
});
```

### play

play(soundType: systemSoundManager.SystemSoundType): Promise&lt;void&gt;

Plays the system sound effect. This API uses a promise to return the result.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name    | Type                     | Mandatory| Description            |
| ---------- | ------------------------- | ---- | ---------------- |
| soundType | [systemSoundManager.SystemSoundType](js-apis-systemSoundManager.md#systemsoundtype) | Yes  | System sound effect type.|

**Return value**

| Type   | Description                           |
| ------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 5400103 | I/O error. |
| 5400105 | Crash or blocking occurs in system process. |
| 5400108 | Parameter check failed. Returned by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.play(systemSoundManager.SystemSoundType.PHOTO_SHUTTER).then(() => {
  console.info('Succeeded in calling the play method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to call the play method. Code: ${err.code}, message: ${err.message}`);
});
```

### unload

unload(soundType: systemSoundManager.SystemSoundType): Promise&lt;void&gt;

Unloads the system sound effect that has been loaded. This API uses a promise to return the result.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name    | Type                     | Mandatory| Description            |
| ---------- | ------------------------- | ---- | ---------------- |
| soundType | [systemSoundManager.SystemSoundType](js-apis-systemSoundManager.md#systemsoundtype) | Yes  | System sound effect type.|

**Return value**

| Type   | Description                           |
| ------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 5400105 | Crash or blocking occurs in system process. |
| 5400108 | Parameter check failed. Returned by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.unload(systemSoundManager.SystemSoundType.PHOTO_SHUTTER).then(() => {
  console.info('Succeeded in calling the unload method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to call the unload method. Code: ${err.code}, message: ${err.message}`);
});
```

### release

release(): Promise&lt;void&gt;

Releases the system sound effect player. This API uses a promise to return the result.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type   | Description                           |
| ------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 5400105 | Crash or blocking occurs in system process. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

systemSoundPlayer?.release().then(() => {
  console.info('Succeeded in calling the release method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to call the release method. Code: ${err.code}, message: ${err.message}`);
});
```
