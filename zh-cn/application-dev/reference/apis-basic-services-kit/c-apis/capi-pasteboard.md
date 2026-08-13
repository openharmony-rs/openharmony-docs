# Pasteboard

## 概述

系统剪贴板支持复制和粘贴多种类型的数据。可以使用此模块接口操作纯文本、HTML、URI、PixelMap等多种类型的数据。

**起始版本：** 13
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [oh_pasteboard_err_code.h](capi-oh-pasteboard-err-code-h.md) | 声明剪贴板框架错误码信息。剪贴板错误码用于标识剪贴板操作过程中的执行结果，开发者可通过错误码判断操作是否成功以及失败的具体原因。 |
| [oh_pasteboard.h](capi-oh-pasteboard-h.md) | 提供访问系统剪贴板的接口、数据结构、枚举类型。支持剪贴板数据的读写、监听剪贴板内容变化、获取粘贴进度等功能。 |
