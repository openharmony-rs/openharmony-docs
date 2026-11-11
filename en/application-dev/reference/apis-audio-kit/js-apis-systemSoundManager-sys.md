# @ohos.multimedia.systemSoundManager (System Sound Management) (System API)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=6b5f52603d23af8219cc31e0de24ebcd4586968e translatedAt=2026-11-09T10:32:01.273Z pushedAt=2026-11-09T11:39:17.574Z nl=1 -->

The systemSoundManager module provides basic capabilities for managing system sounds, including setting and obtaining ringtones and obtaining a player to play the ringtones.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { systemSoundManager } from '@kit.AudioKit';
```

## Constants

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name                                      | Type | Value   | Description      |
|------------------------------------------|---|-----|---------|
| TONE_CATEGORY_RINGTONE<sup>12+</sup>     | number | 1   | Ringtone.   |
| TONE_CATEGORY_TEXT_MESSAGE<sup>12+</sup> | number | 2   | SMS tone. |
| TONE_CATEGORY_NOTIFICATION<sup>12+</sup> | number | 4   | Notification tone. |
| TONE_CATEGORY_ALARM<sup>12+</sup>        | number | 8   | Alarm tone. |
| TONE_CATEGORY_CONTACTS<sup>20+</sup>     | number | 16  | Contact ringtone category.<br>**Model restriction:** This API can be used only in the stage model. |
| TONE_CATEGORY_NOTIFICATION_APP<sup>22+</sup>     | number | 32  | Application-level notification tone. |

## RingtoneType

Enumerates the ringtone types.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name                            | Value  | Description                                                                     |
| ------------------------------- |----|------------------------------------------------------------------------|
| RINGTONE_TYPE_DEFAULT<sup>(deprecated)</sup>           | 0  | Default ringtone type.<br> This enumerated value is deprecated since API version 11. You are advised to use **RINGTONE_TYPE_SIM_CARD_0** instead. |
| RINGTONE_TYPE_SIM_CARD_0<sup>11+</sup> | 0  | Ringtone of SIM card 1.                                                              |
| RINGTONE_TYPE_MULTISIM<sup>(deprecated)</sup>          | 1  | Multi-SIM ringtone type.<br> This enumerated value is deprecated since API version 11. You are advised to use **RINGTONE_TYPE_SIM_CARD_1** instead. |
| RINGTONE_TYPE_SIM_CARD_1<sup>11+</sup> | 1  | Ringtone of SIM card 2.                                                              |
| RINGTONE_TYPE_ESIM_CARD_0 | 2  | Ringtone of ESIM card 1.<br>**Since Version:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| RINGTONE_TYPE_ESIM_CARD_1 | 3  | Ringtone of ESIM card 2.<br>**Since Version:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |

## SystemToneType<sup>11+</sup>

Enumerates the system tone types.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name                            | Value   | Description         |
| ------------------------------- |-----|------------|
| SYSTEM_TONE_TYPE_SIM_CARD_0     | 0   | SMS alert tone for SIM card 1. |
| SYSTEM_TONE_TYPE_SIM_CARD_1     | 1   | SMS alert tone for SIM card 2. |
| SYSTEM_TONE_TYPE_ESIM_CARD_0     | 2   | SMS alert tone for eSIM card 1.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| SYSTEM_TONE_TYPE_ESIM_CARD_1     | 3   | SMS alert tone for eSIM card 2.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| SYSTEM_TONE_TYPE_NOTIFICATION   | 32  | Notification tone.     |

## MediaType<sup>20+</sup>

Enumerates the media types.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name                            | Value   | Description         |
| ------------------------------- |-----|------------|
| AUDIO      | 0   | Audio. |
| VIDEO       | 1   | Video. |

## SystemSoundError<sup>20+</sup>

Enumerates the types of errors available for system sounds.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name                         | Value   | Description         |
| -----------------------------|-----|------------|
| ERROR_IO                     | 5400103  | I/O error.     |
| ERROR_OK                     | 20700000 | No error.     |
| ERROR_TYPE_MISMATCH          | 20700001 | Type mismatch.     |
| ERROR_UNSUPPORTED_OPERATION  | 20700003 | Unsupported operation.     |
| ERROR_DATA_TOO_LARGE         | 20700004 | Data size exceeds the upper limit.     |
| ERROR_TOO_MANY_FILES         | 20700005 | File count exceeds the upper limit.     |
| ERROR_INSUFFICIENT_ROM       | 20700006 | Insufficient ROM space.     |
| ERROR_INVALID_PARAM          | 20700007 | Invalid parameter.     |

## ToneCustomizedType<sup>12+</sup>

Enumerates the tone customization types.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name                         | Value   | Description         |
| ----------------------------|-----|------------|
| PRE_INSTALLED<sup>12+</sup> | 0   | Preinstalled tone. |
| CUSTOMIZED<sup>12+</sup>    | 1   | Custom tone. |

## ToneAttrs<sup>12+</sup>

Manages tone attributes. Before calling any API in ToneAttrs<sup>12+</sup>, you must use [createCustomizedToneAttrs](#systemsoundmanagercreatecustomizedtoneattrs12), [getDefaultRingtoneAttrs](#getdefaultringtoneattrs12), or [getRingtoneAttrList](#getringtoneattrlist12) to obtain a tone instance.

### getTitle<sup>12+</sup>

getTitle(): string

Obtains the title of this tone.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type    | Description  |
|--------|-----|
| string | Title. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |

**Example**

```ts
toneAttrs.getTitle();
```

### setTitle<sup>12+</sup>

setTitle(title: string): void

Sets the title for this tone.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name  | Type    | Mandatory | Description          |
| -------| -------| ---- | ------------|
| title  | string | Yes   | Title.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message              |
|-------| -------------------- |
| 202   | Caller is not a system application. |
| 401   | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
let title = 'text';
toneAttrs.setTitle(title);
```

### getFileName<sup>12+</sup>

getFileName(): string

Obtains the file name of this tone.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type    | Description   |
|--------|------|
| string | File name. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |


**Example**

```ts
toneAttrs.getFileName();
```

### setFileName<sup>12+</sup>

setFileName(name: string): void

Sets the file name for this tone.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name | Type    | Mandatory | Description         |
| ------| -------|-----| ------------|
| name  | string | Yes   | File name. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message              |
|-------| -------------------- |
| 202   | Caller is not a system application. |
| 401   | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
let fileName = 'textFileName';
toneAttrs.setFileName(fileName);
```

### getUri<sup>12+</sup>

getUri(): string

Obtains the URI of this tone.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type    | Description                                                      |
|--------|---------------------------------------------------------|
| string | URI, for example, **'/data/storage/el2/base/RingTone/alarms/test.ogg'**. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |

**Example**

```ts
toneAttrs.getUri();
```

### getCustomizedType<sup>12+</sup>

getCustomizedType(): ToneCustomizedType

Obtains the tone customization type.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type                                         | Description      |
|--------------------------------------------|---------|
| [ToneCustomizedType](#tonecustomizedtype12) | Tone customization type. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |

**Example**

```ts
toneAttrs.getCustomizedType();
```

### setCategory<sup>12+</sup>

setCategory(category: number): void

Sets a category for this tone.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name      | Type      | Mandatory | Description       |
|----------| ---------| ----|----------|
| category | number   | Yes   | Category of the tone. For details, see [Constants](#constants).  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message              |
|-------| -------------------- |
| 202   | Caller is not a system application. |
| 401   | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
let categoryValue = systemSoundManager.TONE_CATEGORY_ALARM; // Change to the actual required type constant.
toneAttrs.setCategory(categoryValue);
```

