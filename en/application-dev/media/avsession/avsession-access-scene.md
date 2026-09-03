# Accessing AVSession
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=6db95933f92c36be892f64316b822565946ecf49 translatedAt=2026-09-03T09:01:21.285Z pushedAt=2026-09-03T09:04:52.946Z -->

When implementing audio and video features, media applications also need to integrate with AVSession Kit. Based on typical use cases, this document describes how to integrate with AVSession for media display and control, providing developers with adaptation guidance.

Different scenarios are presented with different UIs in the Media Controller. In addition, application integration must comply with different requirements and constraints depending on the scenario.

## Scenarios That Require AVSession Access

AVSession restricts background audio playback and VoIP calls. Therefore, applications that provide long-duration audio playback, audiobooks, long-duration video playback, and VoIP calls need to access AVSession. If such an application does not create an AVSession during these services, the system stops the corresponding audio playback or mutes the call when detecting that the application is running in the background. You can verify the restriction locally before the application is released.

For other applications that use audio playback, such as games and live streams, accessing AVSession is optional, depending on whether the application requires background playback. If background playback is required, AVSession access is still mandatory. Otherwise, normal service functions will be restricted.

To implement background playback, the application must also use [Background Tasks Kit](../../task-management/background-task-overview.md) to request a continuous task to avoid being suspended.

## Access Process

The process for implementing AVSession access is as follows:

