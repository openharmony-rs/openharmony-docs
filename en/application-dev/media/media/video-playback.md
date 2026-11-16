# Using AVPlayer to Play Videos (ArkTS)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @chennotfound-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a941c2967fbada19bd502bbb405ec212160e4aac translatedAt=2026-11-09T07:45:33.870Z pushedAt=2026-11-09T08:11:59.274Z nl=1 -->

The system provides two solutions for video playback development:

- [AVPlayer](media-kit-intro.md#avplayer): provides ArkTS and JS APIs to implement audio and video playback. It also supports parsing streaming media and local assets, decapsulating media assets, decoding video, and rendering video. It is applicable to end-to-end playback of media assets and can be used to play video files in MP4 and MKV formats.

- **Video** component: encapsulates basic video playback capabilities. It can be used to play video files after the data source and basic information are set. However, its scalability is poor. This component is provided by ArkUI. For details about how to use this component for video playback development, see [Video Component](../../ui/arkts-common-components-video-player.md).

This section describes how to use AVPlayer to implement video playback. It uses a complete video playback workflow as an example to demonstrate end-to-end playback of media resources.

The full playback process includes creating an AVPlayer instance, setting the media asset to play and the window to display the video, setting playback parameters (volume, speed, and scale type), controlling playback (play, pause, seek, and stop), resetting the playback configuration, and releasing the instance. During application development, you can use the **state** property of AVPlayer to obtain its state or call **on('stateChange')** to listen for state changes. If the application performs an operation when the AVPlayer is not in the given state, the system may throw an exception or generate other undefined behavior.

**Figure 1** Playback state transition

![Playback state change](figures/video-playback-status-change.png)

For details about the states, see [AVPlayerState](../../reference/apis-media-kit/arkts-apis-media-t.md#avplayerstate9). When the AVPlayer is in the **prepared**, **playing**, **paused**, or **completed** state, the playback engine is working and a large amount of RAM is occupied. If your application does not need to use the AVPlayer, call **reset()** or **release()** to release the instance.

## Developer's Tips

This topic describes only how to implement the playback of a media asset. In practice, background playback and playback conflicts may be involved. You can refer to the following description to handle the situation based on your service requirements.

- If you want the application to continue playing the media asset in the background or when the screen is off, use the [AVSession](../avsession/avsession-access-scene.md) and [continuous task](../../task-management/continuous-task.md) to prevent the playback from being forcibly interrupted by the system.
- If the media asset being played involves audio, the playback may be interrupted by other applications based on the system audio management policy. (For details, see [Processing Audio Interruption Events](../audio/audio-playback-concurrency.md).) It is recommended that the player application proactively listen for audio interruption events and handle the events accordingly to avoid the inconsistency between the application status and the expected effect.
- When a device is connected to multiple audio output devices, the application can listen for audio output device changes through [on('audioOutputDeviceChangeWithInfo')](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#onaudiooutputdevicechangewithinfo11) and handle them accordingly.
- To access online media resources, you must request the ohos.permission.INTERNET permission.

## How to Develop

For details about the APIs, see [AVPlayer](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md).

1. Call **createAVPlayer()** to create an AVPlayer instance. The AVPlayer is the idle state.

   <!-- @[createAVPlayer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { media } from '@kit.MediaKit';
   // ...
       // Create an avPlayer instance.
       this.avPlayer = await media.createAVPlayer();
   ```

2. Set the events to listen for, which will be used in the full-process scenario. The table below lists the supported events.
   | Event Type| Description|
   | -------- | -------- |
   | stateChange | Mandatory; used to listen for changes of the **state** property of the AVPlayer.<br>To ensure proper functionality, the listener must be configured when the AVPlayer is in the idle state and before the resource setting API is called. If the listener is set after the resource setting API is called, the stateChange event reported during resource setting may fail to be received.|
   | error | Mandatory; used to listen for AVPlayer errors.<br>To ensure proper functionality, the listener must be configured when the AVPlayer is in the idle state and before the resource setting API is called. If the listener is set after the resource setting API is called, the error event reported during resource setting may fail to be received.|
   | durationUpdate | Used to listen for progress bar updates to refresh the media asset duration.|
   | timeUpdate | Used to listen for the current position of the progress bar to refresh the current time.|
   | seekDone | Used to listen for the completion status of the **seek()** request.<br>This event is reported when the AVPlayer seeks to the playback position specified in **seek()**.|
   | speedDone | Used to listen for the completion status of the **setSpeed()** request.<br>This event is reported when the AVPlayer plays videos at the speed specified in **setSpeed()**.|
   | volumeChange | Used to listen for the completion status of the **setVolume()** request.<br>This event is reported when the AVPlayer plays videos at the volume specified in **setVolume()**.|
   | bitrateDone | Used to listen for the completion status of the **setBitrate()** request, which is used for HTTP Live Streaming (HLS) streams.<br>This event is reported when the AVPlayer plays videos at the bit rate specified in **setBitrate()**.|
   | availableBitrates | Used to listen for available bit rates of HLS resources. The available bit rates are provided for **setBitrate()**.|
   | bufferingUpdate | Used to listen for network playback buffer information.|
   | startRenderFrame | Used to listen for the rendering time of the first frame during video playback.<br>This event is reported when the AVPlayer enters the playing state and the first frame of the video image is rendered to the display. Generally, the application can use this event to remove the video cover, achieving smooth connection between the cover and the video image.|
   | videoSizeChange | Used to listen for the width and height of video playback and adjust the window size and ratio.|
   | audioInterrupt | Used to listen for audio interruption. This event is used together with the **audioInterruptMode** property.<br>This event is reported when the current audio playback is interrupted by another (for example, when a call is coming), so the application can process the event in time.|

   <!-- @[setAVPlayerCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.avPlayer == null) {
     console.error(`${this.tag}: avPlayer has not init!`);
     return;
   }
   this.avPlayer.on('seekDone', (seekDoneTime) => {
     console.info(`${this.tag}: setAVPlayerCallback AVPlayer seek succeeded, seek time is ${seekDoneTime}`);
   });
   this.avPlayer.on('speedDone', (speed) => {
     console.info(`${this.tag}: setAVPlayerCallback AVPlayer speedDone, speed is ${speed}`);
   });
   this.avPlayer.on('durationUpdate', (duration: number) => {
     console.info(`${this.tag}: setAVPlayerCallback AVPlayer durationUpdate, duration is ${duration}`);
   });
   this.avPlayer.on('volumeChange', (vol: number) => {
     console.info(`${this.tag}: setAVPlayerCallback AVPlayer volumeChange, vol is ${vol}`);
   });
   this.avPlayer.on('bufferingUpdate', (infoType: media.BufferingInfoType, value: number) => {
     console.info(`${this.tag}: setAVPlayerCallback AVPlayer bufferingUpdate, vol is ${infoType}, value is ${value}`);
   });
   this.avPlayer.on('audioInterrupt', (info: audio.InterruptEvent) => {
     console.info(`${this.tag}: setAVPlayerCallback AVPlayer audioInterrupt, info is ${info}`);
   });
   // Error callback: call reset to reset avPlayer if an error occurs during an operation.
   this.avPlayer.on('error', (err) => {
     console.error(`${this.tag}: setAVPlayerCallback Invoke avPlayer failed ${JSON.stringify(err)}`);
     if (this.avPlayer == null) {
       console.error(`${this.tag}: avPlayer has not init on error`);
       return;
     }
     this.avPlayer.reset();
   });
   // State change callback.
   this.avPlayer.on('stateChange', async (state, reason) => {
     if (this.avPlayer == null) {
       console.info(`${this.tag}: avPlayer has not init on state change`);
       return;
     }
     switch (state) {
       case 'idle': // Reported after reset is successfully called.
         console.info(`${this.tag}: setAVPlayerCallback AVPlayer state idle called.`);
         break;
       case 'initialized': // Reported after the playback source is set for avPlayer.
         console.info(`${this.tag}: setAVPlayerCallback AVPlayer state initialized called.`);
         if (this.surfaceId) {
           this.avPlayer.surfaceId = this.surfaceId; // Set the display surface. This is not required for audio-only resources.
           console.info(`${this.tag}: setAVPlayerCallback this.avPlayer.surfaceId = ${this.avPlayer.surfaceId}`);
           this.avPlayer.prepare();
         }
         break;
       case 'prepared': // Reported after prepare is successfully called.
         console.info(`${this.tag}: setAVPlayerCallback AVPlayer state prepared called.`);
         this.avPlayer.on('bufferingUpdate', (infoType: media.BufferingInfoType, value: number) => {
           console.info(`${this.tag}: bufferingUpdate called, infoType value: ${infoType}, value:${value}}`);
         })
         this.durationTime = this.avPlayer.duration;
         this.currentTime = this.avPlayer.currentTime;
         this.avPlayer.play(); // Call play to start playback.
         console.info(`${this.tag}:
           setAVPlayerCallback speedSelect: ${this.speedSelect}, duration: ${this.durationTime}`);
         if (this.speedSelect != -1) {
           switch (this.speedSelect) {
             case SPEED_ZERO:
               this.avSetSpeed(media.PlaybackSpeed.SPEED_FORWARD_1_00_X);
               break;
             case SPEED_ONE:
               this.avSetSpeed(media.PlaybackSpeed.SPEED_FORWARD_1_25_X);
               break;
             case SPEED_TWO:
               this.avSetSpeed(media.PlaybackSpeed.SPEED_FORWARD_1_75_X);
               break;
             case SPEED_THREE:
               this.avSetSpeed(media.PlaybackSpeed.SPEED_FORWARD_2_00_X);
               break;
           }
         }
         callback(this.avPlayer);
         break;
       case 'playing': // Reported after play is successfully called.
         console.info(`${this.tag}: setAVPlayerCallback AVPlayer state playing called.`);
         if (this.intervalID != -1) {
           clearInterval(this.intervalID)
         }
         this.intervalID = setInterval(() => { // Update the current time.
           AppStorage.setOrCreate('durationTime', this.durationTime);
           AppStorage.setOrCreate('currentTime', this.currentTime);
         }, 100);
         let eventDataTrue: emitter.EventData = {
           data: {
             'flag': true
           }
         };
         let innerEventTrue: emitter.InnerEvent = {
           eventId: 2,
           priority: emitter.EventPriority.HIGH
         };
         emitter.emit(innerEventTrue, eventDataTrue);
         break;
       case 'completed': // Reported after playback is complete.
         console.info(`${this.tag}: setAVPlayerCallback AVPlayer state completed called.`);
         let eventDataFalse: emitter.EventData = {
           data: {
             'flag': false
           }
         };
         let innerEvent: emitter.InnerEvent = {
           eventId: 1,
           priority: emitter.EventPriority.HIGH
         };
         emitter.emit(innerEvent, eventDataFalse);
         if (this.intervalID != -1) {
           clearInterval(this.intervalID)
         }
         this.avPlayer.off('bufferingUpdate')
         AppStorage.setOrCreate('currentTime', this.durationTime);
         break;
       case 'released':
         console.info(`${this.tag}: setAVPlayerCallback released called.`);
         break
       case 'stopped':
         console.info(`${this.tag}: setAVPlayerCallback AVPlayer state stopped called.`);
         break
       case 'error':
         console.error(`${this.tag}: setAVPlayerCallback AVPlayer state error called.`);
         break
       case 'paused':
         console.info(`${this.tag}: setAVPlayerCallback AVPlayer state paused called.`);
         break
       default:
         console.info(`${this.tag}: setAVPlayerCallback AVPlayer state unknown called.`);
         break;
     }
   });
   // Playback time update callback.
   this.avPlayer.on('timeUpdate', (time: number) => {
     this.currentTime = time;
   });
   ```

3. Set the media asset URL. The AVPlayer enters the **initialized** state.
   > **NOTE**
   >
   > The URL in the code snippet below is for reference only. You need to check the media asset validity and set the URL based on service requirements.
   > 
   > - If local files are used for playback, ensure that the files are available and the application sandbox path is used for access. For details about how to obtain the application sandbox path, see [Obtaining Application File Paths](../../application-models/application-context-stage.md#obtaining-application-file-paths). For details about the application sandbox and how to push files to the application sandbox directory, see [File Management](../../file-management/app-sandbox-directory.md).
   > 
   > - If a network playback path is used, you must [declare the ohos.permission.INTERNET permission](../../security/AccessToken/declare-permissions.md).
   > 
   > - You can use ResourceManager.[getRawFd](../../reference/apis-localization-kit/js-apis-resource-manager.md#getrawfd9) to open the HAP resource file descriptor.
   > 
   > - The [playback formats and protocols](media-kit-intro.md#supported-formats-and-protocols) in use must be those supported by the system.

   <!-- @[changeUrl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->    
   
   ``` TypeScript
   // Change the URL.
   let url = '';
   if (this.avPlayer == null) {
       return;
   }
   this.avPlayer.url = url;
   ```

4. Obtain and set the surface ID of the window to display the video.

   The application obtains the surface ID from the **XComponent**. For details about the process, see [getXComponentSurfaceId](../../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md#getxcomponentsurfaceid9).

   <!-- @[setSurfaceId](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->    
   
   ``` TypeScript
   if (this.avPlayer) {
     try {
       this.avPlayer.surfaceId = this.xComponentController.getXComponentSurfaceId();
     } catch (e) {
       console.error(`${this.tag}: setSurfaceId = ${JSON.stringify(e)}`);
     }
   }
   ```

5. Call **prepare()** to switch the AVPlayer to the **prepared** state. In this state, you can obtain the duration of the media asset to play and set the scale type and volume.

   <!-- @[avPrepare](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.avPlayer) {
     try {
       this.avPlayer.prepare();
       console.info(`${this.tag}: avPrepare==`);
     } catch (e) {
       console.error(`${this.tag}: avPrepare== ${JSON.stringify(e)}`);
     }
   }
   ```

6. Call **play()**, **pause()**, **seek()**, and **stop()** to perform video playback control as required.

   <!-- @[avPlay](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.avPlayer) {
     try {
       this.avPlayer.play();
     } catch (e) {
       console.error(`${this.tag}: avPlay = ${JSON.stringify(e)}`);
     }
   }
   ```

   <!-- @[avPause](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.avPlayer) {
     try {
       this.avPlayer.pause();
       console.info(`${this.tag}: avPause==`);
     } catch (e) {
       console.error(`${this.tag}: avPause== ${JSON.stringify(e)}`);
     }
   }
   ```

   <!-- @[avSeek](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.avPlayer) {
     try {
       console.info(`${this.tag}: videoSeek  seekTime== ${seekTime}`);
       this.avPlayer.seek(seekTime, 2);
       this.currentTime = seekTime;
     } catch (e) {
       console.error(`${this.tag}: videoSeek== ${JSON.stringify(e)}`);
     }
   }
   ```

   <!-- @[avStop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.avPlayer) {
     try {
       this.avPlayer.stop();
       console.info(`${this.tag}: avStop==`);
     } catch (e) {
       console.error(`${this.tag}: avStop== ${JSON.stringify(e)}`);
     }
   }
   ```

7. (Optional) Call **reset()** to reset the AVPlayer. The AVPlayer enters the **idle** state again and you can change the media asset URL.

   <!-- @[avReset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   if (this.avPlayer) {
     try {
       this.avPlayer.reset();
     } catch (e) {
       console.error(`${this.tag}: reset== ${JSON.stringify(e)}`);
     }
   }
   ```

   <!-- @[changeUrl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Change the URL.
   let url = '';
   if (this.avPlayer == null) {
       return;
   }
   this.avPlayer.url = url;
   ```

8. Call **release()** to switch the AVPlayer to the **released** state. Now your application exits the playback.

   <!-- @[release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   this.avPlayer.release((err) => {
     if (err == null) {
       console.info(`${this.tag}: videoRelease release success`);
     } else {
       console.error(`${this.tag}: videoRelease release failed, error message is = ${JSON.stringify(err.message)}`);
     }
   });
   ```

## Running the Sample Project

1. Create a project, download the [sample project](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo), and copy its resources to the corresponding directories.
    ```text
    AVPlayerArkTSVideo
    entry/src/main/ets/
    └── pages
        └── Index.ets (playback UI)
    entry/src/main/resources/
    ├── base
    │   ├── element
    │   │   ├── color.json
    │   │   ├── float.json
    │   │   └── string.json
    │   └── media
    │       ├── ic_video_play.svg (play button image resource)
    │       └── ic_video_pause.svg (pause button image resource)
    └── rawfile
        └── test1.mp4 (video resource)
    ```
2. Compile and run the project.

## Samples

The following samples are provided to help you better understand how to develop video playback:

- [Video Playback (ArkTS, API version 9)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/VideoPlay)

- [Video Player (ArkTS, API version 9)](https://gitcode.com/openharmony/codelabs/tree/master/Media/VideoPlayer)
