# Deprecated Interface (AudioRecorder, deprecated)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_dyOv3Sds-->
<!--Designer: @chris2981-->
<!--Tester: @xchaosioda-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=28c126b79801cdb1d291c8555229ca840635634a translatedAt=2026-09-15T14:12:38.061Z pushedAt=2026-09-17T11:21:11.720Z -->

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [AVRecorder](arkts-apis-media-AVRecorder.md) instead.

**AudioRecorder** is a class for audio recording management. It provides APIs to record audio. It supports operations such as preparing, starting, pausing, resuming, stopping, releasing, and resetting audio recording. The APIs of this class are applicable to scenarios where audio needs to be recorded, such as voice notes, call recording, and music recording. Before calling any API in **AudioRecorder**, you must use [createAudioRecorder()](arkts-apis-media-f.md#mediacreateaudiorecorderdeprecated) to create an **AudioRecorder** instance.

## Modules to Import

```ts
import { media } from '@kit.MediaKit';
```

## prepare<sup>(deprecated)</sup>

prepare(config: AudioRecorderConfig): void

Prepares for recording. This method can be used to initialize recording resources (including the encoder, sampling rate, and number of audio channels) based on the input configuration parameters.

> **NOTE**
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [AVRecorder.prepare](arkts-apis-media-AVRecorder.md#prepare9) instead.

**Required permissions:** ohos.permission.MICROPHONE

**System capability**: SystemCapability.Multimedia.Media.AudioRecorder

**Parameters**

| Name| Type                                       | Mandatory| Description                                                        |
| ------ | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| config | [AudioRecorderConfig](arkts-apis-media-i.md#audiorecorderconfigdeprecated) | Yes | Audio recording parameters, including the audio output URI, encoding format, sample rate, audio channel count, and output format. |

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message             |
| -------- | --------------------- |
| 201      | permission denied. <br>Applicable versions: 12+     |

**Example**

```ts
let audioRecorderConfig: media.AudioRecorderConfig = {
  audioEncoder : media.AudioEncoder.AAC_LC,
  audioEncodeBitRate : 64000,
  audioSampleRate : 44100,
  numberOfChannels : 2,
  format : media.AudioOutputFormat.AAC_ADTS,
  uri : 'fd://1',       // The file descriptor is obtained through fs.open(). The file must be created by the caller and granted with proper permissions.
  location : { latitude : 30, longitude : 130},
};
audioRecorder.on('prepare', () => {    // Set the 'prepare' event callback.
  console.info('prepare called');
});
audioRecorder.prepare(audioRecorderConfig);
```

## start<sup>(deprecated)</sup>

start(): void

Starts recording. This API can be called only after the **prepare()** API is called.

> **NOTE**
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [AVRecorder.start](arkts-apis-media-AVRecorder.md#start9) instead.

**System capability**: SystemCapability.Multimedia.Media.AudioRecorder

**Example**

```ts
audioRecorder.on('start', () => {    // Set the 'start' event callback.
  console.info('audio recorder start called');
});
audioRecorder.start();
```

## pause<sup>(deprecated)</sup>

pause():void

Pauses recording. This API can be called only after the **start()** API is called.

> **NOTE**
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [AVRecorder.pause](arkts-apis-media-AVRecorder.md#pause9) instead.

**System capability**: SystemCapability.Multimedia.Media.AudioRecorder

**Example**

```ts
audioRecorder.on('pause', () => {    // Set the 'pause' event callback.
  console.info('audio recorder pause called');
});
audioRecorder.pause();
```

## resume<sup>(deprecated)</sup>

resume():void

Resumes recording. This API can be called only after the **pause()** API is called.

> **NOTE**
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [AVRecorder.resume](arkts-apis-media-AVRecorder.md#resume9) instead.

**System capability**: SystemCapability.Multimedia.Media.AudioRecorder

**Example**

```ts
audioRecorder.on('resume', () => {    // Set the 'resume' event callback.
  console.info('audio recorder resume called');
});
audioRecorder.resume();
```

## stop<sup>(deprecated)</sup>

stop(): void

Stops recording and saves the recorded audio data to a file. This API can be called only after the **start()** API is called.

> **NOTE**
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [AVRecorder.stop](arkts-apis-media-AVRecorder.md#stop9) instead.

**System capability**: SystemCapability.Multimedia.Media.AudioRecorder

**Example**

```ts
audioRecorder.on('stop', () => {    // Set the 'stop' event callback.
  console.info('audio recorder stop called');
});
audioRecorder.stop();
```

## release<sup>(deprecated)</sup>

release(): void

Releases recording resources. After the resources are released, other recording methods cannot be called.

> **NOTE**
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [AVRecorder.release](arkts-apis-media-AVRecorder.md#release9) instead.

**System capability**: SystemCapability.Multimedia.Media.AudioRecorder

**Example**

```ts
audioRecorder.on('release', () => {    // Set the 'release' event callback.
  console.info('audio recorder release called');
});
audioRecorder.release();
audioRecorder = undefined;
```

## reset<sup>(deprecated)</sup>

reset(): void

Resets recording.

Before resetting audio recording, you must call **stop()** to stop recording. After audio recording is reset, you must call **prepare()** to set the recording configurations for another recording.

> **NOTE**
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [AVRecorder.reset](arkts-apis-media-AVRecorder.md#reset9) instead.

**System capability**: SystemCapability.Multimedia.Media.AudioRecorder

**Example**

```ts
audioRecorder.on('reset', () => {    // Set the 'reset' event callback.
  console.info('audio recorder reset called');
});
audioRecorder.reset();
```

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')<sup>(deprecated)</sup>

on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void

Subscribes to the audio recording events.

> **NOTE**
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [AVRecorder.on('stateChange')](arkts-apis-media-AVRecorder.md#onstatechange9) instead.

**System capability**: SystemCapability.Multimedia.Media.AudioRecorder

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes   | Event type. The following events are supported: 'prepare', 'start', 'pause', 'resume', 'stop', 'release', and 'reset'.<br>-&nbsp;'prepare'&nbsp;: triggered when the **prepare()** API is called and the audio recording parameters are set.<br>-&nbsp;'start'&nbsp;: triggered when the **start()** API is called and audio recording starts.<br>-&nbsp;'pause'&nbsp;: triggered when the **pause()** API is called and audio recording is paused.<br>-&nbsp;'resume'&nbsp;: triggered when the **resume()** API is called and audio recording is resumed.<br>-&nbsp;'stop'&nbsp;: triggered when the **stop()** API is called and audio recording stops.<br>-&nbsp;'release'&nbsp;: triggered when the **release()** API is called and the recording resources are released.<br>-&nbsp;'reset'&nbsp;: triggered when the **reset()** API is called and audio recording is reset. |
| callback | ()=>void | Yes  | Callback invoked when the event is triggered.                                          |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let audioRecorder: media.AudioRecorder = media.createAudioRecorder(); // Create an AudioRecorder instance.
let audioRecorderConfig: media.AudioRecorderConfig = {
  audioEncoder : media.AudioEncoder.AAC_LC,
  audioEncodeBitRate : 64000,
  audioSampleRate : 44100,
  numberOfChannels : 2,
  format : media.AudioOutputFormat.AAC_ADTS,
  uri : 'fd://xx',  // The file descriptor is obtained through fs.open(). The file must be created by the caller and granted with proper permissions.
  location : { latitude : 30, longitude : 130}
};
audioRecorder.on('error', (error: BusinessError) => {  // Set the 'error' event callback.
  console.error(`audio error called, error code: ${error.code}, message: ${error.message}`);
});
audioRecorder.on('prepare', () => {  // Set the 'prepare' event callback.
  console.info('prepare called');
  audioRecorder.start();  // Start recording and trigger the 'start' event callback.
});
audioRecorder.on('start', () => {  // Set the 'start' event callback.
  console.info('audio recorder start called');
});
audioRecorder.on('pause', () => {  // Set the 'pause' event callback.
  console.info('audio recorder pause called');
});
audioRecorder.on('resume', () => {  // Set the 'resume' event callback.
  console.info('audio recorder resume called');
});
audioRecorder.on('stop', () => {  // Set the 'stop' event callback.
  console.info('audio recorder stop called');
});
audioRecorder.on('release', () => {  // Set the 'release' event callback.
  console.info('audio recorder release called');
});
audioRecorder.on('reset', () => {  // Set the 'reset' event callback.
  console.info('audio recorder reset called');
});
audioRecorder.prepare(audioRecorderConfig);  // Set the recording parameters and trigger the 'prepare' event callback.
```

## on('error')<sup>(deprecated)</sup>

on(type: 'error', callback: ErrorCallback): void

Subscribes to the audio recording error event. After an error event is received, you must handle the error, release resources, and exit the current recording.

> **NOTE**
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [AVRecorder.on('error')](arkts-apis-media-AVRecorder.md#onerror9) instead.

**System capability**: SystemCapability.Multimedia.Media.AudioRecorder

**Parameters**

| Name  | Type         | Mandatory| Description                                                        |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| type     | string        | Yes   | Event type, which is **'error'** in this case.<br>This event is triggered when an error occurs during audio recording. |
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | Yes  | Callback invoked when the event is triggered.                                      |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let audioRecorderConfig: media.AudioRecorderConfig = {
  audioEncoder : media.AudioEncoder.AAC_LC,
  audioEncodeBitRate : 22050,
  audioSampleRate : 22050,
  numberOfChannels : 2,
  format : media.AudioOutputFormat.AAC_ADTS,
  uri : 'fd://xx',   // The file descriptor is obtained through fs.open(). The file must be created by the caller and granted with proper permissions.
  location : { latitude : 30, longitude : 130}
};
audioRecorder.on('error', (error: BusinessError) => {  // Set the 'error' event callback.
  console.error(`audio error called, error code: ${error.code}, message: ${error.message}`);
});
audioRecorder.prepare(audioRecorderConfig);  // Set an invalid parameter in prepare and trigger the 'error' event callback.
```