### getCategory<sup>12+</sup>

getCategory(): number

Obtains the category of this tone.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type    | Description     |
|--------|--------|
| number | Category of the tone. For details, see [Constants](#constants). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |


**Example**

```ts
toneAttrs.getCategory();
```

### setMediaType<sup>20+</sup>

setMediaType(type: MediaType): void

Sets a media type for this tone.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name      | Type      | Mandatory | Description       |
|----------| ---------| ---- |----------|
| type | [MediaType](#mediatype20)   | Yes   | Media type.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message              |
|-------| -------------------- |
| 202   | Caller is not a system application. |

**Example**

```ts
let type: systemSoundManager.MediaType = systemSoundManager.MediaType.VIDEO; // Change to the actual required type.
let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
toneAttrs.setMediaType(type);
```

### getMediaType<sup>20+</sup>

getMediaType(): MediaType

Obtains the media type of this tone.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type    | Description     |
|--------|--------|
| [MediaType](#mediatype20) | Media type. If the application has not called setMediaType to set the media type, the default value returned by this function is AUDIO.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |

**Example**

```ts
toneAttrs.getMediaType();
```

## ToneAttrsArray<sup>12+</sup>

type ToneAttrsArray = Array&lt;[ToneAttrs](#toneattrs12)&gt;

Defines an array of tone attributes.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Type                                     | Description      |
|----------------------------------------|---------|
| Array&lt;[ToneAttrs](#toneattrs12)&gt; | Defines an array of tone attributes. |

## systemSoundManager.createCustomizedToneAttrs<sup>12+</sup>

createCustomizedToneAttrs(): ToneAttrs

Creates customized tone attributes.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type                        | Description         |
|---------------------------| ------------ |
| [ToneAttrs](#toneattrs12) | Class for tone attributes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |

**Example**
```ts
let toneAttrs: systemSoundManager.ToneAttrs = systemSoundManager.createCustomizedToneAttrs();
```
## ToneHapticsFeature<sup>13+</sup>

Enumerates the haptics styles for different tones.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name                          | Value | Description                 |
| ----------------------------- | -- | -------------------- |
| STANDARD| 0  | Standard haptics style. |
| GENTLE   | 1  | Gentle haptics style. |

## ToneHapticsType<sup>14+</sup>

Enumerates the haptics types for different tones.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name                     | Value | Description         |
| ------------------------|----|--------|
| CALL_SIM_CARD_0         | 0  | Vibration of the incoming call ringtone of SIM card 1. |
| CALL_SIM_CARD_1         | 1  | Vibration of the incoming call ringtone of SIM card 2. |
| CALL_ESIM_CARD_0         | 2  | Vibration of the incoming call ringtone of eSIM card 1. <br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| CALL_ESIM_CARD_1         | 3  | Vibration of the incoming call ringtone of eSIM card 2. <br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| TEXT_MESSAGE_SIM_CARD_0 | 20 | Vibration of the text message notification tone of SIM card 1. |
| TEXT_MESSAGE_SIM_CARD_1 | 21 | Vibration of the text message notification tone of SIM card 2. |
| TEXT_MESSAGE_ESIM_CARD_0 | 22 | Vibration of the text message notification tone of eSIM card 1.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| TEXT_MESSAGE_ESIM_CARD_1 | 23 | Vibration of the text message notification tone of eSIM card 2.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |
| NOTIFICATION            | 40 | Haptic feedback for notification tone. |
| ALARM            | 41 | Vibration of the alarm.<br>**Since:** 26.0.1<br>**Model restriction:** This interface is only available in the Stage model. |

## ToneHapticsMode<sup>14+</sup>

Enumerates the haptics modes in tone playback scenarios.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name                          | Value | Description                 |
| ----------------------------- | -- | -------------------- |
| NONE        | 0  | No haptics. |
| SYNC        | 1  | Sync mode, where haptic feedback is aligned with tone playback. |
| NON_SYNC    | 2  | Non-sync mode, where haptic feedback is not aligned with tone playback. |

## ToneHapticsSettings<sup>14+</sup>

Describes the haptics settings of a tone.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Name          | Type | Read-Only | Optional | Description                 |
| ------------ | -- | -- | -- | -------------------- |
| mode | [ToneHapticsMode](#tonehapticsmode14) | No | No | Haptics mode. |
| hapticsUri | string                          | No | Yes | URI of the haptics resource. The URI, obtained by calling [getToneHapticsList](#gettonehapticslist14), is valid only in the non-sync mode and should be ignored in other haptics modes. |

## ToneHapticsAttrs<sup>14+</sup>

Manages haptics attributes of tones. Before calling any API in ToneHapticsAttrs<sup>14+</sup>, you must use [getToneHapticsList](#gettonehapticslist14) or [getHapticsAttrsSyncedWithTone](#gethapticsattrssyncedwithtone14) to obtain an instance.

### getUri<sup>14+</sup>

getUri(): string

Obtains the URI of this haptics resource.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type    | Description  |
|--------|-----|
| string | URI, for example, **'/data/storage/el2/base/haptics/synchronized/alarms/test.json'**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |

**Example**

```ts
toneHapticsAttrs.getUri();
```

### getTitle<sup>14+</sup>

getTitle(): string

Obtains the title of this haptics resource.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type    | Description  |
|--------|-----|
| string | Title. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |

**Example**

```ts
toneHapticsAttrs.getTitle();
```

### getFileName<sup>14+</sup>

getFileName(): string

Obtains the file name of this haptics resource.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type    | Description  |
|--------|-----|
| string | File name. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |

**Example**

```ts
toneHapticsAttrs.getFileName();
```
### getGentleUri<sup>22+</sup>

getGentleUri(): string | null

Obtains the URI of the gentle haptics resource.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type    | Description  |
|--------|-----|
| string \| null | URI of the gentle vibration (for example, '/data/storage/el2/base/haptics/synchronized/alarms/test.json'). If no gentle vibration exists, the URI is empty. Gentle vibration means that the motor vibration intensity is weaker than the standard. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |

**Example**

```ts
toneHapticsAttrs.getGentleUri();
```

### getGentleTitle<sup>22+</sup>

getGentleTitle(): string | null

Obtains the title of the gentle haptics resource.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type    | Description  |
|--------|-----|
| string \| null | Title of the gentle haptics resource. If no gentle haptics resource exists, null is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |

**Example**

```ts
toneHapticsAttrs.getGentleTitle();
```

### getGentleFileName<sup>22+</sup>

getGentleFileName(): string | null

Obtains the file name of the gentle haptics resource.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type    | Description  |
|--------|-----|
| string \| null | Name of the gentle vibration file. The vibration file is in JSON format. If no gentle vibration exists, the vibration file name is empty. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |

**Example**

```ts
toneHapticsAttrs.getGentleFileName();
```

## ToneHapticsAttrsArray<sup>14+</sup>

type ToneHapticsAttrsArray = Array&lt;ToneHapticsAttrs&gt;

Describes the haptics attribute array of a tone.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Type                                     | Description      |
|----------------------------------------|---------|
| Array&lt;[ToneHapticsAttrs](#tonehapticsattrs14)&gt; | Describes the haptics attribute array of a tone. |

## systemSoundManager.getSystemSoundManager

getSystemSoundManager(): SystemSoundManager

Obtains a system sound manager.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Return value**

| Type                          | Description         |
| ----------------------------- | ------------ |
| [SystemSoundManager](#systemsoundmanager) | System sound manager obtained. |

**Example**
```ts
let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
```

## SystemSoundManager

Provides APIs to manage system sounds. Before calling any API in SystemSoundManager, you must use [getSystemSoundManager](#systemsoundmanagergetsystemsoundmanager) to obtain a SystemSoundManager instance.

### setSystemRingtoneUri<sup>(deprecated)</sup>

setSystemRingtoneUri(context: Context, uri: string, type: RingtoneType, callback: AsyncCallback&lt;void&gt;): void

Sets a URI for a ringtone. This API uses an asynchronous callback to return the result.

> **NOTE**
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [setRingtoneUri](#setringtoneuri11) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name     | Type                                      | Mandatory | Description                     |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| context  | [Context](../apis-ability-kit/js-apis-inner-application-context.md)   | Yes   | Application context.           |
| uri      | string                                   | Yes   | URI of the ringtone. For details about supported resources, see [media.AVPlayer](../apis-media-kit/arkts-apis-media-AVPlayer.md). |
| type     | [RingtoneType](#ringtonetype)            | Yes   | Type of the ringtone.     |
| callback | AsyncCallback&lt;void&gt;                | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // Change this to the URI of the target ringtone file.
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setSystemRingtoneUri(context, uri, type, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set system ringtone uri. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate a successful setting of the system ringtone uri.`);
});
```

### setSystemRingtoneUri<sup>(deprecated)</sup>

setSystemRingtoneUri(context: Context, uri: string, type: RingtoneType): Promise&lt;void&gt;

Sets a URI for a ringtone. This API uses a promise to return the result.

> **NOTE**
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [setRingtoneUri](#setringtoneuri11) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                                      | Mandatory | Description                     |
| -------- | ---------------------------------------- | ---- | ------------------------ |
| context  | [Context](../apis-ability-kit/js-apis-inner-application-context.md)  | Yes   | Application context.         |
| uri      | string                                   | Yes   | URI of the ringtone. For details about supported resources, see [media.AVPlayer](../apis-media-kit/arkts-apis-media-AVPlayer.md). |
| type     | [RingtoneType](#ringtonetype)            | Yes   | Type of the ringtone.   |

**Return value**

| Type                | Description                            |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // Change this to the URI of the target ringtone file.
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setSystemRingtoneUri(context, uri, type).then(() => {
  console.info('Succeeded in doing setSystemRingtoneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setSystemRingtoneUri. Code: ${err.code}, message: ${err.message}`);
});
```

### getSystemRingtoneUri<sup>(deprecated)</sup>

getSystemRingtoneUri(context: Context, type: RingtoneType, callback: AsyncCallback&lt;string&gt;): void

Obtains the URI of a ringtone. This API uses an asynchronous callback to return the result.

> **NOTE**
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [getRingtoneUri](#getringtoneuri11) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name     | Type                                                                    | Mandatory | Description                     |
| -------- |-----------------------------------------------------------------------| ---- | ------------------------ |
| context  | [Context](../apis-ability-kit/js-apis-inner-application-context.md)   | Yes   | Application context.         |
| type     | [RingtoneType](#ringtonetype)                                         | Yes   | Type of the ringtone.    |
| callback | AsyncCallback&lt;string&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is undefined and **data** is the URI obtained; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemRingtoneUri(context, type, (err: BusinessError, value: string) => {
  if (err) {
    console.error(`Failed to get system ringtone uri. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate the value of the system ringtone uri is obtained ${value}.`);
});
```

### getSystemRingtoneUri<sup>(deprecated)</sup>

getSystemRingtoneUri(context: Context, type: RingtoneType): Promise&lt;string&gt;

Obtains the URI of a ringtone. This API uses a promise to return the result.

> **NOTE**
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [getRingtoneUri](#getringtoneuri11) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                                                                   | Mandatory | Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------ |
| context  | [Context](../apis-ability-kit/js-apis-inner-application-context.md)  | Yes   | Application context.         |
| type     | [RingtoneType](#ringtonetype)                                        | Yes   | Type of the ringtone.   |

**Return value**

| Type                | Description                                |
| ------------------- | ---------------------------------- |
| Promise&lt;string&gt; | Promise used to return the URI obtained. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemRingtoneUri(context, type).then((value: string) => {
  console.info('Succeeded in doing getSystemRingtoneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getSystemRingtoneUri. Code: ${err.code}, message: ${err.message}`);
});
```

### getSystemRingtonePlayer<sup>(deprecated)</sup>

getSystemRingtonePlayer(context: Context, type: RingtoneType, callback: AsyncCallback&lt;RingtonePlayer&gt;): void

Obtains a player to play a ringtone. This API uses an asynchronous callback to return the result.

> **NOTE**
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [getRingtonePlayer](#getringtoneplayer11) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                                      | Mandatory | Description                         |
| -------- | -----------------------------------------| ---- | --------------------------- |
| context  | [Context](../apis-ability-kit/js-apis-inner-application-context.md)  | Yes   | Application context.            |
| type     | [RingtoneType](#ringtonetype)            | Yes   | Type of the ringtone. |
| callback | AsyncCallback&lt;[RingtonePlayer](js-apis-inner-multimedia-ringtonePlayer-sys.md#ringtoneplayer)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is undefined and **data** is the player obtained; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;
let systemRingtonePlayer: systemSoundManager.RingtonePlayer | undefined = undefined;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemRingtonePlayer(context, type, (err: BusinessError, value: systemSoundManager.RingtonePlayer) => {
  if (err) {
    console.error(`Failed to get system ringtone player. ${err}`);
    return;
  }
  console.info(`Callback invoked to indicate the value of the system ringtone player is obtained.`);
  systemRingtonePlayer = value;
});
```

### getSystemRingtonePlayer<sup>(deprecated)</sup>

getSystemRingtonePlayer(context: Context, type: RingtoneType): Promise&lt;RingtonePlayer&gt;

Obtains a player to play a ringtone. This API uses a promise to return the result.

> **NOTE**
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [getRingtonePlayer](#getringtoneplayer11) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name    | Type                                                                  | Mandatory | Description                         |
| ------- |---------------------------------------------------------------------| --------- | ----------------------------------- |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md) | Yes       | Application context. |
| type    | [RingtoneType](#ringtonetype)                                       | Yes       | Type of the ringtone. |

**Return value**

| Type                | Description                            |
| ------------------- | ------------------------------- |
| Promise&lt;[RingtonePlayer](js-apis-inner-multimedia-ringtonePlayer-sys.md#ringtoneplayer)&gt; | Promise used to return the player obtained. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_DEFAULT;
let systemRingtonePlayer: systemSoundManager.RingtonePlayer | undefined = undefined;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemRingtonePlayer(context, type).then((value: systemSoundManager.RingtonePlayer) => {
  console.info('Succeeded in doing getSystemRingtonePlayer.');
  systemRingtonePlayer = value;
}).catch((err: BusinessError) => {
  console.error(`Failed to getSystemRingtonePlayer. Code: ${err.code}, message: ${err.message}`);
});
```

### setRingtoneUri<sup>11+</sup>

setRingtoneUri(context: BaseContext, uri: string, type: RingtoneType): Promise&lt;void&gt;

Sets a URI for a ringtone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                            | Mandatory | Description                     |
| -------- |-------------------------------| ---- | ------------------------ |
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md)            | Yes   | Application context.         |
| uri      | string                        | Yes   | URI of the ringtone. For details about supported resources, see [media.AVPlayer](../apis-media-kit/arkts-apis-media-AVPlayer.md). |
| type     | [RingtoneType](#ringtonetype) | Yes   | Type of the ringtone.   |

**Return value**

| Type                | Description                            |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // Change to the URI of the target ringtone file.
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setRingtoneUri(context, uri, type).then(() => {
  console.info('Succeeded in doing setRingtoneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setRingtoneUri. Code: ${err.code}, message: ${err.message}`);
});
```

### getRingtoneUri<sup>11+</sup>

getRingtoneUri(context: BaseContext, type: RingtoneType): Promise&lt;string&gt;

Obtains the URI of a ringtone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                             | Mandatory | Description                     |
| -------- | -------------------------------| ---- | ------------------------ |
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md)| Yes   | Application context.         |
| type     | [RingtoneType](#ringtonetype)  | Yes   | Type of the ringtone.   |

**Return value**

| Type                | Description                                |
| ------------------- | ---------------------------------- |
| Promise&lt;string&gt; | Promise used to return the URI obtained. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| -------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103  | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getRingtoneUri(context, type).then((value: string) => {
  console.info('Succeeded in doing getRingtoneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getRingtoneUri. Code: ${err.code}, message: ${err.message}`);
});
```

### getRingtonePlayer<sup>11+</sup>

getRingtonePlayer(context: BaseContext, type: RingtoneType): Promise&lt;RingtonePlayer&gt;

Obtains a player to play a ringtone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                              | Mandatory | Description                         |
| -------- | --------------------------------| ---- | --------------------------- |
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.            |
| type     | [RingtoneType](#ringtonetype)   | Yes   | Type of the ringtone. |

**Return value**

| Type                | Description                            |
| ------------------- | ------------------------------- |
| Promise&lt;[RingtonePlayer](js-apis-inner-multimedia-ringtonePlayer-sys.md#ringtoneplayer)&gt; | Promise used to return the player obtained. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message              |
| -------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;
let systemRingtonePlayer: systemSoundManager.RingtonePlayer | undefined = undefined;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getRingtonePlayer(context, type).then((value: systemSoundManager.RingtonePlayer) => {
  console.info('Succeeded in doing getRingtonePlayer.');
  systemRingtonePlayer = value;
}).catch((err: BusinessError) => {
  console.error(`Failed to getRingtonePlayer. Code: ${err.code}, message: ${err.message}`);
});
```

### getMockHapticRingtonePlayer

getMockHapticRingtonePlayer(context: BaseContext, hapticUri: string): Promise&lt;RingtonePlayer | null&gt;

Obtains a mock haptic ringtone player to play the vibration file and its corresponding mock haptic sound file based on the specified haptic file URI. This API uses a promise to return the result.

> **NOTE**
>
> - Before calling this API, ensure that the hapticUri passed in exists in the system; otherwise, exceptions and errors may occur, for example, the matching haptic sound file cannot be played.
> - After obtaining an instance through this API, call [release](js-apis-inner-multimedia-ringtonePlayer-sys.md#release) of RingtonePlayer to release the player resources when the service is terminated.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                              | Mandatory | Description                         |
| -------- | --------------------------------| ---- | --------------------------- |
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.            |
| hapticUri     | string  | Yes   | URI of the haptic file, which must be a JSON file that actually exists in the system files. |

**Return value**

| Type                | Description                            |
| ------------------- | ------------------------------- |
| Promise&lt;[RingtonePlayer](js-apis-inner-multimedia-ringtonePlayer-sys.md#ringtoneplayer) \| null&gt; | Promise object. Returns the mock haptic ringtone player instance on success, or null if an error occurs. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md), [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md), and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| -------- | --------------------- |
| 202 |Caller is not a system application.|
| 20700002 |Parameter verification failed. The hapticUri does not exist or is incorrectly formatted. Ensure it is a JSON file and that it exists in the system's file system.|
| 5400103  |I/O error. The ringtone database access timed out or encountered an error. It is recommended to restart your phone.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let systemRingtonePlayer: systemSoundManager.RingtonePlayer | null = null;
let hapticUri = 'file://data/test.json'; // Change it to the target haptic file URI.

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getMockHapticRingtonePlayer(context, hapticUri).then((value: systemSoundManager.RingtonePlayer | null) => {
  if (value != null) {
    console.info('Succeeded in doing getMockHapticRingtonePlayer.');
    systemRingtonePlayer = value;
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to getMockHapticRingtonePlayer. Code: ${err.code}, message: ${err.message}`);
});
```

### getMockHapticRingtonePlayer

getMockHapticRingtonePlayer(context: BaseContext, type: RingtoneType, ringtoneUri: string): Promise&lt;RingtonePlayer | null&gt;

Obtains a mock haptic ringtone player, which plays the vibration file and the mock haptic sound file corresponding to the specified ringtone type and ringtone file URI. This API uses a promise to return the result.

> **NOTE**
>
> - Before calling this API, ensure that the passed **ringtoneUri** exists in the system; otherwise, exceptions and errors may occur, for example, the matching haptic sound file cannot be played.
> - After obtaining an instance through this API, call [release](js-apis-inner-multimedia-ringtonePlayer-sys.md#release) of **RingtonePlayer** to release the player resources when the service is terminated.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                              | Mandatory | Description                         |
| -------- | --------------------------------| ---- | --------------------------- |
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.            |
| type     | [RingtoneType](#ringtonetype)   | Yes   | Ringtone type of the player to be obtained. |
| ringtoneUri     | string  | Yes   | URI of the ringtone file, which must actually exist in the system file.<br>For a customized ringtone, use the **ringtoneUri** returned by [addCustomizedTone](#addcustomizedtone12) to ensure that the ringtone file URI exists in the ringtone library. |

**Return value**

| Type                | Description                            |
| ------------------- | ------------------------------- |
| Promise&lt;[RingtonePlayer](js-apis-inner-multimedia-ringtonePlayer-sys.md#ringtoneplayer) \| null&gt; | Promise object. Returns the mock haptic ringtone player instance on success, or null if an error occurs. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md), [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md), and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| -------- | --------------------- |
| 202 |Caller is not a system application.|
| 20700002 |Parameter verification failed. Possible causes: 1. The type exceeds the valid range, please use the RingtoneType enum for input. 2. The ringtoneUri does not exist or is incorrectly formatted, please use the ringtoneUri returned by the [addCustomizedTone](#addcustomizedtone12).|
| 5400103  |I/O error. The ringtone database access timed out or encountered an error. It is recommended to restart your phone.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;
let systemRingtonePlayer: systemSoundManager.RingtonePlayer | null = null;
let ringtoneUri = 'file://data/test.json'; // Change it to the URI of the target ringtone file.

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getMockHapticRingtonePlayer(context, type, ringtoneUri).then((value: systemSoundManager.RingtonePlayer | null) => {
  if (value != null) {
    console.info('Succeeded in doing getMockHapticRingtonePlayer.');
    systemRingtonePlayer = value;
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to getMockHapticRingtonePlayer. Code: ${err.code}, message: ${err.message}`);
});
```

### setSystemToneUri<sup>11+</sup>

setSystemToneUri(context: BaseContext, uri: string, type: SystemToneType): Promise&lt;void&gt;

Sets a URI for a system tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                                  | Mandatory | Description                     |
| -------- |-------------------------------------| ---- | ------------------------ |
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.         |
| uri      | string                              | Yes   | URI of the system tone. For details about supported resources, see [media.AVPlayer](../apis-media-kit/arkts-apis-media-AVPlayer.md). |
| type     | [SystemToneType](#systemtonetype11) | Yes   | Type of the system tone.   |

**Return value**

| Type                | Description                            |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // Change it to the URI of the target ringtone file.
let type: systemSoundManager.SystemToneType = systemSoundManager.SystemToneType.SYSTEM_TONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setSystemToneUri(context, uri, type).then(() => {
  console.info('Succeeded in doing setSystemToneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setSystemToneUri. Code: ${err.code}, message: ${err.message}`);
});
```

### getSystemToneUri<sup>11+</sup>

getSystemToneUri(context: BaseContext, type: SystemToneType): Promise&lt;string&gt;

Obtains the URI of a system tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                                  | Mandatory | Description                     |
| -------- |-------------------------------------| ---- | ------------------------ |
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.         |
| type     | [SystemToneType](#systemtonetype11) | Yes   | Type of the system tone.   |

**Return value**

| Type                | Description                                |
| ------------------- | ---------------------------------- |
| Promise&lt;string&gt; | Promise used to return the URI obtained. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.SystemToneType = systemSoundManager.SystemToneType.SYSTEM_TONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemToneUri(context, type).then((value: string) => {
  console.info('Succeeded in doing getSystemToneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getSystemToneUri. Code: ${err.code}, message: ${err.message}`);
});
```

### getSystemTonePlayer<sup>11+</sup>

getSystemTonePlayer(context: BaseContext, type: SystemToneType): Promise&lt;SystemTonePlayer&gt;

Obtains a player to play a system tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                                  | Mandatory | Description                         |
| -------- |-------------------------------------| ---- | --------------------------- |
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.            |
| type     | [SystemToneType](#systemtonetype11) | Yes   | Type of the system tone. |

**Return value**

| Type                                                                                               | Description                            |
|--------------------------------------------------------------------------------------------------| ------------------------------- |
| Promise&lt;[SystemTonePlayer](js-apis-inner-multimedia-systemTonePlayer-sys.md#systemtoneplayer)&gt; | Promise used to return the player obtained. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.SystemToneType = systemSoundManager.SystemToneType.SYSTEM_TONE_TYPE_SIM_CARD_0;
let systemTonePlayer: systemSoundManager.SystemTonePlayer | undefined = undefined;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemTonePlayer(context, type).then((value: systemSoundManager.SystemTonePlayer) => {
  console.info('Succeeded in doing getSystemTonePlayer.');
    systemTonePlayer = value;
}).catch((err: BusinessError) => {
  console.error(`Failed to getSystemTonePlayer. Code: ${err.code}, message: ${err.message}`);
});
```

### getDefaultRingtoneAttrs<sup>12+</sup>

getDefaultRingtoneAttrs(context: BaseContext, type: RingtoneType): Promise&lt;ToneAttrs&gt;

Obtains the attributes of the default ringtone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                                  | Mandatory | Description                         |
| -------- |-------------------------------------| ---- | --------------------------- |
| context  |[BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.            |
| type     |[RingtoneType](#ringtonetype)        | Yes   | Type of the ringtone.  |

**Return value**

| Type                                                                                               | Description                            |
|--------------------------------------------------------------------------------------------------| ------------------------------- |
| Promise&lt;[ToneAttrs](#toneattrs12)&gt; | Promise used to return the attributes of the default ringtone. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getDefaultRingtoneAttrs(context, type).then((value: systemSoundManager.ToneAttrs) => {
  console.info('Succeeded in doing getDefaultRingtoneAttrs.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getDefaultRingtoneAttrs. Code: ${err.code}, message: ${err.message}`);
});
```

### getRingtoneAttrList<sup>12+</sup>

getRingtoneAttrList(context: BaseContext, type: RingtoneType): Promise&lt;ToneAttrsArray&gt;

Obtains an array of attributes of ringtones. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                                  | Mandatory | Description                         |
| -------- |-------------------------------------| ---- | --------------------------- |
| context  |[BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.            |
| type     |[RingtoneType](#ringtonetype)        | Yes   | Type of the ringtone.  |

**Return value**

| Type                                                                                               | Description                            |
|--------------------------------------------------------------------------------------------------| ------------------------------- |
| Promise&lt;[ToneAttrsArray](#toneattrsarray12)&gt; | Promise used to return an array of the attributes of ringtones. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getRingtoneAttrList(context, type).then((value: systemSoundManager.ToneAttrsArray) => {
  console.info('Succeeded in doing getRingtoneAttrList.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getRingtoneAttrList. Code: ${err.code}, message: ${err.message}`);
});
```

### getDefaultSystemToneAttrs<sup>12+</sup>

getDefaultSystemToneAttrs(context: BaseContext, type: SystemToneType): Promise&lt;ToneAttrs&gt;

Obtains the attributes of the default system tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                                                                          | Mandatory | Description                         |
| -------- |-----------------------------------------------------------------------------| ---- | --------------------------- |
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.            |
| type     | [SystemToneType](#systemtonetype11)                                         | Yes   | Type of the system tone. |

**Return value**

| Type                                      | Description                   |
|-----------------------------------------|----------------------|
| Promise&lt;[ToneAttrs](#toneattrs12)&gt; | Promise used to return the attributes of the default system tone. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.SystemToneType = systemSoundManager.SystemToneType.SYSTEM_TONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getDefaultSystemToneAttrs(context, type).then((value: systemSoundManager.ToneAttrs) => {
  console.info('Succeeded in doing getDefaultSystemToneAttrs.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getDefaultSystemToneAttrs. Code: ${err.code}, message: ${err.message}`);
});
```

### getSystemToneAttrList<sup>12+</sup>

getSystemToneAttrList(context: BaseContext, type: SystemToneType): Promise&lt;ToneAttrsArray&gt;

Obtains an array of attributes of system tones. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                                                                          | Mandatory | Description                         |
| -------- |-----------------------------------------------------------------------------| ---- | --------------------------- |
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.            |
| type     | [SystemToneType](#systemtonetype11)                                         | Yes   | Type of the system tone.  |

**Return value**

| Type                                                | Description                     |
|---------------------------------------------------|------------------------|
| Promise&lt;[ToneAttrsArray](#toneattrsarray12)&gt; | Promise used to return an array of the attributes of system tones. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.SystemToneType = systemSoundManager.SystemToneType.SYSTEM_TONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getSystemToneAttrList(context, type).then((value: systemSoundManager.ToneAttrsArray) => {
  console.info('Succeeded in doing getSystemToneAttrList.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getSystemToneAttrList. Code: ${err.code}, message: ${err.message}`);
});
```

### getDefaultAlarmToneAttrs<sup>12+</sup>

getDefaultAlarmToneAttrs(context: BaseContext): Promise&lt;ToneAttrs&gt;

Obtains the attributes of the default alarm tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type         | Mandatory | Description        |
| --------|------------| ---- |-----------|
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context. |

**Return value**

| Type                                      | Description                  |
|-----------------------------------------|---------------------|
| Promise&lt;[ToneAttrs](#toneattrs12)&gt; | Promise used to return the attributes of the default alarm tone. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getDefaultAlarmToneAttrs(context).then((value: systemSoundManager.ToneAttrs) => {
  console.info('Succeeded in doing getDefaultAlarmToneAttrs.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getDefaultAlarmToneAttrs. Code: ${err.code}, message: ${err.message}`);
});
```

### setAlarmToneUri<sup>12+</sup>

setAlarmToneUri(context: BaseContext, uri: string): Promise&lt;void&gt;

Sets a URI for an alarm tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type        | Mandatory | Description   |
| -------- | --------- | ---- |--------------------------|
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.                                                                           |
| uri      | string    | Yes   | URI of the alarm tone. For details about supported resources, see [media.AVPlayer](../apis-media-kit/arkts-apis-media-AVPlayer.md). |

**Return value**

| Type                | Description                   |
| ------------------- |----------------------|
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Media Error Codes](../apis-media-kit/errorcode-media.md), and [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |
| 20700001 | Tone type mismatch, e.g. tone of input uri is not an alarm tone. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // Change it to the URI of the target ringtone file.

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setAlarmToneUri(context, uri).then(() => {
  console.info('Succeeded in doing setAlarmToneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setAlarmToneUri. Code: ${err.code}, message: ${err.message}`);
});
```

### getAlarmToneUri<sup>12+</sup>

getAlarmToneUri(context: BaseContext): Promise&lt;string&gt;

Obtains the URI of the current alarm tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type      | Mandatory | Description              |
| -------- | --------| ---- |-----------------|
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.  |

**Return value**

| Type                    | Description                    |
|-----------------------|-----------------------|
| Promise&lt;string&gt; | Promise used to return the URI of the current alarm tone. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getAlarmToneUri(context).then((value: string) => {
  console.info('Succeeded in doing getAlarmToneUri.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getAlarmToneUri. Code: ${err.code}, message: ${err.message}`);
});
```

### getAlarmToneAttrList<sup>12+</sup>

getAlarmToneAttrList(context: BaseContext): Promise&lt;ToneAttrsArray&gt;

Obtains an array of attributes of alarm tones. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type            | Mandatory | Description                         |
| -------- |--------------| ---- | --------------------------- |
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md)  | Yes   | Application context.            |

**Return value**

| Type                                                 | Description                   |
|----------------------------------------------------|----------------------|
| Promise&lt;[ToneAttrsArray](#toneattrsarray12)&gt; | Promise used to return an array of the attributes of alarm tones. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getAlarmToneAttrList(context).then((value: systemSoundManager.ToneAttrsArray) => {
  console.info('Succeeded in doing getAlarmToneAttrList.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getAlarmToneAttrList. Code: ${err.code}, message: ${err.message}`);
});
```

### openAlarmTone<sup>12+</sup>

openAlarmTone(context: BaseContext, uri: string): Promise&lt;number&gt;

Enables an alarm tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type       | Mandatory | Description                                                                                  |
| -------- | ---------| ---- |-------------------------------------------------------------------------------------|
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.                                                                           |
| uri      | string   | Yes   | URI of the alarm tone. For details about supported resources, see [media.AVPlayer](../apis-media-kit/arkts-apis-media-AVPlayer.md). |

**Return value**

| Type                    | Description             |
|-----------------------|----------------|
| Promise&lt;number&gt; | Promise used to return the FD. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Media Error Codes](../apis-media-kit/errorcode-media.md), and [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |
| 20700001 | Tone type mismatch, e.g. tone of uri is notification instead of alarm. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // Change it to the URI of the target ringtone file.

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.openAlarmTone(context, uri).then((value: number) => {
  console.info('Succeeded in doing openAlarmTone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to openAlarmTone. Code: ${err.code}, message: ${err.message}`);
});
```

### close<sup>12+</sup>

close(fd: number): Promise&lt;void&gt;

Disables an alarm tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name | Type   | Mandatory | Description                                           |
|-----| --------| ---- |----------------------------------------------|
| fd  | number  | Yes   | File descriptor, which is obtained through [openAlarmTone](#openalarmtone12). |

**Return value**

| Type                  | Description             |
|---------------------|----------------|
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component to ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let fd = 50; // Change to the fd of the target ringtone.

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.close(fd).then(() => {
  console.info('Succeeded in doing close.');
}).catch((err: BusinessError) => {
  console.error(`Failed to close. Code: ${err.code}, message: ${err.message}`);
});
```

### addCustomizedTone<sup>12+</sup>

addCustomizedTone(context: BaseContext, toneAttr: ToneAttrs, externalUri: string): Promise&lt;string&gt;

Adds a custom tone with a given URI to the tone library. This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE_RINGTONE

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name | Type        | Mandatory | Description            |
|-----|-----------| ---- |---------------|
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.     |
| toneAttr  | ToneAttrs | Yes   | Attributes of the tone.         |
| externalUri  | string    | Yes   | URI of the tone in the external storage device. |

**Return value**

| Type                    | Description                      |
|-----------------------|-------------------------|
| Promise&lt;string&gt; | Promise used to return the URI of the tone in the tone library. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Media Error Codes](../apis-media-kit/errorcode-media.md), and [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md).

| ID   | Error Message              |
|---------| -------------------- |
| 201     | Permission denied. |
| 202     | Caller is not a system application. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102     | Operation is not allowed, e.g. ringtone to add is not customized. |
| 5400103  | I/O error. Possible causes: 1. The target file size exceeds 2 GB; 2. Failed to find the specified file; 3. System sound manager service error.|
| 20700004 | Data size exceeds the limit. Note:This error is returned when the file size is between 200MB and 2GB.<br>Applicable version: 20+|
| 20700005 | The number of files exceeds the limit.<br>Applicable version: 20+ |
| 20700006 | Insufficient ROM space.<br>Applicable version: 20+ |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let title = 'test'; // Change it to the actual name.
let fileName = 'displayName_test'; // Change it to the actual file name.
let categoryValue = systemSoundManager.TONE_CATEGORY_ALARM;

let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
toneAttrs.setTitle(title);
toneAttrs.setFileName(fileName);
toneAttrs.setCategory(categoryValue);

let path = 'file://data/test.ogg'; // Change it to the actual ringtone URI.

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.addCustomizedTone(context, toneAttrs, path).then((value: string) => {
  console.info('Succeeded in doing addCustomizedTone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to addCustomizedTone. Code: ${err.code}, message: ${err.message}`);
});
```

### addCustomizedTone<sup>12+</sup>

addCustomizedTone(context: BaseContext, toneAttr: ToneAttrs, fd: number, offset?: number, length?: number): Promise&lt;string&gt;

Adds a custom tone with a given FD to the tone library. This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE_RINGTONE

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name | Type        | Mandatory | Description                                                                     |
|-----|-----------|----|------------------------------------------------------------------------|
| context | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes  | Application context.                                                              |
| toneAttr | [ToneAttrs](#toneattrs12) | Yes  | Attributes of the tone.                                                                  |
| fd  | number    | Yes  | File descriptor, which can be obtained using [fileIo.open](../apis-core-file-kit/js-apis-file-fs.md#fileioopen). |
| offset | number    | No  | Offset from which the data is read, in bytes. The default value is **0**.                                              |
| length | number    | No  | Length of the data to read, in bytes. By default, the length is the total number of remaining bytes after the offset.                                 |

**Return value**

| Type                    | Description                      |
|-----------------------|-------------------------|
| Promise&lt;string&gt; | Promise used to return the URI of the tone in the tone library. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Media Error Codes](../apis-media-kit/errorcode-media.md), and [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md).

| ID   | Error Message              |
|---------| -------------------- |
| 201     | Permission denied. |
| 202     | Caller is not a system application. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102     | Operation is not allowed, e.g. ringtone to add is not customized. |
| 5400103  | I/O error. Possible causes: 1. The target file size exceeds 2 GB; 2. Failed to find the specified file; 3. Ringtone library error. 4. System sound manager service error.|
| 20700004 | Data size exceeds the limit. Note: This error is returned when the file size is between 200MB and 2GB.<br>Applicable version: 20+|
| 20700005 | The number of files exceeds the limit.<br>Applicable version: 20+ |
| 20700006 | Insufficient ROM space.<br>Applicable version: 20+ |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let title = 'test'; // Change to the actual name.
let fileName = 'displayName_test'; // Change to the actual file name.
let categoryValue = systemSoundManager.TONE_CATEGORY_ALARM;

let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
toneAttrs.setTitle(title);
toneAttrs.setFileName(fileName);
toneAttrs.setCategory(categoryValue);

let fd = 10; // Change to the actual ringtone fd.
let offset = 0; // Change to the actual required offset.
let length = 50; // Change to the actual required data length.

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.addCustomizedTone(context, toneAttrs, fd, offset, length).then((value: string) => {
  console.info('Succeeded in doing addCustomizedTone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to addCustomizedTone. Code: ${err.code}, message: ${err.message}`);
});
```

### removeCustomizedTone<sup>12+</sup>

removeCustomizedTone(context: BaseContext, uri: string): Promise&lt;void&gt;

Removes a custom tone from the tone library. This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE_RINGTONE

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name | Type        | Mandatory | Description                                                                                                      |
|-----|-----------| ---- |---------------------------------------------------------------------------------------------------------|
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.                                                                                               |
| uri  | string    | Yes   | Tone URI, which is obtained by using [addCustomizedTone](#addcustomizedtone12) or [getAlarmToneAttrList](#getalarmtoneattrlist12). |

**Return value**

| Type                  | Description                    |
|---------------------|-----------------------|
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID   | Error Message              |
|---------| -------------------- |
| 201     | Permission denied. |
| 202     | Caller is not a system application. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102     | Operation is not allowed, e.g. ringtone of this uri is not customized. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uri = 'file://data/test.wav'; // Change it to the URI of the target ringtone file.

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.removeCustomizedTone(context, uri).then(() => {
  console.info('Succeeded in doing removeCustomizedTone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to removeCustomizedTone. Code: ${err.code}, message: ${err.message}`);
});
```

### getToneHapticsSettings<sup>14+</sup>

getToneHapticsSettings(context: BaseContext, type: ToneHapticsType): Promise&lt;ToneHapticsSettings&gt;

Obtains the haptics settings of the tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name | Type        | Mandatory | Description                                                                          |
|-----|-----------| ---- |----------------------------------------------------------------------------------|
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.   |
| type  | [ToneHapticsType](#tonehapticstype14)    | Yes   | Haptics type of the tone. |

**Return value**

| Type                  | Description                    |
|---------------------|-----------------------|
| Promise&lt;[ToneHapticsSettings](#tonehapticssettings14)&gt; | Promise used to return the haptics settings. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Media Error Codes](../apis-media-kit/errorcode-media.md), and [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |
| 20700003 | Unsupported operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context within the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.ToneHapticsType = systemSoundManager.ToneHapticsType.CALL_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getToneHapticsSettings(context, type).then((value: systemSoundManager.ToneHapticsSettings) => {
  console.info('Succeeded in doing getToneHapticsSettings.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getToneHapticsSettings. Code: ${err.code}, message: ${err.message}`);
});
```

### setToneHapticsSettings<sup>14+</sup>

setToneHapticsSettings(context: BaseContext, type: ToneHapticsType, settings: ToneHapticsSettings): Promise&lt;void&gt;

Sets the haptics settings for the tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name | Type        | Mandatory | Description                                                                          |
|-----|-----------| ---- |----------------------------------------------------------------------------------|
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.   |
| type  | [ToneHapticsType](#tonehapticstype14)    | Yes   | Haptics type of the tone. |
| settings  | [ToneHapticsSettings](#tonehapticssettings14)    | Yes   | Haptics settings of the tone. |

**Return value**

| Type                  | Description                    |
|---------------------|-----------------------|
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Media Error Codes](../apis-media-kit/errorcode-media.md), and [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102 | Operation not allowed. For example, the input URI is not valid. |
| 5400103 | I/O error. |
| 20700003 | Unsupported operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context within the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let type: systemSoundManager.ToneHapticsType = systemSoundManager.ToneHapticsType.CALL_SIM_CARD_0;
let toneHapticsSettings: systemSoundManager.ToneHapticsSettings = {
  mode: systemSoundManager.ToneHapticsMode.NON_SYNC,
  hapticsUri: '/data/storage/el2/base/haptics/synchronized/alarms/test.json', // Change it to the URI obtained through getToneHapticsList.
}

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.setToneHapticsSettings(context, type, toneHapticsSettings).then(() => {
  console.info('Succeeded in doing setToneHapticsSettings.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setToneHapticsSettings. Code: ${err.code}, message: ${err.message}`);
});
```

### getToneHapticsList<sup>14+</sup>

getToneHapticsList(context: BaseContext, isSynced: boolean): Promise&lt;ToneHapticsAttrsArray&gt;

Obtains the haptics attributes of the tone in sync or non-sync mode. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name | Type        | Mandatory | Description                                                                          |
|-----|-----------| ---- |----------------------------------------------------------------------------------|
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.   |
| isSynced  | boolean    | Yes   | Whether the haptics feedback is synchronized with the tone. **true** if synchronized, **false** otherwise. |

**Return value**

| Type                  | Description                    |
|---------------------|-----------------------|
| Promise&lt;[ToneHapticsAttrsArray](#tonehapticsattrsarray14)&gt; | Promise used to return the haptics attributes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Media Error Codes](../apis-media-kit/errorcode-media.md), and [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400103 | I/O error. |
| 20700003 | Unsupported operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context within the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getToneHapticsList(context, false).then((value: systemSoundManager.ToneHapticsAttrsArray) => {
  console.info('Succeeded in doing getToneHapticsList.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getToneHapticsList. Code: ${err.code}, message: ${err.message}`);
});
```

### getHapticsAttrsSyncedWithTone<sup>14+</sup>

getHapticsAttrsSyncedWithTone(context: BaseContext, toneUri: string): Promise&lt;ToneHapticsAttrs&gt;

Obtains the attributes of the haptics feedback synchronized with the tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name | Type        | Mandatory | Description                                                                          |
|-----|-----------| ---- |----------------------------------------------------------------------------------|
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.   |
| toneUri  | string    | Yes   | URI of the tone. The URI can be obtained by calling [getRingtoneAttrList](#getringtoneattrlist12) or [getSystemToneAttrList](#getsystemtoneattrlist12). |

**Return value**

| Type                  | Description                    |
|---------------------|-----------------------|
| Promise&lt;[ToneHapticsAttrs](#tonehapticsattrs14)&gt; | Promise used to return the haptics attributes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Media Error Codes](../apis-media-kit/errorcode-media.md), and [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md).

| ID   | Error Message              |
|---------| -------------------- |
| 202     | Caller is not a system application. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102 | Operation not allowed. For example, the input URI is not used for tones. |
| 5400103 | I/O error. |
| 20700003 | Unsupported operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns a UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let toneUri: string = '/data/storage/el2/base/RingTone/alarms/test.ogg'; // Change it to the actual ringtone URI.

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getHapticsAttrsSyncedWithTone(context, toneUri).then((value: systemSoundManager.ToneHapticsAttrs) => {
  console.info('Succeeded in doing getHapticsAttrsSyncedWithTone.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getHapticsAttrsSyncedWithTone. Code: ${err.code}, message: ${err.message}`);
});
```

### openToneHaptics<sup>14+</sup>

openToneHaptics(context: BaseContext, hapticsUri: string): Promise&lt;number&gt;

Enables haptics for the tone. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type       | Mandatory | Description                                                                                  |
| -------- | ---------| ---- |-------------------------------------------------------------------------------------|
| context  | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes   | Application context.           |
| hapticsUri      | string   | Yes   | URI of the haptics resource. For details about supported resources, see [media.AVPlayer](../apis-media-kit/arkts-apis-media-AVPlayer.md). |

**Return value**

| Type                    | Description             |
|-----------------------|----------------|
| Promise&lt;number&gt; | Promise used to return the FD. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Media Error Codes](../apis-media-kit/errorcode-media.md), and [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 5400102 | Operation not allowed. For example, the input URI is not one for haptics. |
| 5400103 | I/O error. |
| 20700003 | Unsupported operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component, and ensure that this.getUIContext().getHostContext() returns UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let hapticsUri = '/data/storage/el2/base/haptics/synchronized/alarms/test.json'; // Change it to the URI of the target system ringtone sound vibration.

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.openToneHaptics(context, hapticsUri).then((value: number) => {
  console.info('Succeeded in doing openToneHaptics.');
}).catch((err: BusinessError) => {
  console.error(`Failed to openToneHaptics. Code: ${err.code}, message: ${err.message}`);
});
```

### getCurrentRingtoneAttribute<sup>20+</sup>

getCurrentRingtoneAttribute(type: RingtoneType): Promise&lt;ToneAttrs&gt;

Obtains the attributes of the ringtone in use. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type                                  | Mandatory | Description                         |
| -------- |-------------------------------------| ---- | --------------------------- |
| type     |[RingtoneType](#ringtonetype)        | Yes   | Type of the ringtone.  |

**Return value**

| Type                    | Description             |
|-----------------------|----------------|
| Promise&lt;[ToneAttrs](#toneattrs12)&gt; | Promise used to return the attributes of the default ringtone. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](../apis-media-kit/errorcode-media.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 5400103 | I/O error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;

let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();
systemSoundManagerInstance.getCurrentRingtoneAttribute(type).then((value: systemSoundManager.ToneAttrs) => {
  console.info('Succeeded in doing getCurrentRingtoneAttribute.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getCurrentRingtoneAttribute. Code: ${err.code}, message: ${err.message}`);
});
```

### openToneList<sup>20+</sup>

openToneList(uriList: Array\<string>): Promise\<Array\<[string, number, SystemSoundError]>>

Obtains an array of attributes of ringtones. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type       | Mandatory | Description                    |
| -------- | ---------| ---- |-----------------------|
| uriList  | Array\<string>| Yes   | URI list of the ringtones. The number of URIs cannot exceed 1024.           |

**Return value**

| Type                    | Description             |
|-----------------------|----------------|
| Promise\<Array\<[string, number, [SystemSoundError](#systemsounderror20)]>> | Promise used to return the result. The first parameter in the array is **uri**, the second parameter is **fd**, and the third parameter is the result of opening that URI. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md).

| ID | Error Message              |
| ------- | --------------------- |
| 202 | Caller is not a system application. |
| 20700007 | Parameter is invalid, e.g. the length of uriList is too long. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;
let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();

systemSoundManagerInstance.getCurrentRingtoneAttribute(type).then((toneAttrs) => {
  console.info('Succeeded in getting current ringtone attribute.');
  systemSoundManagerInstance.openToneList([toneAttrs.getUri()]).then((value) => {
    console.info('Succeeded in opening tone list.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to open tone list. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to get current ringtone attribute. Code: ${err.code}, message: ${err.message}`);
});
```

### removeCustomizedToneList<sup>20+</sup>

removeCustomizedToneList(uriList: Array\<string>): Promise\<Array\<[string, SystemSoundError]>>

Removes a list of custom tones in batch. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.WRITE_RINGTONE

**System capability**: SystemCapability.Multimedia.SystemSound.Core

**Parameters**

| Name   | Type       | Mandatory | Description                               |
| -------- | ---------| ---- |----------------------------------|
| uriList  | Array\<string>| Yes   | URI list of the ringtones. The number of URIs cannot exceed 1024.           |

**Return value**

| Type                    | Description             |
|-----------------------|----------------|
| Promise\<Array\<[string, [SystemSoundError](#systemsounderror20)]>> | Promise used to return the result. The first parameter in the array is **uri**, and the second parameter is the result of removing that URI. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ringtone Error Codes](./errorcode-audio-ringtone-sys.md).

| ID | Error Message              |
| ------- | --------------------- |
| 201     | Permission denied. |
| 202 | Caller is not a system application. |
| 20700007 | Parameter is invalid, e.g. the length of uriList is too long. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let type: systemSoundManager.RingtoneType = systemSoundManager.RingtoneType.RINGTONE_TYPE_SIM_CARD_0;
let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();

systemSoundManagerInstance.getCurrentRingtoneAttribute(type).then((toneAttrs) => {
  console.info('Succeeded in getting current ringtone attribute.');
  systemSoundManagerInstance.removeCustomizedToneList([toneAttrs.getUri()]).then((value) => {
    console.info('Succeeded in using removeCustomizedToneList function.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to use removeCustomizedToneList function. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to get current ringtone attribute. Code: ${err.code}, message: ${err.message}`);
});
```

## RingtonePlayer

type RingtonePlayer = _RingtonePlayer

Defines a ringtone player.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Type              |Description     |
|-----------------|-------|
| [_RingtonePlayer](js-apis-inner-multimedia-ringtonePlayer-sys.md#ringtoneplayer) | Ringtone player. |

## SystemTonePlayer<sup>11+</sup>

type SystemTonePlayer = _SystemTonePlayer

Defines a system tone player.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Type              | Description        |
|-----------------|-----------|
| [_SystemTonePlayer](js-apis-inner-multimedia-systemTonePlayer-sys.md#systemtoneplayer) | System tone player. |

## RingtoneOptions

type RingtoneOptions = _RingtoneOptions

Defines the configuration of a ringtone player.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Type              | Description          |
|-----------------|-------------|
| [_RingtoneOptions](js-apis-inner-multimedia-ringtonePlayer-sys.md#ringtoneoptions) | Defines the configuration of a ringtone player. |

## SystemToneOptions<sup>11+</sup>

type SystemToneOptions = _SystemToneOptions

Defines the configuration of a system tone player.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.SystemSound.Core

| Type              | Description            |
|-----------------|---------------|
| [_SystemToneOptions](js-apis-inner-multimedia-systemTonePlayer-sys.md#systemtoneoptions) | Defines the configuration of a system tone player. |



