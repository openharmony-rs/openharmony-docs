---
kit: Media Kit / 媒体服务
description: 汇总录屏（AVScreenCapture / AVScreenCaptureRecorder）各指南文档引用的同源示例代码片段，映射到 ScreenCaptureSample 示例工程源文件，便于快速检索与对照。
keywords: AVScreenCapture,AVScreenCaptureRecorder,录屏,示例代码,同源,ScreenCaptureSample,代码片段汇总,main.h,napi_init.cpp,AVScreenCaptureDemo.ets
doctype: guide
status: active
---

# 录屏指南示例代码汇总

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->

## 概述

OpenHarmony 录屏开发指南（C/C++ 与 ArkTS）中的所有示例代码片段均同源于 [ScreenCaptureSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample) 示例工程。各指南文档通过 `<!-- @[片段名](源文件URL) -->` 标记引用示例工程中的代码段，由文档工具自动抽取渲染。

本页将分散在多份录屏指南中的示例代码片段统一汇总，形成 **「指南文档 → 代码片段 → 源文件 → 功能」** 的映射，便于快速检索与对照。各片段的完整代码请直接查阅对应指南文档或示例工程源文件。

## 源码示例工程

示例工程根目录：`code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main`

涉及的同源源文件共 3 个：

| 源文件（相对 entry/src/main） | 语言 | 说明 |
| --- | --- | --- |
| `cpp/main.h` | C/C++ | 录屏 C API 头文件包含（hilog、napi、display、native_avscreen_capture 等） |
| `cpp/napi_init.cpp` | C/C++ | 录屏 C API 核心实现：实例创建、参数配置、回调、启停、录屏模式、自定义策略等 |
| `ets/pages/AVScreenCaptureDemo.ets` | ArkTS | AVScreenCaptureRecorder（ArkTS）录屏写文件完整示例 |

> 示例工程还包含 `module.json5`、`resources/` 等配置，与代码片段无直接关联，本页不展开。

## 涉及的录屏指南文档

共 7 份录屏相关指南（本仓库内 `media_copy/`、`media_metadata_out/`、`media_output/media/` 三处为同源副本）：

| 指南文档 | 接口/语言 | 代码片段数 | 涉及源文件 |
| --- | --- | --- | --- |
| [using-avscreencapture-ArkTs.md](using-avscreencapture-ArkTs.md) | AVScreenCaptureRecorder / ArkTS | 10 | AVScreenCaptureDemo.ets |
| [using-avscreencapture-for-file.md](using-avscreencapture-for-file.md) | AVScreenCapture / C/C++（存文件） | 6 | main.h、napi_init.cpp |
| [using-avscreencapture-for-file-with-window.md](using-avscreencapture-for-file-with-window.md) | AVScreenCapture / C/C++（窗口级） | 8 | main.h、napi_init.cpp |
| [avscreencapture-c-basic-process.md](avscreencapture-c-basic-process.md) | AVScreenCapture / C/C++（码流基础流程） | 17 | main.h、napi_init.cpp |
| [avscreencapture-c-custom-scenarios.md](avscreencapture-c-custom-scenarios.md) | AVScreenCapture / C/C++（自定义场景） | 12 | napi_init.cpp |
| [video-supports-rectangular-area-recording.md](video-supports-rectangular-area-recording.md) | AVScreenCapture / C/C++（矩形区域） | 2 | main.h、napi_init.cpp |
| [avscreencapture-faqs.md](avscreencapture-faqs.md) | — | 0 | 无（FAQ，不含示例代码） |

