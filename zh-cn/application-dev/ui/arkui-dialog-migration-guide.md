# 弹窗迁移指南（@ohos.arkui.dialog）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

本文档帮助开发者了解 `@ohos.arkui.dialog` 新接口与老接口（CustomDialog、AlertDialog、TextPickerDialog、TimePickerDialog、DatePickerDialog）的能力差异，并按弹窗类别提供从老接口到新接口的迁移映射和示例。

> **适用版本：** 从 API 版本 26.1.0（OpenHarmony 7.1-Release）开始，`@ohos.arkui.dialog` 提供 Unified Dialog API。版本状态以 [`@ohos.arkui.dialog.d.ts`](../reference/apis-arkui/js-apis-dialog.md) 实际 `@since` 标注为准。

### 快速导航

如需直接迁移，可按弹窗类别跳转至“适配指导”对应小节：

- [CustomDialog 迁移](#customdialog--dialogpresenterpresent自定义弹窗)
- [AlertDialog 迁移](#alertdialog--dialogpresenterpresent固定样式弹窗)
- [TextPickerDialog 迁移](#textpickerdialog--dialogpresenterpresent自定义弹窗内嵌-textpicker)
- [TimePickerDialog 迁移](#timepickerdialog--dialogpresenterpresent自定义弹窗内嵌-timepicker)
- [DatePickerDialog 迁移](#datepickerdialog--dialogpresenterpresent自定义弹窗内嵌-datepicker)

## 能力介绍

`@ohos.arkui.dialog.d.ts` 包含 13 个声明单元，均标注 `@since 26.1.0 dynamic`、`@stagemodelonly`、`@crossplatform`、`@atomicservice`。各单元按"选项类型 / 控制器与结果 / 枚举"逻辑分组，类型继承关系如下：

```
DialogBaseOptions（基类）
  ├── DialogStyleOptions（固定样式）
  └── DialogCustomOptions（自定义样式）

DialogTextStyleOptions
  └── DialogMessage（extends DialogTextStyleOptions）
```

### 13 声明单元

#### 1. DialogTextStyleOptions

- **定位：** 文本样式选项，控制弹窗消息内容的断行方式。
- **要点：** 作为 `DialogMessage` 的基类。
- **关键属性：** `wordBreak?: WordBreak`
- **参考文档：** [js-apis-dialog.md#dialogtextstyleoptions](../reference/apis-arkui/js-apis-dialog.md#dialogtextstyleoptions)

#### 2. DialogButton

- **定位：** 弹窗按钮配置。
- **要点：** 用于 `DialogStyleOptions.buttons` 数组元素。
- **关键属性：** `value: ResourceStr`、`fontColor?`、`backgroundColor?`、`enabled?`（默认 true）、`primary?`、`style?`（默认 DEFAULT）、`action: VoidCallback`
- **参考文档：** [js-apis-dialog.md#dialogbutton](../reference/apis-arkui/js-apis-dialog.md#dialogbutton)

#### 3. DialogSheet

- **定位：** Action-sheet 风格的菜单项。
- **要点：** 用于 `DialogStyleOptions.sheets` 数组元素，与 `buttons` 共存时按钮显示在列表下方。
- **关键属性：** `title: ResourceStr`、`icon?: ResourceStr`、`action: VoidCallback`
- **参考文档：** [js-apis-dialog.md#dialogsheet](../reference/apis-arkui/js-apis-dialog.md#dialogsheet)

#### 4. DialogBaseOptions

- **定位：** 所有弹窗样式的基类选项，承载通用样式和行为配置。
- **要点：** 被 `DialogStyleOptions` 和 `DialogCustomOptions` 继承；也是 `DialogPresenter.update()` 的参数类型。
- **关键属性：** `controller?`、`width?`、`height?`、`backgroundColor?`、`backgroundBlurStyle?`、`backgroundBlurStyleOptions?`、`backgroundEffect?`、`borderRadius?`、`borderWidth?`、`borderColor?`、`borderStyle?`、`shadow?`、`alignment?`、`offset?`、`maskRect?`、`maskColor?`、`isModal?`、`showInSubWindow?`、`displayModeInSubWindow?`、`autoCancel?`、`focusable?`、`dialogTransition?`、`maskTransition?`、`keyboardAvoidMode?`、`keyboardAvoidDistance?`、`onWillAppear?`、`onDidAppear?`、`onWillDisappear?`、`onDidDisappear?`、`onWillDismiss?`、`enableHoverMode?`、`hoverModeArea?`、`levelMode?`、`levelUniqueId?`、`immersiveMode?`、`levelOrder?`、`systemMaterial?`
- **系统接口属性：** `distortionMode?`（@systemapi）、`edgeLightMode?`（@systemapi）——标注"系统接口"，详见 [js-apis-dialog-sys.md](../reference/apis-arkui/js-apis-dialog-sys.md)
- **参考文档：** [js-apis-dialog.md#dialogbaseoptions](../reference/apis-arkui/js-apis-dialog.md#dialogbaseoptions)

#### 5. DialogMessage

- **定位：** 消息内容 + 文本样式，extends `DialogTextStyleOptions`。
- **要点：** 用于 `DialogStyleOptions.message`。
- **关键属性：** `content: ResourceStr`
- **参考文档：** [js-apis-dialog.md#dialogmessage](../reference/apis-arkui/js-apis-dialog.md#dialogmessage)

#### 6. DialogStyleOptions

- **定位：** 固定样式弹窗选项，extends `DialogBaseOptions`。
- **要点：** 用于 `DialogPresenter.present(options)` 的参数类型。
- **关键属性：** `title?`、`subtitle?`、`message?: DialogMessage`、`buttons?: Array<DialogButton>`、`buttonDirection?`（默认 AUTO）、`sheets?: Array<DialogSheet>`、`gridCount?`
- **参考文档：** [js-apis-dialog.md#dialogstyleoptions](../reference/apis-arkui/js-apis-dialog.md#dialogstyleoptions)

#### 7. DialogCustomOptions

- **定位：** 自定义样式弹窗选项，extends `DialogBaseOptions`。
- **要点：** 用于 `DialogPresenter.present(content, options)` 的 `options` 参数类型；弹窗内容由 `present` 第一个参数提供，不在此选项内。
- **关键属性：** `customStyle?: boolean`（默认 false）
- **参考文档：** [js-apis-dialog.md#dialogcustomoptions](../reference/apis-arkui/js-apis-dialog.md#dialogcustomoptions)

#### 8. DialogBaseController

- **定位：** 弹窗控制器类，用于主动控制弹窗。
- **要点：** 通过 `DialogBaseOptions.controller` 传入；`present` 返回的 `Promise<DialogResult>` 也可用于后续 `dismiss`。
- **关键方法：** `constructor()`、`close(): void`、`getState(): DialogState`
- **参考文档：** [js-apis-dialog.md#dialogbasecontroller](../reference/apis-arkui/js-apis-dialog.md#dialogbasecontroller)

<!-- @[dialog_migration_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/DialogStatePage.ets) -->

```typescript
import { dialog } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct DialogStatePage {
  private presenter: dialog.DialogPresenter = this.getUIContext().getDialogPresenter();
  private controller: dialog.DialogBaseController = new dialog.DialogBaseController();
  @State stateText: string = '';

  build() {
    Row() {
      Column() {
        Text('DialogBaseController 状态查询示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('弹出弹窗（通过 controller 控制）')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showDialogWithController();
          })

        Button('查询状态 getState()')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.queryState();
          })

        Button('关闭 close()')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.controller.close();
            this.stateText = '已调用 close()';
          })

        if (this.stateText) {
          Text(this.stateText)
            .fontSize(14)
            .margin({ top: 10 })
        }
      }
      .width('100%')
    }
    .height('100%')
  }

  private showDialogWithController(): void {
    this.presenter.present(() => {
      Column() {
        Text('通过 DialogBaseController 控制的弹窗')
          .fontSize(16)
          .margin({ bottom: 10 })
        Button('内部关闭')
          .onClick(() => {
            this.controller.close();
          })
      }
      .padding(20)
    }, {
      controller: this.controller,
      alignment: dialog.DialogBaseAlignment.CENTER,
      autoCancel: true
    }).then((result: dialog.DialogResult) => {
      this.stateText = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.stateText = `present error: ${error.code}`;
    });
  }

  private queryState(): void {
    const state = this.controller.getState();
    const stateNames = ['UNINITIALIZED', 'INITIALIZED', 'APPEARING', 'APPEARED', 'DISAPPEARING', 'DISAPPEARED'];
    this.stateText = '当前状态: ' + stateNames[state];
  }
}
```

#### 9. DialogBaseAlignment

- **定位：** 弹窗对齐方式枚举。
- **枚举值：** `TOP = 0`、`CENTER = 1`、`BOTTOM = 2`、`DEFAULT = 3`、`TOP_START = 4`、`TOP_END = 5`、`CENTER_START = 6`、`CENTER_END = 7`、`BOTTOM_START = 8`、`BOTTOM_END = 9`
- **参考文档：** [js-apis-dialog.md#dialogbasealignment](../reference/apis-arkui/js-apis-dialog.md#dialogbasealignment)

#### 10. DialogButtonOrientation

- **定位：** 按钮排列方向枚举。
- **枚举值：** `AUTO = 0`、`HORIZONTAL = 1`、`VERTICAL = 2`
- **参考文档：** [js-apis-dialog.md#dialogbuttonorientation](../reference/apis-arkui/js-apis-dialog.md#dialogbuttonorientation)

#### 11. DialogState

- **定位：** 弹窗状态枚举，通过 `DialogBaseController.getState()` 查询。
- **枚举值：** `UNINITIALIZED = 0`、`INITIALIZED = 1`、`APPEARING = 2`、`APPEARED = 3`、`DISAPPEARING = 4`、`DISAPPEARED = 5`
- **参考文档：** [js-apis-dialog.md#dialogstate](../reference/apis-arkui/js-apis-dialog.md#dialogstate)

#### 12. DialogResult

- **定位：** 弹窗操作结果，`present()` 的 Promise 返回值。
- **关键属性：** `dialogId: int`
- **参考文档：** [js-apis-dialog.md#dialogresult](../reference/apis-arkui/js-apis-dialog.md#dialogresult)

#### 13. DialogDismissal

- **定位：** 弹窗关闭信息，`onWillDismiss` 回调参数。
- **关键属性：** `dismiss: VoidCallback`（调用以确认关闭）、`reason: DismissReason`
- **参考文档：** [js-apis-dialog.md#dialogdismissal](../reference/apis-arkui/js-apis-dialog.md#dialogdismissal)

## 新老接口能力差异

### 差异总览

弹窗接口经历三代演进：第一代（API 9+，命令式静态方法如 `AlertDialog.show()`）、第二代（API 8+，`@CustomDialog` 装饰器 + `CustomDialogController`）、第三代（API 26.1.0+，Unified Dialog API，`DialogPresenter.present()` + Promise）。新老接口在以下维度存在差异，按"属性差异"和"使用差异"两类分述（详见下方对应小节）：

| 差异类型 | 对比维度 | 老接口（第一/二代） | 新接口（第三代 `@ohos.arkui.dialog`） |
|---------|---------|-------------------|----------------------------|
| 属性差异 | 高级动画 | `customStyle` + `animationStyle`/`transition` | `dialogTransition` + `maskTransition`（TransitionEffect） |
| 属性差异 | update 更新面 | `CustomDialogController.update()` 支持多属性 | `DialogPresenter.update()` 仅支持 `alignment`/`offset`/`autoCancel`/`maskColor` |
| 使用差异 | 编程模型 | 静态方法 / 装饰器 + Controller | `UIContext.getDialogPresenter()` + Promise |
| 使用差异 | 取消回调 | `onCancel` / `onWillDismiss` | `onWillDismiss: Callback<DialogDismissal>` |
| 使用差异 | FA 模型适用面 | 部分老接口支持 FA 模型 | 仅 Stage 模型（`@stagemodelonly`） |

### 属性差异

#### 1. CustomDialog（自定义弹窗）

| 属性 | 老接口（@CustomDialog + CustomDialogController） | 新接口（DialogPresenter.present + DialogCustomOptions） |
|------|------|------|
| 编程模型 | `@CustomDialog` 装饰器声明自定义组件 + `CustomDialogController` 实例化控制 | `UIContext.getDialogPresenter()` 获取 Presenter，`present(content, options)` 弹出 |
| 内容构建 | `@CustomDialog` 装饰器包裹 `@Component` | `CustomBuilder` / `CustomBuilderWithId` / `ComponentContent<Object>` 作为 `present` 第一个参数 |
| 样式控制 | `customStyle: boolean`（CustomDialogControllerOptions） | `DialogCustomOptions.customStyle: boolean` |
| 打开 | `controller.open()` | `presenter.present(content, options): Promise<DialogResult>` |
| 关闭 | `controller.close()` | `DialogBaseController.close()` 或 `presenter.dismiss(target)` |
| 状态查询 | 无直接等价 | `DialogBaseController.getState(): DialogState` |
| 对齐 | `alignment: DialogAlignment` | `alignment: DialogBaseAlignment` |
| 偏移 | `offset: { dx, dy }` | `offset: Offset` |
| 自动取消 | `autoCancel: boolean` | `autoCancel: boolean` |
| 蒙层颜色 | `maskColor: ResourceColor` | `maskColor: ResourceColor` |
| 蒙层区域 | `maskRect: Rectangle` | `maskRect: Rectangle` |
| 模态 | `isModal: boolean` | `isModal: boolean` |
| 子窗口 | `showInSubWindow: boolean` | `showInSubWindow: boolean` |
| 焦点 | `focusable: boolean`（不可配置，默认 true） | `focusable: boolean`（可配置，默认 true） |
| 打开动画回调 | `onDidAppear` 等 | `onWillAppear` / `onDidAppear` / `onWillDisappear` / `onDidDisappear` |
| 取消回调 | `onCancel` | `onWillDismiss: Callback<DialogDismissal>`（见 G2） |
| 背景模糊 | `backgroundColorBlurStyle`（仅模糊） | `backgroundBlurStyle` + `backgroundBlurStyleOptions` + `backgroundEffect` |
| 边框 | 无 | `borderRadius` / `borderWidth` / `borderColor` / `borderStyle` |
| 阴影 | 无 | `shadow: ShadowOptions | ShadowStyle` |
| 内容区动画 | `animationStyle` + `transition` | `dialogTransition: TransitionEffect`（见 G3） |
| 蒙层动画 | 无 | `maskTransition: TransitionEffect` |
| 键盘避让 | 无直接等价 | `keyboardAvoidMode` + `keyboardAvoidDistance` |
| 悬浮模式 | 无直接等价 | `enableHoverMode` + `hoverModeArea` |
| 层级模式 | 无直接等价 | `levelMode` + `levelUniqueId` + `immersiveMode` + `levelOrder` |
| 系统材质 | 无 | `systemMaterial: SystemUiMaterial` |
| 系统接口属性 | — | `distortionMode`（@systemapi）、`edgeLightMode`（@systemapi）——不入正文，见 [系统接口](../reference/apis-arkui/js-apis-dialog-sys.md) |

#### 2. AlertDialog（确认弹窗）

| 属性 | 老接口（AlertDialog.show） | 新接口（DialogPresenter.present + DialogStyleOptions） |
|------|------|------|
| 编程模型 | `AlertDialog.show(options)` 静态方法 | `presenter.present(options): Promise<DialogResult>`（见 G1） |
| 标题 | `title: string \| Resource` | `title: ResourceStr` |
| 副标题 | 无 | `subtitle: ResourceStr`（新增） |
| 消息内容 | `message: string \| Resource` | `message: DialogMessage`（content + wordBreak） |
| 按钮 | `buttons: Array<Button>` | `buttons: Array<DialogButton>`（含 fontColor/backgroundColor/enabled/primary/style） |
| 按钮排列 | `buttonDirection: DialogButtonDirection` | `buttonDirection: DialogButtonOrientation` |
| 操作菜单 | 无 | `sheets: Array<DialogSheet>`（action-sheet 风格） |
| 网格数 | 无 | `gridCount: int` |
| 确认回调 | `confirm: VoidCallback` / `primaryButton.action` | `DialogButton.action`（通过 Promise 结果） |
| 取消回调 | `cancel` | `onWillDismiss: Callback<DialogDismissal>`（见 G2） |
| 样式 | `alignment` / `offset` / `maskColor` / `autoCancel` 等 | 继承自 `DialogBaseOptions`（同 CustomDialog） |

#### 3. TextPickerDialog（文本选择弹窗）

| 属性 | 老接口（TextPickerDialog.show） | 新接口（迁移到 DialogPresenter + ComponentContent） |
|------|------|------|
| 编程模型 | `TextPickerDialog.show(options)` 静态方法 | 使用 `DialogPresenter.present(content, DialogCustomOptions)` 自定义内容内嵌 TextPicker（见 G1） |
| 选择范围 | `range: string[] \| Resource` / `TextPickerRangeContent[]` | 内容组件中嵌入 `TextPicker`，通过自定义弹窗承载 |
| 默认选中 | `selected: number` | TextPicker 组件 `selected` 属性 |
| 确认回调 | `onAccept: (value: string\|TextPickerResult) => void` | 自定义组件内 `onAccept` 回调 |
| 取消回调 | `onCancel` | `onWillDismiss: Callback<DialogDismissal>`（见 G2） |
| 变化回调 | `onChange: (value: string\|TextPickerResult) => void` | TextPicker 组件 `onChange` |
| 样式 | `alignment` / `offset` / `maskColor` 等 | 继承自 `DialogBaseOptions` |

> **说明：** 新接口无 TextPicker 专用弹窗声明单元。迁移时使用自定义弹窗承载 `TextPicker` 组件，行为差异通过自定义内容实现等价能力。

#### 4. TimePickerDialog（时间选择弹窗）

| 属性 | 老接口（TimePickerDialog.show） | 新接口（迁移到 DialogPresenter + ComponentContent） |
|------|------|------|
| 编程模型 | `TimePickerDialog.show(options)` 静态方法 | 使用 `DialogPresenter.present(content, DialogCustomOptions)` 自定义内容内嵌 TimePicker（见 G1） |
| 24小时制 | `useMilitaryTime: boolean` | TimePicker 组件 `useMilitaryTime` 属性 |
| 响应回调 | `onAccept: (value: TimePickerValue) => void` | 自定义组件内回调 |
| 取消回调 | `onCancel` | `onWillDismiss: Callback<DialogDismissal>`（见 G2） |
| 变化回调 | `onChange` | TimePicker 组件 `onChange` |
| 样式 | `alignment` / `offset` / `maskColor` 等 | 继承自 `DialogBaseOptions` |

#### 5. DatePickerDialog（日期选择弹窗）

| 属性 | 老接口（DatePickerDialog.show） | 新接口（迁移到 DialogPresenter + ComponentContent） |
|------|------|------|
| 编程模型 | `DatePickerDialog.show(options)` 静态方法 | 使用 `DialogPresenter.present(content, DialogCustomOptions)` 自定义内容内嵌 DatePicker（见 G1） |
| 起始日期 | `start: Date` | DatePicker 组件 `start` 属性 |
| 结束日期 | `end: Date` | DatePicker 组件 `end` 属性 |
| 选中类型 | `type: DatePickerType` | DatePicker 组件 `type` 属性 |
| 响应回调 | `onAccept: (value: DatePickerResult) => void` | 自定义组件内回调 |
| 取消回调 | `onCancel` | `onWillDismiss: Callback<DialogDismissal>`（见 G2） |
| 变化回调 | `onChange` | DatePicker 组件 `onChange` |
| 样式 | `alignment` / `offset` / `maskColor` 等 | 继承自 `DialogBaseOptions` |

#### G3：高级动画参数差异

老接口使用 `customStyle: boolean` 控制是否使用自定义样式，`animationStyle`（已废弃）/ `transition` 控制动画。新接口使用 `dialogTransition: TransitionEffect` 控制内容区动画，`maskTransition: TransitionEffect` 控制蒙层动画。两者参数类型不同，**不存在等效映射**，迁移时需按新接口 `TransitionEffect` 重写动画参数。

#### G4：update 更新面收窄

老接口 `CustomDialogController.update()` 可更新多种属性。新接口 `DialogPresenter.update(content, options)` 的 `options` 类型为 `DialogBaseOptions`，实际可更新面收窄为 `alignment`、`offset`、`autoCancel`、`maskColor` 四项。其他属性（如 `backgroundColor`、`borderRadius` 等）不支持通过 `update` 运行时更新。

> **说明：** 本指南如实标注此收窄，不推动 G4 能力补齐（非目标）。

### 使用差异

#### G1：编程模型差异

老接口分两代：第一代使用静态方法（`AlertDialog.show()`、`TextPickerDialog.show()` 等），第二代使用 `@CustomDialog` 装饰器 + `CustomDialogController`。新接口统一为 `UIContext.getDialogPresenter()` 获取 `DialogPresenter` 实例，通过 `present()` 弹出，返回 `Promise<DialogResult>`。

**迁移范式：**

```typescript
// 老接口（第二代 CustomDialog）
@CustomDialog
struct MyDialog {
  controller: CustomDialogController
  build() { /* ... */ }
}
// 使用
let controller = new CustomDialogController({ builder: MyDialog() })
controller.open()

// 新接口（第三代 DialogPresenter）
let presenter = this.getUIContext().getDialogPresenter()
presenter.present(() => { /* CustomBuilder 内容 */ }, { customStyle: false })
```

#### G2：cancel 回调差异

老接口使用 `onCancel: () => void` 直接回调。新接口使用 `onWillDismiss: Callback<DialogDismissal>`，回调参数 `DialogDismissal` 包含 `dismiss: VoidCallback`（调用以确认关闭）和 `reason: DismissReason`（关闭原因）。新接口注册 `onWillDismiss` 后，弹窗不会立即关闭，需在回调中决定是否调用 `dismiss()`。

**等价实现样例：**

```typescript
// 老接口
AlertDialog.show({
  message: '确认删除？',
  cancel: () => { console.info('用户取消') }
})

// 新接口
this.getUIContext().getDialogPresenter().present({
  message: { content: '确认删除？' },
  onWillDismiss: (dismissal: dialog.DialogDismissal) => {
    if (dismissal.reason === DismissReason.PRESS_BACK) {
      console.info('用户取消')
    }
    dismissal.dismiss() // 确认关闭
  }
})
```

#### G5：FA 模型适用面

新接口 `@ohos.arkui.dialog` 标注 `@stagemodelonly`，仅支持 Stage 模型。老接口中部分接口支持 FA 模型。本指南对 FA 适用面不作显式说明（FA 模型开发者如需弹窗请继续使用老接口）。

## 适配指导

以下每个"迁移后示例（新接口）"代码块前均标注了 `<!-- @[tag](sample 文件 URL) -->` 同源注释，指向 samples 工程中对应的 `.ets` 文件。代码块内容为该文件的逐字摘录，开发者可点击注释中的链接查看完整源文件。

> 示例工程路径：`applications_app_samples/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/`

| 示例页面 | 对应章节 | 覆盖 AC |
|---------|---------|--------|
| `Index.ets` | 迁移映射入口 | AC-1, AC-4 |
| `CustomDialogMigrationPage.ets` | CustomDialog 迁移 | AC-3.1, AC-4 |
| `AlertDialogMigrationPage.ets` | AlertDialog 迁移 | AC-3.1, AC-4 |
| `TextPickerMigrationPage.ets` | TextPickerDialog 迁移 | AC-3.1, AC-4 |
| `TimePickerMigrationPage.ets` | TimePickerDialog 迁移 | AC-3.1, AC-4 |
| `DatePickerMigrationPage.ets` | DatePickerDialog 迁移 | AC-3.1, AC-4 |
| `DialogStatePage.ets` | 能力介绍（DialogBaseController/DialogState） | AC-2, AC-3.1 |

### CustomDialog → DialogPresenter.present（自定义弹窗）

| 老接口签名 | 新接口签名 | 说明 |
|-----------|-----------|------|
| `new CustomDialogController({ builder, alignment, offset, customStyle, autoCancel, maskColor, ... }).open()` | `presenter.present(content: CustomBuilder \| CustomBuilderWithId \| ComponentContent<Object>, options?: DialogCustomOptions)` | 编程模型从 Controller 改为 Presenter + Promise |
| `controller.close()` | `controller.close()` 或 `presenter.dismiss(target)` | 新接口支持 controller.close() 和 dismiss(id\|content) 两种方式 |
| `controller.update({ alignment, offset, ... })` | `presenter.update(content, { alignment, offset, autoCancel, maskColor })` | 更新面收窄（G4） |
| `onCancel: () => void` | `onWillDismiss: Callback<DialogDismissal>` | 取消回调改版（G2） |

**迁移前示例（老接口）：**

```typescript
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
struct Index {
  dialogController: CustomDialogController = new CustomDialogController({
    builder: CustomDialogExample(),
    alignment: DialogAlignment.Center,
    autoCancel: true,
    maskColor: 0x33000000
  })
  build() {
    Button('打开弹窗').onClick(() => { this.dialogController.open() })
  }
}
```

**迁移后示例（新接口）：**

<!-- @[dialog_migration_custom](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/CustomDialogMigrationPage.ets) -->

```typescript
import { dialog } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct CustomDialogMigrationPage {
  private presenter: dialog.DialogPresenter = this.getUIContext().getDialogPresenter();
  @State result: string = '';

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
    this.presenter.present(() => {
      Column() {
        Text('自定义弹窗内容')
          .fontSize(16)
          .margin({ bottom: 10 })
        Button('关闭弹窗')
          .onClick(() => {
            this.presenter.dismiss(0);
          })
      }
      .padding(20)
    }, {
      alignment: dialog.DialogBaseAlignment.CENTER,
      autoCancel: true,
      maskColor: 0x33000000
    }).then((result: dialog.DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```

### AlertDialog → DialogPresenter.present（固定样式弹窗）

| 老接口签名 | 新接口签名 | 说明 |
|-----------|-----------|------|
| `AlertDialog.show({ title, message, buttons, alignment, ... })` | `presenter.present(options?: DialogStyleOptions)` | 静态方法改 Presenter + Promise |
| `buttons: Array<{ value, action }>` | `buttons: Array<DialogButton>` | 按钮属性扩展 |
| `confirm: (value) => void` / `primaryButton.action` | `DialogButton.action` + Promise 结果 | 确认回调改 Promise |
| `cancel: () => void` | `onWillDismiss: Callback<DialogDismissal>` | 取消回调改版（G2） |

**迁移前示例（老接口）：**

```typescript
AlertDialog.show({
  title: '提示',
  message: '确认删除？',
  buttons: [
    { text: '取消', action: () => console.info('取消') },
    { text: '确认', action: () => console.info('确认') }
  ],
  alignment: DialogAlignment.Bottom
})
```

**迁移后示例（新接口）：**

<!-- @[dialog_migration_alert](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/AlertDialogMigrationPage.ets) -->

```typescript
import { dialog } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct AlertDialogMigrationPage {
  private presenter: dialog.DialogPresenter = this.getUIContext().getDialogPresenter();
  @State result: string = '';

  build() {
    Row() {
      Column() {
        Text('AlertDialog 迁移示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('老接口：AlertDialog.show')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showOldAlertDialog();
          })

        Button('新接口：DialogPresenter.present（固定样式）')
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

  private showOldAlertDialog(): void {
    this.result = '老接口示例请参考 ts-methods-alert-dialog-box.md';
  }

  private showNewAlertDialog(): void {
    this.presenter.present({
      title: '提示',
      message: { content: '确认删除？' },
      buttons: [
        {
          value: '取消',
          action: () => {
            this.result = '用户点击取消';
          }
        },
        {
          value: '确认',
          action: () => {
            this.result = '用户点击确认';
          }
        }
      ],
      alignment: dialog.DialogBaseAlignment.BOTTOM,
      onWillDismiss: (dismissal: dialog.DialogDismissal) => {
        this.result = 'onWillDismiss, reason: ' + dismissal.reason;
        dismissal.dismiss();
      }
    }).then((result: dialog.DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```

### TextPickerDialog → DialogPresenter.present（自定义弹窗内嵌 TextPicker）

| 老接口签名 | 新接口签名 | 说明 |
|-----------|-----------|------|
| `TextPickerDialog.show({ range, selected, onAccept, onChange, onCancel })` | `presenter.present(content, DialogCustomOptions)` + 内容中嵌入 `TextPicker` | 无专用弹窗声明，用自定义弹窗承载 |
| `onAccept: (value) => void` | 自定义组件内回调 | 回调位置从选项移入内容组件 |
| `onCancel: () => void` | `onWillDismiss: Callback<DialogDismissal>` | 取消回调改版（G2） |

**迁移前示例（老接口）：**

```typescript
TextPickerDialog.show({
  range: ['A', 'B', 'C'],
  selected: 0,
  onAccept: (value: string) => console.info('选中: ' + value),
  onChange: (value: string) => console.info('变化: ' + value)
})
```

**迁移后示例（新接口）：**

<!-- @[dialog_migration_textpicker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/TextPickerMigrationPage.ets) -->

```typescript
import { dialog } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct TextPickerMigrationPage {
  private presenter: dialog.DialogPresenter = this.getUIContext().getDialogPresenter();
  @State selected: number = 0;
  @State result: string = '';
  private range: string[] = ['A', 'B', 'C', 'D'];

  build() {
    Row() {
      Column() {
        Text('TextPickerDialog 迁移示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('老接口：TextPickerDialog.show')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.result = '老接口示例请参考 ts-methods-textpicker-dialog.md';
          })

        Button('新接口：DialogPresenter.present + TextPicker')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showNewTextPickerDialog();
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

  private showNewTextPickerDialog(): void {
    this.presenter.present(() => {
      TextPicker({ range: this.range, selected: this.selected })
        .onChange((value: string) => {
          this.selected = this.range.indexOf(value);
        })
        .onAccept((value: string) => {
          this.result = '选中: ' + value;
        })
    }, {
      alignment: dialog.DialogBaseAlignment.CENTER
    }).then((result: dialog.DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```

### TimePickerDialog → DialogPresenter.present（自定义弹窗内嵌 TimePicker）

| 老接口签名 | 新接口签名 | 说明 |
|-----------|-----------|------|
| `TimePickerDialog.show({ selected, useMilitaryTime, onAccept, onChange, onCancel })` | `presenter.present(content, DialogCustomOptions)` + 内容中嵌入 `TimePicker` | 无专用弹窗声明 |
| `onAccept: (value) => void` | 自定义组件内回调 | 回调位置移入内容组件 |
| `onCancel: () => void` | `onWillDismiss: Callback<DialogDismissal>` | 取消回调改版（G2） |

**迁移前示例（老接口）：**

```typescript
TimePickerDialog.show({
  selected: new Date(),
  useMilitaryTime: true,
  onAccept: (value) => console.info('选中时间'),
  onCancel: () => console.info('取消')
})
```

**迁移后示例（新接口）：**

<!-- @[dialog_migration_timepicker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/TimePickerMigrationPage.ets) -->

```typescript
import { dialog } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct TimePickerMigrationPage {
  private presenter: dialog.DialogPresenter = this.getUIContext().getDialogPresenter();
  @State result: string = '';

  build() {
    Row() {
      Column() {
        Text('TimePickerDialog 迁移示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('老接口：TimePickerDialog.show')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.result = '老接口示例请参考 ts-methods-timepicker-dialog.md';
          })

        Button('新接口：DialogPresenter.present + TimePicker')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showNewTimePickerDialog();
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

  private showNewTimePickerDialog(): void {
    this.presenter.present(() => {
      TimePicker({ selected: new Date(), useMilitaryTime: true })
        .onChange((value: TimePickerValue) => {
          this.result = '时间变化: ' + value.hour + ':' + value.minute;
        })
    }, {
      alignment: dialog.DialogBaseAlignment.CENTER
    }).then((result: dialog.DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```

### DatePickerDialog → DialogPresenter.present（自定义弹窗内嵌 DatePicker）

| 老接口签名 | 新接口签名 | 说明 |
|-----------|-----------|------|
| `DatePickerDialog.show({ start, end, selected, onAccept, onChange, onCancel })` | `presenter.present(content, DialogCustomOptions)` + 内容中嵌入 `DatePicker` | 无专用弹窗声明 |
| `onAccept: (value) => void` | 自定义组件内回调 | 回调位置移入内容组件 |
| `onCancel: () => void` | `onWillDismiss: Callback<DialogDismissal>` | 取消回调改版（G2） |

**迁移前示例（老接口）：**

```typescript
DatePickerDialog.show({
  start: new Date('2020-01-01'),
  end: new Date('2030-12-31'),
  onAccept: (value) => console.info('选中日期'),
  onCancel: () => console.info('取消')
})
```

**迁移后示例（新接口）：**

<!-- @[dialog_migration_datepicker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkuiDialogMigrationSample/entry/src/main/ets/pages/DatePickerMigrationPage.ets) -->

```typescript
import { dialog } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct DatePickerMigrationPage {
  private presenter: dialog.DialogPresenter = this.getUIContext().getDialogPresenter();
  @State result: string = '';

  build() {
    Row() {
      Column() {
        Text('DatePickerDialog 迁移示例')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })

        Button('老接口：DatePickerDialog.show')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.result = '老接口示例请参考 ts-methods-datepicker-dialog.md';
          })

        Button('新接口：DialogPresenter.present + DatePicker')
          .width('90%')
          .margin({ bottom: 10 })
          .onClick(() => {
            this.showNewDatePickerDialog();
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

  private showNewDatePickerDialog(): void {
    this.presenter.present(() => {
      DatePicker({
        start: new Date('2020-01-01'),
        end: new Date('2030-12-31')
      })
        .onChange((value: DatePickerResult) => {
          this.result = '日期变化: ' + value.year + '-' + (value.month + 1) + '-' + value.day;
        })
    }, {
      alignment: dialog.DialogBaseAlignment.CENTER
    }).then((result: dialog.DialogResult) => {
      this.result = 'present success, dialogId: ' + result.dialogId;
    }).catch((error: BusinessError) => {
      this.result = `present error: ${error.code}`;
    });
  }
}
```
