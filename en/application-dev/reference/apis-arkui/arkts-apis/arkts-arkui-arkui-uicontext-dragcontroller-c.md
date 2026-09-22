# DragController

```TypeScript
export class DragController
```

Provides APIs for initiating drag actions. When receiving a gesture event, such as a touch or long-press event, an application can initiate a drag action and carry drag information therein.

> **NOTE:** 
> 
> In the following API examples, you must first use [getDragController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) in
> **UIContext** to obtain a **DragController** instance, and then call the APIs using the obtained instance.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## cancelDataLoading

```TypeScript
cancelDataLoading(key: string): void
```

Cancels the data loading initiated by the [startDataLoading](../arkts-components/arkts-arkui-common-comp-dragevent-i.md#startdataloading) API. This API can be called only after the drag is released.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Identifier for the drag data. It is used to distinguish between different drag operations. The key can be obtained through the **startDataLoading** API. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [190004](../errorcode-drag-event.md#190004-operation-failed) | Operation failed. |

## createDragAction

```TypeScript
createDragAction(customArray: Array<CustomBuilder | DragItemInfo>, dragInfo: dragController.DragInfo): dragController.DragAction
```

Creates a drag action object for initiating drag and drop operations. You need to explicitly specify one or more drag previews, the drag data, and the drag handle point. If a drag operation initiated by an existing drag action object is not completed, no new object can be created, and calling the API will throw an exception. After the lifecycle of the drag action object ends, the callback functions registered on this object become invalid. Therefore, it is necessary to hold this object within a longer scope and replace the old value with a new object returned by **createDragAction** before each drag initiation.

> **NOTE:** 
> 
> For optimal drag and drop performance, limit the number of drag previews.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| customArray | Array&lt;[CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-common-comp-dragiteminfo-i.md)&gt; | Yes | Object to be dragged. |
| dragInfo | [dragController.DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | Yes | Drag information. |

**Return value:**

| Type | Description |
| --- | --- |
| [dragController.DragAction](arkts-arkui-dragcontroller-dragaction-i.md) | **DragAction** object, which is used to subscribe to drag state changes and start the drag service. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal handling failed. |

**Examples**

Obtain the UI context from EntryAbility.ets and save it to LocalStorage.

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
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', this.storage, (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
      windowStage.getMainWindow((err, data) => {
        if (err.code) {
          console.error(`Failed to obtain the main window. Cause:${err.message}`);
          return;
        }
        let windowClass: window.Window = data;
        uiContext = windowClass.getUIContext();
        this.storage.setOrCreate<UIContext>('uiContext', uiContext);
        // Obtain a UIContext instance.
      });
    });
  }

  onWindowStageDestroy(): void {
    // Main window is destroyed, release UI related resources
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
  }

  onForeground(): void {
    // Ability has brought to foreground
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onBackground(): void {
    // Ability has back to background
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onBackground');
  }
}
```

Call this.getUIContext().getSharedLocalStorage() to obtain the context, and then obtain the DragController object to perform subsequent drag operations.

```TypeScript
import { dragController, UIContext } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry()
@Component
struct DragControllerPage {
  private dragAction: dragController.DragAction | null = null;
  customBuilders: Array<CustomBuilder | DragItemInfo> = new Array<CustomBuilder | DragItemInfo>();
  storages = this.getUIContext().getSharedLocalStorage();

