# 处理音频时间戳(C/C++)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

在音视频播放场景中，开发者需要获取音频的播放时延和精确的播放位置信息，用于实现音画同步、进度条显示对齐等功能。时间戳是标记某一帧音频数据对应时间点的信息，通过时间戳可以精确知道当前音频播放到什么位置，从而与视频画面进行同步。

音频数据经回调接口写入后，需经过软件处理、缓冲队列和硬件传输等环节才能从设备出声，因此存在时间差。这意味着应用写入数据的位置始终领先于用户实际听到的播放位置。如果仅根据已写入的数据量来推算播放进度，会导致进度条超前于实际播放；如果仅根据写入时间来对齐音画，会导致视频画面与实际听到的声音不同步。因此，需要通过专门的接口获取真实的播放时延和播放位置信息。

## 接口说明

OHAudio提供以下接口用于获取音频时延和时间戳信息：

| 接口 | 起始版本 | 说明 |
| --- | --- | --- |
| [OH_AudioRenderer_GetLatency](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getlatency) | API版本23 | 获取从写入音频数据到实际出声的整体时延（单位：毫秒）。 |
| [OH_AudioRenderer_GetAudioTimestampInfo](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo) | API版本15 | 获取某一帧的播放位置（framePosition）和对应的时间戳（timestampNs）。支持倍速播放场景。 |
| [OH_AudioRenderer_GetTimestamp](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_gettimestamp) | API版本10 | 获取输出音频流时间戳和位置信息。不支持倍速播放场景，API版本15及以上推荐使用OH_AudioRenderer_GetAudioTimestampInfo替代。 |

## 开发步骤

详细的API说明请参考[OHAudio](../../reference/apis-audio-kit/capi-ohaudio.md)。

关于创建播放器、配置音频流参数、设置回调函数等基础开发步骤，请参考[推荐使用OHAudio开发音频播放功能(C/C++)](using-ohaudio-for-playback.md)。以下各步骤示例为片段代码，可通过示例代码右下方链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AudioMusicPlayer)。

### 在CMake脚本中链接动态库

``` cmake
target_link_libraries(sample PUBLIC libohaudio.so)
```

### 添加头文件

开发者通过引入<[native_audiostreambuilder.h](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md)>和<[native_audiorenderer.h](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md)>头文件，使用音频播放相关API。示例中使用hilog输出日志，还需引入<[hilog/log.h](../../reference/apis-performance-analysis-kit/capi-hilog.md)>头文件。

``` C++
#include <ohaudio/native_audiorenderer.h>
#include <ohaudio/native_audiostreambuilder.h>
#include <hilog/log.h>
```

### 获取播放时延

开发者通过调用[OH_AudioRenderer_GetLatency](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getlatency)接口（从API版本23开始支持），获取当前音频路由的估算时延（单位：毫秒），即从写入音频数据到实际出声的整体耗时，包括软件处理时延和硬件传输时延。该时延不包含播放过程中的实时缓存数据量，因此仅在播放开始前获取一次即可，播放过程中如需获取实时播放位置，请使用[OH_AudioRenderer_GetAudioTimestampInfo](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo)。

若目标设备的API版本低于23，不支持该接口，可跳过初始时延获取，仅使用[OH_AudioRenderer_GetAudioTimestampInfo](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo)或[OH_AudioRenderer_GetTimestamp](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_gettimestamp)自行推算。

该接口通过[OH_AudioStream_LatencyType](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencytype)（从API版本23开始支持）指定要获取的时延类型：

| 时延类型 | 说明 |
| --- | --- |
| AUDIOSTREAM_LATENCY_TYPE_ALL | 获取包含软件与硬件在内的整体音频处理时延。 |
| AUDIOSTREAM_LATENCY_TYPE_SOFTWARE | 获取软件部分的时延，包括软件侧音效处理。 |
| AUDIOSTREAM_LATENCY_TYPE_HARDWARE | 获取硬件部分的时延，包括硬件抽象层（HAL）、驱动与硬件侧音效处理。 |

