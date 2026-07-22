# DragPreview

拖拽背板的对象，在OnDrop和OnDragEnd回调中使用不生效。

**起始版本：** 11

<!--Device-dragController-export class DragPreview--><!--Device-dragController-export class DragPreview-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## animate

```TypeScript
animate(options: AnimationOptions, handler: () =>void): void
```

设置背板蒙版颜色变化动效，在OnDrop和OnDragEnd回调中使用不生效，仅支持通过[getDragPreview()](arkts-arkui-arkui-uicontext-dragcontroller-c.md#getdragpreview)方法获取到的对象上使用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragPreview-animate(options: AnimationOptions, handler: () =>void): void--><!--Device-DragPreview-animate(options: AnimationOptions, handler: () =>void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimationOptions](arkts-arkui-arkui-drawabledescriptor-animationoptions-i.md) | 是 | 动效参数。 |
| handler | () =&gt;void | 是 | 用于修改背板蒙版颜色等属性的回调方法。 |

**示例：**

在EntryAbility.ets中获取UI上下文并保存至LocalStorage中。

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
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s',
          `Code is ${err.code}, message is ${err.message}`);
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

在Index.ets中通过this.getUIContext().getSharedLocalStorage()获取UI上下文，进而获取DragController对象实施后续操作。

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
      Button('拖拽至此处')
        .margin(10)
        .onDragEnter(() => {
          try {
            let uiContext: UIContext = this.storages?.get<UIContext>('uiContext') as UIContext;
            let previewObj: dragController.DragPreview = uiContext.getDragController().getDragPreview();
            let foregroundColor: ResourceColor = Color.Green;

            let previewAnimation: dragController.AnimationOptions = {
              curve: curves.cubicBezierCurve(0.2, 0, 0, 1),
            }
            previewObj.animate(previewAnimation, () => {
              previewObj.setForegroundColor(foregroundColor);
            });
          } catch (error) {
            let msg = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            hilog.error(0x0000, `show error code is ${code}, message is ${msg}`, '');
          }
        })
        .onDrop(() => {
          this.getUIContext().getPromptAction().showToast({ duration: 100, message: 'Drag Success', bottom: 400 })
        })
      Button('拖起').onTouch((event?: TouchEvent) => {
        if (event) {
          if (event.type == TouchType.Down) {
            let text = new unifiedDataChannel.Text()
            let unifiedData = new unifiedDataChannel.UnifiedData(text)
            let dragInfo: dragController.DragInfo = {
              pointerId: 0,
              data: unifiedData,
              extraParams: ''
            }
            let eve: DragInfo = new DragInfo();
            this.getUIContext()
              .getDragController()
              .executeDrag(() => { // 建议使用 this.getUIContext().getDragController().executeDrag()接口
                this.draggingBuilder()
              }, dragInfo, (err, eve) => {
                hilog.info(0x0000, `${JSON.stringify(err)}`, '')
                if (eve && eve.event) {
                  if (eve.event.getResult() == DragResult.DRAG_SUCCESSFUL) {
                    hilog.info(0x0000, 'success', '');
                  } else if (eve.event.getResult() == DragResult.DRAG_FAILED) {
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

设置背板蒙版颜色，在OnDrop和OnDragEnd回调中使用不生效，仅支持通过[getDragPreview()](arkts-arkui-arkui-uicontext-dragcontroller-c.md#getdragpreview)方法获取到的对象上使用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragPreview-setForegroundColor(color: ResourceColor): void--><!--Device-DragPreview-setForegroundColor(color: ResourceColor): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](arkts-arkui-resourcecolor-t.md) | 是 | 背板蒙版颜色。 |

**示例：**

请参考[animate](#animate11)。

