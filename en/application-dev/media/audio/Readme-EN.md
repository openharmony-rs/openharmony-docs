# Audio Kit
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

- [Introduction to Audio Kit](audio-kit-intro.md)
- [Selecting the Appropriate Audio Stream Types](using-right-streamusage-and-sourcetype.md)
- [Introduction to Audio Focus and Audio Sessions](audio-playback-concurrency.md)
- Audio Focus Management<!--audio-session-->
  - [Using AudioSession to Manage Audio Focus (ArkTS)](audio-session-management.md)
  - [Using AudioSession to Manage Audio Focus (C/C++)](using-ohaudio-for-session.md)
- Audio Playback<!--audio-playback-->
  - [Audio Playback Overview](audio-playback-overview.md)
  - [Using AudioRenderer for Audio Playback](using-audiorenderer-for-playback.md)
  <!--Del-->
  - [Using TonePlayer for Audio Playback (for System Applications Only)](using-toneplayer-for-playback-sys.md)
  <!--DelEnd-->
  - [Using OHAudio for Audio Playback (C/C++)](using-ohaudio-for-playback.md)
  - [Low-Latency Audio Playback (C/C++)](audio-fast-playback.md)
  - [Low-Power Audio Playback](power-saving-for-playback.md)
  - [Using AudioHaptic for Audio-Haptic Playback](using-audiohaptic-for-playback.md)
  - [Volume Management](volume-management.md)
  - [Enhancing Audio Performance Experience](audio-performance.md)
  - [Audio Latency Management](audio-latency.md)
  - [Audio Workgroup Management](audio-workgroup.md)
  - [Spatial Audio Capability Query and Status Subscription](public-audio-spatialization-management.md)
  <!--Del-->
  - [Spatial Audio Management (for System Applications Only)](audio-spatialization-management-sys.md)
  <!--DelEnd-->
  - [Audio Playback Stream Management](audio-playback-stream-management.md)
  <!--Del-->
  - [Distributed Audio Playback (for System Applications Only)](distributed-audio-playback-sys.md)
  <!--DelEnd-->
- Audio Recording<!--audio-recording-->
  - [Audio Recording Overview](audio-recording-overview.md)
  - [Using AudioCapturer for Audio Recording](using-audiocapturer-for-recording.md)
  - [Using OHAudio for Audio Recording (C/C++)](using-ohaudio-for-recording.md)
  - [Low-latency Audio Recording (C/C++)](audio-fast-recording.md)
  - [Microphone Management](mic-management.md)
  - [Audio Recording Stream Management](audio-recording-stream-management.md)
  - [Shared Audio Input](audio-recording-concurrency.md)
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
- OpenSL ES Development (Not Recommended)<!--not-recommended-->
  - [Switching from OpenSL ES to OHAudio (C/C++)](replace-opensles-by-ohaudio.md)
  - [Using OpenSL ES for Audio Playback (C/C++)](using-opensl-es-for-playback.md)
  - [Using OpenSL ES for Audio Recording (C/C++)](using-opensl-es-for-recording.md)
