# Local AVSession FAQs
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=9db8f1f2d5fb9478a25d79ce8f5ed2a1d2c3c91f translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

This document summarizes typical issues encountered by audio and video apps during local media session integration with [AVSession Kit](avsession-overview.md), along with their diagnosis and resolution methods. You can use [AVSession management error codes](../../reference/apis-avsession-kit/errorcode-avsession.md) and HiLog logs to further diagnose issues.

## AVSession Creation Failure

**Symptom**

An exception is thrown when [createAVSession](../../reference/apis-avsession-kit/arkts-apis-avsession-f.md#avsessioncreateavsession10) is called, and the session is not created successfully.

**Possible Causes**

- Duplicate creation of an AVSession session object. Only one AVSession object can exist in a process.
- In scenarios where AVSession objects are frequently created and destroyed, the old session may not have been fully destroyed. The destroy call is an asynchronous process. If the app creates a new AVSession immediately after calling destroy, the new session creation may fail because the previous session has not been completely destroyed.
- The context input parameter is invalid. The context parameter of createAVSession must use a valid context of the app.
- The `type` parameter value is invalid. `type` must be a value defined in [AVSessionType](../../reference/apis-avsession-kit/arkts-apis-avsession-t.md#avsessiontype10) (`audio`/`video`/`voice_call`/`video_call`/`photo`). Passing any other string causes validation failure.
- Other required parameters are passed with invalid values. The `context`, `tag`, and `type` parameters of createAVSession are all required. Any missing or invalid parameter throws an exception.

**Solution**

1. Check whether a live AVSession already exists. If necessary, call [destroy](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#destroy10) to release the old session before creating a new one. Before creation, you can also call [getAVSession](../../reference/apis-avsession-kit/arkts-apis-avsession-f.md#avsessiongetavsession22) to check whether the current app has already created a session object, and then decide whether to destroy the old session or reuse the existing one.
2. In scenarios involving frequent creation and destruction, listen for the [on('sessionDestroy')](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#onsessiondestroy10) event through the media session controller, and create a new AVSession object only after receiving the old session destruction callback.

    ```TypeScript
    import { avSession } from '@kit.AVSessionKit';

    async destroyAndRecreateAVSession(context: Context) {
        let videoSession: avSession.AVSession;
        let avSessionController: avSession.AVSessionController;
        try {
            // Create the AVSession for the first time and obtain its controller.
            videoSession = await avSession.createAVSession(context, 'VIDEO_SESSION', 'video');
            avSessionController = await videoSession.getController();

            // Register a session destruction listener. The callback is triggered after the session is destroyed.
            avSessionController.on('sessionDestroy', async () => {
                // Create the AVSession for the second time. After destruction, recreate a session of the same type.
                videoSession = await avSession.createAVSession(context, 'VIDEO_SESSION', 'video');
                // Destroy the AVSession for the second time.
                await videoSession.destroy();
            });

            // Destroy the AVSession for the first time, which triggers the sessionDestroy callback above.
            await videoSession.destroy();
        } catch (err) {
            console.error(`AVSession create Error: Code: ${err.code}, message: ${err.message}`);
        }
    }
    ```

3. It is recommended to obtain the context through `this.getUIContext().getHostContext() as Context` to avoid passing undefined or a context that does not belong to the current UIAbility.
4. Ensure that type is a valid value defined in [AVSessionType](../../reference/apis-avsession-kit/arkts-apis-avsession-t.md#avsessiontype10).
5. Ensure that all required parameters are valid non-null values. For example, avoid passing invalid values such as an empty string for `tag`.

## Audio and Video Forcibly Paused After App Is Relegated to Background

**Symptom**

After the app is switched to the background, audio and video playback is forcibly paused by the system, and the user cannot continue listening.

**Possible Causes**

- AVSession not integrated. The system enforces strict control over audio and video apps that have not integrated AVSession when they are in the background. When the stream type is `STREAM_USAGE_MUSIC`, `STREAM_USAGE_MOVIE`, `STREAM_USAGE_AUDIOBOOK`, or `STREAM_USAGE_GAME`, AVSession must be integrated.
- Continuous task not requested. Integrating AVSession alone is insufficient to ensure background playback. A continuous task must also be requested; otherwise, the app will be suspended or frozen after entering the background.
- AVSession instance reclaimed. The AVSession object must persist throughout the background playback activity. If the session is stored in a local variable, the object is released after the method returns. The system then determines that the app has no valid AVSession instance and forcibly pauses the audio.
- AVSession creation failure causes the app to not hold a valid session.
- The background playback mode is set incorrectly.

**Solution**

1. Refer to [Accessing AVSession](avsession-background-scene.md#accessing-avsession) in Background Playback to complete AVSession integration.
2. Apply for an `AUDIO_PLAYBACK` type [continuous task (ArkTS)](../../task-management/continuous-task.md).
3. Use a class member variable to hold the session instance, and release it only when the app process ends or the playback service exits.
4. Check the related causes in [AVSession Creation Failure](#avsession-creation-failure) one by one to ensure that the app holds a valid session.
5. Before the app is relegated to the background, call [setBackgroundPlayMode](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setbackgroundplaymode24) to set the background playback mode ([BackgroundPlayMode](../../reference/apis-avsession-kit/arkts-apis-avsession-e.md#backgroundplaymode24)), which informs the system whether to continue playback when the app goes to the background:

     - `ENABLE_BACKGROUND_PLAY` (supports background playback): The app continues playback when relegated to the background.
     - `DISABLE_BACKGROUND_PLAY` (does not support background playback): The app stops playback when relegated to the background.

     For apps with [AVSessionType](../../reference/apis-avsession-kit/arkts-apis-avsession-t.md#avsessiontype10) set to `audio`, the default value is `ENABLE_BACKGROUND_PLAY`; for apps with the type set to `video`, the default value is `DISABLE_BACKGROUND_PLAY`. If a video app needs to support background audio playback, you must explicitly set it to `ENABLE_BACKGROUND_PLAY`. If the app provides a "whether background playback is supported" switch, the background playback mode set must be consistent with the switch state; otherwise, the app may be forcibly paused after being relegated to the background, or the system Live View may display incorrectly. The following is a setup example:

     ```TypeScript
     import { avSession } from '@kit.AVSessionKit';
     import { BusinessError } from '@kit.BasicServicesKit';

     // Assume that currentAVSession has been created and is held.
     async setBackgroundPlayMode(currentAVSession: avSession.AVSession) {
       try {
         await currentAVSession.setBackgroundPlayMode(avSession.BackgroundPlayMode.ENABLE_BACKGROUND_PLAY);
         console.info(' Succeeded in setBackgroundPlayMode');
       } catch (err) {
         let error = err as BusinessError;
         console.error(`setBackgroundPlayMode BusinessError: code: ${error.code}, message: ${error.message}`);
       }
     }
     ```

     For more details, see [Configuring Background Playback Mode](avsession-background-scene.md#configuring-background-playback-mode).

<!--RP1--><!--RP1End-->