# @ohos.inputMethodList(输入法切换列表控件)

<br>
 <br>本模块是一个声明式UI组件模块，提供`InputMethodListDialog`自定义弹窗组件，用于展示系统默认输入法子类型和第三方输入法应用列表，并可选地提供输入法模式切换入口（如单手模式、全屏模式等）。
 <br>
 <br>通过本模块提供的弹窗组件，用户可以在输入法列表中查看当前系统中已安装的所有输入法，并从默认输入法切换到其他输入法；对于系统预置输入法，还可在列表中展示模式选项（如单手模式、全屏模式），供用户切换输入法键盘的显示模式。
 <br>
 <br>当系统应用或输入法应用需要提供输入法切换入口时使用本模块。典型场景包括：系统设置应用中的输入法管理页面、输入法应用自身的设置界面、或其他需要让用户选择和切换输入法的系统级界面。本组件仅系统应用和输入法应用可调用，
 `patternOptions`参数仅系统预置输入法支持。
 <br>
 <br>本模块与输入法框架其他模块的关系如下：
 <br>
 <br>- [@ohos.inputMethod](arkts-inputmethod.md)：面向普通前台应用，提供输入法的控制与管理能力（如显示/隐藏软键盘、切换输入法等），可通过程序化接口
 `switchInputMethod`切换输入法，适用于无需交互式选择界面的场景。
 <br>- [@ohos.inputMethodEngine](arkts-inputmethodengine.md)：面向输入法应用，提供创建软键盘窗口、插入/删除字符等输入法服务端能力。
 <br>- @ohos.inputMethodList（本模块）：面向系统应用和输入法应用，提供可视化的输入法切换列表弹窗控件，适用于需要交互式选择界面的场景。
 <br>
 <br> > **说明：**
 <br> >
 <br> > - 该组件从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
 <br> >
 <br> > - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
 <br> > 本模块包含以下关键组件和接口：
 <br>
 | Interface/Struct | 说明 |
 |---|---|
 | InputMethodListDialog | 输入法切换列表弹窗组件，使用`@CustomDialog`装饰器声明。展示输入法列表和可选的模式切换入口，是本模块的核心UI组件。
 需要传入`CustomDialogController`控制弹窗的打开与关闭，可选传入`PatternOptions`配置模式切换功能。 |
 | PatternOptions | 输入法模式选项配置接口，定义模式选项的资源数组、默认选中索引和模式切换回调。仅系统预置输入法支持传入此参数。 |
 | Pattern | 单个输入法模式的图标定义接口，包含默认图标和选中状态图标两个资源属性。 |
 <br>
 <br>使用`InputMethodListDialog`需要多个API组合配合：创建`CustomDialogController` -> 配置`PatternOptions`（可选） -> 在
 `CustomDialogController`的builder中构建`InputMethodListDialog` -> 通过`CustomDialogController.open()`打开弹窗。
 <br>
 <br>###### 属性
 <br>
 <br>不支持通用属性
 <br>
 <br>###### 子组件
 <br>
 <br>无
 <br>
 <br>###### 接口
 <br>
 <br>InputMethodListDialog({controller: CustomDialogController, patternOptions?: PatternOptions})
 <br>
 <br>**装饰器类型：**@CustomDialog
 <br>
 <br>**系统能力：** SystemCapability.MiscServices.InputMethodFramework
 <br>
 <br>**参数：**
 <br>
 | 名称 | 类型 | 必填 | 装饰器类型 | 说明 |
 | -------- | -------- | -------- | -------- | -------- |
 | controller | [CustomDialogController](../../apis-arkui/arkts-apis/arkts-arkui-customdialogcontroller-c.md) | 是 | - | 输入法切换列表弹窗控制器，用于控制弹窗的打开和关闭。
 <br>
 使用场景：当需要通过代码控制输入法切换列表弹窗的显示与隐藏时，必须提供此参数。
 <br>
 使用后效果：设置后，可通过调用controller的open()方法打开弹窗，
 close()方法关闭弹窗。
 <br>
 说明：需先创建CustomDialogController实例并关联InputMethodListDialog，再通过controller.open()打开弹窗。 |
 | patternOptions | [PatternOptions](arkts-ime-inputmethodlist-patternoptions-i.md) | 否 | - | 输入法模式选项配置。仅系统预置输入法支持。
 <br>
 使用场景：系统预置输入法需要支持模式切换功能（如单手模式、全屏模式等）时传入此参数，配置模式图标资源和切换回调。
 <br>
 默认值：不传入时，控件仅显示输入法列表，不提供模式切换功能。
 <br>
 说明：三方输入法应用不可使用此参数。 |
 <br>
 <br>######  事件
 <br>
 <br>不支持通用事件


## 导入模块

```TypeScript
import { InputMethodListDialog, PatternOptions, Pattern } from '@kit.IMEKit';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [InputMethodListDialog(输入法切换列表控件)](arkts-ime-inputmethodlist-inputmethodlistdialog-s.md) | 输入法切换列表弹窗控件。以弹窗形式展示当前系统中已安装的输入法应用列表，支持用户在输入法之间进行切换；对于默认输入法，还提供键盘模式（如单手模式、全屏模式等）的切换入口。 使用场景：当系统应用或输入法应用需要为用户提供可视化的输入法选择和切换功能时使用此控件。例如，在系统设置应用中允许用户选择不同输入法，或在输入法应用中允许用户切换到其他输入法或切换当前输入法的键盘模式。 使用后效果：调用此控件后，将弹出输入法切换列表弹窗。用户在弹窗中选择输入法后，系统将切换到指定的输入法；若用户选择了默认输入法的模式选项，系统将按指定模式显示键盘布局。 相似接口差异点及选取原则：与[inputMethod.switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md)接口相比，本控件提供了可视化的输入 法选择界面，适用于需要交互式选择界面的场景；switchInputMethod接口适用于程序化切换输入法的场景，无需用户手动选择。 使用限制：本组件仅系统应用和输入法应用可调用，patternOptions参数仅系统预置输入法支持。注意事项：  - 前提条件：需先创建[CustomDialogController](../../apis-arkui/arkts-apis/arkts-arkui-customdialogcontroller-c.md)实例并关联InputMethodListDialog，再通过controller的open()方法打开弹  窗。  - 本组件不支持通用属性和通用事件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Pattern(输入法切换列表控件)](arkts-ime-inputmethodlist-pattern-i.md) | 输入法模式选项的图标资源定义，用于配置键盘模式在弹窗中的视觉表现。仅当前输入法（即系统预置输入法）可使用。 |
| [PatternOptions(输入法切换列表控件)](arkts-ime-inputmethodlist-patternoptions-i.md) | 输入法模式选项配置，用于定义键盘模式的切换选项。 |
