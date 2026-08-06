# OH_AudioSuite_DownloadStatusInfo

```c
typedef struct OH_AudioSuite_DownloadStatusInfo {...} OH_AudioSuite_DownloadStatusInfo
```

## 概述

定义下载状态信息结构体。

**起始版本：** 26.0.0

**相关模块：** [AudioSuite](capi-audiosuite.md)

**所在头文件：** [native_audio_suite_download_manager.h](capi-native-audio-suite-download-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char featureName[256] | 特性名称。<br>**起始版本：** 26.0.0 |
| int32_t downloadStatus | 下载状态。<br>**起始版本：** 26.0.0 |
| int64_t size | 特性包大小。<br>**起始版本：** 26.0.0 |
| char installPath[256] | 安装路径。<br>**起始版本：** 26.0.0 |
| int32_t progress | 下载进度【0-100】。<br>**起始版本：** 26.0.0 |
| int32_t errorCode | 错误码。<br>**起始版本：** 26.0.0 |