合计 **55 处片段引用**，去重后约 50 个不同片段（`screenCapture_import`、`screenCapture_buffer_strategy_pickerPopUp` 等被多份指南复用，见 [跨文档复用的片段](#跨文档复用的片段)）。

## 示例代码映射详表

下面按指南文档分组，列出每个代码片段的：片段名、所属源文件、功能简述（关键 API / 作用）。

### 1. using-avscreencapture-ArkTs.md — 录屏写文件（ArkTS）

源文件：`ets/pages/AVScreenCaptureDemo.ets`

| # | 片段名 | 功能简述 |
| --- | --- | --- |
| 1 | screenCapture_arkts_import | 导入 media、fileIo、display、common 等 ArkTS 模块 |
| 2 | screenCapture_arkts_create | `media.createAVScreenCaptureRecorder()` 创建实例并赋给成员变量 |
| 3 | screenCapture_arkts_Callback | `on('stateChange')` / `on('error')` 注册状态与异常回调（含 11 种状态码分支） |
| 4 | screenCapture_arkts_config | 配置 `AVScreenCaptureRecordConfig`（宽高、fd、码率、采样率、preset 等） |
| 5 | screenCapture_arkts_init | `screenCapture.init(config)` 初始化实例 |
| 6 | screenCapture_arkts_skipPrivacyMode | `skipPrivacyMode(windowIDs)` 设置豁免隐私窗口 |
| 7 | screenCapture_arkts_startRecording | `startRecording()` 开始屏幕录制 |
| 8 | screenCapture_arkts_stopRecording | `stopRecording()` 停止录制 |
| 9 | screenCapture_arkts_release | `release()` 销毁实例、释放资源 |
| 10 | screenCapture_arkts_demo | 完整示例：将上述流程整合为一个 `AVScreenCaptureDemo` 类 |

### 2. using-avscreencapture-for-file.md — 录屏写文件（C/C++）

| # | 片段名 | 源文件 | 功能简述 |
| --- | --- | --- | --- |
| 1 | screenCapture_import | main.h | 包含 native_avscreen_capture 等头文件 |
| 2 | screenCapture_create_for_file | napi_init.cpp | `OH_AVScreenCapture_Create()` 创建实例 g_avCapture |
| 3 | screenCapture_config | napi_init.cpp | `SetConfig02()` 配置音频/视频/录制信息与回调（dataType = OH_CAPTURE_FILE） |
| 4 | screenCapture_startScreenRecording_for_file | napi_init.cpp | `OH_AVScreenCapture_StartScreenRecording()` 开始录屏（存文件） |
| 5 | screenCapture_stopScreenRecording | napi_init.cpp | `OH_AVScreenCapture_StopScreenRecording()` 停止录制 |
| 6 | screenCapture_releaseScreenRecording_for_file | napi_init.cpp | `OH_AVScreenCapture_Release()` 销毁实例释放资源 |

### 3. using-avscreencapture-for-file-with-window.md — 窗口级录屏（C/C++）

| # | 片段名 | 源文件 | 功能简述 |
| --- | --- | --- | --- |
| 1 | screenCapture_import | main.h | 包含 native_avscreen_capture 等头文件 |
| 2 | screenCapture_create | napi_init.cpp | `OH_AVScreenCapture_Create()` 创建实例 |
| 3 | screenCapture_config | napi_init.cpp | `SetConfig02()` 配置参数与回调（与存文件版相同） |
| 4 | screenCapture_createCaptureStrategy | napi_init.cpp | 方式一：`StrategyForPickerPopUp(strategy, true)` 弹 Picker 选窗口 |
| 5 | screenCapture_withWindow_forID | napi_init.cpp | 方式二：设置 missionIDs + `OH_CAPTURE_SPECIFIED_WINDOW` 指定窗口 ID |
| 6 | screenCapture_startScreenRecording | napi_init.cpp | `OH_AVScreenCapture_StartScreenRecording()` 开始窗口级录屏 |
| 7 | screenCapture_stopScreenRecording | napi_init.cpp | `OH_AVScreenCapture_StopScreenRecording()` 停止 |
| 8 | screenCapture_releaseScreenRecording | napi_init.cpp | `OH_AVScreenCapture_Release()` 释放并置空 |

### 4. avscreencapture-c-basic-process.md — 录屏基础流程（码流，C/C++）

源文件：main.h（片段 1）、napi_init.cpp（片段 2–17）

| # | 片段名 | 功能简述 |
| --- | --- | --- |
| 1 | screenCapture_import_buffer | 头文件包含（较 `_import` 额外含 native_avbuffer.h、native_buffer.h、vector） |
| 2 | screenCapture_create_buffer | `OH_AVScreenCapture_Create()` 创建实例 |
| 3 | screenCapture_config_buffer_audio | 配置 micCapInfo / innerCapInfo / audioEncInfo，`SetMicrophoneEnabled()` |
| 4 | screenCapture_config_buffer_video | 获取屏幕宽高，配置 videoCapInfo / videoEncInfo |
| 5 | screenCapture_config_buffer_init | 组装 `OH_AVScreenCaptureConfig`（dataType = OH_ORIGINAL_STREAM） |
| 6 | screenCapture_config_buffer_callback | 注册 OnError / OnStateChange / OnBufferAvailable / OnDisplaySelected 回调 |
| 7 | screenCapture_startScreenCapture | `OH_AVScreenCapture_StartScreenCapture()` 启动码流录屏 |
| 8 | screenCapture_config_buffer_OnBufferAvailable | 处理视频 / 内录 / 麦克风 buffer（fwrite 写文件） |
| 9 | screenCapture_stopScreenCapture | `OH_AVScreenCapture_StopScreenCapture()` 停止 |
| 10 | screenCapture_releaseScreenCapture | `OH_AVScreenCapture_Release()` 释放资源 |
| 11 | screenCapture_PCSpecifiedScreenConfigBuffer | 录屏模式：`OH_CAPTURE_SPECIFIED_SCREEN` 指定屏幕 |
| 12 | screenCapture_PCHomeScreenConfigBuffer | 录屏模式：`OH_CAPTURE_HOME_SCREEN` 主屏幕 |
| 13 | SetPCSpecifiedWindowScreenConfigBuffer | 录屏模式：`OH_CAPTURE_SPECIFIED_WINDOW` 单窗口（missionIDs={61}） |
| 14 | SetPCSpecifiedWindowScreenConfigBuffer2 | 录屏模式：`OH_CAPTURE_SPECIFIED_WINDOW` 多窗口（missionIDs={60,61}） |
| 15 | screenCapture_virtualExtendedScreen | 录屏模式：`OH_CAPTURE_VIRTUAL_EXTENDED_SCREEN` 虚拟扩展屏（API 26.0.1+） |
| 16 | screenCapture_buffer_strategy_pickerPopUp | `StrategyForPickerPopUp(true)` 启动后统一弹 Picker |
| 17 | screenCapture_buffer_strategy_pickerPopUpFalse | `StrategyForPickerPopUp(false)` 不弹 Picker，仅隐私弹窗 |

### 5. avscreencapture-c-custom-scenarios.md — 自定义场景（C/C++）

源文件：napi_init.cpp

| # | 片段名 | 功能简述 |
| --- | --- | --- |
| 1 | screenCapture_buffer_strategy_keepCaptureDuringCall | `StrategyForKeepCaptureDuringCall(true)` 蜂窝通话保持录屏（API 20+） |
| 2 | screenCapture_buffer_strategy_BFramesEncoding | `StrategyForBFramesEncoding(true)` 启用 B 帧编码减小文件（API 20+） |
| 3 | screenCapture_buffer_strategy_pickerPopUp | `StrategyForPickerPopUp(true)` 弹出屏幕捕获 Picker（与基础流程同名片段） |
| 4 | screenCapture_buffer_strategy_canvasFollowRotation | `StrategyForCanvasFollowRotation(true)` 跟随屏幕旋转（API 20+） |
| 5 | screenCapture_buffer_strategy_setMicrophoneEnabled | `SetMicrophoneEnabled(isMic)` 麦克风开关 |
| 6 | screenCapture_buffer_strategy_privacyMaskMode | `StrategyForPrivacyMaskMode(value)` 隐私窗口屏蔽模式（API 20+） |
| 7 | screenCapture_buffer_skipPrivacyMode | `SkipPrivacyMode(windowIds)` 豁免隐私窗口（API 12+） |
| 8 | screenCapture_buffer_setCaptureArea | `SetCaptureArea(displayId, region)` 设置捕获矩形区域（API 20+） |
| 9 | screenCapture_buffer_showCursor | `ShowCursor(false)` 光标显示开关（API 15+） |
| 10 | screenCapture_buffer_setMaxVideoFrameRate | `SetMaxVideoFrameRate(rate)` 最大帧率（API 14+） |
| 11 | screenCapture_buffer_resizeCanvas | `ResizeCanvas(w, h)` 调整录屏分辨率 |
| 12 | screenCapture_buffer_excludeContent | `ContentFilter` 过滤通知音 / 指定窗口 |

### 6. video-supports-rectangular-area-recording.md — 矩形区域录制（C/C++）

| # | 片段名 | 源文件 | 功能简述 |
| --- | --- | --- | --- |
| 1 | screenCapture_import | main.h | 头文件包含（与存文件 / 窗口级版相同） |
| 2 | screenCapture_startScreenCapture_rectangular | napi_init.cpp | 创建实例 → Init → `SetCaptureArea()` → `StartScreenCapture()` 矩形区域录屏完整流程 |

## 跨文档复用的片段

以下片段被多份指南引用（同一片段名对应同一源码段）：

| 片段名 | 源文件 | 出现在指南 |
| --- | --- | --- |
| screenCapture_import | main.h | using-avscreencapture-for-file、using-avscreencapture-for-file-with-window、video-supports-rectangular-area-recording |
| screenCapture_buffer_strategy_pickerPopUp | napi_init.cpp | avscreencapture-c-basic-process、avscreencapture-c-custom-scenarios |

> `screenCapture_import`（main.h）与 `screenCapture_import_buffer`（main.h）虽同为头文件包含，但后者额外包含 `native_avbuffer.h`、`native_buffer.h`、`<vector>`，用于码流场景，二者并非同一片段。

## 快速检索

- 想看 **ArkTS 录屏完整 Demo** → `screenCapture_arkts_demo`（AVScreenCaptureDemo.ets）
- 想看 **C/C++ 存文件录屏** → using-avscreencapture-for-file.md 的 6 个片段
- 想看 **C/C++ 码流录屏（含回调 / Buffer 处理）** → avscreencapture-c-basic-process.md
- 想看 **录屏模式（主屏 / 指定屏 / 指定窗口 / 虚拟扩展屏）** → avscreencapture-c-basic-process.md「录屏模式说明」
- 想看 **自定义策略（通话保持、B 帧、Picker、旋转、隐私、区域、光标、帧率、分辨率、内容过滤）** → avscreencapture-c-custom-scenarios.md
- 想看 **窗口级录屏（Picker / 指定窗口 ID）** → using-avscreencapture-for-file-with-window.md
- 想看 **矩形区域录屏** → video-supports-rectangular-area-recording.md
- 录屏**常见问题** → avscreencapture-faqs.md（不含代码片段）
