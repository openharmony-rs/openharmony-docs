# @ohos.arkui.advanced.Dialog(Dialog)

弹出框是一种模态窗口，用于临时展示用户需关注的信息或待处理的操作，同时保持当前上下文环境。用户必须完成交互才能退出该模式。

> **说明：**
 >
 > - 该组件从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
 >
 > - 该组件仅可在Stage模型下使用。
 >
 > - 如果Dialog设置通用属性和通用事件，编译工具链会额外生
 > 成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到Dialog本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议Dialog设置通用属性和通用事件。



## 导入模块

```TypeScript
import { AlertDialog, ButtonOptions, ConfirmDialog, LoadingDialog, SelectDialog, TipsDialog, CustomContentDialog, PopoverDialog, PopoverOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md) |  |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AlertDialog](arkts-arkui-arkui-advanced-dialog-alertdialog-s.md) | 操作确认类弹出框，用于在触发一个将产生严重后果的不可逆操作（如删除、重置、取消编辑、停止等）时进行确认。 |
| [ConfirmDialog](arkts-arkui-arkui-advanced-dialog-confirmdialog-s.md) | 信息确认类弹出框，用于在操作未正确执行（如网络错误、电池电量过低），或未正确操作时（如指纹录入）反馈错误或提示信息。 |
| [CustomContentDialog](arkts-arkui-arkui-advanced-dialog-customcontentdialog-s.md) | 自定义内容区弹出框，同时支持定义操作区按钮样式。 |
| [LoadingDialog](arkts-arkui-arkui-advanced-dialog-loadingdialog-s.md) | 进度加载类弹出框，用于显示操作执行中的提示信息。 |
| [PopoverDialog](arkts-arkui-arkui-advanced-dialog-popoverdialog-s.md) | 跟手弹出框，基于目标组件位置弹出，上述的TipsDialog、SelectDialog、ConfirmDialog、AlertDialog、LoadingDialog、CustomContentDialog都可作为弹出框内容。 |
| [SelectDialog](arkts-arkui-arkui-advanced-dialog-selectdialog-s.md) | 选择类弹出框，弹框中以列表或网格的形式提供可选的内容。 |
| [TipsDialog](arkts-arkui-arkui-advanced-dialog-tipsdialog-s.md) | 提示弹出框，用于提醒用户关注特定事项或进行确认操作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PopoverOptions](arkts-arkui-arkui-advanced-dialog-popoveroptions-i.md) | 跟手弹出框参数，用于设置弹出框内容、位置属性等。 |

## 示例

```TypeScript
### 示例1（上图下文弹出框）

上图下文弹出框，包含imageRes、content等内容。


```

```TypeScript
### 示例2（纯列表弹出框）

纯列表弹出框，包含selectedIndex、radioContent等内容。


```

```TypeScript
### 示例3（文本与勾选弹出框）

文本与勾选弹出框，包含content、checkTips等内容。


```

```TypeScript
### 示例4（纯文本弹出框）

纯文本弹出框，包含primaryTitle、secondaryTitle、content等内容。


```

```TypeScript
### 示例5（进度加载类弹出框）

进度加载类弹出框，包含content等内容。


```

```TypeScript
### 示例6（自定义主题风格弹出框）

自定义主题风格弹出框，包含content、theme等内容。


```

```TypeScript
### 示例7（自定义深浅色模式弹出框）

自定义深浅色模式弹出框，包含content、themeColorMode等内容。


```

```TypeScript
### 示例8（自定义内容弹出框）

支持自定义内容弹出框，包含contentBuilder、buttons等内容。


```

```TypeScript
### 示例9（跟手弹出框）

从API version 14开始，该示例展示了设置跟手弹出框（警告弹出框为例），包含visible、popover、targetBuilder等内容。


```

```TypeScript
### 示例10（弹出框按钮设置默认获焦）

从API version 18开始，该示例展示了设置默认获焦按钮弹出框（以AlertDialog为例），包含defaultFocus等内容。
```
