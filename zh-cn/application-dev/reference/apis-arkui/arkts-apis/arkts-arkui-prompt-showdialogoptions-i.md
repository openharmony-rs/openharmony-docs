# ShowDialogOptions

定义显示对话框的选项。

**起始版本：** 3

<!--Device-unnamed-export interface ShowDialogOptions--><!--Device-unnamed-export interface ShowDialogOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ShowActionMenuOptions, Button, ShowToastOptions, ShowDialogOptions, ShowDialogSuccessResponse } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons?: [Button, Button?, Button?]
```

对话框中按钮的数组，结构为：{text:'button', color: '#666666'}，支持1-6个按钮。大于6个按钮时弹窗不显示。

**类型：** [Button, Button?, Button?]

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowDialogOptions-buttons?: [Button, Button?, Button?]--><!--Device-ShowDialogOptions-buttons?: [Button, Button?, Button?]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancel

```TypeScript
cancel?: (data: string, code: string) => void
```

接口调用失败的回调函数。

**类型：** (data: string, code: string) =&gt; void

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowDialogOptions-cancel?: (data: string, code: string) => void--><!--Device-ShowDialogOptions-cancel?: (data: string, code: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## complete

```TypeScript
complete?: (data: string) => void
```

接口调用结束的回调函数。

**类型：** (data: string) =&gt; void

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowDialogOptions-complete?: (data: string) => void--><!--Device-ShowDialogOptions-complete?: (data: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message?: string
```

文本内容。

**类型：** string

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowDialogOptions-message?: string--><!--Device-ShowDialogOptions-message?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## success

```TypeScript
success?: (data: ShowDialogSuccessResponse) => void
```

接口调用成功的回调函数。

**类型：** (data: ShowDialogSuccessResponse) =&gt; void

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowDialogOptions-success?: (data: ShowDialogSuccessResponse) => void--><!--Device-ShowDialogOptions-success?: (data: ShowDialogSuccessResponse) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

标题文本。

**类型：** string

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowDialogOptions-title?: string--><!--Device-ShowDialogOptions-title?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

