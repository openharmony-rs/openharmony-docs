# DisableAlertBeforeBackPageOptions

定义DisableAlertBeforeBackPage参数选项。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** RouterOptions

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SystemRouter, BackRouterOptions, DisableAlertBeforeBackPageOptions, EnableAlertBeforeBackPageOptions, RouterOptions, RouterState } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel?: (errMsg: string) => void
```

关闭询问对话框失败时触发，errMsg表示返回信息。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** RouterOptions

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errMsg | string | 是 |  |

## complete

```TypeScript
complete?: () => void
```

当对话框关闭时触发该回调。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** RouterOptions

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## success

```TypeScript
success?: (errMsg: string) => void
```

关闭询问对话框成功时触发，errMsg表示返回信息。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** RouterOptions

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errMsg | string | 是 |  |
