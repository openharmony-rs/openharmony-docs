# ShowDialogOptions

对话框的选项。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons?: [Button, Button?, Button?]
```

对话框中按钮的数组，结构为：{text:'button', color: '#666666'}，支持1-3个按钮。其中第一个为positiveButton，第二个为negativeButton，第三个为neutralButton。

**类型：** [Button, Button?, Button?]

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [buttons](arkts-arkui-promptaction-showdialogoptions-i.md#buttons)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message?: string
```

内容文本。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [message](arkts-arkui-promptaction-showdialogoptions-i.md#message)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

标题文本。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [title](arkts-arkui-promptaction-showdialogoptions-i.md#title)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