1. Determine the type of AVSession to be created for the application, and then [create one](#creating-avsession). The AVSession type determines the style of the control template displayed in the Media Controller.
2. [Create a background task](#creating-a-background-task).
3. [Set necessary metadata](#setting-metadata-information) to display corresponding information in the Media Controller. The metadata includes but is not limited to the IDs of the current media asset (**assetId**), previous media asset (**previousAssetId**), and next media asset (**nextAssetId**), title, author, album, writer, and duration.
4. [Set playback state information](#setting-playback-state). The information includes but is not limited to the playback state (**state**), position (**position**), speed (**speed**), buffered time (**bufferedTime**), loop mode (**loopMode**), whether the media asset is favorited (**isFavorite**), media ID being played (**activeItemId**), and custom media data (**extras**).
5. [Register control commands](#control-command-processing) as required, including but not limited to play/pause, previous/next, fast-forward/rewind, favorite, loop mode, and progress bar.
6. Destroy AVSession when the application exits or stops providing service.

## Creating AVSession

[AVSessionType](../../reference/apis-avsession-kit/arkts-apis-avsession-t.md#avsessiontype10) in the constructor determines the type of AVSession to create. Different AVSession types represent the control capabilities in various scenarios and display different control templates in the Media Controller.

- For audio AVSession, the Media Controller provides the following control buttons: favorite, previous, play/pause, next, and loop mode.

- For video AVSession, the Media Controller provides the following control buttons: fast-rewind, previous, play/pause, next, and fast-forward.

- For voice_call AVSession, the application is not displayed in the Media Controller.

Refer to the code snippet below:

> **NOTE**
>
> The sample code below demonstrates only the API call for creating an AVSession object. When actually using it, the application must ensure that the AVSession object persists throughout the application's background playback activities. This prevents the system from reclaiming or releasing it, which could lead to playback being controlled by the system.

<!-- @[createAVSession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/CreateAVSession.ets) -->

``` TypeScript
import { avSession as AVSessionManager } from '@kit.AVSessionKit';
// ...

@Entry
@Component
struct Index {
  @State message: string = 'hello world';
  // ...

  build() {
    Column() {
      // ...
      Text(this.message)
        .onClick(async () => {
          // Start to create and activate an AVSession object.
          // Create an AVSession object.
          let context = this.getUIContext().getHostContext() as Context;
          let type: AVSessionManager.AVSessionType = 'audio';
          let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
          // Call activate() after the metadata and control commands are registered.
          await session.activate();
          console.info(`session create done : sessionId : ${session.sessionId}`);
          // ...
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## Creating a Background Task

To implement background playback, the application must also use [Background Tasks Kit](../../task-management/background-task-overview.md) to request a continuous task to avoid being suspended.

Media playback applications must request a continuous task of the [AUDIO_PLAYBACK](../../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundmode) background mode.


## Setting Metadata Information

The application uses [setAVMetadata](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setavmetadata10) to set the metadata information of the current media session to the system. The Media Controller displays information based on the metadata set by the application.

### Metadata Information

Metadata information [AVMetadata](../../reference/apis-avsession-kit/arkts-apis-avsession-i.md#avmetadata10) includes the ID of the current media (`assetId`), ID of the previous media (`previousAssetId`), ID of the next media (`nextAssetId`), title (`title`), album author (`author`), artist (`artist`), album name (`album`), lyricist (`writer`), media image (`mediaImage`), and media duration (`duration`).

<!-- @[setAVMetadata](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/SetAVMetadata.ets) -->

``` TypeScript
import { avSession as AVSessionManager } from '@kit.AVSessionKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

@Entry
@Component
struct Index {
  @State message: string = 'hello world';
  // ...

  build() {
    Column() {
      // ...
      Text(this.message)
        .onClick(async () => {
          try {
            let context = this.getUIContext().getHostContext() as Context;
            // It is assumed that an AVSession object has been created. For details about how to create an AVSession object, see the node snippet above.
            let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', 'audio');
            // Set necessary AVSession metadata.
            let metadata: AVSessionManager.AVMetadata = {
              assetId: '0', // Specified by the application, used to identify the media asset in the application media library.
              title: 'TITLE',
              mediaImage: 'IMAGE',
              artist: 'ARTIST',
            };
            session.setAVMetadata(metadata).then(() => {
              console.info(`SetAVMetadata successfully`);
              // ...
            }).catch((err: BusinessError) => {
              console.error(`Failed to set AVMetadata. Code: ${err.code}, message: ${err.message}`);
              // ...
            });
          } catch (err) {
            if (err) {
              console.error(`AVSession create Error: Code: ${err.code}, message: ${err.message}`);
              // ...
            }
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Setting Lyrics Field Information

Metadata [AVMetadata](../../reference/apis-avsession-kit/arkts-apis-avsession-i.md#avmetadata10) contains lyric fields. The application can set lyric fields to display lyrics in certain scenarios. Currently, two lyric fields can be set:

- **lyric**: complete lyrics of the media asset. The Media Controller displays lyric content based on this field. The application needs to concatenate the lyric content into a string and pass it in.

- **singleLyricText**: a single line of lyric text. The system Bluetooth module displays lyric content in certain scenarios, such as Bluetooth speakers, based on this field.

> **NOTE**
>
> - The `lyric` field supports only lyrics in LRC format (time tags plus lyric information, for example, `[00:25.44]lyric information`). If you pass lyrics in other formats, the Media Controller may fail to parse them, causing abnormal lyric display.
>
> - The size of both the `lyric` field and the `singleLyricText` field must not exceed 40960 bytes. Otherwise, the lyric information fails to be set due to system transmission limits.

<!-- @[settingLyrics](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/SettingLyrics.ets) -->

``` TypeScript
import { avSession as AVSessionManager } from '@kit.AVSessionKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

@Entry
@Component
struct Index {
  @State message: string = 'hello world';
  // ...

  build() {
    Column() {
      // ...
      Text(this.message)
        .onClick(async () => {
          let context = this.getUIContext().getHostContext() as Context;
          // It is assumed that an AVSession object has been created. For details about how to create an AVSession object, see the node snippet above.
          let type: AVSessionManager.AVSessionType = 'audio';
          let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);

          // Set the lyric information to AVSession.
          let metadata: AVSessionManager.AVMetadata = {
            assetId: '0',
            title: 'TITLE',
            mediaImage: 'IMAGE',
            // There are two types of elements in LRC: one is a time tag plus lyrics, and the other is an ID tag.
            // For example: [00:25.44]xxx\r\n[00:26.44]xxx\r\n.
            lyric: 'lyric content in LRC format',
            // The singleLyricText field stores a single line of lyric text without a timestamp.
            // For example: "single line of lyric content".
            singleLyricText: 'single line of lyric content',
          };
          session.setAVMetadata(metadata).then(() => {
            console.info(`SetAVMetadata successfully`);
            // ...
          }).catch((err: BusinessError) => {
            console.error(`Failed to set AVMetadata. Code: ${err.code}, message: ${err.message}`);
            // ...
          });
          // ...
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Setting Progress Bar Information

The metadata [AVMetadata](../../reference/apis-avsession-kit/arkts-apis-avsession-i.md#avmetadata10) contains the **duration** field, in ms. To display the progress bar of a media asset in the Media Controller, set the correct playback duration in **duration**.

<!-- @[settingTheProgressBar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/SettingTheProgressBar.ets) -->

``` TypeScript
import { avSession as AVSessionManager } from '@kit.AVSessionKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

@Entry
@Component
struct Index {
  @State message: string = 'hello world';
  // ...

  build() {
    Column() {
      // ...
      Text(this.message)
        .onClick(async () => {
          let context = this.getUIContext().getHostContext() as Context;
          // It is assumed that an AVSession object has been created. For details about how to create an AVSession object, see the node snippet above.
          let type: AVSessionManager.AVSessionType = 'audio';
          let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);

          // Set the media resource duration.
          let metadata: AVSessionManager.AVMetadata = {
            assetId: '0',
            title: 'TITLE',
            mediaImage: 'IMAGE',
            duration: 23000, // Duration of the media asset, in milliseconds.
          };
          session.setAVMetadata(metadata).then(() => {
            console.info(`SetAVMetadata successfully`);
            // ...
          }).catch((err: BusinessError) => {
            console.error(`Failed to set AVMetadata. Code: ${err.code}, message: ${err.message}`);
            // ...
          });

          // Set the playback state information, including the playback state, position, speed, and buffered time.
          let playbackState: AVSessionManager.AVPlaybackState = {
            state: AVSessionManager.PlaybackState.PLAYBACK_STATE_PLAY, // Playing state.
            position: {
              elapsedTime: 1000, // Playback position, in milliseconds.
              updateTime: new Date().getTime(), // Timestamp when the application updates the current position, in milliseconds.
            },
            speed: 1.0, // Optional. The default value is 1.0. The playback speed is set based on the speed supported by the application. The system does not verify the speed.
            bufferedTime: 14000, // Optional. Buffered time, in milliseconds.
          };
          session.setAVPlaybackState(playbackState, (err) => {
            if (err) {
              console.error(`Failed to set AVPlaybackState. Code: ${err.code}, message: ${err.message}`);
              // ...
            } else {
              console.info(`SetAVPlaybackState successfully`);
              // ...
            }
          });
          // ...
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

The Media Controller automatically calculates the playback progress based on the information set by the application. The application does not need to update the playback progress in real time. However, when the **state**, **position**, or **speed** changes, the application must update **AVPlaybackState**. Otherwise, the application state information and progress bar information displayed in the Media Controller may be abnormal.

The application reports the start position of the progress once the actual playback starts. If the playback is in the buffer state, the application can report **AVSessionManager.PlaybackState.PLAYBACK_STATE_BUFFERING** to instruct the system not to update the progress.

Certain special processing is required when setting the progress bar.

1. Songs that can be previewed

   (1) The application sets the preview duration, rather than the total duration, for a song. In this case, when the user performs progress control in the Media Controller, the application receives the relative timestamp within the preview duration, rather than that within the total duration. The application needs to calculate the absolute timestamp from the very beginning of the song.

   (2) If the application sets the total duration for a song but requires the system to provide preview, it can report the start position of the progress when the playback starts, and report the end position when the received seek instruction is not within the preview duration. In the latter case, the playback control progress of the system rebounds.

2. Songs that do not support preview

   If a song cannot be previewed, it cannot be played by the application. In this case, the application should set the duration to **-1**, so the system does not display the actual duration.

3. Special contents such as ads

   For media assets with pre-roll or post-roll ads, you are advised to:
   - Set the ad duration separately.
   - Set a new duration for the actual content, to distinguish it from the ad.

<!--RP1--><!--RP1End-->

### Display Tags of Media Assets

The metadata [AVMetadata](../../reference/apis-avsession-kit/arkts-apis-avsession-i.md#avmetadata10) provides the **displayTags** field for displaying the media asset tag, which identifies the audio source of the application. After the application sets **displayTags**, the Media Controller displays the tag synchronously. Currently, only the Audio Vivid tag is supported.

<!-- @[displayTagsOfMediaAssets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/DisplayTagsOfMediaAssets.ets) -->  

``` TypeScript
import { avSession as AVSessionManager } from '@kit.AVSessionKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

@Entry
@Component
struct Index {
  @State message: string = 'hello world';
  // ...

  build() {
    Column() {
      // ...
      Text(this.message)
        .onClick(async () => {
          let context = this.getUIContext().getHostContext() as Context;
          // Assume that a session has been created. For details about how to create a session, see the previous example.
          let type: AVSessionManager.AVSessionType = 'audio';
          let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);

          // Set the media source information to the AVSession.
          let metadata: AVSessionManager.AVMetadata = {
            assetId: '0',
            title: 'TITLE',
            mediaImage: 'IMAGE',
            // Indicate that the media source is Audio Vivid.
            displayTags: AVSessionManager.DisplayTag.TAG_AUDIO_VIVID,
          };
          session.setAVMetadata(metadata).then(() => {
            console.info(`SetAVMetadata successfully`);
            // ...
          }).catch((err: BusinessError) => {
            console.error(`Failed to set AVMetadata. Code: ${err.code}, message: ${err.message}`);
            // ...
          });
          // ...
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## Setting Playback State

The application uses [setAVPlaybackState](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setavplaybackstate10) to set the playback state information of the current media session to the system. The Media Controller strictly displays information based on the playback state information passed by the application.

### Playback State Information

Playback state information [AVPlaybackState](../../reference/apis-avsession-kit/arkts-apis-avsession-i.md#avplaybackstate10) includes the playback state of the current media (`state`), playback position (`position`, which contains the elapsed playback time `elapsedTime` and the update timestamp `updateTime`), playback speed (`speed`), buffered time (`bufferedTime`), loop mode (`loopMode`), whether the media is marked as favorite (`isFavorite`), ID of the media being played (`activeItemId`), and custom media data (`extras`).

<!-- @[settingGeneralStateInformation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/SettingGeneralStateInformation.ets) -->  

``` TypeScript
import { avSession as AVSessionManager } from '@kit.AVSessionKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

@Entry
@Component
struct Index {
  @State message: string = 'hello world';
  // ...

  build() {
    Column() {
      // ...
      Text(this.message)
        .onClick(async () => {
          let context = this.getUIContext().getHostContext() as Context;
          // Assume that a session has been created. For details about how to create a session, see the previous example.
          let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', 'audio');

          // Player logic... triggers changes to the media information and playback state.
          // Set a simple playback state - paused, not favorited.
          let playbackState: AVSessionManager.AVPlaybackState = {
            state: AVSessionManager.PlaybackState.PLAYBACK_STATE_PAUSE,
            isFavorite: false
          };
          session.setAVPlaybackState(playbackState, (err: BusinessError) => {
            if (err) {
              console.error(`Failed to set AVPlaybackState. Code: ${err.code}, message: ${err.message}`);
              // ...
            } else {
              console.info(`SetAVPlaybackState successfully`);
              // ...
            }
          });
          // ...
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## Control Command Processing

### Supported Control Commands

After an application accesses AVSession, it can register control commands through **on()** to implement the corresponding control button operations in the Media Controller.

> **NOTE**
>
> After an AVSession object is created, register control commands supported by the application before activating the object.

The following table lists the control commands supported by audio and video applications.

| Control Command| Description  |
| ------  | -------------------------|
| [play](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onplay10)    | Start playback. |
| [pause](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onpause10)    | Pause playback. |
| [stop](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onstop10)    | Stop playback. |
| [playNext](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onplaynext10)    | Play next track. |
| [playPrevious](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onplayprevious10)    | Play previous track. |
| [fastForward](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onfastforward10)    | Fast forward. |
| [rewind](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onrewind10)    | Fast rewind. |
| [playWithAssetId](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onplaywithassetid20)    | Play based on a specific asset ID. |
| [seek](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onseek10)    | Seek command. |
| [setSpeed](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onsetspeed10)    | Set playback speed. |
| [setLoopMode](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onsetloopmode10)    | Set loop mode. |
| [toggleFavorite](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#ontogglefavorite10)    | Set favorite status. |
| [skipToQueueItem](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onskiptoqueueitem10)    | Play a selected item in the playlist. |
| [handleKeyEvent](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onhandlekeyevent10)    | Handle key events. |
| [commonCommand](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#oncommoncommand10)    | Set custom control. |

The table below lists the control commands for calling applications.

| Control Command| Description  |
| ------  | -------------------------|
| [answer](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onanswer11)    | Answer a call. |
| [hangUp](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onhangup11)    | Hang up a call. |
| [toggleCallMute](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#ontogglecallmute11)    | Mute or unmute a call. |

### Handling Unsupported Control Commands

If the application does not support certain control command operations, for example, the **playPrevious** command, it can use **off()** to unregister the corresponding control command. The Media Controller then grays out or hides the corresponding control button to clearly inform users that the application does not support this control operation.

<!-- @[handing_unSupported](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/HandlingUnsupportedCommands.ets) --> 

``` TypeScript
import { avSession as AVSessionManager } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let context = this.getUIContext().getHostContext() as Context;
          // It is assumed that an AVSession object has been created. For details about how to create an AVSession object, see the node snippet above.
          let type: AVSessionManager.AVSessionType = 'audio';
          let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);

          // Cancel the listener of the AVSession object.
          session.off('play');
          session.off('pause');
          session.off('stop');
          session.off('playNext');
          session.off('playPrevious');
          // ...
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Setting Fast-Forward/Rewind

The system supports three fast-forward/rewind durations, which the application can set through APIs. It also registers the fast-forward/rewind control command to respond to user operations.

> **NOTE**
>
> When applications register commands for fast-forward/rewind and next/previous track switching, there are differences in the display on the Media Controller.

- When **AVSessionType** is **audio**:

  | Registered Events | Buttons Displayed in Media Controller | Button Availability|
  | ------------ | ------------ | ------------ |
  | No events registered| **Previous**, **Next**| All buttons are unavailable.|
  | Previous/Next events registered| **Previous**, **Next**| If the Previous event is registered, the **Previous** button is available.<br>If the Next event is registered, the **Next** button is available.<br>A button is unavailable if its corresponding event is not registered. |
  | Fast-forward/rewind events registered| **Previous**, **Next**|  All buttons are unavailable.|
  | Previous/Next and fast-forward/rewind events registered| **Previous**, **Next**| If the Previous event is registered, the **Previous** button is available.<br>If the Next event is registered, the **Next** button is available.<br>A button is unavailable if its corresponding event is not registered. |

- When **AVSessionType** is **video**:

  | Registered Events | Buttons Displayed in Media Controller| Button Availability|
  | ------------ | ------------ | ------------ |
  | No events registered| **Fast-Forward**, **Rewind**| All buttons are unavailable.|
  | Previous/Next events registered| **Previous**, **Next**| If the Previous event is registered, the **Previous** button is available.<br>If the Next event is registered, the **Next** button is available.<br>A button is unavailable if its corresponding event is not registered. |
  | Fast-forward/rewind events registered| **Fast-Forward**, **Rewind**|  If the Fast-forward event is registered, the **Fast-forward** button is available.<br>If the Rewind event is registered, the **Rewind** button is available.<br>A button is unavailable if its corresponding event is not registered.|
  | Previous/Next and fast-forward/rewind events registered| **Fast-Forward**, **Rewind**|  If the Fast-forward event is registered, the **Fast-forward** button is available.<br>If the Rewind event is registered, the **Rewind** button is available.<br>A button is unavailable if its corresponding event is not registered.|

  <!-- @[settingFastForward](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/SettingFastForward.ets) -->

  ``` TypeScript
  import { avSession as AVSessionManager } from '@kit.AVSessionKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  // ...

  @Entry
  @Component
  struct Index {
    @State message: string = 'hello world';
    // ...

    build() {
      Column() {
        // ...
        Text(this.message)
          .onClick(async () => {
            let context = this.getUIContext().getHostContext() as Context;
            // It is assumed that an AVSession object has been created. For details about how to create an AVSession object, see the node snippet above.
            let type: AVSessionManager.AVSessionType = 'audio';
            let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
            // ...

            // Set the supported fast-forward or rewind duration for AVSession.
            let metadata: AVSessionManager.AVMetadata = {
              assetId: '0', // Specified by the application, used to identify the media asset in the application media library.
              title: 'TITLE',
              mediaImage: 'IMAGE',
              skipIntervals: AVSessionManager.SkipIntervals.SECONDS_10,
            };
            session.setAVMetadata(metadata).then(() => {
              console.info(`SetAVMetadata successfully`);
              // ...
            }).catch((err: BusinessError) => {
              console.error(`Failed to set AVMetadata. Code: ${err.code}, message: ${err.message}`);
              // ...
            });

            session.on('fastForward', (time?: number) => {
              console.info(`on fastForward , do fastForward task`);
              // ...
              // do some tasks ···
            });
            session.on('rewind', (time?: number) => {
              console.info(`on rewind , do rewind task`);
              // ...
              // do some tasks ···
            });
            // ...
          })
      }
      .width('100%')
      .height('100%')
    }
  }
  ```

### Favoriting Media Assets

To implement favoriting, a music application can call [on('toggleFavorite')](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#ontogglefavorite10) to register the **toggleFavorite** control command.

<!-- @[toggleFavorite_mediaAssets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/FavoritingMediaAssets.ets) -->

``` TypeScript
import { avSession as AVSessionManager } from '@kit.AVSessionKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

@Entry
@Component
struct Index {
  @State message: string = 'hello world';
  // ...

  build() {
    Column() {
      // ...
      Text(this.message)
        .onClick(async () => {
          let context = this.getUIContext().getHostContext() as Context;
          // It is assumed that an AVSession object has been created. For details about how to create an AVSession object, see the node snippet above.
          let type: AVSessionManager.AVSessionType = 'audio';
          let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
          // ...
          session.on('toggleFavorite', (assetId) => {
            console.info(`on toggleFavorite `);
            // ...
            // The application receives the toggleFavorite command and favorites or unfavorites the media asset.

            // Set the new state to AVSession after the application finishes favoriting or unfavoriting.
            let playbackState: AVSessionManager.AVPlaybackState = {
              isFavorite: true,
            };
            session.setAVPlaybackState(playbackState).then(() => {
              console.info(`SetAVPlaybackState successfully`);
              // ...
            }).catch((err: BusinessError) => {
              console.error(`SetAVPlaybackState BusinessError: code: ${err.code}, message: ${err.message}`);
              // ...
            });
          });
          // ...
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Implementing Loop Mode

For music applications, the Media Controller displays control operations in loop mode by default.

The Media Controller supports switching between four fixed [loop modes](../../reference/apis-avsession-kit/arkts-apis-avsession-e.md#loopmode10): shuffle, sequential playback, single loop, and playlist loop. After the application receives the loop mode switching command and completes the switching, it needs to report the switched **LoopMode** to the system.

If the **LoopMode** supported by the application does not match any of the four predefined loop modes, the application must select and report one of the four modes to the system. The mode to report is determined by the application.

Refer to the code snippet below:

<!-- @[settingTheLoopMode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/SettingTheLoopMode.ets) -->

``` TypeScript
import { avSession as AVSessionManager } from '@kit.AVSessionKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...

@Entry
@Component
struct Index {
  @State message: string = 'hello world';
  // ...

  build() {
    Column() {
      // ...
      Text(this.message)
        .onClick(async () => {
          let context = this.getUIContext().getHostContext() as Context;
          // It is assumed that an AVSession object has been created. For details about how to create an AVSession object, see the node snippet above.
          let type: AVSessionManager.AVSessionType = 'audio';
          let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
          // ...

          // When the application starts or switches the loop mode, it sets the loop mode in use to the AVSession.
          let playBackState: AVSessionManager.AVPlaybackState = {
            loopMode: AVSessionManager.LoopMode.LOOP_MODE_SINGLE,
          };
          session.setAVPlaybackState(playBackState).then(() => {
            console.info(`set AVPlaybackState successfully`);
            // ...
          }).catch((err: BusinessError) => {
            console.error(`Failed to set AVPlaybackState. Code: ${err.code}, message: ${err.message}`);
            // ...
          });

          // The application listens for loop mode changes.
          session.on('setLoopMode', (mode) => {
            console.info(`on setLoopMode ${mode}`);
            // ...
            // After receiving the instruction for setting the loop mode, the application determines the next mode. After the switching is complete, the application reports the new loop mode through AVPlaybackState.
            let playBackState: AVSessionManager.AVPlaybackState = {
              loopMode: AVSessionManager.LoopMode.LOOP_MODE_SINGLE,
            };
            session.setAVPlaybackState(playBackState).then(() => {
              console.info(`set AVPlaybackState successfully`);
              // ...
            }).catch((err: BusinessError) => {
              console.error(`Failed to set AVPlaybackState. Code: ${err.code}, message: ${err.message}`);
              // ...
            });
          });
          // ...
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Performing Progress Control

If the application supports [progress bar display](#setting-progress-bar-information), it must also support progress bar control by registering the seek control command. When the user drags the progress bar in the Media Controller, the application receives the corresponding callback and must handle it properly. For reference, see the following implementation:

<!-- @[performingProgressControl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/PerformingProgressControl.ets) -->

``` TypeScript
import { avSession as AVSessionManager } from '@kit.AVSessionKit';
// ...

@Entry
@Component
struct Index {
  @State message: string = 'hello world';
  // ...

  build() {
    Column() {
      // ...
      Text(this.message)
        .onClick(async () => {
          let context = this.getUIContext().getHostContext() as Context;
          // It is assumed that an AVSession object has been created. For details about how to create an AVSession object, see the node snippet above.
          let type: AVSessionManager.AVSessionType = 'audio';
          let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
          // ...

          session.on('seek', (time: number) => {
            console.info(`on seek , the time is ${time}`);
            // ...

            // The seek operation may trigger a long buffering time. You can set the playback state to PLAYBACK_STATE_BUFFERING.
            let playbackState: AVSessionManager.AVPlaybackState = {
              state: AVSessionManager.PlaybackState.PLAYBACK_STATE_BUFFERING, // Buffering state.
            };
            session.setAVPlaybackState(playbackState, (err) => {
              if (err) {
                console.error(`Failed to set AVPlaybackState. Code: ${err.code}, message: ${err.message}`);
                // ...
              } else {
                console.info(`SetAVPlaybackState successfully`);
                // ...
              }
            });

            // The application responds to the seek command and seeks to the specified position.

            // After seeking to the specified position, the application synchronizes the new position to the system.
            playbackState.state = AVSessionManager.PlaybackState.PLAYBACK_STATE_PLAY; // Playing state.
            playbackState.position = {
              elapsedTime: time, // Elapsed playback position, in ms.
              updateTime: new Date().getTime(), // Timestamp when the application updates the current position, in milliseconds.
            }
            session.setAVPlaybackState(playbackState, (err) => {
              if (err) {
                console.error(`Failed to set AVPlaybackState. Code: ${err.code}, message: ${err.message}`);
                // ...
              } else {
                console.info(`SetAVPlaybackState successfully`);
                // ...
              }
            });
          });

          // ...
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## Adapting to Media Notification

After the application properly integrates with AVSession by following the preceding process, sets the metadata and correct playback state information, and registers control commands, information about the application is displayed in the system notification and on the lock screen when the application starts playback.


## Adapting to Bluetooth and Wired Key Events

After an application correctly accesses AVSession, it can listen for Bluetooth and wired headset key events by registering control commands. AVSession provides the following two implementation methods:
- Method 1 (recommended)

  You can register the required control commands as needed by referring to [Control Command Processing](#control-command-processing). The AVSession control commands that can be converted are as follows:
  | Control Command| Description  |
  | ------  | -------------------------|
  | play    | Plays the media.|
  | pause    | Pauses the playback.|
  | stop    | Stops the playback.|
  | playNext    | Plays the next media asset.|
  | playPrevious    | Plays the previous media asset.|
  | fastForward    | Fast-forwards.|
  | rewind    | Rewinds.|

  <!-- @[adaptingToBluetoothMethodOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/AdaptingToBluetoothMethodOne.ets) -->

  ``` TypeScript
  import { avSession as AVSessionManager } from '@kit.AVSessionKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  // ...
  
  @Entry
  @Component
  struct Index {
    @State message: string = 'hello world';
    // ...
  
    build() {
      Column() {
        // ...
        Text(this.message)
          .onClick(async () => {
            try {
              let context = this.getUIContext().getHostContext() as Context;
              let type: AVSessionManager.AVSessionType = 'audio';
              let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
              // ...
              // Set the required media information. This is mandatory; otherwise, control events cannot be received.
              let metadata: AVSessionManager.AVMetadata = {
                assetId: '0', // Specified by the application to identify the media in the application's media library.
                title: 'TITLE',
                mediaImage: 'IMAGE',
                artist: 'ARTIST'
              };
              session.setAVMetadata(metadata).then(() => {
                console.info(`SetAVMetadata successfully`);
                // ...
              }).catch((err: BusinessError) => {
                console.error(`Failed to set AVMetadata. Code: ${err.code}, message: ${err.message}`);
                // ...
              });
              // Generally, the corresponding logic for the player is processed in the listener.
              // After processing, synchronize the playback-related information through the set API. Refer to the example above.
              session.on('play', () => {
                console.info(`on play , do play task`);
                // ...
                // If this command is not supported yet, do not register it; or, if it is registered but not used for the time being, cancel the listener through session.off('play').
                // After processing, use setAVPlayState to report the playback state.
              });
              session.on('pause', () => {
                console.info(`on pause , do pause task`);
                // ...
                // If this command is not supported yet, do not register it; or, if it is registered but not used for the time being, cancel the listener through session.off('pause').
                // After processing, use setAVPlayState to report the playback state.
              });
              // ...
            } catch (err) {
              if (err) {
                console.error(`AVSession create Error: Code: ${err.code}, message: ${err.message}`);
                // ...
              }
              }
          })
      }
      .width('100%')
      .height('100%')
      }
    }
  ```

- Method 2

  Register the [on('handleKeyEvent')](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#onhandlekeyevent10) command through AVSession. This callback directly forwards the media key event [KeyEvent](../../reference/apis-input-kit/js-apis-keyevent.md). You need to identify the type of the key event and respond to the event to implement the corresponding function. The key event types that can be forwarded are as follows:

  | Key Type ([KeyCode](../../reference/apis-input-kit/js-apis-keycode.md#keycode))| Description  |
  | ------  | -------------------------|
  | KEYCODE_MEDIA_PLAY_PAUSE    | Play/Pause key.|
  | KEYCODE_MEDIA_STOP    | Stop key.|
  | KEYCODE_MEDIA_NEXT    | Next key.|
  | KEYCODE_MEDIA_PREVIOUS    | Previous key.|
  | KEYCODE_MEDIA_REWIND    | Rewind key.|
  | KEYCODE_MEDIA_FAST_FORWARD    | 	Fast-forward key.|
  | KEYCODE_MEDIA_PLAY    | Play key.|
  | KEYCODE_MEDIA_PAUSE   | Pause key.|

  <!-- @[adaptingToBluetoothMethodTwo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/AdaptingToBluetoothMethodTwo.ets) -->  

  ``` TypeScript
  import { avSession as AVSessionManager } from '@kit.AVSessionKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  // ...
  
  @Entry
  @Component
  struct Index {
    @State message: string = 'hello world';
    // ...
  
    build() {
      Column() {
        // ...
        Text(this.message)
          .onClick(async () => {
            let context = this.getUIContext().getHostContext() as Context;
            let type: AVSessionManager.AVSessionType = 'audio';
            let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', type);
            // ...
            // Set the required media information. This is mandatory; otherwise, key events cannot be received.
            let metadata: AVSessionManager.AVMetadata = {
              assetId: '0', // Specified by the application to identify the media in the application's media library.
              title: 'TITLE',
              mediaImage: 'IMAGE',
              artist: 'ARTIST'
            };
            session.setAVMetadata(metadata).then(() => {
              console.info(`SetAVMetadata successfully`);
              // ...
            }).catch((err: BusinessError) => {
              console.error(`Failed to set AVMetadata. Code: ${err.code}, message: ${err.message}`);
              // ...
            });
            session.on('handleKeyEvent', (event) => {
              // Parse the keycode. The application needs to perform corresponding logic on the player based on the keycode.
              console.info(`on handleKeyEvent, keyCode=${event.key.code}`);
              // ...
            });
            // ...
          })
      }
      .width('100%')
      .height('100%')
      }
    }
  ```

> **NOTE**
>
> 1. Both methods require the accurate configuration of media information AVMetadata and the registration of corresponding control interfaces to receive control commands and key events.
> 2. Choose either method for integration. Method 1 is recommended.

<!--RP2--><!--RP2End-->