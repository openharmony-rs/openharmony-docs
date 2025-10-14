# 低功耗音频播放
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

从API version 11开始支持低功耗音频播放。

低功耗音频播放是一种通过软硬芯协同设计实现的音频渲染方案。其核心机制在于增大音频渲染器的内部缓存，使系统能够一次性填充大量音频数据，从而允许主处理器进入长时间休眠状态，避免因频繁处理音频数据而产生的功耗开销，最终达成系统级功耗负载的显著降低。

当创建普通音频渲染器使用[STREAM_USAGE_MUSIC](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage)或[STREAM_USAGE_AUDIOBOOK](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage)时，系统会默认优先使用低功耗音频渲染器。渲染器缓存因使用场景会存在差异。在亮屏场景，缓存最大1000ms；在熄屏场景，缓存最大10000ms。熄屏场景下，缓存填满后，主处理器会进入休眠状态。当渲染器缺数据时，唤醒主处理器触发应用送数据。送数据周期同渲染器缓存大小一致。

## 使用前提

- 当前支持外放、有线耳机和部分蓝牙耳机实现低功耗功能。

- 低功耗渲染器和低时延渲染器不能实现并发，以先使用优先原则，后使用者降级普通渲染器。

## 开发指导

低功耗音频渲染器与普通音频渲染器接口无差异，仅在应用数据周期与播放进度上存在差异。音频渲染器使用请参考[使用AudioRenderer开发音频播放功能](using-audiorenderer-for-playback.md)和[使用OHAudio开发音频播放功能(C/C++)](using-ohaudio-for-playback.md)。

**数据周期示意图**

![power-saving-data-period](figures/power-saving-data-period.png)

**播放进度示意图**

![power-saving-data-progress](figures/power-saving-data-progress.png)

### 注意事项

1. 流类型使用[STREAM_USAGE_MUSIC](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage)或[STREAM_USAGE_AUDIOBOOK](../../reference/apis-audio-kit/arkts-apis-audio-e.md#streamusage)。

   > **说明：**
   > 普通渲染器指定音乐流与听书流类型，系统默认是低功耗渲染器。

2. 数据写入周期变化，亮屏场景最大1000ms周期，熄屏场景最大10000ms周期。

    > **注意：**
    > - 应用感知周期内未请求数据属于正常情况，无需主动停流。系统感知应用长时间未送数据，也会自决策停流；当应用再次送数据，系统会恢复流状态。
    > - 熄屏场景写满缓存后，主处理器会休眠，应用会被冻结。若应用需要后台播放或熄屏播放，具体参考[后台播放或熄屏播放开发须知](audio-playback-overview.md#后台播放或熄屏播放开发须知)。
    > - 低功耗渲染器每次请求数据长度同普通渲染器一致，仅通过增大请求频率来填满缓存。预计1ms左右请求1次，具体受应用与硬件影响。若应用无法快速提供数据，最差降级到普通渲染器周期。
    > - 应用数据不足一次回调长度时，不要填空数据；否则会导致卡顿，除非数据到达EOS。具体参考[AudioRenderer音频数据回调](using-audiorenderer-for-playback.md#开发步骤及注意事项)和[OHAudio音频数据回调](using-ohaudio-for-playback.md#开发步骤及注意事项)。

3. 低功耗渲染器不支持并发，仅先启动的低功耗渲染器生效，后启动的降级普通渲染器。低功耗渲染器与低时延渲染器也不支持并发，以先使用优先原则。

    > **注意：**
    > - 先起低功耗渲染器A，再起低功耗渲染器B，则B降级普通渲染器。
    > - 先起低功耗渲染器，再起低时延渲染器，则低时延降级普通渲染器。
    > - 先起低时延渲染器，再起低功耗渲染器，则低功耗降级普通渲染器。

4. 应用数据写完，不代表数据已经播完。应用需要调用获取音频时间戳接口[getAudioTimestampInfo()<sup>19+<sup>](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#getaudiotimestampinfo19 "从API version 19开始支持")或[OH_AudioRenderer_GetAudioTimestampInfo()<sup>15+<sup>](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo "从API version 19开始支持")，来判断数据实际播放进度。

    > **注意：**
    > - 获取时间戳接口调用频率不要过高，建议大于200ms一次；否则会影响系统性能。
    > - 调取接口[flush()](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#flush11)或[OH_AudioRenderer_Flush()](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_flush)后，播放的数据量会重置为0。
    > - 播放数据量均会小于写入数据量。由于系统帧长与时延机制，播完的播放数据量可能不会等于写入数据量。当写完数据后获取时间戳周期内，2次时间戳不变，即为播完。或者，当写完数据后获取时间戳，应用根据设置的倍速推算还有多少播放时长，过了相应时长后，即为播完。（如：记总写入数据量$p_1$，写完后获取时间戳$p_2$，设置的倍速$\alpha$且$\alpha>0$，音频采样率$f_s$且$f_s>0$，剩余可播时长$t$。公式：$t = \frac{1}{{\alpha}f_s}(p_1-p_2)；p_1 > p_2，\alpha > 0，f_s > 0$。）