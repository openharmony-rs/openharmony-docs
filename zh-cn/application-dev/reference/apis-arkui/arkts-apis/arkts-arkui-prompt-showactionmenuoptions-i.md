# ShowActionMenuOptions

定义ShowActionMenu的选项。

**起始版本：** 6

<!--Device-unnamed-export interface ShowActionMenuOptions--><!--Device-unnamed-export interface ShowActionMenuOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ShowActionMenuOptions, Button, ShowToastOptions, ShowDialogOptions, ShowDialogSuccessResponse } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons: [Button, Button?, Button?, Button?, Button?, Button?]
```

对话框中按钮的数组，结构为：{text:'button', color: '#666666'}，支持1-6个按钮。

**类型：** [Button, Button?, Button?, Button?, Button?, Button?]

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowActionMenuOptions-buttons: [Button, Button?, Button?, Button?, Button?, Button?]--><!--Device-ShowActionMenuOptions-buttons: [Button, Button?, Button?, Button?, Button?, Button?]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## complete

```TypeScript
complete?: () => void
```

关闭对话框时调用。

**类型：** () =&gt; void

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowActionMenuOptions-complete?: () => void--><!--Device-ShowActionMenuOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fail

```TypeScript
fail?: (errMsg: string) => void
```

接口调用失败的回调函数。

**类型：** (errMsg: string) =&gt; void

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowActionMenuOptions-fail?: (errMsg: string) => void--><!--Device-ShowActionMenuOptions-fail?: (errMsg: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## success

```TypeScript
success?: (tapIndex: number, errMsg: string) => void
```

弹出对话框时调用。

**类型：** (tapIndex: number, errMsg: string) =&gt; void

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowActionMenuOptions-success?: (tapIndex: number, errMsg: string) => void--><!--Device-ShowActionMenuOptions-success?: (tapIndex: number, errMsg: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

标题文本。

**类型：** string

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowActionMenuOptions-title?: string--><!--Device-ShowActionMenuOptions-title?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

