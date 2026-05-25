# 使用AVPlayer播放流媒体(C/C++)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia--> 
<!--Owner: @chennotfound-->
<!--Designer: @dongyu_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

从API version 11开始，支持使用[AVPlayer](../../reference/apis-media-kit/capi-avplayer.md)实现端到端播放流媒体资源。本开发指导将以完整地播放一个流媒体作为示例，向开发者讲解AVPlayer流媒体播放相关功能。

播放的全流程包含：创建AVPlayer、设置回调监听函数、设置播放资源、设置播放参数（音量/倍速/焦点模式）、设置播放窗口、播放控制（播放/暂停/跳转/停止）、重置、销毁播放器实例。

在进行应用开发的过程中，开发者可以通过AVPlayer的信息监听回调函数[OH_AVPlayerOnInfoCallback](../../reference/apis-media-kit/capi-avplayer-base-h.md#oh_avplayeroninfocallback)和错误监听回调函数[OH_AVPlayerOnErrorCallback](../../reference/apis-media-kit/capi-avplayer-base-h.md#oh_avplayeronerrorcallback)主动获取播放过程信息。如果应用在视频播放器处于错误状态时执行操作，系统会抛出异常或生成其他未定义的行为。

状态的详细说明请参考[AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate)。当播放处于prepared/playing/paused/completed状态时，播放引擎处于工作状态，这需要占用系统较多的运行内存。当客户端暂时不使用播放器时，调用reset()或release()回收内存资源，合理利用资源。

**播放状态变化示意图：**
![Playback status change](figures/playback-status-change-ndk.png)

## 开发建议

当前指导仅介绍如何实现流媒体资源播放，如需播放本地资源，请参考[使用AVPlayer播放视频(C/C++)](using-ndk-avplayer-for-video-playback.md)。如果在应用开发过程中涉及后台播放、播放冲突等情况，请根据实际需要参考以下说明。
 
避免播放被系统强制中断。此功能仅适用于ArkTS API，如需使用此功能请参考[使用AVPlayer播放视频(ArkTS)](video-playback.md)。
- 应用在播放过程中，若播放的媒体数据涉及音频，根据系统音频管理策略（参考[处理音频焦点变化](../audio/audio-playback-concurrency.md#处理音频焦点变化)事件），会存在被其他应用打断的情况，建议通过[OH_AVPlayer_SetOnInfoCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setoninfocallback)主动监听音频打断事件[AVPlayerOnInfoType](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayeroninfotype).AV_INFO_TYPE_INTERRUPT_EVENT，根据具体内容提示，做出相应的处理，避免出现应用状态与预期效果不一致的问题。
- 面对设备同时连接多个音频输出设备的情况，建议通过[OH_AVPlayer_SetOnInfoCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setoninfocallback)主动监听音频输出设备变更事件[AVPlayerOnInfoType](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayeroninfotype).AV_INFO_TYPE_AUDIO_OUTPUT_DEVICE_CHANGE，并做出相应处理。
- 应用在播放过程中，系统内部会因为网络数据下载失败、媒体服务异常终止等发生异常。建议通过[OH_AVPlayer_SetOnErrorCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setonerrorcallback)接口设置错误监听回调函数，根据不同错误类型，做出相应处理，避免出现播放异常。

## 开发步骤及注意事项

- 在CMake脚本中链接动态库。

  ```C++
  target_link_libraries(sample PUBLIC libavplayer.so)
  ```

- 使用[OH_AVPlayer_SetOnInfoCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setoninfocallback)、[OH_AVPlayer_SetOnErrorCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setonerrorcallback)接口设置信息监听回调函数和错误监听回调函数，需要在CMake脚本中链接如下动态库。

  ```C++
  target_link_libraries(sample PUBLIC libnative_media_core.so)
  ```

- 开发者使用系统日志能力时，需引入如下头文件。

  ```C++
  #include <hilog/log.h>
  ```

  并需要在CMake脚本中链接如下动态库。

  ```C++
  target_link_libraries(sample PUBLIC libhilog_ndk.z.so)
  ```

开发者通过引入[avplayer.h](../../reference/apis-media-kit/capi-avplayer-h.md)、[avplayer_base.h](../../reference/apis-media-kit/capi-avplayer-base-h.md)和[native_averrors.h](../../reference/apis-avcodec-kit/capi-native-averrors-h.md)头文件，使用流媒体播放相关API。

详细的API说明请参考[AVPlayer](../../reference/apis-media-kit/capi-avplayer.md)。

1. 创建AVPlayer实例：调用[OH_AVPlayer_Create()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_create)接口，AVPlayer初始化为[AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate).AV_IDLE状态。

   <!-- @[OH_AVPlayer_Create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   OH_AVPlayer *player = OH_AVPlayer_Create();
   ```

2. 设置回调监听函数：使用[OH_AVPlayer_SetOnInfoCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setoninfocallback)和[OH_AVPlayer_SetOnErrorCallback()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setonerrorcallback)接口设置信息监听回调函数和错误监听回调函数，配合全流程场景使用。获取更多信息的同时还可以通过设置userData区分不同播放实例。

   支持的监听事件如下所示：
 
   | 事件类型 | 说明 |
   | -------- | -------- |
   | OH_AVPlayerOnInfoCallback | 必要事件，监听播放器的过程信息。<br>需要播放器在AV_IDLE状态下、未调用设置资源接口前完成设置监听。如果在调用设置资源接口后再设置监听，会导致无法收到资源设置过程中上报的OH_AVPlayerOnInfoCallback事件。 |
   | OH_AVPlayerOnErrorCallback | 必要事件，监听播放器的错误信息。<br>需要播放器在AV_IDLE状态下、未调用设置资源接口前完成设置监听。如果在调用设置资源接口后再设置监听，会导致无法收到资源设置过程中上报的OH_AVPlayerOnErrorCallback事件。 |

   <!-- @[OH_AVPlayer_SetOnInfoCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // 设置回调，监听信息。
   LOG("call OH_AVPlayer_SetPlayerOnInfoCallback");
   int32_t ret = OH_AVPlayer_SetOnInfoCallback(player, OHAVPlayerOnInfoCallback, nullptr);
   LOG("OH_AVPlayer_SetPlayerOnInfoCallback ret:%{public}d", ret);
   ```

   <!-- @[OH_AVPlayer_SetOnErrorCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   LOG("call OH_AVPlayer_SetPlayerOnErrorCallback");
   ret = OH_AVPlayer_SetOnErrorCallback(player, OHAVPlayerOnErrorCallback, nullptr);
   LOG("OH_AVPlayer_SetPlayerOnErrorCallback ret:%{public}d", ret);
   ```

3. 设置资源：调用[OH_AVPlayer_SetURLSource()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_seturlsource)，设置属性URL（支持点播和直播源），AVPlayer进入[AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate).AV_INITIALIZED（初始化）状态。

   <!-- @[OH_AVPlayer_SetURLSource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   LOG("player %{public}s >> URL source", url);
   LOG("call %{public}s", "OH_AVPlayer_SetUrlSource");
   ret = OH_AVPlayer_SetURLSource(player, url);
   LOG("OH_AVPlayer_SetUrlSource ret:%{public}d", ret);
   ```

4. （可选）设置智能追帧：直播场景下调用[OH_AVPlayer_SetPlaybackStrategy()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setplaybackstrategy)，设置AVPlayer启用智能追帧。

   <!-- @[OH_AVPlayer_SetPlaybackStrategy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   void OHAVPlayerSetPlaybackStrategy(OH_AVPlayer *player)
   {
       // 设置播放策略。
       OH_AVPlaybackStrategy *myStrategy = OH_AVPlaybackStrategy_Create();
       double waterLine = 6.0;
       OH_AVPlaybackStrategy_SetThresholdForAutoQuickPlay(myStrategy, waterLine); // 直播场景设置智能追帧。
       int32_t ret = OH_AVPlayer_SetPlaybackStrategy(player, myStrategy);
       LOG("OH_AVPlayer_SetPlaybackStrategy ret:%{public}d", ret);
       OH_AVPlaybackStrategy_Destroy(myStrategy);
   }
   ```

5. （可选）设置音频流类型：调用[OH_AVPlayer_SetAudioRendererInfo()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setaudiorendererinfo)，设置AVPlayer音频流类型。

   <!-- @[OH_AVPlayer_SetAudioRendererInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // 设置音频流类型。
   LOG("call %{public}s", "OH_AVPlayer_SetAudioRendererInfo");
   OH_AudioStream_Usage streamUsage = OH_AudioStream_Usage::AUDIOSTREAM_USAGE_UNKNOWN;
   ret = OH_AVPlayer_SetAudioRendererInfo(player, streamUsage);
   LOG("OH_AVPlayer_SetAudioRendererInfo ret:%{public}d", ret);
   ```

6. （可选）设置音频打断模式：调用[OH_AVPlayer_SetAudioInterruptMode()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setaudiointerruptmode)，设置AVPlayer音频流打断模式。

   <!-- @[OH_AVPlayer_SetAudioInterruptMode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // 设置音频流打断模式。
   LOG("call OH_AVPlayer_SetAudioInterruptMode");
   OH_AudioInterrupt_Mode interruptMode = OH_AudioInterrupt_Mode::AUDIOSTREAM_INTERRUPT_MODE_INDEPENDENT;
   ret = OH_AVPlayer_SetAudioInterruptMode(player, interruptMode);
   LOG("OH_AVPlayer_SetAudioInterruptMode ret:%{public}d", ret);
   ```

7. 设置播放画面窗口：调用[OH_AVPlayer_SetVideoSurface()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setvideosurface)设置播放画面窗口。此函数必须在SetSource之后，Prepare之前调用。

   <!-- @[OH_AVPlayer_SetVideoSurface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   ret = OH_AVPlayer_SetVideoSurface(player, context->nativeWindow_);
   LOG("OH_AVPlayer_SetVideoSurface ret:%{public}d", ret);
   ```

8. 准备播放：调用[OH_AVPlayer_Prepare()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_prepare)，AVPlayer进入[AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate).AV_PREPARED（准备）状态，此时可以获取时长，设置音量。

   <!-- @[OH_AVPlayer_Prepare](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   ret = OH_AVPlayer_Prepare(player); // 设置播放源后触发该状态上报。
   if (ret != AV_ERR_OK) {
       // 处理异常。
       LOG("player %{public}s", "OH_AVPlayer_Prepare Err");
   }
   ```

9. （可选）设置音频音效模式：调用[OH_AVPlayer_SetAudioEffectMode()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setaudioeffectmode)，设置AVPlayer音频音效模式。

   <!-- @[OH_AVPlayer_SetAudioEffectMode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   LOG("AVPlayerState AV_PREPARED");
   ret = OH_AVPlayer_SetAudioEffectMode(player, EFFECT_NONE); // 设置音频音效模式。
   LOG("OH_AVPlayer_SetAudioEffectMode ret:%{public}d", ret);
   ```

10. 播放控制：包含播放[OH_AVPlayer_Play()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_play)、暂停[OH_AVPlayer_Pause()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_pause)、跳转[OH_AVPlayer_Seek()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_seek)、停止[OH_AVPlayer_Stop()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_stop)等操作。

    <!-- @[OH_AVPlayer_Play](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value NAPI_Global_Play(napi_env env, napi_callback_info info) {
        int ret = -1;
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            ret = OH_AVPlayer_Play(context->player_);
            LOG("OH_AVPlayer_Play ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, ret, &value);
        return value;
    }
    ```

    <!-- @[OH_AVPlayer_Pause](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value NAPI_Global_Pause(napi_env env, napi_callback_info info) {
        int ret = 100;
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            ret = OH_AVPlayer_Pause(context->player_);
            LOG("OH_AVPlayer_Pause ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, ret, &value);
        return value;
    }
    ```

    <!-- @[OH_AVPlayer_Seek](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value NAPI_Global_Seek(napi_env env, napi_callback_info info) {
        size_t argc = 2;
        napi_value args[2] = {nullptr};
        napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
        int seekValue;
        napi_get_value_int32(env, args[0], &seekValue);
        int mode;
        napi_get_value_int32(env, args[1], &mode);
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            int ret;
            switch (mode) {
            case 0:
                LOG("call NAPI_Global_Seek value:%{public}d  mode:AV_SEEK_NEXT_SYNC", seekValue);
                ret = OH_AVPlayer_Seek(context->player_, seekValue, AV_SEEK_NEXT_SYNC);
                break;
            case 1:
                LOG("call NAPI_Global_Seek value:%{public}d  mode:AV_SEEK_PREVIOUS_SYNC", seekValue);
                ret = OH_AVPlayer_Seek(context->player_, seekValue, AV_SEEK_PREVIOUS_SYNC);
                break;
            case 2:
                LOG("call NAPI_Global_Seek value:%{public}d  mode:AV_SEEK_CLOSEST", seekValue);
                ret = OH_AVPlayer_Seek(context->player_, seekValue, AV_SEEK_CLOSEST);
                break;
            default:
                LOG("call NAPI_Global_Seek value:%{public}d  mode:AV_SEEK_PREVIOUS_SYNC", seekValue);
                ret = OH_AVPlayer_Seek(context->player_, seekValue, AV_SEEK_PREVIOUS_SYNC);
                break;
            }
            LOG("OH_AVPlayer_Seek ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, 0, &value);
        return value;
    }
    ```

    <!-- @[OH_AVPlayer_Stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value NAPI_Global_Stop(napi_env env, napi_callback_info info) {
        int ret = 100;
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            ret = OH_AVPlayer_Stop(context->player_);
            LOG("OH_AVPlayer_Stop ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, ret, &value);
        return value;
    }
    ```

11. （可选）更换资源：调用[OH_AVPlayer_Reset()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_reset)重置资源，AVPlayer重新进入[AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate).AV_IDLE（空闲）状态，允许更换资源URL。

    <!-- @[OH_AVPlayer_Reset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value NAPI_Global_Reset(napi_env env, napi_callback_info info) {
        int ret = 100;
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            ret = OH_AVPlayer_Reset(context->player_);
            LOG("OH_AVPlayer_Reset ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, ret, &value);
        return value;
    }
    ```

12. 退出播放：调用[OH_AVPlayer_Release()](../../reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_release)销毁实例，AVPlayer进入[AVPlayerState](../../reference/apis-media-kit/capi-avplayer-base-h.md#avplayerstate).AV_RELEASED（释放）状态，退出播放。如果后续再操作AVPlayer实例，则行为未知，可能导致应用进程崩溃，应用异常退出等情况。

    <!-- @[OH_AVPlayer_Release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value NAPI_Global_Release(napi_env env, napi_callback_info info) {
        int ret = -1;
        auto context = SampleManager::GetInstance();
        if (context->player_ != NULL) {
            ret = OH_AVPlayer_Release(context->player_);
            LOG("OH_AVPlayer_Release ret:%{public}d", ret);
        } else {
            LOG("no found Player Instances");
        }
        napi_value value;
        napi_create_int32(env, ret, &value);
        return value;
    }
    ```

## 运行完整示例

1. 新建工程，下载[示例工程](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDKStreamingMedia)。
2. 编译新建工程并运行。
