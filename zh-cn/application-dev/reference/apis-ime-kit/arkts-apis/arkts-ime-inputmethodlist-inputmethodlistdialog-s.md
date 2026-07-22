# InputMethodListDialog

InputMethodListDialog({controller: CustomDialogController, patternOptions?: PatternOptions})

输入法切换列表弹窗控件。以弹窗形式展示当前系统中已安装的输入法应用列表，支持用户在输入法之间进行切换；对于默认输入法，还提供键盘模式（如单手模式、全屏模式等）的切换入口。

**使用场景：** 当系统应用或输入法应用需要为用户提供可视化的输入法选择和切换功能时使用此控件。例如，在系统设置应用中允许用户选择不同输入法，或在输入法应用中允许用户切换到其他输入法或切换当前输入法的键盘模式。

**使用后效果：** 调用此控件后，将弹出输入法切换列表弹窗。用户在弹窗中选择输入法后，系统将切换到指定的输入法；若用户选择了默认输入法的模式选项，系统将按指定模式显示键盘布局。

**相似接口差异点及选取原则：** 与[inputMethod.switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md#switchinputmethod)接口相比，本控件提供了可视化的输入法选择界面，适用于需要交互式选择界面的场景；switchInputMethod接口适用于程序化切换输入法的场景，无需用户手动选择。

**起始版本：** 11

<!--Device-unnamed-export declare struct InputMethodListDialog--><!--Device-unnamed-export declare struct InputMethodListDialog-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { Pattern, InputMethodListDialog, PatternOptions } from '@kit.IMEKit';
```

## controller

```TypeScript
controller: CustomDialogController
```

设置控制器。

**类型：** CustomDialogController

**起始版本：** 11

<!--Device-InputMethodListDialog-controller: CustomDialogController--><!--Device-InputMethodListDialog-controller: CustomDialogController-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## patternOptions

```TypeScript
patternOptions?: PatternOptions
```

设置图案选项。当不是默认输入法时，此参数可省略。

**类型：** PatternOptions

**起始版本：** 11

<!--Device-InputMethodListDialog-patternOptions?: PatternOptions--><!--Device-InputMethodListDialog-patternOptions?: PatternOptions-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

