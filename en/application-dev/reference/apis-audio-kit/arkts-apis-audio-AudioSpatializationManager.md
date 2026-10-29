# Interface (AudioSpatializationManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @tom_guo-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=59c3fabc0701f94b960b606856aa3cc084316830 translatedAt=2026-10-08T12:04:46.728Z pushedAt=2026-10-12T06:59:26.500Z -->

**AudioSpatializationManager** is a spatial audio management module in the audio system. This module provides the spatial audio rendering capability, including enabling or disabling spatial audio rendering on the current device and listening for changes in the spatial audio rendering status. When you need to use the spatial audio technology to enhance audio experience, you can use the APIs in this module to perform related operations. This module is applicable to scenarios such as audio and video playback and gaming.

Before calling any API in AudioSpatializationManager, you must use [getSpatializationManager](arkts-apis-audio-AudioManager.md#getspatializationmanager18) to obtain an AudioSpatializationManager instance.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 18.

## Modules to Import

```ts
import { audio } from '@kit.AudioKit';
```

## isSpatializationEnabledForCurrentDevice<sup>18+</sup>

isSpatializationEnabledForCurrentDevice(): boolean

Checks whether spatial audio rendering is enabled for the current device. This API returns the result synchronously.

**System capability**: SystemCapability.Multimedia.Audio.Spatialization

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| boolean | Check result for whether spatial audio rendering is enabled. **true** if enabled, **false** otherwise.|

**Example**

```ts
let isSpatializationEnabledForCurrentDevice: boolean = audioSpatializationManager.isSpatializationEnabledForCurrentDevice();

console.info(`Succeeded in checking whether spatialization is enabled for the current device, isSpatializationEnabledForCurrentDevice: ${isSpatializationEnabledForCurrentDevice}.`);
```

## on('spatializationEnabledChangeForCurrentDevice')<sup>18+</sup>

on(type: 'spatializationEnabledChangeForCurrentDevice', callback: Callback<boolean\>): void

Subscribes to the spatial audio rendering status change event of the current device. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Spatialization

**Parameters**

| Name  | Type                                                | Mandatory| Description                                          |
| :------- | :--------------------------------------------------- | :--- |:---------------------------------------------|
| type     | string | Yes  | Event type. The event **'spatializationEnabledChangeForCurrentDevice'** is triggered when the spatial audio rendering status is changed.|
| callback | Callback<boolean\> | Yes | Callback used to return the result, indicating whether spatial audio rendering is enabled. **true** if enabled, and **false** otherwise. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
audioSpatializationManager.on('spatializationEnabledChangeForCurrentDevice', (isSpatializationEnabledForCurrentDevice: boolean) => {
  console.info(`Spatialization enabled for current device changed, isSpatializationEnabledForCurrentDevice: ${isSpatializationEnabledForCurrentDevice}.`);
});
```

## off('spatializationEnabledChangeForCurrentDevice')<sup>18+</sup>

off(type: 'spatializationEnabledChangeForCurrentDevice', callback?: Callback<boolean\>): void

Unsubscribes from the spatial audio rendering status change event of the current device.

**System capability**: SystemCapability.Multimedia.Audio.Spatialization

**Parameters**

| Name  | Type                                               | Mandatory| Description                                      |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string | Yes   | Event type. This field has a fixed value of **'spatializationEnabledChangeForCurrentDevice'**. |
| callback | Callback<boolean\> | No   | Callback used to return the result. If a callback is passed, only the listener for events corresponding to this callback will be unregistered. The callback must be the same as that bound to [on('spatializationEnabledChangeForCurrentDevice')](#onspatializationenabledchangeforcurrentdevice18). If no parameter is passed, all listeners for events of this event type will be unregistered. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
// Cancel all listeners for this event.
audioSpatializationManager.off('spatializationEnabledChangeForCurrentDevice');

// For the same listening event, the callback parameter passed to the on and off methods must be the same. The off method cancels the listener subscribed by the corresponding on method.
let spatializationEnabledChangeForCurrentDeviceCallback = (enabled: boolean) => {
  console.info(`Spatialization enabled for current device changed, enabled: ${enabled}.`);
};

audioSpatializationManager.on('spatializationEnabledChangeForCurrentDevice', spatializationEnabledChangeForCurrentDeviceCallback);

audioSpatializationManager.off('spatializationEnabledChangeForCurrentDevice', spatializationEnabledChangeForCurrentDeviceCallback);
```
