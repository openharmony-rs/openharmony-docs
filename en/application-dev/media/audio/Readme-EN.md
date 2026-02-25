# Audio Kit
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

- [About This Kit](audio-kit-intro.md)
- [Selecting the Appropriate Audio Stream Types](using-right-streamusage-and-sourcetype.md)
- Audio Focus and Audio Session Management<!--audio-session-->
  - [Introduction to Audio Focus and Audio Sessions](audio-playback-concurrency.md)
  - [Using AudioSession to Manage Audio Focus (ArkTS)](audio-session-management.md)
  - [Using AudioSession to Manage Audio Focus (C/C++)](using-ohaudio-for-session.md)
- Audio Playback<!--audio-playback-->
  - [Audio Playback Overview](audio-playback-overview.md)
  - [(Recommended) Using OHAudio for Audio Playback (C/C++)](using-ohaudio-for-playback.md)
  - [Using AudioRenderer for Audio Playback (ArkTs)](using-audiorenderer-for-playback.md)
  <!--Del-->
  - [Using TonePlayer for Audio Playback (for System Applications Only)](using-toneplayer-for-playback-sys.md)
  <!--DelEnd-->
  - [Low-Latency Audio Playback (C/C++)](audio-fast-playback.md)
  - [Low-Power Audio Playback](power-saving-for-playback.md)
  - [Using AudioHaptic for Audio-Haptic Playback (ArkTs)](using-audiohaptic-for-playback.md)
  - [Using SoundPlayer for System Sound Effect Playback](using-soundplayer-for-playback.md)
  - [Volume Management](volume-management.md)
  - [Spatial Audio Capability Query and Status Subscription](public-audio-spatialization-management.md)
  <!--Del-->
  - [Spatial Audio Management (for System Applications Only)](audio-spatialization-management-sys.md)
  <!--DelEnd-->
  - [Audio Playback Stream Management](audio-playback-stream-management.md)
  <!--Del-->
  - [Distributed Audio Playback (for System Applications Only)](distributed-audio-playback-sys.md)
  <!--DelEnd-->
  <!--Del-->
  - [Collaborative Audio Management (for System Applications Only)](audio-collaborative-management-sys.md)
  <!--DelEnd-->
- Audio Recording<!--audio-recording-->
  - [Audio Recording Overview](audio-recording-overview.md)
  - [(Recommended) Using OHAudio for Audio Recording (C/C++)](using-ohaudio-for-recording.md)
  - [Using AudioCapturer for Audio Recording (ArkTs)](using-audiocapturer-for-recording.md)
  - [Low-latency Audio Recording (C/C++)](audio-fast-recording.md)
  - [Managing Microphone Mute Status](mic-management.md)
  - [Querying and Listening for the Recording Status of Other Applications](audio-recording-stream-management.md)
  - [Recording Concurrency Strategy Description](audio-recording-concurrency.md)
  - [Audio Monitoring](audio-ear-monitor.md)
  - [Low-Latency Audio Monitoring](audio-ear-monitor-loopback.md)
- Audio Device Routing Management<!--audio-device-->
  - [Querying and Listening for Audio Input Devices](audio-input-device-management.md)
  - [Querying and Listening for Audio Output Devices](audio-output-device-management.md)
  - [Switching Audio Input Devices](audio-input-device-switcher.md)
  - [Switching Audio Output Devices](audio-output-device-switcher.md)
  - [Handling Output Device Changes Gracefully](audio-output-device-change.md)
- Audio Call<!--audio-call-->
  - [Audio Call Overview](audio-call-overview.md)
  - [Developing Audio Call](audio-call-development.md)
- Audio Performance Optimization<!--audio-performance-optimization-->
  - [Enhancing Audio Performance Experience](audio-performance.md)
  - [Audio Workgroup Management](audio-workgroup.md)
- Audio Creation<!--audio-production-creation-->
  - [Audio Creation Overview (C/C++)](audio-suite.md)
  - [Offline Editing (C/C++)](audio-suite-manual-rendering.md)
  - [Real-Time Rendering (C/C++)](audio-suite-real-time-rendering.md)
- OpenSL ES Development (Not Recommended)<!--not-recommended-->
  - [Switching from OpenSL ES to OHAudio (C/C++)](replace-opensles-by-ohaudio.md)
  - [Using OpenSL ES for Audio Playback (C/C++)](using-opensl-es-for-playback.md)
  - [Using OpenSL ES for Audio Recording (C/C++)](using-opensl-es-for-recording.md)
