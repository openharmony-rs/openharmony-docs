# Querying and Listening for the Recording Status of Other Applications
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

An audio recording application must notice audio stream state changes and perform corresponding operations. For example, when detecting that the user stops recording, the application must notify the user that the recording finishes.

The examples in each of the following steps are code snippets. You can click the link at the bottom right of the sample code to obtain the [complete sample codes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS).

## Reading or Listening for Audio Stream State Changes in the Application

Create an **AudioCapturer** by referring to [Using AudioCapturer for Audio Recording (ArkTs)](using-audiocapturer-for-recording.md) or [audio.createAudioCapturer](../../reference/apis-audio-kit/arkts-apis-audio-f.md#audiocreateaudiocapturer8). Then obtain the audio stream state changes in either of the following ways.

- Obtain the [property](../../reference/apis-audio-kit/arkts-apis-audio-AudioCapturer.md#properties) state of the **AudioCapturer**.

  <!-- @[view_AudioCapturerState](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioCapture.ets) -->

  ``` TypeScript
  let audioCapturerState: audio.AudioState = audioCapturer.state;
  console.info(`Current state is: ${audioCapturerState }`)
  ```

- Register **stateChange** to listen for state changes of the AudioCapturer.

  <!-- @[listen_AudioCapturerState](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioCapture.ets) -->
  
  ``` TypeScript
  audioCapturer.on('stateChange', (capturerState: audio.AudioState) => {
    console.info(`State change to: ${capturerState}`)
    // ...
  });
  ```

The application then performs an operation, for example, displays a message indicating the end of the recording, by comparing the obtained state with [AudioState](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audiostate8).

## Reading or Listening for Changes in All Audio Streams

If an application needs to obtain the change information about all audio streams, it can use **AudioStreamManager** to read or listen for the changes of all audio streams.

<!--Del-->
> **NOTE**
> 
> The audio stream change information marked as the system API can be viewed only by system applications.
<!--DelEnd-->

The figure below shows the call relationship of audio stream management.

![Call relationship of recording stream management](figures/invoking-relationship-recording-stream-mgmt.png)

During application development, you must call [getStreamManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioManager.md#getstreammanager9) to create an **AudioStreamManager** instance, through which you can manage audio streams.

For details about the APIs, see [AudioStreamManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md).

## How to Develop

1. Create an **AudioStreamManager** instance.

   <!-- @[get_StreamManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioStreamManager.ets) -->

   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   let audioManager = audio.getAudioManager();
   let audioStreamManager = audioManager.getStreamManager();
   ```

2. Use [on('audioCapturerChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#onaudiocapturerchange9) to listen for audio recording stream changes. If the application needs to receive a notification when the audio recording stream state or device changes, it can subscribe to this event.

   <!-- @[audioStreamManager_on](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioStreamManager.ets) -->
   
   ``` TypeScript
   audioStreamManager.on('audioCapturerChange', (audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) =>  {
     // ...
     for (let i = 0; i < audioCapturerChangeInfoArray.length; i++) {
       console.info(`## CapChange on is called for element ${i} ##`);
       console.info(`StreamId for ${i} is: ${audioCapturerChangeInfoArray[i].streamId}`);
       console.info(`Source for ${i} is: ${audioCapturerChangeInfoArray[i].capturerInfo.source}`);
       console.info(`Flag  ${i} is: ${audioCapturerChangeInfoArray[i].capturerInfo.capturerFlags}`);
   
       // ...
   
       let devDescriptor: audio.AudioDeviceDescriptors = audioCapturerChangeInfoArray[i].deviceDescriptors;
       for (let j = 0; j < audioCapturerChangeInfoArray[i].deviceDescriptors.length; j++) {
         console.info(`Id: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].id}`);
         console.info(`Type: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].deviceType}`);
         console.info(`Role: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].deviceRole}`);
         console.info(`Name: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].name}`);
         console.info(`Address: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].address}`);
         console.info(`SampleRates: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].sampleRates[0]}`);
         console.info(`ChannelCounts ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].channelCounts[0]}`);
         console.info(`ChannelMask: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].channelMasks}`);
       }
     }
     // ...
   });
   ```

3. (Optional) Use [off('audioCapturerChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#offaudiocapturerchange9) to cancel listening for audio recording stream changes.

   <!-- @[cancel_ListenAudioStreamManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioStreamManager.ets) -->

   ``` TypeScript
   audioStreamManager.off('audioCapturerChange');
   console.info('CapturerChange Off is called');
   ```

4. (Optional) Use [getCurrentAudioCapturerInfoArray](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#getcurrentaudiocapturerinfoarray9) to obtain the information about all audio recording streams. This API can be used to obtain the unique ID of the audio recording stream, audio capturer information, and audio capturer device information.

   > **NOTE**
   > 
   > Before listening for state changes of all audio streams, the application must [declare the ohos.permission.USE_BLUETOOTH permission](../../security/AccessToken/declare-permissions.md), for the device name and device address (Bluetooth related attributes) to be displayed correctly.
   > Starting from API version 20, you can call [isRecordingAvailable](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#isrecordingavailable20) before audio recording starts to determine whether the recording can be successfully started based on the audio source type in the input **AudioCapturer** information.

   <!-- @[get_CurrentAudioCapturerInfoArray](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioStreamManager.ets) -->
   
   ``` TypeScript
   async function getCurrentAudioCapturerInfoArray(updateCallback?:
     (msg: string, isError: boolean) => void): Promise<void>{
     // ...
   
     await audioStreamManager.getCurrentAudioCapturerInfoArray()
       .then((audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) => {
         console.info('getCurrentAudioCapturerInfoArray Get Promise Called');
         let detailInfo = 'getCurrentAudioCapturerInfoArray Get Promise Called\n';
         if (audioCapturerChangeInfoArray != null) {
           for (let i = 0; i < audioCapturerChangeInfoArray.length; i++) {
             console.info(`StreamId for ${i} is: ${audioCapturerChangeInfoArray[i].streamId}`);
             console.info(`Source for ${i} is: ${audioCapturerChangeInfoArray[i].capturerInfo.source}`);
             console.info(`Flag  ${i} is: ${audioCapturerChangeInfoArray[i].capturerInfo.capturerFlags}`);
   
             detailInfo += `StreamId for ${i} is: ${audioCapturerChangeInfoArray[i].streamId}\n`;
             detailInfo += `Source for ${i} is: ${audioCapturerChangeInfoArray[i].capturerInfo.source}\n`;
             detailInfo += `Flag ${i} is: ${audioCapturerChangeInfoArray[i].capturerInfo.capturerFlags}\n`;
   
             for (let j = 0; j < audioCapturerChangeInfoArray[i].deviceDescriptors.length; j++) {
               console.info(`Id: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].id}`);
               console.info(`Type: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].deviceType}`);
               console.info(`Role: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].deviceRole}`);
               console.info(`Name: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].name}`);
               console.info(`Address: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].address}`);
               console.info(`SampleRates: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].sampleRates[0]}`);
               console.info(`ChannelCounts ${i} : ${audioCapturerChangeInfoArray[i]
                 .deviceDescriptors[j].channelCounts[0]}`);
               console.info(`ChannelMask: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].channelMasks}`);
             }
           }
         }
         if (updateCallback) {
           updateCallback(detailInfo, false);
         }
       }).catch((err: BusinessError) => {
         console.error(`Invoke getCurrentAudioCapturerInfoArray failed, code is ${err.code}, message is ${err.message}`);
         const errorMsg = `Invoke getCurrentAudioCapturerInfoArray failed, code is ${err.code}, message is ${err.message}`;
         if (updateCallback) {
           updateCallback(errorMsg, true);
         }
       });
     // Unregister the listener after data retrieval.
     cancelListenAudioStreamManager();
   }
   ```
