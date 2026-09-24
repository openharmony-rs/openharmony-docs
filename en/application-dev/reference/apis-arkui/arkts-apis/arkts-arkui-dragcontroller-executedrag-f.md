# executeDrag

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## executeDrag

```TypeScript
function executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo,
    callback: AsyncCallback<DragEventParam>): void
```

Initiates a drag action, with the object to be dragged and the drag information passed in. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Since API version 11, you can use the [getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) API in
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md) object
> associated with the current UI context.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** executeDrag

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-common-comp-dragiteminfo-i.md) | Yes | Object to be dragged.<br>**NOTE:** <br>The global builder is not supported. If the Image component is used in the builder, enable synchronous loading, that is, set the [syncLoad](../arkts-components/arkts-arkui-image-comp-attribute.md#syncload) attribute of the component to **true**. The builder is used only to generate the image displayed during the current dragging. If the root component of the builder has zero width or height, it will cause failure in drag image generation, which in turn breaks the entire drag operation. Changes to the builder, if any, apply to the next dragging, but not to the current dragging. |
| dragInfo | [DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | Yes | Drag information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DragEventParam](arkts-arkui-dragcontroller-drageventparam-i.md)&gt; | Yes | Callback function. If the operation is successful, **err** is **undefined** and **data** is the **DragEventParam** object obtained. Otherwise, **err** is an error object.<br>**Since:** 12 |

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
              }, dragInfo, (err, eve) => { // You are advised to use this.getUIContext().getDragController().executeDrag().
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


<a id="executedrag-1"></a>

## executeDrag

```TypeScript
function executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo): Promise<DragEventParam>
```

Initiates a drag action, with the object to be dragged and the drag information passed in. This API uses a promise to return the result.

> **NOTE:** 
> 
> Since API version 11, you can use the [getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) API in
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md) object
> associated with the current UI context.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** executeDrag

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-common-comp-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-common-comp-dragiteminfo-i.md) | Yes | Object to be dragged. |
| dragInfo | [DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | Yes | Drag information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;{ event: DragEvent, extraParams: string }&gt; | Promise used to return the result.<br>**Since:** 10 - 11 |
| Promise&lt;[DragEventParam](arkts-arkui-dragcontroller-drageventparam-i.md)&gt; | A Promise with the drag event information.<br>**Since:** 12 |

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
                .executeDrag(dragItemInfo, dragInfo) // You are advised to use this.getUIContext().getDragController().executeDrag().
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
