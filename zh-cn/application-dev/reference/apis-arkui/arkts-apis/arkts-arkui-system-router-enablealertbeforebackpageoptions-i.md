# EnableAlertBeforeBackPageOptions

定义EnableAlertBeforeBackPage选项。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md#EnableAlertOptions)

<!--Device-unnamed-export interface EnableAlertBeforeBackPageOptions--><!--Device-unnamed-export interface EnableAlertBeforeBackPageOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancel

```TypeScript
cancel?: (errMsg: string) => void
```

用户选择对话框取消按钮时触发，errMsg表示返回信息。

**类型：** (errMsg: string) =&gt; void

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md#EnableAlertOptions)

<!--Device-EnableAlertBeforeBackPageOptions-cancel?: (errMsg: string) => void--><!--Device-EnableAlertBeforeBackPageOptions-cancel?: (errMsg: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## complete

```TypeScript
complete?: () => void
```

当对话框关闭时触发该回调。

**类型：** () =&gt; void

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md#EnableAlertOptions)

<!--Device-EnableAlertBeforeBackPageOptions-complete?: () => void--><!--Device-EnableAlertBeforeBackPageOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string
```

询问对话框内容。

**类型：** string

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** message

<!--Device-EnableAlertBeforeBackPageOptions-message: string--><!--Device-EnableAlertBeforeBackPageOptions-message: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## success

```TypeScript
success?: (errMsg: string) => void
```

用户选择对话框确认按钮时触发，errMsg表示返回信息。

**类型：** (errMsg: string) =&gt; void

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 8

**替代接口：** [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md#EnableAlertOptions)

<!--Device-EnableAlertBeforeBackPageOptions-success?: (errMsg: string) => void--><!--Device-EnableAlertBeforeBackPageOptions-success?: (errMsg: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

