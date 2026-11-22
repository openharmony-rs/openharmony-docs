---
kits: ["Media Kit / Media Services"]
description: "Summarizes common AVTranscoder issues, including automatic audio codec changes and handling transcoding failures, for troubleshooting video transcoding."
keywords: [AVTranscoder, transcoding, FAQs, audio encoding formats, AAC, transcoding failure, error handling, format support]
doctype: faq
status: active
---
# Transcoding FAQs
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @yangde_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=c54ee3c703f5cc7ef1444d6932d400b405f9ea74 translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

## Why does the audio encoding format change when the application sends a video for transcoding?

If no audio encoding format is specified during transcoding, the system converts the audio to AAC by default.

<!--RP2--><!--RP2End-->

## What should I do if the transcoding capabilities provided by the system fail to be called?

1. Check whether the current transcoding system supports the video and the target video format settings.

   Topics describing the transcoding capabilities: [AVTranscoder](media-kit-intro.md#avtranscoder), [AVCodec Supported Formats](../avcodec/avcodec-support-formats.md)<!--RP1--><!--RP1End-->

2. When receiving an error event, the application should send the source video. When receiving a complete event, the application first calls **release** before performing operations such as sending or uploading the transcoded video.
