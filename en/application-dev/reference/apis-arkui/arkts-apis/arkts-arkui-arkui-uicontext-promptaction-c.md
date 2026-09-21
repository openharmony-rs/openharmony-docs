# PromptAction

```TypeScript
export class PromptAction
```

Provides APIs to create and display toasts, dialog boxes, action menus, and custom popups.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 10.
> 
> - In the following API examples, you must first use [getPromptAction()](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction) in
> **UIContext** to obtain a **PromptAction** instance, and then call the APIs using the obtained instance.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## closeCustomDialog

```TypeScript
closeCustomDialog<T extends Object>(dialogContent: ComponentContent<T>): Promise<void>
```

Closes a custom dialog box corresponding to **dialogContent**. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dialogContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content of the custom dialog box. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | Dialog content not found. The ComponentContent cannot be found. |

**Examples**

This example shows how to close a custom dialog box corresponding to dialogContent using closeCustomDialog.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent } from '@kit.ArkUI';

class Params {
  text: string = "";

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
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = "hello";

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText), new Params(this.message));
            promptAction.openCustomDialog(contentNode)
              .then(() => {
                console.info('succeeded');
              })
              .catch((error: BusinessError) => {
                console.error(`OpenCustomDialog args error code is ${error.code}, message is ${error.message}`);
              })
            setTimeout(() => {
              promptAction.closeCustomDialog(contentNode)
                .then(() => {
                  console.info('succeeded');
                })
                .catch((error: BusinessError) => {
                  console.error(`OpenCustomDialog args error code is ${error.code}, message is ${error.message}`);
                })
            }, 2000); // Automatically close the dialog box after 2 seconds.
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

<a id="closecustomdialog-1"></a>

## closeCustomDialog

```TypeScript
closeCustomDialog(dialogId: number): void
```

Closes the specified custom dialog box.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dialogId | number | Yes | ID of the custom dialog box to close. It is returned from **openCustomDialog**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

```TypeScript
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();
  private customDialogComponentId: number = 0;

  @Builder
  customDialogComponent() {
    Column() {
      Text('Dialog box').fontSize(30)
      Row({ space: 50 }) {
        Button("OK").onClick(() => {
          this.promptAction.closeCustomDialog(this.customDialogComponentId);
        })
        Button("Cancel").onClick(() => {
          this.promptAction.closeCustomDialog(this.customDialogComponentId);
        })
      }
    }.height(200).padding(5).justifyContent(FlexAlign.SpaceBetween)
  }

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            this.promptAction.openCustomDialog({
              builder: () => {
                this.customDialogComponent()
              },
              onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
                console.info(`reason ${dismissDialogAction.reason}`);
                console.info('dialog onWillDismiss');
                if (dismissDialogAction.reason == DismissReason.PRESS_BACK) {
                  dismissDialogAction.dismiss();
                }
                if (dismissDialogAction.reason == DismissReason.TOUCH_OUTSIDE) {
                  dismissDialogAction.dismiss();
                }
              }
            }).then((dialogId: number) => {
              this.customDialogComponentId = dialogId;
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

## closeMenu

```TypeScript
closeMenu<T extends Object>(content: ComponentContent<T>): Promise<void>
```

Closes the menu corresponding to the provided content. This API uses a promise to return the result.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the menu. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | The ComponentContent cannot be found. |

**Examples**

This example demonstrates how to close a menu using closeMenu.

```TypeScript
import { ComponentContent, FrameNode } from '@kit.ArkUI';

export function doSomething(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  showMenu(context, uniqueId, contentNode);
}

@Builder
function MyMenu() {
  Column() {
    Menu() {
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "Menu item 1" })
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "Menu item 2" })
    }
  }
  .width('80%')
  .padding('20lpx')
}

