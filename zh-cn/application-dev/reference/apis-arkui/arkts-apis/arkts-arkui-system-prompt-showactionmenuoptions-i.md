# ShowActionMenuOptions

定义ShowActionMenu的选项。

**起始版本：** 6

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Prompt, Button, ShowActionMenuOptions, ShowDialogOptions, ShowDialogSuccessResponse, ShowToastOptions } from '@kit.ArkUI';
```

## complete

```TypeScript
complete?: () => void
```

关闭对话框时调用。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fail

```TypeScript
fail?: (errMsg: string) => void
```

接口调用失败的回调函数。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errMsg | string | 是 |  |

## success

```TypeScript
success?: (tapIndex: number, errMsg: string) => void
```

弹出对话框时调用。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tapIndex | number | 是 |  |
| errMsg | string | 是 |  |

## buttons

```TypeScript
buttons: [Button, Button?, Button?, Button?, Button?, Button?]
```

对话框中按钮的数组，结构为：{text:'button', color: '#666666'}，支持1-6个按钮。

**类型：** [Button, Button?, Button?, Button?, Button?, Button?]

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

标题文本。

**类型：** string

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
