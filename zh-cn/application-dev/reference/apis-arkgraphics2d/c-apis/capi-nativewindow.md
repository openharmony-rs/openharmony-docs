# NativeWindow

## 概述

提供NativeWindow功能，作为数据生产者，可用来和egl对接。

**起始版本：** 12
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [graphic_error_code.h](capi-graphic-error-code-h.md) | 定义错误码，用于标识接口调用过程中可能出现的各类错误情况，包括内存操作错误、参数无效、权限不足、缓冲区状态异常、设备不支持等，帮助开发者快速定位和排查接口调用失败的原因。 |
| [buffer_handle.h](capi-buffer-handle-h.md) | 定义NativeWindow模块使用的BufferHandle的结构体。 |
| [external_window.h](capi-external-window-h.md) | 定义获取和使用NativeWindow的相关函数。 |
