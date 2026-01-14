# Audio Playback Stream Management
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

An audio playback application must notice audio stream state changes and perform corresponding operations. For example, when detecting that an audio stream is being played or paused, the application must change the UI display of the **Play** button.

## Reading or Listening for Audio Stream State Changes in the Application

Create an AudioRenderer by referring to [Using AudioRenderer for Audio Playback (ArkTs)](using-audiorenderer-for-playback.md) or [audio.createAudioRenderer](../../reference/apis-audio-kit/arkts-apis-audio-f.md#audiocreateaudiorenderer8). Then obtain the audio stream state changes in either of the following ways.

- Check the [state](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#properties) of the AudioRenderer.
    
  ```ts
  import { audio } from '@kit.AudioKit';
  
  let audioRendererState: audio.AudioState = audioRenderer.state;
  console.info(`Current state is: ${audioRendererState}`);
  ```

- Register **stateChange** to listen for state changes of the AudioRenderer.
    
  ```ts
  import { audio } from '@kit.AudioKit';
  
  audioRenderer.on('stateChange', (rendererState: audio.AudioState) => {
    console.info(`Succeeded in using on function, state change to: ${rendererState}`);
  });
  ```

The application then performs an operation, for example, changing the display of the **Play** button, by comparing the obtained state with [AudioState](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audiostate8).

## Reading or Listening for Changes in All Audio Streams

If an application needs to obtain the change information about all audio streams, it can use AudioStreamManager to read or listen for the changes of all audio streams.

<!--Del-->
> **NOTE**
> 
> The audio stream change information marked as the system API can be viewed only by system applications.
<!--DelEnd-->

The figure below shows the call relationship of audio stream management.

![Call relationship of audio stream management](figures/audio-stream-mgmt-invoking-relationship.png)

During application development, you must call [getStreamManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioManager.md#getstreammanager9) to create an AudioStreamManager instance, through which you can manage audio streams.

For details about the APIs, see [AudioStreamManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md).

## How to Develop

1. Create an AudioStreamManager instance.

   ```ts
   import { audio } from '@kit.AudioKit';
   
   let audioManager = audio.getAudioManager();
   let audioStreamManager = audioManager.getStreamManager();
   ```

2. Use [on('audioRendererChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#onaudiorendererchange9) to listen for audio playback stream changes. If the application needs to receive a notification when the audio playback stream state or device changes, it can subscribe to this event.

   ```ts
   import { audio } from '@kit.AudioKit';
   
   audioStreamManager.on('audioRendererChange',  (audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
     console.info(`Succeeded in using on function. AudioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}`);
   });
   ```

3. (Optional) Use [off('audioRendererChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#offaudiorendererchange9) to cancel listening for audio playback stream changes.

   ```ts
   audioStreamManager.off('audioRendererChange');
   console.info('Succeeded in using off function.');
   ```

4. (Optional) Use [getCurrentAudioRendererInfoArray](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#getcurrentaudiorendererinfoarray9) to obtain the information about all audio playback streams. This API can be used to obtain the unique ID of the audio playback stream, audio renderer information, and audio playback device information.

   > **NOTE**
   >
   > Before listening for state changes of all audio streams, the application must [declare the ohos.permission.USE_BLUETOOTH permission](../../security/AccessToken/declare-permissions.md), for the device name and device address (Bluetooth related attributes) to be displayed correctly.

   ```ts
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   async function getCurrentAudioRendererInfoArray(): Promise<void> {
     await audioStreamManager.getCurrentAudioRendererInfoArray().then((audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
       console.info(`Succeeded in getting current audio renderer info array. AudioRendererChangeInfoArray: ${JSON.stringify(audioRendererChangeInfoArray)}`);
     }).catch((err: BusinessError ) => {
       console.error(`Failed to get current audio renderer info array. Code: ${err.code}, message: ${err.message}`);
     });
   }
   ```
