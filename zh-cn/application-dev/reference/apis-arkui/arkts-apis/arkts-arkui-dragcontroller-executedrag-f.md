# executeDrag

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## executeDrag

```TypeScript
function executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo,
    callback: AsyncCallback<DragEventParam>): void
```

Execute a drag event.

**起始版本：** 10

**废弃版本：** 18

**替代接口：** executeDrag

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-dragController-function executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo,    callback: AsyncCallback<DragEventParam>): void--><!--Device-dragController-function executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo,    callback: AsyncCallback<DragEventParam>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) \| DragItemInfo | 是 | Object used for prompts displayed when the object is dragged. |
| dragInfo | [DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | 是 | Information about the drag event. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DragEventParam&gt; | 是 | Callback that contains the drag event information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

**示例：**

推荐通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getDragController](arkts-apis-uicontext-uicontext.md#getdragcontroller11)方法获取当前UI上下文关联的DragController对象。

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
  @State text: string = ''

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
      Button('touch to execute drag')
        .margin(10)
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              let text = new unifiedDataChannel.PlainText();
              text.textContent = 'drag text'
              text.abstract = 'abstract'
              let unifiedData = new unifiedDataChannel.UnifiedData(text)

              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              }
              let eve: DragInfo = new DragInfo();
              this.getUIContext().getDragController().executeDrag(() => {
                this.DraggingBuilder()
              }, dragInfo, (err, eve) => { // 建议使用 this.getUIContext().getDragController().executeDrag()接口
                if (eve.event) {
                  if (eve.event.getResult() == DragResult.DRAG_SUCCESSFUL) {
                    // ...
                  } else if (eve.event.getResult() == DragResult.DRAG_FAILED) {
                    // ...
                  }
                }
              })
            }
          }
        })
      Text(this.text)
        .height(100)
        .width(150)
        .margin({ top: 20 })
        .border({ color: Color.Black, width: 1 })
        .onDrop((dragEvent?: DragEvent) => {
          if (dragEvent) {
            let records: Array<unifiedDataChannel.UnifiedRecord> = dragEvent.getData().getRecords();
            let plainText: unifiedDataChannel.PlainText = records[0] as unifiedDataChannel.PlainText;
            this.text = plainText.textContent;
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
function executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo): Promise<DragEventParam>
```

主动发起拖拽能力，传入拖拽发起后跟手效果所拖拽的对象以及携带拖拽信息。使用Promise异步回调。
> **说明：**  
>  
> 从API version 11开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller)方法获取当前UI  
> 上下文关联的[DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md)对象。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** executeDrag

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-dragController-function executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo): Promise<DragEventParam>--><!--Device-dragController-function executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo): Promise<DragEventParam>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) \| DragItemInfo | 是 | 拖拽发起后跟手效果所拖拽的对象。 |
| dragInfo | [DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | 是 | 拖拽信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DragEventParam&gt; | A Promise with the drag event information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

**示例：**

推荐通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getDragController](arkts-apis-uicontext-uicontext.md#getdragcontroller11)方法获取当前UI上下文关联的DragController对象。

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
  @State pixmap: image.PixelMap | undefined = undefined
  @State text: string = ''

  @Builder
  DraggingBuilder() {
    Column() {
      Text("DraggingBuilder")
        .fontColor(Color.White)
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  @Builder
  PixmapBuilder() {
    Column() {
      Text("PixmapBuilder")
        .fontColor(Color.White)
        .fontSize(15)
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  aboutToAppear() {
    let pb: CustomBuilder = (): void => {
      this.PixmapBuilder()
    }
    this.getUIContext().getComponentSnapshot().createFromBuilder(pb).then((pix: image.PixelMap) => {
      this.pixmap = pix;
    })
  }

  build() {
    Column() {
      Button('touch to execute drag')
        .margin(10)
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              let text = new unifiedDataChannel.PlainText()
              text.textContent = 'drag text'
              text.abstract = 'abstract'
              let unifiedData = new unifiedDataChannel.UnifiedData(text)

              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              }
              let dragItemInfo: DragItemInfo = {
                pixelMap: this.pixmap,
                builder: () => {
                  this.DraggingBuilder()
                },
                extraInfo: "DragItemInfoTest"
              }
              let eve: DragInfo = new DragInfo();
              this.getUIContext()
                .getDragController()
                .executeDrag(dragItemInfo, dragInfo) // 建议使用 this.getUIContext().getDragController().executeDrag()接口
                .then((eve) => {
                  if (eve.event.getResult() == DragResult.DRAG_SUCCESSFUL) {
                    // ...
                  } else if (eve.event.getResult() == DragResult.DRAG_FAILED) {
                    // ...
                  }
                })
                .catch((err: Error) => {
                })
            }
          }
        })
      Text(this.text)
        .height(100)
        .width(150)
        .margin({ top: 20 })
        .border({ color: Color.Black, width: 1 })
        .onDrop((dragEvent?: DragEvent) => {
          if (dragEvent) {
            let records: Array<unifiedDataChannel.UnifiedRecord> = dragEvent.getData().getRecords();
            let plainText: unifiedDataChannel.PlainText = records[0] as unifiedDataChannel.PlainText;
            this.text = plainText.textContent;
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}

```

