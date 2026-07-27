# Using AudioCapturer for Audio Recording (ArkTs)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

The AudioCapturer is used to record Pulse Code Modulation (PCM) audio data. It is suitable if you have extensive audio development experience and want to implement more flexible recording features.

## Development Guidelines

The full recording process involves creating an AudioCapturer instance, configuring audio recording parameters, starting and stopping recording, and releasing the instance. In this topic, you will learn how to use the AudioCapturer to record audio data. Before the development, you are advised to read [AudioCapturer](../../reference/apis-audio-kit/arkts-apis-audio-AudioCapturer.md) for the API reference.

The figure below shows the state changes of the AudioCapturer. After an AudioCapturer instance is created, different APIs can be called to switch the AudioCapturer to different states and trigger the required behavior. If an API is called when the AudioCapturer is not in the given state, the system may throw an exception or generate other undefined behavior. Therefore, you are advised to check the AudioCapturer state before triggering state transition.

**Figure 1** AudioCapturer state transition

![AudioCapturer state change](figures/audiocapturer-status-change.png)

You can call **on('stateChange')** to listen for state changes of the AudioCapturer. For details about each state, please refer to [AudioState](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audiostate8).

### How to Develop

The examples in each of the following steps are code snippets. You can click the link at the bottom right of the sample code to obtain the [complete sample codes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS).

