# DragPreview

```TypeScript
export class DragPreview
```

Implements a **DragPreview** object. This API does not work in the **OnDrop** and **OnDragEnd** callbacks.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## animate

```TypeScript
animate(options: AnimationOptions, handler: () =>void): void
```

Applies a foreground color animation to the drag preview. This API does not work in the **OnDrop** and **OnDragEnd** callbacks. It can only be used on the object obtained through the [getDragPreview()](arkts-arkui-arkui-uicontext-dragcontroller-c.md#getdragpreview) API.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimationOptions](arkts-arkui-dragcontroller-animationoptions-i.md) | Yes | Animation settings. |
| handler | () =&gt;void | Yes | Callback used to change attributes such as the background mask color. |

**Examples**

> NOTE
> 
> You are advised to use [getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the DragController object associated with the current UI context.

In the EntryAbility.ets file, obtain the UI context and save it to LocalStorage.

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window, UIContext } from '@kit.ArkUI';

let uiContext: UIContext;
let localStorage: LocalStorage = new LocalStorage('uiContext');

export default class EntryAbility extends UIAbility {
  storage: LocalStorage = localStorage;

  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
  }

  onDestroy(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', this.storage, (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s',
        `Code is ${err.code}, message is ${err.message}`);
      windowStage.getMainWindow((err, data) => {
        if (err.code) {
          console.error(`Failed to obtain the main window. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        uiContext = data.getUIContext();
        this.storage.setOrCreate<UIContext>('uiContext', uiContext);
      })
    });
  }
}
```

In the Index.ets file, call this.getUIContext().getSharedLocalStorage() to obtain the UI context and then use the DragController object obtained to perform subsequent operations.

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { dragController, curves, UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class DragInfo {
  event: DragEvent | undefined = undefined;
  extraParams: string = '';
}

@Entry()
@Component
struct DragControllerPage {
  storages = this.getUIContext().getSharedLocalStorage();

  @Builder
  draggingBuilder() {
    Column() {
      Text('DraggingBuilder')
        .fontColor(Color.White)
        .fontSize(12)
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('Drop Here')
        .margin(10)
        .onDragEnter(() => {
          try {
            let uiContext: UIContext = this.storages?.get<UIContext>('uiContext') as UIContext;
            let dragPreview: dragController.DragPreview = uiContext.getDragController().getDragPreview();
            let foregroundColor: ResourceColor = Color.Green;

            let previewAnimation: dragController.AnimationOptions = {
              curve: curves.cubicBezierCurve(0.2, 0, 0, 1),
            }
            dragPreview.animate(previewAnimation, () => {
              dragPreview.setForegroundColor(foregroundColor);
            });
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`Failed to animate drag preview. Code: ${code}, message: ${message}`);
          }
        })
        .onDrop(() => {
          this.getUIContext().getPromptAction().showToast({ duration: 100, message: 'Drag Success', bottom: 400 })
        })
      Button('Drag').onTouch((event?: TouchEvent) => {
        if (event) {
          if (event.type == TouchType.Down) {
            let text = new unifiedDataChannel.Text()
            let unifiedData = new unifiedDataChannel.UnifiedData(text)
            let dragInfo: dragController.DragInfo = {
              pointerId: 0,
              data: unifiedData,
              extraParams: ''
            }
            this.getUIContext()
              .getDragController()
              .executeDrag(() => { // You are advised to use this.getUIContext().getDragController().executeDrag().
                this.draggingBuilder()
              }, dragInfo, (err, dragEventParam) => {
                if (err) {
                  console.error(`Failed to execute drag. Code: ${err.code}, message: ${err.message}`);
                  return;
                }
                if (dragEventParam && dragEventParam.event) {
                  if (dragEventParam.event.getResult() == DragResult.DRAG_SUCCESSFUL) {
                    hilog.info(0x0000, 'success', '');
                  } else if (dragEventParam.event.getResult() == DragResult.DRAG_FAILED) {
                    hilog.info(0x0000, 'failed', '');
                   }
                 }
               })
          }
        }
      }).margin({ top: 100 })
    }
    .width('100%')
    .height('100%')
  }
}
```

## setForegroundColor

```TypeScript
setForegroundColor(color: ResourceColor): void
```

Sets the foreground color of the drag preview. This API does not work in the **OnDrop** and **OnDragEnd** callbacks. It can only be used on the object obtained through the [getDragPreview()](arkts-arkui-arkui-uicontext-dragcontroller-c.md#getdragpreview) API.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](arkts-arkui-resourcecolor-t.md) | Yes | Foreground color of the drag preview. |

**Examples**

See [animate](#animate).
