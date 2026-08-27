# ShowDialogOptions

定义显示对话框的选项。

**起始版本：** 3

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Prompt, Button, ShowActionMenuOptions, ShowDialogOptions, ShowDialogSuccessResponse, ShowToastOptions } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel?: (data: string, code: string) => void
```

接口调用失败的回调函数。

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 |  |
| code | string | 是 |  |

## complete

```TypeScript
complete?: (data: string) => void
```

接口调用结束的回调函数。

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 |  |

## success

```TypeScript
success?: (data: ShowDialogSuccessResponse) => void
```

接口调用成功的回调函数。

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [ShowDialogSuccessResponse](arkts-arkui-system-prompt-showdialogsuccessresponse-i.md) | 是 |  |

## buttons

```TypeScript
buttons?: [Button, Button?, Button?]
```

对话框中按钮的数组，结构为：{text:'button', color: '#666666'}，支持1-6个按钮。大于6个按钮时弹窗不显示。

**类型：** [Button, Button?, Button?]

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message?: string
```

文本内容。

**类型：** string

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

标题文本。

**类型：** string

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
