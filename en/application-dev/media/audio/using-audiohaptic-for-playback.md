# Using AudioHaptic for Audio-Haptic Playback (ArkTs)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

**AudioHaptic** provides APIs for audio-haptic playback and management. It applies to scenarios where haptic feedback needs to be initiated synchronously during audio playback, for example, when there are incoming calls or messages or users are typing.

## Development Guidelines

The entire process of audio-haptic development involves management of audio and haptic sources, configuration of an audio latency mode and audio stream usage, and creation and management of an audio-haptic player. This topic uses the process of one-time audio-haptic playback as an example to describe how to use **AudioHaptic**. Before the development, read [AudioHaptic](../../reference/apis-audio-kit/js-apis-audioHaptic.md#audiohapticmanager) for better understanding.

### Requesting Permissions

If the audio-haptic player needs to trigger vibration, check whether the application has the permission **ohos.permission.VIBRATE**.

1. [Declare the permission](../../security/AccessToken/declare-permissions.md).
2. [Request user authorization](../../security/AccessToken/request-user-authorization.md).

### How to Develop

The examples in each of the following steps are code snippets. You can click the link at the bottom right of the sample code to obtain the [complete sample codes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS).

1. Obtain an **AudioHapticManager** instance, and register the audio and haptic sources. For details about the sources supported, see [AudioHapticManager](../../reference/apis-audio-kit/js-apis-audioHaptic.md#audiohapticmanager).

   > **NOTE**
   >
   > You can register resources using one of the following methods:
   > - Method 1: Use the [registerSource](../../reference/apis-audio-kit/js-apis-audioHaptic.md#registersource) API to register resources through file URIs.
   > - Method 2 (recommended): Use [registerSourceFromFd](../../reference/apis-audio-kit/js-apis-audioHaptic.md#registersourcefromfd20) to register resources through file descriptors. This API is available from API version 20,

   <!-- @[get_haptic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/haptic.ets) -->
   
   ``` TypeScript
   import { audio, audioHaptic } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';
   
   let audioHapticManagerInstance: audioHaptic.AudioHapticManager = audioHaptic.getAudioHapticManager();
   
   // A maximum of 128 resources can be registered at the same time for an application. Any attempt to register beyond this limit will fail (returning a negative resource ID).
   // You are advised to reasonably manage the number of registered resources. For resources that are no longer used, unregister them in a timely manner.

   // ...
     // Method 1: Use registerSource to register sources.
     let audioUri = 'data/audioTest.wav'; // This is only an example. In actual use, replace the file with the URI of your target audio resource.
     let hapticUri = 'data/hapticTest.json'; // This is only an example. In actual use, replace the file with the URI of your target haptic resource.
     let idForUri = 0;
   
     audioHapticManagerInstance.registerSource(audioUri, hapticUri).then((value: number) => {
       console.info(`Promise returned to indicate that the source id of the registered source ${value}.`);
       idForUri = value;
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to register source ${err}`);
       // ...
     });
     // ...
     // Method 2: Use registerSourceFromFd to register resources.
     // This is only an example. In actual use, replace the file with that in the rawfile directory of the application.
     let audioFile = context.resourceManager.getRawFdSync('audioTest.ogg');
     let audioFd: audioHaptic.AudioHapticFileDescriptor = {
       fd: audioFile.fd,
       offset: audioFile.offset,
       length: audioFile.length,
     };
     // This is only an example. In actual use, replace the file with that in the rawfile directory of the application.
     let hapticFile = context.resourceManager.getRawFdSync('hapticTest.json');
     let hapticFd: audioHaptic.AudioHapticFileDescriptor = {
       fd: hapticFile.fd,
       offset: hapticFile.offset,
       length: hapticFile.length,
     };
     audioHapticManagerInstance.registerSourceFromFd(audioFd, hapticFd).then((value: number) => {
       console.info('Succeeded in doing registerSourceFromFd.');
       idForFd = value;
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to registerSourceFromFd. Code: ${err.code}, message: ${err.message}`);
       // ...
     });
   ```

2. Set the parameters of an audio-haptic player. For details, see [AudioHapticManager](../../reference/apis-audio-kit/js-apis-audioHaptic.md#audiohapticmanager).

   <!-- @[set_hapticparam](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/haptic.ets) -->

   ``` TypeScript
   let latencyMode: audioHaptic.AudioLatencyMode = audioHaptic.AudioLatencyMode.AUDIO_LATENCY_MODE_FAST;
   audioHapticManagerInstance.setAudioLatencyMode(idForFd, latencyMode);

   let usage: audio.StreamUsage = audio.StreamUsage.STREAM_USAGE_NOTIFICATION;
   audioHapticManagerInstance.setStreamUsage(idForFd, usage);
   ```

3. Create an AudioHapticPlayer instance.

   <!-- @[create_haptic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/haptic.ets) -->
   
   ``` TypeScript
   let options: audioHaptic.AudioHapticPlayerOptions = {muteAudio: false, muteHaptics: false};
   let audioHapticPlayer: audioHaptic.AudioHapticPlayer | undefined = undefined;
   // ...
     audioHapticManagerInstance.createPlayer(idForFd, options).then((value: audioHaptic.AudioHapticPlayer) => {
       console.info(`Create the audio haptic player successfully.`);
       audioHapticPlayer = value;
       // ...
     }).catch((err: BusinessError) => {
       console.error(`Failed to create player ${err}`);
       // ...
     });
   ```

4. Call **start()** to start the audio-haptic player.

   <!-- @[haptic_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/haptic.ets) -->
   
   ``` TypeScript
   audioHapticPlayer.start().then(() => {
     console.info(`Promise returned to indicate that start playing successfully.`);
     // ...
   }).catch((err: BusinessError) => {
     console.error(`Failed to start playing. ${err}`);
     // ...
   });
   ```

5. Call **stop()** to stop the audio-haptic player.

   <!-- @[haptic_stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/haptic.ets) -->
   
   ``` TypeScript
   audioHapticPlayer.stop().then(() => {
     console.info(`Promise returned to indicate that stop playing successfully.`);
     // ...
   }).catch((err: BusinessError) => {
     console.error(`Failed to stop playing. ${err}`);
     // ...
   });
   ```

6. Release the AudioHapticPlayer instance.

   <!-- @[haptic_release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/haptic.ets) -->
   
   ``` TypeScript
   audioHapticPlayer.release().then(() => {
     console.info(`Promise returned to indicate that release the audio haptic player successfully.`);
     // ...
   }).catch((err: BusinessError) => {
     console.error(`Failed to release the audio haptic player. ${err}`);
     // ...
   });
   ```

7. Unregister the audio and haptic sources.

   <!-- @[haptic_unregist](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/haptic.ets) -->
   
   ``` TypeScript
   // For resources that are no longer used, you are advised to unregister them in a timely manner to avoid issues such as resource leaks, exceeding the maximum allowed number of registered resources, or other such issues.
   audioHapticManagerInstance.unregisterSource(idForFd).then(() => {
     console.info(`Promise returned to indicate that unregister source successfully`);
     // ...
   }).catch((err: BusinessError) => {
     console.error(`Failed to unregister source ${err}`);
     // ...
   });
   ```
