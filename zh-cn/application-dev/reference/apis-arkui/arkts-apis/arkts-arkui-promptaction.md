# @ohos.promptAction

创建并显示即时反馈、对话框和操作菜单，适用于系统通知、交互确认、菜单选择等场景。

> **说明：** 

> - 本模块不支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)的文件声明处使用，即不能在UIAbility的生命周期中调用，需要在 创建组件实例后使用。
> 
> - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)说明。建议<!--Del-->在除[ServiceExtensionAbility](../../../application-models/serviceextensionability-sys.md)等无UI界面的场景外，均<!--DelEnd-->使用UIContext中的弹窗方法。

## 导入模块

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [promptAction](arkts-arkui-promptaction-n.md) | 创建并显示即时反馈、对话框和操作菜单，适用于系统通知、交互确认、菜单选择等场景。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [LevelOrder](arkts-arkui-promptaction-levelorder-c.md) | 弹窗层级，可以控制弹窗显示的顺序。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DismissDialogAction](arkts-arkui-promptaction-dismissdialogaction-i.md) | Dialog关闭的信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ImmersiveMode](arkts-arkui-promptaction-immersivemode-e.md) | 页面内弹窗蒙层显示区域模式。 |
| [LevelMode](arkts-arkui-promptaction-levelmode-e.md) | 弹窗显示层级模式。 |

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
