# AVPlayerCallback<sup>(deprecated)</sup>
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @dongyu_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct AVPlayerCallback {...} AVPlayerCallback
```

## 概述

AVPlayerCallback（AVPlayer回调）是AVPlayer（音视频播放器）的回调管理结构体，包含了播放过程信息OH_AVPlayerOnInfo和错误信息OH_AVPlayerOnError的回调函数指针。应用需注册此实例结构体到OH_AVPlayer实例中，并对回调上报的信息进行处理，保证AVPlayer的正常运行。通过注册这些回调，开发者可以实时监控AVPlayer的播放状态、获取播放过程信息（如缓冲进度、播放位置等）和错误事件，及时响应和处理播放过程中的各种事件。适用于需要对播放流程进行细粒度控制（Fine-grained Control）和监控的场景，如音乐播放器、视频播放器、直播应用等需要实时监控播放状态和异常处理的应用。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback)或[OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback)。

**相关模块：** [AVPlayer](capi-avplayer.md)

**所在头文件：** [avplayer_base.h](capi-avplayer-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| OH_AVPlayerOnInfo onInfo<sup>(deprecated)</sup> | 监控AVPlayer过程信息，需注册此回调到AVPlayer实例中使用。设置该回调后，当播放器产生消息时会触发回调，开发者可实时获取播放过程信息；不设置则不会触发该回调。建议在需要实时监控播放状态、获取缓冲进度或播放位置等信息的场景中注册此回调，不注册此回调时，应用将无法收到播放过程中的状态变化通知。详细内容参考[OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo)。<br>**起始版本：** 11<br>**废弃版本：** 12<br>**替代接口：** [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) |
| OH_AVPlayerOnError onError<sup>(deprecated)</sup> | 监控AVPlayer操作错误，需注册此回调到AVPlayer实例中使用。设置该回调后，当播放器操作发生错误时会触发回调，开发者可获取错误信息进行处理；不设置则不会触发该回调。建议在需要捕获和处理播放错误的场景中注册此回调，不注册此回调时，应用将无法收到播放过程中的错误事件通知。回调签名为OH_AVPlayerOnError，回调参数信息请参考[OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror)。<br>**起始版本：** 11<br>**废弃版本：** 12<br>**替代接口：** [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback) |
