# AVPlayerCallback

```c
typedef struct AVPlayerCallback {...} AVPlayerCallback
```

## 概述

AVPlayerCallback（AVPlayer回调）是AVPlayer（音视频播放器）的回调管理结构体， 包含了播放过程信息OH_AVPlayerOnInfo和错误信息OH_AVPlayerOnError的回调函数指针。 应用需注册此实例结构体到OH_AVPlayer实例中，并对回调上报的信息进行处理，保证AVPlayer的正常运行。 通过注册这些回调，开发者可以实时监控AVPlayer的播放状态、获取播放过程信息（如缓冲进度、播放位置等）和错误事件，及时响应和处理播放过程中的各种事件。 适用于需要对播放流程进行细粒度控制（Fine-grained Control）和监控的场景，如音乐播放器、视频播放器、直播应用等需要实时监控播放状态和异常处理的应用。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** {@link OH_AVPlayerOnInfoCallback}或{@link OH_AVPlayerOnErrorCallback}。

**相关模块：** [AVPlayer](capi-avplayer.md)

**所在头文件：** [avplayer_base.h](capi-avplayer-base-h.md)

