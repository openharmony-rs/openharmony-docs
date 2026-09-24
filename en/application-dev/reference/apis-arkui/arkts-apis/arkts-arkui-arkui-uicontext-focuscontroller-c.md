# FocusController

```TypeScript
export class FocusController
```

Provides capabilities to control focus, including features such as clearing, moving, and activating focus.

> **NOTE:** 
> 
> In the following API examples, you must first use [getFocusController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getfocuscontroller) in
> **UIContext** to obtain a **FocusController** instance, and then call the APIs using the obtained instance.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

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

Sets the [focus activation state](../../../ui/arkts-common-events-focus-event.md) of this page.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isActive | boolean | Yes | Whether to enter or exit the focus activation state.<br>The value **true** means to enter the focus activation state, and **false** means to exit the focus activation state. |
| autoInactive | boolean | No | Logic for exiting the focus activation state.<br>The value **true** means the focus activation state will be exited automatically when touch or mouse events are triggered, and **false** means the state is controlled solely by API calls.<br>Default value: **true** |

**Examples**

```TypeScript
// This example demonstrates how to enter the focus activation state when the page loading is completed. In this state, arrow keys can be used for focus navigation.
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

Clears the focus and forcibly moves the focus to the root container node of the page, causing other nodes in the focus chain to lose focus.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

In this example, button2 receives initial focus by default. After clearFocus is clicked, focus returns to the page's root container node column1. Pressing the Tab key then restores focus to button2. Clicking button1 transfers focus to that button. Following another clearFocus click, focus again returns to column1, and pressing Tab subsequently moves focus to button1.

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

Obtains the focus activation state of the UI instance.

For details about the focus activation state, see [Basic Concepts](../../../ui/arkts-common-events-focus-event.md#basic-concepts).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Focus activation state of the UI instance. The value **true** means that the instance has entered the focus activation state, and **false** means that the instance has exited the focus activation state. |

**Examples**

The following example verifies that isActive() returns the focus activation state of the UI instance.

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

Transfers focus to a component node by the component ID, which is effective immediately.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | [Component ID](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-common.md) of the target node. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [150001](../errorcode-focus.md#150001-component-not-focusable) | the component cannot be focused. |
| [150002](../errorcode-focus.md#150002-ancestor-component-not-focusable) | This component has an unfocusable ancestor. |
| [150003](../errorcode-focus.md#150003-component-does-not-exist) | the component is not on tree or does not exist. |

**Examples**

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

Sets whether the new page automatically obtains focus during page switching.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isAutoFocusTransfer | boolean | Yes | Whether the new page automatically obtains focus during page switching using navigation components or APIs, such as [Router](arkts-arkui-router.md), Navigation, Menu, [Dialog](arkts-arkui-arkui-advanced-dialog.md), and [Popup](arkts-arkui-arkui-advanced-popup.md). The value **true** means the new page automatically obtains focus, and **false** means the opposite. Default value: **true**. |

**Examples**

```TypeScript
@CustomDialog
struct CustomDialogExample {
  controller?: CustomDialogController;

  build() {
    Column() {
      Text('This is a custom dialog box')
        .fontSize(30)
        .height(100)
      Text('The dialog box should not automatically acquire focus')
        .fontSize(20)
        .height(100)
      Button('Close Dialog Box')
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

Sets the mode for processing key events.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [KeyProcessingMode](arkts-arkui-keyprocessingmode-e.md) | Yes | Mode for processing key events. |

**Examples**

```TypeScript
// This example demonstrates how to set the key event processing priority after page loading is complete.
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
