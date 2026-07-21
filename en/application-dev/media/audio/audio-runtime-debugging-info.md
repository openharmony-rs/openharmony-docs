# Using Audio Snapshots for Troubleshooting

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:18:50.438Z pushedAt=2026-07-14T13:08:29.562Z -->

Starting from API version 26.0.0, the system provides audio snapshot (Audio Debugging Info) capability, which allows apps to obtain the runtime status of the audio subsystem in the current process. Audio Debugging Info captures a point-in-time snapshot of the audio subsystem, including key information such as audio stream parameters, routing status, volume information, audio focus state, and error records. It helps you inspect the internal state of the audio subsystem without affecting app behavior. You can use the captured snapshot to obtain diagnostic information for troubleshooting issues related to audio rendering, audio capture, audio loopback, and audio sessions, such as silent playback, abnormal volume levels, and audio focus loss.

> **NOTE**
>
> - The content and format of audio snapshots may be refined in future releases based on developer feedback and usage. As a result, they are subject to change across releases. Audio snapshots are intended for manual debugging only. Do not rely on their content or format when implementing application logic.
> - Audio snapshot provides both C/C++ APIs and ArkTS APIs. Choose the appropriate API based on your development language.

**Audio Debugging Info Usage Scenarios**

| Module | API Type | Description | Typical Usage Scenario |
| :--- | :--- | :--- | :--- |
| App snapshot | C/C++, ArkTS | Contains snapshot information of all renderer, capturer, loopback, and session instances in the current app process (excluding AudioSuite snapshots). | Overall troubleshooting and system-level issue analysis |
| Audio renderer snapshot | C/C++, ArkTS | Records playback stream parameters, path information, volume, focus state, error records, and more. | Silent playback, abnormal volume, and audio focus conflicts |
| Audio capturer snapshot | C/C++, ArkTS | Records audio capture stream parameters, path information, capture timestamps, overflow count, error records, and more. | No capture data, capture stutter, and buffer overflow |
| Audio loopback snapshot | ArkTS | Records loopback status, device information, audio effect parameters, upstream and downstream stream status, and more. | No loopback audio, excessive loopback latency, and audio effect issues |
| Audio session snapshot | C/C++, ArkTS | Records session status, concurrency policy, scenario type, associated stream information, and more. | Session activation failures and concurrency policy issues |
| AudioSuite snapshot | C/C++ | Records engine status, pipeline running status, node connection relationships, audio effect parameters, and more. | No AudioSuite output, audio effects not taking effect, and pipeline connection issues |

## Preparations

The following examples are code snippets. For the complete sample code, see [AudioSnapshot](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioSnapshot).

### Modules to Import

**C/C++ Development:**

To obtain audio snapshots using C/C++ APIs, you need to include the corresponding header files and link the dynamic library in the CMake script.

**Linking the Dynamic Library in CMake:**

``` cmake
target_link_libraries(sample PUBLIC libohaudio.so)
```

**Including Header Files:**

<!-- @[header_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSnapshot/entry/src/main/cpp/audio.cpp) -->

``` C++
#include <ohaudio/native_audio_debugging_manager.h>
#include <fcntl.h>
#include <unistd.h>
// File permission constant.
constexpr mode_t FILE_PERMISSION = S_IRUSR | S_IWUSR | S_IRGRP | S_IROTH; // 0644
```

**ArkTS Development:**

When using ArkTS APIs to obtain audio snapshots, you need to import the audio module.

<!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSnapshot/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';
import { fileIo as fileio } from '@kit.CoreFileKit';
```

### Obtaining the Audio Debugging Manager

Before using the debugging APIs, obtain an audio debugging manager instance first. This instance is a singleton and can be reused.

For API details, see [getDebuggingManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioManager.md#getdebuggingmanager).

**C/C++ API:**

<!-- @[get_debug_manager_c](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSnapshot/entry/src/main/cpp/audio.cpp) -->

``` C++
// Obtain the audio debugging manager.
OH_AudioDebuggingManager *debugManager = nullptr;
OH_AudioCommon_Result result = OH_AudioManager_GetAudioDebuggingManager(&debugManager);
if (result != AUDIOCOMMON_RESULT_SUCCESS || debugManager == nullptr) {
    // Failed to obtain the audio debugging manager. Handle the error.
    return;
}
```

**ArkTS API:**

<!-- @[get_debug_manager_ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSnapshot/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// Obtain the audio debugging manager.
const audioManager = audio.getAudioManager();
const debugManager: audio.AudioDebuggingManager = audioManager.getDebuggingManager();
```

