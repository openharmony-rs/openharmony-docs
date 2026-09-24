# promptAction(弹窗)

```TypeScript
declare namespace promptAction
```

创建并显示即时反馈、对话框和操作菜单，适用于系统通知、交互确认、菜单选择等场景。

> **说明：** 

> - 本模块不支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)的文件声明处使用，即不能在UIAbility的生命周期中调用，需要在 创建组件实例后使用。
> 
> - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)说明。建议<!--Del-->在除[ServiceExtensionAbility](../../../application-models/serviceextensionability-sys.md)等无UI界面的场景外，均<!--DelEnd-->使用UIContext中的弹窗方法。

**起始版本：** 9

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [showToast](arkts-arkui-promptaction-showtoast-f.md) | Creates and displays a toast. |
| [openToast](arkts-arkui-promptaction-opentoast-f.md) | 显示即时反馈并通过Promise返回其id。 |
| [closeToast](arkts-arkui-promptaction-closetoast-f.md) | 关闭即时反馈。 |
| [showDialog](arkts-arkui-promptaction-showdialog-f.md#showdialog) | 创建并显示对话框，对话框响应结果使用callback异步回调返回。 |
| [showDialog](arkts-arkui-promptaction-showdialog-f.md#showdialog-1) | 创建并显示对话框，对话框通过Promise返回结果。 |
| [openCustomDialog](arkts-arkui-promptaction-opencustomdialog-f.md) | 打开自定义弹窗。通过Promise返回结果。 |
| [closeCustomDialog](arkts-arkui-promptaction-closecustomdialog-f.md) | 关闭自定义弹窗。 |
| [showActionMenu](arkts-arkui-promptaction-showactionmenu-f.md#showactionmenu) | 创建并显示操作菜单，菜单响应结果使用callback异步回调返回。 |
| [showActionMenu](arkts-arkui-promptaction-showactionmenu-f.md#showactionmenu-1) | 创建并显示操作菜单，菜单响应后通过Promise返回结果。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [CommonController](arkts-arkui-promptaction-commoncontroller-c.md) | 公共控制器，可以控制promptAction相关组件。 |
| [DialogController](arkts-arkui-promptaction-dialogcontroller-c.md) | 自定义弹窗控制器，继承自[CommonController](arkts-arkui-promptaction-commoncontroller-c.md)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md) | Toast的选项。 |
| [Button](arkts-arkui-promptaction-button-i.md) | 菜单中的菜单项按钮。 |
| [ShowDialogSuccessResponse](arkts-arkui-promptaction-showdialogsuccessresponse-i.md) | 对话框的响应结果。 |
| [ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md) | 对话框的选项。 |
| [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) | 弹窗的选项。 |
| [CustomDialogOptions](arkts-arkui-promptaction-customdialogoptions-i.md) | 自定义弹窗的内容，继承自[BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md)。 |
| [DialogOptions](arkts-arkui-promptaction-dialogoptions-i.md) | 自定义弹窗的内容，继承自[BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md)，用于配置自定义弹窗的显示参数和行为。 |
| [ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md) | 操作菜单的响应结果。 |
| [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | 操作菜单的选项。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i-sys.md) | 对话框的选项。 |
| [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i-sys.md) | 弹窗的选项。 |
| [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i-sys.md) | 操作菜单的选项。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [DialogOptionsCornerRadius](arkts-arkui-promptaction-dialogoptionscornerradius-t.md) | 表示弹窗背板的圆角半径允许的数据字段类型。 |
| [DialogOptionsBorderWidth](arkts-arkui-promptaction-dialogoptionsborderwidth-t.md) | 表示弹窗背板的边框宽度允许的数据字段类型。 |
| [DialogOptionsBorderColor](arkts-arkui-promptaction-dialogoptionsbordercolor-t.md) | 表示弹窗背板的边框颜色允许的数据字段类型。 |
| [DialogOptionsBorderStyle](arkts-arkui-promptaction-dialogoptionsborderstyle-t.md) | 表示弹窗背板的边框样式允许的数据字段类型。 |
| [DialogOptionsShadow](arkts-arkui-promptaction-dialogoptionsshadow-t.md) | 表示弹窗背板的阴影允许的数据字段类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ToastShowMode](arkts-arkui-promptaction-toastshowmode-e.md) | 设置Toast的显示模式，默认显示在应用内，支持显示在子窗。 |
| [CommonState](arkts-arkui-promptaction-commonstate-e.md) | 自定义弹窗的状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ToastShowMode](arkts-arkui-promptaction-toastshowmode-e-sys.md) | 设置Toast的显示模式，默认显示在应用内，支持显示在子窗。 |
<!--DelEnd-->

## 示例

从API version 20开始，该示例实现了在promptAction.DialogController中调用getState获取弹窗当前状态。

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent, promptAction } from '@kit.ArkUI';

@Component
struct CustomDialogExample {
  build() {
    Column() {
      Text('Hello')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .margin({ bottom: 36 })
      Button('点我关闭弹窗')
        .onClick(() => {
          if (this.getDialogController()) {
            this.getDialogController().close();
          }
        })
      Button('点我获取状态')
        .onClick(() => {
          if (this.getDialogController()) {
            let state: promptAction.CommonState = this.getDialogController().getState();
            switch (state) {
              case promptAction.CommonState.UNINITIALIZED: {
                console.info('The dialog state is uninitialized.');
                break;
              }
              case promptAction.CommonState.INITIALIZED: {
                console.info('The dialog state is initialized.');
                break;
              }
              case promptAction.CommonState.APPEARING: {
                console.info('The dialog state is appearing.');
                break;
              }
              case promptAction.CommonState.APPEARED: {
                console.info('The dialog state is appeared.');
                break;
              }
              case promptAction.CommonState.DISAPPEARING: {
                console.info('The dialog state is disappearing.');
                break;
              }
              case promptAction.CommonState.DISAPPEARED: {
                console.info('The dialog state is disappeared.');
                break;
              }
              default: {
                console.info('The dialog state is unknown.');
                break;
              }
            }
          }
        })

    }.backgroundColor('#FFF0F0F0')
  }
}

@Builder
function buildText() {
   CustomDialogExample()
}

@Entry
@Component
struct Index {

  private dialogController: promptAction.DialogController = new promptAction.DialogController()

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText),
            );

            promptAction.openCustomDialogWithController(contentNode, this.dialogController, {

              transition: TransitionEffect.OPACITY.animation({
                duration: 3000
              })
            }).then(() => {
              console.info('succeeded')
            }).catch((error: BusinessError) => {
              console.error(`OpenCustomDialogWithController args error code is ${error.code}, message is ${error.message}`);
            })
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```