1. Set audio recording parameters and create an AudioCapturer instance. For details about the parameters, see [AudioCapturerOptions](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiocaptureroptions8).

   > **NOTE**
   >
   > When the microphone audio source is set ([SourceType](../../reference/apis-audio-kit/arkts-apis-audio-e.md#sourcetype8) is set to **SOURCE_TYPE_MIC**, **SOURCE_TYPE_VOICE_RECOGNITION**, **SOURCE_TYPE_VOICE_COMMUNICATION**, **SOURCE_TYPE_VOICE_MESSAGE**, or **SOURCE_TYPE_LIVE**), the permission ohos.permission.MICROPHONE is required. Note that **SOURCE_TYPE_LIVE** is supported since API version 20. For details about how to apply for the permission, see [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md).

   <!-- @[create_AudioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioCapture.ets) -->
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   // ...
   let audioStreamInfo: audio.AudioStreamInfo = {
     samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // Sampling rate.
     channels: audio.AudioChannel.CHANNEL_2, // Channel.
     sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // Sampling format.
     encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // Encoding format.
   };
   let audioCapturerInfo: audio.AudioCapturerInfo = {
     source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
     capturerFlags: 0 // Flag indicating an AudioCapturer.
   };
   let audioCapturerOptions: audio.AudioCapturerOptions = {
     streamInfo: audioStreamInfo,
     capturerInfo: audioCapturerInfo
   };
   // ...
     audio.createAudioCapturer(audioCapturerOptions, (err, capturer) => { // Create an AudioCapturer instance.
       if (err) {
         console.error(`Invoke createAudioCapturer failed, code is ${err.code}, message is ${err.message}`);
         // ...
         return;
       }
       console.info(`${TAG}: create AudioCapturer success`);
       // ...
       audioCapturer = capturer;
       if (audioCapturer !== undefined) {
         audioCapturer.on('readData', readDataCallback);
         // ...
       }
     });
   ```

2. Call **on('readData')** to subscribe to the audio data read callback.
   > **NOTE**
   > 
   > - **Thread management**: You are advised not to use multiple threads for data reading. If multithreading is necessary for data reading, ensure proper thread management.
   > - **Thread performance**: Do not execute time-consuming tasks in the thread where the **readData** API resides. Failing to do so may delay the data processing thread's response to callbacks, potentially causing issues like missing audio data, lag, and noise.
   > - **Callback registration**: You should avoid registering callbacks on the main thread, as this may cause delayed callback responses and freezes due to blocking by other service processes. You are advised to use an independent asynchronous thread pool to handle callbacks.

   <!-- @[listen_AudioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioCapture.ets) -->
   
   ``` TypeScript
   import { BusinessError } from '@kit.BasicServicesKit';
   import { fileIo as fs } from '@kit.CoreFileKit';
   import { common, abilityAccessCtrl, PermissionRequestResult } from '@kit.AbilityKit';
   // ...
   class Options {
     public offset?: number;
     public length?: number;
   }
   // ...
     let bufferSize: number = 0;
     let path = context.cacheDir;
     let filePath = path + '/StarWars10s-2C-48000-4SW.pcm';
     file = fs.openSync(filePath, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
     readDataCallback = (buffer: ArrayBuffer) => {
       let options: Options = {
         offset: bufferSize,
         length: buffer.byteLength
       }
       fs.writeSync(file.fd, buffer, options);
       bufferSize += buffer.byteLength;
     };
     // ...
         audioCapturer.on('readData', readDataCallback);
   ```

3. Call **start()** to switch the AudioCapturer to the **running** state and start recording.

   <!-- @[start_AudioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioCapture.ets) -->
   
   ``` TypeScript
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
       audioCapturer.start((err: BusinessError) => {
         if (err) {
           // ...
           console.error('Capturer start failed.');
         } else {
           // ...
           console.info('Capturer start success.');
         }
       });
   ```

4. Call **stop()** to stop recording.

   <!-- @[stop_AudioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioCapture.ets) -->
   
   ``` TypeScript
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
       audioCapturer.stop((err: BusinessError) => {
         if (err) {
           // ...
           console.error('Capturer stop failed.');
         } else {
           // ...
           console.info('Capturer stop success.');
         }
       });
   ```

5. Call **release()** to release the instance.

   <!-- @[release_AudioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioCapture.ets) -->
   
   ``` TypeScript
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
       audioCapturer.release((err: BusinessError) => {
         if (err) {
           // ...
           console.error('Capturer release failed.');
         } else {
           fs.closeSync(file);
           console.info('Capturer release success.');
           // ...
         }
       });
   ```

### Complete Sample Code

Refer to the sample code below to record audio using AudioCapturer.

<!-- @[all_audioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioCapture.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';
import { common, abilityAccessCtrl, PermissionRequestResult } from '@kit.AbilityKit';
const TAG = 'AudioCapturerDemo';
class Options {
  public offset?: number;
  public length?: number;
}

let audioCapturer: audio.AudioCapturer | undefined = undefined;
let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // Sampling rate.
  channels: audio.AudioChannel.CHANNEL_2, // Channel.
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // Sampling format.
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // Encoding format.
};
let audioCapturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // Flag indicating an AudioCapturer.
};
let audioCapturerOptions: audio.AudioCapturerOptions = {
  streamInfo: audioStreamInfo,
  capturerInfo: audioCapturerInfo
};
let file: fs.File;
let readDataCallback: Callback<ArrayBuffer>;

// ...

async function initArguments(context: common.UIAbilityContext): Promise<void> {
  let bufferSize: number = 0;
  let path = context.cacheDir;
  let filePath = path + '/StarWars10s-2C-48000-4SW.pcm';
  file = fs.openSync(filePath, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
  readDataCallback = (buffer: ArrayBuffer) => {
    let options: Options = {
      offset: bufferSize,
      length: buffer.byteLength
    }
    fs.writeSync(file.fd, buffer, options);
    bufferSize += buffer.byteLength;
  };
}

// Create an AudioCapturer instance, and set the events to listen for.
async function init(updateCallback?: (msg: string, isError: boolean) => void, stateCallback?:
  (msg: string) => void): Promise<void> {
  audio.createAudioCapturer(audioCapturerOptions, (err, capturer) => { // Create an AudioCapturer instance.
    if (err) {
      console.error(`Invoke createAudioCapturer failed, code is ${err.code}, message is ${err.message}`);
      // ...
      return;
    }
    console.info(`${TAG}: create AudioCapturer success`);
    // ...
    audioCapturer = capturer;
    if (audioCapturer !== undefined) {
      audioCapturer.on('readData', readDataCallback);
      // ...
    }
  });
}

// Start audio recording.
async function start(updateCallback?: (msg: string, isError: boolean) => void): Promise<void> {
  if (audioCapturer !== undefined) {
    let stateGroup = [audio.AudioState.STATE_PREPARED,
      audio.AudioState.STATE_PAUSED, audio.AudioState.STATE_STOPPED];
    // Recording can be started only when the AudioCapturer is in the STATE_PREPARED, STATE_PAUSED, or STATE_STOPPED state.
    if (stateGroup.indexOf(audioCapturer.state.valueOf()) === -1) {
      console.error(`${TAG}: start failed`);
      // ...
      return;
    }

    // Start recording.
    audioCapturer.start((err: BusinessError) => {
      if (err) {
        // ...
        console.error('Capturer start failed.');
      } else {
        // ...
        console.info('Capturer start success.');
      }
    });
  }
}

// Stop recording.
async function stop(updateCallback?: (msg: string, isError: boolean) => void): Promise<void> {
  if (audioCapturer !== undefined) {
    // The AudioCapturer can be stopped only when it is in the STATE_RUNNING or STATE_PAUSED state.
    if (audioCapturer.state.valueOf() !== audio.AudioState.STATE_RUNNING &&
      audioCapturer.state.valueOf() !== audio.AudioState.STATE_PAUSED) {
      console.info('Capturer is not running or paused');
      // ...
      return;
    }

    // Stop recording.
    audioCapturer.stop((err: BusinessError) => {
      if (err) {
        // ...
        console.error('Capturer stop failed.');
      } else {
        // ...
        console.info('Capturer stop success.');
      }
    });
  }
}

// Release the instance.
async function release(updateCallback?: (msg: string, isError: boolean) => void): Promise<void> {
  if (audioCapturer !== undefined) {
    // The AudioCapturer can be released only when it is not in the STATE_RELEASED or STATE_NEW state.
    if (audioCapturer.state.valueOf() === audio.AudioState.STATE_RELEASED ||
      audioCapturer.state.valueOf() === audio.AudioState.STATE_NEW) {
      console.info('Capturer already released');
      // ...
      return;
    }

    // Release the resources.
    audioCapturer.release((err: BusinessError) => {
      if (err) {
        // ...
        console.error('Capturer release failed.');
      } else {
        fs.closeSync(file);
        console.info('Capturer release success.');
        // ...
      }
    });
  }
}

// ...

// ...
```

### Setting the Mute Interruption Mode

To ensure that the recording is not interrupted by the system's focus concurrency rules, a feature is introduced to change the interruption strategy from stopping the recording to simply muting it. You can control this behavior by calling [setWillMuteWhenInterrupted](../../reference/apis-audio-kit/arkts-apis-audio-AudioCapturer.md#setwillmutewheninterrupted20) when creating an AudioCapturer instance. By default, this mode is disabled, and the audio focus strategy manages the order of concurrent audio streams. When enabled, if the recording is interrupted by another application, it will go into a muted state instead of stopping or pausing. In this state, the audio captured is silent.


### Echo Cancellation

Echo cancellation effectively eliminates echo interference during recording on supported devices, thereby improving audio capture quality. You can enable this feature by specifying particular microphone audio [source types](../../reference/apis-audio-kit/arkts-apis-audio-e.md#sourcetype8) (**SOURCE_TYPE_VOICE_COMMUNICATION** or **SOURCE_TYPE_LIVE**). Once enabled, the system automatically processes the captured audio signal to cancel echoes.

Before enabling this feature, you are advised to call [isAcousticEchoCancelerSupported](../../reference//apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#isacousticechocancelersupported20) to check whether the device supports echo cancellation for the audio input [source type](../../reference/apis-audio-kit/arkts-apis-audio-e.md#sourcetype8). (This API is available since API version 20.) If supported, you can activate the echo cancellation processing by setting the corresponding microphone audio source when creating the audio capturer.
