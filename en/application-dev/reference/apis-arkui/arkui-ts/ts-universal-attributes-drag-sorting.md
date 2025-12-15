# Drag-and-Drop Sorting

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong-->
<!--Designer: @yylong-->
<!--Tester: @liuzhenshuo-->
<!--Adviser: @Brilliantry_Rui-->

By using **ForEach**, **LazyForEach**, or **Repeat** within a **List** component and setting up the **onMove** event, you can implement drag-and-drop sorting. When the drag-and-drop gesture is released, if any item's position changes, the **onMove** event is triggered, which reports the original index and target index of the relocated item. In the **onMove** event, the data source must be updated based on the reported start index and target index. Ensure that only the order of the data changes so that the drop animation can be executed properly.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.

## onMove

onMove(handler: Optional\<OnMoveHandler\>): T

Invoked when data is moved during drag-and-drop sorting. This callback is effective only when the parent container component is [List](./ts-container-list.md) and each iteration of **ForEach**, **LazyForEach**, or **Repeat** generates a **ListItem** component. It allows you to define custom drag actions and handle various drag events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type     | Mandatory| Description      |
| ------ | --------- | ---- | ---------- |
| handler  | Optional\<[OnMoveHandler](#onmovehandler)\> | Yes  | Drag operation.|

**Return value**

| Type     | Description      |
| ------ | --------- |
| T  | Current component.|

## onMove<sup>20+</sup>

onMove(handler: Optional\<OnMoveHandler\>, eventHandler: ItemDragEventHandler): T

Invoked when data is moved during drag-and-drop sorting. This callback is effective only when the parent container component is [List](./ts-container-list.md) and each iteration of **ForEach**, **LazyForEach**, or **Repeat** generates a **ListItem** component. It allows you to define custom drag actions and handle various drag events. Compared with [onMove](#onmove), this API supports the **eventHander** parameter for listening for callback events reported during drag and drop operations.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type     | Mandatory| Description      |
| ------ | --------- | ---- | ---------- |
| handler  | Optional\<[OnMoveHandler](#onmovehandler)\> | Yes  | Drag operation.|
| eventHandler  | [ItemDragEventHandler](#itemdrageventhandler20) | Yes  | Callback invoked when the drag occurs.|

**Return value**

| Type     | Description      |
| ------ | --------- |
| T  | Current component.|

## OnMoveHandler

type OnMoveHandler = (from: number, to: number) => void

Defines the callback triggered when data is moved during drag-and-drop sorting.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type     | Mandatory| Description      |
| ------ | --------- | ---- | ---------- |
| from  | number | Yes  | Start index of the drag operation. The value range is [0, data source length - 1].|
| to  | number | Yes  | End index of the drag operation. The value range is [0, data source length - 1].|

## ItemDragEventHandler<sup>20+</sup>

Defines callbacks for drag events on a data source, allowing you to respond to different drag operations.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type  | Read-Only| Optional| Description                |
| ------ | ------ | ---- | ---- | -------------------- |
| onLongPress  |  [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<number\> | No | Yes| Callback triggered when an item is long-pressed.<br>- **index**: index of the target when the long press occurs.|
| onDragStart  | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<number\> | No  | Yes| Callback triggered when dragging starts.<br>- **index**: index of the target when dragging starts.|
| onMoveThrough  | [OnMoveHandler](#onmovehandler) | No  | Yes| Callback triggered when the dragged item moves over other items.|
| onDrop  | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<number\> | No  | Yes| Callback triggered when dragging ends.<br>- **index**: index of the target when dragging ends.|

## Example

### Example 1: Using onMove for Drag and Drop Operations

This example demonstrates how to use **onMove** for drag and drop with **ForEach** in a **List** component.

```ts
@Entry
@Component
struct ForEachSort {
  @State arr: Array<string> = [];

  build() {
    Row() {
      List() {
        ForEach(this.arr, (item: string) => {
          ListItem() {
            Text(item.toString())
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .size({height: 100, width: '100%'})
          }.margin(10)
          .borderRadius(10)
          .backgroundColor('#FFFFFFFF')
        }, (item: string) => item)
          .onMove((from:number, to:number) => {
            let tmp = this.arr.splice(from, 1);
            this.arr.splice(to, 0, tmp[0]);
          })
      }
      .width('100%')
      .height('100%')
      .backgroundColor('#FFDCDCDC')
    }
  }
  aboutToAppear(): void {
    for (let i = 0; i < 100; i++) {
      this.arr.push(i.toString());
    }
  }
}
```

### Example 2: Using onMove with Drag Event Callbacks

This example demonstrates how to use **onMove** with additional drag event callbacks in a **List** component containing ForEach, available since API version 20.

```ts
// xxx.ets
@Entry
@Component
struct ListOnMoveExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6];

  build() {
    Column() {
      List({ space: 20, initialIndex: 0 }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('First list' + item)
              .width('100%')
              .height(80)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: string) => item)
          .onMove((from: number, to: number) => {
            let tmp = this.arr.splice(from, 1);
            this.arr.splice(to, 0, tmp[0]);
            console.info('List onMove From: ' + from);
            console.info('List onMove To: ' + to);
          },
            {
              onLongPress: (index: number) => {
                console.info('List onLongPress: ' + index);
              },
              onDrop: (index: number) => {
                console.info('List onDrop: ' + index);
              },
              onDragStart: (index: number) => {
                console.info('List onDragStart: ' + index);
              },
              onMoveThrough: (from: number, to: number) => {
                console.info('List onMoveThrough From: ' + from);
                console.info('List onMoveThrough To: ' + to);
              }
            }
          )
      }.width('90%')
      .scrollBar(BarState.Off)
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```
