# 弹出框迁移指南（@ohos.arkui.dialog）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

本文档帮助开发者了解[@ohos.arkui.dialog (弹出框)](../reference/apis-arkui/js-apis-dialog.md)新接口与老接口（[CustomDialogController](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontroller)、[showAlertDialog](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showalertdialog)、[showActionSheet](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showactionsheet)、[promptAction.showDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showdialog)、[promptAction.showActionMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showactionmenu)、[promptAction.openCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog)、[promptAction.openCustomDialogWithController](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18)、[promptAction.presentCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#presentcustomdialog18)）的能力差异，并按弹出框类别提供从老接口到新接口的迁移映射。

> 从API版本26.0.1开始，[@ohos.arkui.dialog (弹出框)](../reference/apis-arkui/js-apis-dialog.md)提供统一的Dialog类型声明能力。版本状态以 [`@ohos.arkui.dialog.d.ts`](../reference/apis-arkui/js-apis-dialog.md) 实际 `@since` 标注为准。

## 接口说明

[@ohos.arkui.dialog (弹出框)](../reference/apis-arkui/js-apis-dialog.md)新接口在完全兼容老接口能力的基础上，新增支持返回错误码的能力。

| 接口名 | 说明 |
|--------|------|
| [DialogTextStyleOptions](../reference/apis-arkui/js-apis-dialog.md#dialogtextstyleoptions) | 文本样式选项，控制弹出框消息内容的断行方式，作为 `DialogMessage` 的基类。 |
| [DialogButton](../reference/apis-arkui/js-apis-dialog.md#dialogbutton) | 弹出框按钮配置，用于 `DialogStyleOptions.buttons` 数组元素。 |
| [DialogSheet](../reference/apis-arkui/js-apis-dialog.md#dialogsheet) | Action-sheet 风格的菜单项，用于 `DialogStyleOptions.sheets` 数组元素。 |
| [DialogBaseOptions](../reference/apis-arkui/js-apis-dialog.md#dialogbaseoptions) | 所有弹出框样式的基类选项，承载通用样式和行为配置，被 `DialogStyleOptions` 和 `DialogCustomOptions` 继承。 |
| [DialogMessage](../reference/apis-arkui/js-apis-dialog.md#dialogmessage) | 消息内容与文本样式，继承自 `DialogTextStyleOptions`，用于 `DialogStyleOptions.message`。 |
| [DialogStyleOptions](../reference/apis-arkui/js-apis-dialog.md#dialogstyleoptions) | 固定样式弹出框选项，继承自 `DialogBaseOptions`，用于 `DialogPresenter.present(options)`。 |
| [DialogCustomOptions](../reference/apis-arkui/js-apis-dialog.md#dialogcustomoptions) | 自定义样式弹出框选项，继承自 `DialogBaseOptions`，用于 `DialogPresenter.present(content, options)`。 |
| [DialogBaseController](../reference/apis-arkui/js-apis-dialog.md#dialogbasecontroller) | 弹出框控制器类，通过 `DialogBaseOptions.controller` 传入，提供 `close()` 和 `getState()` 方法。 |
| [DialogResult](../reference/apis-arkui/js-apis-dialog.md#dialogresult) | 弹出框操作结果，`present()` 的 Promise 返回值，包含 `dialogId`。 |
| [DialogDismissal](../reference/apis-arkui/js-apis-dialog.md#dialogdismissal) | 弹出框关闭信息，`onWillDismiss` 回调参数，包含 `dismiss` 和 `reason`。 |
| [DialogBaseAlignment](../reference/apis-arkui/js-apis-dialog.md#dialogbasealignment) | 弹出框对齐方式枚举（TOP/CENTER/BOTTOM/DEFAULT 等 10 种）。 |
| [DialogButtonOrientation](../reference/apis-arkui/js-apis-dialog.md#dialogbuttonorientation) | 按钮排列方向枚举（AUTO/HORIZONTAL/VERTICAL）。 |
| [DialogState](../reference/apis-arkui/js-apis-dialog.md#dialogstate) | 弹出框状态枚举（UNINITIALIZED~DISAPPEARED），通过 `DialogBaseController.getState()` 查询。 |

## 弹出框新老接口差异

新老接口在“属性”和“使用方式”两个维度存在一定差异，详见下方对应小节：

- **属性差异**：按弹出框类型逐一定义老接口与新接口的属性映射，以及高级动画参数差异。每类弹出框提供属性对照表（含编程模型、内容构建、对齐、偏移、蒙层、边框、阴影、动画回调、键盘避让、悬浮模式、层级模式、系统材质等属性）和“迁移前/迁移后”完整代码示例。
- **使用方式差异**：聚焦老接口无法实现、仅新接口支持的能力，包括弹出后动态修改弹出框位置（对齐、偏移、蒙层颜色等）而无需关闭重开，以及自定义弹出框场景支持系统材质，并配有代码示例对比说明。

### 属性差异

1. CustomDialog（自定义弹出框）

老接口使用CustomDialogController的open和close接口打开和关闭弹出框，新接口使用DialogPresenter的present和dismiss接口打开和关闭弹出框，具体示例见表格下方。

| 属性 | 老接口（@CustomDialog + CustomDialogController） | 新接口（DialogPresenter.present + DialogCustomOptions） |
|------|------|------|
| 编程模型 | `@CustomDialog` 装饰器声明自定义组件 + `CustomDialogController` 实例化控制 | `UIContext.getDialogPresenter()` 获取 Presenter，`present(content, options)` 弹出 |
| 内容构建 | `@CustomDialog` 装饰器包裹 `@Component` | `CustomBuilder` / `CustomBuilderWithId` / `ComponentContent<Object>` 作为 `present` 第一个参数 |
| 样式控制 | `customStyle: boolean`（CustomDialogControllerOptions） | `DialogCustomOptions.customStyle: boolean` |
| 打开 | `controller.open()` | `presenter.present(content, options): Promise<DialogResult>` |
| 关闭 | `controller.close()` | `DialogBaseController.close()` 或 `presenter.dismiss(target)` |
| 状态查询 | `controller.getState(): PromptActionCommonState` | `DialogBaseController.getState(): DialogState` |
| 对齐 | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
| 偏移 | `offset: { dx, dy }` | `offset: Offset` |
| 自动取消 | `autoCancel: boolean` | `autoCancel: boolean` |
| 蒙层颜色 | `maskColor: ResourceColor` | `maskColor: ResourceColor` |
| 蒙层区域 | `maskRect: Rectangle` | `maskRect: Rectangle` |
| 模态 | `isModal: boolean` | `isModal: boolean` |
| 子窗口 | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
| 焦点 | `focusable: boolean`（可配置，默认 true） | `focusable: boolean`（可配置，默认 true） |
| 打开动画回调 | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
| 取消回调 | `cancel: () => void` + `onWillDismiss: Callback<DismissDialogAction>` | `onWillDismiss: Callback<DialogDismissal>` |
| 背景模糊 | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
| 边框 | `cornerRadius` / `borderWidth` / `borderColor` / `borderStyle` | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle`（`cornerRadius` 更名为 `borderRadius`，其余同名） |
| 阴影 | `shadow: ShadowOptions \| ShadowStyle` | `shadow: ShadowOptions \| ShadowStyle` |
| 内容区动画 | `openAnimation` + `closeAnimation`（`AnimateParam`） | `dialogTransition: TransitionEffect` |
| 蒙层动画 | 无 | `maskTransition: TransitionEffect` |
| 键盘避让 | `keyboardAvoidMode` + `keyboardAvoidDistance` | `keyboardAvoidMode` + `keyboardAvoidDistance` |
| 悬浮模式 | `enableHoverMode` + `hoverModeArea` | `enableHoverMode` + `hoverModeArea` |
| 层级模式 | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
| 系统材质 | `systemMaterial: SystemUiMaterial` | `systemMaterial: SystemUiMaterial` |
<!--Del-->
| 系统接口属性 | `distortionMode`（@systemapi）、`edgeLightMode`（@systemapi）——见 [系统接口](../reference/apis-arkui/ts-methods-custom-dialog-box-sys.md) | `distortionMode`（@systemapi）、`edgeLightMode`（@systemapi）——见 [系统接口](../reference/apis-arkui/js-apis-dialog-sys.md) |
<!--DelEnd-->

**迁移前示例（老接口）：**

<!-- @[custom_dialog_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/CustomDialogBeforeMigrate.ets) -->

``` TypeScript
@CustomDialog
struct CustomDialogExample {
  controller?: CustomDialogController
  build() {
    Column() {
      Text('自定义弹窗内容')
      Button('关闭').onClick(() => { this.controller?.close() })
    }
  }
}

@Entry
@Component
export struct CustomDialogBeforeMigrate {
  dialogController: CustomDialogController = new CustomDialogController({
    builder: CustomDialogExample(),
    alignment: DialogAlignment.Center,
    autoCancel: true,
    maskColor: 0x33000000
  })
  build() {
    NavDestination() {
      Column() {
        Button('打开弹窗').onClick(() => {
          this.dialogController.open()
        })
      }
      .width('100%')
      .height('100%')
      .justifyContent(FlexAlign.Center)
    }
  }
}
```

 ![迁移前示例图](figures/CustomDialogBeforeMigrate.png)

**迁移后示例（新接口）：**

<!-- @[custom_dialog_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/CustomDialogAfterMigrate.ets) -->

```typescript
import { DialogPresenter, DialogBaseAlignment, DialogResult, ComponentContent } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// 定义参数类，用于向自定义弹出框内容传递数据
class Params {
  text: string = '';

  constructor(text: string) {
    this.text = text;
  }
}

// 自定义弹出框内容的构建器函数
@Builder
function buildText(params: Params) {
  Column({ space: 20 }) {
    Text(params.text)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
    // 关闭弹出框按钮，通过ComponentContent引用关闭弹出框
    Button('关闭弹窗')
      .onClick(() => {
        dialogPresenter?.dismiss(contentNode)
          .then(() => {
            console.info('dismiss success');
          })
          .catch((error: BusinessError) => {
            console.error(`dismiss error code is ${error.code}, message is ${error.message}`);
          })
      })
  }
}

let contentNode: ComponentContent<Object> | null = null;
// 全局变量，保存DialogPresenter实例
let dialogPresenter: DialogPresenter | null = null;

@Entry
@Component
struct CustomDialogMigrationPage {
  @State result: string = '';

  aboutToAppear(): void {
    // 获取DialogPresenter实例
    dialogPresenter = this.getUIContext().getDialogPresenter();
    // 创建ComponentContent，绑定自定义构建器函数和参数
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params("自定义弹窗内容"));
  }

  build() {
    Row() {
      Column() {
        Text('CustomDialog 迁移示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('老接口：@CustomDialog + CustomDialogController')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showOldCustomDialog();
          })

        Button('新接口：DialogPresenter.present（自定义弹窗）')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showNewCustomDialog();
          })

        if (this.result) {
          Text(this.result)
            .fontSize(14)
            .margin({ top: 10 })
        }
      }
      .width('100%')
    }
    .height('100%')
  }

  private showOldCustomDialog(): void {
    this.result = '老接口示例请参考 DialogProject 工程';
  }

  private showNewCustomDialog(): void {
    dialogPresenter?.present(contentNode, {
      alignment: DialogBaseAlignment.CENTER,
      autoCancel: true,
      maskColor: 0x33000000
    }).then((result: DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```

![迁移后示例图](figures/CustomDialogAfterMigrate.png)

2. AlertDialog（告警弹出框）

老接口使用UIContext.showAlertDialog弹出告警框，新接口使用DialogPresenter.present弹出告警框，具体示例见表格下方。

| 属性 | 老接口（AlertDialog.show） | 新接口（DialogPresenter.present + DialogStyleOptions） |
|------|------|------|
| 编程模型 | `AlertDialog.show(options)` 命令式调用 | `presenter.present(options): Promise<DialogResult>` |
| 标题 | `title: ResourceStr` | `title: ResourceStr` |
| 副标题 | `subtitle: ResourceStr` | `subtitle: ResourceStr` |
| 消息内容 | `message: ResourceStr` | `message: DialogMessage`（content + wordBreak） |
| 文本样式 | `textStyle: TextStyle` | `message.wordBreak: WordBreak`（通过 DialogMessage 设置） |
| 按钮 | `confirm`（单个）/ `primaryButton` + `secondaryButton`（两个）/ `buttons: Array<AlertDialogButtonOptions>`（多个） | `buttons: Array<DialogButton>`（含 value/fontColor/backgroundColor/enabled/primary/style/action） |
| 按钮排列 | `buttonDirection: DialogButtonDirection` | `buttonDirection: DialogButtonOrientation` |
| 操作菜单 | 无 | `sheets: Array<DialogSheet>`（action-sheet 风格） |
| 网格数 | `gridCount: number` | `gridCount: number` |
| 确认回调 | `confirm` / `primaryButton.action` / `secondaryButton.action` / `buttons[].action` | `DialogButton.action`（通过 Promise 结果） |
| 取消回调 | `cancel: VoidCallback` + `onWillDismiss: Callback<DismissDialogAction>` | `onWillDismiss: Callback<DialogDismissal>` |
| 对齐 | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
| 偏移 | `offset: Offset` | `offset: Offset` |
| 自动取消 | `autoCancel: boolean` | `autoCancel: boolean` |
| 蒙层区域 | `maskRect: Rectangle` | `maskRect: Rectangle` |
| 模态 | `isModal: boolean` | `isModal: boolean` |
| 子窗口 | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
| 背景色 | `backgroundColor` | `backgroundColor` |
| 背景模糊 | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
| 边框 | `cornerRadius` / `borderWidth` / `borderColor` / `borderStyle` | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle`（`cornerRadius` 更名为 `borderRadius`） |
| 阴影 | `shadow: ShadowOptions \| ShadowStyle` | `shadow: ShadowOptions \| ShadowStyle` |
| 尺寸 | `width` / `height` | `width` / `height` |
| 过渡动画 | `transition: TransitionEffect` | `dialogTransition: TransitionEffect` |
| 蒙层动画 | 无 | `maskTransition: TransitionEffect` |
| 打开动画回调 | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
| 悬浮模式 | `enableHoverMode` + `hoverModeArea` | `enableHoverMode` + `hoverModeArea` |
| 层级模式 | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
| 系统材质 | `systemMaterial: SystemUiMaterial` | `systemMaterial: SystemUiMaterial` |

**迁移前示例（老接口）：**

<!-- @[alert_dialog_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/AlertDialogBeforeMigrate.ets) -->

```typescript
@Entry
@Component
struct Index {
  @State result: string = '';

  build() {
    Column() {
      Button('打开 AlertDialog')
        .onClick(() => {
          this.getUIContext().showAlertDialog({
            title: '提示',
            message: '确认删除？',
            autoCancel: true,
            buttons: [
              { value: '取消', action: () => { this.result = '取消'; } },
              { value: '确认', action: () => { this.result = '确认'; } }
            ],
            cancel: () => { this.result = 'cancel'; }
          });
        })

      if (this.result) {
        Text(this.result)
          .fontSize(14)
          .margin({ top: 10 })
      }
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
 ```

![迁移前示例图](figures/AlertDialogBeforeMigrate.png)

**迁移后示例（新接口）：**

<!-- @[alert_dialog_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/AlertDialogAfterMigrate.ets) -->

```typescript
import { DialogBaseAlignment, DialogDismissal, DialogPresenter, DialogResult } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct AlertDialogMigrationPage {
  private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
  @State result: string = '';

  build() {
    Row() {
      Column() {
        Text('AlertDialog 迁移示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('老接口：showAlertDialog')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.result = '老接口示例请参考 ts-methods-alert-dialog-box.md';
          })

        Button('新接口：DialogPresenter.present（固定样式弹窗）')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showNewAlertDialog();
          })

        if (this.result) {
          Text(this.result)
            .fontSize(14)
            .margin({ top: 10 })
        }
      }
      .width('100%')
    }
    .height('100%')
  }

  private showNewAlertDialog(): void {
    this.presenter.present({
      title: '提示',
      message: { content: '确认删除？' },
      buttons: [
        {
          value: '取消', action: () => {
          this.result = '用户点击取消';
        }
        },
        {
          value: '确认', action: () => {
          this.result = '用户点击确认';
        }
        }
      ],
      alignment: DialogBaseAlignment.BOTTOM,
      onWillDismiss: (dismissal: DialogDismissal) => {
        this.result = 'onWillDismiss, reason: ' + dismissal.reason;
        dismissal.dismiss();
      }
    }).then((result: DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```

![迁移后示例图](figures/AlertDialogAfterMigrate.png)

3. ActionSheet（列表选择弹出框）

老接口使用UIContext.showActionSheet弹出列表选择弹出框，新接口使用DialogPresenter.present弹出列表选择弹出框，具体示例见表格下方。

| 属性 | 老接口（ActionSheet.show） | 新接口（DialogPresenter.present + DialogStyleOptions） |
|------|------|------|
| 编程模型 | `ActionSheet.show(options)` 命令式调用 | `presenter.present(options): Promise<DialogResult>` |
| 标题 | `title: string \| Resource` | `title: ResourceStr` |
| 副标题 | `subtitle: ResourceStr` | `subtitle: ResourceStr` |
| 消息内容 | `message: string \| Resource` | `message: DialogMessage`（content + wordBreak） |
| 按钮 | `confirm: ActionSheetButtonOptions`（单个确认按钮） | `buttons: Array<DialogButton>` |
| 按钮排列 | 无 | `buttonDirection: DialogButtonOrientation` |
| 操作菜单 | `sheets: Array<SheetInfo>`（title/icon/action） | `sheets: Array<DialogSheet>`（title/icon/action） |
| 网格数 | 无 | `gridCount: number` |
| 确认回调 | `confirm.action: VoidCallback` | `DialogButton.action` |
| 取消回调 | `cancel: VoidCallback` + `onWillDismiss: Callback<DismissDialogAction>` | `onWillDismiss: Callback<DialogDismissal>` |
| 对齐 | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
| 偏移 | `offset: ActionSheetOffset`（含 dx/dy） | `offset: Offset`（含 dx/dy） |
| 自动取消 | `autoCancel: boolean` | `autoCancel: boolean` |
| 蒙层区域 | `maskRect: Rectangle` | `maskRect: Rectangle` |
| 模态 | `isModal: boolean` | `isModal: boolean` |
| 子窗口 | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
| 背景色 | `backgroundColor` | `backgroundColor` |
| 背景模糊 | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
| 边框 | `cornerRadius` / `borderWidth` / `borderColor` / `borderStyle` | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle`（`cornerRadius` 更名为 `borderRadius`） |
| 阴影 | `shadow: ShadowOptions \| ShadowStyle` | `shadow: ShadowOptions \| ShadowStyle` |
| 尺寸 | `width` / `height` | `width` / `height` |
| 过渡动画 | `transition: TransitionEffect` | `dialogTransition: TransitionEffect` |
| 蒙层动画 | 无 | `maskTransition: TransitionEffect` |
| 打开动画回调 | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
| 悬浮模式 | `enableHoverMode` + `hoverModeArea` | `enableHoverMode` + `hoverModeArea` |
| 层级模式 | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
| 系统材质 | `systemMaterial: SystemUiMaterial` | `systemMaterial: SystemUiMaterial` |

**迁移前示例（老接口）：**

<!-- @[action_sheet_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ActionSheetBeforeMigrate.ets) -->

```typescript
@Entry
@Component
struct Index {
  @State result: string = '';

  build() {
    Column() {
      Button('打开 ActionSheet')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: '选择操作',
            message: '请选择一个操作',
            autoCancel: true,
            sheets: [
              { title: '复制', action: () => { this.result = '复制'; } },
              { title: '删除', action: () => { this.result = '删除'; } }
            ],
            cancel: () => { this.result = '取消'; }
          });
        })

      if (this.result) {
        Text(this.result)
          .fontSize(14)
          .margin({ top: 10 })
      }
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

![迁移前示例图](figures/ActionSheetBeforeMigrate.png)

**迁移后示例（新接口）：**

<!-- @[action_sheet_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ActionSheetAfterMigrate.ets) -->

```typescript
import { DialogDismissal, DialogPresenter, DialogResult } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ActionSheetMigrationPage {
  private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
  @State result: string = '';

  build() {
    Row() {
      Column() {
        Text('ActionSheet 迁移示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('老接口：showActionSheet')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.result = '老接口示例请参考 ts-methods-action-sheet.md';
          })

        Button('新接口：DialogPresenter.present（列表选择弹窗）')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showNewActionSheet();
          })

        if (this.result) {
          Text(this.result)
            .fontSize(14)
            .margin({ top: 10 })
        }
      }
      .width('100%')
    }
    .height('100%')
  }

  private showNewActionSheet(): void {
    this.presenter.present({
      title: '选择操作',
      message: { content: '请选择一个操作' },
      autoCancel: true,
      sheets: [
        { title: '复制', action: () => { this.result = '复制'; } },
        { title: '删除', action: () => { this.result = '删除'; } }
      ],
      onWillDismiss: (dismissal: DialogDismissal) => {
        this.result = '取消';
        dismissal.dismiss();
      }
    }).then((result: DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```

![迁移后示例图](figures/ActionSheetAfterMigrate.png)

4. promptAction.showDialog（对话框）

老接口使用promptAction.showDialog弹出对话框，新接口使用DialogPresenter.present弹出对话框，具体示例见表格下方。

| 属性 | 老接口（promptAction.showDialog） | 新接口（DialogPresenter.present + DialogStyleOptions） |
|------|------|------|
| 编程模型 | `promptAction.showDialog(options): Promise<ShowDialogSuccessResponse>` | `presenter.present(options): Promise<DialogResult>` |
| 标题 | `title: string \| Resource` | `title: ResourceStr` |
| 副标题 | 无 | `subtitle: ResourceStr`（新增） |
| 消息内容 | `message: string \| Resource` | `message: DialogMessage`（content + wordBreak） |
| 按钮 | `buttons: Array<Button>`（仅 text + color + primary） | `buttons: Array<DialogButton>`（含 value/fontColor/backgroundColor/enabled/primary/style/action） |
| 按钮排列 | 无 | `buttonDirection: DialogButtonOrientation` |
| 操作菜单 | 无 | `sheets: Array<DialogSheet>`（新增） |
| 网格数 | 无 | `gridCount: number` |
| 确认回调 | 通过 `ShowDialogSuccessResponse.index` 获取按钮索引 | `DialogButton.action` + Promise 结果 |
| 取消回调 | 无 | `onWillDismiss: Callback<DialogDismissal>` |
| 对齐 | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
| 偏移 | `offset: Offset` | `offset: Offset` |
| 自动取消 | 无 | `autoCancel: boolean` |
| 蒙层颜色 | 无 | `maskColor: ResourceColor` |
| 蒙层区域 | `maskRect: Rectangle` | `maskRect: Rectangle` |
| 模态 | `isModal: boolean` | `isModal: boolean` |
| 子窗口 | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
| 背景色 | `backgroundColor` | `backgroundColor` |
| 背景模糊 | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
| 边框 | 无 | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle` |
| 阴影 | `shadow: ShadowOptions \| ShadowStyle` | `shadow: ShadowOptions \| ShadowStyle` |
| 尺寸 | 无 | `width` / `height` |
| 过渡动画 | 无 | `dialogTransition: TransitionEffect` |
| 蒙层动画 | 无 | `maskTransition: TransitionEffect` |
| 打开动画回调 | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
| 悬浮模式 | `enableHoverMode` + `hoverModeArea` | `enableHoverMode` + `hoverModeArea` |
| 层级模式 | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
| 系统材质 | `systemMaterial: SystemUiMaterial` | `systemMaterial: SystemUiMaterial` |

**迁移前示例（老接口）：**

<!-- @[show_dialog_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ShowDialogBeforeMigrate.ets) -->

```typescript
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State result: string = '';

  build() {
    Column() {
      Button('打开 showDialog')
        .onClick(() => {
          this.getUIContext().getPromptAction().showDialog({
            title: '提示',
            message: '确认删除？',
            buttons: [
              { text: '取消', color: '#666666' },
              { text: '确认', color: '#0000FF' }
            ]
          }).then((data) => {
            this.result = 'click button index: ' + data.index;
          }).catch((error: BusinessError) => {
            this.result = `showDialog error: ${error.code}`;
          });
        })

      if (this.result) {
        Text(this.result)
          .fontSize(14)
          .margin({ top: 10 })
      }
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

![迁移前示例图](figures/ShowDialogBeforeMigrate.png)

**迁移后示例（新接口）：**

<!-- @[show_dialog_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ShowDialogAfterMigrate.ets) -->

```typescript
import { DialogPresenter, DialogResult } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ShowDialogMigrationPage {
  private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
  @State result: string = '';

  build() {
    Row() {
      Column() {
        Text('showDialog 迁移示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('老接口：promptAction.showDialog')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.result = '老接口示例请参考 js-apis-promptAction.md';
          })

        Button('新接口：DialogPresenter.present（对话框）')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showNewDialog();
          })

        if (this.result) {
          Text(this.result)
            .fontSize(14)
            .margin({ top: 10 })
        }
      }
      .width('100%')
    }
    .height('100%')
  }

  private showNewDialog(): void {
    this.presenter.present({
      title: '提示',
      message: { content: '确认删除？' },
      buttons: [
        { value: '取消', action: () => { this.result = '取消'; } },
        { value: '确认', action: () => { this.result = '确认'; } }
      ]
    }).then((result: DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```

![迁移后示例图](figures/ShowDialogAfterMigrate.png)

5. promptAction.showActionMenu（操作菜单）

老接口使用promptAction.showActionMenu弹出操作菜单，新接口使用DialogPresenter.present弹出操作菜单，具体示例见表格下方。

| 属性 | 老接口（promptAction.showActionMenu） | 新接口（DialogPresenter.present + DialogStyleOptions） |
|------|------|------|
| 编程模型 | `promptAction.showActionMenu(options): Promise<ActionMenuSuccessResponse>` | `presenter.present(options): Promise<DialogResult>` |
| 标题 | `title: string \| Resource` | `title: ResourceStr` |
| 副标题 | 无 | `subtitle: ResourceStr`（新增） |
| 消息内容 | 无 | `message: DialogMessage`（新增） |
| 按钮 | `buttons: [Button, ...]`（1-6 个，仅 text + color + primary） | `buttons: Array<DialogButton>`（无数量限制，含 value/fontColor/backgroundColor/enabled/primary/style/action） |
| 按钮排列 | 无 | `buttonDirection: DialogButtonOrientation` |
| 操作菜单 | 无 | `sheets: Array<DialogSheet>`（新增） |
| 网格数 | 无 | `gridCount: number` |
| 确认回调 | 通过 `ActionMenuSuccessResponse.index` 获取按钮索引 | `DialogButton.action` + Promise 结果 |
| 取消回调 | 无 | `onWillDismiss: Callback<DialogDismissal>` |
| 对齐 | 无 | `alignment: DialogBaseAlignment` |
| 偏移 | 无 | `offset: Offset` |
| 自动取消 | 无 | `autoCancel: boolean` |
| 蒙层颜色 | 无 | `maskColor: ResourceColor` |
| 蒙层区域 | 无 | `maskRect: Rectangle` |
| 模态 | `isModal: boolean` | `isModal: boolean` |
| 子窗口 | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
| 背景色 | 无 | `backgroundColor` |
| 背景模糊 | 无 | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
| 边框 | 无 | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle` |
| 阴影 | 无 | `shadow: ShadowOptions \| ShadowStyle` |
| 尺寸 | 无 | `width` / `height` |
| 过渡动画 | 无 | `dialogTransition: TransitionEffect` |
| 蒙层动画 | 无 | `maskTransition: TransitionEffect` |
| 打开动画回调 | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
| 悬浮模式 | 无 | `enableHoverMode` + `hoverModeArea` |
| 层级模式 | `levelMode` + `levelUniqueId` + `immersiveMode` | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
| 系统材质 | `systemMaterial: SystemUiMaterial` | `systemMaterial: SystemUiMaterial` |

**迁移前示例（老接口）：**

<!-- @[action_menu_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ActionMenuBeforeMigrate.ets) -->

```typescript
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State result: string = '';

  build() {
    Column() {
      Button('打开 showActionMenu')
        .onClick(() => {
          this.getUIContext().getPromptAction().showActionMenu({
            title: '选择操作',
            buttons: [
              { text: '保存', color: '#0000FF' },
              { text: '分享', color: '#0000FF' },
              { text: '删除', color: '#FF0000' }
            ]
          }).then((data) => {
            this.result = 'click button index: ' + data.index;
          }).catch((error: BusinessError) => {
            this.result = `showActionMenu error: ${error.code}`;
          });
        })

      if (this.result) {
        Text(this.result)
          .fontSize(14)
          .margin({ top: 10 })
      }
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

![迁移前示例图](figures/ActionMenuBeforeMigrate.png)

**迁移后示例（新接口）：**

<!-- @[action_menu_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/ActionMenuAfterMigrate.ets) -->

```typescript
import { DialogPresenter, DialogResult } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ShowActionMenuMigrationPage {
  private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
  @State result: string = '';

  build() {
    Row() {
      Column() {
        Text('showActionMenu 迁移示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('老接口：promptAction.showActionMenu')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.result = '老接口示例请参考 js-apis-promptAction.md';
          })

        Button('新接口：DialogPresenter.present（操作菜单）')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showNewActionMenu();
          })

        if (this.result) {
          Text(this.result)
            .fontSize(14)
            .margin({ top: 10 })
        }
      }
      .width('100%')
    }
    .height('100%')
  }

  private showNewActionMenu(): void {
    this.presenter.present({
      title: '选择操作',
      buttons: [
        { value: '保存', action: () => { this.result = '保存'; } },
        { value: '分享', action: () => { this.result = '分享'; } },
        { value: '删除', action: () => { this.result = '删除'; } }
      ]
    }).then((result: DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```

![迁移后示例图](figures/ActionMenuAfterMigrate.png)

6. promptAction.presentCustomDialog（自定义弹出框）

老接口使用promptAction.presentCustomDialog弹出自定义弹出框，新接口使用DialogPresenter.present弹出自定义弹出框，具体示例见表格下方。

| 属性 | 老接口（promptAction.presentCustomDialog） | 新接口（DialogPresenter.present + DialogCustomOptions） |
|------|------|------|
| 编程模型 | `promptAction.presentCustomDialog(builder, controller?, options?): Promise<number>` | `presenter.present(content, options?: DialogCustomOptions): Promise<DialogResult>` |
| 内容构建 | `CustomBuilder` / `CustomBuilderWithId` | `CustomBuilder` / `CustomBuilderWithId` / `ComponentContent<Object>` |
| 控制器 | `promptAction.DialogController` | `DialogBaseController` |
| 选项类型 | `DialogOptions`（继承 `BaseDialogOptions`） | `DialogCustomOptions`（继承 `DialogBaseOptions`） |
| 样式控制 | 无 `customStyle` 属性（内容样式完全由 builder 决定） | `customStyle: boolean` |
| 对齐 | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
| 偏移 | `offset: Offset` | `offset: Offset` |
| 自动取消 | `autoCancel: boolean` | `autoCancel: boolean` |
| 蒙层颜色 | `maskColor: ResourceColor` | `maskColor: ResourceColor` |
| 蒙层区域 | `maskRect: Rectangle` | `maskRect: Rectangle` |
| 模态 | `isModal: boolean` | `isModal: boolean` |
| 子窗口 | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
| 背景色 | `backgroundColor`（`DialogOptions`） | `backgroundColor` |
| 背景模糊 | `backgroundBlurStyle`（`DialogOptions`） + `backgroundBlurStyleOptions` + `backgroundEffect` | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
| 边框 | `cornerRadius` / `borderWidth` / `borderColor` / `borderStyle`（`DialogOptions`） | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle`（`cornerRadius` 更名为 `borderRadius`） |
| 阴影 | `shadow`（`DialogOptions`） | `shadow: ShadowOptions \| ShadowStyle` |
| 尺寸 | `width` / `height`（`DialogOptions`） | `width` / `height` |
| 过渡动画 | `transition: TransitionEffect` / `dialogTransition` | `dialogTransition: TransitionEffect` |
| 蒙层动画 | `maskTransition: TransitionEffect` | `maskTransition: TransitionEffect` |
| 焦点 | `focusable: boolean` | `focusable: boolean` |
| 打开动画回调 | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
| 取消回调 | `onWillDismiss: Callback<DismissDialogAction>` | `onWillDismiss: Callback<DialogDismissal>` |
| 键盘避让 | `keyboardAvoidMode` + `keyboardAvoidDistance`  | `keyboardAvoidMode` + `keyboardAvoidDistance` |
| 悬浮模式 | `enableHoverMode`  + `hoverModeArea`  | `enableHoverMode` + `hoverModeArea` |
| 层级模式 | `levelMode`  + `levelUniqueId`  + `immersiveMode`  + `levelOrder`  | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
| 系统材质 | `systemMaterial: SystemUiMaterial`  | `systemMaterial: SystemUiMaterial` |

**迁移前示例（老接口）：**

<!-- @[present_custom_dialog_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/PresentCustomDialogBeforeMigrate.ets) -->

```typescript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private dialogController: promptAction.DialogController = new promptAction.DialogController();
  @State result: string = '';

  @Builder customDialogComponent() {
    Column() {
      Text('自定义弹窗内容')
        .fontSize(16)
        .margin({ bottom: 10 })
      Button('关闭弹窗')
        .onClick(() => {
          this.dialogController.close();
        })
    }
    .padding(20)
  }

  build() {
    Column() {
      Button('打开 presentCustomDialog')
        .onClick(() => {
          this.getUIContext().getPromptAction().presentCustomDialog(() => {
            this.customDialogComponent()
          }, this.dialogController, { autoCancel: true })
            .then((dialogId: number) => {
              this.result = 'present success, dialogId: ' + dialogId;
            })
            .catch((error: BusinessError) => {
              this.result = `present error: ${error.code}`;
            });
        })

      if (this.result) {
        Text(this.result)
          .fontSize(14)
          .margin({ top: 10 })
      }
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

![迁移前示例图](figures/PresentCustomDialogBeforeMigrate.png)

**迁移后示例（新接口）：**

<!-- @[present_custom_dialog_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/PresentCustomDialogAfterMigrate.ets) -->

```typescript
import { DialogBaseController, DialogPresenter, DialogResult } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct PresentCustomDialogMigrationPage {
  private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
  private controller: DialogBaseController = new DialogBaseController();
  @State result: string = '';

  build() {
    Row() {
      Column() {
        Text('presentCustomDialog 迁移示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('老接口：promptAction.presentCustomDialog')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.result = '老接口示例请参考 arkts-apis-uicontext-promptaction.md';
          })

        Button('新接口：DialogPresenter.present（自定义弹窗）')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showNewCustomDialog();
          })

        if (this.result) {
          Text(this.result)
            .fontSize(14)
            .margin({ top: 10 })
        }
      }
      .width('100%')
    }
    .height('100%')
  }

  @Builder
  CustomComponentContent() {
    Column() {
      Text('自定义弹窗内容')
        .fontSize(16)
        .margin({ bottom: 10 })
      Button('关闭弹窗')
        .onClick(() => {
          this.controller.close();
        })
    }
    .padding(20)
  }

  private showNewCustomDialog(): void {
    this.presenter.present(() => {
      this.CustomComponentContent()
    }, {
      controller: this.controller,
      autoCancel: true
    }).then((result: DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```

![迁移后示例图](figures/PresentCustomDialogAfterMigrate.png)

7. promptAction.openCustomDialogWithController（带控制器的自定义弹出框）

老接口使用promptAction.openCustomDialogWithController弹出带控制器的自定义弹出框，新接口使用DialogPresenter.present弹出带控制器的自定义弹出框，具体示例见表格下方。

| 属性 | 老接口（promptAction.openCustomDialogWithController） | 新接口（DialogPresenter.present + DialogCustomOptions） |
|------|------|------|
| 编程模型 | `promptAction.openCustomDialogWithController(content, controller, options?): Promise<void>` | `presenter.present(content, options?: DialogCustomOptions): Promise<DialogResult>` |
| 内容构建 | `ComponentContent<Object>` | `CustomBuilder` / `CustomBuilderWithId` / `ComponentContent<Object>` |
| 控制器 | `promptAction.DialogController`  | `DialogBaseController` |
| 选项类型 | `BaseDialogOptions` | `DialogCustomOptions`（继承 `DialogBaseOptions`） |
| 样式控制 | 无 `customStyle` 属性（内容样式完全由 ComponentContent 决定） | `customStyle: boolean` |
| 对齐 | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
| 偏移 | `offset: Offset` | `offset: Offset` |
| 自动取消 | `autoCancel: boolean`  | `autoCancel: boolean` |
| 蒙层颜色 | `maskColor: ResourceColor`  | `maskColor: ResourceColor` |
| 蒙层区域 | `maskRect: Rectangle` | `maskRect: Rectangle` |
| 模态 | `isModal: boolean` | `isModal: boolean` |
| 子窗口 | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
| 背景色 | 无（`BaseDialogOptions` 不含 `backgroundColor`） | `backgroundColor` |
| 背景模糊 | `backgroundBlurStyleOptions`  + `backgroundEffect`  | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
| 边框 | 无（`BaseDialogOptions` 不含边框属性） | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle` |
| 阴影 | 无（`BaseDialogOptions` 不含 `shadow`） | `shadow: ShadowOptions \| ShadowStyle` |
| 尺寸 | 无（`BaseDialogOptions` 不含 `width` / `height`） | `width` / `height` |
| 过渡动画 | `transition: TransitionEffect`  / `dialogTransition`  | `dialogTransition: TransitionEffect` |
| 蒙层动画 | `maskTransition: TransitionEffect`  | `maskTransition: TransitionEffect` |
| 焦点 | `focusable: boolean`  | `focusable: boolean` |
| 打开动画回调 | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear`  | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
| 取消回调 | `onWillDismiss: Callback<DismissDialogAction>`  | `onWillDismiss: Callback<DialogDismissal>` |
| 键盘避让 | `keyboardAvoidMode`  + `keyboardAvoidDistance`  | `keyboardAvoidMode` + `keyboardAvoidDistance` |
| 悬浮模式 | `enableHoverMode`  + `hoverModeArea`  | `enableHoverMode` + `hoverModeArea` |
| 层级模式 | `levelMode`  + `levelUniqueId`  + `immersiveMode`  + `levelOrder`  | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
| 系统材质 | `systemMaterial: SystemUiMaterial`  | `systemMaterial: SystemUiMaterial` |

**迁移前示例（老接口）：**

<!-- @[open_custom_dialog_with_controller_before_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/OpenCustomDialogWithControllerBeforeMigrate.ets) -->

```typescript
import { ComponentContent, promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = '';

  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(16)
      .margin({ bottom: 10 })
    Button('关闭弹窗')
      .onClick(() => {
      })
  }
  .padding(20)
}

@Entry
@Component
struct Index {
  private dialogController: promptAction.DialogController = new promptAction.DialogController();
  @State result: string = '';

  build() {
    Column() {
      Button('打开 openCustomDialogWithController')
        .onClick(() => {
          let contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText),
            new Params('自定义弹窗内容'));
          this.getUIContext().getPromptAction().openCustomDialogWithController(contentNode,
            this.dialogController, {
              autoCancel: true,
              alignment: DialogAlignment.Center
            }).then(() => {
              this.result = 'opened';
            }).catch((error: BusinessError) => {
              this.result = `open error: ${error.code}`;
            });
        })

      if (this.result) {
        Text(this.result)
          .fontSize(14)
          .margin({ top: 10 })
      }
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

![迁移前示例图](figures/OpenCustomDialogWithControllerBeforeMigrate.png)

**迁移后示例（新接口）：**

<!-- @[open_custom_dialog_with_controller_after_migrate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/OpenCustomDialogWithControllerAfterMigrate.ets) -->

```typescript
import { DialogBaseAlignment, DialogBaseController, DialogPresenter, DialogResult } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct OpenCustomDialogWithControllerMigrationPage {
  private presenter: DialogPresenter = this.getUIContext().getDialogPresenter();
  private controller: DialogBaseController = new DialogBaseController();
  @State result: string = '';

  build() {
    Row() {
      Column() {
        Text('openCustomDialogWithController 迁移示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('老接口：promptAction.openCustomDialogWithController')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.result = '老接口示例请参考 arkts-apis-uicontext-promptaction.md';
          })

        Button('新接口：DialogPresenter.present（自定义弹窗）')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showNewCustomDialog();
          })

        if (this.result) {
          Text(this.result)
            .fontSize(14)
            .margin({ top: 10 })
        }
      }
      .width('100%')
    }
    .height('100%')
  }

  @Builder
  CustomContent() {
    Column() {
      Text('自定义弹窗内容')
        .fontSize(16)
        .margin({ bottom: 10 })
      Button('关闭弹窗')
        .onClick(() => {
          this.controller.close();
        })
    }
    .padding(20)
  }

  private showNewCustomDialog(): void {
    this.presenter.present(() => {
      this.CustomContent()
    }, {
      controller: this.controller,
      autoCancel: true,
      alignment: DialogBaseAlignment.CENTER
    }).then((result: DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```

![迁移后示例图](figures/OpenCustomDialogWithControllerAfterMigrate.png)

8. 高级动画参数差异

老接口使用 `customStyle: boolean` 控制是否使用自定义样式，`openAnimation` / `closeAnimation`（`AnimateParam`）控制打开和关闭动画。新接口使用 `dialogTransition: TransitionEffect` 控制内容区动画，`maskTransition: TransitionEffect` 控制蒙层动画。两者参数类型不同，**不存在等效映射**，迁移时需按新接口 `TransitionEffect` 重写动画参数。

### 使用方式差异

新接口可以支持一些新的使用方式而老接口不能使用，比如老接口不支持弹出后动态修改弹出框位置，新接口可以；老接口在自定义场景不能使用系统材质，新接口可以。

老接口示例：

<!-- @[custom_dialog_old_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/CustomDialogOldInterface.ets) -->

```ts
import { ComponentContent } from '@kit.ArkUI';
import { AbilityConstant, Configuration, EnvironmentCallback, ConfigurationConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

class Params {
  text: string = "";
  colorMode: resourceManager.ColorMode = resourceManager.ColorMode.LIGHT

  constructor(text: string, colorMode: resourceManager.ColorMode) {
    this.text = text
    this.colorMode = colorMode
  }
}

@Builder
function BuilderDialog(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
  }.backgroundColor(params.colorMode == resourceManager.ColorMode.LIGHT ? "#D5D5D5" : "#004AAF")
}

@Entry
@Component
struct Index {
  @State message: string = "hello";
  contentNode: ComponentContent<Params> | null = null;
  callbackId: number | undefined = 0;

  aboutToAppear(): void {
    let environmentCallback: EnvironmentCallback = {
      onMemoryLevel: (level: AbilityConstant.MemoryLevel): void => {
      },
      onConfigurationUpdated: (config: Configuration): void => {
        console.info(`onConfigurationUpdated ${config}`);
        this.getUIContext().getHostContext()?.getApplicationContext().resourceManager.getConfiguration((err,
          config) => {
          // 调用ComponentContent的update更新colorMode信息
          this.contentNode?.update(new Params(this.message, config.colorMode))
          setTimeout(() => {
            // 调用ComponentContent的updateConfiguration，触发节点的全量更新
            this.contentNode?.updateConfiguration()
          })
        })
      }
    }
    // 注册监听系统环境变化监听器
    this.callbackId =
      this.getUIContext().getHostContext()?.getApplicationContext().on('environment', environmentCallback)
    // 设置应用深浅色跟随系统
    this.getUIContext()
      .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET)
  }

  aboutToDisappear() {
    // 解注册监听系统环境变化的回调
    this.getUIContext().getHostContext()?.getApplicationContext().off('environment', this.callbackId)
    this.contentNode?.dispose()
  }

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            if (this.contentNode == null && uiContext.getHostContext() != undefined) {
              this.contentNode = new ComponentContent(uiContext, wrapBuilder(BuilderDialog), new Params(this.message,
                uiContext.getHostContext()!!.getApplicationContext().resourceManager.getConfigurationSync().colorMode))
            }
            if (this.contentNode == null) {
              return
            }
            promptAction.closeCustomDialog(this.contentNode)
            // 先关闭已存在的弹窗，再重新打开
            promptAction.openCustomDialog(this.contentNode).then(() => {
              console.info("succeeded")
            }).catch((error: BusinessError) => {
              console.error(`OpenCustomDialog args error code is ${error.code}, message is ${error.message}`);
            })
          })
      }
      .width('100%')
      .height('100%')
      .justifyContent(FlexAlign.Center)
    }
    .height('100%')
  }
}
```

![老接口示例图](figures/CustomDialogOldInterface.gif)

新接口示例：

<!-- @[custom_dialog_new_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/CustomDialogNewInterface.ets) -->

```
import {
  ComponentContent,
  DialogPresenter,
  DialogResult,
  DialogBaseAlignment,
  LevelMode,
  ImmersiveMode,
  uiMaterial
} from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// 定义参数类，用于向自定义弹出框内容传递数据
class Params {
  text: string = '';

  constructor(text: string) {
    this.text = text;
  }
}

// 自定义弹出框内容的构建器函数
@Builder
function buildText(params: Params) {
  Column({ space: 20 }) {
    Text(params.text)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
    // 更新弹出框样式按钮，动态修改蒙层颜色、对齐方式和偏移量
    Button('Update dialog')
      .onClick(() => {
        dialogPresenter?.update(contentNode, {
          offset: { dx: 0, dy: 30 }
        })
          .then(() => {
            console.info('update success');
          })
          .catch((error: BusinessError) => {
            console.error(`update error code is ${error.code}, message is ${error.message}`);
          })
      })
    // 关闭弹出框按钮，通过ComponentContent引用关闭弹出框
    Button('Dismiss dialog')
      .onClick(() => {
        dialogPresenter?.dismiss(contentNode)
          .then(() => {
            console.info('dismiss success');
          })
          .catch((error: BusinessError) => {
            console.error(`dismiss error code is ${error.code}, message is ${error.message}`);
          })
      })
  }
}

// 全局变量，保存DialogPresenter实例
let dialogPresenter: DialogPresenter | null = null;
// 全局变量，保存自定义弹出框的ComponentContent实例
let contentNode: ComponentContent<Object> | null = null;

@Entry
@Component
struct Index {
  @State message: string = 'custom dialog';

  aboutToAppear(): void {
    // 获取DialogPresenter实例
    dialogPresenter = this.getUIContext().getDialogPresenter();
    // 创建ComponentContent，绑定自定义构建器函数和参数
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    Column({ space: 10 }) {
      Button('Present custom dialog')
        .id("PresentDialog")
        .onClick(() => {
          // 弹出自定义样式弹出框，传入ComponentContent和配置选项
          dialogPresenter?.present(contentNode, {
            systemMaterial: new uiMaterial.ImmersiveMaterial({ style: uiMaterial.ImmersiveStyle.REGULAR })
          })
          // 弹出成功，获取弹出框ID
            .then((result: DialogResult) => {
              console.info('present success, dialogId: ' + result.dialogId);
            })
            .catch((error: BusinessError) => {
              console.error(`present error code is ${error.code}, message is ${error.message}`);
            })
        })
    }.width('100%').height('100%').justifyContent(FlexAlign.Center)
  }
}
```

![新接口示例图](figures/CustomDialogNewInterface.gif)

## 典型场景迁移指导

### 全局自定义弹出框迁移

**迁移前示例（老接口）：**

[完整示例](arkts-uicontext-custom-dialog.md#完整示例)

**迁移后示例（新接口）：**

<!-- @[dialog_presenter_class_new](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/common/DialogPresenterClassNew.ts) -->

```typescript
// DialogPresenterClassNew.ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent, dialog, DialogResult, UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

export class DialogPresenterClassNew {
  static ctx: UIContext;
  static contentNode: ComponentContent<Object>;
  static options: dialog.DialogBaseOptions;

  static setContext(context: UIContext) {
    DialogPresenterClassNew.ctx = context;
  }

  static setContentNode(node: ComponentContent<Object>) {
    DialogPresenterClassNew.contentNode = node;
  }

  static setOptions(options: dialog.DialogBaseOptions) {
    DialogPresenterClassNew.options = options;
  }

  // 打开弹窗
  static openDialog() {
    if (DialogPresenterClassNew.contentNode !== null) {
      // [Start dialog_presenter_class_open_custom_dialog]
      DialogPresenterClassNew.ctx.getDialogPresenter()?.present(this.contentNode, DialogPresenterClassNew.options)
        .then((result: DialogResult) => {
          hilog.info(DOMAIN, 'testTag', 'testTag', 'OpenCustomDialog complete.');
        }).catch((error: BusinessError) => {
        let message = (error as BusinessError).message;
        let code = (error as BusinessError).code;
        hilog.error(DOMAIN, 'testTag', 'testTag', `OpenCustomDialog args error code is ${code}, message is ${message}`);
      })
      // [End dialog_presenter_class_open_custom_dialog]
    }
  }

  // 关闭弹窗
  static closeDialog() {
    if (DialogPresenterClassNew.contentNode !== null) {
      DialogPresenterClassNew.ctx.getDialogPresenter()?.dismiss(this.contentNode)
        .then(() => {
          hilog.info(DOMAIN, 'testTag', 'testTag', 'CloseCustomDialog complete.');
        })
        .catch((error: BusinessError) => {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          hilog.error(DOMAIN, 'testTag', 'testTag', `CloseCustomDialog args error code is ${code}, message is ${message}`);
        })
    }
  }

  // 更新弹窗
  static updateDialog(options: dialog.DialogBaseOptions) {
    if (DialogPresenterClassNew.contentNode !== null) {
      // [Start dialog_presenter_class_update_options]
      DialogPresenterClassNew.ctx.getDialogPresenter()?.update(this.contentNode, options)
        .then(() => {
          hilog.info(DOMAIN, 'testTag', 'testTag', 'UpdateCustomDialog complete.');
        })
        .catch((error: BusinessError) => {
          let message = (error as BusinessError).message;
          let code = (error as BusinessError).code;
          hilog.error(DOMAIN, 'testTag', 'testTag', `UpdateCustomDialog args error code is ${code}, message is ${message}`);
        })
      // [End dialog_presenter_class_update_options]
    }
  }
}
```

<!-- @[open_dialog_and_update](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/opencustomdialog/OpenDialogAndUpdate.ets) -->

```typescript
// Index.ets
import { ComponentContent, DialogBaseAlignment } from '@kit.ArkUI';
import { DialogPresenterClassNew } from '../../common/DialogPresenterClassNew';

class Params {
  public text: string = '';

  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
    Button('Close')
      .onClick(() => {
        DialogPresenterClassNew.closeDialog();
      })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
export struct OpenDialogAndUpdate {
  @State message: string = 'hello';
  private ctx: UIContext = this.getUIContext();
  // [Start open_dialog_and_update_create_componentContent]
  private contentNode: ComponentContent<Object> =
    new ComponentContent(this.ctx, wrapBuilder(buildText), new Params(this.message));
  // [End open_dialog_and_update_create_componentContent]
  aboutToAppear(): void {
    DialogPresenterClassNew.setContext(this.ctx);
    DialogPresenterClassNew.setContentNode(this.contentNode);
    DialogPresenterClassNew.setOptions({ alignment: DialogBaseAlignment.TOP, offset: { dx: 0, dy: 50 } });
  }

  build() {
    NavDestination() {
      Row() {
        Column() {
          Button('open dialog and update options')
            .margin({ top: 50 })
            .onClick(() => {
              DialogPresenterClassNew.openDialog();

              setTimeout(() => {
                DialogPresenterClassNew.updateDialog({
                  alignment: DialogBaseAlignment.BOTTOM,
                  offset: { dx: 0, dy: -50 }
                });
              }, 1500)
            })
          Button('open dialog and update content')
            .margin({ top: 50 })
            .onClick(() => {
              DialogPresenterClassNew.openDialog();

              setTimeout(() => {
                // [Start open_dialog_and_update_content]
                this.contentNode.update(new Params('update'));
                // [End open_dialog_and_update_content]
              }, 1500)
            })
        }
        .width('100%')
        .height('100%')
      }
      .height('100%')
    }
  }
}
```

![全局自定义弹出框](figures/GlobalDialogBasePresenter.gif)


### 页面级弹出框迁移

**迁移前示例（老接口）：**

[完整示例](arkts-embedded-dialog.md#完整示例)

**迁移后示例（新接口）：**

下述示例为基于Router路由模式下的页面级弹出框。

<!-- @[page_level_dialog](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/customdialog/pageleveldialogbox/PageLevelDialogBox.ets) -->

```typescript
// PageLevelDialogBox.ets
import { LevelMode, ImmersiveMode, DialogResult } from '@kit.ArkUI';

let customDialogId: number = 0;

@Builder
function customDialogBuilder(uiContext: UIContext) {
  Column() {
    Text('Custom dialog Message').fontSize(20).height(100)
    Row() {
      Button('Next').onClick(() => {
        // 在弹窗内部进行路由跳转。
        uiContext.getRouter().pushUrl({ url: 'pages/customdialog/pageleveldialogbox/Next' });
      })
      Blank().width(50)
      Button('Close').onClick(() => {
        uiContext.getDialogPresenter()?.dismiss(customDialogId);
      })
    }
  }.padding(20)
}

@Entry
@Component
export struct PageLevelDialogBox {
  @State message: string = 'Hello World';

  @Builder
  customDialogComponent() {
    customDialogBuilder(this.getUIContext());
  }

  build() {
    NavDestination() {
      Row() {
        Column() {
          // [Start test_text]
          // [Start dialog_embedded]
          Text(this.message).id('test_text')
            .fontSize(50)
            .fontWeight(FontWeight.Bold)
            .onClick(() => {
              const node: FrameNode | null = this.getUIContext().getFrameNodeById('test_text') || null;
              // [Start open_custom_dialog]
              this.getUIContext().getDialogPresenter()?.present(() => this.customDialogComponent(), {
                levelMode: LevelMode.EMBEDDED, // 启用页面级弹出框
                // [StartExclude open_custom_dialog]
                levelUniqueId: node?.getUniqueId(), // 设置页面级弹出框所在页面的任意节点ID
                // [StartExclude test_text]
                immersiveMode: ImmersiveMode.EXTEND, // 设置页面级弹出框蒙层的显示模式
                // [EndExclude test_text]
                // [EndExclude open_custom_dialog]
              })
              // [End open_custom_dialog]
                .then((result: DialogResult) => {
                  customDialogId = result.dialogId;
                });
            })
          // [End dialog_embedded]
          // [End test_text]
        }
        .width('100%')
      }
      .height('100%')
    }
  }
}
```

<!-- @[next](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/customdialog/pageleveldialogbox/Next.ets) -->

```typescript
// Next.ets
// Next.ets
@Entry
@Component
struct Next {
  @State message: string = 'Back';

  build() {
    Row() {
      Column() {
        Button(this.message)
          .fontSize(20)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            this.getUIContext().getRouter().back();
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

![页面级弹出框1](figures/RoutePageLevelDialogBasePresenter.gif)

下述示例为基于Navigation导航模式下的页面级弹出框。使用本示例前需要参考[Navigation使用NavDestination作为导航页](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#示例16navigation使用navdestination作为导航页)文档完成Index首页和router_map.json的创建与配置。并使用下述示例代码中的PageLevelDialogInNavigation和PageLevelDialogInNavigationTestTwo组件替换Navigation参考文档中的PageHome和PageOne组件。

<!-- @[page_level_dialog](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/customdialog/pageleveldialogbox/PageLevelDialogInNavigation.ets) -->

```typescript
// PageLevelDialogInNavigation.ets
import { LevelMode, ImmersiveMode, DialogResult } from '@kit.ArkUI';

let customDialogId: number = 0;

@Builder
function customDialogBuilder(uiContext: UIContext, stack: NavPathStack | undefined) {
  Column() {
    Text('Custom dialog Message').fontSize(20).height(100)
    Row() {
      Button('Next').onClick(() => {
        // 在弹窗内部进行路由跳转。
        if (stack) {
          stack.pushPath({ name: 'Custom_ROUTE_PREFIX/PageLevelDialogInNavigationPageTwo'})
        }
      })
      Blank().width(50)
      Button('Close').onClick(() => {
        uiContext.getDialogPresenter()?.dismiss(customDialogId);
      })
    }
  }.padding(20)
}

@Component
export struct PageLevelDialogInNavigation {
  private stack: NavPathStack | undefined = undefined;
  private uiContext: UIContext = this.getUIContext();
  @State message: string = 'Hello World';

  @Builder
  customDialogComponent() {
    customDialogBuilder(this.uiContext, this.stack);
  }

  build() {
    NavDestination() {
      Stack({alignContent: Alignment.Center}) {
        Column() {
          Text(this.message).id('test_text')
            .fontSize(50)
            .fontWeight(FontWeight.Bold)
            .onClick(() => {
              const node: FrameNode | null = this.getUIContext().getFrameNodeById('test_text') || null;
              this.uiContext.getDialogPresenter()?.present(() => this.customDialogComponent(), {
                levelMode: LevelMode.EMBEDDED, // 启用页面级弹出框
                levelUniqueId: node?.getUniqueId(), // 设置页面级弹出框所在页面的任意节点ID
                immersiveMode: ImmersiveMode.EXTEND, // 设置页面级弹出框蒙层的显示模式
              }).then((result: DialogResult) => {
                customDialogId = result.dialogId;
              })
            })
        }
        .width('100%')
      }.width('100%').height('100%')
    }
    .width('100%').height('100%')
    .title('PageOne')
    .onReady((ctx: NavDestinationContext) => {
      this.stack = ctx.pathStack;
    })
  }
}

@Component
export struct PageLevelDialogInNavigationTestTwo {
  @State message: string = 'Back';
  private stack: NavPathStack | undefined = undefined;

  build() {
    NavDestination() {
      Stack({alignContent: Alignment.Center}) {
        Column() {
          Button(this.message)
            .fontSize(20)
            .fontWeight(FontWeight.Bold)
            .onClick(() => {
              if (this.stack) {
                this.stack.pop()
              }
            })
        }
        .width('100%')
      }.width('100%').height('100%')
    }
    .width('100%').height('100%')
    .title('PageTwo')
    .onReady((ctx: NavDestinationContext) => {
      this.stack = ctx.pathStack;
    })
  }
}
```

![页面级弹出框2](figures/NavigationPageLevelDialogBasePresenter.gif)