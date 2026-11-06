---
kits: ["Media Kit / Media Services"]
description: "Lists samples accompanying Media Kit guides, grouping ArkTS and C/C++ (NDK) examples by audio/video playback, recording, screen capture, transcoding, and metadata extraction scenarios."
keywords: [Media Kit, sample code, AVPlayer, AVRecorder, SoundPool, AVScreenCapture, AVTranscoder, AVMetadataExtractor]
doctype: guide
status: active
---

# Media Kit Samples
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia--> 
<!--Owner: @chennotfound-->
<!--Designer: @chennotfound-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=340b97ec406a889eaba3b079caf13ae5052ff9bb translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

| Category | Sample | Language | Scenario |
| -------- | -------- | -------- | -------- |
| Audio playback | [AVPlayerArkTSAudio](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSAudio) | ArkTS | Uses AVPlayer to play a complete music track, demonstrating a pause after 3 seconds and resumption after another 3 seconds. |
| Video playback | [AVPlayerArkTSVideo](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSVideo) | ArkTS | Uses AVPlayer to play a complete local video, demonstrating end-to-end playback. |
| Playback URL settings | [AVPlayerArkTSURL](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSURL) | ArkTS | Demonstrates setting AVPlayer playback URLs for streaming media and local files. |
| Streaming playback | [AVPlayerArkTSStreamingMedia](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSStreamingMedia) | ArkTS | Uses AVPlayer to play a complete streaming video, demonstrating buffering callbacks, HLS bitrate switching, DASH startup policies, and track switching. |
| External video subtitles | [AVPlayerArkTSSubtitle](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSSubtitle) | ArkTS | Uses AVPlayer to configure external subtitles and play a video, demonstrating addSubtitleFromFd and subtitleUpdate callbacks. |
| Short audio playback | [SoundPoolArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/SoundPool/SoundPoolArkTS) | ArkTS | Uses SoundPool for low-latency short audio playback, demonstrating one load followed by multiple playbacks. |
| Audio/video recording | [AVRecorder](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVRecorder/AVRecorder) | ArkTS | Uses AVRecorder to record audio and video, demonstrating the complete recording state machine. |
| Metadata extraction | [AVMetadataExtractorArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVMetadataExtractor/AVMetadataExtractorArkTS) | ArkTS | Uses AVMetadataExtractor to extract metadata from audio resources. |
| Video thumbnails | [AVImageGeneratorArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVImageGenerator/AVImageGeneratorArkTS) | ArkTS | Uses AVImageGenerator to obtain thumbnails from video resources. |
| Video transcoding | [AVTranscoderArkTS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVTranscoder/AVTranscoderArkTS) | ArkTS | Uses AVTranscoder for video transcoding, demonstrating the complete start, pause, resume, and completion workflow. |
| Asynchronous transcoding | [AsyncTranscoder](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVTranscoder/AsyncTranscoder) | ArkTS | Uses a Worker thread to run AVTranscoder video transcoding asynchronously. |
| Audio playback | [AVPlayerNDKAudio](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKAudio) | C/C++ | Uses AVPlayer to play a complete music track, demonstrating the full audio playback workflow through NDK APIs. |
| Video playback | [AVPlayerNDKVideo](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKVideo) | C/C++ | Uses AVPlayer to play a complete video, demonstrating the full video playback workflow through NDK APIs. |
| Streaming playback | [AVPlayerNDKStreamingMedia](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia) | C/C++ | Uses AVPlayer to play streaming media, demonstrating the full streaming playback workflow through NDK APIs. |
| Audio/video recording | [AVRecorderNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVRecorder/AVRecorderNDK) | C/C++ | Uses AVRecorder to record audio and video, demonstrating the complete recording state machine. |
| Screen capture | [ScreenCaptureSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample) | ArkTS, C/C++ | Uses AVScreenCapture for screen recording, covering file output, window-level capture, rectangular area capture, and custom capture scenarios. |
| Metadata extraction | [AVMetadataExtractorNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVMetadataExtractor/AVMetadataExtractorNDK) | C/C++ | Uses AVMetadataExtractor to extract metadata from audio resources. |
| Video thumbnails | [AVImageGeneratorNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVImageGenerator/AVImageGeneratorNDK) | C/C++ | Uses AVImageGenerator to obtain thumbnails from video resources. |
| Video transcoding | [AVTranscoderNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVTranscoder/AVTranscoderNDK) | C/C++ | Uses AVTranscoder (C/C++) for video transcoding, demonstrating the complete start, pause, resume, and completion workflow. |
