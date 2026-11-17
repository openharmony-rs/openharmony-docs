# AVSession_PlaybackPosition
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct AVSession_PlaybackPosition {...} AVSession_PlaybackPosition
```

## 概述

媒体播放位置的相关属性。

**起始版本：** 13

**相关模块：** [OHAVSession](capi-ohavsession.md)

**所在头文件：** [native_avplaybackstate.h](capi-native-avplaybackstate-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int64_t elapsedTime | 已用时间，单位为毫秒（ms）。 |
| int64_t updateTime | 更新时间，单位为毫秒（ms）。 |


