# Interface (AudioSpatializationManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @tom_guo-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=24d41a0bca6541c58a989fa09a384d3cf0eeb920 translatedAt=2026-11-03T03:37:31.200Z pushedAt=2026-11-04T03:11:46.921Z nl=1 -->

AudioSpatializationManager is the spatial audio management module in the audio system. This module provides spatial audio rendering capabilities, including enabling or disabling spatial audio rendering for the current device and listening for changes in the spatial audio rendering switch state. When developers need to use spatial audio technology to enhance the audio experience, they can use the APIs of this module to perform related operations, which are applicable to scenarios such as audio/video playback and gaming.

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
| callback | Callback<boolean\> | Required | Callback invoked when the spatial audio rendering state changes. The value true indicates that spatial audio rendering is enabled, and false indicates that it is disabled. |

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

Unsubscribes from the spatial audio rendering switch state change event of the current device.

**System capability**: SystemCapability.Multimedia.Audio.Spatialization

**Parameters**

| Name  | Type                                               | Mandatory| Description                                      |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string | Yes   | Event callback type. The supported event is 'spatializationEnabledChangeForCurrentDevice'. |
| callback | Callback<boolean\> | No   | Callback for the event. When a callback is passed in, only the listener corresponding to this callback is unsubscribed, and it must be the same callback bound to [on('spatializationEnabledChangeForCurrentDevice')](#onspatializationenabledchangeforcurrentdevice18). When no parameter is passed in, all subscribed listeners of this event type are unsubscribed. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |

**Example**

```ts
// Cancel all listeners of this event.
audioSpatializationManager.off('spatializationEnabledChangeForCurrentDevice');

// For the same listening event, the callback parameter passed to the on and off methods must be the same. The off method cancels the listener subscribed by the corresponding on method.
let spatializationEnabledChangeForCurrentDeviceCallback = (enabled: boolean) => {
  console.info(`Spatialization enabled for current device changed, enabled: ${enabled}.`);
};

audioSpatializationManager.on('spatializationEnabledChangeForCurrentDevice', spatializationEnabledChangeForCurrentDeviceCallback);

audioSpatializationManager.off('spatializationEnabledChangeForCurrentDevice', spatializationEnabledChangeForCurrentDeviceCallback);
```