> **注意：**
>
> - 该接口应在创建播放器（OH_AudioStreamBuilder_GenerateRenderer）之后、启动播放器（OH_AudioRenderer_Start）之前调用，通常创建播放器后只需调用一次。
> - 由于时延未计入实时缓冲区，频繁调用可能因路由切换而阻塞该接口。
> - 无线连接的音频设备（如蓝牙耳机），实际时延并不稳定，与估计值存在误差，结果仅供参考。
> - 当音频数据输出到硬件后，建议使用[OH_AudioRenderer_GetAudioTimestampInfo](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo)进行音视频同步。

以下示例中，`audioRenderer`由`OH_AudioStreamBuilder_GenerateRenderer()`创建，`audioLatencyMs`为播放器类中保存的时延值（单位：毫秒），示例省略了播放器的创建与配置步骤，详见[推荐使用OHAudio开发音频播放功能(C/C++)](using-ohaudio-for-playback.md)。

在创建播放器后、启动播放器前，调用该接口获取时延信息，用于后续的播放进度校准等操作：

<!-- @[GetLatency](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AudioMusicPlayer/entry/src/main/cpp/player/oh_audio_playing.cpp) -->

``` C++
int32_t latencyMs = 0;
auto latencyRet = OH_AudioRenderer_GetLatency(audioRenderer, AUDIOSTREAM_LATENCY_TYPE_ALL, &latencyMs);
if (latencyRet == AUDIOSTREAM_SUCCESS) {
    // 创建播放器后，启动播放器前，根据获取的时延信息，进行音乐播放器播放进度校准等操作。
    audioLatencyMs = latencyMs;
    OH_LOG_INFO(LOG_APP, "Audio latency after create: %{public}d ms", latencyMs);
} else {
    OH_LOG_ERROR(LOG_APP, "Get audio latency after create failed, ret: %{public}d", latencyRet);
}
```

### 处理音频时间戳

开发者通过调用[OH_AudioRenderer_GetAudioTimestampInfo](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo)接口（从API版本15开始支持），获取输出音频流当前的实际播放位置和对应的系统时间戳。接口返回两个值：

- **framePosition**：截至timestampNs时刻，已提交到硬件的音频帧位置（单位：采样数samples）。结合采样率可换算为已播放的媒体时间：`已播放时间（ms）= framePosition × 1000 / 采样率`。
- **timestampNs**：播放到framePosition位置时对应的系统单调时钟时间（单位：ns）。经过计算后，可用于与视频时间戳进行对齐比较。

该接口支持倍速播放场景，例如当播放速度设置为2倍时，framePosition的增长速度也为正常的2倍。返回信息可用于以下场景：

- **音画同步**：先通过framePosition换算出已播放的音频帧时间，再与待显示视频帧的PTS比较，判断音频领先还是落后于视频，据此决定丢帧、等待或加速。timestampNs可用于校准系统时钟与播放位置的对应关系，提升同步精度。
- **播放进度显示**：framePosition换算出的已播放时间反映已提交到硬件的播放位置，是音画同步的基准点，与用户实际听到的位置之间仍可能有硬件侧缓冲差异。对进度精度要求不高的场景，也可以不调用该接口，直接以已写入帧对应的媒体文件时间作为进度。但低功耗播放模式下系统缓存较大，写入位置与实际播放位置差距明显，必须使用该接口获取真实播放位置才能保证进度准确，详见[低功耗音频播放](power-saving-for-playback.md)。

音画同步的核心是比较音频与视频的PTS，使画面和声音同步呈现。计算步骤如下：

1. 缓冲时延（μs）= (已写入采样数 - framePosition) ÷ 采样率 × 1000000
   - 已写入采样数通过[OH_AudioRenderer_GetFramesWritten](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getframeswritten)获取（采样数 = 帧数 × 声道数），采样率为创建播放器时配置的采样率。注意：调用OH_AudioRenderer_Flush()后GetFramesWritten不清零而framePosition会重置，需重新建立基准，本公式仅适用于未Flush的连续播放场景。
2. 时间戳偏移（μs）= (当前系统时间 - timestampNs) ÷ 1000
   - 当前系统时间使用与timestampNs相同的系统单调时钟获取（如clock_gettime(CLOCK_MONOTONIC, &ts)，换算为ns）。
