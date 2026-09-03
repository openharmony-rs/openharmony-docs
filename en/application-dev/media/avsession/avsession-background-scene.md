# Background Playback
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=5b3ab60fe000eb4bad70440a3e7f30019a2671f9 translatedAt=2026-09-03T06:54:08.110Z pushedAt=2026-09-03T07:24:02.974Z -->

In real-world application scenarios, most audio and video applications require background playback. This guide describes in detail how to implement long-duration background playback.

## Basic Concepts

Before diving in, you should understand the following basic concepts to effectively implement background playback based on your player type.

- Continuous task: Refer to [Continuous Tasks (ArkTS)](../../task-management/continuous-task.md).

  Actions such as returning to the home screen, locking the screen, or switching applications can push an application to the background. When an application is pushed to the background and resumes activity, it may cause rapid battery drain and UI lag. To reduce battery consumption and ensure a smooth user experience, the system manages applications pushed to the background, including process suspension and termination. If an application has a perceivable task that needs to run in an extended period of time in the background, it can request a continuous task to prevent itself from being suspended. Examples of continuous tasks include music playback and video playback in the background.

- AVSession: Refer to [Introduction to AVSession Kit](../avsession/avsession-overview.md).

  AVSession Kit is a system-provided audio and video playback control service used to uniformly manage audio and video behaviors in the system, helping you quickly build unified display and control capabilities for audio and video. After an audio and video application integrates with AVSession, it can set its data (such as the song being played and the playback status of the song). Users can display and control the playback of different applications through the Media Controller. AVSession imposes constraints on media playback in the background. Therefore, audio applications, audiobook applications, video applications, and the like all need to integrate with AVSession. If an application performs the preceding services without creating an AVSession, the system stops the corresponding audio and video playback when it detects that the application has moved to the background, so as to constrain the application behavior.

