# DisableAlertBeforeBackPageOptions

定义DisableAlertBeforeBackPage参数选项。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** RouterOptions

<!--Device-unnamed-export interface DisableAlertBeforeBackPageOptions--><!--Device-unnamed-export interface DisableAlertBeforeBackPageOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { BackRouterOptions, DisableAlertBeforeBackPageOptions, RouterOptions, RouterState, EnableAlertBeforeBackPageOptions } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel?: (errMsg: string) => void
```

关闭询问对话框失败时触发，errMsg表示返回信息。

**类型：** (errMsg: string) =&gt; void

**起始版本：** 6

**废弃版本：** 8

**替代接口：** RouterOptions

<!--Device-DisableAlertBeforeBackPageOptions-cancel?: (errMsg: string) => void--><!--Device-DisableAlertBeforeBackPageOptions-cancel?: (errMsg: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## complete

```TypeScript
complete?: () => void
```

当对话框关闭时触发该回调。

**类型：** () =&gt; void

**起始版本：** 6

**废弃版本：** 8

**替代接口：** RouterOptions

<!--Device-DisableAlertBeforeBackPageOptions-complete?: () => void--><!--Device-DisableAlertBeforeBackPageOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## success

```TypeScript
success?: (errMsg: string) => void
```

关闭询问对话框成功时触发，errMsg表示返回信息。

**类型：** (errMsg: string) =&gt; void

**起始版本：** 6

**废弃版本：** 8

**替代接口：** RouterOptions

<!--Device-DisableAlertBeforeBackPageOptions-success?: (errMsg: string) => void--><!--Device-DisableAlertBeforeBackPageOptions-success?: (errMsg: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

