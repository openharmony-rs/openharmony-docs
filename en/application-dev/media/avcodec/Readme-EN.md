# AVCodec Kit

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @rchdlee-->
<!--Designer: @dpy2650-->
<!--Tester: @cyakee; @baotianhao-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a97bafa60b418a6aa9bd1a00412d13c18f9a66e3 translatedAt=2026-10-22T13:52:24.789Z pushedAt=2026-10-22T13:59:04.534Z nl=1 -->

- [About This Kit](avcodec-kit-intro.md)
- [AVCodec Supported Formats](avcodec-support-formats.md)
- Audio and Video Codecs<!--audio-video-codec-->
  - [Obtaining Supported Codecs](obtain-supported-codecs.md)
  - Audio Codec<!--audio-base-codec-->
    - [Asynchronous Audio Encoding](audio-encoding.md)
    - [Asynchronous Audio Decoding](audio-decoding.md)
    - [Synchronous Audio Encoding](synchronous-audio-encoding.md)
    - [Synchronous Audio Decoding](synchronous-audio-decoding.md)
  - Video Codec<!--video-base-codec-->
    - [Asynchronous Video Encoding](video-encoding.md)
    - [Asynchronous Video Decoding](video-decoding.md)
    - [Synchronous Video Encoding](synchronous-video-encoding.md)
    - [Synchronous Video Decoding](synchronous-video-decoding.md)
    - [Video Encoding Preprocessing](video-encoding-preproc.md)
    - [Video Encoding with One Input and Dual Outputs](video-encoding-preproc-one-in-dual-out.md)
  - Low-Power Strategy for Smooth Video Playback<!--audio-video-low-power-consumption-codec-->
    - [Video Variable Frame Rate](video-variable-refreshrate.md)
    - [Intelligent Smooth High-Speed Playback Decoding](video-smart-fluency-decoding.md)<!--RP1--><!--RP1End-->
  - Typical Video Encoding and Decoding Scenario Practices<!--audio-video-typical-scenarios-codec-->
    - [Basic Configuration for Video Encoding in Various Scenarios](video-encoding-configuration-typical-scenarios.md)
    - [High-Compression-Ratio B-Frame Encoding](video-encoding-b-frame.md)
    - [ROI Encoding for a Clearer Specified Region](video-encoding-ROI.md)
    - [Temporal Scalable Encoding with Packet Loss Resilience in Poor Network Conditions](video-encoding-temporal-scalability.md)<!--RP2--><!--RP2End-->
- Media Data Multiplexing and Demultiplexing<!--file-muxing-demuxing-->
  - [Media Data Multiplexing](audio-video-muxer.md)
  - [Media Data Demultiplexing](audio-video-demuxer.md)
- AVCodec Kit FAQs<!--file-avcodec-kit-faq-->
  - [Concurrently Creating a Video Decoder and Initializing NativeWindow](parallel-decoding-nativeWindow.md)
  - [Video Codec Width, Height, Stride, and Crop Information](video-dimension-guide.md)
- [Glossary](avcodec-glossary.md)