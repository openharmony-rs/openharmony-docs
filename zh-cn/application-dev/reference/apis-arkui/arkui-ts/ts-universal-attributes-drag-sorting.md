# 拖拽排序

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong-->
<!--SE: @yylong-->
<!--TSE: @liuzhenshuo-->

在List组件下使用ForEach/LazyForEach/Repeat，并设置onMove事件，每次迭代生成一个ListItem时，可以使能拖拽排序。拖拽排序离手后，如果数据位置发生变化，将触发onMove事件，上报数据移动原始索引号和目标索引号。在onMove事件中，需要根据上报的起始索引号和目标索引号修改数据源。确保数据仅顺序发生变化，才能正常执行落位动画。

> **说明：**
> 
> 从API version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## onMove

onMove(handler: Optional\<OnMoveHandler\>)

拖拽排序数据移动回调。当父容器组件为[List](./ts-container-list.md)，并且ForEach/LazyForEach/Repeat每次迭代都生成一个ListItem组件时才生效。设置拖拽排序时可以定义不同的拖拽操作，并在响应事件发生时响应。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型      | 必填 | 说明       |
| ------ | --------- | ---- | ---------- |
| handler  | Optional\<[OnMoveHandler](#onmovehandler)\> | 是   | 拖拽动作。 |

## onMove<sup>20+</sup>

onMove(handler: Optional\<OnMoveHandler\>, eventHandler: ItemDragEventHandler)

拖拽排序数据移动回调。当父容器组件为[List](./ts-container-list.md)，并且ForEach/LazyForEach/Repeat每次迭代都生成一个ListItem组件时才生效。设置拖拽排序时可以定义不同的拖拽操作，并在响应事件发生时响应。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型      | 必填 | 说明       |
| ------ | --------- | ---- | ---------- |
| handler  | Optional\<[OnMoveHandler](#onmovehandler)\> | 是   | 拖拽动作。 |
| eventHandler  | [ItemDragEventHandler](#itemdrageventhandler20) | 是   | 拖拽发生时产生的回调。 |

## OnMoveHandler

type OnMoveHandler = (from: number, to: number) => void

定义数据源拖拽回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型      | 必填 | 说明       |
| ------ | --------- | ---- | ---------- |
| from  | number | 是   | 数据源拖拽起始索引号。取值范围是[0, 数据源长度-1]。 |
| to  | number | 是   | 数据源拖拽目标索引号。取值范围是[0, 数据源长度-1]。 |

## ItemDragEventHandler<sup>20+</sup>

定义数据源拖拽事件回调。用于响应不同的拖拽操作。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明                 |
| ------ | ------ | ---- | -------------------- |
| onLongPress  |  [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<number\> | 否  | 长按时触发的回调。<br>- 参数index为长按时当前目标的索引号。 |
| onDragStart  | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<number\> | 否   | 在页面跟手滑动开始时触发的回调。<br>- 参数index为拖拽开始时当前目标的索引号。 |
| onMoveThrough  | [OnMoveHandler](#onmovehandler) | 否   | 在页面跟手滑动过程中经过其他组件时触发的回调。 |
| onDrop  | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<number\> | 否   | 在页面跟手滑动结束时触发的回调。<br>- 参数index为拖拽结束时当前目标的索引号。 |

## 示例

### 示例1（使用OnMove进行拖拽）

以下示例展示了ForEach在List组件内使用时的拖拽效果。

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

### 示例2（使用OnMove进行拖拽，并设置拖拽事件回调）

以下示例展示了ForEach在List组件设置拖拽效果后触发的回调事件。

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
            Text('第一个List' + item)
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
            console.log('List onMove From: ' + from);
            console.log('List onMove To: ' + to);
          },
            {
              onLongPress: (index: number) => {
                console.log('List onLongPress: ' + index);
              },
              onDrop: (index: number) => {
                console.log('List onDrop: ' + index);
              },
              onDragStart: (index: number) => {
                console.log('List onDragStart: ' + index);
              },
              onMoveThrough: (from: number, to: number) => {
                console.log('List onMoveThrough From: ' + from);
                console.log('List onMoveThrough To: ' + to);
              }
            }
          )
      }.width('90%')
        .scrollBar(BarState.Off)
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```