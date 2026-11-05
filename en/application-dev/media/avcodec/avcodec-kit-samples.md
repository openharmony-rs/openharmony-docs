---
kits: ["AVCodec Kit / Audio and Video Codec Services"]
description: "Lists the sample projects accompanying AVCodec Kit guides, covering video and audio encoding and decoding, media muxing and demuxing, smart high-speed decoding, temporal scalability encoding, and ROI video encoding."
keywords: [AVCodec Kit, sample code, video encoding and decoding, audio encoding and decoding, muxing, demuxing, intelligent smooth high-speed playback decoding, temporal scalability encoding, ROI encoding]
doctype: guide
status: active
---

# AVCodec Kit Samples

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @rchdlee-->
<!--Designer: @dpy2650-->
<!--Tester: @cyakee; @baotianhao-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=9f06eb06466b30d0e7330f8a46c6f2bf0a90b096 translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

| Category | Sample | Language | Scenario |
| -------- | -------- | -------- | -------- |
| Video encoding and decoding | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | C/C++ | Uses AVCodec Kit (C/C++) for video encoding and decoding, with hardware, software, and automatic decoder selection (including software fallback), Surface and Buffer modes, and OpenGL and Vulkan rendering. Supports camera input through the encoder Surface and H.264/H.265 output in both synchronous and asynchronous modes. |
| Audio encoding and decoding | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | C/C++ | Uses AVCodec Kit (C/C++) for audio encoding and decoding. During playback, decodes AAC, MP3, FLAC, and other bitstreams into PCM for playback through AudioRenderer callbacks. During recording, captures PCM through AudioCapturer and encodes it into AAC using the configured sampling rate, channel count, and bitrate. Covers synchronous and asynchronous modes. |
| Media data muxing and demuxing | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | C/C++ | Demuxes media files such as mp4, mkv, and mpeg-ts during playback to obtain track information and audio/video samples. During recording, muxes encoded audio and video into mp4 and flv files. |
| Intelligent smooth high-speed playback decoding | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | C/C++ | Uses the adaptive (ADAPTIVE) frame retention policy for X2/X3 playback, switches to full (FULL) retention at X1, and switches to uniform (UNIFORM) retention on thermal warnings, demonstrating decoding load reduction and power optimization during high-speed playback. |
| Temporal scalability encoding | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | C/C++ | Demonstrates output callback handling for temporal scalability encoding. Obtains temporal layer information through OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_LAYER_ID and scales the frame rate by dropping bitstream layers to dynamically adjust the bitrate for poor network conditions. |
| ROI video encoding | [ROISample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVCodec/ROISample) | C/C++ | Demonstrates live streaming ROI encoding, from camera capture and OpenGL rendering to ROI extraction, configuration, encoding, and mp4 muxing. Covers NativeBuffer metadata configuration, encoder input parameter callbacks, and Buffer frame data, as well as common live streaming features such as background music and front/rear camera switching. |