  @Builder
  DraggingBuilder() {
    Column() {
      Text('DraggingBuilder')
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('Drag Multiple Objects').onTouch((event?: TouchEvent) => {
        if (event) {
          if (event.type == TouchType.Down) {
            console.info('multi drag Down by listener');
            this.customBuilders.push(() => {
              this.DraggingBuilder()
            });
            this.customBuilders.push(() => {
              this.DraggingBuilder()
            });
            this.customBuilders.push(() => {
              this.DraggingBuilder()
            });
            let text = new unifiedDataChannel.Text();
            let unifiedData = new unifiedDataChannel.UnifiedData(text);
            let dragInfo: dragController.DragInfo = {
              pointerId: 0,
              data: unifiedData,
              extraParams: ''
            };
            try {
              this.dragAction = this.getUIContext().getDragController().createDragAction(this.customBuilders, dragInfo);
              if (!this.dragAction) {
                console.info('listener dragAction is null');
                return;
              }
              this.dragAction.on('statusChange', (dragAndDropInfo) => {
                if (dragAndDropInfo.status == dragController.DragStatus.STARTED) {
                  console.info('drag has start');
                } else if (dragAndDropInfo.status == dragController.DragStatus.ENDED) {
                  console.info('drag has end');
                  if (!this.dragAction) {
                    return;
                  }
                  // After the drag operation is complete, clear the drag preview array and cancel the status listener.
                  this.customBuilders.splice(0, this.customBuilders.length);
                  this.dragAction.off('statusChange');
                }
              });
              this.dragAction.startDrag().then(() => {
              }).catch((err: BusinessError) => {
                console.error(`Failed to start drag. Code: ${err.code}, message: ${err.message}`);
              });
            } catch (err) {
              const error = err as BusinessError;
              console.error(`Failed to create dragAction. Code: ${error.code}, message: ${error.message}`);
            }
          }
        }
      }).margin({ top: 20 })
    }
    .width('100%')
    .height('100%')
  }
}
```

## enableDropDisallowedBadge

```TypeScript
enableDropDisallowedBadge(enabled: boolean): void
```

Specifies whether to enable the display of a disallowed badge when dragged content is incompatible with a component's configured [allowDrop](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#allowdrop) types. When a component can accept or process dragged dataor returns **DragBehavior.COPY** to indicate copy mode processing, the drag preview shows a plus icon with data count badge. When the component returns **DragBehavior.MOVE** to indicate cut mode processing, only the data count badge appears. When this feature is enabled, the system automatically displays a disallowed badge during drag operations if the dragged data types are incompatible with the target component's allowed drop types. This API currently does not support [UIExtension](arkts-arkui-arkui-uiextension.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable the display of a disallowed badge when dragged content is incompatible with a component's configured [allowDrop](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#allowdrop) types. The value **true** means to enable the display of a disallowed badge, and **false** means the opposite. The default value is **false**. |

**Examples**

This example demonstrates the function of displaying a drag-disallowed badge when a drag object passes over a target area where dropping is not allowed, implemented via the enableDropDisallowedBadge API.

Call the enableDropDisallowedBadge API in EntryAbility.ets and set the enabled parameter to true.

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window, UIContext } from '@kit.ArkUI';

 export default class EntryAbility extends UIAbility {
   onWindowStageCreate(windowStage: window.WindowStage): void {
       windowStage.loadContent('pages/Index', (err, data) => {
         if (err.code) {
         return;
       }
       windowStage.getMainWindow((err, data) => {
         if (err.code) {
           return;
         }
         let windowClass: window.Window = data;
         let uiContext: UIContext = windowClass.getUIContext();
         uiContext.getDragController().enableDropDisallowedBadge(true);
     });
   });
 }
}
```

Drag the icon to the blank area below in Index.ets. The drag-disallowed badge is displayed.

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column({ space: 20 }) {
      // Replace $r('app.media.startIcon') with the image resource file you use.
      Image($r('app.media.startIcon'))
        .width(120)
        .height(120)
      Text ('Invalid drop zone.')
      Column()
        .width('100%')
        .layoutWeight(1)
        .allowDrop(null)
        .onDrop(() => {
        })
    }.width('100%')
  }
}
```

## executeDrag

```TypeScript
executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo,
    callback: AsyncCallback<dragController.DragEventParam>): void
