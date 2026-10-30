# native_avscreen_capture_errors.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

## 概述

声明屏幕录制接口调用的错误码，帮助开发者识别和处理屏幕录制中的各类异常情况，适用于屏幕录制故障排查和错误处理的开发场景。

**引用文件：** <multimedia/player_framework/native_avscreen_capture_errors.h>

**库：** libnative_avscreen_capture.so

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**起始版本：** 10

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](#oh_avscreen_capture_errcode) | OH_AVSCREEN_CAPTURE_ErrCode | 屏幕录制过程中产生的不同结果码。 |

## 枚举类型说明

### OH_AVSCREEN_CAPTURE_ErrCode

```c
enum OH_AVSCREEN_CAPTURE_ErrCode
```

**描述**

屏幕录制过程中产生的不同结果码。

开发者可在屏幕录制应用、在线会议屏幕共享、远程协助等场景中，根据返回的错误码判断接口调用的异常原因并进行相应的错误处理。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AV_SCREEN_CAPTURE_ERR_BASE = 0 | 错误码的基础值，其他错误码在此基础上递增，用于标识不同的错误类型。 | 
| AV_SCREEN_CAPTURE_ERR_OK = AV_SCREEN_CAPTURE_ERR_BASE | 操作成功。 | 
| AV_SCREEN_CAPTURE_ERR_NO_MEMORY = AV_SCREEN_CAPTURE_ERR_BASE + 1 | 内存不足。<br>可能原因：系统可用内存不足。<br>解决措施：请检查录制参数或系统内存状况。 | 
| AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT = AV_SCREEN_CAPTURE_ERR_BASE + 2 | 不允许操作。<br>可能原因：1. 实例数量超出限制时，录屏启动报错。2. 通话中未设置保持录屏策略时，无法启动录屏报错。3. 录屏超过规格限制时，无法启动录屏报错。<br>解决措施：1. 实例数量超出规格限制，当前规格为每种数据格式最多两个实例。建议释放多余实例后再使用新实例。2. 从API版本20开始，如需在通话中保持录屏，可使用[OH_AVScreenCapture_StrategyForKeepCaptureDuringCall()](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforkeepcaptureduringcall)设置“蜂窝通话时保持录屏”策略。3. 检查并调整录屏配置参数，确保视频码率（videoBitrate）取值范围在[1, 30000000]内。 | 
| AV_SCREEN_CAPTURE_ERR_INVALID_VAL = AV_SCREEN_CAPTURE_ERR_BASE + 3 | 无效参数。<br>可能原因：传入的参数不符合接口要求或取值范围不正确。<br>解决措施：请检查参数类型和取值范围后重试。 | 
| AV_SCREEN_CAPTURE_ERR_IO = AV_SCREEN_CAPTURE_ERR_BASE + 4 | 输入输出流异常。<br>可能原因：文件读写失败或数据传输错误。<br>解决措施：请检查文件路径、权限和存储空间后重试。 | 
| AV_SCREEN_CAPTURE_ERR_TIMEOUT = AV_SCREEN_CAPTURE_ERR_BASE + 5 | 网络超时。<br>可能原因：网络连接不稳定或服务器响应超时。<br>解决措施：请检查网络连接状态后重试。 | 
| AV_SCREEN_CAPTURE_ERR_UNKNOWN = AV_SCREEN_CAPTURE_ERR_BASE + 6 | 未知错误。<br>可能原因：发生了未预期的异常情况。<br>解决措施：请检查日志信息。 | 
| AV_SCREEN_CAPTURE_ERR_SERVICE_DIED = AV_SCREEN_CAPTURE_ERR_BASE + 7 | 媒体服务已终止。<br>可能原因：媒体服务进程崩溃或被系统终止。<br>解决措施：请检查系统资源或重启服务。 | 
| AV_SCREEN_CAPTURE_ERR_INVALID_STATE = AV_SCREEN_CAPTURE_ERR_BASE + 8 | 当前状态不支持此操作。<br>可能原因：调用接口时实例处于错误状态。<br>解决措施：请检查当前状态并按正确流程调用接口。 | 
| AV_SCREEN_CAPTURE_ERR_UNSUPPORT = AV_SCREEN_CAPTURE_ERR_BASE + 9 | 不支持的接口。<br>可能原因：当前版本不支持此接口或功能。<br>解决措施：请检查API版本或设备兼容性。 | 
| AV_SCREEN_CAPTURE_ERR_EXTEND_START = AV_SCREEN_CAPTURE_ERR_BASE + 100 | 预期之外的错误。<br>可能原因：发生了扩展的错误情况。<br>解决措施：请查看详细错误信息。 | 