## App Snapshot

The app snapshot contains all information about renderer, capturer, loopback, and session snapshots within the current app process. It is a summary of snapshots from different scenarios. The app snapshot does not include AudioSuite snapshots. It is suitable for scenarios where you need to obtain the overall audio running status at once.

The following table lists the information in app snapshots.

| Category | Field | Description |
| :--- | :--- | :--- |
| Renderer snapshot list | renderers | All audio renderer snapshot information in the current app process. For details, see [Audio Renderer Snapshot](#audio-renderer-snapshot). |
| Capturer snapshot list | capturers | All audio capturer snapshot information in the current app process. For details, see [Audio Capturer Snapshot](#audio-capturer-snapshot). |
| Loopback snapshot list | loopbacks | All audio loopback snapshot information in the current app process. For details, see [Audio Loopback Snapshot](#audio-loopback-snapshot). |
| Session snapshot list | sessions | All audio session snapshot information in the current app process. For details, see [Audio Session Snapshot](#audio-session-snapshot). |

> **NOTE**
>
> For detailed field information of each snapshot, see the output examples in the corresponding sections below.

For API details, see [printAppInfo](../../reference/apis-audio-kit/arkts-apis-audio-AudioDebuggingManager.md#printappinfo).

**C/C++ API:**

<!-- @[print_app_snapshot_c](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSnapshot/entry/src/main/cpp/audio.cpp) -->

``` C++
// Print the app snapshot to a file.
int32_t fd = open("/data/storage/el2/base/cache/audio_snapshot.txt", O_WRONLY | O_CREAT | O_TRUNC, FILE_PERMISSION);
if (fd >= 0) {
    OH_AudioDebuggingManager_PrintAppInfo(debugManager, fd);
    close(fd);
}

// You can also output the snapshot information to the hilog log (when fd < 0).
OH_AudioDebuggingManager_PrintAppInfo(debugManager, -1);
```

**ArkTS API:**

<!-- @[print_app_snapshot_ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSnapshot/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// Print the app snapshot to a file.
const path = this.context.filesDir + '/audio_snapshot.txt';
const file = fileio.openSync(path, 0o102 | 0o200, 0o644); // O_WRONLY | O_CREAT
debugManager.printAppInfo(file.fd);
fileio.closeSync(file);

// You can also output the snapshot information to the hilog log (when fd < 0).
debugManager.printAppInfo(-1);
```

**Example:**

```text
audioApp {
  renderers: [                          // List of renderer snapshot information.
    { ... },                            // Renderer snapshot information. For details, see "Audio Renderer Snapshot".
    { ... }
  ],
  capturers: [                          // List of capturer snapshot information.
    { ... },                            // Capturer snapshot information. For details, see "Audio Capturer Snapshot".
    { ... }
  ],
  loopbacks: [                          // List of loopback snapshot information.
    { ... }                             // Loopback snapshot information. For details, see "Audio Loopback Snapshot".
  ],
  sessions: [                           // List of session snapshot information.
    { ... }                             // Session snapshot information. For details, see "Audio Session Snapshot".
  ]
}
```

## Audio Renderer Snapshot

The audio renderer snapshot records playback stream parameters, path information, volume, device information, focus state, error records, and more. It is suitable for troubleshooting issues such as no sound during playback, abnormal volume, and focus preemption.

The following table lists the information in audio renderer snapshots.

| Category | Field | Description |
| :--- | :--- | :--- |
| Stream information | streamId, samplingRate, channels, format, encoding, streamUsage, rendererFlags | Basic audio stream parameters. |
| Path information | pipeId, pipeRole, pipeName, routeFlag, adapterName, pipeFormat, pipeRate, etc. | Underlying audio path status. |
| Device information | mainDeviceType | Current output device type. |
| Volume information | volumeType, streamVolume, systemVolume, volume | Volume information at each level. |
| Audio effect information | speed, pitch, effectMode | Audio effect parameters. |
| Focus information | focusState, focusHistory | Current focus state and focus change history. |
| Error codes | errorInfos | Error code records. The system retains up to 10 of the most recent error code entries. |

> **NOTE**
>
> See the output example below for detailed field information.

For API details, see [printRendererInfo](../../reference/apis-audio-kit/arkts-apis-audio-AudioDebuggingManager.md#printrendererinfo).

**C/C++ API:**

<!-- @[print_renderer_snapshot_c](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSnapshot/entry/src/main/cpp/audio.cpp) -->

``` C++
// Print the snapshot of the specified renderer instance.
int32_t fd = open("/data/storage/el2/base/cache/renderer_snapshot.txt",
    O_WRONLY | O_CREAT | O_TRUNC, FILE_PERMISSION);
if (fd >= 0) {
    OH_AudioDebuggingManager_PrintRendererInfo(debugManager, renderer, fd);
    close(fd);
}
```

**ArkTS API:**

<!-- @[print_renderer_snapshot_ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSnapshot/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// Print the snapshot of the specified renderer instance.
const path = this.context.filesDir + '/renderer_snapshot.txt';
const file = fileio.openSync(path, 0o102 | 0o200, 0o644);
debugManager.printRendererInfo(renderer, file.fd);
fileio.closeSync(file);
```

**Example:**

```text
audioRenderer {
  streamInfo: {                         // Stream information.
    streamId: 100001,                   // Stream ID.
    samplingRate: 48000,               // Sampling rate.
    channels: 2,                        // Number of channels.
    format: SAMPLE_S16LE,              // Sample format.
    encoding: ENCODING_PCM,            // Encoding format.
    streamUsage: STREAM_USAGE_MUSIC,   // Playback stream usage.
    rendererFlags: AUDIO_FLAG_NORMAL   // Playback stream flag.
  },
  pipeInfo: {                           // Pipeline  information.
    pipeId: 5,                          // Pipeline ID.
    pipeRole: PIPE_ROLE_OUTPUT,        // Pipeline role.
    pipeName: primary,                  // Pipeline name.
    routeFlag: OUTPUT_FLAG_NORMAL,     // Route flag.
    adapterName: primary,              // Adapter name.
    pipeFormat: S16LE,                 // Pipeline format.
    pipeRate: 48000,                   // Pipeline sample rate.
    pipeChannels: 2,                   // Pipeline channel count.
    pipeChannelLayout: CH_LAYOUT_STEREO, // Pipeline channel layout.
    pipeDeviceType: DEVICE_TYPE_SPEAKER // Pipeline device type.
  },
  deviceInfo: {                         // Device information.
    mainDeviceType: DEVICE_TYPE_SPEAKER // Main device type.
  },
  volumeInfo: {                         // Volume information.
    volumeType: MEDIA_STREAM,          // Volume type.
    streamVolume: 1.000000,            // Stream volume.
    systemVolume: 1.000000,            // System volume.
    volume: 1.000000                   // Actual volume.
  },
  effectInfo: {                         // Effect information.
    speed: 1.000000,                    // Speed.
    pitch: 1.000000,                    // Pitch.
    effectMode: EFFECT_DEFAULT          // Sound effect mode.
  },
  focusInfo: {                          // Focus information.
    focusState: ACTIVE,                // Current focus state.
    focusHistory: [                    // Historical focus behaviors.
      { streamId: 100001, pid: xx, uid: xx, streamType: STREAM_MUSIC,
        sourceType: SOURCE_TYPE_INVALID, hintType: INTERRUPT_HINT_NONE,
        timestamp: xx },
    ]
  },
  errorInfos: []                        // List of error code information.
}
```

## Audio Capturer Snapshot

The audio capturer snapshot records audio capture stream parameters, path information, capture timestamps, device information, overflow count, error records, and more. It is suitable for troubleshooting issues such as no capture data or capture stuttering.

The following table lists the information in audio capturer snapshots.

| Category | Field | Description |
| :--- | :--- | :--- |
| Stream information | streamId, samplingRate, channels, format, encoding, sourceType, capturerFlag | Basic audio stream parameters. |
| Capture information | timestamp, bufferSize, overflowCount, muteWhenInterrupted, inputDeviceType | Capture running status. |
| Path information | pipeRole, samplingRate, channels, format, encoding, channelLayout | Underlying path status. |
| Focus information | focusState, focusHistory | Current focus state and focus change history. |
| Error codes | errorInfos | Error code records. The system retains up to 10 latest error code entries. |

> **NOTE**
>
> For detailed field information, see the output example below.

For API reference, see [printCapturerInfo](../../reference/apis-audio-kit/arkts-apis-audio-AudioDebuggingManager.md#printcapturerinfo).

**C/C++ API:**

<!-- @[print_capturer_snapshot_c](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSnapshot/entry/src/main/cpp/audio.cpp) -->

``` C++
// Print the snapshot of the specified capturer instance.
int32_t fd = open("/data/storage/el2/base/cache/capturer_snapshot.txt",
    O_WRONLY | O_CREAT | O_TRUNC, FILE_PERMISSION);
if (fd >= 0) {
    OH_AudioDebuggingManager_PrintCapturerInfo(debugManager, capturer, fd);
    close(fd);
}
```

**ArkTS API:**

<!-- @[print_capturer_snapshot_ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSnapshot/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// Print the snapshot of the specified capturer instance.
const path = this.context.filesDir + '/capturer_snapshot.txt';
const file = fileio.openSync(path, 0o102 | 0o200, 0o644);
debugManager.printCapturerInfo(capturer, file.fd);
fileio.closeSync(file);
```

**Example:**

```text
audioCapturer {
  streamInfo: {                         // Stream information.
    streamId: 100002,                   // Stream ID.
    samplingRate: 16000,               // Sampling rate.
    channels: 1,                        // Number of channels.
    format: SAMPLE_S16LE,              // Sample format.
    encoding: ENCODING_PCM,            // Encoding format.
    channelLayout: CH_LAYOUT_MONO,     // Channel layout.
    sourceType: SOURCE_TYPE_MIC,       // Capture stream type.
    capturerFlag: AUDIO_FLAG_NORMAL    // Capturer flag.
  },
  captureInfo: {                        // Capture information.
    timestamp(frame: xx, sec: xx, nsec: xx), // Timestamp.
    bufferSize: 6400,                  // Buffer size.
    overflowCount: 0,                  // Overflow count.
    muteWhenInterrupted: false,        // Mute state when interrupted by focus.
    inputDeviceType: 15                // Input device type.
  },
  pipeInfo: {                           // Pipeline information.
    pipeRole: PIPE_ROLE_INPUT,         // Pipeline role.
    samplingRate: 16000,               // Pipeline sampling rate.
    channels: 1,                        // Number of pipeline channels.
    format: SAMPLE_S16LE,              // Channel format.
    encoding: ENCODING_PCM,            // Channel encoding.
    channelLayout: CH_LAYOUT_MONO      // Channel layout.
  },
  focusInfo: {                          // Focus information.
    focusState: ACTIVE,                // Current focus state.
    focusHistory: []                   // Historical focus behaviors.
  },
  errorInfos: []                        // List of error code information.
}
```

## Audio Loopback Snapshot

The audio loopback snapshot records the working mode, current state, active devices, audio effect parameters (reverb/equalizer presets, volume), and uplink/downlink stream status of the loopback, helping troubleshoot issues such as no sound during loopback, high loopback latency, and abnormal audio effects.

The following table lists the information in audio loopback snapshots.

| Category | Fields | Description |
| :--- | :--- | :--- |
| App info | appUid, appName | Information about the app to which the loopback belongs. |
| State info | mode, currentState | Working mode and current state of the loopback. |
| Device info | activeOutputDevice, activeInputDevice | Currently active output and input devices. |
| Audio effect info | reverbPreset, equalizerPreset, volume | Reverb preset, equalizer preset, and volume. |
| Stream state info | uplinkStreamState, downlinkStreamState | Status of the uplink capture stream and downlink playback stream. |

> **NOTE**
>
> For detailed field information, see the output example below.
> Before calling this method, you need to create an AudioLoopback instance. For details about how to create and use loopback, see [Low-Latency Audio Monitoring](audio-ear-monitor-loopback.md). When the loopback is in the available state (`AVAILABLE_IDLE` or `AVAILABLE_RUNNING`), the complete snapshot information can be queried.

For API details, refer to [printLoopbackInfo](../../reference/apis-audio-kit/arkts-apis-audio-AudioDebuggingManager.md#printloopbackinfo).

**ArkTS API:**

<!-- @[print_loopback_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioLoopbackDebugInfo.ets) -->

``` TypeScript
// audioLoopback is the created AudioLoopback instance.
// Obtain the debugging manager.
let debugManager = audio.getAudioManager().getDebuggingManager();

// Output to hilog logs.
debugManager.printLoopbackInfo(audioLoopback, -1);

// Output to a file.
let filePath = getContext().filesDir + '/audio_loopback_debug.txt';
let file = fs.openSync(filePath, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
debugManager.printLoopbackInfo(audioLoopback, file.fd);
fs.closeSync(file);
```

**Output example:**

```text
audioLoopback {
  appInfo: {                            // App information.
    appUid: 10001,                      // App UID.
    appName: com.example.karaoke        // App name.
  },
  statusInfo: {                         // Status information.
    mode: LOOPBACK_HARDWARE,           // Loopback mode.
    currentState: LOOPBACK_STATE_RUNNING // Current state.
  },
  deviceInfo: {                         // Device information.
    activeOutputDevice: DEVICE_TYPE_WIRED_HEADPHONES, // Active output device.
    activeInputDevice: DEVICE_TYPE_WIRED_HEADPHONES   // Active input device.
  },
  effectInfo: {                         // Audio effect information.
    reverbPreset: REVERB_PRESET_THEATER, // Reverb preset.
    equalizerPreset: EQUALIZER_PRESET_FULL, // Equalizer preset.
    volume: 50                          // Volume.
  },
  streamInfo: {                         // Stream status information.
    uplinkStreamState: CAPTURER_RUNNING,   // Uplink stream status.
    downlinkStreamState: RENDERER_RUNNING  // Downlink stream status.
  }
}
```

## Audio Session Snapshot

The audio session snapshot records the session state, concurrency policy, scenario type, device information, associated stream information, and more. It is suitable for troubleshooting issues such as session activation exceptions and concurrency policy failures.

The following table lists the information in audio session snapshots.

| Category | Field | Description |
| :--- | :--- | :--- |
| Policy information | concurrencyMode | Session concurrency policy. |
| Scenario information | audioSessionScene, defaultDeviceType | Session scenario and default device. |
| State information | state, fakeFocusState | Session state. |
| Process information | pid, uid | Process information associated with the audio session. |
| Associated stream information | streamInfos (streamId, focusState, streamType) | List of audio streams associated with the session. |

> **NOTE**
>
> For detailed field information, see the output example below.
> Before calling this method, you need to create and activate an audio session. For details about how to create and use an audio session, see [Using OHAudio for Audio Session (C/C++)](using-ohaudio-for-session.md) or [Using AudioSession to Manage Audio Focus (ArkTS)](audio-session-management.md).

For API details, see [printSessionInfo](../../reference/apis-audio-kit/arkts-apis-audio-AudioDebuggingManager.md#printsessioninfo).

**C/C++ APIs:**

<!-- @[print_session_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleC/entry/src/main/cpp/audiosession.cpp) -->

``` C++
#include "ohaudio/native_audio_debugging_manager.h"
// ...
OH_AudioSessionManager *audioSessionManager;
// ...
    // Create the audio session manager.
    OH_AudioManager_GetAudioSessionManager(&audioSessionManager);
    // Set the audio concurrency mode.
    OH_AudioSession_Strategy strategy = {CONCURRENCY_MIX_WITH_OTHERS};
    // Activate the audio session.
    OH_AudioSessionManager_ActivateAudioSession(audioSessionManager, &strategy);
    
    // Create the audio debugging manager.
    OH_AudioDebuggingManager *audioDebuggingManager;
    OH_AudioManager_GetAudioDebuggingManager(&audioDebuggingManager);
    
    // Output to the hilog log.
    OH_AudioDebuggingManager_PrintSessionInfo(audioDebuggingManager, audioSessionManager, -1);
    
    // fd: file descriptor. Obtain it based on the actual situation.
    // Output to a file.
    OH_AudioDebuggingManager_PrintSessionInfo(audioDebuggingManager, audioSessionManager, fd);
}
```

**ArkTS API:**

<!-- @[print_session_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSessionSampleJS/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
// ...
import { fileIo as fs } from '@kit.CoreFileKit';
// ...
  // Set the audio concurrency mode.
  let strategy: audio.AudioSessionStrategy = {
    concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
  };
  // Activate the audio session.
  await audioSessionManager.activateAudioSession(strategy);

  // Create an audio debugging manager.
  let audioDebuggingManager: audio.AudioDebuggingManager = audioManager.getDebuggingManager();

  // Output to the hilog log.
  audioDebuggingManager.printSessionInfo(audioSessionManager, -1);

  // Obtain the fd based on the actual situation during use.
  let filePath = context.filesDir + '/audio_session_info.txt';
  let fd = fs.openSync(filePath, fs.OpenMode.CREATE | fs.OpenMode.WRITE_ONLY | fs.OpenMode.TRUNC).fd;
  // Output to a file.
  audioDebuggingManager.printSessionInfo(audioSessionManager, fd);
  fs.closeSync(fd);
```

**Example:**

```text
audioSession {
  strategy: DEFAULT,                    // Session strategy.
  audioSessionScene: MEDIA,            // Session scenario.
  defaultDeviceType: DEVICE_TYPE_SPEAKER, // Default device type.
  state: SESSION_ACTIVE,               // Session state.
  fakeFocusState: ACTIVE,              // Fake focus state.
  pid: xx,                              // Process ID.
  uid: xx,                              // User ID.
  streams: [                            // List of associated streams.
    {
      streamId: 100001,                 // Stream ID.
      streamType: STREAM_MUSIC         // Stream type.
    },
  ]
}
```

## AudioSuite Snapshot

An AudioSuite Snapshot provides the runtime status of the AudioSuite engine, pipelines, and nodes, helping you troubleshoot issues in the AudioSuite processing pipeline. For an introduction to the basic AudioSuite concepts, such as engines, pipelines, and nodes, see [Audio Creation Overview (C/C++)](audio-suite.md).

The following table lists the information in AudioSuite snapshots.

| Category | Field | Description |
| :--- | :--- | :--- |
| Engine information | engineState, pipelineCount | Engine running state and pipeline count. |
| Pipeline information | pipelineId, pipelineState, nodeCount | Pipeline ID, running state, and node count. |
| Node information | nodeId, nodeType, connectState, format | Node ID, type, connection state, and audio format. |
| Effect information | effectType, effectParams | Effect type and parameters used by the node. |

> **NOTE**
>
> For detailed field information, see the output example below.

For API reference, see [OH_AudioSuite_PrintInfo](../../reference/apis-audio-kit/capi-native-audio-suite-engine-h.md#oh_audiosuite_printinfo).

<!-- @[audioSuite_PrintInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSuiteSample/entry/src/main/cpp/print_info_to_file.cpp) -->

``` C++
// engine is the created OH_AudioSuiteEngine instance. Ensure that the engine parameter is valid; otherwise, the output is empty.
// When pipeline is nullptr, all pipelines are output. When a specific pipeline instance is passed in, only that pipeline is output.
OH_AudioSuiteEngine *engine = audioSuiteEngine;
if (!engine) {
    OH_AudioSuiteEngine_Create(&g_printInfoEngine);
    engine = g_printInfoEngine;
}
// Print the AudioSuite snapshot to a file.
const char *filePath =
    "/storage/Users/currentUser/Download/com.example.audiosuitesample/printfile/audio_snapshot.txt";
int fd = open(filePath, O_WRONLY | O_CREAT | O_APPEND, FILE_PERMISSION);
if (fd < 0) {
    // Failed to open the file. Fall back to log output.
    // fd < 0 indicates output to the log.
    OH_AudioSuite_PrintInfo(engine, nullptr, -1);
    napi_get_boolean(env, true, &result);
    return result;
}
// Output all pipeline information to the file.
// nullptr indicates output of all pipelines under the engine, and fd is the file descriptor.
OH_AudioSuite_Result ret = OH_AudioSuite_PrintInfo(engine, nullptr, fd);
close(fd);
```

**Output example:**

```text
========================================
Audio Suite Engine Debug Info
Timestamp: xxxx-xx-xx xx:xx:xx.xxx      // Timestamp.
========================================

Total Pipelines: 1                       // Total number of pipelines.

Pipeline [ID: 1]                         // Unique identifier of the pipeline.
  Work Mode: EDIT_MODE                  // Work mode: Manual (offline editing) or Real-time (real-time rendering).
  State: RUNNING                         // Current state: Stopped or Running.
  Nodes: 3                               // Number of nodes.
  Connections: 2                         // Number of connections.

  Node [ID: 103, Type: NODE_TYPE_EQUALIZER] // Unique identifier and type of the node.
    Volume: 1                            // Volume.
    Bypass: false                        // Bypass.
    Gains: band0:1, band1:1, ...        // Gain parameters.

  Node [ID: 102, Type: NODE_TYPE_OUTPUT]    // Unique identifier and type of the node.
    Format: sampleRate=24000, channels=2, format=PCM24 // Audio format.
    Volume: 1                            // Volume.

  Node [ID: 101, Type: NODE_TYPE_INPUT]     // Unique identifier and type of the node.
    Format: sampleRate=44100, channels=2, format=FLOAT32 // Audio format.
    Volume: 1                            // Volume.
    Finished: true                       // Whether finished.

  Connections:                           // Forward connections: upstream node -> downstream node.
    103 -> 102
    101 -> 103

  Reverse Connections:                   // Reverse connections: downstream node <- upstream node.
    102 -> 103
    103 -> 101

========================================
```

## Notes

- When calling a print API, if `fd` is less than 0 or not writable, the snapshot information will be output to the running log (hilog) and can be viewed using the log tool.

- It is recommended that you obtain snapshot information when an audio exception occurs (such as no sound, abnormal volume, or focus loss) for fault locating.

- Each print API is a synchronous call. It is recommended that you avoid calling them in audio data callbacks to prevent affecting audio processing performance.

- The snapshot file is saved in the app sandbox directory and can be exported to the local device for viewing using the hdc tool:

  ``` bash
  hdc file recv /data/app/el2/100/base/<bundleName>/haps/entry/cache/audio_snapshot.txt ./
  ```

- The complete snapshot information can be queried only when audio loopback is in an available state (`AVAILABLE_IDLE` or `AVAILABLE_RUNNING`).

- Before calling the session snapshot API, an audio session must be created and activated; otherwise, complete snapshot information cannot be obtained.

- When the `pipeline` parameter is NULL, information about all pipelines under the engine is output.

- The specific parameters for node attribute configuration vary by node type. For details, see the description of each node in [OHAudioSuite](../../reference/apis-audio-kit/capi-ohaudiosuite.md).