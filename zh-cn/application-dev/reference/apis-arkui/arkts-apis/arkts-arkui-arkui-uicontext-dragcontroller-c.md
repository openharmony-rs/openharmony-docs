# DragController

提供发起主动拖拽的能力，当应用接收到触摸或长按等事件时可以主动发起拖拽的动作，并在其中携带拖拽信息。

> **说明：**
> 
> 以下API需先使用UIContext中的[getDragController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller)方法获取DragController实例，再通过此实例调用对应方法。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

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

当使用[startDataLoading](../arkts-components/arkts-arkui-dragevent-i.md#startdataloading)获取拖拽数据时，可调用该接口取消数据传输。仅可在拖拽释放后调用。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 拖拽数据的标识，用于区分每次拖拽。key可通过startDataLoading接口获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [190004](../errorcode-drag-event.md#190004-操作失败) | Operation failed. |

## createDragAction

```TypeScript
createDragAction(customArray: Array<CustomBuilder | DragItemInfo>, dragInfo: dragController.DragInfo): dragController.DragAction
```

创建拖拽的Action对象，需要显式指定拖拽背板图（可多个），以及拖拽的数据，跟手点等信息；当通过一个已创建的Action对象发起的拖拽未结束时，无法再次创建新的Action对象，接口会抛出异常；当Action对象的生命周期结束 后，注册在该对象上的回调函数会失效，因此需要在一个尽量长的作用域下持有该对象，并在每次发起拖拽前通过createDragAction返回新的对象覆盖旧值。

> **说明：**
> 
> 建议控制传递的拖拽背板数量，传递过多容易导致拖起的效率问题。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customArray | Array&lt;[CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) \| [DragItemInfo](../arkts-components/arkts-arkui-dragiteminfo-i.md)&gt; | 是 | 拖拽发起后跟手效果所拖拽的对象。 |
| dragInfo | dragController.DragInfo | 是 | 拖拽信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| dragController.DragAction | DragAction** object, which is used to subscribe to drag state changes and start the drag service. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

**示例**

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
        // 获取UIContext实例
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

调用this.getUIContext().getSharedLocalStorage()获取上下文，再获取DragController对象以执行后续拖拽操作。

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
      Button('多对象dragAction customBuilder拖拽').onTouch((event?: TouchEvent) => {
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
                  // 拖拽结束后，清空拖拽背板数组并取消状态监听。
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

当组件的类型与配置的[allowDrop](../arkts-components/arkts-arkui-commonmethod-c.md#allowdrop)无交集时可显示禁用角标。通常，当组件可以接收或处理拖拽数据，或当它返回DragBehavior.COPY向系统声明数据以复制方式 处理时，拖拽对象会显示加号及数据编号的角标。如果返回DragBehavior.MOVE以向系统声明数据以剪切方式处理，拖拽对象将只显示数据编号的角标。当目标进行拖拽时，若系统决定或组件显式声明无法处理拖拽数据，可通过该方法检查是否 应显示拖拽禁止角标。该接口暂不支持[UIExtension](arkts-arkui-uiextension.md)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 当组件的类型与配置的[allowDrop](../arkts-components/arkts-arkui-commonmethod-c.md#allowdrop)无交集时可显示禁用角标，当目标进行拖拽时，通过 enableDropDisallowedBadge方法检查是否显示拖拽禁止角标。true表示显示拖拽禁止角标，false表示不显示拖拽禁止角标。默认值为false。 |

**示例**

在EntryAbility.ets中调用enableDropDisallowedBadge接口，设置enabled参数为true。

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

在Index.ets中拖拽图标icon至下方空白区域，显示拖拽禁止角标。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column({ space: 20 }) {
      // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件
      Image($r('app.media.startIcon'))
        .width(120)
        .height(120)
      Text('这里是不能落入区域')
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

主动发起拖拽能力，传入拖拽发起后跟手效果所拖拽的对象以及携带拖拽信息。通过回调返回拖拽事件结果。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) \| [DragItemInfo](../arkts-components/arkts-arkui-dragiteminfo-i.md) | 是 | 拖拽发起后跟手效果所拖拽的对象。    **说明：** 不支持全局builder。如果builder中使用了 Image组件，应尽量开启同步加载，即配置Image的syncLoad为true。该builder只用于生成当次拖拽中显示的图 片。builder的根组件宽高为0时，无法生成拖拽显示的图片导致拖拽失败。builder的修改不会同步到当前正在拖拽的图片，对builder的修改需要在下一次拖拽时生效。 |
| dragInfo | dragController.DragInfo | 是 | 拖拽信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;dragController.DragEventParam&gt; | 是 | 拖拽结束返回结果的回调   - event：拖拽事件信息，仅包括拖拽结果。   - extraParams：拖拽事件额外信息。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

**示例**

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

## executeDrag

```TypeScript
executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo)
    : Promise<dragController.DragEventParam>
```

主动发起拖拽能力，传入拖拽发起后跟手效果所拖拽的对象以及携带拖拽信息。通过Promise返回拖拽事件结果。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) \| [DragItemInfo](../arkts-components/arkts-arkui-dragiteminfo-i.md) | 是 | 拖拽发起后跟手效果所拖拽的对象。 |
| dragInfo | dragController.DragInfo | 是 | 拖拽信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;{ event: DragEvent, extraParams: string | > } Callback used to return the result. |
| Promise & lt;dragController.DragEventParam & gt; | A Promise with the drag event information.<br>**适用版本：** 12+ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

**示例**

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

返回一个代表拖拽背板的对象。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| dragController.DragPreview | DragPreview** object. It provides the API for setting the preview style. It does not work in the **OnDrop** and **OnDragEnd** callbacks. |

**示例**

请参考[animate](arkts-arkui-dragcontroller-dragpreview-c.md#animate)示例。

## notifyDragStartRequest

```TypeScript
notifyDragStartRequest(requestStatus: dragController.DragStartRequestStatus): void
```

控制应用是否可以发起拖拽。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestStatus | dragController.DragStartRequestStatus | 是 | 定义应用是否可以发起拖拽。 |

**示例**

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
    // 设置4s后才能发起拖拽
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
              // 应用数据准备阶段，无法发起拖拽
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

当目标从父组件拖拽到子组件时，通过该方法设置是否会触发父组件的onDragLeave的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 将目标从父组件拖拽到子组件时，是否会触发父组件的onDragLeave的回调。true表示触发父组件的onDragLeave的回调，false表示不触发。 |

**示例**

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
