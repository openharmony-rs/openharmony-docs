# AVPlayerCallback
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

AVPlayerCallback是AVPlayer的回调管理结构体，包含了播放过程信息OH_AVPlayerOnInfo和错误信息OH_AVPlayerOnError的回调函数指针。应用需注册此实例结构体到OH_AVPlayer实例中，并对回调上报的信息进行处理，保证AVPlayer的正常运行。通过注册这些回调，开发者可以实时监控AVPlayer的播放状态、获取播放过程信息（如缓冲进度、播放位置等）和错误事件，及时响应和处理播放过程中的各种事件，适用于需要对播放流程进行细粒度控制和监控的场景。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback)或[OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback)。

**相关模块：** [AVPlayer](capi-avplayer.md)

**所在头文件：** [avplayer_base.h](capi-avplayer-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| OH_AVPlayerOnInfo onInfo | 监控AVPlayer过程信息，需注册此回调到AVPlayer实例中使用，详细内容参考[OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo)。<br>**起始版本：** 11<br>**废弃版本：** 12<br>**替代接口：** [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) |
| OH_AVPlayerOnError onError | 监控AVPlayer操作错误，需注册此回调到AVPlayer实例中使用。回调签名为OH_AVPlayerOnError。回调参数信息请参考[OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror)。<br>**起始版本：** 11<br>**废弃版本：** 12<br>**替代接口：** [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback) |
