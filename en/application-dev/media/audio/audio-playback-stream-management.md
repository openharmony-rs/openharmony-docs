# Audio Playback Stream Management
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

An audio playback application must notice audio stream state changes and perform corresponding operations. For example, when detecting that an audio stream is being played or paused, the application must change the UI display of the **Play** button.

The examples in each of the following steps are code snippets. You can click the link at the bottom right of the sample code to obtain the [complete sample codes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS).

## Reading or Listening for Audio Stream State Changes in the Application

Create an **AudioRenderer** by referring to [Using AudioRenderer for Audio Playback (ArkTs)](using-audiorenderer-for-playback.md) or [audio.createAudioRenderer](../../reference/apis-audio-kit/arkts-apis-audio-f.md#audiocreateaudiorenderer8). Then obtain the audio stream state changes in either of the following ways.

- Obtain the [property](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#properties) state of the **AudioRenderer**.

  <!-- @[check_renderstate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
  
  ``` TypeScript
  import { audio } from '@kit.AudioKit';
  // ...
      let audioRendererState: audio.AudioState = audioRenderer.state;
      console.info(`Current state is: ${audioRendererState }`);
  ```

- Register **stateChange** to listen for state changes of the AudioRenderer.

  <!-- @[regist_listeningrendererchange](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
  
  ``` TypeScript
  import { audio } from '@kit.AudioKit';
  // ...
      audioRenderer.on('stateChange', (rendererState: audio.AudioState) => {
        console.info(`State change to: ${rendererState}`);
        // ...
      });
  ```

The application then performs an operation, for example, changing the display of the **Play** button, by comparing the obtained state with [AudioState](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audiostate8).

## Reading or Listening for Changes in All Audio Streams

If an application needs to obtain the change information about all audio streams, it can use **AudioStreamManager** to read or listen for the changes of all audio streams.

<!--Del-->
> **NOTE**
> 
> The audio stream change information marked as the system API can be viewed only by system applications.
<!--DelEnd-->

The figure below shows the call relationship of audio stream management.

![Call relationship of audio stream management](figures/audio-stream-mgmt-invoking-relationship.png)

During application development, you must call [getStreamManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioManager.md#getstreammanager9) to create an **AudioStreamManager** instance, through which you can manage audio streams.

For details about the APIs, see [AudioStreamManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md).

## How to Develop

1. Create an **AudioStreamManager** instance.

   <!-- @[create_streammanager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   // ...
   let audioManager = audio.getAudioManager();
   // ...
   let audioStreamManager = audioManager.getStreamManager();
   ```

2. Use [on('audioRendererChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#onaudiorendererchange9) to listen for audio playback stream changes. If the application needs to receive a notification when the audio playback stream state or device changes, it can subscribe to this event.

   <!-- @[regist_renderchangechallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   // ...
     audioStreamManager.on('audioRendererChange',  (audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
       for (let i = 0; i < audioRendererChangeInfoArray.length; i++) {
         let audioRendererChangeInfo = audioRendererChangeInfoArray[i];
         console.info(`## RendererChange on is called for ${i} ##`);
         console.info(`StreamId for ${i} is: ${audioRendererChangeInfo.streamId}`);
         console.info(`Content ${i} is: ${audioRendererChangeInfo.rendererInfo.content}`);
         console.info(`Stream ${i} is: ${audioRendererChangeInfo.rendererInfo.usage}`);
         console.info(`Flag ${i} is: ${audioRendererChangeInfo.rendererInfo.rendererFlags}`);
         // ...
         for (let j = 0;j < audioRendererChangeInfo.deviceDescriptors.length; j++) {
           console.info(`Id: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].id}`);
           console.info(`Type: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].deviceType}`);
           console.info(`Role: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].deviceRole}`);
           console.info(`Name: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].name}`);
           console.info(`Address: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].address}`);
           console.info(`SampleRates: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].sampleRates[0]}`);
           console.info(`ChannelCount ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].channelCounts[0]}`);
           console.info(`ChannelMask: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].channelMasks}`);
         }
       }
     });
   ```

3. (Optional) Use [off('audioRendererChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#offaudiorendererchange9) to cancel listening for audio playback stream changes.

   <!-- @[unregist_renderchangechallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
 
   ``` TypeScript
   audioStreamManager.off('audioRendererChange');
   console.info('RendererChange Off is called ');
   ```

4. (Optional) Use [getCurrentAudioRendererInfoArray](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#getcurrentaudiorendererinfoarray9) to obtain the information about all audio playback streams. This API can be used to obtain the unique ID of the audio playback stream, audio renderer information, and audio playback device information.

   > **NOTE**
   >
   > Before listening for state changes of all audio streams, the application must [declare the ohos.permission.USE_BLUETOOTH permission](../../security/AccessToken/declare-permissions.md), for the device name and device address (Bluetooth related attributes) to be displayed correctly.

   <!-- @[get_allstreaminfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   // ...
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
   async function getCurrentAudioRendererInfoArray(): Promise<void> {
     await audioStreamManager.getCurrentAudioRendererInfoArray()
       .then((audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
         console.info(`getCurrentAudioRendererInfoArray  Get Promise is called `);
         // ...
         if (audioRendererChangeInfoArray != null) {
           for (let i = 0; i < audioRendererChangeInfoArray.length; i++) {
             let audioRendererChangeInfo = audioRendererChangeInfoArray[i];
             console.info(`StreamId for ${i} is: ${audioRendererChangeInfo.streamId}`);
             console.info(`Content ${i} is: ${audioRendererChangeInfo.rendererInfo.content}`);
             console.info(`Stream ${i} is: ${audioRendererChangeInfo.rendererInfo.usage}`);
             console.info(`Flag ${i} is: ${audioRendererChangeInfo.rendererInfo.rendererFlags}`);
             // ...
             for (let j = 0;j < audioRendererChangeInfo.deviceDescriptors.length; j++) {
               console.info(`Id: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].id}`);
               console.info(`Type: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].deviceType}`);
               console.info(`Role: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].deviceRole}`);
               console.info(`Name: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].name}`);
               console.info(`Address: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].address}`);
               console.info(`SampleRates: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].sampleRates[0]}`);
               console.info(`ChannelCount ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].channelCounts[0]}`);
               console.info(`ChannelMask: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].channelMasks}`);
             }
           }
         }
       }).catch((err: BusinessError ) => {
         console.error(`Invoke getCurrentAudioRendererInfoArray failed, code is ${err.code}, message is ${err.message}`);
         // ...
       });
   }
   ```