export function showMenu(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  const promptAction = context.getPromptAction();
  let frameNode: FrameNode | null = context.getFrameNodeByUniqueId(uniqueId);
  let frameNodeTarget = frameNode?.getFirstChild();
  frameNodeTarget = frameNodeTarget?.getChild(0);
  let targetId = frameNodeTarget?.getUniqueId();
  promptAction.openMenu(contentNode, { id: targetId }, {
    enableArrow: true,
  });
  setTimeout(() => {
    promptAction.closeMenu(contentNode);
  }, 2000);
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('OpenMenu', { type: ButtonType.Normal, stateEffect: true })
        .borderRadius('16lpx')
        .width('80%')
        .margin(10)
        .onClick(() => {
          let context = this.getUIContext();
          const contentNode = new ComponentContent(context, wrapBuilder(MyMenu));
          doSomething(context, this.getUniqueId(), contentNode);
        })
    }
  }
}
```

## closePopup

```TypeScript
closePopup<T extends Object>(content: ComponentContent<T>): Promise<void>
```

Closes the popup corresponding to the provided **content**. This API uses a promise to return the result.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the popup. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | The ComponentContent cannot be found. |

**Examples**

See the example for [openPopup](#openpopup).

## closeToast

```TypeScript
closeToast(toastId: number): void
```

Closes the specified toast.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| toastId | number | Yes | Toast ID returned from **openToast**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [103401](../errorcode-promptAction.md#103401-toast-not-found) | Cannot find the toast. |

**Examples**

See the example for [openToast18](#opentoast).

## getBottomOrder

```TypeScript
getBottomOrder(): LevelOrder
```

This API returns the order of the dialog box currently at the bottom layer. This information can be used to specify the desired order for subsequent dialog boxes.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LevelOrder](arkts-arkui-promptaction-levelorder-c.md) | Order of the topmost dialog box. |

**Examples**

This example shows how to use getBottomOrder to obtain the order of the dialog box currently at the bottom layer.

```TypeScript
import { ComponentContent, PromptAction, LevelOrder, promptAction, UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";
  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column({ space: 20 }) {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = 'Dialog box';
  private ctx: UIContext = this.getUIContext();
  private promptAction: PromptAction = this.ctx.getPromptAction();
  private contentNode: ComponentContent<Object> =
    new ComponentContent(this.ctx, wrapBuilder(buildText), new Params(this.message));

  private baseDialogOptions: promptAction.BaseDialogOptions = {
    showInSubWindow: false,
    levelOrder: LevelOrder.clamp(30.1),
  };

  build() {
    Row() {
      Column({ space: 10 }) {
        Button('Open Custom Dialog Box')
          .fontSize(20)
          .onClick(() => {
            this.promptAction.openCustomDialog(this.contentNode, this.baseDialogOptions)
              .catch((err: BusinessError) => {
                console.error("openCustomDialog error: " + err.code + " " + err.message);
              })
              .then(() => {
                let bottomOrder: LevelOrder = this.promptAction.getBottomOrder();
                if (bottomOrder !== undefined) {
                  console.error('bottomOrder: ' + bottomOrder.getOrder());
                }
              })
          })
      }.width('100%')
    }.height('100%')
  }
}
```

## getTopOrder

```TypeScript
getTopOrder(): LevelOrder
```

Obtains the order of the topmost dialog box.

This API returns the order of the dialog box currently at the top layer. This information can be used to specify the desired order for subsequent dialog boxes.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LevelOrder](arkts-arkui-promptaction-levelorder-c.md) | Order of the topmost dialog box. |

**Examples**

This example shows how to use getTopOrder to obtain the order of the dialog box currently at the top layer.

```TypeScript
import { ComponentContent, PromptAction, LevelOrder, promptAction, UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";
  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column({ space: 20 }) {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = 'Dialog box';
  private ctx: UIContext = this.getUIContext();
  private promptAction: PromptAction = this.ctx.getPromptAction();
  private contentNode: ComponentContent<Object> =
    new ComponentContent(this.ctx, wrapBuilder(buildText), new Params(this.message));

  private baseDialogOptions: promptAction.BaseDialogOptions = {
    showInSubWindow: false,
    levelOrder: LevelOrder.clamp(30.1),
  };

  build() {
    Row() {
      Column({ space: 10 }) {
        Button('Open Custom Dialog Box')
          .fontSize(20)
          .onClick(() => {
            this.promptAction.openCustomDialog(this.contentNode, this.baseDialogOptions)
              .catch((err: BusinessError) => {
                console.error("openCustomDialog error: " + err.code + " " + err.message);
              })
              .then(() => {
                let topOrder: LevelOrder = this.promptAction.getTopOrder();
                if (topOrder !== undefined) {
                  console.error('topOrder: ' + topOrder.getOrder());
                }
              })
          })
      }.width('100%')
    }.height('100%')
  }
}
```

## openCustomDialog

```TypeScript
openCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options?: promptAction.BaseDialogOptions): Promise<void>
```

Opens a custom dialog box corresponding to **dialogContent**. This API uses a promise to return the result. The dialog box displayed through this API has its content fully following style settings of **dialogContent**. It is displayed in the same way where **customStyle** is set to **true**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dialogContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content of the custom dialog box. |
| options | [promptAction.BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) | No | Dialog box style.<br> Note: If both [isModal](arkts-arkui-promptaction-basedialogoptions-i.md) and [showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md) in **BaseDialogOptions** are set to **true**, only **showInSubWindow** takes effect. In this case, the non-modal dialog box is displayed without mask in the subwindow. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | Dialog content error. The ComponentContent is incorrect. |
| [103302](../errorcode-promptAction.md#103302-custom-dialog-box-already-exists) | Dialog content already exist. The ComponentContent has already been opened. |

**Examples**

This example demonstrates how to listen for changes in [system environment information](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md) (such as system language and color mode) and update a custom dialog box using the [update](arkts-arkui-arkui-uicontext-dialogpresenter-c.md#update) and updateConfiguration APIs of ComponentContent<T>.

```TypeScript
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
          // Call update of ComponentContent to update the colorMode settings.
          this.contentNode?.update(new Params(this.message, config.colorMode))
          setTimeout(() => {
            // Call updateConfiguration of ComponentContent to trigger configuration update of the entire node.
            this.contentNode?.updateConfiguration()
          })
        })
      }
    }
    // Register a listener for system environment changes.
    this.callbackId =
      this.getUIContext().getHostContext()?.getApplicationContext().on('environment', environmentCallback)
    // Set the application color mode to follow the system settings.
    this.getUIContext()
      .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET)
  }

  aboutToDisappear() {
    // Unregister the listener for system environment changes.
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
            promptAction.openCustomDialog(this.contentNode).then(() => {
              console.info("succeeded")
            }).catch((error: BusinessError) => {
              console.error(`OpenCustomDialog args error code is ${error.code}, message is ${error.message}`);
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

<a id="opencustomdialog-1"></a>

## openCustomDialog

```TypeScript
openCustomDialog(options: promptAction.CustomDialogOptions): Promise<number>
```

Creates and displays a custom dialog box. This API uses a promise to return the dialog box ID for use with **closeCustomDialog**.

+ *

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.CustomDialogOptions](arkts-arkui-promptaction-customdialogoptions-i.md) | Yes | Content of the custom dialog box.<br> + * Note: If both [isModal](arkts-arkui-promptaction-basedialogoptions-i.md) + * and [showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md) in **BaseDialogOptions** are set to **true**, + * only **showInSubWindow** takes effect. In this case, the non-modal dialog box is displayed without mask in the subwindow. + |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise that returns the dialog box ID for use with **closeCustomDialog**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private customDialogComponentId: number = 0;

  @Builder
  customDialogComponent() {
    Column() {
      Text('A dialog box is open').fontSize(20)
      Row({ space: 10 }) {
        Button('Cancel').onClick(() => {
          try {
            this.getUIContext().getPromptAction().closeCustomDialog(this.customDialogComponentId)
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
          }
        }).width(100).backgroundColor('#d5d5d5').fontColor('#707070')
        Button('OK').onClick(() => {
          try {
            this.getUIContext().getPromptAction().closeCustomDialog(this.customDialogComponentId)
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`closeCustomDialog error code is ${code}, message is ${message}`);
          }
        }).width(100)
      }
    }.height(150).padding(20).justifyContent(FlexAlign.SpaceBetween)
  }

  build() {
    Row() {
      Column({ space: 20 }) {
        Button('Click Me')
          .fontSize(30)
          .onClick(() => {
            this.getUIContext()
              .getPromptAction()
              .openCustomDialog({
                builder: () => {
                  this.customDialogComponent()
                },
                onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
                  console.info('reason' + JSON.stringify(dismissDialogAction.reason));
                  console.info('dialog onWillDismiss');
                  if (dismissDialogAction.reason == DismissReason.PRESS_BACK) {
                    dismissDialogAction.dismiss();
                  }
                  if (dismissDialogAction.reason == DismissReason.TOUCH_OUTSIDE) {
                    dismissDialogAction.dismiss();
                  }
                }
              })
              .then((dialogId: number) => {
                this.customDialogComponentId = dialogId;
              })
              .catch((error: BusinessError) => {
                console.error(`openCustomDialog error code is ${error.code}, message is ${error.message}`);
              })
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## openCustomDialogWithController

```TypeScript
openCustomDialogWithController<T extends Object>(dialogContent: ComponentContent<T>, controller: promptAction.DialogController,
    options?: promptAction.BaseDialogOptions): Promise<void>
```

Opens a custom dialog box corresponding to **dialogContent**. This API uses a promise to return the result. A dialog box controller can be bound to the custom dialog box, allowing for subsequent control of the dialog box through the controller.

The dialog box displayed through this API has its content fully following style settings of **dialogContent**. It is displayed in the same way where **customStyle** is set to **true**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dialogContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content of the custom dialog box. |
| controller | [promptAction.DialogController](arkts-arkui-promptaction-dialogcontroller-c.md) | Yes | Controller of the custom dialog box. |
| options | [promptAction.BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) | No | Style of the custom dialog box.<br> Note: If both [isModal](arkts-arkui-promptaction-basedialogoptions-i.md) and [showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md) in **BaseDialogOptions** are set to **true**, only **showInSubWindow** takes effect. In this case, the non-modal dialog box is displayed without mask in the subwindow. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | Dialog content error. The ComponentContent is incorrect. |
| [103302](../errorcode-promptAction.md#103302-custom-dialog-box-already-exists) | Dialog content already exist. The ComponentContent has already been opened. |

**Examples**

This example demonstrates how to create a custom dialog box with an external controller binding using openCustomDialog.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent, promptAction } from '@kit.ArkUI';

class Params {
  text: string = "";
  dialogController: promptAction.DialogController = new promptAction.DialogController();

  constructor(text: string, dialogController: promptAction.DialogController) {
    this.text = text;
    this.dialogController = dialogController;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
    Button('Close by DialogController')
      .onClick(() => {
        if (params.dialogController != undefined) {
          params.dialogController.close();
        }
      })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@ComponentV2
struct Index {
  @Local message: string = "hello";
  private dialogController: promptAction.DialogController = new promptAction.DialogController();

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText),
              new Params(this.message, this.dialogController));
            promptAction.openCustomDialogWithController(contentNode, this.dialogController)
              .then(() => {
                console.info('succeeded');
              })
              .catch((error: BusinessError) => {
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

## openMenu

```TypeScript
openMenu<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: MenuOptions): Promise<void>
```

Opens a menu with the specified content. This API uses a promise to return the result.

> **NOTE:** 
> 
> - If an invalid **target** is provided, the menu will not be displayed.
> 
> - You must maintain the provided **content**, on which [updateMenu](#updatemenu) and [closeMenu](#closemenu) rely to identify the target menu.
> 
> - If your **wrapBuilder** includes other components (such as [Popup](arkts-arkui-arkui-advanced-popup.md) or [Chip](arkts-arkui-arkui-advanced-chip.md)), the [ComponentContent](arkts-arkui-componentcontent-c.md)constructor must include four parameters, and the **options** parameter must be
> **{ nestingBuilderSupported: true }**.
> 
> - Nested subwindow dialog boxes are not supported. For example, when [openMenu](#openmenu) has
> **showInSubWindow** set to **true**, another dialog box with **showInSubWindow=true** cannot be displayed.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the menu. |
| target | [TargetInfo](arkts-arkui-arkui-uicontext-targetinfo-i.md) | Yes | Information about the target component to bind. |
| options | [MenuOptions](../arkts-components/arkts-arkui-common-comp-menuoptions-i.md) | No | Style of the menu.<br>**NOTE:** <br>The **title** property is not effective.<br> The **preview** parameter supports only the **MenuPreviewMode** type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103302](../errorcode-promptAction.md#103302-custom-dialog-box-already-exists) | The ComponentContent already exists. |
| [103304](../errorcode-promptAction.md#103304-target-id-not-found) | The targetId does not exist. |
| [103305](../errorcode-promptAction.md#103305-node-specified-by-targetid-not-mounted-on-the-component-tree) | The node of targetId is not in the component tree. |

**Examples**

This example demonstrates how to create and display a menu using openMenu.

```TypeScript
import { ComponentContent, FrameNode } from '@kit.ArkUI';

export function doSomething(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  showMenu(context, uniqueId, contentNode);
}

@Builder
function MyMenu() {
  Column() {
    Menu() {
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "Menu item 1" })
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "Menu item 2" })
    }
  }
  .width('80%')
  .padding('20lpx')
}

export function showMenu(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  const promptAction = context.getPromptAction();
  let frameNode: FrameNode | null = context.getFrameNodeByUniqueId(uniqueId);
  let frameNodeTarget = frameNode?.getFirstChild();
  frameNodeTarget = frameNodeTarget?.getChild(0);
  let targetId = frameNodeTarget?.getUniqueId();
  promptAction.openMenu(contentNode, { id: targetId }, {
    enableArrow: true,
  });
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('OpenMenu', { type: ButtonType.Normal, stateEffect: true })
        .borderRadius('16lpx')
        .width('80%')
        .margin(10)
        .onClick(() => {
          let context = this.getUIContext();
          const contentNode = new ComponentContent(context, wrapBuilder(MyMenu));
          doSomething(context, this.getUniqueId(), contentNode);
        })
    }
  }
}
```

## openPopup

```TypeScript
openPopup<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: PopupCommonOptions): Promise<void>
```

Creates and displays a popup with the specified content. This API uses a promise to return the result.

> **NOTE:** 
> 
> - If an invalid **target** is provided, the popup will not be displayed.
> 
> - You must maintain the provided **content**, on which [updatePopup](#updatepopup) and [closePopup](#closepopup) rely to identify the target popup.
> 
> - If your **wrapBuilder** includes other components (such as [Popup](arkts-arkui-arkui-advanced-popup.md) or [Chip](arkts-arkui-arkui-advanced-chip.md)), the [ComponentContent](arkts-arkui-componentcontent-c.md)constructor must include four parameters, and the **options** parameter must be
> **{ nestingBuilderSupported: true }**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the popup. |
| target | [TargetInfo](arkts-arkui-arkui-uicontext-targetinfo-i.md) | Yes | Information about the target component to bind. |
| options | [PopupCommonOptions](../arkts-components/arkts-arkui-common-comp-popupcommonoptions-i.md) | No | Style of the popup. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103302](../errorcode-promptAction.md#103302-custom-dialog-box-already-exists) | The ComponentContent already exists. |
| [103304](../errorcode-promptAction.md#103304-target-id-not-found) | The targetId does not exist. |
| [103305](../errorcode-promptAction.md#103305-node-specified-by-targetid-not-mounted-on-the-component-tree) | The node of targetId is not in the component tree. |

**Examples**

This example demonstrates how to display, update, and close a popup using the openPopup, updatePopup, and closePopup APIs.

```TypeScript
import { ComponentContent, FrameNode } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

interface PopupParam {
  updateFunc?: () => void;
  closeFunc?: () => void;
}

export function showPopup(context: UIContext, uniqueId: number, contentNode: ComponentContent<PopupParam>,
  popupParam: PopupParam) {
  const promptAction = context.getPromptAction();
  let frameNode: FrameNode | null = context.getFrameNodeByUniqueId(uniqueId);
  let targetId = frameNode?.getFirstChild()?.getUniqueId();
  promptAction.openPopup(contentNode, { id: targetId }, {
    radius: 16,
    mask: { color: Color.Pink },
    enableArrow: true,
  })
    .then(() => {
      console.info('openPopup success');
    })
    .catch((err: BusinessError) => {
      console.error('openPopup error: ' + err.code + ' ' + err.message);
    })
  popupParam.updateFunc = () => {
    promptAction.updatePopup(contentNode, {
      enableArrow: false
    }, true)
      .then(() => {
        console.info('updatePopup success');
      })
      .catch((err: BusinessError) => {
        console.error('updatePopup error: ' + err.code + ' ' + err.message);
      })
  }
  popupParam.closeFunc = () => {
    promptAction.closePopup(contentNode)
      .then(() => {
        console.info('closePopup success');
      })
      .catch((err: BusinessError) => {
        console.error('closePopup error: ' + err.code + ' ' + err.message);
      })
  }
}

@Builder
function buildText(param?: PopupParam) {
  Column() {
    Text('popup')
    Button('Update Popup')
      .fontSize(20)
      .onClick(() => {
        param?.updateFunc?.();
      })
    Button('Close Popup')
      .fontSize(20)
      .onClick(() => {
        param?.closeFunc?.();
      })
  }
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('Open Popup')
        .fontSize(20)
        .onClick(() => {
          let context = this.getUIContext();
          const popupParam: PopupParam = {};
          const contentNode = new ComponentContent(context, wrapBuilder(buildText), popupParam);
          showPopup(context, this.getUniqueId(), contentNode, popupParam);
        })
    }
  }
}
```

## openToast

```TypeScript
openToast(options: promptAction.ShowToastOptions): Promise<number>
```

Displays a toast. This API uses a promise to return the toast ID for use with **closeToast**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md) | Yes | Toast configuration options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise that returns the toast ID for use with **closeToast**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

This example demonstrates how to display and close a toast by calling openToast and closeToast.

```TypeScript
import { PromptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State toastId: number = 0;
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('OpenToast')
        .height(100)
        .onClick(() => {
          this.promptAction.openToast({
            message: 'Toast Message',
            duration: 10000,
          }).then((toastId: number) => {
            this.toastId = toastId;
          })
            .catch((error: BusinessError) => {
              console.error(`openToast error code is ${error.code}, message is ${error.message}`);
            })
        })
      Blank().height(50)
      Button('Close Toast')
        .height(100)
        .onClick(() => {
          try {
            this.promptAction.closeToast(this.toastId);
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`CloseToast error code is ${code}, message is ${message}`);
          };
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

## presentCustomDialog

```TypeScript
presentCustomDialog(builder: CustomBuilder | CustomBuilderWithId, controller?: promptAction.DialogController,
    options?: promptAction.DialogOptions): Promise<number>
```

Creates and displays a custom dialog box. This API uses a promise to return the dialog box ID for use with **closeCustomDialog**.

The dialog box ID can be included in the dialog box content for related operations. A dialog box controller can be bound to the custom dialog box, allowing for subsequent control of the dialog box through the controller.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md) &#124; [CustomBuilderWithId](arkts-arkui-custombuilderwithid-t.md) | Yes | Content of the custom dialog box. |
| controller | [promptAction.DialogController](arkts-arkui-promptaction-dialogcontroller-c.md) | No | Controller of the custom dialog box. |
| options | [promptAction.DialogOptions](arkts-arkui-promptaction-dialogoptions-i.md) | No | Style of the custom dialog box.<br> Note: If both [isModal](arkts-arkui-promptaction-basedialogoptions-i.md) and [showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md) in **BaseDialogOptions** are set to **true**, only **showInSubWindow** takes effect. In this case, the non-modal dialog box is displayed without mask in the subwindow. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise Promise used to return the custom dialog box ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { PromptAction, promptAction } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local message: string = "hello";
  private ctx: UIContext = this.getUIContext();
  private promptAction: PromptAction = this.ctx.getPromptAction();
  private dialogController: promptAction.DialogController = new promptAction.DialogController();

  private customDialogComponentId: number = 0;
  @Builder customDialogComponent() {
    Column() {
      Text(this.message).fontSize(30)
      Row({ space: 10 }) {
        Button("Close by DialogId").onClick(() => {
          this.promptAction.closeCustomDialog(this.customDialogComponentId);
        })
        Button("Close by DialogController").onClick(() => {
          this.dialogController.close();
        })
      }
    }.height(200).padding(5).justifyContent(FlexAlign.SpaceBetween)
  }

  @Builder customDialogComponentWithId(dialogId: number) {
    Column() {
      Text(this.message).fontSize(30)
      Row({ space: 10 }) {
        Button("Close by DialogId").onClick(() => {
          this.promptAction.closeCustomDialog(dialogId);
        })
        Button("Close by DialogController").onClick(() => {
          this.dialogController.close();
        })
      }
    }.height(200).padding(5).justifyContent(FlexAlign.SpaceBetween)
  }

  build() {
    Row() {
      Column({ space: 10 }) {
        Button('presentCustomDialog')
          .fontSize(20)
          .onClick(() => {
            this.promptAction.presentCustomDialog(() => {
              this.customDialogComponent()
            }, this.dialogController)
              .then((dialogId: number) => {
                this.customDialogComponentId = dialogId;
              })
              .catch((err: BusinessError) => {
                console.error("presentCustomDialog error: " + err.code + " " + err.message);
              })
          })
        Button('presentCustomDialog with id')
          .fontSize(20)
          .onClick(() => {
            this.promptAction.presentCustomDialog((dialogId: number) => {
              this.customDialogComponentWithId(dialogId)
            }, this.dialogController)
              .catch((err: BusinessError) => {
                console.error("presentCustomDialog with id error: " + err.code + " " + err.message);
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

## showActionMenu

```TypeScript
showActionMenu(options: promptAction.ActionMenuOptions, callback: promptAction.ActionMenuSuccessResponse): void
```

Shows an action menu in the given settings. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [showActionMenu](#showactionmenu)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | Yes | Action menu options. |
| callback | [promptAction.ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md) | Yes | Callback used to return the action menu response result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

```TypeScript
import { PromptAction, promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showActionMenu')
        .onClick(() => {
          try {
            this.promptAction.showActionMenu({
              title: 'Title Info',
              buttons: [
                {
                  text: 'item1',
                  color: '#666666'
                },
                {
                  text: 'item2',
                  color: '#000000'
                }
              ]
            }, (err: BusinessError, data: promptAction.ActionMenuSuccessResponse) => {
              if (err) {
                console.error('showActionMenu err: ' + err);
                return;
              }
              console.info('showActionMenu success callback, click button: ' + data.index);
            });
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`showActionMenu args error code is ${code}, message is ${message}`);
          };
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

This example demonstrates how to display an action menu and return the action menu response result through a promise using the showActionMenu API.

```TypeScript
import { PromptAction } from '@kit.ArkUI';
@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showActionMenu')
        .onClick(() => {
          this.promptAction.showActionMenu({
            title: 'showActionMenu Title Info',
            buttons: [
              {
                text: 'item1',
                color: '#666666'
              },
              {
                text: 'item2',
                color: '#000000'
              },
            ]
          })
            .then(data => {
              console.info('showActionMenu success, click button: ' + data.index);
            })
            .catch((err: Error) => {
              console.error('showActionMenu error: ' + err);
            })
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

This example demonstrates how to display an action menu and return the action menu response result using the showActionMenu API.

```TypeScript
import { PromptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showActionMenu')
        .onClick(() => {
          try {
            this.promptAction.showActionMenu({
              title: 'Title Info',
              buttons: [
                {
                  text: 'item1',
                  color: '#666666'
                },
                {
                  text: 'item2',
                  color: '#000000'
                }
              ]
            }, { index: 0 });
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`showActionMenu args error code is ${code}, message is ${message}`);
          }
          ;
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

<a id="showactionmenu-1"></a>

## showActionMenu

```TypeScript
showActionMenu(options: promptAction.ActionMenuOptions, callback: AsyncCallback<promptAction.ActionMenuSuccessResponse>): void
```

Creates and displays an action menu. This API uses an asynchronous callback to return the result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | Yes | Action menu options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[promptAction.ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md)&gt; | Yes | Callback used to return the result. On success, **err** is **undefined** and **data** contains the action menu response. On failure, **err** provides error details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

See [showActionMenu](#showactionmenu)

<a id="showactionmenu-2"></a>

## showActionMenu

```TypeScript
showActionMenu(options: promptAction.ActionMenuOptions): Promise<promptAction.ActionMenuSuccessResponse>
```

Creates and displays an action menu. This API uses a promise to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | Yes | Action menu options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[promptAction.ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md)&gt; | callback - Promise that returns the action menu response. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

This example demonstrates how to display an action menu and return the action menu response result through a promise using the showActionMenu API.

```TypeScript
import { PromptAction } from '@kit.ArkUI';
@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showActionMenu')
        .onClick(() => {
          this.promptAction.showActionMenu({
            title: 'showActionMenu Title Info',
            buttons: [
              {
                text: 'item1',
                color: '#666666'
              },
              {
                text: 'item2',
                color: '#000000'
              },
            ]
          })
            .then(data => {
              console.info('showActionMenu success, click button: ' + data.index);
            })
            .catch((err: Error) => {
              console.error('showActionMenu error: ' + err);
            })
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

## showDialog

```TypeScript
showDialog(options: promptAction.ShowDialogOptions, callback: AsyncCallback<promptAction.ShowDialogSuccessResponse>): void
```

Creates and displays a dialog box. This API uses an asynchronous callback to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md) | Yes | Dialog box configuration options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[promptAction.ShowDialogSuccessResponse](arkts-arkui-promptaction-showdialogsuccessresponse-i.md)&gt; | Yes | Callback used to return the result. On success, **err** is **undefined** and **data** contains the dialog box response. On failure, **err** provides error details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

This example demonstrates how to display a dialog box and return the dialog box response result using the showDialog API.

```TypeScript
import { PromptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showDialog')
        .onClick(() => {
          try {
            this.promptAction.showDialog({
              title: 'showDialog Title Info',
              message: 'Message Info',
              buttons: [
                {
                  text: 'button1',
                  color: '#000000'
                },
                {
                  text: 'button2',
                  color: '#000000'
                }
              ]
            }, (err, data) => {
              if (err) {
                console.error('showDialog err: ' + err);
                return;
              }
              console.info('showDialog success callback, click button: ' + data.index);
            });
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`showDialog args error code is ${code}, message is ${message}`);
          };
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

<a id="showdialog-1"></a>

## showDialog

```TypeScript
showDialog(options: promptAction.ShowDialogOptions): Promise<promptAction.ShowDialogSuccessResponse>
```

Creates and displays a dialog box. This API uses a promise to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md) | Yes | Dialog box configuration options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[promptAction.ShowDialogSuccessResponse](arkts-arkui-promptaction-showdialogsuccessresponse-i.md)&gt; | Promise that returns the dialog box response. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

This example demonstrates how to display a dialog box and return the dialog box response result through a promise using the showDialog API.

```TypeScript
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showDialog')
        .onClick(() => {
          this.promptAction.showDialog({
            title: 'Title Info',
            message: 'Message Info',
            buttons: [
              {
                text: 'button1',
                color: '#000000'
              },
              {
                text: 'button2',
                color: '#000000'
              }
            ],
          })
            .then(data => {
              console.info('showDialog success, click button: ' + data.index);
            })
            .catch((err: Error) => {
              console.error('showDialog error: ' + err);
            })
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

## showToast

```TypeScript
showToast(options: promptAction.ShowToastOptions): void
```

Creates and displays a toast.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [promptAction.ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md) | Yes | Toast configuration options |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

This example demonstrates how to display a toast by calling showToast.

```TypeScript
import { PromptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showToast')
        .onClick(() => {
          try {
            this.promptAction.showToast({
              message: 'Message Info',
              duration: 2000
            });
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`showToast args error code is ${code}, message is ${message}`);
          };
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

## updateCustomDialog

```TypeScript
updateCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options: promptAction.BaseDialogOptions): Promise<void>
```

Updates a custom dialog box corresponding to **dialogContent**. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dialogContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content of the custom dialog box. |
| options | [promptAction.BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) | Yes | Dialog box style. Currently, only **alignment**, **offset**, **autoCancel**, and **maskColor** can be updated. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | Dialog content not found. The ComponentContent cannot be found. |

**Examples**

This example demonstrates how to dynamically adjust the position of an open custom dialog using updateCustomDialog.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent } from '@kit.ArkUI';

class Params {
  text: string = "";

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
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = "hello";

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText), new Params(this.message));
            promptAction.openCustomDialog(contentNode)
              .then(() => {
                console.info('succeeded');
              })
              .catch((error: BusinessError) => {
                console.error(`updateCustomDialog args error code is ${error.code}, message is ${error.message}`);
              })

            setTimeout(() => {
              promptAction.updateCustomDialog(contentNode, { alignment: DialogAlignment.CenterEnd })
                .then(() => {
                  console.info('succeeded');
                })
                .catch((error: BusinessError) => {
                  console.error(`updateCustomDialog args error code is ${error.code}, message is ${error.message}`);
                })
            }, 2000); // Automatically update the dialog box position after 2 seconds.
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

## updateMenu

```TypeScript
updateMenu<T extends Object>(content: ComponentContent<T>, options: MenuOptions, partialUpdate?: boolean): Promise<void>
```

Updates the style of the menu corresponding to the provided **content**. This API uses a promise to return the result.

> **NOTE:** 
> 
> - Updating for the following is not supported: **showInSubWindow**, **preview**, **previewAnimationOptions**,
> **transition**, **onAppear**, **aboutToAppear**, **onDisappear**, **aboutToDisappear**, **onWillAppear**,
> **onDidAppear**, **onWillDisappear**, and **onDidDisappear**.
> 
> - The mask style can be updated by configuring [MenuMaskType](../arkts-components/arkts-arkui-common-comp-menumasktype-i.md). However, this API does not support mask presence toggling (that is, switching the mask from non-existent to existent or vice versa) by setting a boolean value.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the menu. |
| options | [MenuOptions](../arkts-components/arkts-arkui-common-comp-menuoptions-i.md) | Yes | Style of the menu.<br>**NOTE:** <br>1. Updating for the following is not supported: **showInSubWindow**, **preview**, **previewAnimationOptions**, **transition**, **onAppear**, **aboutToAppear**, **onDisappear**, **aboutToDisappear**, **onWillAppear**, **onDidAppear**, **onWillDisappear**, and **onDidDisappear**.<br>2. The mask style can be updated by configuring [MenuMaskType](../arkts-components/arkts-arkui-common-comp-menumasktype-i.md). However, this API does not support mask presence toggling (that is, switching the mask from non-existent to existent or vice versa) by setting a boolean value. |
| partialUpdate | boolean | No | Whether to update the menu in incremental mode. Default value: **false**.<br> **NOTE:** <br>1. **true**: incremental update, where the specified properties in **options** are updated, and other properties stay at their current value.<br>2. **false**: full update, where all properties except those specified in **options** are restored to default values. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | The ComponentContent cannot be found. |

**Examples**

This example demonstrates how to update the arrow style of a menu using updateMenu.

```TypeScript
import { ComponentContent, FrameNode } from '@kit.ArkUI';

export function doSomething(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  showMenu(context, uniqueId, contentNode);
}

@Builder
function MyMenu() {
  Column() {
    Menu() {
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "Menu item 1" })
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "Menu item 2" })
    }
  }
  .width('80%')
  .padding('20lpx')
}

export function showMenu(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  const promptAction = context.getPromptAction();
  let frameNode: FrameNode | null = context.getFrameNodeByUniqueId(uniqueId);
  let frameNodeTarget = frameNode?.getFirstChild();
  frameNodeTarget = frameNodeTarget?.getChild(0);
  let targetId = frameNodeTarget?.getUniqueId();
  promptAction.openMenu(contentNode, { id: targetId }, {
    enableArrow: true,
  });
  setTimeout(() => {
    promptAction.updateMenu(contentNode, {
      enableArrow: false,
    });
  }, 2000);
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('OpenMenu', { type: ButtonType.Normal, stateEffect: true })
        .borderRadius('16lpx')
        .width('80%')
        .margin(10)
        .onClick(() => {
          let context = this.getUIContext();
          const contentNode = new ComponentContent(context, wrapBuilder(MyMenu));
          doSomething(context, this.getUniqueId(), contentNode);
        })
    }
  }
}
```

## updatePopup

```TypeScript
updatePopup<T extends Object>(content: ComponentContent<T>, options: PopupCommonOptions, partialUpdate?: boolean): Promise<void>
```

Updates the style of the popup corresponding to the provided **content**. This API uses a promise to return the result.

> **NOTE:** 
> 
> Updating the following properties is not supported: **showInSubWindow**, **focusable**, **onStateChange**, **onWillDismiss**, and **transition**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content displayed in the popup. |
| options | [PopupCommonOptions](../arkts-components/arkts-arkui-common-comp-popupcommonoptions-i.md) | Yes | Style of the popup.<br> **NOTE:** <br> Updating the following properties is not supported: **showInSubWindow**, **focusable**, **onStateChange**, **onWillDismiss**, and **transition**. |
| partialUpdate | boolean | No | Whether to update the popup in incremental mode.<br> Default value: **false**<br> **NOTE:** <br> **true**: Incremental update. Only specified attributes in **options** are updated, and the other attributes retain their current values. If the attribute value passed in **options** is invalid or **undefined**, the attribute is not updated.<br> **false**: Full update. Specified attributes in **options** are updated, and the other attributes are restored to their default values. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [103301](../errorcode-promptAction.md#103301-dialog-content-error) | The ComponentContent is incorrect. |
| [103303](../errorcode-promptAction.md#103303-custom-dialog-box-not-found) | The ComponentContent cannot be found. |

**Examples**

See the example for [openPopup](#openpopup).
