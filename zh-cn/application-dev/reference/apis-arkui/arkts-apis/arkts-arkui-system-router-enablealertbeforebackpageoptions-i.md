# EnableAlertBeforeBackPageOptions

定义EnableAlertBeforeBackPage选项。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SystemRouter, BackRouterOptions, DisableAlertBeforeBackPageOptions, EnableAlertBeforeBackPageOptions, RouterOptions, RouterState } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel?: (errMsg: string) => void
```

用户选择对话框取消按钮时触发，errMsg表示返回信息。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md)

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

**替代接口：** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## success

```TypeScript
success?: (errMsg: string) => void
```

用户选择对话框确认按钮时触发，errMsg表示返回信息。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errMsg | string | 是 |  |

## message

```TypeScript
message: string
```

询问对话框内容。

**类型：** string

**起始版本：** 6

**废弃版本：** 8

**替代接口：** message

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
