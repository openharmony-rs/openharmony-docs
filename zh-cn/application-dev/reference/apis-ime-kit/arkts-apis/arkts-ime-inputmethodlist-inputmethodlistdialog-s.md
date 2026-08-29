# InputMethodListDialog

输入法切换列表弹窗控件。以弹窗形式展示当前系统中已安装的输入法应用列表，支持用户在输入法之间进行切换；对于默认输入法，还提供键盘模式（如单手模式、全屏模式等）的切换入口。 使用场景：当系统应用或输入法应用需要为用户提供可视化的输入法选择和切换功能时使用此控件。例如，在系统设置应用中允许用户选择不同输入法，或在输入法应用中允许用户切换到其他输入法或切换当前输入法的键盘模式。 使用后效果：调用此控件后，将弹出输入法切换列表弹窗。用户在弹窗中选择输入法后，系统将切换到指定的输入法；若用户选择了默认输入法的模式选项，系统将按指定模式显示键盘布局。 相似接口差异点及选取原则：与[inputMethod.switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md)接口相比，本控件提供了可视化的输入 法选择界面，适用于需要交互式选择界面的场景；switchInputMethod接口适用于程序化切换输入法的场景，无需用户手动选择。 使用限制：本组件仅系统应用和输入法应用可调用，patternOptions参数仅系统预置输入法支持。注意事项：  
- 前提条件：需先创建[CustomDialogController](../../apis-arkui/arkts-apis/arkts-arkui-customdialogcontroller-c.md)实例并关联InputMethodListDialog，再通过controller的open()方法打开弹  
窗。  
- 本组件不支持通用属性和通用事件。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { InputMethodListDialog, PatternOptions, Pattern } from '@kit.IMEKit';
```

## controller

```TypeScript
controller: CustomDialogController
```

输入法切换列表弹窗控制器，用于控制弹窗的打开和关闭。 使用场景：当需要通过代码控制输入法切换列表弹窗的显示与隐藏时，必须提供此参数。 使用后效果：设置后，可通过调用controller的open()方法打开弹窗， close()方法关闭弹窗。 说明：需先创建CustomDialogController实例并关联InputMethodListDialog，再通过controller.open()打开弹窗。

**类型：** CustomDialogController

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## patternOptions

```TypeScript
patternOptions?: PatternOptions
```

输入法模式选项配置。仅系统预置输入法支持。 使用场景：系统预置输入法需要支持模式切换功能（如单手模式、全屏模式等）时传入此参数，配置模式图标资源和切换回调。 默认值：不传入时，控件仅显示输入法列表，不提供模式切换功能。 说明：三方输入法应用不可使用此参数。

**类型：** [PatternOptions](arkts-ime-inputmethodlist-patternoptions-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework
