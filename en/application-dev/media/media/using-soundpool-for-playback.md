# Using SoundPool to Play Short Sounds (ArkTS)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=abc15d7bb8be02d9aa7005197435e9f85d20e257 translatedAt=2026-11-09T07:46:15.398Z pushedAt=2026-11-09T08:11:55.986Z nl=1 -->

The [SoundPool](media-kit-intro.md#soundpool) class provides APIs to implement low-latency playback of short sounds.

Short sound effects (such as the camera shutter sound effect and system notification sound effect) are often required during application development. You can call the APIs provided by SoundPool to implement one-time loading of short sounds and multiple times of low-latency playback.

SoundPool currently supports playing of audio files that are under 1 MB in size after decoding. For audio files that exceed this limit after decoding, only the first 1 MB of data is played. This is equivalent to approximately 5.6 seconds of audio duration at a 44.1 kHz sampling rate with 16-bit depth for stereo sound. (At lower sampling rates or in mono mode, the duration may be slightly longer.)

This topic walks you through on how to use the SoundPool APIs to implement low-latency playback. For details about the API declaration, see [SoundPool](../../reference/apis-media-kit/js-apis-inner-multimedia-soundPool.md).

The full process includes creating a SoundPool instance, loading a sound (including decapsulation and decoding), setting playback parameters (loop mode, and playback priority), playing the sound, stopping the playback, and releasing the instance. (For details about the decoding formats, see [Audio Decoding](../avcodec/audio-decoding.md).)

During application development, you must subscribe to playback state changes and call the APIs in the defined sequence. Otherwise, an exception or undefined behavior may occur.

> **NOTE**
>
> For details about the audio focus strategy when SoundPool is used to play short sounds, see [Introduction to Audio Focus and Audio Session](../audio/audio-playback-concurrency.md).

## How to Develop

1. Call [createSoundPool](../../reference/apis-media-kit/arkts-apis-media-f.md#mediacreatesoundpool10-1) to create a SoundPool instance.

   <!-- @[SoundPool_Create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // The value of the usage parameter in audioRendererInfo is STREAM_USAGE_UNKNOWN, STREAM_USAGE_MUSIC, or STREAM_USAGE_MOVIE.
   // or STREAM_USAGE_AUDIOBOOK, SoundPool plays a short sound in audio mixing mode, without interrupting the playback of other audio streams.
   let audioRendererInfo: audio.AudioRendererInfo = {
     usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
     rendererFlags: 1 // AudioRenderer flag.
   }
   // Create a SoundPool instance.
   this.soundPool = await media.createSoundPool(14, audioRendererInfo);
   ```

2. Call [on('loadComplete')](../../reference/apis-media-kit/js-apis-inner-multimedia-soundPool.md#onloadcomplete) to listen for the completion of sound loading.

   <!-- @[SoundPool_onLoadComplete](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Callback invoked when the sound finishes loading.
   this.soundPool!.on('loadComplete', (soundId_: number) => {
     this.soundId = soundId_;
     console.info('loadComplete soundId: ' + soundId_);
   })
   ```

3. Call **on('playFinished')** or **on('playFinishedWithStreamId')** to listen for the completion of audio playback.

    When only the **'playFinished'** or **'playFinishedWithStreamId'** event callback is registered, the registered callback is triggered when audio playback finishes.

    When both the **'playFinished'** and **'playFinishedWithStreamId'** event callbacks are registered, only the **'playFinishedWithStreamId'** event callback is triggered when audio playback finishes. The **'playFinished'** event callback is not triggered.

   <!-- @[SoundPool_onPlayFinished](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   this.soundPool!.on('playFinished', () => {
     console.info('receive play finished message');
     // The next playback can be performed.
   })
   ```

4. Call **on('error')** to listen for errors that may occur.

   <!-- @[SoundPool_onError](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   this.soundPool!.on('error', (error: BusinessError) => {
     console.error('error happened,message is :' + error.code);
     console.error('error happened,message is :' + error.message);
   })
   ```

5. Call **load()** to load a sound.

    You can pass in a URI or an FD to load the sound. The following uses the FD as an example. For more methods, see [load](../../reference/apis-media-kit/js-apis-inner-multimedia-soundPool.md#load).

    When the system finishes loading the sound, the **loadComplete** callback is invoked to notify the user that the loading is complete. Perform the subsequent play operation after the callback is received.

   <!-- @[SoundPool_Load](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let context = this.getUIContext().getHostContext();;
   let fileDescriptor = await context!.resourceManager.getRawFd('test.ogg');
   this.soundId = await this.soundPool!.load(fileDescriptor.fd, fileDescriptor.offset, fileDescriptor.length);
   console.info(`load soundPool soundId: ${this.soundId}`)
   ```

6. Set **PlayParameters**, and call **play** after the **loadComplete** callback is received. If **play()** with the same sound ID passed in is called for multiple times, the sound is played only once.

   <!-- @[SoundPool_Play](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let playParameters: media.PlayParameters = {
     loop: 1, // Loop once, that is, play twice.
     rate: 1, // Play at 1x speed.
     leftVolume: 0.5, // Value range: [0.0, 1.0].
     rightVolume: 0.5, // Value range: [0.0, 1.0].
     priority: 0, // Lowest priority.
   };
   // Start playback. Here, play can also carry the playback parameter PlayParameters. Perform the play operation only after the audio resource is loaded, that is, after the loadComplete callback is received.
   this.soundPool!.play(this.soundId, playParameters, (error, streamID: number) => {
     if (error) {
       console.error(`play sound Error: errCode is ${error.code}, errMessage is ${error.message}`)
     } else {
       this.streamId = streamID;
       console.info('play success soundid:' + this.streamId);
     }
   });
   ```

7. Call **setLoop()** to set the number of loops.

   <!-- @[SoundPool_SetLoop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Set the number of loops.
   await this.soundPool!.setLoop(this.streamId, 2); // Play three times.
   ```

8. Call **setPriority()** to set the playback priority.

   <!-- @[SoundPool_SetPriority](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Set the priority of the corresponding stream.
   await this.soundPool!.setPriority(this.streamId, 1);
   ```

9. Call **setVolume()** to set the playback volume.

   <!-- @[SoundPool_SetVolume](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Set the volume.
   await this.soundPool!.setVolume(this.streamId, 0.5, 0.5);
   ```

10. Call **stop()** to stop the playback.

    <!-- @[SoundPool_Stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    // Stop the playback of the stream.
    await this.soundPool!.stop(this.streamId);
    ```

11. Call **unload()** to unload a sound.

    <!-- @[SoundPool_Unload](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    // Unload the sound.
    await this.soundPool!.unload(this.soundId);
    ```

12. Call **off('loadComplete')** to stop listening for the completion of sound loading.

    <!-- @[SoundPool_offLoadComplete](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    this.soundPool!.off('loadComplete');
    ```

13. Call **off('playFinished')** to stop listening for the completion of audio playback.

    <!-- @[SoundPool_offPlayFinished](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    this.soundPool!.off('playFinished');
    ```

14. Call **off('error')** to stop listening for errors.

    <!-- @[SoundPool_offError](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    this.soundPool!.off('error');
    ```

15. Call **release()** to release the SoundPool instance.

    <!-- @[SoundPool_Release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    // Release the SoundPool instance.
    await this.soundPool!.release();
    ```

## Running the Sample Project

Refer to the sample project to use SoundPool to play audio at a low latency.

1. Create a project, download the [sample project](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS), and copy its resources to the corresponding directories.

    ```txt
    SoundPoolArkTS
    entry/src/main/ets/
    └── pages
        └── Index.ets (Playback UI)
    entry/src/main/resources/
    ├── base
    │   ├── element
    │   │   ├── color.json
    │   │   ├── float.json
    │   │   └── string.json
    │   └── media
    │
    └── rawfile
        └── test.ogg (Audio resource)
    ```
2. Compile and run the project.