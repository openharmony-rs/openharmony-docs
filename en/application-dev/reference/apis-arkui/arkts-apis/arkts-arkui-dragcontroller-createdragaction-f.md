# createDragAction

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## createDragAction

```TypeScript
function createDragAction(customArray: Array<CustomBuilder | DragItemInfo>, dragInfo: DragInfo): DragAction
```

Creates a drag action object for initiating drag and drop operations. You need to explicitly specify one or more drag previews, the drag data, and the drag handle point. If a drag operation initiated by an existing drag action object is not completed, no new object can be created, and calling the API will throw an exception. After the lifecycle of the drag action object ends, the callback functions registered on this object become invalid. Therefore, it is necessary to hold this object within a longer scope and replace the old value with a new object returned by **createDragAction** before each drag initiation.

> **NOTE:** 
> 
> - Since API version 11, you can use the [getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md) object associated with the current UI context.
> 
> - For optimal drag and drop performance, limit the number of drag previews.

**Since:** 11

**Deprecated since:** 18

**Substitutes:** [createDragAction](arkts-arkui-arkui-uicontext-dragcontroller-c.md#createdragaction)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-dragController-function createDragAction(customArray: Array<CustomBuilder | DragItemInfo>, dragInfo: DragInfo): DragAction--><!--Device-dragController-function createDragAction(customArray: Array<CustomBuilder | DragItemInfo>, dragInfo: DragInfo): DragAction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| customArray | Array&lt;[CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-common-comp-dragiteminfo-i.md)&gt; | Yes | Object to be dragged. |
| dragInfo | [DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | Yes | Drag information. |

**Return value:**

| Type | Description |
| --- | --- |
| [DragAction](arkts-arkui-dragcontroller-dragaction-i.md) | **DragAction** object, which is used to subscribe to drag state changes and start the drag service. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal handling failed. |

**Examples**

> NOTE
> 
> You are advised to use [getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the DragController object associated with the current UI context.

```TypeScript
import { dragController } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@Component
struct DragControllerPage {
  @State pixmap: image.PixelMap | null = null
  @State text: string = ''
  private dragAction: dragController.DragAction | null = null;
  customBuilders: Array<CustomBuilder | DragItemInfo> = new Array<CustomBuilder | DragItemInfo>();

  @Builder
  DraggingBuilder() {
    Column() {
      Text("DraggingBuilder")
        .fontColor(Color.White)
        .fontSize(12)
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {

      Column() {
        Text(this.text)
          .width('100%')
          .height('100%')
          .fontColor(Color.White)
          .fontSize(18)
          .onDrop((dragEvent?: DragEvent) => {
            if (dragEvent) {
              let records: Array<unifiedDataChannel.UnifiedRecord> = dragEvent.getData().getRecords();
              let plainText: unifiedDataChannel.PlainText = records[0] as unifiedDataChannel.PlainText;
              this.text = plainText.textContent;
            }
          })
      }
      .width(100)
      .height(100)
      .backgroundColor(Color.Red)
      .margin(10)

      Button('Drag Multiple Objects').onTouch((event?: TouchEvent) => {
        if (event) {
          if (event.type == TouchType.Down) {
            console.info("multi drag Down by listener");
            this.customBuilders.splice(0, this.customBuilders.length);
            this.customBuilders.push(() => {
              this.DraggingBuilder()
            });
            this.customBuilders.push(() => {
              this.DraggingBuilder()
            });
            this.customBuilders.push(() => {
              this.DraggingBuilder()
            });
            let text = new unifiedDataChannel.PlainText()
            text.textContent = 'drag text'
            let unifiedData = new unifiedDataChannel.UnifiedData(text)
            let dragInfo: dragController.DragInfo = {
              pointerId: 0,
              data: unifiedData,
              extraParams: ''
            }
            try {
              this.dragAction = this.getUIContext()
                .getDragController()
                .createDragAction(this.customBuilders,
                  dragInfo) // You are advised to use this.getUIContext().getDragController().createDragAction().
              if (!this.dragAction) {
                console.info("listener dragAction is null");
                return
              }
              this.dragAction.on('statusChange', (dragAndDropInfo: dragController.DragAndDropInfo) => {
                if (dragAndDropInfo.status == dragController.DragStatus.STARTED) {
                  console.info("drag has start");
                } else if (dragAndDropInfo.status == dragController.DragStatus.ENDED) {
                  console.info("drag has end");
                  if (!this.dragAction) {
                    return
                  }
                  this.dragAction.off('statusChange')
                }
              })
              this.dragAction.startDrag().then(() => {
              }).catch((err: Error) => {
                console.error(`Failed to start drag. Code: ${err.code}, message: ${err.message}`);
              })
            } catch (err) {
              console.error(`Failed to create dragAction. Code: ${err.code}, message: ${err.message}`);
            }
          }
        }
      }).margin({ top: 20 })
    }
  }
}
```
