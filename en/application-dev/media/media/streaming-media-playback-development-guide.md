# Using AVPlayer to Play Streaming Media (ArkTS)

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @dongyu_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=0d56cd17ee73deede8fc63cfd49a705ef680e337 translatedAt=2026-08-22T02:10:32.775Z pushedAt=2026-08-22T06:48:49.292Z -->

This topic describes how to use [AVPlayer](media-kit-intro.md#avplayer) for streaming live broadcasts and video-on-demand. The examples demonstrate how to play streaming videos in an end-to-end manner.

This guide focuses solely on streaming media playback. For details about other scenarios such as local audio and video playback, see [Using AVPlayer to Play Videos (ArkTS)](video-playback.md).

## Formats Supported by Streaming Media

| Streaming Media Protocol| Typical Link Format| On-Demand Streaming| Live Streaming|Content Protection|
| -------- | -------- | -------- | -------- | -------- |
| HLS | `https://example/index.m3u8` | Supported | Supported | Supported (see [DRM Kit](../drm/drm-overview.md)) |
| DASH | `https://example.mpd` | Supported | - | Supported (see [DRM Kit](../drm/drm-overview.md)) |
| HTTP/HTTPS | `https://example.mp4` | Supported | - | - |
| HTTP-FLV | `https://example.flv` | Supported | Supported | - |

## How to Develop

The full streaming media playback process includes creating an AVPlayer instance, setting the media asset to play and the window to display the video, setting playback parameters (volume, speed, and scale type), controlling playback (play, pause, seek, and stop), resetting the playback configuration, and releasing the instance. During application development, you can use the **state** property of the AVPlayer to obtain the AVPlayer state or call **on('stateChange')** to listen for state changes. Performing actions when the AVPlayer is in an incorrect state can lead to exceptions or undefined behavior. For details, see [AVPlayerState](../../reference/apis-media-kit/arkts-apis-media-t.md#avplayerstate9).  

1. Call **createAVPlayer()** to create an AVPlayer instance. The AVPlayer is in the **idle** state.

2. Set the events to listen for, which will be used in the full-process scenario. The table below lists the supported events.

   | Event| Description|
   | -------- | -------- |
   | stateChange | Mandatory; used to listen for changes of the **state** property of the AVPlayer.<br>To ensure proper functionality, the listener must be configured when the AVPlayer is in the idle state and before the resource setting API is called. If the listener is set after the resource setting API is called, the stateChange event reported during resource setting may fail to be received.|
   | error | Mandatory; used to listen for AVPlayer errors.<br>To ensure proper functionality, the listener must be configured when the AVPlayer is in the idle state and before the resource setting API is called. If the listener is set after the resource setting API is called, the error event reported during resource setting may fail to be received.|
   | durationUpdate | Used to listen for progress bar updates to refresh the media asset duration.|
   | timeUpdate | Used to listen for the current position of the progress bar to refresh the current time.|
   | seekDone | Used to listen for the completion status of the **seek()** request.<br>This event is reported when the AVPlayer seeks to the playback position specified in **seek()**.|
   | speedDone | Used to listen for the completion status of the **setSpeed()** request.<br>This event is reported when the AVPlayer plays videos at the speed specified in **setSpeed()**.|
   | volumeChange | Used to listen for the completion status of the **setVolume()** request.<br>This event is reported when the AVPlayer plays videos at the volume specified in **setVolume()**.|
   | bufferingUpdate | Used to listen for network playback buffer information. This event reports the buffer percentage and playback progress.|
   | audioInterrupt | Used to listen for audio interruption. This event is used together with the **audioInterruptMode** property.<br>This event is reported when the current audio playback is interrupted by another (for example, when a call comes), so the application can process the event in time.|

3. Set the media asset. Specifically, [use the AVPlayer to set the playback URL](playback-url-setting-method.md). The AVPlayer transitions to the initialized state.

   > **NOTE**
   >
   > The URL in the code snippet below is for reference only. You need to check the media asset validity and set the URL based on service requirements.
   > 
   > - If a network playback path is used, you must [declare the ohos.permission.INTERNET permission](../../security/AccessToken/declare-permissions.md).
   > 
   > - The playback format and protocol must be supported.
   > 

4. Obtain and set the surface ID of the window to display the video.

   The application obtains the surface ID from the **XComponent**. For details about the process, see [XComponent](../../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md).

5. Call **prepare()** to switch the AVPlayer to the **prepared** state. In this state, you can obtain the duration of the media asset to play and set the scale type and volume.

6. Call **play()**, **pause()**, **seek()**, and **stop()** to perform video playback control as required.

7. (Optional) Call **reset()** to reset the AVPlayer. The AVPlayer enters the **idle** state again and you can change the media asset URL.

8. Call **release()** to switch the AVPlayer to the **released** state. Now your application exits the playback.

## Special Notes

The standard process for playing streaming media follows the development steps outlined above. However, different streaming media formats have their own peculiarities in practice. This section delves into these differences, covering aspects like video startup strategies and the switching between audio and video tracks.

### Buffering Status for Streaming Media

When the download rate is lower than the bitrate of the media source, playback stuttering occurs. In this case, the player detects insufficient buffer data and buffers some data before resuming playback to avoid continuous stuttering. The buffering event reporting process for a single stuttering event is as follows: BUFFERING_START -> BUFFERING_PERCENT 0 -> ... -> BUFFERING_PERCENT 100 -> BUFFERING_END. CACHED_DURATION is continuously reported during both stuttering and playback until the resource is fully downloaded. For details, see [BufferingInfoType](../../reference/apis-media-kit/arkts-apis-media-e.md#bufferinginfotype8).

Sample code for listening for the bufferingUpdate event:

<!-- @[bufferingUpdate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSStreamingMedia/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
this.avPlayer.on('bufferingUpdate', (infoType: media.BufferingInfoType, value: number) => {
  console.info(`${this.tag}: bufferingUpdate called, infoType value: ${infoType}, value:${value}}`);
})
```

### HLS Bit Rate Switching

HLS streams currently support playback at multiple bit rates. By default, the AVPlayer selects the most suitable bit rate based on the network download speed.

1. Use [on('availableBitrates')](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#onavailablebitrates9) to listen for the available bit rates for an HLS stream. If the bit rate list has a length of 0, setting a specific bit rate is not supported.

   <!-- @[availableBitrates](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSStreamingMedia/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   this.avPlayer.on('availableBitrates', (bitrates: Array<number>) => {
     console.info('availableBitrates called, and availableBitrates length is: ' + bitrates.length);
     this.bitrate = bitrates[0]; // Save the bitrate to be switched.
   })
   ```

2. Use [setBitrate](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#setbitrate9) to set the playback bit rate. If the bit rate is not among the available bit rates, the AVPlayer selects the minimum and closest bit rate from the available ones. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. You can listen for the [bitrateDone](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#onbitratedone9) event to check whether the setting takes effect.

   <!-- @[setBitrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSStreamingMedia/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // Set playback bitrate.
   try {
     this.avPlayer.setBitrate(bitrate);
   } catch (error) {
     console.error(`${this.tag}: setBitrate failed, error message is = ${JSON.stringify(error.message)}`);
   }
   ```

### DASH Video Playback Startup Strategy

To maintain a smooth playback experience in environments with poor network connectivity, the AVPlayer initially selects the lowest video resolution for playback and then adjusts automatically based on the network status. You can customize the playback startup strategy, including setting parameters such as the video width, height, and color format, for DASH videos based on service requirements.

The sample code below demonstrates setting the video to start at a width of 1920 px and a height of 1080 px. The AVPlayer selects a video stream with a resolution of 1920 x 1080 from the MPD resources for playback.

```ts
import { media } from '@kit.MediaKit';

let mediaSource : media.MediaSource = media.createMediaSourceWithUrl("http://example/abc.mpd",  {"User-Agent" : "User-Agent-Value"});
let playbackStrategy : media.PlaybackStrategy = {preferredWidth: 1920, preferredHeight: 1080};
this.avPlayer.setMediaSource(mediaSource, playbackStrategy);
```

### DASH Audio and Video Track Switching

DASH streaming media includes multiple audio, video, and subtitle tracks, each with different resolutions, bit rates, sampling rates, and encoding formats. By default, the AVPlayer automatically selects video tracks with different bit rates based on the network status. You can manually select an audio or video track for playback based on service requirements. In this case, the adaptive bit rate switching feature becomes invalid.

1. Set the [trackChange](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#ontrackchange12) event.

   <!-- @[trackChange](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSStreamingMedia/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   this.avPlayer.on('trackChange', (index: number, isSelect: boolean) => {
   console.info(`trackChange info, index: ${index}, isSelect: ${isSelect}`);
   })
   ```

2. Call [getTrackDescription](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#gettrackdescription9) to obtain the list of all audio and video tracks. You can determine the index of the target track based on actual requirements and information about each field in [MediaDescription](../../reference/apis-media-kit/arkts-apis-media-i.md#mediadescription8).

   <!-- @[getTrackDescription](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSStreamingMedia/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   this.avPlayer.getTrackDescription((error: BusinessError, arrList: Array<media.MediaDescription>) => {
     if (arrList != null) {
       for (let i = 0; i < arrList.length; i++) {
         let propertyIndex: Object = arrList[i][media.MediaDescriptionKey.MD_KEY_TRACK_INDEX];
         let propertyType: Object = arrList[i][media.MediaDescriptionKey.MD_KEY_TRACK_TYPE];
         let propertyWidth: Object = arrList[i][media.MediaDescriptionKey.MD_KEY_WIDTH];
         let propertyHeight: Object = arrList[i][media.MediaDescriptionKey.MD_KEY_HEIGHT];
         if (propertyType == media.MediaType.MEDIA_TYPE_VID && propertyWidth == 1920 && propertyHeight == 1080) {
           this.videoTrackIndex = parseInt(propertyIndex.toString()); // Obtain the 1080p video track index.
         }
       }
     } else {
       console.error(`getTrackDescription fail, error:${error}`);
     }
   });
   ```

3. During audio and video playback, call [selectTrack](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#selecttrack12) to select audio and video tracks, or call [deselectTrack](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#deselecttrack12) to deselect them.

   <!-- @[selectTrack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSStreamingMedia/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // Switch to the target video track.
   try {
     this.avPlayer.selectTrack(track);
   } catch (error) {
     console.error(`${this.tag}: selectTrack failed, error message is = ${JSON.stringify(error.message)}`);
   }
   ```

## Exception Description

If the network is disconnected when the AVPlayer is playing streaming media, the AVPlayer module handles the fault based on the returned error code, server response time, and number of requests. If the error code type does not require a retry, the module reports the corresponding error code to the application. If the error code type requires a retry, the module initiates a maximum of 10 retries within 30 seconds. If the number of retries exceeds 10 or the total retry duration exceeds 30 seconds, the module reports the corresponding error code to the application. If the retry is successful, the module continues the playback.

## Running the Sample Project

Refer to the following example to play a complete streaming video.

1. Create a project, download the [sample project](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSStreamingMedia), and copy its resources to the corresponding directories.

    ```txt
    AVPlayerArkTSAudio
    entry/src/main/ets/
    └── pages
        └── Index.ets (playback page)
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

2. Request the network permission in the **/entry/src/main/module.json5** file. Alternatively, replace the **module.json5** file with that in the sample project.

    ```json
    "requestPermissions": [
      {
        "name": "ohos.permission.INTERNET"
      },
      {
        "name": "ohos.permission.GET_WIFI_INFO"
      }
    ]
    ```

3. Comment out or uncomment the above examples in the **entry/src/main/ets/pages/Index.ets** file, and compile and run the application.