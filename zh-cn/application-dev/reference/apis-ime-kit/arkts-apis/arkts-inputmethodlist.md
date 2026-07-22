# @ohos.inputMethodList

## 导入模块

```TypeScript
import { Pattern, InputMethodListDialog, PatternOptions } from '@kit.IMEKit';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [InputMethodListDialog](arkts-ime-inputmethodlist-inputmethodlistdialog-s.md) | InputMethodListDialog({controller: CustomDialogController, patternOptions?: PatternOptions})  输入法切换列表弹窗控件。以弹窗形式展示当前系统中已安装的输入法应用列表，支持用户在输入法之间进行切换；对于默认输入法，还提供键盘模式（如单手模式、全屏模式等）的切换入口。  **使用场景：** 当系统应用或输入法应用需要为用户提供可视化的输入法选择和切换功能时使用此控件。例如，在系统设置应用中允许用户选择不同输入法，或在输入法应用中允许用户切换到其他输入法或切换当前输入法的键盘模式。  **使用后效果：** 调用此控件后，将弹出输入法切换列表弹窗。用户在弹窗中选择输入法后，系统将切换到指定的输入法；若用户选择了默认输入法的模式选项，系统将按指定模式显示键盘布局。  **相似接口差异点及选取原则：** 与[inputMethod.switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md#switchinputmethod)接口相比，本控件提供了可视化的输入法选择界面，适用于需要交互式选择界面的场景；switchInputMethod接口适用于程序化切换输入法的场景，无需用户手动选择。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Pattern](arkts-ime-inputmethodlist-pattern-i.md) | 输入法模式选项的图标资源定义，用于配置键盘模式在弹窗中的视觉表现。仅当前输入法（即系统预置输入法）可使用。 |
| [PatternOptions](arkts-ime-inputmethodlist-patternoptions-i.md) | 输入法模式选项配置，用于定义键盘模式的切换选项。 |

