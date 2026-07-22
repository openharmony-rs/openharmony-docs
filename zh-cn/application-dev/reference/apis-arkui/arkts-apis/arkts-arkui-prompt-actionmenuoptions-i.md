# ActionMenuOptions

操作菜单的选项。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** ActionMenuOptions

<!--Device-prompt-interface ActionMenuOptions--><!--Device-prompt-interface ActionMenuOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons: [Button, Button?, Button?, Button?, Button?, Button?]
```

菜单中菜单项按钮的数组，结构为：{text:'button', color: '#666666'}，支持1-6个按钮。大于6个按钮时弹窗不显示。

**类型：** [Button, Button?, Button?, Button?, Button?, Button?]

**起始版本：** 8

**废弃版本：** 9

**替代接口：** buttons

<!--Device-ActionMenuOptions-buttons: [Button, Button?, Button?, Button?, Button?, Button?]--><!--Device-ActionMenuOptions-buttons: [Button, Button?, Button?, Button?, Button?, Button?]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

标题文本。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** title

<!--Device-ActionMenuOptions-title?: string--><!--Device-ActionMenuOptions-title?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