3. 当前音频播放时间 = 最近写入缓冲区的音频帧PTS - 缓冲时延 + 时间戳偏移
   - 音频帧PTS由解码器提供，标记该帧在媒体文件中的呈现时间。此处的"缓冲时延"指缓冲区中尚未播放的时长，与OH_AudioRenderer_GetLatency返回的整体时延是不同概念。PTS若由解码器以ms给出，需先统一换算为μs。
4. 视频等待时间 = 视频帧PTS - 当前音频播放时间（正值等待，负值丢帧）
   - 视频帧PTS由视频解码器提供，标记该帧应该被送显的时间。

> **注意：**
>
> - 该接口应在启动播放器（OH_AudioRenderer_Start）之后调用。
> - 刚开始播放前几帧时，播放通路尚未稳定，可能无法获取到有效数据，建议在播放稳定后再调用（如连续两次调用framePosition差值符合采样率推算且不再跳变，视为稳定）。
> - 当设备切换或暂停恢复时，由于播放通路本身需要一段时间恢复，调用该接口获取的播放位置和时间戳会短暂地保持在切换或暂停前的状态。
> - 当音频流路由变化时（例如设备变化或输出类型变化），播放位置可能会被重置，但时间戳仍会持续增长。建议在实际播放位置和时间戳的变化趋于稳定后，再使用该接口获取的值。
> - 两次调用间隔建议不小于200ms，推荐频率为每秒一次。在能保证音画同步效果的情况下，不需要频繁查询，避免出现功耗问题。

以下示例中，`audioRenderer`为OH_AudioRenderer实例，`audioLatencyMs`为播放器类中保存的时延值，示例省略了播放器的创建与配置步骤，详见[推荐使用OHAudio开发音频播放功能(C/C++)](using-ohaudio-for-playback.md)。

在启动播放器后，每隔一段时间周期性调用该接口，根据framePosition和timestampNs信息进行音乐播放器播放进度校准等操作：

<!-- @[GetAudioTimestampInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AudioMusicPlayer/entry/src/main/cpp/player/oh_audio_playing.cpp) -->

``` C++
int64_t framePosition = 0;
int64_t timestampNs = 0;
auto tsRet = OH_AudioRenderer_GetAudioTimestampInfo(audioRenderer, &framePosition, &timestampNs);
if (tsRet == AUDIOSTREAM_SUCCESS) {
    // 启动播放器后，根据framePosition、timestampNs信息，可以进行音乐播放器播放进度校准等操作。
    OH_LOG_INFO(LOG_APP,
        "AudioTimestamp: framePos=%{public}lld, ts=%{public}lld ns, latency=%{public}d ms",
        (long long)framePosition, (long long)timestampNs, audioLatencyMs);
} else {
    OH_LOG_ERROR(LOG_APP, "GetAudioTimestampInfo failed, ret: %{public}d", tsRet);
}
```

## 注意事项

[OH_AudioRenderer_GetAudioTimestampInfo](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo)从API版本15开始支持。若目标设备的API版本低于15，需要使用[OH_AudioRenderer_GetTimestamp](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_gettimestamp)（从API版本10开始支持）替代。

两个接口的功能类似，均可获取音频流的播放位置（framePosition）和时间戳（timestamp），但存在以下差异：

| 接口 | 差异 |
| --- | --- |
| OH_AudioRenderer_GetAudioTimestampInfo | 支持倍速播放场景，例如2倍速时播放位置增长速度也为正常2倍。 |
| OH_AudioRenderer_GetTimestamp | 不支持倍速播放场景，设置倍速后播放位置的增长速度不会随之变化。调用时需传入`clockId`参数，并指定为`CLOCK_MONOTONIC`。 |

需要支持倍速播放场景，或目标API版本为15及以上时，使用OH_AudioRenderer_GetAudioTimestampInfo。需兼容API版本10至14时，使用OH_AudioRenderer_GetTimestamp，并将`clockId`传为`CLOCK_MONOTONIC`。
