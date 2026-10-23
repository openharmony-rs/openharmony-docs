# OH_AudioSuite_FeatureVersionInfo（系统接口）
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AudioSuite_FeatureVersionInfo {...} OH_AudioSuite_FeatureVersionInfo
```

## 概述

定义特性版本信息结构体。

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

**所在头文件：** [native_audio_suite_download_manager.h](capi-native-audio-suite-download-manager-h-sys.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char featureName[256] | 特性名称。<br>**起始版本：** 26.0.1 |
| int32_t downloadStatus | 特性当前状态。<br>**起始版本：** 26.0.1 |
| char version[128] | 特性版本。<br>**起始版本：** 26.0.1 |
| int64_t size | 特性模块占用空间大小。单位为：字节。<br>**起始版本：** 26.0.1 |
| int32_t errorCode | 错误码。<br>**起始版本：** 26.0.1 |
