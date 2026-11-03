---
kits: ["Media Kit / Media Services"]
description: "Describes configuring external subtitles before AVPlayer video playback, loading srt subtitles through addSubtitleFromFd, displaying subtitles through subtitleUpdate callbacks, and hiding subtitles by unregistering the callback."
keywords: [AVPlayer, external subtitles, subtitle callbacks, subtitle resources, video playback]
doctype: guide
status: active
---

# Using AVPlayer to Add External Subtitles to Videos (ArkTS)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @chennotfound-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=f22e77cbcaa42a8fa1756926aaad60ac753033f0 translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

Currently, you can add external subtitles to a video only before it starts playing.

During application development, you can call **on('subtitleUpdate')** of an AVPlayer instance to listen for subtitle updates.

## How to Develop

Read [AVPlayer](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md) for the API reference.

1. Call [addSubtitleFromFd](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#addsubtitlefromfd12) to set an external subtitle resource in the AVPlayer instance used for video playback.
   <!-- @[addSubtitleFromFd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSSubtitle/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Call getRawFd of the resourceManager member of UIAbilityContext to obtain the media asset URL.
   // The return type is {fd,offset,length}, where fd indicates the file descriptor address of the HAP file, offset indicates the media asset offset, and length indicates the duration of the media asset to play.
   if (this.context == undefined) return;
   let fileDescriptorVideo = await this.context.resourceManager.getRawFd(this.fileName);
   let avFileDescriptor: media.AVFileDescriptor =
     { fd: fileDescriptorVideo.fd, offset: fileDescriptorVideo.offset, length: fileDescriptorVideo.length };
   
   if (this.avPlayer) {
     console.info(`${this.tag}: init avPlayer release2createNew`);
     this.avPlayer.release();
     await this.msleepAsync(1500);
   }
   // Create an AVPlayer instance.
   this.avPlayer = await media.createAVPlayer();
   
   // Set a callback function for state changes.
   await this.setAVPlayerCallback((avPlayer: media.AVPlayer) => {
     this.percent = avPlayer.width / avPlayer.height;
     this.setVideoWH();
     this.durationTime = this.getDurationTime();
     setInterval(() => { // Update the current time.
       if (!this.isSwiping) {
         this.currentTime = this.getCurrentTime();
       }
     }, SET_INTERVAL);
   });
   
   // Assign a value to fdSrc to trigger the reporting of the initialized state.
   this.avPlayer.fdSrc = avFileDescriptor;
   
   // Set the subtitle.
   let fileDescriptorSub = await this.context.resourceManager.getRawFd('test1.srt');
   this.avPlayer.addSubtitleFromFd(fileDescriptorSub.fd, fileDescriptorSub.offset, fileDescriptorSub.length);
   ```

2. Call [on('subtitleUpdate')](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#onsubtitleupdate12) to register a subtitle callback function.
   <!-- @[onSubtitleUpdate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSSubtitle/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Callback function for subtitle updates.
   this.avPlayer.on('subtitleUpdate', (info: media.SubtitleInfo) => {
     if (!!info) {
       let text = (!info.text) ? '' : info.text;
       let startTime = (!info.startTime) ? 0 : info.startTime;
       let duration = (!info.duration) ? 0 : info.duration;
       console.info(`${this.tag}: subtitleUpdate info: text=${text} startTime=${startTime} duration=${duration}`);
       this.subtitle = text;
     } else {
       console.info(`${this.tag}: subtitleUpdate info is null`);
     }
   });
   ```

3. (Optional) Unregister the subtitle callback from the AVPlayer instance used for video playback when subtitles are not needed.
   <!-- @[offSubtitleUpdate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSSubtitle/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // (Optional) Unregister the subtitle callback from the AVPlayer instance used for video playback when subtitles are not needed.
   async avTurnOffSubtitle() {
     this.avPlayer?.off('subtitleUpdate');
   }
   ```


## Running the Sample Project

1. Create a project, download the [sample project](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSSubtitle), and copy its resources to the corresponding directories.
   ```text
    AVPlayerArkTSSubtitle
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
        └── test1.srt (subtitle resource)
   ```

2. Compile and run the project.