```

Initiates a drag action, with the object to be dragged and the drag information passed in. This API uses a callback to return the drag event result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-common-comp-dragiteminfo-i.md) | Yes | Object to be dragged.<br> **NOTE:** <br>The global builder is not supported. If the [Image](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) component is used in the builder, enable synchronous loading, that is, set the [syncLoad](../arkts-components/arkts-arkui-image-comp-attribute.md#syncload) attribute of the component to **true**. The builder is used only to generate the image displayed during the current dragging. If the root component of the builder has zero width or height, it will cause failure in drag image generation, which in turn breaks the entire drag operation. Changes to the builder, if any, apply to the next dragging, but not to the current dragging. |
| dragInfo | [dragController.DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | Yes | Drag information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[dragController.DragEventParam](arkts-arkui-dragcontroller-drageventparam-i.md)&gt; | Yes | Callback used to return the result.<br>- **event**: drag event information that includes only the drag result.<br>- **extraParams**: extra information about the drag event.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal handling failed. |

**Examples**

```TypeScript
import { dragController } from '@kit.ArkUI';
import { unifiedDataChannel } from '@kit.ArkData';

class DragInfo {
  event: DragEvent | undefined = undefined;
  extraParams: string = '';
}

@Entry
@Component
struct DragControllerPage {
  @Builder
  DraggingBuilder() {
    Column() {
      Text('DraggingBuilder')
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('touch to execute drag')
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              let text = new unifiedDataChannel.Text();
              let unifiedData = new unifiedDataChannel.UnifiedData(text);

              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              };
              this.getUIContext().getDragController().executeDrag(() => {
                this.DraggingBuilder()
              }, dragInfo, (err, dragEventParam) => {
                if (dragEventParam.event) {
                  if (dragEventParam.event.getResult() == DragResult.DRAG_SUCCESSFUL) {
                    // ...
                  } else if (dragEventParam.event.getResult() == DragResult.DRAG_FAILED) {
                    // ...
                  }
                }
              });
            }
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

<a id="executedrag-1"></a>

## executeDrag

```TypeScript
executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo)
    : Promise<dragController.DragEventParam>
```

Initiates a drag action, with the object to be dragged and the drag information passed in. This API uses a promise to return the drag event result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-common-comp-dragiteminfo-i.md) | Yes | Object to be dragged. |
| dragInfo | [dragController.DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | Yes | Drag information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;{ event: DragEvent, extraParams: string }&gt; | Callback used to return the result.<br>- **event**: drag event information that includes only the drag result. <br>- **extraParams**: extra information about the drag event.<br>**Since:** 11 |
| Promise&lt;[dragController.DragEventParam](arkts-arkui-dragcontroller-drageventparam-i.md)&gt; | A Promise with the drag event information.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal handling failed. |

**Examples**

```TypeScript
import { dragController } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';
import { unifiedDataChannel } from '@kit.ArkData';

class DragInfo {
  event: DragEvent | undefined = undefined;
  extraParams: string = '';
}

@Entry
@Component
struct DragControllerPage {
  @State pixmap: image.PixelMap | null = null;

  @Builder
  DraggingBuilder() {
    Column() {
      Text('DraggingBuilder')
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  @Builder
  PixmapBuilder() {
    Column() {
      Text('PixmapBuilder')
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('touch to execute drag')
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              let text = new unifiedDataChannel.Text();
              let unifiedData = new unifiedDataChannel.UnifiedData(text);

              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              };
              let pixmapBuilder: CustomBuilder = (): void => {
                this.PixmapBuilder()
              };
              this.getUIContext().getComponentSnapshot().createFromBuilder(pixmapBuilder).then((pixelMap: image.PixelMap) => {
                this.pixmap = pixelMap;
                let dragItemInfo: DragItemInfo = {
                  pixelMap: this.pixmap,
                  builder: () => {
                    this.DraggingBuilder()
                  },
                  extraInfo: 'DragItemInfoTest'
                };
                this.getUIContext()
                  .getDragController()
                  .executeDrag(dragItemInfo, dragInfo)
                  .then((dragEventParam) => {
                    if (dragEventParam.event.getResult() == DragResult.DRAG_SUCCESSFUL) {
                      // ...
                    } else if (dragEventParam.event.getResult() == DragResult.DRAG_FAILED) {
                      // ...
                    }
                  })
                  .catch((err: Error) => {
                  })
              });
            }
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## getDragPreview

```TypeScript
getDragPreview(): dragController.DragPreview
```

Obtains the **DragPreview** object, which represents the preview displayed during a drag operation.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [dragController.DragPreview](arkts-arkui-dragcontroller-dragpreview-c.md) | **DragPreview** object. It provides the API for setting the preview style. It does not work in the **OnDrop** and **OnDragEnd** callbacks. |

**Examples**

See the example for animate.

## notifyDragStartRequest

```TypeScript
notifyDragStartRequest(requestStatus: dragController.DragStartRequestStatus): void
```

Controls whether the application can initiate a drag operation.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| requestStatus | [dragController.DragStartRequestStatus](arkts-arkui-dragcontroller-dragstartrequeststatus-e.md) | Yes | Whether the application can initiate a drag operation. |

**Examples**

```TypeScript
// xxx.ets
import { unifiedDataChannel } from '@kit.ArkData';
import { image } from '@kit.ImageKit';
import { dragController } from '@kit.ArkUI';

@Entry
@Component
struct NormalEts {
  @State finished: boolean = false;
  @State timeout1: number = 1;
  @State pixmap: image.PixelMap | undefined = undefined;
  @State unifiedData1: unifiedDataChannel.UnifiedData | undefined = undefined;
  @State previewData: DragItemInfo | undefined = undefined;

  loadData() {
    // Set a 4-second delay before initiating a drag action.
    let timeout = setTimeout(() => {
      this.getUIContext().getComponentSnapshot().get('image1', (error: Error, pixmap: image.PixelMap) => {
        if (error) {
          return;
        }
        this.pixmap = pixmap;
        this.previewData = {
          pixelMap: this.pixmap
        };
      });

      let data: unifiedDataChannel.Image = new unifiedDataChannel.Image();
      data.imageUri = 'app.media.startIcon';
      let unifiedData = new unifiedDataChannel.UnifiedData(data);
      this.unifiedData1 = unifiedData;
      this.finished = true;

      this.getUIContext().getDragController().notifyDragStartRequest(dragController.DragStartRequestStatus.READY);
    }, 4000);
    this.timeout1 = timeout;
  }

  build() {
    Column({ space: 20 }) {
      Image($r('app.media.startIcon'))
        .width(150)
        .height(150)
        .id('image1')
        .draggable(true)
        .dragPreview(this.previewData)
        .onPreDrag((status: PreDragStatus) => {
          if (status == PreDragStatus.PREPARING_FOR_DRAG_DETECTION) {
            this.loadData();
          } else {
            clearTimeout(this.timeout1);
          }
        })
        .onDragStart((event: DragEvent) => {
          if (this.finished == false) {
            this.getUIContext()
              .getDragController()
              // In the application data preparation phase, a drag action cannot be initiated.
              .notifyDragStartRequest(dragController.DragStartRequestStatus.WAITING);
          } else {
            event.setData(this.unifiedData1);
          }
        })
        .onDragEnd(() => {
          this.finished = false;
        })
    }
    .width('100%')
    .height(400)
  }
}
```

## setDragEventStrictReportingEnabled

```TypeScript
setDragEventStrictReportingEnabled(enable: boolean): void
```

Sets whether the **onDragLeave** callback of the parent component is triggered when an item is dragged from the parent to the child component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether the **onDragLeave** callback of the parent component is triggered when an item is dragged from the parent to the child component. The value **true** means the **onDragLeave** callback of the parent component is triggered, and **false** means the opposite. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window, UIContext } from '@kit.ArkUI';

 export default class EntryAbility extends UIAbility {
   onWindowStageCreate(windowStage: window.WindowStage): void {
       windowStage.loadContent('pages/Index', (err, data) => {
         if (err.code) {
         return;
       }
       windowStage.getMainWindow((err, data) => {
         if (err.code) {
           return;
         }
         let windowClass: window.Window = data;
         let uiContext: UIContext = windowClass.getUIContext();
         uiContext.getDragController().setDragEventStrictReportingEnabled(true);
     });
   });
 }
}
```