- AVPlayer: For details, see [AVPlayer](../media/media-kit-intro.md#avplayer).

  AVPlayer is a powerful media player that can play various audio and video formats (such as mp4, mp3, mkv, mpeg-ts) end to end. You only need to provide the media source to start playback without worrying about complex demultiplexing and decoding processes.

- AudioRenderer: For details, see [Using AudioRenderer for Audio Playback (ArkTs)](../audio/using-audiorenderer-for-playback.md).

  AudioRenderer is an audio renderer used to play Pulse Code Modulation (PCM) audio data. Compared with AVPlayer, AudioRenderer allows data preprocessing before input, making it more suitable for developers with audio development experience to achieve more flexible playback features.

## Application Access Standards

- When an application needs to play media stream (stream types `STREAM_USAGE_MUSIC`, `STREAM_USAGE_MOVIE`, and `STREAM_USAGE_AUDIOBOOK`) and game stream (stream type `STREAM_USAGE_GAME`) in the background, it must integrate with AVSession and request a continuous task. For details about stream types, refer to [Choosing the Right Playback Stream Type](../audio/using-right-streamusage-for-playback.md). For details about the types supported by continuous tasks, refer to [BackgroundMode](../../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundmode).

- In addition to the aforementioned playback types, when an application needs to run other user-perceptible tasks in the background for a long time, it must request continuous tasks of the AUDIO_PLAYBACK type.

If an application does not meet the above access standards, playback in the background will be muted and frozen by the system, preventing normal background playback. Playback will only resume and unmute when the application is brought back to the foreground.

## How to Develop

The basic steps for audio and video applications to achieve background playback are as follows:

### Starting the Player

You can play audio and video using AudioRenderer, AVPlayer, or other third-party or custom players.

- AudioRenderer: When using AudioRenderer to create an audio stream, pay attention to using the appropriate audio stream type. Different stream types have a decisive impact on volume control, audio focus management, and input/output devices. For details, refer to [Choosing the Right Playback Stream Type](../audio/using-right-streamusage-for-playback.md).<br>
  In addition, you must correctly handle audio focus. The system presets default audio focus strategies that uniformly manage all playback and recording audio streams based on the type of audio stream and the order in which they are started. During audio playback or recording, if another audio stream requests focus, the system handles the focus according to the focus strategy. If it determines that the focus of the current audio stream has changed, the system automatically performs necessary operations (such as pausing, resuming, lowering the volume, and restoring the volume) and notifies the application through an audio focus event (InterruptEvent). For details, refer to [Handling Audio Focus Changes](../audio/audio-playback-concurrency.md#handling-audio-focus-changes).<br>
  For development guidance, refer to [Using AudioRenderer for Audio Playback (ArkTS)](../audio/using-audiorenderer-for-playback.md).

- AVPlayer: Using AVPlayer can achieve end-to-end playback of raw media resources. To achieve background playback or playback with the screen off, you need to access AVSession and request continuous tasks to prevent playback from being forcibly interrupted by the system. [AVPlayer](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md) can set the focus management strategy through the **audioInterruptMode** property, which defaults to **SHARE_MODE**.
  For details about the development, see [Using AVPlayer to Play Audio (ArkTS)](../media/using-avplayer-for-playback.md).

### Accessing AVSession

When the created audio stream type is `STREAM_USAGE_MUSIC`, `STREAM_USAGE_MOVIE`, `STREAM_USAGE_AUDIOBOOK`, or `STREAM_USAGE_GAME`, you must integrate with AVSession regardless of whether the application moves to the background to continue playback or starts playback in the background.

It is recommended that you create an AVSession before the application starts or before starting the playback service, and release it when the application process ends or exits the playback service, to avoid frequent creation and release that affect playback continuity. During background playback, ensure that the AVSession object instance always exists and is not reclaimed by the system, for example, by storing it in a class member variable instead of a local variable.

After creating an AVSession, to ensure user experience, you must set the following metadata and register the following control commands.

- Metadata: title, subtitle/artist, and cover image. For details, see [Setting Metadata](avsession-access-scene.md#setting-metadata-information).

- Register control commands: play and pause. For details, see [Registering Control Commands](avsession-access-scene.md#control-command-processing).

For details about how to access AVSession, see [Accessing AVSession](avsession-access-scene.md).

### Requesting Continuous Tasks

You can request various types of continuous tasks. For example, when the background audio playback task type is `AUDIO_PLAYBACK`, the application can request a continuous task of type `AUDIO_PLAYBACK` when playing audio or video in the background or casting through the AVSession casting component.
- Request a continuous task during playback. If the application explicitly has background playback service (for example, a video application enables background playback options), you can request a continuous task during foreground playback.
- Actively cancel the continuous task when pausing or stopping. For example, when the user actively taps to pause music playback, the application needs to promptly cancel the corresponding continuous task; when the user taps to play music again, the application needs to request a continuous task again.
- If audio playback in the background is interrupted (for example, by focus interruption), the system automatically detects and freezes or cancels the continuous task. When the application restarts audio playback, it needs to request a continuous task again.
- When the application receives AVSession playback control commands or audio device changes that require corresponding playback and pause operations, it needs to cancel the continuous task when pausing and request a continuous task again when playing.
- When casting in the background through the AVSession casting component, request a continuous task when starting the cast and cancel it when disconnecting. If audio playback is paused during casting, no processing is required for the continuous task.

For details, see [Continuous Task (ArkTS)](../../task-management/continuous-task.md#how-to-develop).

### Listening for Foreground and Background States

If the application does not have background playback service, you can use the lifecycle function [onBackground](../../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onbackground) to determine whether the application has entered the background and proactively stop playback. Otherwise, it will be affected by AVSession and continuous task module management, impacting the application's normal playback. If you need to restart playback when the application returns to the foreground, use the lifecycle function [onForeground](../../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onforeground) to determine whether the application is back in the foreground.

## Configuring Background Playback Mode

Before the application moves to the background, you can call [setBackgroundPlayMode](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setbackgroundplaymode24) to configure the background playback mode and inform the system whether the application has playback behavior when it moves to the background. When you configure the background playback mode for an audio and video application, the system determines whether to display the system live window when the application moves to the background based on the value you set.

### Playback Mode Description

The system supports two playback modes:
- **ENABLE_BACKGROUND_PLAY (supports background playback)**: The app continues playback when moved to the background.
- **DISABLE_BACKGROUND_PLAY (does not support background playback)**: The app stops playback when moved to the background.

> **NOTE**
>
> 1. For an application whose [AVSessionType](../../reference/apis-avsession-kit/arkts-apis-avsession-t.md#avsessiontype10) is `audio`, the system default value is `ENABLE_BACKGROUND_PLAY`; for an application whose [AVSessionType](../../reference/apis-avsession-kit/arkts-apis-avsession-t.md#avsessiontype10) is `video`, the system default value is `DISABLE_BACKGROUND_PLAY`.
>
> 2. Before moving to the background, an audio and video application should set the correct background playback mode to ensure that the system live window is displayed correctly when the application moves to the background. If the application provides a switch such as "whether to support background playback", the background playback mode set by the application must be consistent with the switch state in the application.

### How to Develop

The development steps for background playback of an audio and video application are as follows.

1. Before configuring the background playback mode, create an AVSession. It is recommended that you create the session when the application starts or when playback begins. For details, refer to [Accessing AVSession](#accessing-avsession).

2. After creating the AVSession, call [setBackgroundPlayMode](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setbackgroundplaymode24) before the application moves to the background to set the accurate background playback mode.

 <!-- @[setBackgroundPlayMode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession/entry/src/main/ets/pages/SetBackgroundPlayMode.ets) -->

 ``` TypeScript
 import { avSession } from '@kit.AVSessionKit';
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
           let currentAVSession: avSession.AVSession | undefined = undefined;
           let tag = 'createNewSession';
           let context: Context = this.getUIContext().getHostContext() as Context;
           // Assume that a session has been created. For details about how to create a session, refer to the previous example.
           avSession.createAVSession(context, tag, 'audio', (err: BusinessError, data: avSession.AVSession) => {
             if (err) {
               console.error(`CreateAVSession BusinessError: code: ${err.code}, message: ${err.message}`);
             } else {
               currentAVSession = data;
             }
           });
           // Set the background playback mode.
           if (currentAVSession !== undefined) {
             try {
               (currentAVSession as avSession.AVSession)
                 .setBackgroundPlayMode(avSession.BackgroundPlayMode.ENABLE_BACKGROUND_PLAY);
               // ...
             } catch (err) {
               console.error(`setBackgroundPlayMode BusinessError: code: ${err.code}, message: ${err.message}`);
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

 <!--RP1--><!--RP1End-->

<!--no_check-->
