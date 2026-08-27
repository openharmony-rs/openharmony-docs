# FocusController

提供控制焦点的能力，如清除、移动和激活焦点等功能。

> **说明：**
> 
> 以下API需先使用UIContext中的[getFocusController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getfocuscontroller)方法获取FocusController实例，再通过该实例调用对应方法。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## activate

```TypeScript
activate(isActive: boolean, autoInactive?: boolean): void
```

设置当前界面的[焦点激活态](../../../ui/arkts-common-events-focus-event.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isActive | boolean | 是 | 设置是否进入/退出焦点激活态。true表示设置进入焦点激活态，false表示设置退出焦点激活态。 |
| autoInactive | boolean | 否 | 设置焦点激活态退出逻辑。为true时，会自动在触摸事件、鼠标事件触发时退出，为false时，仅受开发者API控制。默认值：true |

**示例**

```TypeScript
// 该示例表示在页面加载完成时进入焦点激活态，可按方向键在button间走焦
@Entry
@Component
struct ActivateExample {
  aboutToAppear() {
    this.getUIContext().getFocusController().activate(true, false);
  }

  aboutToDisappear() {
    this.getUIContext().getFocusController().activate(false);
  }

  build() {
    Row() {
      Button('Button1')
        .width(200)
        .height(70)
        .defaultFocus(true)

      Button('Button2')
        .width(200)
        .height(70)

      Button('Button3')
        .width(200)
        .height(70)
    }
    .padding(10)
    .justifyContent(FlexAlign.SpaceBetween)
    .width(800)
  }
}
```

## clearFocus

```TypeScript
clearFocus(): void
```

清除焦点，将焦点强制转移到页面根容器节点，焦点链路上其他节点失焦。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

在该示例中，按钮"button2"默认获焦，点击按钮"clearFocus"后，焦点回到该页面的根容器节点"column1"，此时按下键盘TAB键，按钮"button2"重新获焦。可通过点击"button1"使该按钮获焦，点击按钮"clearFocus"后，焦点同样回到该页面的根容器节点"column1"，此时按下键盘TAB键，由按钮"button1"重新获焦。

```TypeScript
@Entry
@Component
struct ClearFocusExample {
  @State buttonColor: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Column({ space: 5 }) {
        Button('button1')
          .width(200)
          .height(70)
          .fontColor(Color.White)
          .focusOnTouch(true)
          .backgroundColor(Color.Blue)
        Button('button2')
          .width(200)
          .height(70)
          .fontColor(Color.White)
          .focusOnTouch(true)
          .backgroundColor(this.buttonColor)
          .defaultFocus(true)
          .onFocus(() => {
            this.buttonColor = Color.Red;
          })
          .onBlur(() => {
            this.buttonColor = Color.Blue;
          })
        Button('clearFocus')
          .width(200)
          .height(70)
          .fontColor(Color.White)
          .backgroundColor(Color.Blue)
          .onClick(() => {
            this.getUIContext().getFocusController().clearFocus();
          })
      }
      .id('column2')
    }
    .id('column1')
    .width('100%')
    .height('100%')
  }
}
```

## isActive

```TypeScript
isActive(): boolean
```

返回UI实例的焦点激活态。焦点激活态可参考[基础概念：焦点激活态](../../../ui/arkts-common-events-focus-event.md#基础概念)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回UI实例的焦点激活态。true表示当前进入焦点激活态，false表示当前已退出焦点激活态。 |

**示例**

验证isActive返回UI实例的焦点激活态。

```TypeScript
@Entry
@Component
struct IsActiveExample {
  @State btColor: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Column({ space: 5 }) {
        Button('button1')
          .width(200)
          .height(70)
          .fontColor(Color.White)
          .focusOnTouch(true)
          .backgroundColor(Color.Blue)
          .onClick(() => {
            console.info('button1 onClick');
            this.getUIContext().getFocusController().activate(true);
            console.info(`focus status ${this.getUIContext().getFocusController().isActive()}`);
          })
        Button('button2')
          .width(200)
          .height(70)
          .fontColor(Color.White)
          .focusOnTouch(true)
          .backgroundColor(this.btColor)
          .defaultFocus(true)
          .onClick(() => {
            console.info('button2 onClick');
            this.getUIContext().getFocusController().activate(false);
            console.info(`focus status ${this.getUIContext().getFocusController().isActive()}`);
          })
          .onFocus(() => {
            this.btColor = Color.Red;
          })
          .onBlur(() => {
            this.btColor = Color.Blue;
          })
      }
    }
    .width('100%')
    .height('100%')
  }
}
```

## requestFocus

```TypeScript
requestFocus(key: string): void
```

通过组件的id将焦点转移到组件树对应的实体节点，当前帧生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 节点对应的组件标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [150001](../errorcode-focus.md#150001-节点无法获得焦点) | the component cannot be focused. |
| [150002](../errorcode-focus.md#150002-祖先节点无法获得焦点) | This component has an unfocusable ancestor. |
| [150003](../errorcode-focus.md#150003-节点不存在) | the component is not on tree or does not exist. |

**示例**

```TypeScript
@Entry
@Component
struct RequestExample {
  @State btColor: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Column({ space: 5 }) {
        Button('Button')
          .width(200)
          .height(70)
          .fontColor(Color.White)
          .focusOnTouch(true)
          .backgroundColor(this.btColor)
          .onFocus(() => {
            this.btColor = Color.Red;
          })
          .onBlur(() => {
            this.btColor = Color.Blue;
          })
          .id('testButton')

        Divider()
          .vertical(false)
          .width('80%')
          .backgroundColor(Color.Black)
          .height(10)

        Button('requestFocus')
          .width(200)
          .height(70)
          .onClick(() => {
            this.getUIContext().getFocusController().requestFocus('testButton');
          })

        Button('requestFocus fail')
          .width(200)
          .height(70)
          .onClick(() => {
            try {
              this.getUIContext().getFocusController().requestFocus('eee');
            } catch (error) {
              console.error(`Failed to request focus. Code: ${error.code}, message: ${error.message}`);
            }
          })
      }
    }
    .width('100%')
    .height('100%')
  }
}
```

## setAutoFocusTransfer

```TypeScript
setAutoFocusTransfer(isAutoFocusTransfer: boolean): void
```

设置页面切换时，新的页面是否需要主动获取焦点。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isAutoFocusTransfer | boolean | 是 | 设置页面切换时，新的页面是否需要主动获取焦点，例如[Router](arkts-router.md)、 Navigation、Menu、Dialog、 Popup等。true表示需要主动获取焦点，false表示不需要主动获取焦点。默认值为true。 |

**示例**

```TypeScript
@CustomDialog
struct CustomDialogExample {
  controller?: CustomDialogController;

  build() {
    Column() {
      Text('这是自定义弹窗')
        .fontSize(30)
        .height(100)
      Text('弹窗不能主动获取焦点')
        .fontSize(20)
        .height(100)
      Button('点我关闭弹窗')
        .onClick(() => {
          if (this.controller != undefined) {
            this.getUIContext().getFocusController().setAutoFocusTransfer(true);
            this.controller.close();
          }
        })
        .margin(20)
    }
  }
}

@Entry
@Component
struct CustomDialogUser {
  dialogController: CustomDialogController | null = new CustomDialogController({
    builder: CustomDialogExample({}),
  });

  aboutToDisappear() {
    this.dialogController = null;
  }

  build() {
    Column() {
      Button('click me')
        .onClick(() => {
          if (this.dialogController != null) {
            this.getUIContext().getFocusController().setAutoFocusTransfer(false);
            this.dialogController.open();
          }
        }).backgroundColor(0x317aff)
    }.width('100%').margin({ top: 5 })
  }
}
```

## setKeyProcessingMode

```TypeScript
setKeyProcessingMode(mode: KeyProcessingMode): void
```

设置按键事件处理的优先级。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [KeyProcessingMode](arkts-arkui-keyprocessingmode-e.md) | 是 | 按键处理模式。 |

**示例**

```TypeScript
// 该示例演示了在页面加载完成后设置按键事件处理优先级的实现方式。
@Entry
@Component
struct Index {
  aboutToAppear() {
    this.getUIContext().getFocusController().setKeyProcessingMode(KeyProcessingMode.ANCESTOR_EVENT);
  }

  build() {
    Row() {
      Row() {
        Button('Button1').id('Button1').onKeyEvent((event) => {
          console.info('Button1');
          return true;
        })
        Button('Button2').id('Button2').onKeyEvent((event) => {
          console.info('Button2');
          return true;
        })
      }
      .width('100%')
      .height('100%')
      .id('Row1')
      .onKeyEventDispatch((event) => {
        let context = this.getUIContext();
        context.getFocusController().requestFocus('Button1');
        return context.dispatchKeyEvent('Button1', event);
      })
    }
    .height('100%')
    .width('100%')
    .onKeyEventDispatch((event) => {
      if (event.type == KeyType.Down) {
        let context = this.getUIContext();
        context.getFocusController().requestFocus('Row1');
        return context.dispatchKeyEvent('Row1', event);
      }
      return true;
    })
  }
}
```
