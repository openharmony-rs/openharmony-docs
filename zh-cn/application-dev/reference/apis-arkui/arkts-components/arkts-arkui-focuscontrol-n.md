# focusControl

```TypeScript
declare namespace focusControl
```

焦点控制模块。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [requestFocus](arkts-arkui-focuscontrol-requestfocus-f.md) | 方法语句中可使用的全局接口，调用此接口可以主动让焦点在下一帧渲染时转移至参数指定的组件上。 |

## 示例

该示例主要演示通过foregroundBlurStyle为图片设置内容模糊效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct ForegroundBlurStyleDemo {
  build() {
    Column() {
      Text('Thin Material').fontSize(30).fontColor(0xCCCCCC)
      // $r("app.media.bg")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.bg'))
        .width(300)
        .height(350)
        .foregroundBlurStyle(BlurStyle.Thin,
          { colorMode: ThemeColorMode.LIGHT, adaptiveColor: AdaptiveColor.DEFAULT, scale: 1.0 })
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例1（半模态设置边缘光效动画）

以下示例通过设置edgeLightMode属性开启边缘光效动画，同时使用[SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions)中的systemMaterial接口实现了半透明材质效果。

从API版本26.0.0开始，[SheetOptions](arkts-arkui-common-comp-sheetoptions-i.md)新增edgeLightMode属性。



```TypeScript
// xxx.ets
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct SheetMaterialExample {
  @State isShow: boolean = false;
  @State sheetHeight: number = 300;
  @State sheetMaterial: SystemUiMaterial | undefined = new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
  });

  @Builder
  sheetBuilder() {
    Column({ space: 10 }) {
      Text('Text')
        .fontSize(20)
        .margin(10)
    }
    .width('100%')
    .height('100%')
  }

  build() {
    Stack() {
      // 请开发者替换为实际资源文件
      Image($r('app.media.startIcon'))
      Column() {
        Button('open Sheet')
          .onClick(() => {
            this.isShow = true;
          })
          .fontSize(20)
          .margin(10)
          .bindSheet($$this.isShow, this.sheetBuilder(), {
            height: this.sheetHeight,
            backgroundColor: Color.Transparent,
            edgeLightMode: EdgeLightMode.EDGELIGHT_ENABLED,
            systemMaterial: this.sheetMaterial
          })
      }
      .justifyContent(FlexAlign.Center)
      .width('100%')
      .height('100%')
    }
  }
}
```

### 示例2（半模态设置模糊优化）

以下示例通过设置blurSnapshot属性开启模糊优化。当使用[SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions)中的systemMaterial接口设置材质效果或使用[SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions)中的blurStyle接口设置模糊时发现功耗明显增加时，可以尝试开启模糊优化。

从API版本26.0.0开始，[SheetOptions](arkts-arkui-common-comp-sheetoptions-i.md)新增blurSnapshot属性。

```TypeScript
// xxx.ets
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct SheetTransitionExample {
  @State isShow: boolean = false;
  @State rotateAngle: number = 0;
  @State sheetMaterial: SystemUiMaterial | undefined = new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
  });

  @Builder
  sheetBuilder() {
    Text('Context')
  }

  build() {
    Stack() {
      Button('This is Text')
        .margin(100)
        .rotate({
          x: 0,
          y: 0,
          z: 1,
          angle: this.rotateAngle
        })
        .onAppear(() => {
          this.getUIContext()?.animateTo({
            duration: 1200,
            curve: Curve.Friction,
            delay: 500,
            iterations: -1,
            expectedFrameRateRange: {
              min: 10,
              max: 120,
              expected: 60,
            }
          }, () => {
            this.rotateAngle = 360;
          })
        })
      Column() {
        Button('Open BindSheet')
          .onClick(() => {
            this.isShow = true;
          })
          .fontSize(20)
          .margin(10)
          .bindSheet($$this.isShow, this.sheetBuilder(), {
            height: 400,
            showClose: true,
            backgroundColor: Color.Transparent,
            // 若在设置blurStyle或者systemMaterial时发现功耗明显增加时，可以尝试开启模糊优化
            blurStyle: BlurStyle.Thin,
            // systemMaterial: this.sheetMaterial,
            blurSnapshot: { enableFreeze: true },
          })
      }
      .justifyContent(FlexAlign.Start)
      .width('100%')
      .height('100%')
    }
  }
}
```

属性动画状态下添加运动模糊效果。

```TypeScript
// xxx.ets
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct MotionBlurTest {
  @State widthSize: number = 300
  @State heightSize: number = 240
  @State flag: boolean = true
  @State radius: number = 0
  @State x: number = 0.5
  @State y: number = 0.5

  build() {
    Column() {
      Column() {
        // $r('app.media.test')需要替换为开发者所需的图像资源文件。
        Image($r('app.media.test'))
          .width(this.widthSize)
          .height(this.heightSize)
          .scale({ x: this.flag ? 1 : 0.8, y: this.flag ? 1 : 0.8, centerX: '50%', centerY: '50%' })
          .onClick(() => {
            // 点击时设置运动模糊参数并触发缩放动画
            this.radius = 50;
            this.x = 0.5;
            this.y = 0.5;
            this.flag = !this.flag;
          })
          .animation({
            duration: 2000, // 动画播放时间
            iterations: 1, // 动画播放次数
            playMode: PlayMode.Alternate, // 动画播放模式，在奇数次（1、3、5...）正向播放，在偶数次（2、4、6...）反向播放
            curve: curves.springCurve(10, 1, 228, 30), // 动画曲线
            onFinish: () => {
              // 动画结束后将模糊半径置为0，清除运动模糊效果
              this.radius = 0;
              console.info('onFinish');
            },
          })
          .motionBlur({ radius: this.radius, anchor: { x: this.x, y: this.y } })
      }
    }.width('100%')
    .margin({ top: 50 })
  }
}
```

该示例通过setCursor实现了鼠标光标样式的设置。

```TypeScript
// xxx.ets
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct CursorControlExample {
  build() {
    Column() {
      Row()
        .height(200)
        .width(200)
        .backgroundColor(Color.Green)
        .position({ x: 60, y: 70 })
        .onHover((flag) => {
          if (flag) {
            // 建议使用this.getUIContext().getCursorController().setCursor()
            cursorControl.setCursor(pointer.PointerStyle.EAST);
          } else {
            // 建议使用this.getUIContext().getCursorController().restoreDefault()
            cursorControl.restoreDefault();
          }
        })
      Row()
        .height(200)
        .width(200)
        .backgroundColor(Color.Blue)
        .position({ x: 130, y: 120 })
        .onHover((flag) => {
          if (flag) {
            // 建议使用this.getUIContext().getCursorController().setCursor()
            cursorControl.setCursor(pointer.PointerStyle.WEST);
          } else {
            // 建议使用this.getUIContext().getCursorController().restoreDefault()
            cursorControl.restoreDefault();
          }
        })
    }.width('100%')
  }
}
```

该示例实现了组件注册表冠事件，并上报接收到的表冠事件数据内容。

```TypeScript
// xxx.ets
@Entry
@Component
struct CityList {
  @State message: string = 'onDigitalCrown';

  build() {
    Column() {
      Row() {
        Stack() {
          Text(this.message)
            .fontSize(20)
            .fontColor(Color.White)
            .backgroundColor('#262626')
            .textAlign(TextAlign.Center)
            .focusable(true)
            .focusOnTouch(true)
            .defaultFocus(true)
            .borderWidth(2)
            .width(223)
            .height(223)
            .borderRadius(110)
            .onDigitalCrown((event: CrownEvent) => {
              event.stopPropagation();
              this.message = 'CrownEvent\n\n' + JSON.stringify(event);
              console.info(`action: ${event.action}, angularVelocity: ${event.angularVelocity}, degree: ${event.degree}, timestamp: ${event.timestamp}`);
            })
        }.width('100%').height('100%')
      }.width('100%').height('100%')
    }
  }
}
```

### 示例1（List使用OnMove进行拖拽）

以下示例展示了ForEach在List组件内使用时的拖拽效果。

```TypeScript
@Entry
@Component
struct ForEachSort {
  @State arr: Array<string> = [];

  build() {
    Row() {
      List() {
        ForEach(this.arr, (item: string) => {
          ListItem() {
            Text(item)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .size({height: 100, width: '100%'})
          }.margin(10)
          .borderRadius(10)
          .backgroundColor('#FFFFFFFF')
        }, (item: string) => item)
          .onMove((from: number, to: number) => {
            // 根据拖拽起止索引移动数据，确保数据顺序与拖拽结果一致。
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

### 示例2（List使用OnMove进行拖拽，并设置拖拽事件回调）

从API version 20开始，以下示例展示了ForEach在List组件设置拖拽效果后触发的回调事件。

```TypeScript
// xxx.ets
@Entry
@Component
struct ListOnMoveExample {
  @State arr: number[] = [0, 1, 2, 3, 4, 5, 6];

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
        }, (item: number) => item.toString())
          .onMove((from: number, to: number) => {
            // 根据拖拽起止索引移动数据，确保数据顺序与拖拽结果一致。
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

### 示例3（Grid规则布局使用ForEach的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了ForEach在Grid组件设置拖拽效果后触发的回调事件，Grid里全是规则的GridItem。



```TypeScript
// xxx.ets
@Entry
@Component
struct GridOnMoveExample {
  private arr: Array<string> = [];

  build() {
    Row() {
      Grid() {
        ForEach(this.arr, (item: string) => {
          GridItem() {
            Text(item.toString())
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .size({height: 100, width: '100%'})
          }.margin(10)
          .borderRadius(10)
          .backgroundColor(0xF9CF93)
        }, (item: string) => item)
          // 当拖拽松手时，被拖拽项落位位置与拖拽前不同时触发，from为起始索引，to为目标索引
          .onMove((from: number, to: number) => {
            let tmp = this.arr.splice(from, 1);  // 从原位置取出被拖拽元素
            this.arr.splice(to, 0, tmp[0]);      // 将取出的被拖拽元素插入到目标位置
            console.info('Grid onMove From: ' + from);
            console.info('Grid onMove To: ' + to);
          },
            {
              onLongPress: (index: number) => {
                // GridItem长按浮起时触发
                console.info('Grid onLongPress: ' + index);
              },
              onDrop: (index: number) => {
                // 拖拽的GridItem松手时触发
                console.info('Grid onDrop: ' + index);
              },
              onDragStart: (index: number) => {
                // GridItem长按浮起并开始拖拽时触发
                console.info('Grid onDragStart: ' + index);
              },
              onMoveThrough: (from: number, to: number) => {
                // GridItem拖拽过程中持续触发
                console.info('Grid onMoveThrough From: ' + from);
                console.info('Grid onMoveThrough To: ' + to);
              }
            }
          )
      }
      .columnsTemplate('1fr 1fr')  // 两列等宽布局
      .width('100%')
      .height('100%')
      .backgroundColor(0xFAEEE0)
    }
  }
  aboutToAppear(): void {
    // 初始化100条数据作为Grid内容
    for (let i = 0; i < 100; i++) {
      this.arr.push(i.toString())
    }
  }
}
```

### 示例4（Grid不规则布局使用ForEach的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了ForEach在Grid组件设置拖拽效果后触发的回调事件，Grid里存在不规则的GridItem。应用可通过[irregularIndexes](ts-container-grid.md#gridlayoutoptions10对象说明)设置哪些索引是不规则节点，通过修改对应索引的rectSize调整该GridItem所占的行列数。



```TypeScript
// xxx.ets
class Rects {
  id: number = 0
  // rectSize表示该GridItem占用的[行, 列]数，默认[1, 1]为规则节点
  rectSize: [number, number] = [1, 1]
  constructor(id_: number) {
    this.id = id_
  }
}

@Entry
@Component
struct GridOnMoveExample {
  @State arr: Array<Rects> = [];

  // 网格布局选项（实际生效），声明不规则节点的索引及各自占用的行列数
  @State layoutOptions: GridLayoutOptions = {
    regularSize: [1, 1],
    irregularIndexes: [8],   // 索引为8的GridItem为不规则节点
    onGetIrregularSizeByIndex: (index: number) => {
      return this.arr[index].rectSize
    }
  };

  // 布局选项（备份），用于拖拽时通过整体赋值触发layoutOptions刷新
  layoutOptions_back: GridLayoutOptions = {
    regularSize: [1, 1],
    irregularIndexes: [8],   // 索引为8的GridItem为不规则节点
    onGetIrregularSizeByIndex: (index: number) => {
      return this.arr[index].rectSize
    }
  };

  build() {
    Row() {
      Grid(undefined, this.layoutOptions) {
        ForEach(this.arr, (item: Rects) => {
          GridItem() {
            Text(item.id.toString())
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .size({ height: 100 * item.rectSize[0] + (item.rectSize[0] - 1) * 20, width: '100%'}) // 设置高度，跨行GridItem需额外增加外边距(规则GridItem的间距为2*10)用于界面对齐
          }.margin(10)
          .borderRadius(10)
          .backgroundColor(0xF9CF93)
        }, (item: Rects) => item.id.toString())
          // 当拖拽松手时，被拖拽项落位位置与拖拽前不同时触发，from为起始索引，to为目标索引
          .onMove((from:number, to:number) => {
            console.info("Grid onMove from " + from + " to " + to)
            // 更新this.arr数据源
            let tmp = this.arr.splice(from, 1);
            this.arr.splice(to, 0, tmp[0]);
            if (from < to) {  // 被拖拽项索引小于目标位置索引
              // 先保存被拖拽项在irregularIndexes数组中的位置，避免后续循环更新产生重复值后indexOf定位错误
              let from_idx = -1
              if (this.layoutOptions.irregularIndexes?.includes(from)) {
                from_idx = this.layoutOptions.irregularIndexes.indexOf(from)
              }

              // 被拖拽项与目标位置之间的元素整体前移一位（索引-1）
              if (this.layoutOptions.irregularIndexes != undefined) {
                let len = this.layoutOptions.irregularIndexes.length
                for (let i = len - 1; i >= 0; i --) {
                  let irregularIndex = this.layoutOptions.irregularIndexes[i]
                  if (irregularIndex > from && irregularIndex <= to) {
                    this.layoutOptions.irregularIndexes[i] --
                  }
                }
              }

              // 若被拖拽项本身为不规则节点，更新其索引到目标位置
              if (from_idx != -1 && this.layoutOptions.irregularIndexes != undefined) {
                this.layoutOptions.irregularIndexes[from_idx] = to
              }
            } else {  // 被拖拽项索引大于等于目标位置索引
              // 先保存被拖拽项在irregularIndexes数组中的位置，避免后续循环更新产生重复值后indexOf定位错误
              let from_idx = -1
              if (this.layoutOptions.irregularIndexes?.includes(from)) {
                from_idx = this.layoutOptions.irregularIndexes.indexOf(from)
              }

              // 目标位置至被拖拽项之间的元素整体后移一位（索引+1）
              if (this.layoutOptions.irregularIndexes != undefined) {
                let len = this.layoutOptions.irregularIndexes.length
                for (let i = 0; i < len; i ++) {
                  let irregularIndex = this.layoutOptions.irregularIndexes[i]
                  if (irregularIndex >= to && irregularIndex < from) {
                    this.layoutOptions.irregularIndexes[i] ++
                  }
                }
              }

              // 若被拖拽项本身为不规则节点，更新其索引到目标位置
              if (from_idx != -1 && this.layoutOptions.irregularIndexes != undefined) {
                this.layoutOptions.irregularIndexes[from_idx] = to
              }
            }
            // 通过备份对象整体赋值，强制layoutOptions刷新生效
            this.layoutOptions_back.irregularIndexes = this.layoutOptions.irregularIndexes
            this.layoutOptions = this.layoutOptions_back
            console.info("Grid this.layoutOptions.irregularIndexes " + this.layoutOptions.irregularIndexes)
          },
            {
              onLongPress: (index: number) => {
                // GridItem长按浮起时触发
                console.info('Grid onLongPress: ' + index);
              },
              onDrop: (index: number) => {
                // 拖拽的GridItem松手时触发
                console.info('Grid onDrop: ' + index);
              },
              onDragStart: (index: number) => {
                // GridItem长按浮起并开始拖拽时触发
                console.info('Grid onDragStart: ' + index);
              },
              onMoveThrough: (from: number, to: number) => {
                // GridItem拖拽过程中持续触发
                console.info('Grid onMoveThrough From: ' + from + ' to: ' + to);
              }
            })
      }
      .columnsTemplate('1fr 1fr 1fr 1fr')   // 四列等宽布局
      .width('100%')
      .height('100%')
      .backgroundColor(0xFAEEE0)
    }
  }
  aboutToAppear(): void {
    // 初始化100个矩形数据，并设置索引8为2x2的不规则节点
    for (let i = 0; i < 100; i++) {
      this.arr.push(new Rects(i));
    }
    this.arr[8].rectSize = [2, 2] // 2行2列
  }
}
```

### 示例5（Grid不规则布局使用LazyForEach的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了LazyForEach在Grid组件设置拖拽效果后触发的回调事件，Grid里存在不规则的GridItem。应用可通过irregularIndexes设置哪些索引是不规则节点，通过修改对应索引的rectSize调整该GridItem所占的行列数。

```TypeScript
// RectGridDataSource.ets
export class Rects {
  id: number = 0
  // rectSize表示该GridItem占用的[行, 列]数，默认[1, 1]为规则节点
  rectSize: [number, number] = [1, 1]
  constructor(id_: number) {
    this.id = id_
  }
}

// LazyForEach的数据源，实现IDataSource接口，负责管理数据及通知UI刷新
export class RectGridDataSource implements IDataSource {
  private list: Array<Rects> = [];
  private listeners: DataChangeListener[] = [];

  constructor(list: Rects[]) {
    this.list = list;
  }

  // 返回数据总数
  totalCount(): number {
    return this.list.length;
  }

  // 根据索引获取对应的数据项
  getData(index: number): Rects {
    return this.list[index];
  }

  // 注册数据变更监听器
  registerDataChangeListener(listener: DataChangeListener): void {
    if (this.listeners.indexOf(listener) < 0) {
      this.listeners.push(listener);
    }
  }

  // 注销数据变更监听器
  unregisterDataChangeListener(listener: DataChangeListener): void {
    const pos = this.listeners.indexOf(listener);
    if (pos >= 0) {
      this.listeners.splice(pos, 1);
    }
  }

  // 通知控制器数据位置变化
  notifyDataMove(from: number, to: number): void {
    this.listeners.forEach(listener => {
      listener.onDataMove(from, to);
    })
  }

  // 重新加载所有数据
  notifyDataReload(): void {
    this.listeners.forEach(listener => {
      listener.onDataReloaded();
    })
  }

  // 将from位置的元素移动到to位置，并通知UI全部重载刷新
  public moveItem(from: number, to: number): void {
    let tmp = this.list.splice(from, 1);  // 先移除被拖拽项
    this.list.splice(to, 0, tmp[0]);      // 将被拖拽项插入到目标位置
    this.notifyDataReload()
  }
}
```



```TypeScript
// xxx.ets
import { RectGridDataSource, Rects } from './RectGridDataSource';

@Entry
@Component
struct GridOnMoveExample {
  numbers: RectGridDataSource = new RectGridDataSource([]);

  // 网格布局选项（实际生效），声明不规则节点的索引及各自占用的行列数
  @State layoutOptions: GridLayoutOptions = {
    regularSize: [1, 1],
    irregularIndexes: [4, 5, 6, 7, 8, 13],   // 设置哪些索引对应的GridItem为不规则节点
    onGetIrregularSizeByIndex: (index: number) => {
      return this.numbers.getData(index).rectSize
    }
  };

  // 布局选项（备份），用于拖拽时通过整体赋值触发layoutOptions刷新
  layoutOptions_back: GridLayoutOptions = {
    regularSize: [1, 1],
    irregularIndexes: [4, 5, 6, 7, 8, 13],
    onGetIrregularSizeByIndex: (index: number) => {
      return this.numbers.getData(index).rectSize
    }
  };

  build() {
    Row() {
      Grid(undefined, this.layoutOptions) {
        LazyForEach(this.numbers, (item: Rects) => {
          GridItem() {
            Text(item.id.toString())
              .fontSize(16)
              .textAlign(TextAlign.Center)
              // 设置高度，跨行GridItem需额外增加外边距(规则GridItem的间距为2*10)用于界面对齐
              .size({ height: 100 * item.rectSize[0] + (item.rectSize[0] - 1) * 20, width: '100%'})
          }.margin(10)
          .borderRadius(10)
          .backgroundColor(0xF9CF93)
        }, (index: Rects) => index.id.toString())
          // 当拖拽松手时，被拖拽项落位位置与拖拽前不同时触发，from为起始索引，to为目标索引
          .onMove((from:number, to:number) => {
            console.info("Grid onMove from " + from + " to " + to)
            // 更新数据源
            this.numbers.moveItem(from, to)
            if (from < to) {  // 被拖拽项索引小于目标位置索引
              // 先保存被拖拽项在irregularIndexes数组中的位置，避免后续循环更新产生重复值后indexOf定位错误
              let from_idx = -1
              if (this.layoutOptions.irregularIndexes?.includes(from)) {
                from_idx = this.layoutOptions.irregularIndexes.indexOf(from)
              }

              // 被拖拽项与目标位置之间的元素整体前移一位（索引-1）
              if (this.layoutOptions.irregularIndexes != undefined) {
                let len = this.layoutOptions.irregularIndexes.length
                for (let i = len - 1; i >= 0; i --) {
                  let irregularIndex = this.layoutOptions.irregularIndexes[i]
                  if (irregularIndex > from && irregularIndex <= to) {
                    this.layoutOptions.irregularIndexes[i] --
                  }
                }
              }

              // 若被拖拽项本身为不规则节点，更新其索引到目标位置
              if (from_idx != -1 && this.layoutOptions.irregularIndexes != undefined) {
                this.layoutOptions.irregularIndexes[from_idx] = to
              }
            } else {  // 被拖拽项索引大于等于目标位置索引
              // 先保存被拖拽项在irregularIndexes数组中的位置，避免后续循环更新产生重复值后indexOf定位错误
              let from_idx = -1
              if (this.layoutOptions.irregularIndexes?.includes(from)) {
                from_idx = this.layoutOptions.irregularIndexes.indexOf(from)
              }

              // 目标位置至被拖拽项之间的元素整体后移一位（索引+1）
              if (this.layoutOptions.irregularIndexes != undefined) {
                let len = this.layoutOptions.irregularIndexes.length
                for (let i = 0; i < len; i ++) {
                  let irregularIndex = this.layoutOptions.irregularIndexes[i]
                  if (irregularIndex >= to && irregularIndex < from) {
                    this.layoutOptions.irregularIndexes[i] ++
                  }
                }
              }

              // 若被拖拽项本身为不规则节点，更新其索引到目标位置
              if (from_idx != -1 && this.layoutOptions.irregularIndexes != undefined) {
                this.layoutOptions.irregularIndexes[from_idx] = to
              }
            }
            // 通过备份对象整体赋值，强制layoutOptions刷新生效
            this.layoutOptions_back.irregularIndexes = this.layoutOptions.irregularIndexes
            this.layoutOptions = this.layoutOptions_back
            console.info("Grid this.layoutOptions.irregularIndexes " + this.layoutOptions.irregularIndexes)
          },
            {
              onLongPress: (index: number) => {
                // GridItem长按浮起时触发
                console.info('Grid onLongPress: ' + index);
              },
              onDrop: (index: number) => {
                // 拖拽的GridItem松手时触发
                console.info('Grid onDrop: ' + index);
              },
              onDragStart: (index: number) => {
                // GridItem长按浮起并开始拖拽时触发
                console.info('Grid onDragStart: ' + index);
              },
              onMoveThrough: (from: number, to: number) => {
                // GridItem拖拽过程中持续触发
                console.info('Grid onMoveThrough From: ' + from + ' to: ' + to);
              }
            })
      }
      .columnsTemplate('1fr 1fr 1fr 1fr')   // 四列等宽布局
      .width('100%')
      .height('100%')
      .backgroundColor(0xFAEEE0)
    }
  }

  aboutToAppear(): void {
    // 初始化100个矩形数据并设置各不规则节点的跨占尺寸
    let list: Rects[] = [];
    for (let i = 0; i < 100; i++) {
      list.push(new Rects(i));
    }
    list[4].rectSize = [2, 2] // 2行2列
    list[5].rectSize = [1, 2] // 1行2列
    list[6].rectSize = [1, 2] // 1行2列
    list[7].rectSize = [2, 1] // 2行1列
    list[8].rectSize = [2, 1] // 2行1列
    list[13].rectSize = [1, 4]  // 1行4列
    this.numbers = new RectGridDataSource(list);
  }
}
```

### 示例6（Grid不规则布局使用Repeat的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了Repeat在Grid组件设置拖拽效果后触发的回调事件，Grid里存在不规则的GridItem。应用可通过irregularIndexes设置哪些索引是不规则节点，通过修改对应索引的rectSize调整该GridItem所占的行列数。

```TypeScript
// xxx.ets
class Rects {
  id: number = 0
  // rectSize表示该GridItem占用的[行, 列]数，默认[1, 1]为规则节点
  rectSize: [number, number] = [1, 1]
  constructor(id_: number) {
    this.id = id_
  }
}

@Entry
@ComponentV2
struct GridOnMoveExample {
  @Local arr: Array<Rects> = [];

  // 网格布局选项（实际生效），声明不规则节点的索引及各自占用的行列数
  @Local layoutOptions: GridLayoutOptions = {
    regularSize: [1, 1],
    irregularIndexes: [4, 5, 6, 7, 8, 13],   // 设置哪些索引对应的GridItem为不规则节点
    onGetIrregularSizeByIndex: (index: number) => {
      return this.arr[index].rectSize
    }
  };

  // 布局选项（备份），用于拖拽时通过整体赋值触发layoutOptions刷新
  layoutOptions_back: GridLayoutOptions = {
    regularSize: [1, 1],
    irregularIndexes: [4, 5, 6, 7, 8, 13],
    onGetIrregularSizeByIndex: (index: number) => {
      return this.arr[index].rectSize
    }
  };

  aboutToAppear(): void {
    // 初始化100个矩形数据
    for (let i = 0; i < 100; i++) {
      this.arr.push(new Rects(i));
    }
    // 设置各不规则节点的跨占尺寸
    this.arr[4].rectSize = [2, 2] // 2行2列
    this.arr[5].rectSize = [1, 2] // 1行2列
    this.arr[6].rectSize = [1, 2] // 1行2列
    this.arr[7].rectSize = [2, 1] // 2行1列
    this.arr[8].rectSize = [2, 1] // 2行1列
    this.arr[13].rectSize = [1, 4] // 1行4列
  }

  build() {
    Column() {
      Grid(undefined, this.layoutOptions) {
        Repeat<Rects>(this.arr)
        // 当拖拽松手时，被拖拽项落位位置与拖拽前不同时触发，from为起始索引，to为目标索引
          .onMove((from: number, to: number) => {
            if (from == to) {
              return
            }
            console.info("Grid onMove from " + from + " to " + to)
            // 更新this.arr数据源
            let tmp = this.arr.splice(from, 1);
            this.arr.splice(to, 0, tmp[0]);
            if (from < to) {  // 被拖拽项索引小于目标位置索引
              // 先保存被拖拽项在irregularIndexes数组中的位置，避免后续循环更新产生重复值后indexOf定位错误
              let from_idx = -1
              if (this.layoutOptions.irregularIndexes?.includes(from)) {
                from_idx = this.layoutOptions.irregularIndexes.indexOf(from)
              }

              // 被拖拽项与目标位置之间的元素整体前移一位（索引-1）
              if (this.layoutOptions.irregularIndexes != undefined) {
                let len = this.layoutOptions.irregularIndexes.length
                for (let i = len - 1; i >= 0; i --) {
                  let irregularIndex = this.layoutOptions.irregularIndexes[i]
                  if (irregularIndex > from && irregularIndex <= to) {
                    this.layoutOptions.irregularIndexes[i] --
                  }
                }
              }

              // 若被拖拽项本身为不规则节点，更新其索引到目标位置
              if (from_idx != -1 && this.layoutOptions.irregularIndexes != undefined) {
                this.layoutOptions.irregularIndexes[from_idx] = to
              }
            } else {  // 被拖拽项索引大于等于目标位置索引
              // 先保存被拖拽项在irregularIndexes数组中的位置，避免后续循环更新产生重复值后indexOf定位错误
              let from_idx = -1
              if (this.layoutOptions.irregularIndexes?.includes(from)) {
                from_idx = this.layoutOptions.irregularIndexes.indexOf(from)
              }

              // 目标位置至被拖拽项之间的元素整体后移一位（索引+1）
              if (this.layoutOptions.irregularIndexes != undefined) {
                let len = this.layoutOptions.irregularIndexes.length
                for (let i = 0; i < len; i ++) {
                  let irregularIndex = this.layoutOptions.irregularIndexes[i]
                  if (irregularIndex >= to && irregularIndex < from) {
                    this.layoutOptions.irregularIndexes[i] ++
                  }
                }
              }

              // 若被拖拽项本身为不规则节点，更新其索引到目标位置
              if (from_idx != -1 && this.layoutOptions.irregularIndexes != undefined) {
                this.layoutOptions.irregularIndexes[from_idx] = to
              }
            }
            // 通过备份对象整体赋值，强制layoutOptions刷新生效
            this.layoutOptions_back.irregularIndexes = this.layoutOptions.irregularIndexes
            this.layoutOptions = this.layoutOptions_back
            console.info("Grid this.layoutOptions.irregularIndexes " + this.layoutOptions.irregularIndexes)
          },
            {
              onLongPress: (index: number) => {
                // GridItem长按浮起时触发
                console.info('Grid onLongPress: ' + index);
              },
              onDrop: (index: number) => {
                // 拖拽的GridItem松手时触发
                console.info('Grid onDrop: ' + index);
              },
              onDragStart: (index: number) => {
                // GridItem长按浮起并开始拖拽时触发
                console.info('Grid onDragStart: ' + index);
              },
              onMoveThrough: (from: number, to: number) => {
                // GridItem拖拽过程中持续触发
                console.info('Grid onMoveThrough From: ' + from + ' to: ' + to);
              }
            })
          .each((obj: RepeatItem<Rects>) => {
            GridItem() {
              Text(obj.item.id.toString())
                .fontSize(16)
                .textAlign(TextAlign.Center)
                // 设置高度，跨行GridItem需额外增加外边距(规则GridItem的间距为2*10)用于界面对齐
                .size({ height: 100 * this.arr[obj.index].rectSize[0] + (this.arr[obj.index].rectSize[0] - 1) * 20, width: '100%' })
            }.margin(10)
            .borderRadius(10)
            .backgroundColor(0xF9CF93)
          })
          .key((item: Rects, index: number) => {
            return item.id.toString();
          })
          .virtualScroll({ totalCount: this.arr.length })   // 开启虚拟滚动，仅渲染可见项以提升性能
      }
      .columnsTemplate('1fr 1fr 1fr 1fr')   // 四列等宽布局
      .border({ width: 1 })
      .backgroundColor(0xFAEEE0)
      .width('100%')
      .height('100%')
    }
  }
}
```

该示例分别使用了不传参@Preview和传参的@Preview。

```TypeScript
@Entry
@Preview
@Component
struct Index {
  @State message: string = 'default Preview';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
    }
    .height('100%')
    .width('100%')
  }
}

@Preview({
  title: 'PreviewParams',
  width: 540,
  height: 1170
})
@Component
struct Test {
  @State message: string = 'PreviewParams';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontSize(40)
        .fontWeight(FontWeight.Bold)
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例1（触摸测试模式为Block和Transparent的触摸测试效果）

该示例通过设置不同的[HitTestMode](./ts-appendix-enums.md#hittestmode9)值演示了Block和Transparent的触摸测试效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct HitTestBehaviorExample {
  build() {
    // outer stack
    Stack() {
      Button('outer button')
        .onTouch((event) => {
          console.info(`outer button touched type: ${(event as TouchEvent).type}`);
        })
      // inner stack
      Stack() {
        Button('inner button')
          .onTouch((event) => {
            console.info(`inner button touched type: ${(event as TouchEvent).type}`);
          })
      }
      .width('100%').height('100%')
      // 设置触摸测试类型为Block，自身响应触摸测试但阻止兄弟节点参与触摸测试
      .hitTestBehavior(HitTestMode.Block)
      .onTouch((event) => {
        console.info(`stack touched type: ${(event as TouchEvent).type}`);
      })

      Text('Transparent')
        // 设置触摸测试类型为Transparent，自身不拦截触摸测试，允许下层节点响应触摸测试
        .hitTestBehavior(HitTestMode.Transparent)
        .width('100%').height('100%')
        .onTouch((event) => {
          console.info(`text touched type: ${(event as TouchEvent).type}`);
        })
    }.width(300).height(300)
  }
}
```

### 示例2（触摸测试类型为BLOCK_HIERARCHY时的触摸测试效果）

从API version 20开始，该示例演示了设置触摸测试模式为BLOCK_HIERARCHY时的触摸测试效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct BlockHierarchy {
  build() {
    // outer stack
    Stack() {
      Stack() {
        Button('outer button')
          .onTouch((event) => {
            console.info(`HitTestMode outer button touched type: ${(event as TouchEvent).type}`);
          })
          .width(200)
          .height(200)
          .backgroundColor('#D5D5D5')
        // inner stack
        Stack() {
          Button()
            .id('button150')
            .backgroundColor('#F7F7F7')
            .width(150)
            .height(150)
            .onTouch((event) => {
              console.info(`HitTestMode button150 touched type: ${(event as TouchEvent).type}`);
            })
            .hitTestBehavior(HitTestMode.Transparent)
          Button()
            .id('button100')
            .backgroundColor('#707070')
            .width(100)
            .height(100)
            .onTouch((event) => {
              console.info(`HitTestMode button100 touched type: ${(event as TouchEvent).type}`);
            })
            .hitTestBehavior(HitTestMode.Transparent)
          Button()
            .id('button050')
            .backgroundColor('#D5D5D5')
            .width(50)
            .height(50)
            .onTouch((event) => {
              console.info(`HitTestMode button050 touched type: ${(event as TouchEvent).type}`);
            })
            .hitTestBehavior(HitTestMode.Transparent)
        }
        .width('100%').height('100%')
        // 设置触摸测试模式，自身和子节点响应触摸测试，阻止所有优先级较低的兄弟节点和父节点参与触摸测试
        .hitTestBehavior(HitTestMode.BLOCK_HIERARCHY)
        .onTouch((event) => {
          console.info(`HitTestMode stack touched type: ${(event as TouchEvent).type}`);
        })

        Text('Transparent')
          .hitTestBehavior(HitTestMode.Transparent)
          .width('100%').height('100%')
          .onTouch((event) => {
            console.info(`HitTestMode text touched type: ${(event as TouchEvent).type}`);
          })
      }.width(300).height(300)
      .borderWidth(2)
      .onTouch((event) => {
        console.info(`HitTestMode father stack touched type: ${(event as TouchEvent).type}`);
      })
    }.width(500).height(500)
    .borderWidth(2)
    .onTouch((event) => {
      console.info(`HitTestMode grandfather stack touched type: ${(event as TouchEvent).type}`);
    })
  }
}
```

### 示例3（触摸测试类型为BLOCK_DESCENDANTS时的触摸测试效果）

从API version 20开始，该示例演示了设置触摸测试模式为BLOCK_DESCENDANTS时的触摸测试效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct BlockDescendants {
  build() {
    // outer stack
    Stack() {
      Stack() {
        Button('outer button')
          .onTouch((event) => {
            console.info(`HitTestMode outer button touched type: ${(event as TouchEvent).type}`);
          })
          .width(200)
          .height(200)
          .backgroundColor('#D5D5D5')
        // inner stack
        Stack() {
          Button('inner button')
            .width(100)
            .height(100)
            .onTouch((event) => {
              console.info(`HitTestMode inner button touched type: ${(event as TouchEvent).type}`);
            })
        }
        .width('100%').height('100%')
        // 设置触摸测试模式，自身不响应触摸测试，并且所有的后代（孩子、孙子等）也不响应触摸测试，不会影响祖先节点的触摸测试
        .hitTestBehavior(HitTestMode.BLOCK_DESCENDANTS)
        .onTouch((event) => {
          console.info(`HitTestMode stack touched type: ${(event as TouchEvent).type}`);
        })

        Text('Transparent')
          .hitTestBehavior(HitTestMode.Transparent)
          .width('100%').height('100%')
          .onTouch((event) => {
            console.info(`HitTestMode text touched type: ${(event as TouchEvent).type}`);
          })
      }.width(300).height(300)
      .borderWidth(2)
      .onTouch((event) => {
        console.info(`HitTestMode father stack touched type: ${(event as TouchEvent).type}`);
      })
    }.width(500).height(500)
    .borderWidth(2)
    .onTouch((event) => {
      console.info(`HitTestMode grandfather stack touched type: ${(event as TouchEvent).type}`);
    })
  }
}
```

### 示例4（Stack组件中多节点重合时的触摸测试效果）

该示例演示了在Stack组件中存在多节点触摸区域重叠时的触摸测试效果。此时设置[HitTestMode](./ts-appendix-enums.md#hittestmode9)为None时，重叠的背景区域无法响应触摸测试；只有设置为Transparent时，背景区域才能响应触摸测试。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State @Watch('onModeChange') mode: number = HitTestMode.None;
  @State modeStr: string = 'None';

  onModeChange() {
    this.modeStr = this.mode === HitTestMode.None ? 'None' : 'Transparent';
  }

  build() {
    Stack() {
      Column()
        .height('100%')
        .width('100%')
        .onTouch(() => {
          console.info('background hit test!');
        })
      Stack() {
        // 点击按钮进行触摸测试
        Button('HitTest')
        // 点击按钮切换不同的触摸测试模式
        Button('HitTestMode: ' + this.modeStr)
          .margin({ top: 100 })
          .onClick(() => {
            this.mode = this.mode === HitTestMode.None ?
              HitTestMode.Transparent : HitTestMode.None;
          })
      }
      .height('100%')
      .width('100%')
      // 只有上层节点的HitTestMode设置为Transparent时，下层节点才能响应触摸测试
      .hitTestBehavior(this.mode)
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例1（使用全屏模态转场）

该示例主要演示通过bindContentCover来实现全屏模态转场。



```TypeScript
// xxx.ets
@Entry
@Component
struct ModalTransitionExample {
  @State isShow: boolean = false;
  @State isShow2: boolean = false;

  @Builder
  myBuilder2() {
    Column() {
      Button('close modal 2')
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow2 = false;
        })
    }
    .width('100%')
    .height('100%')
  }

  @Builder
  myBuilder() {
    Column() {
      Button("transition modal 2")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow2 = true;
        }).bindContentCover(this.isShow2, this.myBuilder2(), {
        modalTransition: ModalTransition.NONE,
        backgroundColor: Color.Orange,
        onWillAppear: () => {
          console.info('BindContentCover onWillAppear.');
        },
        onAppear: () => {
          console.info("BindContentCover onAppear.");
        },
        onWillDisappear: () => {
          console.info("BindContentCover onWillDisappear.");
        },
        onDisappear: () => {
          console.info("BindContentCover onDisappear.");
        }
      })

      Button("close modal 1")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow = false;
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindContentCover(this.isShow, this.myBuilder(), {
          modalTransition: ModalTransition.NONE,
          backgroundColor: Color.Pink,
          onWillAppear: () => {
            console.info("BindContentCover onWillAppear.");
          },
          onAppear: () => {
            console.info("BindContentCover onAppear.");
          },
          onWillDisappear: () => {
            console.info("BindContentCover onWillDisappear.");
          },
          onDisappear: () => {
            console.info("BindContentCover onDisappear.");
          }
        })
    }
    .justifyContent(FlexAlign.Center)
    .backgroundColor("#ff49c8ab")
    .width('100%')
    .height('100%')
  }
}
```

### 示例2（自定义转场动画）

全屏模态无动画转场模式下，自定义转场动画。



```TypeScript
// xxx.ets
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct ModalTransitionExample {
  @State @Watch("isShow1Change") isShow: boolean = false;
  @State @Watch("isShow2Change") isShow2: boolean = false;
  @State scale1: number = 1;
  @State scale2: number = 1;

  isShow1Change() {
    this.isShow ? this.scale1 = 0.95 : this.scale1 = 1;
  }

  isShow2Change() {
    this.isShow2 ? this.scale2 = 0.95 : this.scale2 = 1;
  }

  @Builder
  myBuilder2() {
    Column() {
      Button('close modal 2')
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow2 = false;
        })
    }
    .width('100%')
    .height('100%')
  }

  @Builder
  myBuilder() {
    Column() {
      Button('transition modal 2')
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow2 = true;
        }).bindContentCover(this.isShow2, this.myBuilder2(), {
        modalTransition: ModalTransition.NONE,
        backgroundColor: Color.Orange,
        onWillAppear: () => {
          console.info("BindContentCover onWillAppear.");
        },
        onAppear: () => {
          console.info("BindContentCover onAppear.");
        },
        onWillDisappear: () => {
          console.info("BindContentCover onWillDisappear.");
        },
        onDisappear: () => {
          console.info("BindContentCover onDisappear.");
        }
      })

      Button('close modal 1')
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow = false;
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .scale({ x: this.scale2, y: this.scale2 })
    .animation({ curve: curves.springMotion() })
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindContentCover(this.isShow, this.myBuilder(), {
          modalTransition: ModalTransition.NONE,
          backgroundColor: Color.Pink,
          onWillAppear: () => {
            console.info("BindContentCover onWillAppear.");
          },
          onAppear: () => {
            console.info("BindContentCover onAppear.");
          },
          onWillDisappear: () => {
            console.info("BindContentCover onWillDisappear.");
          },
          onDisappear: () => {
            console.info("BindContentCover onDisappear.");
          }
        })
    }
    .justifyContent(FlexAlign.Center)
    .backgroundColor("#ff49c8ab")
    .width('100%')
    .height('100%')
    .scale({ x: this.scale1, y: this.scale1 })
    .animation({ curve: curves.springMotion() })
  }
}
```

### 示例3（上下切换转场）

全屏模态上下切换转场。



```TypeScript
// xxx.ets
@Entry
@Component
struct ModalTransitionExample {
  @State isShow: boolean = false;
  @State isShow2: boolean = false;

  @Builder
  myBuilder2() {
    Column() {
      Button('close modal 2')
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow2 = false;
        })
    }
    .width('100%')
    .height('100%')
  }

  @Builder
  myBuilder() {
    Column() {
      Button('transition modal 2')
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow2 = true;
        }).bindContentCover(this.isShow2, this.myBuilder2(), {
        modalTransition: ModalTransition.DEFAULT,
        backgroundColor: Color.Gray,
        onWillAppear: () => {
          console.info("BindContentCover onWillAppear.");
        },
        onAppear: () => {
          console.info("BindContentCover onAppear.");
        },
        onWillDisappear: () => {
          console.info("BindContentCover onWillDisappear.");
        },
        onDisappear: () => {
          console.info("BindContentCover onDisappear.");
        }
      })

      Button('close modal 1')
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow = false;
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindContentCover(this.isShow, this.myBuilder(), {
          modalTransition: ModalTransition.DEFAULT,
          backgroundColor: Color.Pink,
          onWillAppear: () => {
            console.info("BindContentCover onWillAppear.");
          },
          onAppear: () => {
            console.info("BindContentCover onAppear.");
          },
          onWillDisappear: () => {
            console.info("BindContentCover onWillDisappear.");
          },
          onDisappear: () => {
            console.info("BindContentCover onDisappear.");
          }
        })
    }
    .justifyContent(FlexAlign.Center)
    .backgroundColor(Color.White)
    .width('100%')
    .height('100%')
  }
}
```

### 示例4（透明度渐变转场）

全屏模态透明度渐变转场。



```TypeScript
// xxx.ets
@Entry
@Component
struct ModalTransitionExample {
  @State isShow: boolean = false;
  @State isShow2: boolean = false;

  @Builder
  myBuilder2() {
    Column() {
      Button('close modal 2')
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow2 = false;
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }

  @Builder
  myBuilder() {
    Column() {
      Button('transition modal 2')
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow2 = true;
        }).bindContentCover(this.isShow2, this.myBuilder2(), {
        modalTransition: ModalTransition.ALPHA,
        backgroundColor: Color.Gray,
        onWillAppear: () => {
          console.info("BindContentCover onWillAppear.");
        },
        onAppear: () => {
          console.info("BindContentCover onAppear.");
        },
        onWillDisappear: () => {
          console.info("BindContentCover onWillDisappear.");
        },
        onDisappear: () => {
          console.info("BindContentCover onDisappear.");
        }
      })

      Button('close modal 1')
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow = false;
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindContentCover(this.isShow, this.myBuilder(), {
          modalTransition: ModalTransition.ALPHA,
          backgroundColor: Color.Pink,
          onWillAppear: () => {
            console.info("BindContentCover onWillAppear.");
          },
          onAppear: () => {
            console.info("BindContentCover onAppear.");
          },
          onWillDisappear: () => {
            console.info("BindContentCover onWillDisappear.");
          },
          onDisappear: () => {
            console.info("BindContentCover onDisappear.");
          }
        })
    }
    .justifyContent(FlexAlign.Center)
    .backgroundColor(Color.White)
    .width('100%')
    .height('100%')
  }
}
```

### 示例5（设置不同效果的自定义转场）

该示例主要演示全屏模态旋转、平移等自定义转场。



```TypeScript
// xxx.ets
@Entry
@Component
struct ModalTransitionExample {
  @State isShow: boolean = false;
  @State isShow2: boolean = false;

  @Builder
  myBuilder2() {
    Column() {
      Button("Close Modal 2")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow2 = false;
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }

  @Builder
  myBuilder() {
    Column() {
      Button("Transition Modal 2")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow2 = true;
        })
        .bindContentCover(
          this.isShow2,
          this.myBuilder2(),
          {
            modalTransition: ModalTransition.DEFAULT,
            backgroundColor: Color.Gray,
            transition: TransitionEffect.SLIDE.animation({ duration: 5000, curve: Curve.LinearOutSlowIn }),
            // 处理关闭原因后调用dismiss()关闭模态
            onWillDismiss: ((dismissContentCoverAction: DismissContentCoverAction) => {
              if (dismissContentCoverAction.reason === DismissReason.PRESS_BACK) {
                console.info("BindContentCover dismiss reason is back pressed");
              }
              dismissContentCoverAction.dismiss();
            }),
            onAppear: () => {
              console.info("BindContentCover onAppear.");
            },
            // 模态消失时同步状态变量
            onDisappear: () => {
              this.isShow2 = false;
              console.info("BindContentCover onDisappear.");
            }
          })

      Button("Close Modal 1")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow = false;
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }

  build() {
    Column() {
      Button("Transition Modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindContentCover(
          this.isShow,
          this.myBuilder(),
          {
            modalTransition: ModalTransition.DEFAULT,
            backgroundColor: Color.Pink,
            transition: TransitionEffect.asymmetric(
              TransitionEffect.OPACITY.animation({ duration: 1100 }).combine(
                TransitionEffect.rotate({ z: 1, angle: 180 }).animation({ delay: 1000, duration: 1000 }))
              ,
              TransitionEffect.OPACITY.animation({ duration: 1200 }).combine(
                TransitionEffect.rotate({ z: 1, angle: 180 }).animation({ duration: 1300 }))
            ),
            onWillDismiss: ((dismissContentCoverAction: DismissContentCoverAction) => {
              if (dismissContentCoverAction.reason === DismissReason.PRESS_BACK) {
                console.info("back pressed");
              }
              dismissContentCoverAction.dismiss();
            }),
            onAppear: () => {
              console.info("BindContentCover onAppear.");
            },
            onDisappear: () => {
              this.isShow = false;
              console.info("BindContentCover onDisappear.");
            }
          })
    }
    .justifyContent(FlexAlign.Center)
    .backgroundColor(Color.White)
    .width('100%')
    .height('100%')
  }
}
```

### 示例6（设置全屏模态适配安全区）

从API version 20开始，该示例主要演示设置enableSafeArea为true后全屏模态适配安全区的内容效果。全屏模态容器的背景色为浅蓝色，内容颜色为灰色，内容在安全区内布局。

```TypeScript
// xxx.ets
@Entry
@Component
struct SafeAreaController {
  @State isShow: boolean = false;
  @State isSafeArea: boolean | undefined = true;
  @State heightMode: string = '100%';

  @Builder
  myBuilder() {
    Column() {
      Column() {
        Button("Content")
          .fontSize(20)
      }
      .width('100%')
      .height('50%')
      .borderRadius(10)
      .borderStyle(BorderStyle.Dotted)
      .borderWidth(2)
      Column() {
        Button("Content")
          .margin({top:340})
          .fontSize(20)
      }
      .width('100%')
      .height('50%')
      .borderRadius(10)
      .borderStyle(BorderStyle.Dotted)
      .borderWidth(2)
    }
    .backgroundColor(Color.Grey)
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height(this.heightMode)
  }
  build() {
    Column() {
      Button("Open ContentCover")
        .onClick(() => this.isShow = true)
        .fontSize(20)
        .margin(10)
        .bindContentCover(this.isShow, this.myBuilder(), {
          modalTransition: ModalTransition.ALPHA,
          backgroundColor: 0xFF87CEEB,
          // 动态设置安全区域模式
          enableSafeArea: this.isSafeArea
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

### 示例1（设置组件获焦和走焦的效果）

该示例通过配置[defaultFocus](#defaultfocus9)可以使绑定的组件成为[层级页面](../../../ui/arkts-common-events-focus-event.md#基础概念)创建后首次获焦的焦点，配置[groupDefaultFocus](arkts-arkui-common-comp-commonmethod-c.md#groupdefaultfocus)可以使绑定的组件成为tabIndex容器创建后首次获焦的焦点，配置[focusOnTouch](arkts-arkui-common-comp-commonmethod-c.md#focusontouch)可以使绑定的组件点击后立即获焦。

示意图：

首次进入时，焦点默认在defaultFocus绑定的TextInput组件上：



首次按Tab键，焦点切换到tabIndex(1)的容器上，且自动走焦到内部第一个可获焦组件上：



第二次按Tab键，焦点切换到tabIndex(2)的容器上，且自动走焦到其内部的groupDefaultFocus绑定的组件上：



第三次按Tab键，焦点切换到tabIndex(3)的容器上，且自动走焦到内部配置了defaultFocus的组件上：



点击绑定了focusOnTouch的组件，组件自身获焦，焦点框被清除，再按下Tab键后，显示焦点框：



```TypeScript
// focusTest.ets
@Entry
@Component
struct FocusableExample {
  @State inputValue: string = '';

  build() {
    Scroll() {
      Row({ space: 20 }) {
        Column({ space: 20 }) {
          Column({ space: 5 }) {
            Button('Group1')
              .width(165)
              .height(40)
              .fontColor(Color.White)
              .focusOnTouch(true) // 该Button组件点击后可获焦
            Row({ space: 5 }) {
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
                .focusOnTouch(true) // 该Button组件点击后可获焦
            }

            Row({ space: 5 }) {
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
            }
          }.borderWidth(2).borderColor(Color.Red).borderStyle(BorderStyle.Dashed)
          .tabIndex(1) // 该Column组件为按Tab键走焦的第一个获焦的组件
          Column({ space: 5 }) {
            Button('Group2')
              .width(165)
              .height(40)
              .fontColor(Color.White)
            Row({ space: 5 }) {
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
                .groupDefaultFocus(true) // 该Button组件上级Column组件获焦时获焦
            }

            Row({ space: 5 }) {
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
            }
          }.borderWidth(2).borderColor(Color.Green).borderStyle(BorderStyle.Dashed)
          .tabIndex(2) // 该Column组件为按Tab键走焦的第二个获焦的组件
        }

        Column({ space: 5 }) {
          TextInput({ placeholder: 'input', text: this.inputValue })
            .onChange((value: string) => {
              this.inputValue = value;
            })
            .width(156)
            .defaultFocus(true) // 该TextInput组件为层级页面的初始默认焦点
          Button('Group3')
            .width(165)
            .height(40)
            .fontColor(Color.White)
          Row({ space: 5 }) {
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
          }

          Button()
            .width(165)
            .height(40)
            .fontColor(Color.White)
          Row({ space: 5 }) {
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
          }

          Button()
            .width(165)
            .height(40)
            .fontColor(Color.White)
          Row({ space: 5 }) {
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
          }
        }.borderWidth(2).borderColor(Color.Orange).borderStyle(BorderStyle.Dashed)
        .tabIndex(3) // 该Column组件为按Tab键走焦的第三个获焦的组件
      }.alignItems(VerticalAlign.Top)
    }
  }
}
```

### 示例2（设置指定组件获焦）

该示例通过配置[focusControl.requestFocus](#requestfocus9)使指定组件获取焦点。

示意图：

按下Tab键，激活焦点态显示。

申请不存在的组件获焦：



申请不可获焦的组件获焦：



申请存在且可获焦的组件获焦：



```TypeScript
// requestFocus.ets
@Entry
@Component
struct RequestFocusExample {
  @State idList: string[] = ['A', 'B', 'C', 'D', 'E', 'F', 'LastPageId'];
  @State selectId: string = 'LastPageId';

  build() {
    Column({ space: 20 }) {
      Row({ space: 5 }) {
        Button('id: ' + this.idList[0] + ' focusable(false)')
          .width(180)
          .height(70)
          .fontColor(Color.White)
          .id(this.idList[0])
          .focusable(false)
        Button('id: ' + this.idList[1])
          .width(180).height(70).fontColor(Color.White)
          .id(this.idList[1])
      }

      Row({ space: 5 }) {
        Button('id: ' + this.idList[2])
          .width(180).height(70).fontColor(Color.White)
          .id(this.idList[2])
        Button('id: ' + this.idList[3])
          .width(180).height(70).fontColor(Color.White)
          .id(this.idList[3])
      }

      Row({ space: 5 }) {
        Button('id: ' + this.idList[4])
          .width(180).height(70).fontColor(Color.White)
          .id(this.idList[4])
        Button('id: ' + this.idList[5])
          .width(180).height(70).fontColor(Color.White)
          .id(this.idList[5])
      }

      Row({ space: 5 }) {
        Select([{ value: this.idList[0] },
          { value: this.idList[1] },
          { value: this.idList[2] },
          { value: this.idList[3] },
          { value: this.idList[4] },
          { value: this.idList[5] },
          { value: this.idList[6] }])
          .value(this.selectId)
          .onSelect((index: number) => {
            this.selectId = this.idList[index];
          })
        Button('RequestFocus')
          .width(180).height(70).fontColor(Color.White)
          .onClick(() => {
            // 建议使用this.getUIContext().getFocusController().requestFocus()
            let res = focusControl.requestFocus(this.selectId); // 使选中的this.selectId的组件获焦
            if (res) {
              this.getUIContext().getPromptAction().showToast({ message: 'Request success' })
            } else {
              this.getUIContext().getPromptAction().showToast({ message: 'Request failed' })
            }
          })
      }
    }.width('100%').margin({ top: 20 })
  }
}
```

### 示例3（设置焦点框样式）

该示例通过配置[focusBox](#focusbox12)修改组件的焦点框样式。



```TypeScript
import { ColorMetrics, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct FocusBoxExample {
  build() {
    Column({ space: 30 }) {
      Button('small black focus box')
        .focusBox({
          margin: new LengthMetrics(0),
          strokeColor: ColorMetrics.rgba(0, 0, 0),
        })
      Button('large red focus box')
        .focusBox({
          margin: LengthMetrics.px(20),
          strokeColor: ColorMetrics.rgba(255, 0, 0),
          strokeWidth: LengthMetrics.px(10)
        })
    }
    .alignItems(HorizontalAlign.Center)
    .width('100%')
  }
}
```

### 示例4（设置焦点组走焦）

该示例通过配置[focusScopePriority](arkts-arkui-common-comp-commonmethod-c.md#focusscopepriority)，可以使绑定的组件在所属容器首次获焦时成为焦点，配置[focusScopeId](arkts-arkui-common-comp-commonmethod-c.md#focusscopeid)，可以使绑定的容器组件成为焦点组。

示意图：

首次按下Tab键时，焦点转移到容器1中绑定focusScopePriority的组件上。



继续按下Tab键，焦点转移到容器1下一个组件上。



再次按下Tab键，焦点转移到容器1下一个组件上。



继续按下Tab键，焦点转移到容器2中配置了focusScopePriority的组件上。



继续按下Tab键，焦点转移到容器1中名为Group1的组件上。



```TypeScript
// focusTest.ets
@Entry
@Component
struct FocusableExample {
  @State inputValue: string = '';

  build() {
    Scroll() {
      Row({ space: 20 }) {
        Column({ space: 20 }) { // 标记为Column1
          Column({ space: 5 }) {
            Button('Group1')
              .width(165)
              .height(40)
              .fontColor(Color.White)
            Row({ space: 5 }) {
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
            }

            Row({ space: 5 }) {
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
            }
          }.borderWidth(2).borderColor(Color.Red).borderStyle(BorderStyle.Dashed)

          Column({ space: 5 }) {
            Button('Group2')
              .width(165)
              .height(40)
              .fontColor(Color.White)
            Row({ space: 5 }) {
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
                .focusScopePriority('ColumnScope1', FocusPriority.PRIOR) // Column1首次获焦时获焦
            }

            Row({ space: 5 }) {
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
              Button()
                .width(80)
                .height(40)
                .fontColor(Color.White)
            }
          }.borderWidth(2).borderColor(Color.Green).borderStyle(BorderStyle.Dashed)
        }
        .focusScopeId('ColumnScope1')

        Column({ space: 5 }) { // 标记为Column2
          TextInput({ placeholder: 'input', text: this.inputValue })
            .onChange((value: string) => {
              this.inputValue = value
            })
            .width(156)
          Button('Group3')
            .width(165)
            .height(40)
            .fontColor(Color.White)
          Row({ space: 5 }) {
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
          }

          Button()
            .width(165)
            .height(40)
            .fontColor(Color.White)
            .focusScopePriority('ColumnScope2', FocusPriority.PREVIOUS) // Column2获焦时获焦
          Row({ space: 5 }) {
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
          }

          Button()
            .width(165)
            .height(40)
            .fontColor(Color.White)
          Row({ space: 5 }) {
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
            Button()
              .width(80)
              .height(40)
              .fontColor(Color.White)
          }
        }.borderWidth(2).borderColor(Color.Orange).borderStyle(BorderStyle.Dashed)
        .focusScopeId('ColumnScope2', true) // Column2为焦点组
      }.alignItems(VerticalAlign.Top)
    }
  }
}
```

### 示例5（设置Tab走焦停留）

该示例通过配置[tabStop](arkts-arkui-common-comp-commonmethod-c.md#tabstop)实现使用Tab走焦停留在组件上。

示意图：

连续按下两次Tab键，焦点转移到button2上。



接着按下Tab键，焦点转移到配置了tabStop的组件。



再按下Enter键，焦点转移至内部button3上。



再按下ESC键，焦点转移到配置了tabStop的组件上。



再按下Tab键，焦点循环走焦到button1上。



```TypeScript
import { ColorMetrics, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct TabStop {
  build() {
    Column({ space: 20 }) {
      Column({ space: 20 }) {
        Column({ space: 20 }) {
          Row({ space: 5 }) {
            Button('button 1')
              .width(200).height(70).fontColor(Color.White)
              .focusBox({
                margin: LengthMetrics.px(20),
                strokeColor: ColorMetrics.rgba(23, 169, 141),
                strokeWidth: LengthMetrics.px(10)
              })
          }

          Row({ space: 5 }) {
            Button('button 2')
              .width(200).height(70).fontColor(Color.White)
              .focusBox({
                margin: LengthMetrics.px(20),
                strokeColor: ColorMetrics.rgba(23, 169, 141),
                strokeWidth: LengthMetrics.px(10)
              })
          }
        }.width('80%').margin({ top: 30 }).borderColor(Color.Black)
      }.width('95%').margin({ top: 60 }).borderColor(Color.Black)

      Column({ space: 20 }) {
        Column({ space: 20 }) {
          Row({ space: 5 }) {
            Button('button 3')
              .width(200)
              .height('70%')
              .fontColor(Color.White)
              .focusBox({
                margin: LengthMetrics.px(20),
                strokeColor: ColorMetrics.rgba(23, 169, 141),
                strokeWidth: LengthMetrics.px(10)
              })
              .margin({ top: 15 })
          }
        }
        .width('80%')
        .height(120)
        .borderColor(Color.Black)
        .margin({ top: 10 })
        .tabStop(true)
        .focusBox({
          margin: LengthMetrics.px(20),
          strokeColor: ColorMetrics.rgba(23, 169, 141),
          strokeWidth: LengthMetrics.px(10)
        })
        .borderWidth(1)
      }.width('95%').margin({ top: 50 }).borderColor(Color.Black)
    }
  }
}
```

### 示例6（设置自定义走焦）

从API version 18开始，该示例通过配置[nextFocus](arkts-arkui-common-comp-commonmethod-c.md#nextfocus)实现自定义走焦规则。

如果不配置[nextFocus](arkts-arkui-common-comp-commonmethod-c.md#nextfocus)，默认的按下Tab键的走焦顺序为：M->A->B->C->D->E->F；配置了[nextFocus](arkts-arkui-common-comp-commonmethod-c.md#nextfocus)以后，走焦顺序变更为：M->D->F->B->C。

```TypeScript
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
  applyNormalAttribute(instance: ButtonAttribute): void {
    instance.id('M');
    instance.nextFocus({ forward: 'D', up: 'C', down: 'D' });
  }
}

@Entry
@Component
struct Index {
  @State modifier: MyButtonModifier = new MyButtonModifier();
  @State idList: string[] = ['A', 'B', 'C', 'D', 'E', 'F'];

  build() {
    Column({ space: 10 }) {
      Row({ space: 10 }) {
        Button('id: M')
          .attributeModifier(this.modifier)
        Button('id: ' + this.idList[0])
          .id(this.idList[0])
          .nextFocus({
            forward: 'C',
            backward: 'M',
            up: 'E',
            right: 'F',
            down: 'B',
            left: 'D'
          });
        Button('id: ' + this.idList[1])
          .id(this.idList[1])
      }

      Column({ space: 10 }) {
        Button('id: ' + this.idList[2])
          .id(this.idList[2]);
        Button('id: ' + this.idList[3])
          .id(this.idList[3])
          .nextFocus({ forward: 'F' });
      }

      Row({ space: 10 }) {
        Button('id: ' + this.idList[4])
          .id(this.idList[4]);
        Button('id: ' + this.idList[5])
          .id(this.idList[5])
          .nextFocus({ forward: 'B' });
      }
    }
  }
}
```

该示例通过Text组件设置组件尺寸变化事件，当Text尺寸变化时可以触发onSizeChange事件，获取oldValue和newValue参数。

```TypeScript
// xxx.ets
@Entry
@Component
struct AreaExample {
  @State value: string = 'Text'
  @State sizeValue: string = ''

  build() {
    Column() {
      Text(this.value)
        .backgroundColor(Color.Green)
        .margin(30)
        .fontSize(20)
        .onClick(() => {
          this.value = this.value + 'Text';
        })
        .onSizeChange((oldValue: SizeOptions, newValue: SizeOptions) => {
          console.info(`Ace: on size change, oldValue is ${JSON.stringify(oldValue)} newValue is ${JSON.stringify(newValue)}`);
          this.sizeValue = JSON.stringify(newValue);
        })
      Text('new area is: \n' + this.sizeValue).margin({ right: 30, left: 30 })
    }
    .width('100%').height('100%').margin({ top: 30 })
  }
}
```

### 示例1（使用onAreaChange监听区域变化）

该示例通过Text组件设置组件区域变化事件，当Text布局变化时可以触发onAreaChange事件，获取相关参数。



```TypeScript
// xxx.ets
@Entry
@Component
struct AreaExample {
  @State value: string = 'Text';
  @State sizeValue: string = '';

  build() {
    Column() {
      Text(this.value)
        .backgroundColor(Color.Green)
        .margin(30)
        .fontSize(20)
        .onClick(() => {
          this.value = this.value + 'Text';
        })
        .onAreaChange((oldValue: Area, newValue: Area) => {
          console.info(`Ace: on area change, oldValue is ${JSON.stringify(oldValue)} newValue is ${JSON.stringify(newValue)}`);
          this.sizeValue = JSON.stringify(newValue);
        })
      Text('new area is: \n' + this.sizeValue).margin({ right: 30, left: 30 })
    }
    .width('100%').height('100%').margin({ top: 30 })
  }
}
```

### 示例2（使用onAreaChange自定义间隔监听区域变化）

该示例通过设置[expectedUpdateInterval](arkts-arkui-common-comp-areachangeoptions-i.md)，当Text布局变化时可以触发[onAreaChange](#onareachange-1)事件，达到间隔回调的效果。

从API版本26.0.0开始，新增[onAreaChange](#onareachange-1)、[AreaChangeCallback](arkts-arkui-common-comp-areachangecallback-t.md)和[AreaChangeOptions](arkts-arkui-common-comp-areachangeoptions-i.md)。

```TypeScript
// xxx.ets
@Entry
@Component
struct AreaExample {
  @State value: string = 'Text';
  @State sizeValue: string = '';

  build() {
    Column() {
      Text(this.value)
        .backgroundColor(Color.Green)
        .margin(30)
        .fontSize(20)
        .onClick(() => {
          this.value = this.value + 'Text';
        })
        // 当设置expectedUpdateInterval时，区域变化的回调会按照设置的时间间隔触发。
        .onAreaChange((oldValue: Area, newValue: Area) => {
          console.info(`ACE: on area change, oldValue is ${JSON.stringify(oldValue)} newValue is ${JSON.stringify(newValue)}`);
          this.sizeValue = JSON.stringify(newValue);
        }, {expectedUpdateInterval: 1000})
      Text('new area is: \n' + this.sizeValue).margin({ right: 30, left: 30 })
    }
    .width('100%').height('100%').margin({ top: 30 })
  }
}
```

### 示例1（使用外描边属性）

该示例主要演示如何通过[outline](arkts-arkui-common-comp-commonmethod-c.md#outline)来实现组件外描边。



```TypeScript
// xxx.ets
@Entry
@Component
struct OutlineExample {
  build() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceAround, alignItems: ItemAlign.Center }) {
        // 虚线
        Text('DASHED')
          .backgroundColor(Color.Pink)
          .outlineStyle(OutlineStyle.DASHED).outlineWidth(5).outlineColor(0xAFEEEE).outlineRadius(10)
          .width(120).height(120).textAlign(TextAlign.Center).fontSize(16)
        // 点线
        Text('DOTTED')
          .backgroundColor(Color.Pink)
          .outline({ width: 5, color: 0x317AF7, radius: 10, style: OutlineStyle.DOTTED })
          .width(120).height(120).textAlign(TextAlign.Center).fontSize(16)
      }.width('100%').height(150)

      Text('.outline')
        .backgroundColor(Color.Pink)
        .fontSize(50)
        .width(300)
        .height(300)
        .outline({
          width: { left: 3, right: 6, top: 10, bottom: 15 },
          color: { left: '#e3bbbb', right: Color.Blue, top: Color.Red, bottom: Color.Green },
          radius: { topLeft: 10, topRight: 20, bottomLeft: 40, bottomRight: 80 },
          style: {
            left: OutlineStyle.DOTTED,
            right: OutlineStyle.DOTTED,
            top: OutlineStyle.SOLID,
            bottom: OutlineStyle.DASHED
          }
        }).textAlign(TextAlign.Center)
    }
  }
}
```

### 示例2（使用LocalizedEdgeColors类型）

该示例将[outline](arkts-arkui-common-comp-commonmethod-c.md#outline)属性中的color属性值设置为[LocalizedEdgeColors](ts-types.md#localizededgecolors12)类型。

```TypeScript
// xxx.ets

@Entry
@Component
struct OutlineExample {
  build() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceAround, alignItems: ItemAlign.Center }) {
        // 虚线
        Text('DASHED')
          .backgroundColor(Color.Pink)
          .outlineStyle(OutlineStyle.DASHED).outlineWidth(5).outlineColor(0xAFEEEE).outlineRadius(10)
          .width(120).height(120).textAlign(TextAlign.Center).fontSize(16)
        // 点线
        Text('DOTTED')
          .backgroundColor(Color.Pink)
          .outline({ width: 5, color: 0x317AF7, radius: 10, style: OutlineStyle.DOTTED })
          .width(120).height(120).textAlign(TextAlign.Center).fontSize(16)
      }.width('100%').height(150)

      Text('.outline')
        .backgroundColor(Color.Pink)
        .fontSize(50)
        .width(300)
        .height(300)
        .outline({
          width: { left: 3, right: 6, top: 10, bottom: 15 },
          // color使用LocalizedEdgeColors类型，start和end分别对应不同显示方向下的起始边和结束边颜色
          color: { start: '#e3bbbb', end: Color.Blue, top: Color.Red, bottom: Color.Green },
          radius: { topLeft: 10, topRight: 20, bottomLeft: 40, bottomRight: 80 },
          style: {
            left: OutlineStyle.DOTTED,
            right: OutlineStyle.DOTTED,
            top: OutlineStyle.SOLID,
            bottom: OutlineStyle.DASHED
          }
        }).textAlign(TextAlign.Center)
    }
  }
}
```

### 示例1（系统组件设置自定义属性）

在[Column](ts-container-column.md)组件上设置自定义属性，并在其对应的FrameNode上获取所设置的自定义属性。

```TypeScript
// xxx.ets
import { FrameNode, UIContext } from '@kit.ArkUI';

@Entry
@Component
struct CustomPropertyExample {
  build() {
    Column() {
      Text('text')
      Button('print').onClick(() => {
        // 获取Column对应的frameNode节点并查询设置的自定义属性
        const uiContext: UIContext = this.getUIContext();
        if (uiContext) {
          const node: FrameNode | null = uiContext.getFrameNodeById('Test_Column');
          if (node) {
            for (let i = 1; i < 4; i++) {
              const key = 'customProperty' + i;
              const property = node.getCustomProperty(key);
              console.info(key, JSON.stringify(property));
            }
          }
        }
      })
    }
    .id('Test_Column')
    // 设置Column组件的自定义属性
    .customProperty('customProperty1', {
      'number': 10,
      'string': 'this is a string',
      'bool': true,
      'object': {
        'name': 'name',
        'value': 100
      }
    })
    .customProperty('customProperty2', {})
    .customProperty('customProperty3', undefined)
    .width('100%')
    .height('100%')
  }
}
```

### 示例2（自定义组件设置自定义属性）

从API版本26.0.0开始，自定义组件支持通过[customProperty](#customproperty)接口设置自定义属性。本示例以[自定义组件的自定义布局](../../../ui/state-management/arkts-page-custom-components-layout.md)场景为例，在自定义组件上设置自定义属性，并在其[onMeasureSize](ts-custom-component-layout.md#onmeasuresize10)回调中获取所设置的自定义属性。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      CustomLayout({ builder: columnChildren })
        .customProperty('width', 100) // 为自定义组件设置自定义属性
        .customProperty('height', 400)
    }
  }
}

// 通过builder的方式传递多个组件，作为自定义组件的一级子组件（即不包含容器组件，如Column）
@Builder
function columnChildren() {
  ForEach([1, 2, 3], (index: number) => {
    Text('S' + index)
      .fontSize(30)
      .width(100)
      .height(100)
      .borderWidth(2)
      .offset({ x: 10, y: 20 })
  })
}

@Component
struct CustomLayout {
  @Builder
  doNothingBuilder() {
    // 空函数，仅演示使用方法。
  };

  @BuilderParam builder: () => void = this.doNothingBuilder;
  result: SizeResult = {
    width: 0,
    height: 0
  };

  // 计算各子组件的大小
  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let size = 100;
    children.forEach((child) => {
      let result: MeasureResult = child.measure({ minHeight: size, minWidth: size, maxWidth: size, maxHeight: size })
      size += result.width / 2;
    })
    let frameNode = this.getUIContext().getFrameNodeByUniqueId(this.getUniqueId());
    // 通过getCustomProperty获取设置的自定义属性
    // this.result在该用例中代表自定义组件本身的大小，onMeasureSize方法返回的是组件自身的尺寸
    this.result.width = (frameNode?.getCustomProperty('width') as number) ?? 50;
    this.result.height = (frameNode?.getCustomProperty('height') as number) ?? 50;
    return this.result;
  }
  // 放置各子组件的位置
  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    let startPos = 300;
    children.forEach((child) => {
      let pos = startPos - child.measureResult.height;
      child.layout({ x: pos, y: pos })
    })
  }

  build() {
    this.builder()
  }
}
```

### 示例1（组件绑定Modifier切换背景颜色）

该示例通过Button绑定Modifier实现了点击切换背景颜色的效果。



```TypeScript
// xxx.ets
// 设置Button组件属性的自定义AttributeModifier
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
  public isDark: boolean = false;

  applyNormalAttribute(instance: ButtonAttribute): void {
    if (this.isDark) {
      instance.backgroundColor(Color.Black);
    } else {
      instance.backgroundColor(Color.Red);
    }
  }
}

@Entry
@Component
struct AttributeDemo {
  @State modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Button('Button')
          .attributeModifier(this.modifier)
          .onClick(() => {
            this.modifier.isDark = !this.modifier.isDark;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例2（组件绑定Modifier实现按压态效果）

该示例通过Button绑定Modifier实现了按压态的效果。如果配合状态管理V2使用，详情见：[Modifier与makeObserved](../../../ui/state-management/arkts-v1-v2-migration-inner-object.md#modifier)。



```TypeScript
// xxx.ets
// 设置Button组件属性的自定义AttributeModifier
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
  applyNormalAttribute(instance: ButtonAttribute): void {
    instance.backgroundColor(Color.Black);
  }

  applyPressedAttribute(instance: ButtonAttribute): void {
    instance.backgroundColor(Color.Red);
  }
}

@Entry
@Component
struct AttributePressedDemo {
  @State modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Button('Button')
          .attributeModifier(this.modifier)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例3（自定义Modifier不支持感知@State装饰的状态数据变化）

该示例通过状态数据设置自定义Modifier的宽度，自定义Modifier不支持感知@State装饰的状态数据变化，点击按钮后宽度不发生改变。



```TypeScript
import { CommonModifier } from '@kit.ArkUI';

const TEST_TAG: string = 'AttributeModifier';

// 设置通用组件属性的自定义AttributeModifier
class MyModifier extends CommonModifier {
  applyNormalAttribute(instance: CommonAttribute): void {
    super.applyNormalAttribute?.(instance);
  }
}

@Component
struct MyImage1 {
  @Link modifier: CommonModifier;

  build() {
    Image($r('app.media.startIcon')).attributeModifier(this.modifier as MyModifier)
  }
}

@Entry
@Component
struct Index {
  index: number = 0;
  @State width1: number = 100;
  @State height1: number = 100;
  @State myModifier: CommonModifier = new MyModifier().width(this.width1).height(this.height1).margin(10);

  build() {
    Column() {
      Button($r('app.string.EntryAbility_label'))
        .margin(10)
        .onClick(() => {
          console.info(TEST_TAG, 'onClick');
          this.index++;
          if (this.index % 2 === 1) {
            this.width1 = 10;
            console.info(TEST_TAG, 'setGroup1');
          } else {
            this.height1 = 10;
            console.info(TEST_TAG, 'setGroup2');
          }
        })
      MyImage1({ modifier: this.myModifier })
    }
    .width('100%')
  }
}
```

### 示例4（Modifier和自定义Modifier的属性同时生效）

该示例通过自定义Modifier设置了width、height和margin，点击按钮时设置[borderStyle](ts-appendix-enums.md#borderstyle)和[borderWidth](ts-universal-attributes-border.md#borderwidth)，点击后5个属性同时生效。



```TypeScript
import { CommonModifier } from '@kit.ArkUI';

const TEST_TAG: string = 'AttributeModifier';

// 设置通用组件属性的自定义AttributeModifier
class MyModifier extends CommonModifier {
  applyNormalAttribute(instance: CommonAttribute): void {
    super.applyNormalAttribute?.(instance);
  }

  public setGroup1(): void {
    this.borderStyle(BorderStyle.Dotted);
    this.borderWidth(8);
  }

  public setGroup2(): void {
    this.borderStyle(BorderStyle.Dashed);
    this.borderWidth(8);
  }
}

@Component
struct MyImage1 {
  @Link modifier: CommonModifier;

  build() {
    Image($r('app.media.startIcon')).attributeModifier(this.modifier as MyModifier)
  }
}

@Entry
@Component
struct Index {
  @State myModifier: CommonModifier = new MyModifier().width(100).height(100).margin(10);
  index: number = 0;

  build() {
    Column() {
      Button($r('app.string.EntryAbility_label'))
        .margin(10)
        .onClick(() => {
          console.info(TEST_TAG, 'onClick');
          this.index++;
          if (this.index % 2 === 1) {
            (this.myModifier as MyModifier).setGroup1();
            console.info(TEST_TAG, 'setGroup1');
          } else {
            (this.myModifier as MyModifier).setGroup2();
            console.info(TEST_TAG, 'setGroup2');
          }
        })
      MyImage1({ modifier: this.myModifier })
    }
    .width('100%')
  }
}
```

### 示例5（组件绑定Modifier获焦样式）

该示例通过Button绑定Modifier实现了组件在获得焦点时的样式效果。点击Button2后，Button会显示获得焦点后的样式。



```TypeScript
// 设置Button组件属性的自定义AttributeModifier
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {

  applyNormalAttribute(instance: ButtonAttribute): void {
    instance.backgroundColor(Color.Blue);
  }
  applyFocusedAttribute(instance: ButtonAttribute): void {
    instance.backgroundColor(Color.Green);
  }
}

@Entry
@Component
struct AttributeDemo {
  @State modifier: MyButtonModifier = new MyButtonModifier();
  @State isDisable: boolean = true;

  build() {
    Row() {
      Column() {
        Button('Button')
          .attributeModifier(this.modifier)
          .enabled(this.isDisable)
          .id('app')
        Divider().vertical(false).strokeWidth(15).color(Color.Transparent)
        Button('Button2')
          .onClick(() => {
            this.getUIContext().getFocusController().activate(true);
            this.getUIContext().getFocusController().requestFocus('app');
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例6（组件绑定Modifier禁用状态的样式）

该示例通过Button绑定Modifier实现了组件禁用时的样式效果。点击Button2后，Button会显示禁用状态的样式。



```TypeScript
// 设置Button组件属性的自定义AttributeModifier
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
  applyDisabledAttribute(instance: ButtonAttribute): void {
    instance.width(200);
  }
}

@Entry
@Component
struct AttributeDemo {
  @State modifier: MyButtonModifier = new MyButtonModifier();
  @State isDisable: boolean = true;

  build() {
    Row() {
      Column() {
        Button('Button')
          .attributeModifier(this.modifier)
          .enabled(this.isDisable)
        Divider().vertical(false).strokeWidth(15).color(Color.Transparent)
        Button('Button2')
          .onClick(() => {
            this.isDisable = !this.isDisable;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例7（组件绑定Modifier选中状态样式）

该示例通过Radio绑定Modifier实现了组件选中时的样式效果。



```TypeScript
// 设置Radio组件属性的自定义AttributeModifier
class MyRadioModifier implements AttributeModifier<RadioAttribute> {
  applyNormalAttribute(instance: RadioAttribute): void {
    instance.backgroundColor(Color.Blue);
  }

  applySelectedAttribute(instance: RadioAttribute): void {
    instance.backgroundColor(Color.Red);
    instance.borderWidth(2);
  }
}

@Entry
@Component
struct AttributeDemo {
  @State modifier: MyRadioModifier = new MyRadioModifier();
  @State value: boolean = false;

  build() {
    Row() {
      Column() {
        Radio({ value: 'Radio1', group: 'radioGroup1' })
          .checked(this.value)
          .height(50)
          .width(50)
          .borderWidth(0)
          .borderRadius(30)
          .onClick(() => {
            this.value = !this.value;
          })
          .attributeModifier(this.modifier)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例8（自定义组件绑定Modifier实现按压态效果）

该示例通过Common（自定义）绑定Modifier实现了按压态的效果。



```TypeScript
// xxx.ets
// 设置自定义组件属性的自定义AttributeModifier
class CustomModifier implements AttributeModifier<CommonAttribute> {
  applyNormalAttribute(instance: CommonAttribute): void {
    instance.backgroundColor(Color.Blue);
  }

  applyPressedAttribute(instance: CommonAttribute): void {
    instance.backgroundColor(Color.Gray);
  }
}

@Entry
@Component
struct AttributePressedDemo {
  @State modifier: CustomModifier = new CustomModifier();

  build() {
    Row() {
      Column() {
        ChildComponent()
          .attributeModifier(this.modifier)
      }
      .width('100%')
    }
    .height('100%')
  }
}

// 自定义组件
@Component
struct ChildComponent {
  build() {
    Text('common')
      .fontColor(Color.White)
      .fontSize(28)
      .textAlign(TextAlign.Center)
      .width('35%')
      .height('10%')
  }
}
```

### 示例9（组件绑定Modifier实现鼠标悬浮态效果）

该示例通过Button绑定Modifier实现了鼠标悬浮态的效果。当鼠标移动到Button上时，Button的背景颜色变为红色，此时为悬浮态效果；当鼠标离开Button时，Button的背景颜色变为黑色，此时为普通态效果；同时通过[applyHoveredAttribute](arkts-arkui-common-comp-attributemodifier-i.md#applyhoveredattribute)接口设置悬浮态样式。

从API版本26.0.0开始，新增[applyHoveredAttribute](arkts-arkui-common-comp-attributemodifier-i.md#applyhoveredattribute)接口。

```TypeScript
// xxx.ets
// 设置Button组件属性的自定义AttributeModifier
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
  applyNormalAttribute(instance: ButtonAttribute): void {
    instance.backgroundColor(Color.Black);
  }

  // 设置悬浮态样式
  applyHoveredAttribute(instance: ButtonAttribute): void {
    instance.backgroundColor(Color.Red);
  }
}

@Entry
@Component
struct AttributeHoveredDemo {
  @State modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Button('Button')
          .attributeModifier(this.modifier)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例1（使用onHover）

该示例通过按钮设置了悬浮事件[onHover](#onhover)，鼠标悬浮可触发该事件修改按钮颜色。

示意图：

未悬浮时的文本内容与背景颜色：



手写笔悬浮时改变文本内容与背景颜色：



```TypeScript
// xxx.ets
@Entry
@Component
struct HoverEventExample {
  @State hoverText: string = 'no hover';
  @State color: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Button(this.hoverText, { type: ButtonType.Capsule })
        .width(180).height(80)
        .backgroundColor(this.color)
        .onHover((isHover: boolean, event: HoverEvent) => {
          // 通过onHover事件动态修改按钮在是否有鼠标或手写笔悬浮时的文本内容与背景颜色
          // 通过event.sourceTool区分设备是鼠标还是手写笔
          if (isHover) {
            if (event.sourceTool == SourceTool.Pen) {
              this.hoverText = 'pen hover';
              this.color = Color.Pink;
            } else if (event.sourceTool == SourceTool.MOUSE) {
              this.hoverText = 'mouse hover';
              this.color = Color.Red;
            }
          } else {
            this.hoverText = 'no hover';
            this.color = Color.Blue;
          }
        })
    }.padding({ top: 30 }).width('100%')
  }
}
```

### 示例2（使用onHoverMove）

从API version 15开始，该示例设置了按钮的[onHoverMove](arkts-arkui-common-comp-commonmethod-c.md#onhovermove)事件。当手写笔悬浮在按钮上时，UI会显示手写笔当前悬浮的位置。

```TypeScript
// xxx.ets
@Entry
@Component
struct OnHoverMoveEventExample {
  @State hoverMoveText: string = '';

  build() {
    Column({ space: 20 }) {
      Button('onHoverMove', { type: ButtonType.Capsule })
        .width(180).height(80)
        .onHoverMove((event: HoverEvent) => {
          this.hoverMoveText = 'onHoverMove:\nXY = (' + event.x + ', ' + event.y + ')' +
                               '\nwindowXY = (' + event.windowX + ', ' + event.windowY + ')' +
                               '\ndisplayXY = (' + event.displayX + ', ' + event.displayY + ')';
        })

      Text(this.hoverMoveText)
    }.padding({ top: 30 }).width('100%')
  }
}
```

### 示例1（设置组件提亮）

该示例主要通过advancedBlendMode给组件添加提亮效果。

效果图如下：



```TypeScript
// xxx.ets
import { uiEffect } from '@kit.ArkGraphics2D';

// uiEffect.createBrightnessBlender创建BrightnessBlender实例用于给组件添加提亮效果
let blender: uiEffect.BrightnessBlender = uiEffect.createBrightnessBlender({
  cubicRate: 0.5,
  quadraticRate: 0.5,
  linearRate: 0.5,
  degree: 0.5,
  saturation: 0.5,
  positiveCoefficient: [2.3, 4.5, 2.0],
  negativeCoefficient: [0.5, 2.0, 0.5],
  fraction: 0.5
});
// 注意：使用自定义object作为Blender入参不会生效，请使用uiEffect.createBrightnessBlender方法创建Blender实例。
let customBlender: uiEffect.BrightnessBlender = {
  cubicRate: 0.5,
  quadraticRate: 0.5,
  linearRate: 0.5,
  degree: 0.5,
  saturation: 0.5,
  positiveCoefficient: [2.3, 4.5, 2.0],
  negativeCoefficient: [0.5, 2.0, 0.5],
  fraction: 0.5
};

@Entry
@Component
struct Index {
  build() {
    Stack() {
      Image($r('app.media.img_1'))

      Column() {
        Text(String.fromCodePoint(0x1F600) + 'TEST')
          .fontSize(60)

        Text(String.fromCodePoint(0x1F600) + 'FAST')
          .fontSize(60)
          .advancedBlendMode(blender)

        Text(String.fromCodePoint(0x1F600) + 'OFFSCREEN')
          .fontSize(60)
          .advancedBlendMode(blender, BlendApplyType.OFFSCREEN)

        Text(String.fromCodePoint(0x1F600) + 'TEST')
          .fontSize(60)
          .advancedBlendMode(customBlender)
      }
    }
  }
}
```

### 示例2（设置节点组剔除属性）

该示例演示在组件的属性动画场景下，如何通过使用节点组剔除属性[excludeFromRenderGroup](arkts-arkui-common-comp-commonmethod-c-sys.md#excludefromrendergroup)，避免节点组缓存反复失效。

从API version 22开始，新增[excludeFromRenderGroup](arkts-arkui-common-comp-commonmethod-c-sys.md#excludefromrendergroup)属性。



```TypeScript
// xxx.ets
@Entry
@Component
struct ExcludeFromRenderGroupDemo {
  readonly color1: ResourceColor = '#2787d9';
  readonly color2: ResourceColor = '#ffc000';
  @State myColor: ResourceColor = this.color1;
  @State isExcluded: boolean = false;
  animationCnt: number = 0;

  build() {
    Column() {
      Column({ space: 10 }) {
        Column()
          .width(100)
          .height(100)
          .backgroundColor(this.myColor)
          // 设置excludeFromRenderGroup属性。该组件做背景色动画时，实际显示效果需频繁更新属性，且该组件区域只占节点组区域的一部分，因此设置excludeFromRenderGroup属性以复用节点组缓存
          .excludeFromRenderGroup(this.isExcluded)
          .onClick(() => {
            this.isExcluded = true; // 在播放动画前，修改节点组剔除属性为true
            this.animationCnt++;
            this.getUIContext().animateTo({
              duration: 600,
              onFinish: () => {
                this.animationCnt--;
                if (this.animationCnt === 0) { // animationCnt变为0表示所有动画都结束
                  this.isExcluded = false; // 在组件动画结束后，组件上不再发生属性变化时，可以重置节点组剔除属性
                }
              }
            }, () => {
              this.myColor = (this.myColor === this.color1) ? this.color2 : this.color1;
            })
          })
        // 节点组内的其他组件
        Image($r('app.media.bg1')) // $r('app.media.bg1')需要替换为开发者所需的图像资源文件
          .width(100)
          .height(100)
        Image($r('app.media.bg1')) // $r('app.media.bg1')需要替换为开发者所需的图像资源文件
          .width(100)
          .height(100)
      }.renderGroup(true)
      .width('100%')
      .height('70%')
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例3（设置组件提亮并渐隐）

从API version 23开始，该示例主要演示如何通过advancedBlendMode给组件同时添加提亮和渐隐效果。



```TypeScript
// xxx.ets
import { uiEffect } from '@kit.ArkGraphics2D';

// uiEffect.createBrightnessBlender创建BrightnessBlender实例用于给组件添加提亮效果
let blender: uiEffect.BrightnessBlender = uiEffect.createBrightnessBlender({
  cubicRate: 0.5,
  quadraticRate: 0.5,
  linearRate: 0.5,
  degree: 0.5,
  saturation: 0.5,
  positiveCoefficient: [2.3, 4.5, 2.0],
  negativeCoefficient: [0.5, 2.0, 0.5],
  fraction: 0.3
});

@Entry
@Component
struct Index {
  build() {
    Column() {
      Stack() {
        Column() {
          Text(String.fromCodePoint(0x1F600) + ' BlendApplyType OFFSCREEN WITH BACKGROUND ' +
          String.fromCodePoint(0x1F600))
            .fontSize(35)
            .fontColor(Color.Black)
        }
        .advancedBlendMode(blender, BlendApplyType.FAST)

        Column()
          .width('100%')
          .height('100%')
          .linearGradient({
            direction: GradientDirection.Right,
            colors: [
              [Color.Transparent, 0.0],
              [Color.Black, 0.50],
              [Color.Black, 0.55],
              [Color.Transparent, 1.0]
            ]
          })
          .blendMode(BlendMode.DST_IN, BlendApplyType.FAST)
      }
      .advancedBlendMode(BlendMode.SRC_OVER, BlendApplyType.OFFSCREEN_WITH_BACKGROUND)
      .width('100%')
      .height('20%')
    }
    .backgroundColor('rgb(254, 238, 239)')
    .width('100%')
    .height('100%')
  }
}
```

该示例展示了组件获焦和失焦的情况，按钮获焦和失焦时会改变按钮的颜色。

```TypeScript
// xxx.ets
@Entry
@Component
struct FocusEventExample {
  @State oneButtonColor: string = '#0066FF'
  @State twoButtonColor: string = '#87CEFA'
  @State threeButtonColor: string = '#90EE90'

  build() {
    Column({ space: 20 }) {
      // 当焦点在三个按钮间移动，按钮获焦时颜色变化，失焦时变回原背景色
      Button('First Button')
        .backgroundColor(this.oneButtonColor)
        .width(260)
        .height(70)
        .fontColor(Color.Black)
        .onFocus(() => {
          this.oneButtonColor = '#FFFFFF';
        })
        .onBlur(() => {
          this.oneButtonColor = '#0066FF';
        })
      Button('Second Button')
        .backgroundColor(this.twoButtonColor)
        .width(260)
        .height(70)
        .fontColor(Color.Black)
        .onFocus(() => {
          this.twoButtonColor = '#FFFFFF';
        })
        .onBlur(() => {
          this.twoButtonColor = '#87CEFA';
        })
      Button('Third Button')
        .backgroundColor(this.threeButtonColor)
        .width(260)
        .height(70)
        .fontColor(Color.Black)
        .onFocus(() => {
          this.threeButtonColor = '#FFFFFF';
        })
        .onBlur(() => {
          this.threeButtonColor = '#90EE90';
        })
    }.width('100%').margin({ top: 20 })
  }
}
```

### 示例1（悬浮气泡的显示和消失）

此示例为bindTips通过绑定Button产生悬浮气泡。



```TypeScript
// xxx.ets
@Entry
@Component
struct TipsExample {
  build() {
    Flex({ direction: FlexDirection.Column }) {
      Button('Hover Tips')
        .bindTips("Tips", {
          appearingTime: 700,
          disappearingTime: 300,
          appearingTimeWithContinuousOperation: 300,
          disappearingTimeWithContinuousOperation: 0,
          enableArrow: true,
        })
        .position({ x: 100, y: 250 })
    }.width('100%').padding({ top: 5 })
  }
}
```

### 示例2（多个悬浮气泡的显示和消失）

此示例展示了如何使用bindTips配置多个悬浮气泡依次显示和消失。



```TypeScript
// xxx.ets

@Entry
@Component
struct TipsExample {
  build() {
    Flex({ direction: FlexDirection.Column }) {
      Button('Hover Tips')
        .bindTips("Tips", {
          appearingTime: 700,
          disappearingTime: 300,
          appearingTimeWithContinuousOperation: 300,
          disappearingTimeWithContinuousOperation: 0,
          enableArrow: true,
        })
        .position({ x: 100, y: 250 })

      Button('Hover Tips')
        .bindTips("Tips", {
          appearingTime: 700,
          disappearingTime: 300,
          appearingTimeWithContinuousOperation: 300,
          disappearingTimeWithContinuousOperation: 0,
          enableArrow: true,
        })
        .position({ x: 100, y: 350 })


    }.width('100%').padding({ top: 5 })
  }
}
```

### 示例3（设置悬浮气泡的沉浸光感视效）

该示例通过[TipsOptions](#tipsoptions类型说明)中的systemMaterial属性设置组件的系统材质，实现了bindTips的沉浸光感视效。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在TipsOptions中新增了systemMaterial属性。

```TypeScript
// xxx.ets
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct TipsExample {
  build() {
    Flex({ direction: FlexDirection.Column }) {
      Button('Hover Tips')
        .bindTips("悬浮气泡测试", {
          // 控制是否设置系统材质接口
          systemMaterial: new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.THIN
          })
        })
        .position({ x: 100, y: 300 })
    }.width('100%').padding({ top: 5 })
    // 请开发者替换为实际资源文件
    .backgroundImage($r("app.media.img"))
    .backgroundImageSize({width: '100%', height: '100%'})
  }
}
```

### 示例1（动态绑定手势）

该示例通过gestureModifier动态设置组件绑定的手势。



```TypeScript
// xxx.ets
class MyButtonModifier implements GestureModifier {
  supportDoubleTap: boolean = true;

  applyGesture(event: UIGestureEvent): void {
    // 根据supportDoubleTap状态绑定双击手势或拖动手势
    if (this.supportDoubleTap) {
      event.addGesture(
        new TapGestureHandler({
          count: 2,
          fingers: 1,
          // 从API version 23开始，新增distanceThreshold属性
          distanceThreshold: 100
        })
          .tag('doubleTapGesture')
          .onAction((event: GestureEvent) => {
            console.info('Gesture Info is', JSON.stringify(event));
            console.info('button tap');
          })
      );
    } else {
      event.addGesture(
        new PanGestureHandler()
          .onActionStart(() => {
            console.info('Pan start');
          })
      )
    }
  }
}

@Entry
@Component
struct Index {
  @State modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Column()
          .gestureModifier(this.modifier)
          .width(500)
          .height(500)
          .backgroundColor(Color.Gray)
        Button('changeGesture')
          .onClick(() => {
            this.modifier.supportDoubleTap = !this.modifier.supportDoubleTap;
          })
          .margin({ top: 10 })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例2（动态绑定手势组）

该示例通过gestureModifier动态设置组件绑定的手势组。

```TypeScript
class MyButtonModifier implements GestureModifier {
  isExclusive: boolean = true;

  applyGesture(event: UIGestureEvent): void {
    if (this.isExclusive) {
      // 绑定互斥手势组
      event.addGesture(new GestureGroupHandler({
        mode: GestureMode.Exclusive,
        gestures: [new TapGestureHandler({ count: 2, fingers: 1 }).onAction((event) => {
          console.info('event info is', JSON.stringify(event));
          console.info('ExclusiveGroupGesture TapGesture is called');
        }), new LongPressGestureHandler({ repeat: true, fingers: 1 }).onAction((event) => {
          console.info('event info is', JSON.stringify(event));
          console.info('ExclusiveGroupGesture LongPressGesture is called');
        }), new PanGestureHandler({ fingers: 1 }).onActionStart((event) => {
          console.info('event info is', JSON.stringify(event));
          console.info('ExclusiveGroupGesture PanGesture onActionStart is called');
        }).onActionEnd((event) => {
          console.info('event info is', JSON.stringify(event));
          console.info('ExclusiveGroupGesture PanGesture onActionEnd is called');
        })]
      }));
    } else {
      // 绑定并行手势组
      event.addGesture(new GestureGroupHandler({
        mode: GestureMode.Parallel,
        gestures: [new TapGestureHandler({ count: 2, fingers: 1 }).onAction((event) => {
          console.info('event info is', JSON.stringify(event));
          console.info('ParallelGroupGesture TapGesture is called');
        }), new LongPressGestureHandler({ repeat: true, fingers: 1 }).onAction((event) => {
          console.info('event info is', JSON.stringify(event));
          console.info('ParallelGroupGesture LongPressGesture is called');
        }), new PanGestureHandler({ fingers: 1 }).onActionStart((event) => {
          console.info('event info is', JSON.stringify(event));
          console.info('ParallelGroupGesture PanGesture onActionStart is called');
        }).onActionEnd((event) => {
          console.info('event info is', JSON.stringify(event));
          console.info('ParallelGroupGesture PanGesture onActionEnd is called');
        })]
      }));
    }
  }
}

@Entry
@Component
struct Index {
  @State modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Column()
          .gestureModifier(this.modifier)
          .width(500)
          .height(500)
          .backgroundColor(Color.Gray)

        Button('changeGestureGroupType')
          .onClick(() => {
            this.modifier.isExclusive = !this.modifier.isExclusive;
          })
          .margin({ top: 10 })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例1（自定义手势判定）

该示例通过配置[onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin)实现了对长按、快滑、滑动、捏合和拖动手势的自定义判定。从API version 21开始，支持通过[BaseEvent](ts-universal-events-click.md#baseevent8)的axisPinch属性获取双指缩放比例。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State message: string = '';

  build() {
    Column() {
      Row({ space: 20 }) {
        Text(this.message).width(200).height(80).backgroundColor(Color.Pink)
          .fontSize(25)
      }.margin(20)
    }
    .width('100%')
    .height(200)
    .borderWidth(2)
    .onDragStart(() => {
      this.message = 'drag';
      console.info('Drag start.');
    })
    .gesture(
      TapGesture()
        .tag('tap1') // 设置点击手势标志
        .onAction(() => {
          this.message = 'tap1';
        })
    )
    .gesture(
      LongPressGesture()
        .tag('longPress1') // 设置长按手势标志
        .onAction(() => {
          this.message = 'longPress';
        })
    )
    .gesture(
      SwipeGesture()
        .tag('swipe1') // 设置快滑手势标志
        .onAction(() => {
          this.message = 'swipe1';
        })
    )
    .gesture(
      PanGesture()
        .tag('pan1') // 设置滑动手势标志
        .onActionStart(() => {
          this.message = 'pan1';
        })
    )
    .gesture(
      PinchGesture()
        .tag('pinch1') // 设置捏合手势标志
        .onActionStart(() => {
          this.message = 'pinch1'
        })
    )
    .onGestureJudgeBegin((gestureInfo: GestureInfo, event: BaseGestureEvent) => {
      // 若该手势类型为长按手势，转换为长按手势事件
      if (gestureInfo.type == GestureControl.GestureType.LONG_PRESS_GESTURE) {
        let longPressEvent = event as LongPressGestureEvent;
        console.info(`repeat ${longPressEvent.repeat}`);
      }
      // 若该手势类型为快滑手势，转换为快滑手势事件
      if (gestureInfo.type == GestureControl.GestureType.SWIPE_GESTURE) {
        let swipeEvent = event as SwipeGestureEvent;
        console.info(`angle ${swipeEvent.angle}`);
      }
      // 若该手势类型为滑动手势，转换为滑动手势事件
      if (gestureInfo.type == GestureControl.GestureType.PAN_GESTURE) {
        let panEvent = event as PanGestureEvent;
        console.info(`velocity ${panEvent.velocity}`);
      }
      // 若该手势类型为捏合手势，转换为捏合手势事件
      if (gestureInfo.type == GestureControl.GestureType.PINCH_GESTURE) {
        let pinchEvent = event as PinchGestureEvent;
        console.info(`axisPinch ${pinchEvent.axisPinch}`);
      }
      // 自定义判定标准
      if (gestureInfo.type == GestureControl.GestureType.DRAG) {
        // 返回 GestureJudgeResult.REJECT 会使拖动手势失败。
        return GestureJudgeResult.REJECT;
      } else if (gestureInfo.tag === 'longPress1' && event.fingerList.length > 0 && event.fingerList[0].localY < 100) {
        // 返回 GestureJudgeResult.CONTINUE 将保持系统判定。
        return GestureJudgeResult.CONTINUE;
      }
      return GestureJudgeResult.CONTINUE;
    })
  }
}
```

### 示例2（自定义区域手势判定）

该示例通过配置onGestureJudgeBegin，根据触发位置所在区域决定长按手势和拖动手势是否响应。



```TypeScript
// xxx.ets
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  scroller: Scroller = new Scroller()
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Text('Drag 上下两层 上层绑定长按，下层绑定拖拽。先长按后平移上半区红色区域只会响应长按，先长按后平移下半区蓝色区域只会响应拖拽')
          .width('100%')
          .fontSize(20)
          .fontColor('0xffdd00')
          .backgroundColor(0xeeddaa00)
        Stack({ alignContent: Alignment.Center }) {
          Column() {
            // 模拟上半区和下半区
            Stack().width('200').height('100').backgroundColor(Color.Red)
            Stack().width('200').height('100').backgroundColor(Color.Blue)
          }.width('200vp').height('200vp')

          // Stack的下半区是绑定了拖动手势的图像区域
          Image($r('sys.media.ohos_app_icon'))
            .draggable(true)
            .onDragStart(() => {
              this.promptAction.showToast({ message: 'Drag 下半区蓝色区域，Image响应' });
            })
            .width('200').height('200')
          // Stack的上半区是绑定了长按手势的浮动区域
          Stack() {
          }
          .width('200')
          .height('200')
          .hitTestBehavior(HitTestMode.Transparent)
          .onGestureJudgeBegin((gestureInfo: GestureInfo, event: BaseGestureEvent) => {
            // 确定gestureInfo的tag标志是否有值
            if (gestureInfo.tag) {
              console.info(`gestureInfo tag ${gestureInfo.tag.toString()}`);
            }
            console.info(`gestureInfo Type ${gestureInfo.type.toString()}`);
            console.info(`isSystemGesture ${gestureInfo.isSystemGesture}`);
            console.info(`pressure ${event.pressure}\nfingerList.length ${event.fingerList.length}\ntimeStamp ${event.timestamp}\nsourceType ${event.source.toString()}\n` +
              `tiltX ${event.tiltX}\ntiltY ${event.tiltY}\nrollAngle ${event.rollAngle}\nsourceTool ${event.sourceTool.toString()}`);
            // 如果是长按类型手势，判断点击的位置是否在上半区
            if (gestureInfo.type == GestureControl.GestureType.LONG_PRESS_GESTURE) {
              if (event.fingerList.length > 0 && event.fingerList[0].localY < 100) {
                return GestureJudgeResult.CONTINUE
              } else {
                return GestureJudgeResult.REJECT
              }
            }
            return GestureJudgeResult.CONTINUE
          })
          .gesture(GestureGroup(GestureMode.Parallel,
            LongPressGesture()
              .onAction((event: GestureEvent) => {
                this.promptAction.showToast({ message: 'LongPressGesture 长按上半区 红色区域，红色区域响应' });
              })
              .tag('tap111')
          ))

        }.width('100%')
      }.width('100%')
    }
  }
}
```

### 示例3（实时监测参与手势的有效触点的数量及其简要信息）

该示例通过配置onGestureJudgeBegin回调，读取fingerInfos实时检测参与手势的有效触点数量、各个触点ID及其坐标。

```TypeScript
// xxx.ets
@Entry
@Component
struct GestureDetectorExample {
  @State message: string = '触摸区域'
  @State fingerCount: number = 0
  @State fingerDetails: string = ''

  build() {
    Column() {
      // 显示信息区域
      Column() {
        Text(this.message)
          .fontSize(20)
          .fontWeight(FontWeight.Bold)

        Text(`触点数量：${this.fingerCount}`)
          .fontSize(16)
          .margin({ top: 8 })


        Text(this.fingerDetails)
          .fontSize(14)
          .margin({ top: 8 })
      }
      .padding(10)
      .border({ width: 1, color: Color.Gray })

      // 手势检测区域
      Column()
        .width('90%')
        .height(200)
        .margin(20)
        .border({ width: 2, color: Color.Black })
        .gesture(
          GestureGroup(GestureMode.Exclusive,
            TapGesture()
              .onAction(() => {
                this.message = '单击事件';
              }),
            LongPressGesture()
              .onAction(() => {
                this.message = '长按事件';
              }),
            PanGesture()
              .onActionStart(() => {
                this.message = '拖动开始';
              })
              .onActionUpdate(() => {
                this.message = '拖动中...';
              })
              .onActionEnd(() => {
                this.message = '拖动结束';
                this.fingerCount = 0;
                this.fingerDetails = '';
              })
          )
        )
        .onGestureJudgeBegin((_gestureInfo: GestureInfo, event: BaseGestureEvent) => {
          // 获取 fingerInfos 信息
          if (event?.fingerInfos) {
            this.fingerCount = event.fingerInfos.length;
            this.fingerDetails = event.fingerInfos.map(finger =>
            `ID：${finger.id}: (${finger.localX.toFixed(1)}, ${finger.localY.toFixed(1)})`
            ).join('\n');
            console.info(`触点信息：${JSON.stringify(event.fingerInfos)}`);
          }
          // 当触点数量超过2个时，拒绝当前手势。
          if (this.fingerCount > 2) {
            return GestureJudgeResult.REJECT
          }
          return GestureJudgeResult.CONTINUE
        })
    }
    .width('100%')
    .height('100%')
    .padding(10)
  }
}
```

### 示例1 (使用onVisibleAreaChange来监听区域变化)

该示例对组件设置[onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange)事件，当组件完全显示或者完全消失时触发回调。

```TypeScript
// xxx.ets
@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  @State testTextStr: string = 'test';
  @State testRowStr: string = 'test';

  build() {
    Column() {
      Column() {
        Text(this.testTextStr)
          .fontSize(20)

        Text(this.testRowStr)
          .fontSize(20)
      }
      .height(100)
      .backgroundColor(Color.Gray)
      .opacity(0.3)

      Scroll(this.scroller) {
        Column() {
          Text('Test Text Visible Change')
            .fontSize(20)
            .height(200)
            .margin({ top: 50, bottom: 20 })
            .backgroundColor(Color.Green)
            // 通过设置ratios为[0.0, 1.0]，实现当组件完全显示或完全消失在屏幕中时触发回调。
            .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
              console.info(`Test Text isExpanding: ${isExpanding}, currentRatio: ${currentRatio}`);
              if (isExpanding && currentRatio >= 1.0) {
                console.info(`Test Text is fully visible. currentRatio: ${currentRatio}`);
                this.testTextStr = 'Test Text is fully visible';
              }

              if (!isExpanding && currentRatio <= 0.0) {
                console.info('Test Text is completely invisible.');
                this.testTextStr = 'Test Text is completely invisible';
              }
            })

          Row() {
            Text('Test Row Visible Change')
              .fontSize(20)
              .margin({ bottom: 20 })

          }
          .height(200)
          .backgroundColor(Color.Yellow)
          .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
            console.info(`Test Row isExpanding: ${isExpanding}, currentRatio: ${currentRatio}`);
            if (isExpanding && currentRatio >= 1.0) {
              console.info('Test Row is fully visible.');
              this.testRowStr = 'Test Row is fully visible';
            }

            if (!isExpanding && currentRatio <= 0.0) {
              console.info('Test Row is completely invisible.');
              this.testRowStr = 'Test Row is completely invisible';
            }
          })

          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: number) => (item.toString()))

        }.width('100%')
      }
      .backgroundColor(0x317aff)
      .scrollable(ScrollDirection.Vertical)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Gray)
      .scrollBarWidth(10)
      .onWillScroll((xOffset: number, yOffset: number) => {
        console.info(`${xOffset} ${yOffset}`);
      })
      .onScrollEdge(() => {
        console.info('To the edge');
      })
      .onScrollStop(() => {
        console.info('Scroll Stop');
      })

    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### 示例2 (使用onVisibleAreaApproximateChange来监听区域变化)

从API version 17开始，该示例对组件设置[onVisibleAreaApproximateChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareaapproximatechange)事件，当组件完全显示或者完全消失时触发回调。



```TypeScript
// xxx.ets
@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  @State testTextStr: string = 'test';
  @State testRowStr: string = 'test';

  build() {
    Column() {
      Column() {
        Text(this.testTextStr)
          .fontSize(20)

        Text(this.testRowStr)
          .fontSize(20)
      }
      .height(100)
      .backgroundColor(Color.Gray)
      .opacity(0.3)

      Scroll(this.scroller) {
        Column() {
          Text('Test Text Visible Change')
            .fontSize(20)
            .height(200)
            .margin({ top: 50, bottom: 20 })
            .backgroundColor(Color.Green)
            // 通过设置ratios为[0.0, 1.0]，实现当组件完全显示或完全消失在屏幕中时触发回调。
            .onVisibleAreaApproximateChange({ ratios: [0.0, 1.0], expectedUpdateInterval: 1000 },
              (isExpanding: boolean, currentRatio: number) => {
                console.info(`Test Text isExpanding: ${isExpanding}, currentRatio: ${currentRatio}`);
                if (isExpanding && currentRatio >= 1.0) {
                  console.info(`Test Text is fully visible. currentRatio: ${currentRatio}`);
                  this.testTextStr = 'Test Text is fully visible';
                }

                if (!isExpanding && currentRatio <= 0.0) {
                  console.info('Test Text is completely invisible.');
                  this.testTextStr = 'Test Text is completely invisible';
                }
              })

          Row() {
            Text('Test Row Visible Change')
              .fontSize(20)
              .margin({ bottom: 20 })

          }
          .height(200)
          .backgroundColor(Color.Yellow)
          .onVisibleAreaApproximateChange({ ratios: [0.0, 1.0], expectedUpdateInterval: 1000 }, (isExpanding: boolean, currentRatio: number) => {
            console.info(`Test Row isExpanding: ${isExpanding}, currentRatio: ${currentRatio}`);
            if (isExpanding && currentRatio >= 1.0) {
              console.info('Test Row is fully visible.');
              this.testRowStr = 'Test Row is fully visible';
            }

            if (!isExpanding && currentRatio <= 0.0) {
              console.info('Test Row is completely invisible.');
              this.testRowStr = 'Test Row is completely invisible';
            }
          })

          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: number) => (item.toString()))

        }.width('100%')
      }
      .backgroundColor(0x317aff)
      .scrollable(ScrollDirection.Vertical)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Gray)
      .scrollBarWidth(10)
      .onWillScroll((xOffset: number, yOffset: number) => {
        console.info(`${xOffset} ${yOffset}`);
      })
      .onScrollEdge(() => {
        console.info('To the edge');
      })
      .onScrollStop(() => {
        console.info('Scroll Stop');
      })

    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### 示例3 (设置measureFromViewport计算子组件超出父组件显示时的可见区域)

从API version 22开始，该示例展示onVisibleAreaChange事件设置measureFromViewport参数后的效果对比，主要差异体现在回调返回的组件可见比例（currentRatio）上。设置measureFromViewport为true时，返回的组件可见比例（currentRatio）更符合实际效果。由于不同设备的屏幕像素密度不同，可见区域变化事件的计算过程涉及小数取整，currentRatio可能存在微小差异。

```TypeScript
@Entry
@Component
struct OnVisibleAreaChangeSample {
  @State ratio1: number = 0.0;
  @State ratio2: number = 0.0;
  @State ratio3: number = 0.0;

  build() {
    Column() {
      Text(`onVisibleChange1 with measureFromViewport \nratio: ${this.ratio1}`)
      Column() {
        Row() {
          Row() {

          }
          .backgroundColor(Color.Blue)
          .height(120)
          .width(120)
          .offset({ x: 0, y: 60 })
          // measureFromViewport设置为true，父组件未设置clip(true)，超出父组件的区域被视为可见区域。
          .onVisibleAreaApproximateChange({
            ratios: [0.0, 1.0],
            expectedUpdateInterval: 500,
            measureFromViewport: true
          }, (isExpanding: boolean, currentRatio: number) => {
            console.info(`onVisibleAreaApproximateChange1 isExpanding: ${isExpanding} currentRatio: ${currentRatio}`);
          })
          .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
            this.ratio1 = currentRatio;
          }, true)
        }
        .backgroundColor(Color.Pink)
        .height(120)
        .width(120)
      }
      .padding(5)
      .borderWidth(1)
      .height(200)
      .width(200)

      Text(`onVisibleChange2 without measureFromViewport \nratio: ${this.ratio2}`)
      Column() {
        Row() {
          Row() {

          }
          .backgroundColor(Color.Blue)
          .height(120)
          .width(120)
          .offset({ x: 0, y: 60 })
          // 不设置measureFromViewport，measureFromViewport默认为false，父组件未设置clip(true)，超出父组件的区域被视为不可见区域。
          .onVisibleAreaApproximateChange({ ratios: [0.0, 1.0], expectedUpdateInterval: 500 },
            (isExpanding: boolean, currentRatio: number) => {
              console.info(`onVisibleAreaApproximateChange2 isExpanding: ${isExpanding} currentRatio: ${currentRatio}`);
            })
          .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
            this.ratio2 = currentRatio;
          })
        }
        .backgroundColor(Color.Pink)
        .height(120)
        .width(120)
      }
      .padding(5)
      .borderWidth(1)
      .height(200)
      .width(200)

      Text(`parent set clip(true) onVisibleChange3 with measureFromViewport \nratio: ${this.ratio3}`)
      Column() {
        Row() {
          Row() {

          }
          .backgroundColor(Color.Blue)
          .height(120)
          .width(120)
          .offset({ x: 0, y: 60 })
          // measureFromViewport设置为true，父组件设置clip(true)，超出父组件的区域被视为不可见区域。
          .onVisibleAreaApproximateChange({
            ratios: [0.0, 1.0],
            expectedUpdateInterval: 500,
            measureFromViewport: true
          }, (isExpanding: boolean, currentRatio: number) => {
            console.info(`onVisibleAreaApproximateChange3 isExpanding: ${isExpanding} currentRatio: ${currentRatio}`);
          })
          .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
            this.ratio3 = currentRatio;
          }, true)
        }
        .clip(true)
        .backgroundColor(Color.Pink)
        .height(120)
        .width(120)
      }
      .padding(5)
      .borderWidth(1)
      .height(200)
      .width(200)
    }
    .height('100%')
    .width('100%')
  }
}
```

该示例通过hoverEffect设置组件的鼠标悬浮态显示效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct HoverExample {
  @State isHoverVal: boolean = false

  build() {
    Column({ space: 5 }) {
      Column({ space: 5 }) {
        Text('Scale').fontSize(20).fontColor(Color.Gray).width('90%').position({ x: 0, y: 80 })
        Column()
          .width('80%')
          .height(200)
          .backgroundColor(Color.Gray)
          .position({ x: 40, y: 120 })
          .hoverEffect(HoverEffect.Scale)
          .onHover((isHover: boolean) => {
            console.info(`Scale isHover: ${isHover}`);
            this.isHoverVal = isHover;
          })

        Text('Board').fontSize(20).fontColor(Color.Gray).width('90%').position({ x: 0, y: 380 });
        Column()
          .width('80%')
          .height(200)
          .backgroundColor(Color.Yellow)
          .hoverEffect(HoverEffect.Highlight)
          .position({ x: 40, y: 420 })
          .onHover((isHover: boolean) => {
            console.info(`Highlight isHover: ${isHover}`);
            this.isHoverVal = isHover;
          })
      }
      .hoverEffect(HoverEffect.None)
      .width('100%')
      .height('100%')
      .border({ width: 1 })
      .onHover((isHover: boolean) => {
        console.info('HoverEffect.None');
        this.isHoverVal = isHover;
      })
    }
  }
}
```

该示例演示通过foregroundEffect接口设置前景属性。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Row() {
      // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.icon'))
          .width(100)
          .height(100)
          // 设置前景模糊效果，模糊半径为20
          .foregroundEffect({ radius: 20 })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

### 示例1（使用自动内存优化策略）

以下示例中，可复用自定义组件ReusableComponent通过[ReusableOptions](arkts-arkui-common-comp-reusableoptions-i.md)的memoryOptimizationStrategy属性使用了自动内存优化策略。点击Recycle按钮，可触发ReusableComponent组件回收。之后应用退后台，可触发复用池缓存释放。

从API版本26.0.0开始，新增ReusableOptions接口。

```TypeScript
@Reusable({ memoryOptimizationStrategy: ReusableMemOptStrategy.ENABLE_AUTO_CACHE_OPTIMIZATION }) // 使用自动内存优化策略
@Component
struct ReusableComponent {
  aboutToRecycle() {
    console.info('ReusableComponent aboutToRecycle');
  }
  aboutToDisappear() {
    console.info('ReusableComponent aboutToDisappear');
  }
  build() {
    Text('ReusableComponent')
  }
}

@Entry
@Component
struct MemoryOptimizeDemo {
  @State showReusableComponent: boolean = true;
  build() {
    Column() {
      Button('Recycle').onClick(() => { // 点击按钮触发组件回收
        this.showReusableComponent = false;
      })
      if (this.showReusableComponent) {
        ReusableComponent()
      }
    }
  }
}
```

该示例主要演示如何通过keyframeAnimateTo来设置关键帧动画，包括delay延迟、onFinish播放完成回调以及各关键帧的curve曲线配置。

```TypeScript
// xxx.ets
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct KeyframeDemo {
  @State myScale: number = 1.0;
  uiContext: UIContext | undefined = undefined;

  aboutToAppear() {
    this.uiContext = this.getUIContext?.();
  }

  build() {
    Column() {
      Circle()
        .width(100)
        .height(100)
        .fill('#46B1E3')
        .margin(100)
        .scale({ x: this.myScale, y: this.myScale })
        .onClick(() => {
          if (!this.uiContext) {
            console.info('no uiContext, keyframe failed');
            return;
          }
          this.myScale = 1;
          // 设置关键帧动画整体播放3次，延迟200ms，并在结束时触发onFinish回调
          this.uiContext.keyframeAnimateTo({
              iterations: 3,
              delay: 200,
              onFinish: () => {
                console.info('keyframe animate finish');
              },
              // 从API version 19开始新增expectedFrameRateRange
              expectedFrameRateRange: {
                min: 10,
                max: 120,
                expected: 60,
              }
            }, [
            {
              // 第一段关键帧动画时长为800ms，使用EaseIn曲线，scale属性做从1到1.5的动画
              duration: 800,
              curve: Curve.EaseIn,
              event: () => {
                this.myScale = 1.5;
              }
            },
            {
              // 第二段关键帧动画时长为500ms，使用EaseOut曲线，scale属性做从1.5到1的动画
              duration: 500,
              curve: Curve.EaseOut,
              event: () => {
                this.myScale = 1;
              }
            }
          ]);
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State lightIntensity: number = 0;
  @State bloomValue: number = 0;

  build() {
    Row({ space: 20 }) {
      Flex()
        .pointLight({ illuminated: IlluminatedType.BORDER })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)

      Flex()
        .pointLight({
          lightSource: {
            intensity: this.lightIntensity,
            positionX: '50%',
            positionY: '50%',
            positionZ: 80
          },
          bloom: this.bloomValue
        })
        .animation({ duration: 333 })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)
        .onTouch((event: TouchEvent) => {
          // 按下时增强光源强度和发光强度，松开或取消时恢复默认效果。
          if (event.type === TouchType.Down) {
            this.lightIntensity = 1;
            this.bloomValue = 1;
          } else if (event.type === TouchType.Up || event.type === TouchType.Cancel) {
            this.lightIntensity = 0;
            this.bloomValue = 0;
          }
        })

      Flex()
        .pointLight({ illuminated: IlluminatedType.BORDER_CONTENT })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)
    }
    .justifyContent(FlexAlign.Center)
    .backgroundColor(Color.Black)
    .size({ width: '100%', height: '100%' })
  }
}
```

### 示例1（使用不同裁剪属性）

该示例通过[clipShape](arkts-arkui-common-comp-commonmethod-c.md#clipshape)、[clip](#clip12)、[maskShape](arkts-arkui-common-comp-commonmethod-c.md#maskshape)实现图片的裁剪和遮罩。



```TypeScript
// xxx.ets
import { CircleShape, RectShape } from '@kit.ArkUI';

@Entry
@Component
struct ClipAndMaskExample {
  build() {
    Column({ space: 15 }) {
      Text('clip').fontSize(12).width('75%').fontColor('#DCDCDC')
      Row() {
        // $r("app.media.testImg")需要替换为开发者所需的图像资源文件。
        Image($r('app.media.testImg')).width('500px').height('280px')
      }
      .clip(true) // 如这里不设置clip为true，则Row组件的圆角不会限制其中的Image组件，Image组件的四个角会超出Row
      .borderRadius(20)

      // 用一个280px直径的圆对图片进行裁剪
      // $r("app.media.testImg")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.testImg'))
        .clipShape(new CircleShape({ width: '280px', height: '280px' }))
        .width('500px').height('280px')

      Text('mask').fontSize(12).width('75%').fontColor('#DCDCDC')
      // 给图片添加了一个500px*280px的方形遮罩
      // $r("app.media.testImg")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.testImg'))
        .maskShape(new RectShape({ width: '500px', height: '280px' }).fill(Color.Gray))
        .width('500px').height('280px')

      // 给图片添加了一个280px*280px的圆形遮罩
      // $r("app.media.testImg")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.testImg'))
        .maskShape(new CircleShape({ width: '280px', height: '280px' }).fill(Color.Gray))
        .width('500px').height('280px')
    }
    .width('100%')
    .margin({ top: 15 })
  }
}
```

### 示例2（实现组件遮罩）

该示例通过[mask](#mask12)实现图片的遮罩。

```TypeScript
@Entry
@Component
struct ProgressMaskExample {
  @State isRedColor: boolean = true;
  @State value: number = 10.0;
  @State enableBreathingAnimation: boolean = false;
  @State progress: ProgressMask = new ProgressMask(10.0, 100.0, Color.Gray);

  build() {
    Column({ space: 15 }) {
      Text('progress mask').fontSize(12).width('75%').fontColor('#DCDCDC')
      // 给图片添加了一个进度遮罩
      // $r("app.media.testImg")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.testImg'))
        .width('500px').height('280px')
        .mask(this.progress)
        .animation({
          duration: 2000, // 动画时长
          curve: Curve.Linear, // 动画曲线
          delay: 0, // 动画延迟
          iterations: 1, // 播放次数
          playMode: PlayMode.Normal // 动画模式
        }) // 对Image组件的遮罩进度变化进行动画配置

      // 更新进度遮罩的进度值
      Button('updateProgress')
        .onClick((event?: ClickEvent) => {
          this.value += 10;
          this.progress.updateProgress(this.value);
        }).width(200).height(50).margin(20)

      // 更新进度遮罩的颜色
      Button('updateColor')
        .onClick((event?: ClickEvent) => {
          if (this.isRedColor) {
            this.progress.updateColor(0x9fff0000);
          } else {
            this.progress.updateColor(0x9f0000ff);
          }
          this.isRedColor = !this.isRedColor;
        }).width(200).height(50).margin(20)

      // 开关呼吸光晕动画
      Button('enableBreathingAnimation:' + this.enableBreathingAnimation)
        .onClick((event?: ClickEvent) => {
          this.enableBreathingAnimation = !this.enableBreathingAnimation;
          this.progress.enableBreathingAnimation(this.enableBreathingAnimation);
        }).width(200).height(50).margin(20)

      // 恢复进度遮罩
      Button('click reset')
        .onClick((event?: ClickEvent) => {
          this.value = 0;
          this.progress.updateProgress(this.value);
        }).width(200).height(50).margin(20)
    }
    .width('100%')
    .margin({ top: 15 })
  }
}
```

### 示例1（通过DrawModifier进行自定义绘制）

通过DrawModifier对[Text](ts-basic-components-text.md)组件进行自定义绘制。



```TypeScript
// xxx.ets
import { drawing } from '@kit.ArkGraphics2D';
import { AnimatorResult } from '@kit.ArkUI';

// 继承DrawModifier实现自定义绘制控制器
class MyFullDrawModifier extends DrawModifier {
  public scaleX: number = 1;
  public scaleY: number = 1;
  uiContext: UIContext;

  constructor(uiContext: UIContext) {
    super();
    this.uiContext = uiContext;
  }

  // 重载drawBehind方法，自定义绘制背景  
  drawBehind(context: DrawContext): void {
    const brush = new drawing.Brush();
    brush.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    context.canvas.attachBrush(brush);
    const halfWidth = context.size.width / 2;
    const halfHeight = context.size.height / 2;
    context.canvas.drawRect({
      left: this.uiContext.vp2px(halfWidth - 50 * this.scaleX),
      top: this.uiContext.vp2px(halfHeight - 50 * this.scaleY),
      right: this.uiContext.vp2px(halfWidth + 50 * this.scaleX),
      bottom: this.uiContext.vp2px(halfHeight + 50 * this.scaleY)
    });
  }

  // 重载drawContent方法，自定义绘制内容
  drawContent(context: DrawContext): void {
    const brush = new drawing.Brush();
    brush.setColor({
      alpha: 255,
      red: 0,
      green: 255,
      blue: 0
    });
    context.canvas.attachBrush(brush);
    const halfWidth = context.size.width / 2;
    const halfHeight = context.size.height / 2;
    context.canvas.drawRect({
      left: this.uiContext.vp2px(halfWidth - 30 * this.scaleX),
      top: this.uiContext.vp2px(halfHeight - 30 * this.scaleY),
      right: this.uiContext.vp2px(halfWidth + 30 * this.scaleX),
      bottom: this.uiContext.vp2px(halfHeight + 30 * this.scaleY)
    });
  }

  // 重载drawFront方法，自定义绘制内容前景
  drawFront(context: DrawContext): void {
    const brush = new drawing.Brush();
    brush.setColor({
      alpha: 255,
      red: 0,
      green: 0,
      blue: 255
    });
    context.canvas.attachBrush(brush);
    const halfWidth = context.size.width / 2;
    const halfHeight = context.size.height / 2;
    const radiusScale = (this.scaleX + this.scaleY) / 2;
    context.canvas.drawCircle(this.uiContext.vp2px(halfWidth), this.uiContext.vp2px(halfHeight),
      this.uiContext.vp2px(20 * radiusScale));
  }
}

// 继承DrawModifier实现自定义绘制控制器，仅支持自定义绘制内容前景
class MyFrontDrawModifier extends DrawModifier {
  public scaleX: number = 1;
  public scaleY: number = 1;
  uiContext: UIContext;

  constructor(uiContext: UIContext) {
    super();
    this.uiContext = uiContext;
  }

  drawFront(context: DrawContext): void {
    const brush = new drawing.Brush();
    brush.setColor({
      alpha: 255,
      red: 0,
      green: 0,
      blue: 255
    });
    context.canvas.attachBrush(brush);
    const halfWidth = context.size.width / 2;
    const halfHeight = context.size.height / 2;
    const radiusScale = (this.scaleX + this.scaleY) / 2;
    context.canvas.drawCircle(this.uiContext.vp2px(halfWidth), this.uiContext.vp2px(halfHeight),
      this.uiContext.vp2px(20 * radiusScale));
  }
}

@Entry
@Component
struct DrawModifierExample {
  private fullModifier: MyFullDrawModifier = new MyFullDrawModifier(this.getUIContext());
  private frontModifier: MyFrontDrawModifier = new MyFrontDrawModifier(this.getUIContext());
  private drawAnimator: AnimatorResult | undefined = undefined;
  @State modifier: DrawModifier = new MyFrontDrawModifier(this.getUIContext());
  private count = 0;

  // 创建Animator对象并设置动画
  create() {
    let self = this;
    this.drawAnimator = this.getUIContext().createAnimator({
      duration: 1000,
      easing: 'ease',
      delay: 0,
      fill: 'forwards',
      direction: 'normal',
      iterations: 1,
      begin: 0,
      end: 2
    });
    // 设置帧回调，动态更新缩放值并触发重绘
    this.drawAnimator.onFrame = (value: number) => {
      console.info('frame value =', value);
      const tempModifier = self.modifier as MyFullDrawModifier | MyFrontDrawModifier;
      tempModifier.scaleX = Math.abs(value - 1);
      tempModifier.scaleY = Math.abs(value - 1);
      // 主动触发重绘
      self.modifier.invalidate();
    };
  }

  build() {
    Column() {
      Row() {
        Text('test text')
          .width(100)
          .height(100)
          .margin(10)
          .backgroundColor(Color.Gray)
          .onClick(() => {
            const tempModifier = this.modifier as MyFullDrawModifier | MyFrontDrawModifier;
            tempModifier.scaleX -= 0.1;
            tempModifier.scaleY -= 0.1;
          })
          .drawModifier(this.modifier)
      }

      Row() {
        Button('create')
          .width(100)
          .height(100)
          .borderRadius(50)
          .margin(10)
          .onClick(() => {
            this.create();
          })
        Button('play')
          .width(100)
          .height(100)
          .borderRadius(50)
          .margin(10)
          .onClick(() => {
            if (this.drawAnimator) {
              this.drawAnimator.play();
            }
          })
        Button('changeModifier')
          .width(100)
          .height(100)
          .borderRadius(50)
          .margin(10)
          .onClick(() => {
            this.count += 1;
            if (this.count % 2 === 1) {
              console.info('change to full modifier');
              this.modifier = this.fullModifier;
            } else {
              console.info('change to front modifier');
              this.modifier = this.frontModifier;
            }
          })
      }
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例2（通过DrawModifier对容器的前景进行自定义绘制）

通过DrawModifier对[Column](ts-container-column.md)容器的前景进行自定义绘制。

```TypeScript
// xxx.ets
import { drawing } from '@kit.ArkGraphics2D';

class MyForegroundDrawModifier extends DrawModifier {
  public scaleX: number = 3;
  public scaleY: number = 3;
  uiContext: UIContext;

  constructor(uiContext: UIContext) {
    super();
    this.uiContext = uiContext;
  }

  // 重载drawForeground方法，实现自定义绘制前景
  drawForeground(context: DrawContext): void {
    const brush = new drawing.Brush();
    brush.setColor({
      alpha: 255,
      red: 0,
      green: 50,
      blue: 100
    });
    context.canvas.attachBrush(brush);
    const halfWidth = context.size.width / 2;
    const halfHeight = context.size.height / 2;
    context.canvas.drawRect({
      left: this.uiContext.vp2px(halfWidth - 30 * this.scaleX),
      top: this.uiContext.vp2px(halfHeight - 30 * this.scaleY),
      right: this.uiContext.vp2px(halfWidth + 30 * this.scaleX),
      bottom: this.uiContext.vp2px(halfHeight + 30 * this.scaleY)
    });
  }
}

@Entry
@Component
struct DrawModifierExample {
  // 将自定义绘制前景的类实例化，传入UIContext实例
  private foregroundModifier: MyForegroundDrawModifier = new MyForegroundDrawModifier(this.getUIContext());

  build() {
    Column() {
      Text('此文本是子节点')
        .fontSize(36)
        .width('100%')
        .height('100%')
        .textAlign(TextAlign.Center)
    }
    .margin(50)
    .width(280)
    .height(300)
    .backgroundColor(0x87CEEB)
    // 调用此接口并传入自定义绘制前景的类实例，即可实现自定义绘制前景
    .drawModifier(this.foregroundModifier)
  }
}
```

该示例主要演示前景滤镜、背景滤镜和合成滤镜的模糊效果。

```TypeScript
// xxx.ets
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct FilterEffectExample {
  @State foregroundBlurFilter: uiEffect.Filter = uiEffect.createFilter().blur(10);
  @State backgroundBlurFilter: uiEffect.Filter = uiEffect.createFilter().blur(10);
  @State compositingBlurFilter: uiEffect.Filter = uiEffect.createFilter().blur(10);

  build() {
    Column({ space: 15 }) {

      Text('foregroundFilter').fontSize(20).width('75%').fontColor('#DCDCDC')
      Text('前景滤镜')
        .width(100)
        .height(100)
        .backgroundColor('#ADD8E6')
        // $r("app.media.app_icon")需在项目的“resources/base/media”目录下准备名为app_icon的图片资源文件
        .backgroundImage($r('app.media.app_icon'))
        .backgroundImageSize({ width: 80, height: 80 })
        .foregroundFilter(this.foregroundBlurFilter) // 通过foregroundFilter设置模糊效果

      Text('backgroundFilter').fontSize(20).width('75%').fontColor('#DCDCDC')
      Text('背景滤镜')
        .width(100)
        .height(100)
        .backgroundColor('#ADD8E6')
        // $r("app.media.app_icon")需替换为开发者所需的资源文件
        .backgroundImage($r('app.media.app_icon'))
        .backgroundImageSize({ width: 80, height: 80 })
        .backgroundFilter(this.backgroundBlurFilter) // 通过backgroundFilter设置模糊效果

      Text('compositingFilter').fontSize(20).width('75%').fontColor('#DCDCDC')
      Text('合成滤镜')
        .width(100)
        .height(100)
        .backgroundColor('#ADD8E6')
        // $r("app.media.app_icon")需替换为开发者所需的资源文件
        .backgroundImage($r('app.media.app_icon'))
        .backgroundImageSize({ width: 80, height: 80 })
        .compositingFilter(this.compositingBlurFilter) // 通过compositingFilter设置模糊效果
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例1（设置组件快捷键）

该示例通过设置组件的快捷键，同时按控制键+对应的字符可以触发组件响应快捷键，并触发onClick事件或自定义事件。



```TypeScript
@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column({ space: 5 }) {
        Text(this.message);
        Button('Test short cut 1').onClick(() => {
          this.message = 'I clicked Button 1';
          console.info('I clicked 1');
        }).keyboardShortcut('.', [ModifierKey.SHIFT, ModifierKey.CTRL, ModifierKey.ALT])
          .onKeyEvent((event: KeyEvent) => {
            console.info('event.keyCode: ' + JSON.stringify(event));
          });
        Button('Test short cut 2').onClick(() => {
          this.message = 'I clicked Button 2';
          console.info('I clicked 2');
        }).keyboardShortcut('1', [ModifierKey.CTRL]);
        Button('Test short cut 3').onClick(() => {
          this.message = 'I clicked Button 3';
          console.info('I clicked 3');
        }).keyboardShortcut('A', [ModifierKey.SHIFT]);
        Button('Test short cut 4').onClick(() => {
          this.message = 'I clicked Button 4';
          console.info('I clicked 4');
        }).keyboardShortcut(FunctionKey.F5, [], () => {
          this.message = 'I clicked Button 4';
          console.info('I clicked user callback.');
        }).keyboardShortcut(FunctionKey.F3, []);
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例2（快捷键的绑定和解除绑定）

该示例演示了如何实现快捷键的绑定和解除绑定。

```TypeScript
@Entry
@Component
struct Index {
  @State message: string = 'disable';
  @State shortCutEnable: boolean = false;
  @State keyValue: string = '';

  build() {
    Row() {
      Column({ space: 5 }) {
        Text('Ctrl+A is ' + this.message);
        Button('Test short cut').onClick(() => {
          this.message = 'I clicked Button';
          console.info('I clicked');
        }).keyboardShortcut(this.keyValue, [ModifierKey.CTRL]);
        Button(this.message + 'shortCut').onClick(() => {
          this.shortCutEnable = !this.shortCutEnable;
          this.message = this.shortCutEnable ? 'enable' : 'disable';
          this.keyValue = this.shortCutEnable ? 'a' : '';
        });
        Button('multi-shortcut').onClick(() => {
          console.info('Trigger keyboard shortcut success.');
        }).keyboardShortcut('q', [ModifierKey.CTRL])
          .keyboardShortcut('w', [ModifierKey.CTRL])
          .keyboardShortcut('', []); // 不生效，绑定了多个快捷键的组件不能解除绑定快捷键
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例1（设置无障碍文本和无障碍说明）

该示例主要演示accessibilityText无障碍文本和accessibilityDescription无障碍说明的播报内容。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @Builder
  customAccessibilityNode() {
    Column() {
      Text(`virtual node`)
    }
    .width(10)
    .height(10)
  }

  build() {
    Row() {
      Column() {
        Text('文本1')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
        Text("文本2")
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
      .accessibilityGroup(true)
      .accessibilityLevel("yes")
      .accessibilityText("分组") // 无障碍文本的内容，若组件既拥有文本属性又拥有无障碍文本属性，则组件被选中时，仅播报无障碍文本内容。
      .accessibilityDescription("Column组件可以被选中，播报的内容是“分组”")
      .accessibilityVirtualNode(this.customAccessibilityNode)
      .accessibilityChecked(true)
      .accessibilitySelected(undefined)
    }
    .height('100%')
  }
}
```

### 示例2（设置无障碍组）

该示例主要演示优先使用子组件的无障碍文本进行朗读。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Text('123456')
        .focusable(true)
        .borderRadius(5)
        .accessibilityText("有accessibility有text优先读accessibility")
        .accessibilityLevel("yes")
      Button().accessibilityLevel("yes").accessibilityText("accessibility无text 读accessibility")
      Button("无accessibility有text 读text").accessibilityLevel("yes")
      Button()
      Button('btn123').accessibilityText('有accessibility有text btn123').accessibilityLevel('yes')
      Button('btn123').accessibilityLevel("yes")
    }
    .accessibilityGroup(true, { accessibilityPreferred: true })
    .borderWidth(5)
    .width('100%')
    .height('100%')
  }
}
```

### 示例3（设置首焦点和组件的下一个焦点）

该示例主要演示accessibilityDefaultFocus屏幕朗读当前页默认首焦点和accessibilityNextFocusId走焦过程中组件的下一个焦点。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column({ space: 20 }) {
      Text('Text Demo 1')
        .fontSize(50)
        .accessibilityLevel('yes')
        .accessibilityNextFocusId('text3')
      Text('Text Demo 2')
        .id('text2')
        .fontSize(50)
        .accessibilityLevel('yes')
        .accessibilityDefaultFocus(true)  // 设置该组件为屏幕朗读当前页默认首焦点
        .accessibilityNextFocusId('text4')
      Text('Text Demo 3')
        .id('text3')
        .fontSize(50)
        .accessibilityLevel('yes')
        .accessibilityNextFocusId('text2')
      Text('Text Demo 4')
        .id('text4')
        .fontSize(50)
        .accessibilityLevel('yes')
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例4（设置无障碍组件类型和文本提示信息）

该示例主要演示accessibilityRole无障碍组件类型和accessibilityTextHint设置组件的文本提示信息（仅在与车机交互的场景下供车机的无障碍服务监听并响应）。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State isDownloading: boolean = false;
  @State hintStr: string = '点击开始下载';

  build() {
    Column({ space: 20 }) {
      Button(this.isDownloading ? '下载中' : '点击下载')
        .accessibilityLevel('yes')
        .accessibilityTextHint(this.hintStr)
        .onClick(() => {
          this.isDownloading = !this.isDownloading;
          this.hintStr = this.isDownloading ? '状态变为下载中' : '状态变为暂停下载';
        })
      TextInput({ placeholder: '请输入手机号码' })
        .accessibilityLevel('yes')
        .accessibilityTextHint('请输入11位手机号码')
        .width('80%')
      Text('按照按钮类型播报')
        .accessibilityLevel('yes')
        .accessibilityRole(AccessibilityRoleType.BUTTON)
        .accessibilityTextHint('屏幕朗读播报时，该组件将按照按钮类型进行播报')
        .fontSize(30)
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例5（设置无障碍屏幕朗读滚动和焦点绿框绘制）

该示例主要演示accessibilityScrollTriggerable设置无障碍节点是否支持屏幕朗读滚动、accessibilityFocusDrawLevel设置无障碍焦点绿框的绘制层级和accessibilityUseSamePage为跨进程嵌入式显示的组件（如[EmbeddedComponent](ts-container-embedded-component.md)）设置同page模式。



```TypeScript
// xxx.ets
import { Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'Message: ';
  private want: Want = {
    // EmbeddedComponent提供方的bundleName，根据实际情况配置。
    bundleName: 'com.example.embeddeddemo',
    // EmbeddedComponent提供方的abilityName，根据实际情况配置。
    abilityName: 'ExampleEmbeddedAbility',
  }

  build() {
    Row() {
      List() {
        ListItem() {
          Column() {
            Text(this.message)
              .fontSize(18)
              .fontColor('#2D2D2D')
              .fontWeight(FontWeight.Medium)
            Column() {
              EmbeddedComponent(this.want, EmbeddedType.EMBEDDED_UI_EXTENSION)
                .onTerminated((info) => {
                  this.message = 'Termination: code = ' + info.code + ', want = ' + JSON.stringify(info.want);
                })
                .onError((error) => {
                  this.message = 'Error: code = ' + error.code;
                })
                .accessibilityUseSamePage(AccessibilitySamePageMode.FULL_SILENT)
                .width('90%')
                .height('50%')
                .backgroundColor('#F0F0F0')
                .borderRadius(8)
                .borderWidth(1)
                .borderColor('#D9D9D9')

              Stack() {
                Column() {
                  Text('文本1')
                    .fontSize(18)
                    .fontColor('#2D2D2D')
                    .fontWeight(FontWeight.Medium)
                  Text('文本1')
                    .fontSize(18)
                    .fontColor('#2D2D2D')
                    .fontWeight(FontWeight.Medium)
                    .accessibilityFocusDrawLevel(FocusDrawLevel.TOP)
                }
                .padding({ top: 8, bottom: 8 })

                Column() {
                  Text('文本2')
                    .fontSize(18)
                    .fontColor('#FFFFFF')
                    .fontWeight(FontWeight.Medium)
                  Text('文本2')
                    .fontSize(18)
                    .fontColor('#FFFFFF')
                    .fontWeight(FontWeight.Medium)
                }
                .backgroundColor('#4A90E2')
                .padding({
                  left: 12,
                  right: 12,
                  top: 10,
                  bottom: 10
                })
                .borderRadius(6)
              }
              .width('100%')
              .margin({ top: 10, bottom: 10 })
            }
            .width('100%')
            .height('100%')
            .margin({ top: 15 })
            .accessibilityText($r('app.string.app_name'))
            .accessibilityDescription($r('app.string.module_desc'))

            Column() {
              Text('文本4')
                .fontSize(18)
                .fontWeight(FontWeight.Medium)
            }
            .margin({ top: 15 })
          }
          .width('100%')
        }
      }
      .accessibilityScrollTriggerable(false)
      .width('100%')
    }
    .height('100%')
    .backgroundColor('#F7F9FC')
  }
}
```

### 示例6（设置无障碍聚合功能下的子组件状态和操作接管功能）

该示例主要演示使用accessibilityGroup的可选参数stateControllerRoleType或者stateControllerId来选择一个特定子组件接管其无障碍状态信息，可选参数actionControllerRoleType或者actionControllerId来选择一个特定子组件接管其无障碍控制操作。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {

  build() {
    Column({ space: 20 }) {
      Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
        Text('是否开启功能')
        Toggle({ type: ToggleType.Switch, isOn: false })
          .selectedColor('#007DFF')
          .switchPointColor('#FFFFFF')
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })
      }
      .accessibilityGroup(true, {
        stateControllerRoleType: AccessibilityRoleType.TOGGLER,
        actionControllerRoleType: AccessibilityRoleType.TOGGLER
      })
      .width('80%')
      .border({ color: Color.Black, width: 2 })

      Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
        Text("是否开启功能")
        Toggle({ type: ToggleType.Switch, isOn: false })
          .selectedColor('#007DFF')
          .switchPointColor('#FFFFFF')
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })
          .id("TestToggle")
      }
      .accessibilityGroup(true, {
        stateControllerId: "TestToggle",
        actionControllerId: "TestToggle"
      })
      .width('80%')
      .border({ color: Color.Black, width: 2 })

    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例7（设置无障碍组件状态播报信息）

该示例主要通过[accessibilityStateDescription](#accessibilitystatedescription23)接口修改组件的状态播报。在开启无障碍功能后，组件发生聚焦或者点击后，屏幕朗读进行组件的状态信息播报。

从API version 23开始，新增accessibilityStateDescription接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State isSelected: boolean = false;

  build() {
    Column({ space: 20 }) {
      Button(this.isSelected ? '已点赞' : '未点赞')
        .accessibilityLevel('yes')
        .onClick(() => {
          this.isSelected = !this.isSelected;
        })
        .accessibilityStateDescription(this.isSelected ? '已点赞' : '未点赞')
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例8（设置无障碍操作选项修改组件滑动步数）

本示例主要演示如何通过[accessibilityActionOptions](ts-types.md#accessibilityactionoptions23对象说明)中的scrollStep参数，自定义组件的滑动步数。以下将以slider组件在屏幕朗读场景下滑动距离变化为例进行说明。

从API version 23开始，新增AccessibilityActionOptions。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column({ space: 20 }) {
      Row() {
        Slider({
          min: 0,
          max: 100,
          style: SliderStyle.OutSet
        })
        // 调整屏幕朗读手势下slider滑动的步数
        .accessibilityActionOptions({ scrollStep: 10 })
      }
      .width('80%')
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例9（设置自定义无障碍操作）

本示例主要演示如何使用[accessibilityCustomActions](arkts-arkui-common-comp-commonmethod-c.md#accessibilitycustomactions)为组件设置自定义无障碍操作。开发者可以按操作名为组件进行自定义操作的回调绑定。

从API版本26.0.0开始，新增accessibilityCustomActions。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State listData: Array<string> = ['列表项1', '列表项2', '列表项3', '列表项4'];

  build() {
    Column() {
      List({ space: 10 }) {
        ForEach(this.listData, (item: string, index: number) => {
          ListItem() {
            Row() {
              Text(item)
                .fontSize(16)
              Blank()
              Text('删除')
                .fontSize(14)
                .fontColor(Color.Red)
            }
            .width('100%')
            .padding(10)
            .onClick(() => {
              console.info('[TestTag] click success!')
            })
            .accessibilityLevel('yes')
            .accessibilityCustomActions([
              {
                name: 'deleteItem',
                onAction: () => {
                  this.listData.splice(index, 1);
                }
              }
            ])
          }
        }, (item: string) => item)
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

### 示例1（设置Text多态样式）

该示例展示了[stateStyles](#statestyles)设置状态为hovered、pressed和disabled时Text组件的样式变化。

从API版本26.0.0开始，[stateStyles](#statestyles)新增hovered属性。



```TypeScript
// xxx.ets
@Entry
@Component
struct StyleExample {
  @State isEnable: boolean = true

  @Styles
  hoveredStyles(): void {
    .backgroundColor('#12db70')
    .borderRadius(10)
    .borderStyle(BorderStyle.Dashed)
    .borderWidth(2)
    .borderColor('#33000000')
    .width(120)
    .height(30)
    .opacity(1)
  }

  @Styles
  pressedStyles(): void {
    .backgroundColor('#ED6F21')
    .borderRadius(10)
    .borderStyle(BorderStyle.Dashed)
    .borderWidth(2)
    .borderColor('#33000000')
    .width(120)
    .height(30)
    .opacity(1)
  }

  @Styles
  disabledStyles(): void {
    .backgroundColor('#E5E5E5')
    .borderRadius(10)
    .borderStyle(BorderStyle.Solid)
    .borderWidth(2)
    .borderColor('#2a4c1919')
    .width(90)
    .height(25)
    .opacity(1)
  }

  @Styles
  normalStyles(): void {
    .backgroundColor('#0A59F7')
    .borderRadius(10)
    .borderStyle(BorderStyle.Solid)
    .borderWidth(2)
    .borderColor('#33000000')
    .width(100)
    .height(25)
    .opacity(1)
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center }) {
      Text('normal')
        .fontSize(14)
        .fontColor(Color.White)
        .opacity(0.5)
        // stateStyles设置组件无状态时的样式
        .stateStyles({
          normal: this.normalStyles,
        })
        .margin({ bottom: 20 })
        .textAlign(TextAlign.Center)
      Text('hovered')
        .backgroundColor('#0A59F7')
        .borderRadius(20)
        .borderStyle(BorderStyle.Dotted)
        .borderWidth(2)
        .borderColor(Color.Red)
        .width(100)
        .height(25)
        .opacity(1)
        .fontSize(14)
        .fontColor(Color.White)
        // stateStyles设置组件鼠标悬浮状态时的样式
        .stateStyles({
          hovered: this.hoveredStyles,
        })
        .margin({ bottom: 20 })
        .textAlign(TextAlign.Center)
      Text('pressed')
        .backgroundColor('#0A59F7')
        .borderRadius(20)
        .borderStyle(BorderStyle.Dotted)
        .borderWidth(2)
        .borderColor(Color.Red)
        .width(100)
        .height(25)
        .opacity(1)
        .fontSize(14)
        .fontColor(Color.White)
        // stateStyles设置组件按下状态时的样式
        .stateStyles({
          pressed: this.pressedStyles,
        })
        .margin({ bottom: 20 })
        .textAlign(TextAlign.Center)
      Text(this.isEnable ? 'effective' : 'disabled')
        .backgroundColor('#0A59F7')
        .borderRadius(20)
        .borderStyle(BorderStyle.Solid)
        .borderWidth(2)
        .borderColor(Color.Gray)
        .width(100)
        .height(25)
        .opacity(1)
        .fontSize(14)
        .fontColor(Color.White)
        .enabled(this.isEnable)
        // stateStyles设置组件禁用状态时的样式
        .stateStyles({
          disabled: this.disabledStyles,
        })
        .textAlign(TextAlign.Center)
      Text('control disabled')
        .onClick(() => {
          this.isEnable = !this.isEnable;
          console.info(`${this.isEnable}`);
        })
    }
    .width(350).height(300)
  }
}
```

### 示例2（设置Radio多态样式）

该示例展示了状态为selected时Radio组件的样式变化。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State isRadio1Selected: boolean = false
  @State isRadio2Selected: boolean = false

  @Styles
  normalStyles(): void {
    .backgroundColor('#E5E5E1')
  }

  @Styles
  selectStyles(): void {
    .backgroundColor('#ED6F21')
    .borderWidth(2)
  }

  build() {
    Flex({ direction: FlexDirection.Row, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Column() {
        Text('Radio1')
          .fontSize(25)
        Radio({ value: 'Radio1', group: 'radioGroup1' })
          .checked(this.isRadio1Selected)
          .height(50)
          .width(50)
          .borderWidth(0)
          .borderRadius(30)
          .onClick(() => {
            this.isRadio1Selected = !this.isRadio1Selected;
          })
          .stateStyles({
            normal: this.normalStyles,
            selected: this.selectStyles,
          })
      }
      .margin(30)

      Column() {
        Text('Radio2')
          .fontSize(25)
        Radio({ value: 'Radio2', group: 'radioGroup2' })
          .checked($$this.isRadio2Selected)
          .height(50)
          .width(50)
          .borderWidth(0)
          .borderRadius(30)
          .stateStyles({
            normal: this.normalStyles,
            selected: this.selectStyles,
          })
      }
      .margin(30)
    }.padding({ top: 30 })
  }
}
```

### 示例3（设置Builder多态样式）

该示例展示了状态为pressed时@Builder中自定义组件的样式变化。

```TypeScript
import { ComponentContent } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Component
struct Child {
  build() {
    Row()
      .zIndex(10)
      .width(200)
      .height(200)
      .stateStyles({
        normal: {
          .backgroundColor(Color.Blue)
        },
        pressed: {
          .backgroundColor(Color.Black)
        }
      })
  }
}

@Builder
function buildText() {
  Child()
}

@Entry
@Component
struct Index {
  private contentNode: ComponentContent<Object> =
    new ComponentContent(this.getUIContext(), wrapBuilder(buildText));

  build() {
    Column() {
      Button().margin({ top: 200 }).onClick(() => {
        this.getUIContext()
          .getPromptAction()
          .openCustomDialog(this.contentNode)
          .then(() => {
            console.info('OpenCustomDialog complete.');
          })
          .catch((error: BusinessError) => {
            let message = error.message;
            let code = error.code;
            console.error(`OpenCustomDialog args error code is ${code}, message is ${message}`);
          });
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

该示例主要展示如何通过组件标识接口，获取特定id组件的属性，以及如何向该id的组件触发事件。

```TypeScript
// xxx.ets
import { IntentionCode } from '@kit.InputKit';

class Utils {
  static rectLeft: number;
  static rectTop: number;
  static rectRight: number;
  static rectBottom: number;
  static rectValue: Record<string, number>;

  // 获取组件所占矩形区域坐标
  static getComponentRect(key: string): Record<string, number> {
    let strJson = getInspectorByKey(key);
    let obj: Record<string, string> = JSON.parse(strJson);
    console.info('[getInspectorByKey] current component obj is: ' + JSON.stringify(obj));
    let rectInfo: string[] = JSON.parse('[' + obj.$rect + ']');
    console.info('[getInspectorByKey] rectInfo is: ' + rectInfo);
    Utils.rectLeft = JSON.parse('[' + rectInfo[0] + ']')[0]; // 组件左上角相对于窗口左上角的水平方向坐标
    Utils.rectTop = JSON.parse('[' + rectInfo[0] + ']')[1]; // 组件左上角相对于窗口左上角的垂直方向坐标
    Utils.rectRight = JSON.parse('[' + rectInfo[1] + ']')[0]; // 组件右下角相对于窗口左上角的水平方向坐标
    Utils.rectBottom = JSON.parse('[' + rectInfo[1] + ']')[1]; // 组件右下角相对于窗口左上角的垂直方向坐标
    return Utils.rectValue = {
      "left": Utils.rectLeft,
      "top": Utils.rectTop,
      "right": Utils.rectRight,
      "bottom": Utils.rectBottom
    };
  };
}

@Entry
@Component
struct IdExample {
  @State text: string = '';

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {

      Button() {
        Text('onKeyTab').fontSize(25).fontWeight(FontWeight.Bold)
      }.margin({ top: 20 }).backgroundColor('#0D9FFB')
      .onKeyEvent(() => {
        this.text = 'onKeyTab';
      })

      Button() {
        Text('click to start').fontSize(25).fontWeight(FontWeight.Bold)
      }.margin({ top: 20 })
      .onClick(() => {
        console.info(getInspectorByKey('click'));
        console.info(JSON.stringify(getInspectorTree()));
        this.text = "Button 'click to start' is clicked";
        setTimeout(() => {
          sendEventByKey('longClick', 11, ''); // 向id为"longClick"的组件发送长按事件
        }, 2000)
      }).id('click')

      Button() {
        Text('longClick').fontSize(25).fontWeight(FontWeight.Bold)
      }.margin({ top: 20 }).backgroundColor('#0D9FFB')
      .gesture(
        LongPressGesture().onActionEnd(() => {
          console.info('long clicked');
          this.text = "Button 'longClick' is longclicked";
          setTimeout(() => {
            let rect = Utils.getComponentRect('onTouch'); // 获取id为"onTouch"组件的矩形区域坐标
            let touchPoint: TouchObject = {
              id: 1,
              type: TouchType.Down,
              x: rect.left + (rect.right - rect.left) / 2, // 相对于组件左上角的水平方向坐标
              y: rect.top + (rect.bottom - rect.top) / 2, // 相对于组件左上角的垂直方向坐标
              windowX: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的水平方向坐标
              windowY: rect.top + (rect.bottom - rect.top) / 2, // 相对于应用窗口左上角的垂直方向坐标
              displayX: rect.left + (rect.right - rect.left) / 2, // 相对于设备屏幕左上角的水平方向坐标
              displayY: rect.top + (rect.bottom - rect.top) / 2, // 相对于设备屏幕左上角的垂直方向坐标
              screenX: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的水平方向坐标
              screenY: rect.top + (rect.bottom - rect.top) / 2, // 相对于应用窗口左上角的垂直方向坐标
            };
            sendTouchEvent(touchPoint); // 发送触摸事件
            touchPoint.type = TouchType.Up;
            sendTouchEvent(touchPoint); // 发送触摸事件
          }, 2000)
        })).id('longClick')

      Button() {
        Text('onTouch').fontSize(25).fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule).margin({ top: 20 })
      .onClick(() => {
        console.info('onTouch is clicked');
        this.text = "Button 'onTouch' is clicked";
        setTimeout(() => {
          let rect = Utils.getComponentRect('onMouse'); // 获取id为"onMouse"组件的矩形区域坐标
          let mouseEvent: MouseEvent = {
            button: MouseButton.Left,
            action: MouseAction.Press,
            x: rect.left + (rect.right - rect.left) / 2, // 相对于组件左上角的水平方向坐标
            y: rect.top + (rect.bottom - rect.top) / 2, // 相对于组件左上角的垂直方向坐标
            windowX: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的水平方向坐标
            windowY: rect.top + (rect.bottom - rect.top) / 2, // 相对于应用窗口左上角的垂直方向坐标
            displayX: rect.left + (rect.right - rect.left) / 2, // 相对于设备屏幕左上角的水平方向坐标
            displayY: rect.top + (rect.bottom - rect.top) / 2, // 相对于设备屏幕左上角的垂直方向坐标
            screenX: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的水平方向坐标
            screenY: rect.top + (rect.bottom - rect.top) / 2, // 相对于应用窗口左上角的垂直方向坐标
            stopPropagation: () => {
            },
            timestamp: 1,
            target: {
              area: {
                width: 1,
                height: 1,
                position: {
                  x: 1,
                  y: 1
                },
                globalPosition: {
                  x: 1,
                  y: 1
                }
              }
            },
            source: SourceType.Mouse,
            pressure: 1,
            tiltX: 1,
            tiltY: 1,
            sourceTool: SourceTool.Unknown
          };
          sendMouseEvent(mouseEvent); // 发送鼠标事件
        }, 2000)
      }).id('onTouch')

      Button() {
        Text('onMouse').fontSize(25).fontWeight(FontWeight.Bold)
      }.margin({ top: 20 }).backgroundColor('#0D9FFB')
      .onMouse(() => {
        console.info('onMouse');
        this.text = "Button 'onMouse' in onMouse";
        setTimeout(() => {
          let keyEvent: KeyEvent = {
            type: KeyType.Down,
            keyCode: 2049,
            keyText: 'tab',
            keySource: 4,
            deviceId: 0,
            metaKey: 0,
            timestamp: 0,
            stopPropagation: () => {
            },
            intentionCode: IntentionCode.INTENTION_DOWN
          };
          sendKeyEvent(keyEvent); // 发送按键事件
        }, 2000)
      }).id('onMouse')

      Text(this.text).fontSize(25).padding(15)
    }
    .width('100%').height('100%')
  }
}
```

该示例通过animation实现了组件的属性动画。

```TypeScript
// xxx.ets
@Entry
@Component
struct AttrAnimationExample {
  @State widthSize: number = 250
  @State heightSize: number = 100
  @State rotateAngle: number = 0
  @State flag: boolean = true

  build() {
    Column() {
      Button('change size')
        .onClick(() => {
          if (this.flag) {
            this.widthSize = 150
            this.heightSize = 60
          } else {
            this.widthSize = 250
            this.heightSize = 100
          }
          this.flag = !this.flag
        })
        .margin(30)
        .width(this.widthSize)
        .height(this.heightSize)
        .animation({
          duration: 2000,
          curve: Curve.EaseOut,
          iterations: 3,
          playMode: PlayMode.Normal
        })
      Button('change rotate angle')
        .onClick(() => {
          this.rotateAngle = 90
        })
        .margin(50)
        .rotate({ angle: this.rotateAngle })
        // 为旋转角度变化配置阻尼曲线，延迟500ms启动，无限循环交替播放
        .animation({
          duration: 1200,
          curve: Curve.Friction,
          delay: 500,
          iterations: -1, // 设置-1表示动画无限循环
          playMode: PlayMode.Alternate,
          expectedFrameRateRange: {
            min: 20,
            max: 120,
            expected: 90,
          }
        })
    }.width('100%').margin({ top: 20 })
  }
}
```

### 示例1（不同高度的半模态弹窗）

该示例通过height设置不同高度的半模态弹窗。



```TypeScript
// xxx.ets
@Entry
@Component
struct SheetTransitionExample {
  @State isShow: boolean = false;
  @State sheetHeight: number = 300;

  @Builder
  myBuilder() {
    Column() {
      Button("change height")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.sheetHeight = 500;
        })

      Button("Set Illegal height")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.sheetHeight = -1;
        })

      Button("close modal 1")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow = false;
        })
    }
    .width('100%')
    .height('100%')
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          height: this.sheetHeight,
          backgroundColor: Color.Green,
          onWillAppear: () => {
            console.info("BindSheet onWillAppear.");
          },
          onAppear: () => {
            console.info("BindSheet onAppear.");
          },
          onWillDisappear: () => {
            console.info("BindSheet onWillDisappear.");
          },
          onDisappear: () => {
            console.info("BindSheet onDisappear.");
          }
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

### 示例2（设置三个不同高度的挡位）

使用bindSheet的detents属性设置三个不同高度的挡位。

dragBar控制条只在多个挡位高度时生效；

区别于height属性在不同时刻设置不同挡位的能力，多挡位能力有手势切换挡位高度的效果，且更适合固定高度区间的场景；

若高度范围不确定，且可能存在大于3个不同高度的场景，不建议使用detents属性。



```TypeScript
// xxx.ets
@Entry
@Component
struct SheetTransitionExample {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Button("content1")
        .margin(10)
        .fontSize(20)

      Button("content2")
        .margin(10)
        .fontSize(20)
    }
    .width('100%')
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          detents: [SheetSize.MEDIUM, SheetSize.LARGE, 200],
          blurStyle: BlurStyle.Thick,
          showClose: true,
          title: { title: "title", subtitle: "subtitle" },
        })
    }
    .justifyContent(FlexAlign.Start)
    .width('100%')
    .height('100%')
  }
}
```

### 示例3（使用边框宽度和颜色）

bindSheet属性的borderWidth、borderColor属性值使用LocalizedEdgeWidths类型和LocalizedEdgeColors类型。

从左至右显示语言模式示例图



从右至左显示语言模式示例图



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SheetTransitionExample {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Button("content1")
        .margin(10)
        .fontSize(20)

      Button("content2")
        .margin(10)
        .fontSize(20)
    }
    .width('100%')
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          detents: [SheetSize.MEDIUM, SheetSize.LARGE, 200],
          backgroundColor: Color.Gray,
          blurStyle: BlurStyle.Thick,
          showClose: true,
          title: { title: "title", subtitle: "subtitle" },
          borderWidth: { top: LengthMetrics.vp(10), start: LengthMetrics.vp(10), end: LengthMetrics.vp(20) },
          borderColor: { top: Color.Pink, start: Color.Blue, end: Color.Yellow },
        })
    }
    .justifyContent(FlexAlign.Start)
    .width('100%')
    .height('100%')
  }
}
```

### 示例4（使用关闭回调函数）

bindSheet注册onWillDismiss与onWillSpringBackWhenDismiss。



```TypeScript
// xxx.ets
@Entry
@Component
struct BindSheetExample {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Button("CONTEXT")
        .margin(10)
        .fontSize(20)
    }
  }

  build() {
    Column() {
      Button("NoRegisterSpringback")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          height: SheetSize.MEDIUM,
          blurStyle: BlurStyle.Thick,
          showClose: true,
          title: { title: "title", subtitle: "subtitle" },
          preferType: SheetType.CENTER,

          onWillDismiss: ((dismissSheetAction: DismissSheetAction) => {
            // 仅在用户下滑操作时，调用dismiss关闭半模态页面
            if (dismissSheetAction.reason == DismissReason.SLIDE_DOWN) {
                dismissSheetAction.dismiss(); // 关闭半模态页面
            }
          }),

          onWillSpringBackWhenDismiss: ((springBackAction: SpringBackAction) => {
          // 没有注册springBack，下拉半模态页面无回弹行为
          // SpringBackAction.springBack();
          }),
        })
    }
  }
}
```

### 示例5（设置内容区刷新时机）

ScrollSizeMode.CONTINUOUS持续更新内容适合detents多挡位切换场景。

建议在builder内减少UI加载耗时的操作，滑动时内容实时刷新对性能要求较高。

跟手触发挡位切换时，松手才触发面板内容高度刷新。



跟手触发挡位切换时，跟手时期就会触发面板内容高度刷新。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Column()
        .backgroundColor(Color.Blue)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Green)
        .height(200)
        .width('100%')
    }
  }

  build() {
    Column() {
      Button("BindSheet")
        .onClick(() => {
          this.isShow = true;
        })
        .bindSheet($$this.isShow, this.myBuilder(), {
          detents: [300, 600, 900],
          uiContext: this.getUIContext(),
          mode: SheetMode.OVERLAY,
          scrollSizeMode: ScrollSizeMode.CONTINUOUS,
          backgroundColor: Color.Orange,
          title: { title: 'Title', subtitle: 'Subtitle' }
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

### 示例6（设置压缩模态内容）

通过设置SheetKeyboardAvoidMode为RESIZE_ONLY，当键盘高度变化时，根据高度变化实现滚动组件的滚动。



```TypeScript
// xxx.ets
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ListenKeyboardHeightChange {
  @State isShow: boolean = false;
  @State avoidMode: SheetKeyboardAvoidMode = SheetKeyboardAvoidMode.RESIZE_ONLY;
  scroller = new Scroller();
  private numberList: number[] = [0, 1, 2, 3, 4, 5, 6];
  windowClass: window.Window | undefined = undefined;

  aboutToAppear(): void {
    try {
      window.getLastWindow(this.getUIContext().getHostContext(), (err: BusinessError, data) => {
        if (err && err.code) {
          console.error(`Failed to obtain the top window, Code: ${err.code}, message: ${err.message}`);
          return;
        }
        this.windowClass = data;
        try {
          if (this.windowClass !== undefined) {
            console.info('success in listen height change');
            this.windowClass.on('keyboardHeightChange', this.callback);
          }
        } catch (exception) {
          console.error(`Failed to enable the listener for keyboard height changes, Cause code: ${exception.code}, message: ${exception.message}`);
        }
        console.info('Succeeded in obtaining the top window. Data: ' + JSON.stringify(data));
      });
    } catch (exception) {
      console.error(`Failed to obtain the top window, Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }

  callback = (height: number) => {
    console.info('height change: ' + height);
    if (height !== 0) {
      this.scroller.scrollTo({
        xOffset: 0, yOffset: height + this.scroller.currentOffset().yOffset,
        animation: { duration: 1000, curve: Curve.Ease, canOverScroll: false }
      });
    }
  }

  @Builder
  myBuilder() {
    Scroll(this.scroller) {
      Column() {
        ForEach(this.numberList, (item: number) => {
          Row() {
            Text(item.toString())
              .width('80%')
              .height(60)
              .backgroundColor('#3366CC')
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 5 })
          }
        }, (item: number) => item.toString())

        TextInput().height('100')

        Flex({ alignItems: ItemAlign.End }) {
          Row() {
            Button("click")
              .margin(10)
              .fontSize(20)
              .width('45%')

            Button("cancel")
              .margin(10)
              .fontSize(20)
              .width('45%')
          }.width('100%')
        }.height(100)
      }.margin({ right: 15, bottom: 50 })
    }
    .height('100%')
    .scrollBar(BarState.On)
    .scrollable(ScrollDirection.Vertical)
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          height: 750,
          backgroundColor: Color.Gray,
          blurStyle: BlurStyle.Thick,
          showClose: true,
          title: { title: "title", subtitle: "subtitle" },
          keyboardAvoidMode: SheetKeyboardAvoidMode.RESIZE_ONLY,
        })
    }
    .justifyContent(FlexAlign.Start)
    .width('100%')
    .height('100%')
  }
}
```

### 示例7（镜像场景下如何设置圆角属性）

此示例为说明镜像场景而设置了不同的圆角半径，通常不建议开发者设置不同的值，会造成视觉体验不佳。

其中，从API version 15开始，半模态的radius属性值使用LocalizedBorderRadiuses类型。

从左至右显示语言模式示例图



从右至左显示语言模式示例图



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SheetTransitionExample {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Button("content1")
        .margin(10)
        .fontSize(20)

      Button("content2")
        .margin(10)
        .fontSize(20)
    }
    .width('100%')
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          detents: [SheetSize.MEDIUM, SheetSize.LARGE, 200],
          title: { title: "title", subtitle: "subtitle" },
          radius: { topStart: LengthMetrics.vp(50), topEnd: LengthMetrics.vp(10) },
        })
    }
    .justifyContent(FlexAlign.Start)
    .width('100%')
    .height('100%')
  }
}
```

### 示例8（半模态Side侧边样式）

从API version 20开始，此示例实现半模态侧边样式。



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SheetSideExample {
  @State isShowSide: boolean = false;
  @State enableOutsideInteractive: boolean = false;
  @State borderWidths: LocalizedEdgeWidths | undefined = undefined;
  @State borderColors: Resource | undefined = undefined;
  private numberList: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16];

  @Builder
  sideBuilder() {
    Column() {
      ForEach(this.numberList, (item: number) => {
        Row() {
          Text(item.toString())
            .width('90%')
            .height(60)
            .backgroundColor('#3366CC')
            .borderRadius(15)
            .fontSize(16)
            .textAlign(TextAlign.Center)
            .margin({ top: 5 })
        }
      }, (item: number) => item.toString())
      TextInput()
        .margin({ top: 5 })
      Text('改变半模态交互模式')
        .fontSize(22).fontColor(Color.White).fontWeight(FontWeight.Bold).textAlign(TextAlign.Center)
        .width('100%').height(50).backgroundColor('#2ebd82')
      Button("change enableOutsideInteractive = " + this.enableOutsideInteractive)
        .margin({ top: 5 })
        .onClick(() => {
          this.enableOutsideInteractive = !this.enableOutsideInteractive;
          if (this.enableOutsideInteractive) {
            this.borderWidths = {start : LengthMetrics.vp(1)};
            this.borderColors = $r('sys.color.comp_divider');
          } else {
            this.borderWidths = undefined;
            this.borderColors = undefined;
          }
        })
    }
    .width('100%')
    .height('auto')
  }


  build() {
    Column({space:3}) {
      Button("半模态弹窗-Side")
        .onClick(() => {
          this.isShowSide = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShowSide, this.sideBuilder(), {
          title: { title: "SideSheet", subtitle: "默认宽度" },
          backgroundColor: Color.Grey,
          onWillAppear: () => {
            console.info("SideSheet onWillAppear.");
          },
          onAppear: () => {
            console.info("SideSheet onAppear.");
          },
          onWillDisappear: () => {
            console.info("SideSheet onWillDisappear.");
          },
          onDisappear: () => {
            console.info("SideSheet onDisappear.");
          },

          preferType: SheetType.SIDE,
          blurStyle: BlurStyle.Regular,
          maskColor: "#4bffc62d",  // 自定义蒙层颜色
          enableOutsideInteractive: this.enableOutsideInteractive,

          borderWidth: this.borderWidths,
          borderColor: this.borderColors,

          onHeightDidChange: (height: number) => {
            console.info("SideSheet height change:" + height);
          },
          onTypeDidChange: (type: SheetType) => {
            console.info("SideSheet type change:" + type);
          },
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

### 示例9（半模态ContentCover全屏样式）

从API version 20开始，此示例实现半模态的全屏显示效果。



```TypeScript
// xxx.ets
@Entry
@Component
struct ContentCoverExample {
  @State isShow: boolean = false

  @Builder
  myBuilder() {
    Column() {
      Button("Close Content Cover Sheet")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow = false;
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }

  build() {
    Column() {
      Button("Show Content Cover Sheet")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet(this.isShow, this.myBuilder(), {
          modalTransition: ModalTransition.DEFAULT,
          preferType: SheetType.CONTENT_COVER,
          backgroundColor: '#ffd5d5d5',
          onWillAppear: () => {
            console.info("ContentCover onWillAppear.");
          },
          onAppear: () => {
            console.info("ContentCover onAppear.");
          },
          onWillDisappear: () => {
            console.info("ContentCover onWillDisappear.");
          },
          onDisappear: () => {
            console.info("ContentCover onDisappear.");
          },
        })
    }
    .justifyContent(FlexAlign.Center)
    .backgroundColor(Color.White)
    .width('100%')
    .height('100%')
  }
}
```

### 示例10（半模态设置系统材质）

该示例通过半模态systemMaterial属性设置系统材质。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，[SheetOptions](arkts-arkui-common-comp-sheetoptions-i.md)新增systemMaterial属性。



```TypeScript
// xxx.ets
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct SheetMaterialExample {
  @State isShow: boolean = false;
  @State sheetHeight: number = 300;
  @State myMaterial: SystemUiMaterial | undefined = new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.ULTRA_THICK,
  });

  @Builder
  myBuilder() {
    Column({ space: 10 }) {
      Text("Text")
        .fontSize(20)
        .margin(10)
    }
    .width('100%')
    .height('100%')
  }

  build() {
    Stack() {
      // 请开发者替换为实际资源文件
      Image($r('app.media.startIcon'))
      Column() {
        Button("open Sheet")
          .onClick(() => {
            this.isShow = true;
          })
          .fontSize(20)
          .margin(10)
          .bindSheet($$this.isShow, this.myBuilder(), {
            height: this.sheetHeight,
            // 以下接口不建议与systemMaterial一起使用
            // borderWidth: 20,
            // borderColor: Color.Red,
            // backgroundColor: Color.Green,
            // shadow: { radius: 30, type: ShadowType.COLOR, color: Color.Yellow },
            systemMaterial: this.myMaterial // 从API版本26.0.0开始，新增systemMaterial属性
          })
      }
      .justifyContent(FlexAlign.Center)
      .width('100%')
      .height('100%')
    }
  }
}
```

### 示例11（半模态自定义按钮材质）

该示例通过closeButtonMaterial属性自定义半模态关闭按钮的材质效果，对比未设置（使用systemMaterial内置材质）、关闭材质、自定义材质三种状态。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-common-comp-sheetoptions-i.md)新增closeButtonMaterial属性。

未设置closeButtonMaterial时，关闭按钮使用systemMaterial带来的内置材质效果。



设置closeButtonMaterial为uiMaterial.Material.empty时，关闭按钮无材质效果。



设置closeButtonMaterial为自定义材质时，关闭按钮使用自定义材质效果。



```TypeScript
// xxx.ets
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct SheetMaterialExample {
  @State isShow: boolean = false;
  @State myMaterial: SystemUiMaterial | undefined = undefined;
  @State myCloseIconMaterial: SystemUiMaterial | undefined = undefined;

  @Builder
  myBuilder() {
    Column({ space: 10 }) {
      Text('Content')
        .fontSize(30)
    }
    .width('100%')
    .justifyContent(FlexAlign.Center)
  }

  build() {
    Stack() {
      Column() {
        Button('按钮带有默认材质')
          .onClick(() => {
            this.myMaterial = new uiMaterial.ImmersiveMaterial({
              style: uiMaterial.ImmersiveStyle.ULTRA_THICK,
            });
            this.myCloseIconMaterial = undefined;
            this.isShow = true;
          })
          .fontSize(20)
          .margin(10)
          .bindSheet($$this.isShow, this.myBuilder(), {
            height: SheetSize.MEDIUM,
            systemMaterial: this.myMaterial,
            closeButtonMaterial: this.myCloseIconMaterial,
          })
        Button('按钮关闭材质')
          .onClick(() => {
            this.myMaterial = new uiMaterial.ImmersiveMaterial({
              style: uiMaterial.ImmersiveStyle.ULTRA_THICK,
            });
            this.myCloseIconMaterial = uiMaterial.Material.empty;
            this.isShow = true;
          })
          .fontSize(20)
          .margin(10)
        Button('按钮设置自定义材质')
          .onClick(() => {
            this.myMaterial = new uiMaterial.ImmersiveMaterial({
              style: uiMaterial.ImmersiveStyle.ULTRA_THICK,
            });
            this.myCloseIconMaterial = new uiMaterial.ImmersiveMaterial({
              style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
            });
            this.isShow = true;
          })
          .fontSize(20)
          .margin(10)
      }
      .justifyContent(FlexAlign.Center)
      .width('100%')
      .height('100%')
    }
  }
}
```

### 示例12（半模态标题栏背景模糊）

该示例通过titleBarBackgroundBlur属性设置半模态标题栏背景渐变模糊效果。同时配合titleBarHoverMode设置为STACK堆叠模式，使标题栏悬浮于内容区上方时模糊效果可见。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-common-comp-sheetoptions-i.md)新增titleBarBackgroundBlur属性。



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SheetMaterialExample {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Column()
        .backgroundColor(Color.Pink)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Orange)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Pink)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Orange)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Pink)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Orange)
        .height(200)
        .width('100%')
    }
    .width('100%')
  }

  build() {
    Stack() {
      Column() {
        Button('拉起半模态')
          .onClick(() => {
            this.isShow = true;
          })
          .fontSize(20)
          .margin(10)
          .bindSheet($$this.isShow, this.myBuilder(), {
            height: SheetSize.MEDIUM,
            title: { title: '标题' },
            titleBarHoverMode: SheetTitleBarHoverMode.STACK,
            titleBarBackgroundBlur: {
              blurStyle: SheetTitleBarBackgroundBlur.GRADIENT,
            },
          })
      }
      .justifyContent(FlexAlign.Center)
      .width('100%')
      .height('100%')
    }
  }
}
```

### 示例13（半模态标题栏悬浮模式）

该示例通过titleBarHoverMode属性设置半模态标题栏为STACK堆叠模式，标题栏悬浮在内容区上方。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-common-comp-sheetoptions-i.md)新增titleBarHoverMode属性。



```TypeScript
// xxx.ets
@Entry
@Component
struct SheetMaterialExample {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Column()
        .backgroundColor(Color.Pink)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Orange)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Pink)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Orange)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Pink)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Orange)
        .height(200)
        .width('100%')
    }
    .width('100%')
  }

  build() {
    Stack() {
      Column() {
        Button('拉起半模态')
          .onClick(() => {
            this.isShow = true;
          })
          .fontSize(20)
          .margin(10)
          .bindSheet($$this.isShow, this.myBuilder(), {
            height: SheetSize.MEDIUM,
            title: { title: '标题' },
            titleBarHoverMode: SheetTitleBarHoverMode.STACK,
          })
      }
      .justifyContent(FlexAlign.Center)
      .width('100%')
      .height('100%')
    }
  }
}
```

### 示例14（半模态滚动条状态）

该示例通过scrollBarState属性设置半模态内容区滚动条的显示状态，点击按钮在[BarState](ts-appendix-enums.md#barstate)的Off、On、Auto和未设置之间切换。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-common-comp-sheetoptions-i.md)新增scrollBarState属性。

```TypeScript
// xxx.ets
@Entry
@Component
struct SheetMaterialExample {
  @State isShow: boolean = false;
  @State myScrollBarMode: BarState | undefined = BarState.Off;

  @Builder
  myBuilder() {
    Column() {
      Row() {
        Button('当前的ScrollBarMode：' + this.myScrollBarMode)
          .onClick(() => {
            if (this.myScrollBarMode == undefined) {
              this.myScrollBarMode = BarState.Off
            } else if (this.myScrollBarMode == BarState.Off) {
              this.myScrollBarMode = BarState.On
            } else if (this.myScrollBarMode == BarState.On) {
              this.myScrollBarMode = BarState.Auto
            } else if (this.myScrollBarMode == BarState.Auto) {
              this.myScrollBarMode = undefined
            }
          })
      }.width('100%').justifyContent(FlexAlign.Center).margin(25)

      Column() {
        Column()
          .backgroundColor(Color.Pink)
          .height(200)
          .width('100%')
        Column()
          .backgroundColor(Color.Orange)
          .height(200)
          .width('100%')
        Column()
          .backgroundColor(Color.Pink)
          .height(200)
          .width('100%')
        Column()
          .backgroundColor(Color.Orange)
          .height(200)
          .width('100%')
        Column()
          .backgroundColor(Color.Pink)
          .height(200)
          .width('100%')
        Column()
          .backgroundColor(Color.Orange)
          .height(200)
          .width('100%')
      }
    }
    .width('100%')
  }

  build() {
    Stack() {
      Column() {
        Button('拉起半模态')
          .onClick(() => {
            this.isShow = true;
          })
          .fontSize(20)
          .margin(10)
          .bindSheet($$this.isShow, this.myBuilder(), {
            height: SheetSize.MEDIUM,
            scrollBarState: this.myScrollBarMode,
          })
      }
      .justifyContent(FlexAlign.Center)
      .width('100%')
      .height('100%')
    }
  }
}
```

### 示例1（支持滚动手势）

该示例通过设置[enableScrollInteraction](#enablescrollinteraction11)属性，实现了使用手势滚动纵向列表，并在当前显示界面发生改变时回调索引。

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](./ts-container-list.md#示例1添加滚动事件)。



```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);

  build() {
    Column() {
      List({ space: 20, initialIndex: 0 }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .enableScrollInteraction(true)
      .listDirection(Axis.Vertical) // 排列方向
      .scrollBar(BarState.Off)
      .friction(0.6)
      .divider({
        strokeWidth: 2,
        color: 0xFFFFFF,
        startMargin: 20,
        endMargin: 20
      }) // 每行之间的分界线
      .edgeEffect(EdgeEffect.Spring) // 边缘效果设置为Spring
      .onScrollIndex((firstIndex: number, lastIndex: number, centerIndex: number) => {
        console.info('first' + firstIndex);
        console.info('last' + lastIndex);
        console.info('center' + centerIndex);
      })
      .onScrollVisibleContentChange((start: VisibleListContentInfo, end: VisibleListContentInfo) => {
        console.info(' start index: ' + start.index +
          ' start item group area: ' + start.itemGroupArea +
          ' start index in group: ' + start.itemIndexInGroup);
        console.info(' end index: ' + end.index +
          ' end item group area: ' + end.itemGroupArea +
          ' end index in group: ' + end.itemIndexInGroup);
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onDidScroll scrollState = ` + scrollState + `, scrollOffset = ` + scrollOffset);
      })
      .width('90%')
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

### 示例2（设置边缘渐隐）

该示例通过设置[fadingEdge](#fadingedge14)属性，实现了[List](ts-container-list.md)组件开启边缘渐隐效果并设置边缘渐隐长度。

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](./ts-container-list.md#示例1添加滚动事件)。



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]);
  scrollerForList: Scroller = new Scroller();

  build() {
    Column() {

      List({ space: 20, initialIndex: 0, scroller: this.scrollerForList }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .fadingEdge(true, { fadingEdgeLength: LengthMetrics.vp(80) })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

### 示例3（设置裁剪区域）

该示例通过设置[clipContent](arkts-arkui-common-comp-scrollablecommonmethod-c.md#clipcontent)属性，改变组件的内容层裁剪区域。



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
  @State clipContent: ContentClipMode | RectShape | undefined = undefined;

  build() {
    Column() {
      Scroll(this.scroller) {
        Column() {
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width(300)
              .height(80)
              .fontSize(20)
              .textAlign(TextAlign.Center)
              .backgroundColor(Color.Grey)
          }, (item: number) => item.toString())
        }
      }
      .backgroundColor(Color.Blue)
      .clipContent(this.clipContent)
      .scrollBar(BarState.Off)
      .friction(0.6)
      .width(300)
      .height('50%')
      .padding(10)
      .safeAreaPadding(LengthMetrics.vp(10))
      .initialOffset({ yOffset: 80 })
      .margin({ top: 20 })

      Button('clipContent SAFE_AREA')
        .onClick(() => {
          this.clipContent = ContentClipMode.SAFE_AREA;
        }).margin({ top: 30 })

      Button('clipContent BOUNDARY')
        .onClick(() => {
          this.clipContent = ContentClipMode.BOUNDARY;
        }).margin({ top: 35 })

      Button('clipContent CONTENT_ONLY')
        .onClick(() => {
          this.clipContent = ContentClipMode.CONTENT_ONLY;
        }).margin({ top: 40 })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### 示例4（设置滚动条边距）

从API version 20开始，该示例通过设置[scrollBarMargin](#scrollbarmargin20)属性，调整滚动组件的滚动条边距。

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](./ts-container-list.md#示例1添加滚动事件)。

```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ListExample {
  arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);
  @State scrollBarMargin: ScrollBarMargin = { start: LengthMetrics.vp(0), end: LengthMetrics.vp(0) };

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Column() {
        List({ space: 20, initialIndex: 0 }) {
          LazyForEach(this.arr, (item: number) => {
            ListItem() {
              Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center }) {
                Text('' + item)
                  .width('100%')
                  .height(80)
                  .fontSize(20)
                  .textAlign(TextAlign.Center)
                  .borderRadius(10)
                  .backgroundColor(Color.White)
                  .flexShrink(1)
              }
            }
          }, (item: number) => item.toString())
        }.width('90%')
        .friction(0.6)
        .scrollBar(BarState.On)
        .scrollBarMargin(this.scrollBarMargin)
      }.width('100%')

      Button('scrollBarMargin')
        .onClick(() => {
          this.scrollBarMargin = { start: LengthMetrics.vp(45), end: LengthMetrics.vp(70) };
        }).margin({ top: 5, left: 20 })

      Button('scrollBarMargin2')
        .onClick(() => {
          this.scrollBarMargin = { start: LengthMetrics.vp(15), end: LengthMetrics.vp(100) };
        }).margin({ top: 200, left: 20 })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State isShow: boolean = false

  build() {
    Stack({ alignContent: Alignment.Center }) {
      if (this.isShow) {
        Image($r('app.media.pic'))
          .autoResize(false)
          .clip(true)
          .width(300)
          .height(400)
          .offset({ y: 100 })
          .geometryTransition("picture", { hierarchyStrategy: TransitionHierarchyStrategy.ADAPTIVE })
          .transition(TransitionEffect.OPACITY)
      } else {
        // geometryTransition此处绑定的是容器，那么容器内的子组件需设为相对布局跟随父容器变化，
        // 套多层容器为了说明相对布局约束传递
        Column() {
          Column() {
            Image($r('app.media.icon'))
              .width('100%').height('100%')
          }.width('100%').height('100%')
        }
        .width(80)
        .height(80)
        // geometryTransition会同步圆角，但仅限于geometryTransition绑定处，此处绑定的是容器
        // 则对容器本身有圆角同步而不会操作容器内部子组件的borderRadius
        .borderRadius(20)
        .clip(true)
        .geometryTransition("picture", { hierarchyStrategy: TransitionHierarchyStrategy.ADAPTIVE })
        // transition保证组件离场不被立即析构，可设置其他转场效果
        .transition(TransitionEffect.OPACITY)
      }
    }
    .onClick(() => {
      this.getUIContext()?.animateTo({ duration: 1000 }, () => {
        this.isShow = !this.isShow;
      })
    })
  }
}
```

### 示例1（弹出不同类型的气泡）

该示例通过配置[PopupOptions](#popupoptions类型说明)或[CustomPopupOptions](#custompopupoptions8类型说明)中的keyboardAvoidMode属性，设置气泡是否避让软键盘。

从API version 15开始，分别在PopupOptions和CustomPopupOptions中新增了keyboardAvoidMode属性。



```TypeScript
// xxx.ets
@Entry
@Component
struct PopupExample {
  @State handlePopup: boolean = false;
  @State customPopup: boolean = false;

  // Popup构造器定义弹框内容
  @Builder popupBuilder() {
    Row({ space: 2 }) {
      // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.icon')).width(24).height(24).margin({ left: -5 })
      Text('Custom Popup').fontSize(10)
    }.width(100).height(50).padding(5)
  }

  build() {
    Flex({ direction: FlexDirection.Column }) {
      // PopupOptions类型设置弹框内容
      Button('PopupOptions')
        .onClick(() => {
          this.handlePopup = !this.handlePopup;
        })
        .bindPopup(this.handlePopup, {
          message: 'This is a popup with PopupOptions',
          placement: Placement.Top,
          showInSubWindow: false,
          keyboardAvoidMode: KeyboardAvoidMode.DEFAULT, // 设置气泡避让软键盘
          primaryButton: {
            value: 'confirm',
            action: () => {
              this.handlePopup = !this.handlePopup;
              console.info('confirm Button click');
            }
          },
          // 第二个按钮
          secondaryButton: {
            value: 'cancel',
            action: () => {
              this.handlePopup = !this.handlePopup;
              console.info('cancel Button click');
            }
          },
          onStateChange: (e) => {
            console.info(JSON.stringify(e.isVisible));
            if (!e.isVisible) {
              this.handlePopup = false;
            }
          }
        })
        .position({ x: 100, y: 150 })


      // CustomPopupOptions类型设置弹框内容
      Button('CustomPopupOptions')
        .onClick(() => {
          this.customPopup = !this.customPopup;
        })
        .bindPopup(this.customPopup, {
          builder: this.popupBuilder,
          placement: Placement.Top,
          mask: { color: '#33000000' },
          popupColor: Color.Yellow,
          enableArrow: true,
          keyboardAvoidMode: KeyboardAvoidMode.DEFAULT, // 设置气泡避让软键盘
          showInSubWindow: false,
          onStateChange: (e) => {
            if (!e.isVisible) {
              this.customPopup = false;
            }
          }
        })
        .position({ x: 80, y: 300 })
    }.width('100%').padding({ top: 5 })
  }
}
```

### 示例2（设置气泡的文本样式）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的messageOptions属性，实现了弹出自定义文本样式的气泡。



```TypeScript
// xxx.ets

@Entry
@Component
struct PopupExample {
  @State handlePopup: boolean = false;

  build() {
    Column({ space: 100 }) {
      Button('PopupOptions').margin(100)
        .onClick(() => {
          this.handlePopup = !this.handlePopup;
        })
        .bindPopup(this.handlePopup, {
          // PopupOptions类型气泡的内容
          message: 'This is a popup with PopupOptions',
          messageOptions: {
            // 气泡的文本样式
            textColor: Color.Red,
            font: {
              size: '14vp',
              style: FontStyle.Italic,
              weight: FontWeight.Bolder
            }
          },
          placement: Placement.Bottom,
          enableArrow: false, // 气泡弹出时不显示箭头
          targetSpace: '15vp',
          onStateChange: (e) => {
            console.info(JSON.stringify(e.isVisible));
            if (!e.isVisible) {
              this.handlePopup = false;
            }
          }
        })
    }.margin(20)
  }
}
```

### 示例3（设置气泡的样式）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的arrowHeight、arrowWidth、radius、shadow和popupColor属性，实现了气泡箭头以及气泡本身的样式。



```TypeScript
// xxx.ets

@Entry
@Component
struct PopupExample {
  @State customPopup: boolean = false;
  @State handlePopup: boolean = false;

  build() {
    Column({ space: 100 }) {
      Button('popup')
        .margin({ top: 50 })
        .onClick(() => {
          this.customPopup = !this.customPopup;
        })
        .bindPopup(this.customPopup!!, {
          message: 'this is a popup',
          arrowHeight: 20, // 设置气泡箭头高度
          arrowWidth: 20, // 设置气泡箭头宽度
          radius: 20, // 设置气泡的圆角
          shadow: ShadowStyle.OUTER_DEFAULT_XS, // 设置气泡的阴影
        })

      Button('PopupOptions')
        .onClick(() => {
          this.handlePopup = !this.handlePopup;
        })
        .bindPopup(this.handlePopup!!, {
          width: 300,
          message: 'This is a popup with PopupOptions',
          arrowPointPosition: ArrowPointPosition.START, // 设置箭头的位置
          backgroundBlurStyle: BlurStyle.NONE, // 关闭气泡的模糊背景
          popupColor: Color.Red, // 设置气泡的背景色
          autoCancel: true,
        })
    }
    .width('100%')
  }
}
```

### 示例4（设置气泡的动效）

该示例通过配置[PopupOptions](#popupoptions类型说明)或[CustomPopupOptions](#custompopupoptions8类型说明)中的transition属性，实现了气泡显示以及退出的动效。



```TypeScript
// xxx.ets
@Entry
@Component
struct PopupExample {
  @State handlePopup: boolean = false;
  @State customPopup: boolean = false;

  // Popup构造器定义弹框内容
  @Builder
  popupBuilder() {
    Row() {
      Text('Custom Popup with transitionEffect').fontSize(10)
    }.height(50).padding(5)
  }

  build() {
    Flex({ direction: FlexDirection.Column }) {
      // PopupOptions类型设置弹框内容
      Button('PopupOptions')
        .onClick(() => {
          this.handlePopup = !this.handlePopup;
        })
        .bindPopup(this.handlePopup, {
          message: 'This is a popup with transitionEffect',
          placement: Placement.Top,
          showInSubWindow: false,
          onStateChange: (e) => {
            console.info(JSON.stringify(e.isVisible));
            if (!e.isVisible) {
              this.handlePopup = false;
            }
          },
          // 设置气泡显示动效为透明度动效与平移动效的组合效果，无退出动效
          transition: TransitionEffect.asymmetric(
            TransitionEffect.OPACITY.animation({ duration: 1000, curve: Curve.Ease }).combine(
              TransitionEffect.translate({ x: 50, y: 50 })),
            TransitionEffect.IDENTITY)
        })
        .position({ x: 100, y: 150 })

      // CustomPopupOptions类型设置弹框内容
      Button('CustomPopupOptions')
        .onClick(() => {
          this.customPopup = !this.customPopup;
        })
        .bindPopup(this.customPopup, {
          builder: this.popupBuilder,
          placement: Placement.Top,
          showInSubWindow: false,
          onStateChange: (e) => {
            if (!e.isVisible) {
              this.customPopup = false;
            }
          },
          // 设置气泡显示动效与退出动效为缩放动效
          transition: TransitionEffect.scale({ x: 1, y: 0 }).animation({ duration: 500, curve: Curve.Ease })
        })
        .position({ x: 80, y: 300 })
    }.width('100%').padding({ top: 5 })
  }
}
```

### 示例5（为气泡添加事件）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的onWillDismiss属性，实现了当气泡退出时，拦截退出事件并执行回调函数。



```TypeScript
// xxx.ets

@Entry
@Component
struct PopupExample {
  @State handlePopup: boolean = false;
  build() {
    Column() {
      Button('PopupOptions')
        .onClick(() => {
          this.handlePopup = true;
        })
        .bindPopup(this.handlePopup, {
          message: 'This is a popup with PopupOptions',
          messageOptions: {
            textColor: Color.Red,
            font: {
              size: '14vp',
              style: FontStyle.Italic,
              weight: FontWeight.Bolder
            }
          },
          placement: Placement.Bottom,
          enableArrow: false,
          targetSpace: '15vp',
          onStateChange: (e) => {
            if (!e.isVisible) {
              this.handlePopup = false;
            }
          },
          /**
           * 气泡即将关闭前拦截回调
           * dismissPopupAction：气泡关闭行为对象，包含关闭原因与关闭方法
           */
          onWillDismiss: (
            (dismissPopupAction: DismissPopupAction) => {
              console.info('dismissReason:' + JSON.stringify(dismissPopupAction.reason));
              if (dismissPopupAction.reason === DismissReason.PRESS_BACK) {
                dismissPopupAction.dismiss();
              }
            }
          )
        })
    }.margin(20)
  }
}
```

### 示例6（为气泡拦截退出事件）

该示例将[PopupOptions](#popupoptions类型说明)的onWillDismiss属性设为false，使气泡不响应退出事件。同时，配置[PopupOptions](#popupoptions类型说明)的followTransformOfTarget属性，设置气泡是否跟随宿主组件变换。



```TypeScript
// xxx.ets

@Entry
@Component
struct PopupExample {
  @State handlePopup: boolean = false;
  private timer: number = -1;

  build() {
    Column() {
      Button('PopupOptions')
        .onClick(() => {
          this.handlePopup = true;
        })
        .bindPopup(this.handlePopup, {
          message: 'This is a popup with PopupOptions',
          messageOptions: {
            textColor: Color.Red,
            font: {
              size: '14vp',
              style: FontStyle.Italic,
              weight: FontWeight.Bolder
            }
          },
          placement: Placement.Bottom,
          enableArrow: false,
          targetSpace: '15vp',
          // 气泡跟随按钮的平移、缩放等变换同步变动
          followTransformOfTarget: true,
          onStateChange: (e) => {
            // 设置气泡显示6秒后自动关闭
            if (e.isVisible) {
              this.timer = setTimeout(() => {
                this.handlePopup = false;
              }, 6000);
            } else {
              this.handlePopup = false;
              if (this.timer !== -1) {
                clearTimeout(this.timer);
                this.timer = -1;
              }
            }
          },
          // 不响应点击、侧滑（左滑/右滑）、三键back、路由跳转或键盘ESC退出事件，仅当设置“气泡显示状态”参数值为false时才退出
          onWillDismiss: false
        })
    }.margin(20)
  }
}
```

### 示例7（为气泡内外描边设置线性渐变）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的outlineWidth、borderWidth、outlineLinearGradient、borderLinearGradient属性，为气泡设置内外描边线性渐变的颜色和方向。

从API version 20开始，在PopupOptions中新增了outlineWidth、borderWidth、outlineLinearGradient、borderLinearGradient属性。



```TypeScript
// xxx.ets
@Entry
@Component
struct PopupExample {
  @State handlePopup: boolean = false

  build() {
    Flex({ direction: FlexDirection.Column }) {
      Button('PopupOptions')
        .onClick(() => {
          this.handlePopup = !this.handlePopup
        })
        /**
         * 为按钮绑定气泡
         * 第一个参数：气泡显隐控制变量
         * message：气泡内部展示文本
         * placement.Top：气泡从按钮上方弹出
         * outlineWidth：外描边线宽度1vp
         * outlineLinearGradient：外描边垂直从上到下黄到绿线性渐变
         * borderWidth：弹窗内部边框宽度1vp
         * borderLinearGradient：内边框垂直从下到上红到蓝线性渐变
         */
        .bindPopup(this.handlePopup!!, {
          message: 'This is a popup with PopupOptions',
          placement: Placement.Top,
          outlineWidth: 1,
          outlineLinearGradient: {
            direction: GradientDirection.Top,
            colors: [[Color.Yellow, 0.0], [Color.Green, 1.0]]
          },
          borderWidth: 1,
          borderLinearGradient: {
            direction: GradientDirection.Bottom,
            colors: [[Color.Red, 0.0], [Color.Blue, 1.0]]
          }
        })
        .position({ x: 100, y: 150 }) 
    }.width('100%').padding({ top: 5 })
  }
}
```

### 示例8（设置气泡避让绑定的组件模式）

该示例通过配置[PopupOptions](#popupoptions类型说明)的avoidTarget属性，实现气泡对其绑定组件的避让。

从API version 20开始，在PopupOptions中新增了avoidTarget属性。



```TypeScript
// xxx.ets
@Entry
@Component
struct PopupExample {
  @State handlePopup: boolean = false;

  build() {
    Flex({ direction: FlexDirection.Column }) {
      Button('PopupOptions')
        .onClick(() => {
          this.handlePopup = !this.handlePopup
        })
        .bindPopup(this.handlePopup!!, {
          message: 'popup message '.repeat(200),
          placement: Placement.Top,
          // 气泡在剩余显示空间不足的情况下，在最大空间处压缩显示
          avoidTarget: AvoidanceMode.AVOID_AROUND_TARGET,
        })
        .position({ x: 100, y: 150 }) 
    }.width('100%').padding({ top: 5 })
  }
}
```

### 示例9（设置Popup的沉浸光感视觉效果）

该示例通过[PopupOptions](#popupoptions类型说明)中的systemMaterial属性设置组件的系统材质，实现了Popup的沉浸光感视效。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在PopupOptions中新增了systemMaterial属性。

未设置系统材质时：



设置系统材质后：



```TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct PopupExample {
  @State handlePopup: boolean = false;

  build() {
    Flex({ direction: FlexDirection.Column }) {
      Button('PopupOptions')
        .onClick(() => {
          this.handlePopup = !this.handlePopup
        })
        /**
         * 绑定气泡至按钮
         * 第一个参数：气泡显示控制布尔值
         * message：气泡内展示文本
         * placement.Top：气泡弹出位置在按钮上方
         * systemMaterial：为气泡配置沉浸式磨砂材质
         * ImmersiveStyle.THIN：薄款磨砂，中等通透度
         */
        .bindPopup(this.handlePopup!!, {
          message: 'This is a popup with PopupOptions',
          placement: Placement.Top,
          // 控制是否设置系统材质接口
          systemMaterial: new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.THIN
          })
        })
        .position({ x: 100, y: 300 })
    }.width('100%')
    // 请开发者替换为实际资源文件
    .backgroundImage($r('app.media.img'))
    .backgroundImageSize({ width: '100%', height: '100%' })
  }
}
```

### 示例10（自定义气泡背景效果参数）

该示例通过配置[PopupOptions](#popupoptions类型说明)的backgroundBlurStyleOptions和backgroundEffect属性，实现自定义气泡背景效果。

从API版本26.0.0开始，在PopupOptions中新增了backgroundBlurStyleOptions和backgroundEffect属性。



```TypeScript
// xxx.ets
@Entry
@Component
struct PopupExample {
  @State handlePopup: boolean = false;

  build() {
    Flex({ direction: FlexDirection.Column }) {
      Button('Popup自定义背景效果1')
        .onClick(() => {
          this.handlePopup = !this.handlePopup
        })
        /**
         * 绑定气泡，使用系统标准化磨砂模糊样式
         * message：气泡长文本内容，重复拼接加长文本用于测试换行与模糊透出效果
         * backgroundBlurStyleOptions：系统沉浸式模糊配置项
         * colorMode.LIGHT：浅色主题调色模式
         * adaptiveColor.AVERAGE：取底层背景平均色作为磨砂底色
         * scale：磨砂通透缩放系数0.5
         * blurOptions.grayscale：灰度滤镜区间[最小值,最大值]
         */
        .bindPopup(this.handlePopup!!, {
          message: 'popup message '.repeat(20),
          backgroundBlurStyleOptions: {
            colorMode: ThemeColorMode.LIGHT,
            adaptiveColor: AdaptiveColor.AVERAGE,
            scale: 0.5,
            blurOptions: { grayscale: [20, 20] },
          }
        })
        .position({ x: 100, y: 150 }) 

      Button('Popup自定义背景效果2')
        .onClick(() => {
          this.handlePopup = !this.handlePopup
        })
        /**
         * 绑定气泡，使用完全自定义混合背景特效
         * radius：背景模糊半径60，模糊程度更高
         * saturation：饱和度0，画面去色黑白化
         * brightness：亮度1，保持原始亮度不变
         * color：叠加粉色底色
         * blurOptions.grayscale：灰度滤镜参数
         */
        .bindPopup(this.handlePopup!!, {
          message: 'popup message '.repeat(20),
          backgroundEffect: {
            radius: 60,
            saturation: 0,
            brightness: 1,
            color: Color.Pink,
            blurOptions: { grayscale: [20, 20] }
          }
        })
        .position({ x: 100, y: 400 }) 
    }.width('100%')
    // 请开发者替换为实际资源文件
    .backgroundImage($r('app.media.img'))
    .backgroundImageSize({ width: '100%', height: '100%' })
  }
}
```

### 示例11（设置气泡的显示层级模式）

该示例通过配置[PopupOptions](#popupoptions类型说明)的levelMode属性，实现气泡在页面内嵌入显示。点击按钮后页面级的气泡不会显示在下一个路由页面中。

从API版本26.0.0开始，在PopupOptions中新增了levelMode属性。

```TypeScript
import { LevelMode } from '@kit.ArkUI';

@Entry
@Component
struct PopupExample {
  @State handlePopup: boolean = false;

  build() {
    Column() {
      Button('PopupOptions EMBEDDED')
        .id('targetButton')
        .onClick(() => {
          // 切换气泡显示/隐藏状态
          this.handlePopup = !this.handlePopup;
          // 延迟500ms跳转路由，确保气泡动画播放完成
          setTimeout(() => {
            // pages/PageTwo需要开发者替换为实际路由名称
            this.getUIContext().getRouter().pushUrl({ url: 'pages/PageTwo'}).catch(() => {
              console.error("route to PageTwo error!")
            })
          }, 500)
        })
        /**
         * 绑定气泡到当前按钮
         * 第一个参数：气泡显示控制布尔值
         * message：气泡内展示文本
         * levelMode: EMBEDDED 嵌入式模式，气泡隶属于当前页面，页面跳转气泡同步销毁
         */
        .bindPopup(this.handlePopup!!, {
          message: 'This is an embedded popup',
          levelMode: LevelMode.EMBEDDED,
        })
        .position({ x: 60, y: 300 })
    }.width('100%').padding({ top: 5 })
  }
}
```

PageTwo页面：

```TypeScript
@Entry
@Component
struct PageTwo {
  build() {
    Column() {
      Text("This is next page")
    }
    .position({ x: 120, y: 300 })
  }
}
```

### 示例1（获取轴事件相关参数）

该示例中，对按钮设置轴事件，通过滚动鼠标滚轮可获取轴事件的相关参数。从API version 21开始，该示例通过[BaseEvent](./ts-universal-events-click.md#baseevent8)的属性和[getPinchAxisScaleValue](arkts-arkui-common-comp-axisevent-i.md#getpinchaxisscalevalue)获取双指缩放比例；从API version 22开始，该示例通过[hasAxis](arkts-arkui-common-comp-axisevent-i.md#hasaxis)判断轴事件是否包含指定的轴类型。

鼠标滚轮滚动时：



```TypeScript
// xxx.ets
@Entry
@Component
struct AxisEventExample {
  @State text: string = '';

  build() {
    Column() {
      Row({ space: 20 }) {
        Button('AxisEvent').width(100).height(40)
          .onAxisEvent((event?: AxisEvent) => {
            if (event) {
              this.text =
                'AxisEvent:' + '\n  action:' + event.action + '\n  displayX:' + event.displayX + '\n  displayY:' +
                event.displayY + '\n  windowX:' + event.windowX + '\n  windowY:' + event.windowY + '\n  x:' + event.x +
                  '\n  y:' + event.y + '\n VerticalAxisValue:' + event.getVerticalAxisValue() +
                  '\n HorizontalAxisValue:' + event.getHorizontalAxisValue() + '\n axisPinch:' + event.axisPinch +
                  '\n PinchAxisScaleValue:' + event.getPinchAxisScaleValue() +
                  '\n HasAxis:' + event.hasAxis(AxisType.VERTICAL_AXIS);
            }
          })
      }.margin(20)

      Text(this.text).margin(15)
    }.width('100%')
  }
}
```

### 示例2（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取鼠标光标位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct GetCurrentLocalPositionExample {
  @State positionText: string = '';
  @State textOffsetY: number = 0;

  build() {
    Column() {
      Button('获取鼠标光标位置相对于当前组件实时位置左上角的坐标').translate({ y: this.textOffsetY })
        .onAxisEvent((event?: AxisEvent) => {
          if (event) {
            // 先移动按钮位置，延迟后获取鼠标光标相对于组件实时位置左上角的坐标。
            this.textOffsetY = -200;
            setTimeout(() => {
              let localPos: Coordinate2D | undefined = event?.getCurrentLocalPosition?.();
              this.positionText = `相对于当前组件实时位置左上角的坐标：\n  x: ${localPos?.x}\n  y: ${localPos?.y}`;
            }, 2000);
          }
        })

      Text(this.positionText)
    }.width('100%')
  }
}
```

### 示例1（设置组件宽高比）

通过aspectRatio设置不同的宽高比。

图1 竖屏显示

图2 横屏显示

```TypeScript
// xxx.ets
@Entry
@Component
struct AspectRatioExample {
  private children: string[] = ['1', '2', '3', '4', '5', '6']

  build() {
    Column({ space: 20 }) {
      Text('using container: row').fontSize(14).fontColor(0xCCCCCC).width('100%')
      Row({ space: 10 }) {
        ForEach(this.children, (item:string) => {
          // 组件宽度 = 组件高度*1.5 = 90
          Text(item)
            .backgroundColor(0xbbb2cb)
            .fontSize(20)
            .aspectRatio(1.5)
            .height(60)
          // 组件高度 = 组件宽度/1.5 = 60/1.5 = 40
          Text(item)
            .backgroundColor(0xbbb2cb)
            .fontSize(20)
            .aspectRatio(1.5)
            .width(60)
        }, (item:string) => item)
      }
      .size({ width: "100%", height: 100 })
      .backgroundColor(0xd2cab3)
      .clip(true)

      // grid子元素width/height=3/2
      Text('using container: grid').fontSize(14).fontColor(0xCCCCCC).width('100%')
      Grid() {
        ForEach(this.children, (item:string) => {
          GridItem() {
            Text(item)
              .backgroundColor(0xbbb2cb)
              .fontSize(40)
              .width('100%')
              .aspectRatio(1.5)
          }
        }, (item:string) => item)
      }
      .columnsTemplate('1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .size({ width: "100%", height: 165 })
      .backgroundColor(0xd2cab3)
    }.padding(10)
  }
}
```

### 示例2（设置组件显示优先级）

使用displayPriority为子组件设置显示优先级。

```TypeScript
class ContainerInfo {
  label: string = '';
  size: string = '';
}

class ChildInfo {
  text: string = '';
  priority: number = 0;
}

@Entry
@Component
struct DisplayPriorityExample {
  // 显示容器大小
  private container: ContainerInfo[] = [
    { label: 'Big container', size: '90%' },
    { label: 'Middle container', size: '50%' },
    { label: 'Small container', size: '30%' }
  ]
  private children: ChildInfo[] = [
    { text: '1\n(priority:2)', priority: 2 },
    { text: '2\n(priority:1)', priority: 1 },
    { text: '3\n(priority:3)', priority: 3 },
    { text: '4\n(priority:1)', priority: 1 },
    { text: '5\n(priority:2)', priority: 2 }
  ]
  @State currentIndex: number = 0;

  build() {
    Column({ space: 10 }) {
      // 切换父级容器大小
      Button(this.container[this.currentIndex].label).backgroundColor(0x317aff)
        .onClick(() => {
          this.currentIndex = (this.currentIndex + 1) % this.container.length;
        })
      // 通过变量设置Flex父容器宽度
      Flex({ justifyContent: FlexAlign.SpaceBetween }) {
        ForEach(this.children, (item:ChildInfo) => {
          // 使用displayPriority给子组件绑定显示优先级
          Text(item.text)
            .width(120)
            .height(60)
            .fontSize(24)
            .textAlign(TextAlign.Center)
            .backgroundColor(0xbbb2cb)
            .displayPriority(item.priority)
        }, (item:ChildInfo) => item.text)
      }
      .width(this.container[this.currentIndex].size)
      .backgroundColor(0xd2cab3)
    }.width("100%").margin({ top: 50 })
  }
}
```

### 示例1（触发onKeyEvent回调）

该示例为按钮设置按键事件。按钮获焦时，按下按键可触发onKeyEvent回调。按键事件触发的流程和具体时机参考[按键事件数据流](../../../ui/arkts-interaction-development-guide-keyboard.md#按键事件数据流)。



```TypeScript
// xxx.ets
@Entry
@Component
struct KeyEventExample {
  @State text: string = ''
  @State eventType: string = ''

  build() {
    Column() {
      Button('KeyEvent')
        .defaultFocus(true)
        .onKeyEvent((event?: KeyEvent) => {
          if (event) {
            if (event.type === KeyType.Down) {
              this.eventType = 'Down';
            }
            if (event.type === KeyType.Up) {
              this.eventType = 'Up';
            }
            this.text = 'KeyType:' + this.eventType + '\nkeyCode:' + event.keyCode + '\nkeyText:' + event.keyText +
              '\nintentionCode:' + event.intentionCode;
          }
        })
      Text(this.text).padding(15)
    }.height(300).width('100%').padding(35)
  }
}
```

### 示例2（获取Unicode码值）

该示例通过按键事件获取所按按键的Unicode码值。



```TypeScript
// xxx.ets
@Entry
@Component
struct KeyEventExample {
  @State text: string = ''
  @State eventType: string = ''
  @State keyType: string = ''

  build() {
    Column({ space: 10 }) {
      Button('KeyEvent')
        .onKeyEvent((event?: KeyEvent) => {
          if (event) {
            if (event.type === KeyType.Down) {
              this.eventType = 'Down';
            }
            if (event.type === KeyType.Up) {
              this.eventType = 'Up';
            }
            if (event.unicode === 97) {
              this.keyType = 'a';
            } else if (event.unicode === 65) {
              this.keyType = 'A';
            } else {
              this.keyType = ' ';
            }
            this.text =
              'KeyType:' + this.eventType + '\nUnicode:' + event.unicode + '\nkeyCode:' + event.keyCode + '\nkeyType:' +
              this.keyType;
          }
        })
      Text(this.text).padding(15)
    }.height(300).width('100%').padding(35)
  }
}
```

### 示例3（触发onKeyPreIme回调）

该示例使用onKeyPreIme屏蔽输入框中的方向左键。

```TypeScript
import { KeyCode } from '@kit.InputKit';

@Entry
@Component
struct PreImeEventExample {

  build() {
    Column() {
      Search({
        placeholder: 'Search...'
      })
        .width('80%')
        .height('40vp')
        .border({ radius: '20vp' })
        .onKeyPreIme((event: KeyEvent) => {
          // 使用方向左键不生效
          if (event.keyCode === KeyCode.KEYCODE_DPAD_LEFT) {
            return true;
          }
          return false;
        })
    }
  }
}
```

### 示例4（使用stopPropagation阻止冒泡）

该示例使用stopPropagation阻止事件冒泡。即，通过在Button的onKeyEvent回调中加入event.stopPropagation()方法，达到“仅Button响应键盘事件，Column不响应”的效果。

> 说明：
> 
> onKeyEvent事件默认是冒泡的。
> 
> 事件冒泡：在一个树形结构中，当子节点处理完一个事件后，再将该事件交给它的父节点处理。
> 
> 可以在[onKeyEvent15+](#onkeyevent15)中，通过返回true消费按键事件阻止冒泡，效果等同于stopPropagation。

```TypeScript
@Entry
@Component
struct KeyEventExample {
  @State buttonText: string = '';
  @State buttonType: string = '';
  @State columnText: string = '';
  @State columnType: string = '';

  build() {
    Column() {
      Button('onKeyEvent')
        .defaultFocus(true)
        .width(112).height(56)
        .onKeyEvent((event?: KeyEvent) => {
          // 通过stopPropagation阻止事件冒泡
          if (event) {
            event.stopPropagation();
            if (event.type === KeyType.Down) {
              this.buttonType = 'Down';
            }
            if (event.type === KeyType.Up) {
              this.buttonType = 'Up';
            }
            this.buttonText = 'Button: \n' +
              'KeyType:' + this.buttonType + '\n' +
              'KeyCode:' + event.keyCode + '\n' +
              'KeyText:' + event.keyText;
          }
        })

      Divider()
      Text(this.buttonText).fontColor(Color.Green)

      Divider()
      Text(this.columnText).fontColor(Color.Red)
    }.width('100%').height('100%').justifyContent(FlexAlign.Center)
    .onKeyEvent((event?: KeyEvent) => { // 给父组件Column设置onKeyEvent事件
      if (event) {
        if (event.type === KeyType.Down) {
          this.columnType = 'Down';
        }
        if (event.type === KeyType.Up) {
          this.columnType = 'Up';
        }
        this.columnText = 'Column: \n' +
          'KeyType:' + this.columnType + '\n' +
          'KeyCode:' + event.keyCode + '\n' +
          'KeyText:' + event.keyText;
      }
    })
  }
}
```

### 示例1（设置onAccessibilityActionIntercept拦截点击事件）

该示例演示在无障碍模式下，通过onAccessibilityActionIntercept事件在Toggle组件点击事件触发前进行拦截，并弹出确认对话框由用户确认是否放行该点击事件。

```TypeScript
// xxx.ets
@Entry
@Component
struct OnAccessibilityActionInterceptExample {
  @State private isOn: boolean = false;

  build() {
    NavDestination() {
      Column() {
        Text('onAccessibilityActionIntercept')
        Row() {
          Text('Label message')
          Blank()
          Toggle({ type: ToggleType.Switch, isOn: $$this.isOn })
            .onAccessibilityActionIntercept((action: AccessibilityAction) => {
              // 无障碍点击操作触发时，弹出确认对话框由用户决定是否放行
              if (action === AccessibilityAction.ACCESSIBILITY_CLICK) {
                this.getUIContext().showAlertDialog({
                  title: '标题',
                  message: '内容信息',
                  primaryButton: {
                    value: '确认',
                    action: () => {
                      this.isOn = !this.isOn;
                    }
                  },
                  secondaryButton: {
                    value: '取消',
                    action: () => {
                    }
                  }
                });
                // 拦截本次点击，阻止组件默认点击行为
                return AccessibilityActionInterceptResult.ACTION_INTERCEPT;
              } else {
                // 其他无障碍操作不拦截，直接放行
                return AccessibilityActionInterceptResult.ACTION_CONTINUE;
              }
            })
        }.width('100%')
      }
      .padding(24)
      .width('100%')
    }
  }
}
```

### 示例2（设置onAccessibilityFocus回调函数）

从API version 18开始，当获焦、失焦状态发生变化时，触发该回调函数。本示例展示了[onAccessibilityFocus](arkts-arkui-common-comp-commonmethod-c.md#onaccessibilityfocus)的基本用法，聚焦到"onAccessibilityFocus takes effect"时，会打印"[testingTag] isFocus current is true"，当聚焦到"onAccessibilityFocus takes effect"以外的位置时，会打印"[testingTag] isFocus current is false"。

```TypeScript
// xxx.ets
@Entry
@Component
struct OnAccessibilityFocusExample {

  build() {
    NavDestination() {
      Column() {
        Text("onAccessibilityFocus doesn't take effect")
        Text('onAccessibilityFocus takes effect')
          .onAccessibilityFocus((isFocus: boolean) => {
            console.info(`[testingTag] isFocus current is ${isFocus}`);
          })
      }
      .padding(24)
      .width('100%')
    }
  }
}
```

该示例通过onTouchIntercept修改组件的HitTestMode属性。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  isPolygon(event: TouchEvent) {
    return true;
  }

  build() {
    Row() {
      Column() {
        Text('hello world')
          .backgroundColor(Color.Blue)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            console.info('Text click');
          })
      }
      .width(400)
      .height(300)
      .backgroundColor(Color.Pink)
      .onClick(() => {
        console.info('Column click');
      })
      // 调用onTouchIntercept修改该组件的HitTestMode属性
      .onTouchIntercept((event: TouchEvent) => {
        console.info('OnTouchIntercept + ' + JSON.stringify(event));
        // 使用touches时需要先校验是否为空
        if (event && event.touches) {
          let touches = event.touches;
          for (let i = 0; touches[i] != null; i++) {
            console.info('onTouchIntercept touches:', JSON.stringify(touches[i]));
          }
        }
        // 当满足自定义拦截条件时，返回HitTestMode.None使该组件不参与触摸测试
        if (this.isPolygon(event)) {
          return HitTestMode.None;
        }
        return HitTestMode.Default;
      })
    }
    .width('100%')
  }
}
```

### 示例1（基本样式用法）

设置边框的宽度、颜色、圆角半径以及点、线样式。



```TypeScript
// xxx.ets
@Entry
@Component
struct BorderExample {
  build() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceAround, alignItems: ItemAlign.Center }) {
        // 虚线
        Text('dashed')
          .borderStyle(BorderStyle.Dashed)
          .borderWidth(5)
          .borderColor(0xAFEEEE)
          .borderRadius(10)
          .width(120)
          .height(120)
          .textAlign(TextAlign.Center)
          .fontSize(16)
        // 点线
        Text('dotted')
          .border({
            width: 5,
            color: 0x317AF7,
            radius: 10,
            style: BorderStyle.Dotted
          })
          .width(120)
          .height(120)
          .textAlign(TextAlign.Center)
          .fontSize(16)
      }.width('100%').height(150)

      Text('.border')
        .fontSize(50)
        .width(300)
        .height(300)
        // 使用border属性分别设置左、右、上、下四边的宽度、颜色、圆角和样式
        .border({
          width: {
            left: 3,
            right: 6,
            top: 10,
            bottom: 15
          },
          color: {
            left: '#e3bbbb',
            right: Color.Blue,
            top: Color.Red,
            bottom: Color.Green
          },
          radius: {
            topLeft: 10,
            topRight: 20,
            bottomLeft: 40,
            bottomRight: 80
          },
          style: {
            left: BorderStyle.Dotted,
            right: BorderStyle.Dotted,
            top: BorderStyle.Solid,
            bottom: BorderStyle.Dashed
          }
        })
        .textAlign(TextAlign.Center)
    }
  }
}
```

### 示例2（边框宽度、圆角半径和颜色类型）

border属性的width、radius、color属性值分别使用LocalizedEdgeWidths类型、LocalizedBorderRadiuses类型和LocalizedEdgeColors类型。

从左至右（LTR）显示语言示例图



从右至左（RTL）显示语言示例图



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct BorderExample {
  build() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceAround, alignItems: ItemAlign.Center }) {
        // 虚线
        Text('dashed')
          .borderStyle(BorderStyle.Dashed)
          .borderWidth(5)
          .borderColor(0xAFEEEE)
          .borderRadius(10)
          .width(120)
          .height(120)
          .textAlign(TextAlign.Center)
          .fontSize(16)
        // 点线
        Text('dotted')
          .border({
            width: 5,
            color: 0x317AF7,
            radius: 10,
            style: BorderStyle.Dotted
          })
          .width(120)
          .height(120)
          .textAlign(TextAlign.Center)
          .fontSize(16)
      }.width('100%').height(150)

      Text('.border')
        .fontSize(50)
        .width(300)
        .height(300)
        // 使用LocalizedEdgeWidths和LocalizedBorderRadiuses类型，start/end方向适配RTL/LTR布局
        .border({
          width: {
            start: LengthMetrics.vp(3),
            end: LengthMetrics.vp(6),
            top: LengthMetrics.vp(10),
            bottom: LengthMetrics.vp(15)
          },
          color: {
            start: '#e3bbbb',
            end: Color.Blue,
            top: Color.Red,
            bottom: Color.Green
          },
          radius: {
            topStart: LengthMetrics.vp(10),
            topEnd: LengthMetrics.vp(20),
            bottomStart: LengthMetrics.vp(40),
            bottomEnd: LengthMetrics.vp(80)
          },
          style: {
            left: BorderStyle.Dotted,
            right: BorderStyle.Dotted,
            top: BorderStyle.Solid,
            bottom: BorderStyle.Dashed
          }
        })
        .textAlign(TextAlign.Center)
    }
  }
}
```

### 示例3（设置离屏圆角）

从API version 22开始，该示例支持设置组件绘制圆角的模式。

快速绘制模式（RenderStrategy.FAST）通过GPU硬件加速进行实时绘制，适用于普通圆角场景；离屏绘制模式（RenderStrategy.OFFSCREEN）将组件先绘制到离屏缓冲区再合成，适用于包含模糊、滚动等复杂内容的圆角场景，可避免圆角裁剪异常。设置在线绘制模式（上方）以及离屏绘制模式（下方）的示例图如下：



```TypeScript
// xxx.ets
@Entry
@Component
struct RenderStrategyExample {
  build() {
    NavDestination() {
      Column({ space: 20 }) {
        // 快速绘制模式：适用于常规圆角场景，性能更优
        Stack() {
          Column()
            .width(320)
            .height(320)
            .backgroundColor(Color.Black)

          Stack() {
            Stack() {
              Scroll(new Scroller()) {
                Image($r('app.media.startIcon'))
                  .width('100%')
                  .height('200%')
              }

              Column()
                .blur(50) // 设置模糊效果
                .width(300)
                .height(100)
                .position({ x: 0, y: 0 })
            }
          }
          .width(300)
          .height(300)
          .backgroundColor(Color.Pink)
          .borderRadius(50, RenderStrategy.FAST) // 设置快速绘制模式圆角
          .clip(true)
        }

        // 离屏绘制模式：适用于包含模糊效果的圆角场景，可避免裁剪异常
        Stack() {
          Column()
            .width(320)
            .height(320)
            .backgroundColor(Color.Black)

          Stack() {
            Stack() {
              Scroll(new Scroller()) {
                Image($r('app.media.startIcon'))
                  .width('100%')
                  .height('200%')
              }

              Column()
                .blur(50) // 设置模糊效果
                .width(300)
                .height(100)
                .position({ x: 0, y: 0 })
            }
          }
          .width(300)
          .height(300)
          .backgroundColor(Color.Pink)
          .borderRadius(50, RenderStrategy.OFFSCREEN) // 设置离屏绘制模式圆角
          .clip(true)
        }
      }
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例4（设置异形圆角）

该示例通过[borderRadius](#borderradius)设置四个不同圆角值。当其中一个圆角值超过高度或宽度最小值的一半时，按值的比例绘制异形圆角。

```TypeScript
// xxx.ets
@Entry
@Component
struct BorderExample {
  build() {
    Column() {
      Flex({ justifyContent: FlexAlign.SpaceAround, alignItems: ItemAlign.Center }) {
        Text('Text')
          .borderWidth(5)
          .borderColor(0xAFEEEE)
          // topLeft: 2000超过最小值(100)的一半，按值的比例绘制异形圆角
          .borderRadius({
            topLeft: 2000,
            topRight: 10,
            bottomLeft: 30,
            bottomRight: 50
          })
          .width(100)
          .height(100)
          .textAlign(TextAlign.Center)
          .fontSize(16)
      }
    }
  }
}
```

### 示例1（设置组件堆叠顺序）

该示例通过zIndex设置组件堆叠顺序。

Stack容器内子组件不设置zIndex时，默认按照声明顺序显示，后声明的组件会覆盖在先声明的组件上方。



Stack容器子组件设置zIndex后的效果。



```TypeScript
// xxx.ets
@Entry
@Component
struct ZIndexExample {
  build() {
    Column() {
      Stack() {
        // Stack会重叠组件，默认后定义的在最上面，具有较高zIndex值的元素在zIndex较小的元素前面
        // Text1设置zIndex值为2
        Text('1, zIndex(2)')
          .size({ width: '40%', height: '30%' }).backgroundColor(0xbbb2cb)
          .zIndex(2)
        // Text2设置zIndex值为1
        Text('2, zIndex(1)')
          .size({ width: '70%', height: '50%' }).backgroundColor(0xd2cab3).align(Alignment.TopStart)
          .zIndex(1)
        // Text3设置zIndex值为0
        Text('3, zIndex(0)')
          .size({ width: '90%', height: '80%' }).backgroundColor(0xc1cbac).align(Alignment.TopStart)
          .zIndex(0)
      }.width('100%').height(200)
    }.width('100%').height(200)
  }
}
```

### 示例2（动态修改zIndex属性）

该示例使用Button组件动态修改zIndex属性。

不点击Button修改zIndex值的效果。



点击Button动态修改zIndex，使Text1和Text2的zIndex相等，因为在点击Button前的层级顺序上根据zIndex进行稳定排序，层级顺序不发生改变。



点击Button动态修改zIndex，使Text2的zIndex大于Text1，层级顺序发生改变。



```TypeScript
// xxx.ets
@Entry
@Component
struct ZIndexExample {
  @State zIndexValue: number = 0;

  build() {
    Column() {
      // 点击Button改变zIndex后，在点击Button前的层级顺序上根据zIndex进行稳定排序。
      Button('change Text2 zIndex')
        .onClick(() => {
          this.zIndexValue = (this.zIndexValue + 1) % 3;
        })
      Stack() {
        // Text1设置zIndex值为1
        Text('1, zIndex(1)')
          .size({ width: '70%', height: '50%' }).backgroundColor(0xd2cab3).align(Alignment.TopStart)
          .zIndex(1)
        // Text2设置zIndex默认值为0
        Text('2, default zIndex(0), now zIndex:' + this.zIndexValue)
          .size({ width: '90%', height: '80%' }).backgroundColor(0xc1cbac).align(Alignment.TopStart)
          .zIndex(this.zIndexValue)
      }.width('100%').height(200)
    }.width('100%').height(200)
  }
}
```

### 示例3（设置不同容器内组件的zIndex属性）

该示例在不同容器内设置zIndex属性。其中，Text1、Text2在同一个Stack容器内，Text3在另一个Stack容器内。虽然Text3的zIndex值最小，但Text1、Text2仍无法根据zIndex值显示在Text3的上方。

```TypeScript
// xxx.ets
@Entry
@Component
struct ZIndexExample {
  build() {
    Stack() {
      Stack() {
        // Text1设置zIndex值为2
        Text('1, zIndex(2)')
          .size({ width: '40%', height: '30%' }).backgroundColor(0xbbb2cb)
          .zIndex(2)
        // Text2设置zIndex值为1
        Text('2, zIndex(1)')
          .size({ width: '70%', height: '50%' }).backgroundColor(0xd2cab3).align(Alignment.TopStart)
          .zIndex(1)
      }.width('100%').height(200)

      Stack() {
        // zIndex在不同容器的组件中无法生效，Text3会显示在最上方
        // Text3设置zIndex值为0
        Text('3, zIndex(0)')
          .size({ width: '90%', height: '80%' }).backgroundColor(0xc1cbac).align(Alignment.TopStart)
          .zIndex(0)
      }.width('100%').height(200)
    }.width('100%').height(200)
  }
}
```

### 示例1（设置组件的宽高和边距）

设置组件的宽度、高度、内边距及外边距。



```TypeScript
// xxx.ets
@Entry
@Component
struct SizeExample {
  build() {
    Column({ space: 10 }) {
      Text('margin and padding:').fontSize(12).fontColor(0xCCCCCC).width('90%')
      Row() {
        // 宽度80 ,高度80 ,外边距20(蓝色区域），上下左右的内边距分别为5、15、10、20（白色区域）
        Row() {
          Row()
            .size({ width: '100%', height: '100%' })
            .backgroundColor(Color.Yellow)
        }
        .width(80)
        .height(80)
        .padding({
          top: 5,
          left: 10,
          bottom: 15,
          right: 20
        })
        .margin(20)
        .backgroundColor(Color.White)
      }.backgroundColor(Color.Blue)

      Text('constraintSize')
        .fontSize(12)
        .fontColor(0xCCCCCC)
        .width('90%')
      Text('this is a Text.this is a Text.this is a Text.this is a Text.this is a Text.this is a Text.this is a Text.this is a Text.this is a Text.this is a Text.this is a Text.this is a Text.this is a Text.this is a Text.this is a Text')
        .width('90%')
        .constraintSize({ maxWidth: 200 })

      Text('layoutWeight')
        .fontSize(12)
        .fontColor(0xCCCCCC)
        .width('90%')
      // 父容器尺寸确定时，设置了layoutWeight的子组件在主轴布局尺寸按照权重进行分配，忽略本身尺寸设置。
      Row() {
        // 权重1，占主轴剩余空间1/3
        Text('layoutWeight(1)')
          .size({ width: '30%', height: 110 }).backgroundColor(0xFFEFD5).textAlign(TextAlign.Center)
          .layoutWeight(1)
        // 权重2，占主轴剩余空间2/3
        Text('layoutWeight(2)')
          .size({ width: '30%', height: 110 }).backgroundColor(0xF5DEB3).textAlign(TextAlign.Center)
          .layoutWeight(2)
        // 未设置layoutWeight属性，组件按照自身尺寸渲染
        Text('no layoutWeight')
          .size({ width: '30%', height: 110 }).backgroundColor(0xD2B48C).textAlign(TextAlign.Center)
      }
      .size({ width: '90%', height: 140 })
      .backgroundColor(0xAFEEEE)

      // calc计算特性
      Text('calc:')
        .fontSize(12)
        .fontColor(0xCCCCCC)
        .width('90%')
      Column() {
        Row() {
          Text('width 50%')
            .fontSize(14)
            .borderWidth(1)
            .textAlign(TextAlign.Center)
            .size({ width: '50%', height: 50 })
          Text('width 50vp')
            .fontSize(14)
            .borderWidth(1)
            .textAlign(TextAlign.Center)
            .size({ width: '50vp', height: 50 })
        }
        .width('100%')
        .justifyContent(FlexAlign.Center)

        Text('width:calc(50% + 50vp), height:calc(50%)')
          .fontSize(14)
          .borderWidth(1)
          .fontWeight(FontWeight.Bold)
          .backgroundColor(0xFFFAF0)
          .textAlign(TextAlign.Center)
          .size({ width: 'calc(50% + 50vp)', height: 'calc(50%)' })
          // width和height设置百分比时，以父容器的width和height作为基础值。calc的宽度计算结果与上方的两个text宽度之和相等。
      }.width('100%').height(100)
    }
    .width('100%')
    .margin({ top: 5 })
  }
}
```

### 示例2（LocalizedPadding和LocalizedMargin类型的使用）

使用LocalizedPadding类型和LocalizedMargin类型定义padding和margin属性。

从左至右显示语言示例图



从右至左显示语言示例图



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI'

@Entry
@Component
struct SizeExample {
  build() {
    Column({ space: 10 }) {
      Text('margin and padding:')
        .fontSize(12)
        .fontColor(0xCCCCCC)
        .width('90%')
      Row() {
        // 宽度80 ,高度80 ,上下开始结束的外边距40、20、30、10(蓝色区域），上下开始结束的内边距分别为5、15、10、20（白色区域）
        Row() {
          Row()
            .size({ width: '100%', height: '100%' })
            .backgroundColor(Color.Yellow)
        }
        .width(80)
        .height(80)
        .padding({
          top: LengthMetrics.vp(5),
          bottom: LengthMetrics.vp(15),
          start: LengthMetrics.vp(10),
          end: LengthMetrics.vp(20)
        })
        .margin({
          top: LengthMetrics.vp(40),
          bottom: LengthMetrics.vp(20),
          start: LengthMetrics.vp(30),
          end: LengthMetrics.vp(10)
        })
        .backgroundColor(Color.White)
      }
      .backgroundColor(Color.Blue)
    }
    .width('100%')
    .margin({ top: 5 })
  }
}
```

### 示例3（设置组件级安全区）

对容器设置组件级安全区。



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SafeAreaPaddingExample {
  build() {
    Column() {
      Column() {
        Column()
          .width('100%')
          .height('100%')
          .backgroundColor(Color.Pink)
      }
      .width(200)
      .height(200)
      .backgroundColor(Color.Yellow)
      .borderWidth(10)
      .padding(10)
      .safeAreaPadding(LengthMetrics.vp(40))
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例4（使用attributeModifier动态设置安全区）

使用attributeModifier对容器设置组件级安全区。



```TypeScript
// xxx.ets
class MyModifier implements AttributeModifier<CommonAttribute> {
  applyNormalAttribute(instance: CommonAttribute): void {
    instance.safeAreaPadding({
      left: 10,
      top: 20,
      right: 30,
      bottom: 40
    })
  }
}

@Entry
@Component
struct SafeAreaPaddingExample {
  @State modifier: MyModifier = new MyModifier()

  build() {
    Column() {
      Column() {
        Column()
          .width('100%')
          .height('100%')
          .backgroundColor(Color.Pink)
      }
      .width(200)
      .height(200)
      .backgroundColor(Color.Yellow)
      .borderWidth(10)
      .padding(10)
      .attributeModifier(this.modifier)
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例5（设置布局策略）

对容器大小设置布局策略。



```TypeScript
// xxx.ets
@Entry
@Component
struct LayoutPolicyExample {
  build() {
    Column() {
      Column() {
        // matchParent生效时，当前组件会与其父组件内容区大小（180vp * 180vp）相等，同时依旧受自身constraintSize（150vp * 150vp）约束，因此当前组件大小为150vp * 150vp
        Text('matchParent')
        Flex()
          .backgroundColor('rgb(0, 74, 175)')
          .width(LayoutPolicy.matchParent)
          .height(LayoutPolicy.matchParent)
          .constraintSize({ maxWidth: 150, maxHeight: 150 })

        // wrapContent生效时，当前组件会与其子组件大小（300vp * 300vp）相等，但不能超过父组件内容大小（180vp * 180vp）且会受自身constraintSize（250vp * 250vp）约束，因此当前组件大小为180vp * 180vp
        Text('wrapContent')
        Row() {
          Flex()
            .width(300)
            .height(300)
        }
        .backgroundColor('rgb(39, 135, 217)')
        .width(LayoutPolicy.wrapContent)
        .height(LayoutPolicy.wrapContent)
        .constraintSize({ maxWidth: 250, maxHeight: 250 })

        // 从API version 20开始，layoutPolicy支持wrapContent和fixAtIdealSize。fixAtIdealSize生效时，当前组件会与其子组件大小（300vp * 300vp）相等，可以超过父组件内容大小（180vp * 180vp）但会受自身constraintSize（250vp * 250vp）约束，因此当前组件大小为250vp * 250vp
        Text('fixAtIdealSize')

        Row() {
          Flex()
            .width(300)
            .height(300)
        }
        .backgroundColor('rgb(240, 250, 255)')
        .width(LayoutPolicy.fixAtIdealSize)
        .height(LayoutPolicy.fixAtIdealSize)
        .constraintSize({ maxWidth: 250, maxHeight: 250 })
      }
      .width(200)
      .height(200)
      .padding(10)
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例6（子组件单方向设置matchParent效果）

该示例展示Column组件自适应子组件且子组件仅单方向设置matchParent时的布局效果。从API版本26.0.0开始，Column组件高度自适应第一个和第二个子组件，宽度自适应第一个和第三个子组件。

```TypeScript
@Entry
@Component
struct Demo {
  build() {
    Column() {
      // API版本26.0.0之前，父组件高度计算为 padding + 组件1高度 = 30px * 2 + 200px = 260px, 宽度计算为 padding + 组件1宽度 = 30px * 2 + 200px = 260px
      // 从API版本26.0.0开始，父组件高度计算为 padding + space + 组件1高度 + 组件2高度 = 30px * 2 + 30px + 200px + 200px = 490px, 宽度计算为 padding + max(组件1宽度, 组件3宽度) = 30px * 2 + max(200px, 400px) = 460px
      Column({space: "30px"}) {
        Column()
          .width("200px")
          .height("200px")
          .backgroundColor('rgb(0, 74, 175)')

        Column()
          .width(LayoutPolicy.matchParent) // 子组件宽度与父组件内容区宽度保持一致
          .height("200px")
          .backgroundColor('rgb(0, 74, 175)')

        Column()
          .width("400px")
          .height(LayoutPolicy.matchParent) // 子组件高度与父组件内容区高度保持一致
          .backgroundColor('rgb(0, 74, 175)')
      }
      .width(LayoutPolicy.wrapContent)
      .height(LayoutPolicy.wrapContent)
      .backgroundColor('rgb(39, 135, 217)')
      .padding("30px")
    }.width("100%")
  }
}
```

### 示例1（逐帧布局的效果）

以下示例通过改变Text组件宽度实现逐帧布局的效果。



```TypeScript
@AnimatableExtend(Text)
function animatableWidth(width: number) {
  .width(width)
}

@Entry
@Component
struct AnimatablePropertyExample {
  @State textWidth: number = 80;

  build() {
    Column() {
      Text("AnimatableProperty")
        .animatableWidth(this.textWidth)
        .animation({ duration: 2000, curve: Curve.Ease })
      Button("Play")
        .onClick(() => {
          this.textWidth = this.textWidth === 80 ? 160 : 80;
        })
    }.width("100%")
    .padding(10)
  }
}
```

### 示例2（折线的动画效果）

以下示例实现折线的动画效果。

```TypeScript
class Point {
  x: number
  y: number

  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }

  plus(rhs: Point): Point {
    return new Point(this.x + rhs.x, this.y + rhs.y);
  }

  subtract(rhs: Point): Point {
    return new Point(this.x - rhs.x, this.y - rhs.y);
  }

  multiply(scale: number): Point {
    return new Point(this.x * scale, this.y * scale);
  }

  equals(rhs: Point): boolean {
    return this.x === rhs.x && this.y === rhs.y;
  }
}

// PointVector实现了AnimatableArithmetic<T>接口
class PointVector extends Array<Point> implements AnimatableArithmetic<PointVector> {
  constructor(value: Array<Point>) {
    super();
    value.forEach(point => this.push(point));
  }

  plus(rhs: PointVector): PointVector {
    let result = new PointVector([]);
    const len = Math.min(this.length, rhs.length);
    for (let i = 0; i < len; i++) {
      result.push((this as Array<Point>)[i].plus((rhs as Array<Point>)[i]));
    }
    return result;
  }

  subtract(rhs: PointVector): PointVector {
    let result = new PointVector([]);
    const len = Math.min(this.length, rhs.length);
    for (let i = 0; i < len; i++) {
      result.push((this as Array<Point>)[i].subtract((rhs as Array<Point>)[i]));
    }
    return result;
  }

  multiply(scale: number): PointVector {
    let result = new PointVector([]);
    for (let i = 0; i < this.length; i++) {
      result.push((this as Array<Point>)[i].multiply(scale));
    }
    return result;
  }

  equals(rhs: PointVector): boolean {
    if (this.length !== rhs.length) {
      return false;
    }
    for (let i = 0; i < this.length; i++) {
      if (!(this as Array<Point>)[i].equals((rhs as Array<Point>)[i])) {
        return false;
      }
    }
    return true;
  }

  get(): Array<Object[]> {
    let result: Array<Object[]> = [];
    this.forEach(point => result.push([point.x, point.y]));
    return result;
  }
}

@AnimatableExtend(Polyline)
function animatablePoints(points: PointVector) {
  // 将PointVector转换为Polyline的points属性所需的数组格式
  .points(points.get())
}

@Entry
@Component
struct AnimatablePropertyExample {
  @State points: PointVector = new PointVector([
    new Point(50, Math.random() * 200),
    new Point(100, Math.random() * 200),
    new Point(150, Math.random() * 200),
    new Point(200, Math.random() * 200),
    new Point(250, Math.random() * 200),
  ])

  build() {
    Column() {
      Polyline()
        .animatablePoints(this.points)
        .animation({ duration: 1000, curve: Curve.Ease }) // 设置动画参数
        .size({ height: 220, width: 300 })
        .fill(Color.Green)
        .stroke(Color.Red)
        .backgroundColor('#eeaacc')
      Button("Play")
        .onClick(() => {
          // points是实现了可动画协议的数据类型，points在动画过程中可按照定义的运算规则、动画参数从之前的PointVector变为新的PointVector数据，产生每一帧的PointVector数据，进而产生动画
          this.points = new PointVector([
            new Point(50, Math.random() * 200),
            new Point(100, Math.random() * 200),
            new Point(150, Math.random() * 200),
            new Point(200, Math.random() * 200),
            new Point(250, Math.random() * 200),
          ]);
        })
    }.width("100%")
    .padding(10)
  }
}
```

### 示例1（对齐方式和主轴方向上的布局）

设置内容在元素内的对齐方式和子元素在父组件主轴方向上的布局。



```TypeScript
// xxx.ets
@Entry
@Component
struct PositionExample1 {
  build() {
    Column() {
      Column({ space: 10 }) {
        // 元素内容 < 元素宽高，设置内容在元素内的对齐方式
        Text('align').fontSize(9).fontColor(0xCCCCCC).width('90%')
        Stack() {
          Text('First show in bottom end').height('65%').backgroundColor(0xD2B48C)
          Text('Second show in bottom end').backgroundColor(0xF5DEB3).opacity(0.9)
        }.width('90%').height(50).margin({ top: 5 }).backgroundColor(0xFFE4C4)
        .align(Alignment.BottomEnd)
        Stack() {
          Text('top start')
        }.width('90%').height(50).margin({ top: 5 }).backgroundColor(0xFFE4C4)
        .align(Alignment.TopStart)

        // 父组件设置direction为Direction.Ltr，子元素从左到右排列
        Text('direction').fontSize(9).fontColor(0xCCCCCC).width('90%')
        Row() {
          Text('1').height(50).width('25%').fontSize(16).backgroundColor(0xF5DEB3)
          Text('2').height(50).width('25%').fontSize(16).backgroundColor(0xD2B48C)
          Text('3').height(50).width('25%').fontSize(16).backgroundColor(0xF5DEB3)
          Text('4').height(50).width('25%').fontSize(16).backgroundColor(0xD2B48C)
        }
        .width('90%')
        .direction(Direction.Ltr)
        // 父组件设置direction为Direction.Rtl，子元素从右到左排列
        Row() {
          Text('1').height(50).width('25%').fontSize(16).backgroundColor(0xF5DEB3).textAlign(TextAlign.End)
          Text('2').height(50).width('25%').fontSize(16).backgroundColor(0xD2B48C).textAlign(TextAlign.End)
          Text('3').height(50).width('25%').fontSize(16).backgroundColor(0xF5DEB3).textAlign(TextAlign.End)
          Text('4').height(50).width('25%').fontSize(16).backgroundColor(0xD2B48C).textAlign(TextAlign.End)
        }
        .width('90%')
        .direction(Direction.Rtl)
      }
    }
    .width('100%').margin({ top: 5 })
  }
}
```

### 示例2（位置偏移）

基于父组件、相对定位、锚点作出位置偏移。



```TypeScript
// xxx.ets
@Entry
@Component
struct PositionExample2 {
  build() {
    Column({ space: 20 }) {
      // 设置子组件左上角相对于父组件左上角的偏移位置
      Text('position').fontSize(12).fontColor(0xCCCCCC).width('90%')
      Row() {
        Text('1').size({ width: '30%', height: '50' }).backgroundColor(0xdeb887).border({ width: 1 }).fontSize(16)
          .textAlign(TextAlign.Center)
        Text('2 position(30, 10)')
          .size({ width: '60%', height: '30' })
          .backgroundColor(0xbbb2cb)
          .border({ width: 1 })
          .fontSize(16)
          .align(Alignment.Start)
          .position({ x: 30, y: 10 })
        Text('3').size({ width: '45%', height: '50' }).backgroundColor(0xdeb887).border({ width: 1 }).fontSize(16)
          .textAlign(TextAlign.Center)
        Text('4 position(50%, 70%)')
          .size({ width: '50%', height: '50' })
          .backgroundColor(0xbbb2cb)
          .border({ width: 1 })
          .fontSize(16)
          .position({ x: '50%', y: '70%' })
      }.width('90%').height(100).border({ width: 1, style: BorderStyle.Dashed })

      // 相对于起点偏移，其中x为最终定位点距离起点水平方向间距，x>0往左，反之向右。
      // y为最终定位点距离起点垂直方向间距，y>0向上，反之向下
      Text('markAnchor').fontSize(12).fontColor(0xCCCCCC).width('90%')
      Stack({ alignContent: Alignment.TopStart }) {
        Row()
          .size({ width: '100', height: '100' })
          .backgroundColor(0xdeb887)
        Text('text')
          .fontSize('30px')
          .textAlign(TextAlign.Center)
          .size({ width: 25, height: 25 })
          .backgroundColor(Color.Green)
          .markAnchor({ x: 25, y: 25 })
        Text('text')
          .fontSize('30px')
          .textAlign(TextAlign.Center)
          .size({ width: 25, height: 25 })
          .backgroundColor(Color.Green)
          .markAnchor({ x: -100, y: -25 })
        Text('text')
          .fontSize('30px')
          .textAlign(TextAlign.Center)
          .size({ width: 25, height: 25 })
          .backgroundColor(Color.Green)
          .markAnchor({ x: 25, y: -25 })
      }.margin({ top: 25 }).border({ width: 1, style: BorderStyle.Dashed })

      // 相对定位，x>0向右偏移，反之向左，y>0向下偏移，反之向上
      Text('offset').fontSize(12).fontColor(0xCCCCCC).width('90%')
      Row() {
        Text('1').size({ width: '15%', height: '50' }).backgroundColor(0xdeb887).border({ width: 1 }).fontSize(16)
          .textAlign(TextAlign.Center)
        Text('2  offset(15, 30)')
          .size({ width: 120, height: '50' })
          .backgroundColor(0xbbb2cb)
          .border({ width: 1 })
          .fontSize(16)
          .align(Alignment.Start)
          .offset({ x: 15, y: 30 })
        Text('3').size({ width: '15%', height: '50' }).backgroundColor(0xdeb887).border({ width: 1 }).fontSize(16)
          .textAlign(TextAlign.Center)
        Text('4 offset(-5%, 20%)')
          .size({ width: 100, height: '50' })
          .backgroundColor(0xbbb2cb)
          .border({ width: 1 })
          .fontSize(16)
          .offset({ x: '-5%', y: '20%' })
      }.width('90%').height(100).border({ width: 1, style: BorderStyle.Dashed })
    }
    .width('100%').margin({ top: 25 })
  }
}
```

### 示例3（绝对定位和相对偏移）

使用position设置绝对定位，确定子组件相对父组件的位置。使用offset设置相对偏移，组件相对原本的布局位置进行偏移。



```TypeScript
// xxx.ets
@Entry
@Component
struct Example3 {
  build() {
    Column({ space: 20 }) {
      Text('position use Edges').fontSize(12).fontColor(0xCCCCCC).width('90%')
      Row() {
        Text('bottom:0, right:0')
          .size({ width: '30%', height: '50' })
          .backgroundColor(0xdeb887)
          .border({ width: 1 })
          .fontSize(16)
          .textAlign(TextAlign.Center)
          .position({ bottom: 0, right: 0 })
        Text('top:0, left:0')
          .size({ width: '30%', height: '50' })
          .backgroundColor(0xdeb887)
          .border({ width: 1 })
          .fontSize(16)
          .textAlign(TextAlign.Center)
          .position({ top: 0, left: 0 })
        Text('top:10%, left:50%')
          .size({ width: '50%', height: '30' })
          .backgroundColor(0xbbb2cb)
          .border({ width: 1 })
          .fontSize(16)
          .textAlign(TextAlign.Center)
          .position({ top: '10%', left: '50%' })
        Text('bottom:0, left:30')
          .size({ width: '50%', height: '30' })
          .backgroundColor(0xbbb2cb)
          .border({ width: 1 })
          .fontSize(16)
          .textAlign(TextAlign.Center)
          .position({ bottom: 0, left: 30 })
      }.width('90%').height(100).border({ width: 1, style: BorderStyle.Dashed })


      Text('offset use Edges').fontSize(12).fontColor(0xCCCCCC).width('90%')
      Row() {
        Text('1')
          .size({ width: '25%', height: 50 })
          .backgroundColor(0xdeb887)
          .border({ width: 1 })
          .fontSize(16)
          .textAlign(TextAlign.Center)
        Text('2 top:30, left:0')
          .size({ width: '25%', height: 50 })
          .backgroundColor(0xbbb2cb)
          .border({ width: 1 })
          .fontSize(16)
          .textAlign(TextAlign.Center)
          .offset({ top: 30, left: 0 })
        Text('3')
          .size({ width: '25%', height: 50 })
          .backgroundColor(0xdeb887)
          .border({ width: 1 })
          .fontSize(16)
          .textAlign(TextAlign.Center)
        Text('4 bottom:10, right:30')
          .size({ width: '25%', height: 50 })
          .backgroundColor(0xbbb2cb)
          .border({ width: 1 })
          .fontSize(12)
          .textAlign(TextAlign.Center)
          .offset({ bottom: 10, right: 30 })
      }.width('90%').height(150).border({ width: 1, style: BorderStyle.Dashed })
    }.width('100%').margin({ top: 25 })
  }
}
```

### 示例4（镜像效果）

通用布局属性支持[使用镜像能力](./../../../ui/arkts-internationalization.md#使用镜像能力)。下述示例从上到下依次通过[position](#position)、[offset](#offset)和[markAnchor](#markanchor)实现镜像效果，为对比镜像前后的差异，浅蓝色对应镜像前效果，深蓝色对应镜像后效果。

镜像前效果：



镜像后效果如下，镜像生效条件请参考[使用镜像能力](./../../../ui/arkts-internationalization.md#使用镜像能力)：



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Example4 {
  private scroller: Scroller = new Scroller()

  build() {
    Column() {
      Stack({ alignContent: Alignment.End }) {
        Scroll(this.scroller) {
          Flex({ direction: FlexDirection.Column }) {
            RelativeContainer() {
              Row() {
              }
              .position({ start: LengthMetrics.px(200), top: LengthMetrics.px(100) }) // position接口中的参数使用LocalizedEdges类型，支持镜像翻转效果
              .width("30%")
              .height("20%")
              .backgroundColor('rgb(0, 74, 175)')
              .padding(50)
              .margin(50)

              Row() {
              }
              .position({ left: '200px', top: '100px' }) // position接口中的参数使用Edges类型，不支持镜像翻转效果
              .width("30%")
              .height("20%")
              .backgroundColor('rgb(39, 135, 217)')
              .padding(50)
              .margin(50)

              Row() {
              }
              .offset({ start: LengthMetrics.vp(100), top: LengthMetrics.vp(200) }) // offset接口中的参数使用LocalizedEdges类型，支持镜像翻转效果
              .width("30%")
              .height("20%")
              .backgroundColor('rgb(0, 74, 175)')
              .padding(50)
              .margin(50)

              Row() {
              }
              .offset({ left: 100, top: 200 }) // offset接口中的参数使用Edges类型，不支持镜像翻转效果
              .width("30%")
              .height("20%")
              .backgroundColor('rgb(39, 135, 217)')
              .padding(50)
              .margin(50)

              Row() {
              }
              .markAnchor({
                start: LengthMetrics.fp(100),
                top: LengthMetrics.fp(-350)
              }) // markAnchor接口中的参数使用LocalizedPosition类型，支持镜像翻转效果
              .width("30%")
              .height("20%")
              .backgroundColor('rgb(0, 74, 175)')
              .padding(50)
              .margin(50)

              Row() {
              }
              .markAnchor({ x: '100fp', y: '-350fp' }) // markAnchor接口中的参数使用Position类型，不支持镜像翻转效果
              .width("30%")
              .height("20%")
              .backgroundColor('rgb(39, 135, 217)')
              .padding(50)
              .margin(50)
            }
            .backgroundColor(Color.White)
            .padding(50)
            .margin(50)
          }
        }
        .width('100%')
        .scrollBar(BarState.Off)
        .scrollable(ScrollDirection.Vertical)

        ScrollBar({ scroller: this.scroller, direction: ScrollBarDirection.Vertical, state: BarState.Auto }) {
          Text()
            .width(20)
            .height(100)
            .borderRadius(10)
            .backgroundColor('#C0C0C0')
        }.width(20).backgroundColor('#ededed')
      }
    }.height('90%')
  }
}
```

### 示例5（align属性适配镜像特性）

设置内容在元素内的对齐方式和子元素在父组件主轴方向上的布局。



```TypeScript
// xxx.ets
@Entry
@Component
struct buttonTestDemo {
  @State isLocalizedAlignment: LocalizedAlignment[] =
    [LocalizedAlignment.TOP_START, LocalizedAlignment.TOP, LocalizedAlignment.TOP_END, LocalizedAlignment.START,
      LocalizedAlignment.CENTER, LocalizedAlignment.END, LocalizedAlignment.BOTTOM_START, LocalizedAlignment.BOTTOM,
      LocalizedAlignment.BOTTOM_END]
  @State isLocalizedAlignmentIndex: number = 4
  @State isDirection: Direction[] = [Direction.Ltr, Direction.Rtl, Direction.Auto]
  @State isDirectionIndex: number = 0

  build() {
    Row() {
      Column() {

        Row({ space: 5 }) {
          Button('START')
            .onClick(() => {
              this.isLocalizedAlignmentIndex = 3
            })
          Button('CENTER')
            .onClick(() => {
              this.isLocalizedAlignmentIndex = 4
            })
          Button('END')
            .onClick(() => {
              this.isLocalizedAlignmentIndex = 5
            })
        }.margin(20)

        Row({ space: 5 }) {
          Button('Ltr')
            .onClick(() => {
              this.isDirectionIndex = 0
            })
          Button('Rtl')
            .onClick(() => {
              this.isDirectionIndex = 1
            })
          Button('Auto')
            .onClick(() => {
              this.isDirectionIndex = 2
            })
        }.margin(20)

        Row() {
          Button('OK', { type: ButtonType.Capsule, stateEffect: true })
            .backgroundColor(0x317aff)
            .width(200)
            .height(100)
            .direction(this.isDirection[this.isDirectionIndex])
            .align(this.isLocalizedAlignment[this.isLocalizedAlignmentIndex])
        }.margin(20)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例6（layoutGravity属性单独设置Stack组件中子组件的对齐规则）

更改Stack中Text的位置。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index5 {
  private layoutGravityArr: LocalizedAlignment[] = [
    LocalizedAlignment.TOP_START, LocalizedAlignment.TOP, LocalizedAlignment.TOP_END,
    LocalizedAlignment.START, LocalizedAlignment.CENTER, LocalizedAlignment.END,
    LocalizedAlignment.BOTTOM_START, LocalizedAlignment.BOTTOM, LocalizedAlignment.BOTTOM_END];
  @State layoutGravityIndex: number = 0;
  private directionArr: Direction[] = [Direction.Ltr, Direction.Rtl, Direction.Auto];
  @State directionIndex: number = 0;

  build() {
    Row() {
      Column() {
        Stack({
          alignContent: Alignment.TopStart
        }) {
          Text('StackChildAlign_TopStart').fontSize(15)
          Text('Child Text')
            .width(150)
            .height(150)
            .backgroundColor(Color.Yellow)
            .fontSize(15)
            .layoutGravity(this.layoutGravityArr[this.layoutGravityIndex])
        }
        .width('100%')
        .height(400)
        .backgroundColor(Color.Grey)
        .margin({ top: 10, bottom: 10 })
        .direction(this.directionArr[this.directionIndex])

        Button("LayoutGravity: " + this.layoutGravityArr[this.layoutGravityIndex])
          .width(300)
          .fontSize(16)
          .onClick(() => {
            this.layoutGravityIndex = ++this.layoutGravityIndex % this.layoutGravityArr.length;
          })
          .margin({ bottom: 10 })

        Button("Direction: " + this.directionArr[this.directionIndex])
          .width(150)
          .fontSize(16)
          .onClick(() => {
            this.directionIndex = ++this.directionIndex % this.directionArr.length;
          })
          .margin({ bottom: 10 })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

该示例主要显示通过[opacity](#opacity)设置组件的不透明度。

```TypeScript
// xxx.ets
@Entry
@Component
struct OpacityExample {
  build() {
    Column({ space: 5 }) {
      Text('opacity(1)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Text().width('90%').height(50).opacity(1).backgroundColor(0xAFEEEE)
      Text('opacity(0.7)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Text().width('90%').height(50).opacity(0.7).backgroundColor(0xAFEEEE)
      Text('opacity(0.4)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Text().width('90%').height(50).opacity(0.4).backgroundColor(0xAFEEEE)
      Text('opacity(0.1)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Text().width('90%').height(50).opacity(0.1).backgroundColor(0xAFEEEE)
      Text('opacity(0)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Text().width('90%').height(50).opacity(0).backgroundColor(0xAFEEEE)
    }
    .width('100%')
    .padding({ top: 5 })
  }
}
```

该示例通过为[Navigation](ts-basic-components-navigation.md)下的[Button](ts-basic-components-button.md)组件绑定toolbar通用属性，为标题栏NavBar分栏开头位置添加包含两个[Button](ts-basic-components-button.md)组件的工具栏项。为[NavDestination](ts-basic-components-navdestination.md)下的[Text](ts-basic-components-text.md)组件绑定toolbar通用属性，为标题栏NavDestination分栏末尾位置添加两个工具栏项，分别包含一个滑动条组件和一个搜索框组件。

```TypeScript
// xxx.ets
@Entry
@Component
struct ToolbarExample {
  normalIcon: Resource = $r('app.media.startIcon')
  selectedIcon: Resource = $r('app.media.startIcon')
  @State arr: number[] = [1, 2, 3]
  @State current: number = 1
  @Provide('navPathStack') navPathStack: NavPathStack = new NavPathStack()

  @Builder
  MyToolbar() {
    ToolBarItem({ placement: ToolBarItemPlacement.TOP_BAR_LEADING }) {
      Button("left").height("30vp")
    }

    ToolBarItem({ placement: ToolBarItemPlacement.TOP_BAR_LEADING }) {
      Button("right").height("30vp")
    }
  }

  @Builder
  MyToolbarNavDest() {
    ToolBarItem({ placement: ToolBarItemPlacement.TOP_BAR_TRAILING }) {
      Slider().width("120vp")
    }

    ToolBarItem({ placement: ToolBarItemPlacement.TOP_BAR_TRAILING }) {
      Search().width("120vp")
    }
  }

  @Builder
  PageNavDest(name: string) {
    NavDestination() {
      Column() {
        Text("add toolbar")
          .fontSize(30)
          .toolbar(this.MyToolbarNavDest())
      }
      .backgroundColor(Color.Gray)
    }
  }

  build() {
    SideBarContainer(SideBarContainerType.Embed) {
      Column() {
        ForEach(this.arr, (item: number) => {
          Column({ space: 5 }) {
            Image(this.current === item ? this.selectedIcon : this.normalIcon).width(64).height(64)
            Text("Index0" + item)
              .fontSize(25)
              .fontColor(this.current === item ? '#0A59F7' : '#999')
              .fontFamily('source-sans-pro,cursive,sans-serif')
          }
          .onClick(() => {
            this.current = item;
          })
        }, (item: number) => item.toString())
      }.width('100%')
      .justifyContent(FlexAlign.SpaceEvenly)
      .backgroundColor('#19000000')

      Navigation(this.navPathStack) {
        Column() {
          Button('pushPath', { stateEffect: true, type: ButtonType.Capsule })
            .width('20%')
            .height(40)
            .margin(20)
            .toolbar(this.MyToolbar())
          Button('showNavDest', { stateEffect: true, type: ButtonType.Capsule })
            .width('20%')
            .height(40)
            .margin(20)
            .onClick(() => {
              this.navPathStack.pushPath({ name: '1' });
            })
        }
        .width('100%')
        .height('100%')
      }
      .navBarPosition(NavBarPosition.Start)
      .navBarWidth("50%")
      .navBarWidthRange(["25%", "70%"])
      .hideBackButton(true)
      .navDestination(this.PageNavDest)
      .height('100%')
      .title('Navigation')
    }
    .sideBarWidth(150)
    .minSideBarWidth(50)
    .maxSideBarWidth(300)
    .minContentWidth(0)
    .onChange((value: boolean) => {
      console.info('status:' + value);
    })
    .divider({
      strokeWidth: '1vp',
      color: Color.Gray,
      startMargin: '4vp',
      endMargin: '4vp'
    })
  }
}
```

### 示例1（允许拖拽和落入）

示例1通过配置[allowDrop](arkts-arkui-common-comp-commonmethod-c.md#allowdrop)设置组件是否可落入，通过配置[draggable](#draggable)设置组件是否可拖拽。



```TypeScript
// xxx.ets
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

@Entry
@Component
struct ImageExample {
  @State uri: string = '';
  @State disallowedBlockArr: string[] = [];
  @State allowedBlockArr: string[] = [];
  @State disallowedAreaVisible: Visibility = Visibility.Visible;

  build() {
    Column() {
      Text('Image拖拽')
        .fontSize('30dp')
      Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center, justifyContent: FlexAlign.SpaceAround }) {
        // $r('app.media.icon')需要替换为开发者所需的图像资源文件
        Image($r('app.media.icon'))
          .width(100)
          .height(100)
          .border({ width: 1 })
          .visibility(this.disallowedAreaVisible)
          .draggable(true)
          .onDragEnd((event: DragEvent) => {
            let ret = event.getResult();
            if (ret == 0) {
              console.info('enter ret == 0');
              this.disallowedAreaVisible = Visibility.Hidden;
            } else {
              console.info('enter ret != 0');
              this.disallowedAreaVisible = Visibility.Visible;
            }
          })
      }
      .margin({ bottom: 20 })

      Row() {
        Column() {
          Text('不允许释放区域')
            .fontSize('15dp')
            .height('10%')
          List() {
            ForEach(this.disallowedBlockArr, (item: string, index) => {
              ListItem() {
                Image(item)
                  .width(100)
                  .height(100)
                  .border({ width: 1 })
              }
              .margin({ left: 30, top: 30 })
            }, (item: string) => item)
          }
          .height('90%')
          .width('100%')
          .allowDrop([uniformTypeDescriptor.UniformDataType.TEXT])
          .onDrop((event?: DragEvent, extraParams?: string) => {
            this.uri = JSON.parse(extraParams as string)?.extraInfo;
            this.disallowedBlockArr.splice(JSON.parse(extraParams as string)?.insertIndex, 0, this.uri);
            console.info('ondrop not udmf data');
          })
          .border({ width: 1 })
        }
        .height('50%')
        .width('45%')
        .border({ width: 1 })
        .margin({ left: 12 })

        Column() {
          Text('可释放区域')
            .fontSize('15dp')
            .height('10%')
          List() {
            ForEach(this.allowedBlockArr, (item: string, index) => {
              ListItem() {
                Image(item)
                  .width(100)
                  .height(100)
                  .border({ width: 1 })
              }
              .margin({ left: 30, top: 30 })
            }, (item: string) => item)
          }
          .border({ width: 1 })
          .height('90%')
          .width('100%')
          .allowDrop([uniformTypeDescriptor.UniformDataType.IMAGE])
          .onDrop((event?: DragEvent, extraParams?: string) => {
            console.info('enter onDrop');
            let dragData: UnifiedData = (event as DragEvent).getData() as UnifiedData;
            if (dragData != undefined) {
              let arr: Array<unifiedDataChannel.UnifiedRecord> = dragData.getRecords();
              if (arr.length > 0) {
                let image = arr[0] as unifiedDataChannel.Image;
                this.uri = image.imageUri;
                this.allowedBlockArr.splice(JSON.parse(extraParams as string)?.insertIndex, 0, this.uri);
              } else {
                console.info(`dragData arr is null`);
              }
            } else {
              console.info(`dragData  is undefined`);
            }
            console.info('ondrop udmf data');
          })
        }
        .height('50%')
        .width('45%')
        .border({ width: 1 })
        .margin({ left: 12 })
      }
    }.width('100%')
  }
}
```

### 示例2（设置预览图）

示例2通过配置[dragPreview](#dragpreview11)设置拖拽过程的预览图。



```TypeScript
// xxx.ets
@Entry
@Component
struct DragPreviewDemo {
  @Builder
  dragPreviewBuilder() {
    Column() {
      Text('dragPreview')
        .width(150)
        .height(50)
        .fontSize(20)
        .borderRadius(10)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Pink)
    }
  }

  @Builder
  menuBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('menu item 1')
        .fontSize(15)
        .width(100)
        .height(40)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Pink)
      Divider()
        .height(5)
      Text('menu item 2')
        .fontSize(15)
        .width(100)
        .height(40)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Pink)
    }
    .width(100)
  }

  build() {
    Row() {
      Column() {
        // $r('app.media.image')需要替换为开发者所需的图像资源文件
        Image($r('app.media.image'))
          .width('30%')
          .draggable(true)
          .bindContextMenu(this.menuBuilder, ResponseType.LongPress)
          .onDragStart(() => {
            console.info('Image onDragStart');
          })
          .dragPreview(this.dragPreviewBuilder)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例3（设置背板图样式）

示例3通过配置[dragPreviewOptions](#dragpreviewoptions11)为ENABLE_DEFAULT_SHADOW、ENABLE_DEFAULT_RADIUS设置默认阴影和统一圆角效果。从API version 18开始，通过配置[dragPreviewOptions](#dragpreviewoptions11)为ENABLE_DRAG_ITEM_GRAY_EFFECT设置灰显效果。



```TypeScript
// xxx.ets
@Entry
@Component
struct DragPreviewOptionsDemo {
  build() {
    Row() {
      Column() {
        // $r('app.media.image')需要替换为开发者所需的图像资源文件
        Image($r('app.media.image'))
          .margin({ top: 10 })
          .width('30%')
          .draggable(true)
          .dragPreviewOptions({ mode: DragPreviewMode.AUTO })
        // $r('app.media.image')需要替换为开发者所需的图像资源文件
        Image($r('app.media.image'))
          .margin({ top: 10 })
          .width('30%')
          .border({
            radius: {
              topLeft: 1,
              topRight: 2,
              bottomLeft: 4,
              bottomRight: 8
            }
          })
          .draggable(true)
          .onDragStart(() => {
            console.info('Image onDragStart');
          })
          .dragPreviewOptions({
            mode: [DragPreviewMode.ENABLE_DEFAULT_SHADOW, DragPreviewMode.ENABLE_DEFAULT_RADIUS,
              DragPreviewMode.ENABLE_DRAG_ITEM_GRAY_EFFECT]
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

### 示例4（设置多选拖拽）

示例4通过配置[isMultiSelectionEnabled](arkts-arkui-common-comp-draginteractionoptions-i.md)实现Grid组件的多选拖拽效果。



```TypeScript
@Entry
@Component
struct Example {
  @State numbers: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8]

  build() {
    Column({ space: 5 }) {
      Grid() {
        ForEach(this.numbers, (item: number) => {
          GridItem() {
            Column()
              .backgroundColor(Color.Blue)
              .width('100%')
              .height('100%')
          }
          .width(90)
          .height(90)
          .selectable(true)
          .selected(true)
          .dragPreviewOptions({}, { isMultiSelectionEnabled: true })
          .onDragStart(() => {

          })
        }, (item: number) => item.toString())
      }
      .columnsTemplate('1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr')
      .height(300)
    }
    .width('100%')
  }
}
```

### 示例5（设置默认点按效果）

示例5通过配置[defaultAnimationBeforeLifting](arkts-arkui-common-comp-draginteractionoptions-i.md)实现Grid组件的默认点按效果。



```TypeScript
@Entry
@Component
struct Example {
  @State numbers: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8]

  build() {
    Column({ space: 5 }) {
      Grid() {
        ForEach(this.numbers, (item: number) => {
          GridItem() {
            Column()
              .backgroundColor(Color.Blue)
              .width('100%')
              .height('100%')
          }
          .width(90)
          .height(90)
          .selectable(true)
          .selected(true)
          .dragPreviewOptions({}, { isMultiSelectionEnabled: true, defaultAnimationBeforeLifting: true })
          .onDragStart(() => {

          })
        }, (item: number) => item.toString())
      }
      .columnsTemplate('1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr')
      .height(300)
    }
    .width('100%')
  }
}
```

### 示例6（自定义背板图样式）

示例6通过配置[ImageModifier](arkts-arkui-common-comp-imagemodifier-t.md)实现Image组件的自定义背板图样式。



```TypeScript
// xxx.ets
import { ImageModifier } from '@kit.ArkUI';

@Entry
@Component
struct DragPreviewOptionsDemo {
  @State myModifier: ImageAttribute = new ImageModifier().opacity(0.5)
  @State opacityIndex: number = 0
  @State opacityList: (number | undefined | null)[] = [
    0.3, 0.5, 0.7, 1, -50, 0, 10, undefined, null
  ]

  build() {
    Row() {
      Column() {
        Text(this.opacityList[this.opacityIndex] + '')
        Button('Opacity')
          .onClick(() => {
            this.opacityIndex++;
            if (this.opacityIndex > this.opacityList.length - 1) {
              this.opacityIndex = 0;
            }
          })
        // $r('app.media.image')需要替换为开发者所需的图像资源文件
        Image($r('app.media.image'))
          .margin({ top: 10 })
          .width('100%')
          .draggable(true)
          .dragPreviewOptions({
            modifier: this.myModifier.opacity(this.opacityList[this.opacityIndex]) as ImageModifier
          })
      }
      .width('50%')
      .height('50%')
    }
  }
}
```

### 示例7（图片拖拽设置）

示例7展示了不同图片（在线图片资源、本地图片资源和PixelMap）在拖拽时组件的设置。

使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。



```TypeScript
// xxx.ets
import { uniformTypeDescriptor, unifiedDataChannel } from '@kit.ArkData';
import { image } from '@kit.ImageKit';
import { request } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';
import { buffer } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ImageDrag {
  @State targetImage1: string | PixelMap | null = null;
  @State targetImage2: string | PixelMap | null = null;
  @State targetImage3: string | PixelMap | null = null;
  context: Context | undefined = this.getUIContext().getHostContext();
  filesDir = this.context?.filesDir;

  public async createPixelMap(pixelMap: unifiedDataChannel.SystemDefinedPixelMap): Promise<image.PixelMap | null> {
    let pixelMapWidth: number = (pixelMap.details?.width ?? -1) as number;
    let pixelMapHeight: number = (pixelMap.details?.height ?? -1) as number;
    let pixelMapPixelFormat: image.PixelMapFormat =
      (pixelMap.details?.['pixel-format'] ?? image.PixelMapFormat.UNKNOWN) as image.PixelMapFormat;
    let itemPixelMapData: Uint8Array = pixelMap.rawData;
    const opts: image.InitializationOptions = {
      editable: false, pixelFormat: pixelMapPixelFormat, size: {
        height: pixelMapHeight,
        width: pixelMapWidth
      }
    };
    const buffer: ArrayBuffer = itemPixelMapData.buffer.slice(itemPixelMapData.byteOffset,
      itemPixelMapData.byteLength + itemPixelMapData.byteOffset);
    try {
      let pixelMap: image.PixelMap = await image.createPixelMap(buffer, opts);
      return pixelMap;
    } catch (err) {
      console.error('dragtest--> getPixelMap', err);
      return null;
    }
  }

  build() {
    Column() {
      Flex({ direction: FlexDirection.Row, justifyContent: FlexAlign.Center }) {
        // 在线图片资源拖出
        Column() {
          Text('Online Image').fontSize(14)
          Image('https://www.example.com/xxx.png') // 请填写一个具体的网络图片地址
            .objectFit(ImageFit.Contain)
            .draggable(true)
            .onDragStart(() => {
            })
            .width(100)
            .height(100)
        }
        .border({
          width: 2,
          color: Color.Gray,
          radius: 5,
          style: BorderStyle.Dotted
        })
        .alignItems(HorizontalAlign.Center).justifyContent(FlexAlign.Center)

        // 本地图片资源拖出
        Column() {
          Text('Local Image').fontSize(14)
          // $r('app.media.example')需要替换为开发者所需的图像资源文件
          Image($r('app.media.example'))
            .objectFit(ImageFit.Contain)
            .draggable(true)
            .onDragStart(() => {
            })
            .width(100)
            .height(100)
        }
        .border({
          width: 2,
          color: Color.Gray,
          radius: 5,
          style: BorderStyle.Dotted
        })
        .alignItems(HorizontalAlign.Center).justifyContent(FlexAlign.Center)

        // PixelMap拖出
        Column() {
          Text('PixelMap').fontSize(14)
          // $r('app.media.example')需要替换为开发者所需的图像资源文件
          Image(this.context?.resourceManager.getDrawableDescriptor($r('app.media.example').id).getPixelMap())
            .objectFit(ImageFit.Contain)
            .draggable(true)
            .onDragStart(() => {
            })
            .width(100)
            .height(100)
        }
        .border({
          width: 2,
          color: Color.Gray,
          radius: 5,
          style: BorderStyle.Dotted
        })
        .alignItems(HorizontalAlign.Center).justifyContent(FlexAlign.Center)
      }

      // 落入数据类型为Image
      Text('Data type is Image').fontSize(14).margin({ top: 10 })
      Column() {
        Image(this.targetImage1)
          .objectFit(ImageFit.Contain)
          .width('70%')
          .height('70%')
          .allowDrop([uniformTypeDescriptor.UniformDataType.IMAGE])
          .onDrop((event: DragEvent, extraParams: string) => {
            if (extraParams === null || extraParams === undefined) {
              return;
            }
            // 通过extraParams获取图片
            let arr: Record<string, object> = JSON.parse(extraParams) as Record<string, object>;
            let uri = arr['extraInfo'];
            if (typeof uri == 'string') {
              this.targetImage1 = uri;
              try {
                request.downloadFile(this.context, {
                  url: uri,
                  filePath: this.filesDir + '/example.png'
                }).then((downloadTask: request.DownloadTask) => {
                  let file = fileIo.openSync(this.filesDir + '/example.png', fileIo.OpenMode.READ_WRITE);
                  let arrayBuffer = new ArrayBuffer(1024);
                  let readLen = fileIo.readSync(file.fd, arrayBuffer);
                  let buf = buffer.from(arrayBuffer, 0, readLen);
                  console.info(`The content of file: ${buf.toString()}`);
                  fileIo.closeSync(file);
                });
              } catch (error) {
              }
            }
          })
      }
      .width('70%')
      .height('25%')
      .border({
        width: 2,
        color: Color.Gray,
        radius: 5,
        style: BorderStyle.Dotted
      })
      .alignItems(HorizontalAlign.Center)
      .justifyContent(FlexAlign.Center)

      Column() {
        Image(this.targetImage2)
          .objectFit(ImageFit.Contain)
          .width('70%')
          .height('70%')
          .allowDrop([uniformTypeDescriptor.UniformDataType.IMAGE])
          .onDrop((event: DragEvent, extraParams: string) => {
            // 通过uniformTypeDescriptor获取图片
            let data: UnifiedData = event.getData();
            let records: Array<unifiedDataChannel.UnifiedRecord> = data.getRecords();
            if (records[0].getType() === uniformTypeDescriptor.UniformDataType.IMAGE) {
              let image: unifiedDataChannel.Image = records[0] as unifiedDataChannel.Image;
              this.targetImage2 = image.imageUri;
            }
          })
      }
      .width('70%')
      .height('25%')
      .border({
        width: 2,
        color: Color.Gray,
        radius: 5,
        style: BorderStyle.Dotted
      })
      .alignItems(HorizontalAlign.Center)
      .justifyContent(FlexAlign.Center)

      // 落入数据类型为PixelMap
      Text('Data type is PixelMap').fontSize(14).margin({ top: 10 })
      Column() {
        Image(this.targetImage3)
          .objectFit(ImageFit.Contain)
          .width('70%')
          .height('70%')
          .allowDrop([uniformTypeDescriptor.UniformDataType.OPENHARMONY_PIXEL_MAP])
          .onDrop(async (event: DragEvent, extraParams: string) => {
            // 通过uniformTypeDescriptor获取图片
            let data: UnifiedData = event.getData();
            let records: Array<unifiedDataChannel.UnifiedRecord> = data.getRecords();
            if (records[0].getType() === uniformTypeDescriptor.UniformDataType.OPENHARMONY_PIXEL_MAP) {
              let record: unifiedDataChannel.SystemDefinedPixelMap =
                records[0] as unifiedDataChannel.SystemDefinedPixelMap;
              this.targetImage3 = await this.createPixelMap(record);

              // 落盘到本地
              const imagePackerApi = image.createImagePacker();
              let packOpts: image.PackingOption = { format: 'image/jpeg', quality: 98 };
              const path: string = this.context?.cacheDir + "/pixel_map.jpg";
              let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
              imagePackerApi.packToFile(this.targetImage3, file.fd, packOpts).then(() => {
                // 直接打包进文件
                fileIo.closeSync(file);
              }).catch((error: BusinessError) => {
                fileIo.closeSync(file);
                console.error('Failed to pack the image. And the error is: ' + error);
              });
            }
          })
      }
      .width('70%')
      .height('25%')
      .border({
        width: 2,
        color: Color.Gray,
        radius: 5,
        style: BorderStyle.Dotted
      })
      .alignItems(HorizontalAlign.Center)
      .justifyContent(FlexAlign.Center)

    }.width('100%').height('100%')
  }
}
```

### 示例8（设置图片拖拽震动）

从API version 18开始，示例8通过设置[enableHapticFeedback](arkts-arkui-common-comp-draginteractionoptions-i.md)实现图片拖拽的震动效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct DragPreviewDemo {
  @Builder
  menuBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('menu item 1')
        .fontSize(15)
        .width(100)
        .height(40)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Pink)
      Divider()
        .height(5)
      Text('menu item 2')
        .fontSize(15)
        .width(100)
        .height(40)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Pink)
    }
    .width(100)
  }

  build() {
    Row() {
      Column() {
        // $r('app.media.app_icon')需要替换为开发者所需的图像资源文件
        Image($r('app.media.app_icon'))
          .width('30%')
          .draggable(true)
          .dragPreviewOptions({},
            { isMultiSelectionEnabled: true, defaultAnimationBeforeLifting: true, enableHapticFeedback: true })
          .bindContextMenu(this.menuBuilder, ResponseType.LongPress)
          .onDragStart(() => {
            console.info('Image onDragStart');
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例9（自定义预览图）

从API version 15开始，示例9通过配置[onlyForLifting](./ts-universal-events-drag-drop.md#previewconfiguration15)实现自定义预览图，仅用于浮起效果以及配置[isLiftingDisabled](arkts-arkui-common-comp-draginteractionoptions-i.md)实现禁用浮起效果。

自定义预览图用于浮起效果。



自定义预览图禁用浮起效果。



```TypeScript
// xxx.ets
@Entry
@Component
struct LiftingExampleDemo {
  @Builder
  dragPreviewBuilder() {
    Column() {
      Text('dragPreview builder')
        .width(150)
        .height(50)
        .fontSize(20)
        .borderRadius(10)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Green)
    }
  }

  @Builder
  menuBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('menu 1')
        .fontSize(25)
        .width(200)
        .height(60)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Green)
      Divider()
        .height(5)
      Text('menu 2')
        .fontSize(25)
        .width(200)
        .height(60)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Green)
    }
    .width(100)
  }

  build() {
    Column() {
      Column() {
        Text('禁用浮起效果')
          .fontSize(30)
          .height(30)
          .backgroundColor('#FFFFFF')
          .margin({ top: 30 })
        // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件
        Image($r('app.media.startIcon'))
          .width('40%')
          .draggable(true)
          .margin({ top: 15 })
          .bindContextMenu(this.menuBuilder, ResponseType.LongPress)
          .onDragStart(() => {
          })
          .dragPreviewOptions({}, {
            isLiftingDisabled: true
          })
          .dragPreview(this.dragPreviewBuilder, {
            onlyForLifting: true,
            delayCreating: true
          })
      }.width('100%')

      Column() {
        Text('仅用于浮起效果')
          .fontSize(30)
          .height(30)
          .backgroundColor('#FFFFFF')
          .margin({ top: 80 })
        // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件
        Image($r('app.media.startIcon'))
          .width('40%')
          .draggable(true)
          .margin({ top: 15 })
          .onDragStart(() => {
          })
          .dragPreviewOptions({}, {
            isLiftingDisabled: false
          })
          .dragPreview(this.dragPreviewBuilder, {
            onlyForLifting: true,
            delayCreating: true
          })
      }.width('100%')
    }.height('100%')
  }
}
```

### 示例10（以拖拽预览图初始尺寸计算跟手点位置）

从API version 19开始，示例10通过配置[DragPreviewMode](#dragpreviewmode11枚举说明)为ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW实现基于最终拖拽预览图的原始尺寸来计算拖拽过程中跟手点位置。当设置[DragPreviewMode](#dragpreviewmode11枚举说明)为ENABLE_MULTI_TILE_EFFECT时，该属性不生效。



```TypeScript
@Entry
@Component
struct Index {
  // $r('app.media.app_icon')需要替换为开发者所需的图像资源文件
  private iconStr: ResourceStr = $r('app.media.app_icon')

  @Builder
  myPreview() {
    // $r('app.media.image')需要替换为开发者所需的图像资源文件
    Image($r('app.media.image'))
      .width(100)
      .height(100)
  }

  @Builder
  myMenuPreview() {
    Column() {
      // $r('app.media.image')需要替换为开发者所需的图像资源文件
      Image($r('app.media.image'))
        .width(100)
        .height(100)
    }
    .backgroundColor(Color.Green)
    .width(300)
    .height(300)
  }

  @Builder
  myMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: '菜单选项' })
      MenuItem({ startIcon: this.iconStr, content: '菜单选项' })
    }
  }

  build() {
    NavDestination() {
      Scroll() {
        Column() {
          Text('no ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW')
          // $r('app.media.image')需要替换为开发者所需的图像资源文件
          Image($r('app.media.image'))
            .width(200)
            .height(200)
            .bindContextMenu(this.myMenu, ResponseType.LongPress, {
              preview: this.myPreview
            })
            .dragPreview(this.myMenuPreview)
            .draggable(true)

          Text('ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW')
          // $r('app.media.image')需要替换为开发者所需的图像资源文件
          Image($r('app.media.image'))
            .width(200)
            .height(200)
            .bindContextMenu(this.myMenu, ResponseType.LongPress, {
              preview: this.myPreview
            })
            .dragPreview(this.myMenuPreview)
            .draggable(true)
            .dragPreviewOptions({
              mode: [DragPreviewMode.ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW]
            })
        }.width('100%')
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例11（长按浮起预览图与拖拽预览图过渡动效）

从API version 19开始，示例11通过配置[DraggingSizeChangeEffect](#draggingsizechangeeffect19枚举说明)实现不同拖拽过渡效果。



```TypeScript
@Entry
@Component
struct Index {
  // $r('app.media.app_icon')需要替换为开发者所需的图像资源文件
  private iconStr: ResourceStr = $r('app.media.app_icon');

  @Builder
  myPreview() {
    // $r('app.media.image')需要替换为开发者所需的图像资源文件
    Image($r('app.media.image'))
      .width(200)
      .height(200)
  }

  @Builder
  myMenuPreviewSame() {
    Column() {
      // $r('app.media.image')需要替换为开发者所需的图像资源文件
      Image($r('app.media.image'))
        .width(300)
        .height(300)
    }
  }

  @Builder
  myMenuPreview() {
    Column() {
      // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件
      Image($r('app.media.startIcon'))
        .width(300)
        .height(300)
    }
  }

  @Builder
  myMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: '菜单选项' })
      MenuItem({ startIcon: this.iconStr, content: '菜单选项' })
    }
  }

  build() {
    Column() {
      Text('sizeChangeEffect: SIZE_TRANSITION，长按弹出菜单，拖拽移动后菜单预览图过渡到预览图，有缩放无叠加效果')
        .margin({ top: 10 })
      // $r('app.media.image')需要替换为开发者所需的图像资源文件
      Image($r('app.media.image'))
        .width(200)
        .height(200)
        .bindContextMenu(this.myMenu, ResponseType.LongPress, {
          preview: this.myMenuPreviewSame
        })
        .dragPreview(this.myPreview)
        .dragPreviewOptions({
          sizeChangeEffect: DraggingSizeChangeEffect.SIZE_TRANSITION
        })
        .draggable(true)

      Text('sizeChangeEffect: SIZE_CONTENT_TRANSITION，长按弹出菜单，拖拽移动后菜单预览图和拖拽预览图两层叠加过渡')
        .margin({ top: 10 })
      // $r('app.media.image')需要替换为开发者所需的图像资源文件
      Image($r('app.media.image'))
        .width(200)
        .height(200)
        .bindContextMenu(this.myMenu, ResponseType.LongPress, {
          preview: this.myMenuPreview
        })
        .dragPreview(this.myPreview)
        .dragPreviewOptions({
          sizeChangeEffect: DraggingSizeChangeEffect.SIZE_CONTENT_TRANSITION
        })
        .draggable(true)
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例12（设置自定义组件落入）

从API version 23开始，示例12通过组件的[onDragStart](ts-universal-events-drag-drop.md#ondragstart)接口传递其类型，并在目标组件的[allowDrop](arkts-arkui-common-comp-commonmethod-c.md#allowdrop)属性中设置允许该类型落入，即可实现自定义组件的拖拽落入功能。



```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@Component
struct CustomExample {
  // 用于存储已放置的组件信息
  @State droppedItems: Array<string> = []

  build() {
    Column() {
      // 标题
      Text('自定义组件拖拽落入')
        .fontSize(25)
        .fontWeight(FontWeight.Bold)
        .margin(10)

      // 拖拽区域和放置区域的容器
      Row() {
        // 左侧 - 拖拽起始区域
        Column() {
          Text('拖拽源区域')
            .fontSize(18)
            .fontWeight(FontWeight.Medium)
            .margin(10)

          // 自定义组件 - 可拖拽
          CustomCard({ title: '自定义卡片', color: Color.Blue })
            .draggable(true)
            .onDragStart((event: DragEvent) => {
              // 构造符合UnifiedData类型的数据
              let customCardData: Record<string, string> = {
                'uniformDataType': 'custom.card',
                'value': '自定义卡片'
              };
              let unifiedRecord = new unifiedDataChannel.UnifiedRecord('custom.card', customCardData);
              let unifiedData = new unifiedDataChannel.UnifiedData(unifiedRecord);
              event.setData(unifiedData);
            })
        }
        .backgroundColor(Color.White)
        .border({ color: '#ff0e0303', width: 1 })
        .width('40%')
        .height(300)

        // 右侧 - 放置区域
        Column() {
          Text('放置区域')
            .fontSize(18)
            .fontWeight(FontWeight.Medium)
            .margin(10)

          // 放置区域内容
          if (this.droppedItems.length === 0) {
            Text('将组件拖到此处')
              .fontSize(16)
              .opacity(0.6)
          } else {
            // 显示已放置的组件
            ForEach(this.droppedItems, (item: string) => {
              CustomCard({ title: item, color: Color.Blue })
            }, (item: string) => item)
          }
        }
        .backgroundColor(Color.White)
        .border({ color: '#ff0e0303', width: 1 })
        .width('40%')
        .height(300)
        // 允许放置的类型 - 字符串数组形式
        .allowDrop(['custom.card'])
        .onDrop((event: DragEvent) => {
          console.info('setData onDrop success');
          let data = event.getData();
          let arr: Array<unifiedDataChannel.UnifiedRecord> = data.getRecords();
          if (arr.length > 0) {
            if (arr[0].getTypes()[0] === 'custom.card') {
              let customCardData = arr[0].getValue() as Record<string, string>;
              this.droppedItems.push(customCardData.value);
            }
          }
        })
      }
      .justifyContent(FlexAlign.SpaceAround)
      .width('100%')
      .height('70%')

      // 操作说明
      Text('操作说明：长按左侧卡片并拖拽到右侧区域')
        .fontSize(14)
        .opacity(0.7)
        .margin(10)
    }
    .width('100%')
    .height('65%')
    .backgroundColor('#f8f9fa')
  }
}

// 自定义卡片组件
@Component
struct CustomCard {
  title: string = '默认标题';
  color: Color = Color.Gray;

  build() {
    Column() {
      Text(this.title)
        .fontSize(16)
        .fontColor(Color.White)
        .fontWeight(FontWeight.Medium)
        .margin(5)

      Text('这是一个自定义组件')
        .fontColor(Color.White)
        .fontSize(14)
        .opacity(0.7)
    }
    .backgroundColor(this.color)
    .borderRadius(12)
    .width(120)
    .height(100)
  }
}
```

### 示例13（设置背板图材质效果）

该示例通过配置[ImageModifier](arkts-arkui-common-comp-imagemodifier-t.md)中的[systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial)属性，设置拖拽背板的材质效果。

从API版本26.0.0开始，[DragPreviewOptions](#dragpreviewoptions11-1)接口中的modifier参数新增支持[systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial)属性。

```TypeScript
// xxx.ets
import { ImageModifier } from '@kit.ArkUI';
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct DragPreviewMaterialDemo {
  @State materialIndex: number = 0;
  @State materialName: string = 'ULTRA_THIN';
  // 材质样式列表
  @State materialList: uiMaterial.ImmersiveStyle[] = [
    uiMaterial.ImmersiveStyle.ULTRA_THIN,
    uiMaterial.ImmersiveStyle.THIN,
    uiMaterial.ImmersiveStyle.REGULAR,
    uiMaterial.ImmersiveStyle.THICK,
    uiMaterial.ImmersiveStyle.ULTRA_THICK
  ]
  @State materialNames: string[] = [
    'ULTRA_THIN', 'THIN', 'REGULAR', 'THICK', 'ULTRA_THICK'
  ]

  build() {
    Row() {
      Column() {
        Text('当前材质样式：' + this.materialName)
          .fontSize(16)
          .margin({ bottom: 10 })

        Button('切换材质样式')
          .onClick(() => {
            this.materialIndex++;
            if (this.materialIndex > this.materialList.length - 1) {
              this.materialIndex = 0;
            }
            this.materialName = this.materialNames[this.materialIndex];
          })
          .margin({ bottom: 20 })

        Column() {
          Text('材质效果')
            .fontSize(20)
            .fontColor(Color.White)
            .margin({ top: 30, bottom: 10 })
          Text('拖拽我查看效果')
            .fontSize(14)
            .fontColor(Color.White)
        }
        .width(150)
        .height(150)
        .backgroundColor('rgba(100, 150, 255, 0.3)')
        .justifyContent(FlexAlign.Center)
        .draggable(true)
        .onDragStart((event: DragEvent) => {
        })
        .dragPreviewOptions({
          modifier: new ImageModifier().systemMaterial(
            new uiMaterial.ImmersiveMaterial({
              style: this.materialList[this.materialIndex]
            })
          ) as ImageModifier
        })

        Text('操作说明：长按方块并拖拽\n查看不同材质效果')
          .fontSize(14)
          .fontColor(Color.Gray)
          .margin({ top: 20 })
          .textAlign(TextAlign.Center)
      }
      .width('100%')
      .height('100%')
      .padding(20)
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#f5f5f5')
  }
}
```

### 示例1（if else范式下的共享元素实现）

该示例主要演示if else范式下的共享元素效果集成。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State isShow: boolean = false;

  build() {
    Stack({ alignContent: Alignment.Center }) {
      if (this.isShow) {
        // 图片使用Resource资源，需用户自定义
        Image($r('app.media.pic'))
          .autoResize(false)
          .clip(true)
          .width(300)
          .height(400)
          .offset({ y: 100 })
          .geometryTransition('picture')
          .transition(TransitionEffect.OPACITY)
      } else {
        // geometryTransition此处绑定的是容器，那么容器内的子组件需设为相对布局跟随父容器变化，
        // 套多层容器为了说明相对布局约束传递
        Column() {
          Column() {
            // 图片使用Resource资源，需用户自定义
            Image($r('app.media.icon'))
              .width('100%').height('100%')
          }.width('100%').height('100%')
        }
        .width(80)
        .height(80)
        // geometryTransition会同步圆角，但仅限于geometryTransition绑定处，此处绑定的是容器
        // 则对容器本身有圆角同步而不会操作容器内部子组件的borderRadius
        .borderRadius(20)
        .clip(true)
        .geometryTransition('picture')
        // transition保证组件离场不被立即析构，可设置其他转场效果
        .transition(TransitionEffect.OPACITY)
      }
    }
    .onClick(() => {
      this.getUIContext().animateTo({ duration: 1000 }, () => {
        this.isShow = !this.isShow;
      });
    })
  }
}
```

### 示例2（if范式下使用follow实现跟随效果）

该示例主要演示if范式下使用follow参数实现不下树的组件的跟随效果。

```TypeScript
// xxx.ets
const FOLLOW_TRUE_ID: string = 'follow_true_id';
const FOLLOW_FALSE_ID: string = 'follow_false_id';

@Entry
@Component
struct Index {
  @State isFollow: boolean = false;
  @State isShow: boolean = false;
  @State geometryId: string = '';

  @Builder
  myBuilder() {
    Column() {
      Column()
        .backgroundColor('#ff663399')
        .size({ width: 100, height: 100 })
        .position({ x: 200, y: 500 })
        .borderRadius(25)
        .clip(true)
        .geometryTransition(this.geometryId)
        .transition(TransitionEffect.OPACITY)
    }
    .size({ width: '100%', height: '100%' })
    .backgroundColor("#33000000")
    .transition(TransitionEffect.OPACITY)
  }

  build() {
    Stack() {
      if (this.isFollow) {
        Column()
          .backgroundColor('#ff103460')
          .size({ width: 100, height: 100 })
          .position({ x: 30, y: 30 })
          .borderRadius(50)
          // follow为true时，一镜到底转场期间该组件会下树做跟随效果
          .geometryTransition(FOLLOW_TRUE_ID, { follow: true })
          .transition(TransitionEffect.OPACITY)
      } else {
        Column()
          .backgroundColor('#ff103460')
          .size({ width: 100, height: 100 })
          .position({ x: 30, y: 30 })
          .borderRadius(50)
          // follow为false时，一镜到底转场期间该组件会留在原地不做跟随
          .geometryTransition(FOLLOW_FALSE_ID, { follow: false })
          .transition(TransitionEffect.OPACITY)
      }

      Button('follow: ' + (this.isFollow ? 'true' : 'false'))
        .onClick(() => {
          this.isFollow = !this.isFollow;
          this.geometryId = this.isFollow ? FOLLOW_TRUE_ID : FOLLOW_FALSE_ID;
        })
        .size({ width: 200, height: 50 })
        .backgroundColor('#ff6b879b')
    }
    .size({ width: '100%', height: '100%' })
    .bindContentCover(this.isShow, this.myBuilder(), {
      // 模态页面实现一镜到底动效时，需要设置modalTransition为ModalTransition.NONE
      modalTransition: ModalTransition.NONE,
      onWillDismiss: () => {
        // 侧滑关闭模态页面时，通过animateTo创造动画环境实现一镜到底动效
        this.getUIContext().animateTo({ duration: 350 }, () => {
          this.isShow = !this.isShow;
        });
      }
    })
    .onClick(() => {
      // 点击弹出模态页
      this.getUIContext().animateTo({ duration: 350 }, () => {
        this.isShow = !this.isShow;
      });
    })
  }
}
```

该示例通过按钮控制组件的挂载和卸载，触发onAttach和onDetach事件。

```TypeScript
// xxx.ets
@Entry
@Component
struct AppearExample {
  @State isShow: boolean = true;
  @State changeAppear: string = '点我卸载挂载组件';
  private myText: string = 'Text for onAppear';

  build() {
    Column() {
      Button(this.changeAppear)
        .onClick(() => {
          this.isShow = !this.isShow;
        }).margin(15)
      if (this.isShow) {
        Text(this.myText).fontSize(26).fontWeight(FontWeight.Bold)
          .onAttach(() => {
            this.getUIContext().getPromptAction().showToast({
              message: 'The text is shown',
              duration: 2000,
              bottom: 500
            })
          })
          .onDetach(() => {
            this.getUIContext().getPromptAction().showToast({
              message: 'The text is hidden',
              duration: 2000,
              bottom: 500
            })
          })
      }
    }.padding(30).width('100%')
  }
}
```

### 示例1（使用前景色设置）

该示例主要演示通过foregroundColor设置前景色。



```TypeScript
// xxx.ets
@Entry
@Component
struct ForegroundColorExample {
  build() {
    Column({ space: 100 }) {
      // 绘制一个直径为150的圆，默认填充色为黑色
      Circle({ width: 150, height: 200 }).margin(20)
      // 绘制一个直径为150的圆，设置前景色为橙色
      Circle({ width: 150, height: 200 }).foregroundColor(Color.Orange)
    }.width('100%').backgroundColor(Color.Gray)
  }
}
```

### 示例2（设置前景色为组件背景色反色）

该示例通过[ColoringStrategy](ts-appendix-enums.md#coloringstrategy10).INVERT将前景色设置为背景色反色。



```TypeScript
// xxx.ets
@Entry
@Component
struct ColoringStrategyExample {
  build() {
    Column({ space: 100 }) {
      // 绘制一个直径为150的圆，默认填充色为黑色
      Circle({ width: 150, height: 200 })
      // 绘制一个直径为150的圆，设置前景色为组件背景色的反色
      Circle({ width: 150, height: 200 })
        .backgroundColor(Color.Black)
        .foregroundColor(ColoringStrategy.INVERT)
    }.width('100%')
  }
}
```

### 示例3（前景色未继承父组件）

该示例主要演示组件同时设置前景色和背景色与只设置背景色的效果对比。

```TypeScript
// xxx.ets
@Entry
@Component
struct ForegroundColorInherit {
  build() {
    Column() {
      Button('设置前景色为橙色').fontSize(20).foregroundColor(Color.Orange).backgroundColor(Color.Gray)
      Divider()
      Button('未设置前景色继承自父组件').fontSize(20).backgroundColor(Color.Gray)
    }.foregroundColor(Color.Pink)
  }
}
```

### 示例1（通过responseRegion接口设置触摸热区）

该示例通过responseRegion设置按钮的触摸热区以响应点击事件。



```TypeScript
// xxx.ets
@Entry
@Component
struct TouchTargetExample {
  @State text: string = '';

  build() {
    Column({ space: 20 }) {
      Text("{x:0,y:0,width:'50%',height:'100%'}")
      // 热区宽度为按钮的一半，点击button1右半部无响应
      Button('button1')
        .responseRegion({
          x: 0,
          y: 0,
          width: '50%',
          height: '100%'
        })
        .onClick(() => {
          this.text = 'button1 clicked';
        })

      // 为一个组件添加多个热区
      Text("[{x:'100%',y:0,width:'50%',height:'100%'}," +
        "\n{ x: 0, y: 0, width: '50%', height: '100%' }]")
      Button('button2')
        .responseRegion([
          {
            x: '100%',
            y: 0,
            width: '50%',
            height: '100%'
          }, // 第一个热区宽度为按钮的一半，且右移一个按钮宽度，点击button2右边按钮宽度一半的区域，点击事件生效
          {
            x: 0,
            y: 0,
            width: '50%',
            height: '100%'
          } // 第二个热区宽度为按钮的一半，点击button2左半部，点击事件生效
        ])
        .onClick(() => {
          this.text = 'button2 clicked';
        })
      // 热区大小为整个按钮，且下移一个按钮高度，点击button3下方按钮大小区域，点击事件生效
      Text("{x:0,y:'100%',width:'100%',height:'100%'}")
      Button('button3')
        .responseRegion({
          x: 0,
          y: '100%',
          width: '100%',
          height: '100%'
        })
        .onClick(() => {
          this.text = 'button3 clicked';
        })

      Text(this.text).margin({ top: 50 })
    }.width('100%').margin({ top: 10 })
  }
}
```

### 示例2（通过responseRegionList接口设置触摸热区）

该示例通过[responseRegionList](arkts-arkui-common-comp-commonmethod-c.md#responseregionlist)设置按钮的触摸热区以响应点击事件。

从API version 22开始，新增responseRegionList接口。



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct TouchTargetExample {
  @State text: string = '';

  build() {
    Column({ space: 20 }) {
      Text('left part of button1')
      // 热区宽度为按钮的一半，点击button1右半部无响应
      Button('button1')
        .responseRegionList([{
          x: LengthMetrics.vp(0),
          y: LengthMetrics.vp(0),
          width: LengthMetrics.percent(0.5),
          height: LengthMetrics.percent(1),
        }])
        .onClick(() => {
          this.text = 'button1 clicked';
        })

      // 热区一的大小为整个按钮，且右移一个按钮宽度，点击button2右边按钮大小区域，点击事件生效
      // 热区二的大小为整个按钮，且下移一个按钮高度，鼠标点击button2下方按钮大小区域，点击事件生效
      Text('one button size right of button2,' + '\n one button size below button2')
      Button('button2')
        .responseRegionList([{
          x: LengthMetrics.percent(1),
          y: LengthMetrics.vp(0),
          width: LengthMetrics.percent(1),
          height: LengthMetrics.percent(1),
        }, {
          tool: ResponseRegionSupportedTool.MOUSE,
          x: LengthMetrics.vp(0),
          y: LengthMetrics.percent(1),
          width: 'calc(100% + 0vp)',
          height: 'calc(100% - 0px)',
        }])
        .onClick(() => {
          this.text = 'button2 clicked';
        })

      Text(this.text).margin({ top: 50 })
    }.width('100%').margin({ top: 10 })
  }
}
```

### 示例3（设置鼠标的触摸热区以响应点击事件）

该示例通过[mouseResponseRegion](arkts-arkui-common-comp-commonmethod-c.md#mouseresponseregion)设置鼠标的触摸热区以响应点击事件。

```TypeScript
// xxx.ets
@Entry
@Component
struct MouseResponseRegionExample {
  @State clickInfo: string = '点击热区触发事件';

  build() {
    Column({ space: 30 }) {
      // 示例1：单个热区（仅按钮左半部分响应鼠标点击）
      Text('热区：按钮左半区域（点击左半才触发）')
        .fontSize(14)
      Button('Button1（左半热区）')
        .width(200)
        .height(60)
        // 鼠标热区：仅按钮左半部分（x/y相对组件自身，宽度50%）
        .mouseResponseRegion({
          // 热区相对组件的X坐标（左上角为原点）
          x: 0,
          // 热区相对组件的Y坐标
          y: 0,
          // 热区宽度（按钮的50%）
          width: '50%',
          // 热区高度（按钮的100%）
          height: '100%'
        })
        .onClick(() => {
          this.clickInfo = 'Button1 左半热区被点击';
        })
      // 示例2：多个热区（按钮左半 + 按钮下方区域都响应）
      Text('热区：按钮左半 + 按钮下方区域（点击两处都触发）')
        .fontSize(14)
      Button('Button2（多热区）')
        .width(200)
        .height(60)
        // 鼠标热区：数组形式，包含2个独立热区
        .mouseResponseRegion([
          // 热区1：按钮左半部分
          {
            x: 0,
            y: 0,
            width: '50%',
            height: '100%'
          },
          // 热区2：按钮正下方区域（y=100%表示按钮底部，高度60vp）
          {
            x: 0,
            y: '100%',
            width: '100%',
            height: 60
          }
        ])
        .onClick(() => {
          this.clickInfo = 'Button2 任一热区被点击';
        })
      // 示例3：热区在按钮外部（按钮右侧空白处响应）
      Text('热区：按钮右侧外部（点击按钮右边空白处触发）')
        .fontSize(14)
      Button('Button3（右侧外热区）')
        .width(200)
        .height(60)
        // 鼠标热区：按钮右侧外部区域（x=100%表示按钮右边缘）
        .mouseResponseRegion({
          // 热区X坐标：按钮右边缘
          x: '100%',
          y: 0,
          // 热区宽度80vp
          width: 80,
          height: '100%'
        })
        .onClick(() => {
          this.clickInfo = 'Button3 右侧外热区被点击';
        })
      // 显示点击结果
      Text(this.clickInfo)
        .fontSize(16)
        .margin({ top: 20 })
    }
    .width('100%')
    .height('100%')
    // 整体居中显示
    .justifyContent(FlexAlign.Center)
  }
}
```

该示例主要演示不同组件的点击回弹效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct ToggleExample {
  build() {
    Column({ space: 10 }) {
      Text('type: Switch').fontSize(12).fontColor(0xcccccc).width('90%')
      Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
        Toggle({ type: ToggleType.Switch, isOn: false })
          .clickEffect({ level: ClickEffectLevel.LIGHT })
          .selectedColor('#007DFF')
          .switchPointColor('#FFFFFF')
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })

        Toggle({ type: ToggleType.Switch, isOn: true })
          .clickEffect({ level: ClickEffectLevel.LIGHT, scale: 0.5 })
          .selectedColor('#007DFF')
          .switchPointColor('#FFFFFF')
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })
      }

      Text('type: Checkbox').fontSize(12).fontColor(0xcccccc).width('90%')
      Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
        Toggle({ type: ToggleType.Checkbox, isOn: false })
          .clickEffect({ level: ClickEffectLevel.MIDDLE })
          .size({ width: 20, height: 20 })
          .selectedColor('#007DFF')
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })

        Toggle({ type: ToggleType.Checkbox, isOn: true })
          .clickEffect({ level: ClickEffectLevel.MIDDLE, scale: 0.5 })
          .size({ width: 20, height: 20 })
          .selectedColor('#007DFF')
          .onChange((isOn: boolean) => {
            console.info('Component status:' + isOn);
          })
      }

      Text('type: Button').fontSize(12).fontColor(0xcccccc).width('90%')
      Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
        Toggle({ type: ToggleType.Button, isOn: false }) {
          Text('status button').fontColor('#182431').fontSize(12)
        }.width(106)
        .clickEffect({ level: ClickEffectLevel.HEAVY })
        .selectedColor('rgba(0,125,255,0.20)')
        .onChange((isOn: boolean) => {
          console.info('Component status:' + isOn);
        })

        Toggle({ type: ToggleType.Button, isOn: true }) {
          Text('status button').fontColor('#182431').fontSize(12)
        }.width(106)
        .clickEffect({ level: ClickEffectLevel.HEAVY, scale: 0.5 })
        .selectedColor('rgba(0,125,255,0.20)')
        .onChange((isOn: boolean) => {
          console.info('Component status:' + isOn);
        })
      }
    }.width('100%').padding(24)
  }
}
```

### 示例1（为组件添加图形变换效果）

该示例通过[rotate](#rotate)、[translate](#translate)、[scale](#scale)、[transform](#transform)为组件添加旋转、平移、缩放、变换矩阵效果。



```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct TransformExample {
  build() {
    Column() {
      Text('rotate').width('90%').fontColor(0xCCCCCC).padding(15).fontSize(14)
      Row()
        .rotate({
          x: 0,
          y: 0,
          z: 1,
          centerX: '50%',
          centerY: '50%',
          angle: 300
        }) // 组件以矢量(0,0,1)为旋转轴，绕中心点顺时针旋转300度
        .width(100).height(100).backgroundColor(0xAFEEEE)

      Text('translate').width('90%').fontColor(0xCCCCCC).padding(10).fontSize(14)
      Row()
        .translate({ x: 100, y: 10 }) // x轴方向平移100，y轴方向平移10
        .width(100)
        .height(100)
        .backgroundColor(0xAFEEEE)
        .margin({ bottom: 10 })

      Text('scale').width('90%').fontColor(0xCCCCCC).padding(15).fontSize(14)
      Row()
        .scale({ x: 2, y: 0.5 }) // 高度缩小一倍，宽度放大一倍，z轴在2D下无效果
        .width(100).height(100).backgroundColor(0xAFEEEE)

      Text('Matrix4').width('90%').fontColor(0xCCCCCC).padding(15).fontSize(14)
      Row()
        .width(100).height(100).backgroundColor(0xAFEEEE)
        .transform(matrix4.identity().translate({ x: 50, y: 50 }).scale({ x: 1.5, y: 1 }).rotate({
          x: 0,
          y: 0,
          z: 1,
          angle: 60
        }))
    }.width('100%').margin({ top: 5 })
  }
}
```

### 示例2（设置旋转视距）

该示例通过[perspective](#rotateoptions对象说明)为组件添加视距效果。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State prep: number = 10;

  build() {
    Row() {
      Column() {
        Stack()
          .width(100)
          .height(100)
          .backgroundColor(Color.Red)
          .rotate({ y: 1, angle: 45, perspective: this.prep })
        Button('change prep')
          .margin({ top: 100 })
          .onClick(() => {
            this.getUIContext()?.animateTo({
              duration: 2000,
              curve: Curve.EaseIn,
              iterations: 1,
              playMode: PlayMode.Normal,
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.prep = 500; // 组件视距从10变换到500
            })
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例3（按中心点旋转）

该示例通过设置[rotate](#rotate)和[transform](#transform)为不同的参数实现相同的旋转效果。



```TypeScript
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)

      Text('Hello2')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          // 绕(100vp,60vp)的锚点旋转90度，rotate或scale的centerX、centerY为组件锚点
          z: 1,
          angle: 90,
          centerX: 100,
          centerY: 60
        })

      Text('Hello3')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .transform(matrix4.identity()
          .rotate({
            // 组件锚点(centerX,centerY)默认为(50%,50%)，即锚点在(50vp,30vp)
            // transform的rotate指定(centerX,centerY)为(50vp,30vp)，相对于在组件本身锚点基础上再额外偏移(50vp,30vp)
            // 此次变换相当于绕(100vp,60vp)旋转，和"Hello2"实现同样的旋转效果
            z: 1,
            angle: 90,
            centerX: this.getUIContext().vp2px(50),
            centerY: this.getUIContext().vp2px(30)
          }))

      Text('Hello4')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .scale({
          // 当设置x或y时，centerX和centerY才能生效
          // 设置组件锚点为(100vp,60vp)
          x: 1,
          y: 1,
          centerX: 100,
          centerY: 60
        }) // transform的rotate不指定centerX、centerY，此次旋转的中心相对于组件本身锚点没有额外偏移
          // 该组件通过scale设置的锚点，绕(100vp,60vp)进行旋转，和"Hello2"实现同样的旋转效果
        .transform(matrix4.identity().rotate({ z: 1, angle: 90 }))
    }.width('100%')
    .height('100%')
  }
}
```

### 示例4（通过transform3D实现图形变换）

从API version 20开始，该示例通过设置[transform3D](arkts-arkui-common-comp-commonmethod-c.md#transform3d)实现图形变换效果。



```TypeScript
import { matrix4 } from '@kit.ArkUI';

// 初始化3D变换矩阵，用于演示transform3D的图形变换效果
let matrix: matrix4.Matrix4Transit = matrix4.init([
  0.53033, 0, -0.53033, 0.00053033,
  0, 0.75, 0, 0,
  0.707107, 0, 0.707107, -0.000707107,
  0, 0, 0, 1
]);

@Entry
@Component
struct Transform3DExample {
  build() {
    Column() {
      Stack() {
        Stack()
          .width(200)
          .height(100)
          .backgroundColor(Color.Grey)
        Stack()
          .width(200)
          .height(100)
          .backgroundColor(Color.Blue)
          .transform3D(matrix)
      }
    }.width('100%')
  }
}
```

### 示例5（按各轴旋转角的方式实现旋转）

从API version 20开始，该示例通过设置rotate的[RotateAngleOptions](#rotateangleoptions20对象说明)参数实现旋转效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Stack()
          .width(100)
          .height(100)
          .backgroundColor(Color.Blue)
          .rotate({ angleZ: -45 })
        Button('rotateAngle')
          .width('40%')
          .margin({ top: 100 })
          .rotate({ angleY: 30, centerX: '90%', perspective: 10 })
        Image($r('app.media.startIcon'))
          .width(200)
          .height(200)
          .rotate({
            angleX: 60,
            angleY: -125,
            angleZ: 75,
            centerX: 100,
            centerZ: 20
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

示例代码为点击图片所在区域跳转页面时，显示共享元素图片的自定义转场动效。

```TypeScript
// xxx.ets
@Entry
@Component
struct SharedTransitionExample {

  build() {
    Column() {
      // $r('app.media.ic_health_heart')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.ic_health_heart')).width(50).height(50).margin({ left: 20, top: 20 })
        .sharedTransition('sharedImage', { duration: 800, curve: Curve.Linear, delay: 100 }) 
    }.width('100%').height('100%').alignItems(HorizontalAlign.Start)
    .onClick(() => {
      this.getUIContext().getRouter().pushUrl({ url: 'pages/PageB' });
    })
  }

  pageTransition() {
    PageTransitionEnter({ type: RouteType.None, duration: 0 })
    PageTransitionExit({ type: RouteType.None, duration: 0 })
  }
}
```

```TypeScript
// PageB.ets
@Entry
@Component
struct PageBExample {
  build() {
    Stack() {
      // $r('app.media.ic_health_heart')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.ic_health_heart')).width(150).height(150)
        .sharedTransition('sharedImage', { duration: 800, curve: Curve.Linear, delay: 100 })
    }.width('100%').height('100%')
  }

  pageTransition() {
    PageTransitionEnter({ type: RouteType.None, duration: 0 })
    PageTransitionExit({ type: RouteType.None, duration: 0 })
  }
}
```

### 示例1（实现沉浸式效果）

该示例通过设置expandSafeArea属性向顶部和底部扩展安全区实现沉浸式效果。



```TypeScript
// xxx.ets
@Entry
@Component
struct SafeAreaExample1 {
  build() {
    Row() {
      Column()
        .width('100%')
        .height('100%')
        // $r('app.media.bg')需要替换为开发者所需的图像资源文件
        .backgroundImage($r('app.media.bg'))
        .backgroundImageSize(ImageSize.Cover)
        .expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM])
    }.height('100%')
  }
}
```

### 示例2（同时设置固定宽高和expandSafeArea属性）

该示例展示了同时设置固定宽高和expandSafeArea属性的效果。

如下图：Column组件扩展至了顶部状态栏[SafeAreaEdge.TOP]，未扩展至底部导航条[SafeAreaEdge.BOTTOM]，扩展后的组件高度维持设置值不变。



```TypeScript
// xxx.ets
@Entry
@Component
struct SafeAreaExample2 {
  @State text: string = ''
  controller: TextInputController = new TextInputController()

  build() {
    Column() {
      TextInput({ text: this.text, placeholder: 'input your word...', controller: this.controller })
        .placeholderFont({ size: 14, weight: 400 })
        .width(320).height(40).offset({y: 120})
        .fontSize(14).fontColor(Color.Black)
        .backgroundColor(Color.White)
    }
    .height('780')
    .width('100%')
    .backgroundColor('rgb(179,217,235)')
    .expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM])
  }
}
```

### 示例3（键盘避让时固定背景图位置）

该示例通过为背景图组件设置expandSafeArea属性，来实现拉起键盘进行避让时，背景图保持不动的效果。



```TypeScript
// xxx.ets
@Entry
@Component
struct SafeAreaExample3 {
  @State text: string = ''
  controller: TextInputController = new TextInputController()

  build() {
    Row() {
      Stack() {
        Column()
          .width('100%')
          .height('100%')
          // $r('app.media.bg')需要替换为开发者所需的图像资源文件
          .backgroundImage($r('app.media.bg'))
          .backgroundImageSize(ImageSize.Cover)
          .expandSafeArea([SafeAreaType.KEYBOARD, SafeAreaType.SYSTEM])
        Column() {
          Button('Set caretPosition 1')
            .onClick(() => {
              this.controller.caretPosition(1)
            })
          TextInput({ text: this.text, placeholder: 'input your word...', controller: this.controller })
            .placeholderFont({ size: 14, weight: 400 })
            .width(320)
            .height(40)
            .offset({ y: 120 })
            .fontSize(14)
            .fontColor(Color.Black)
            .backgroundColor(Color.White)
        }.width('100%').alignItems(HorizontalAlign.Center)
      }
    }.height('100%')
  }
}
```

### 示例4（设置键盘避让模式为压缩）

该示例通过调用setKeyboardAvoidMode设置键盘避让模式为RESIZE模式，实现键盘抬起时page的压缩效果。

```TypeScript
// EntryAbility.ets
import { window, KeyboardAvoidMode } from '@kit.ArkUI';
export default class EntryAbility extends UIAbility{
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      // 设置虚拟键盘抬起时压缩页面大小为减去键盘的高度
      windowStage.getMainWindowSync().getUIContext().setKeyboardAvoidMode(KeyboardAvoidMode.RESIZE);
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```



```TypeScript
// xxx.ets
@Entry
@Component
struct KeyboardAvoidExample1 {
  build() {
    Column() {
      Row()
        .width('100%')
        .height('30%')
        .backgroundColor(Color.Gray)
      TextArea()
        .width('100%')
        .borderWidth(1)
      Text('I can see the bottom of the page')
        .width('100%')
        .textAlign(TextAlign.Center)
        .backgroundColor('rgb(179,217,235)')
        .layoutWeight(1)
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例5（设置键盘避让模式为上抬）

该示例通过调用setKeyboardAvoidMode设置键盘避让模式为OFFSET模式，实现键盘抬起时page的上抬效果。但当输入光标距离屏幕底部的高度大于键盘高度时，page不会抬起，如本例中所示。

```TypeScript
// EntryAbility.ets
import { window, KeyboardAvoidMode } from '@kit.ArkUI';
export default class EntryAbility extends UIAbility{
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      // 设置虚拟键盘抬起时把页面上抬直到露出光标
      windowStage.getMainWindowSync().getUIContext().setKeyboardAvoidMode(KeyboardAvoidMode.OFFSET);
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```



```TypeScript
// xxx.ets
@Entry
@Component
struct KeyboardAvoidExample2 {
  build() {
    Column() {
      Row()
        .width('100%')
        .height('30%')
        .backgroundColor(Color.Gray)
      TextArea()
        .width('100%')
        .borderWidth(1)
      Text('I can see the bottom of the page')
        .width('100%')
        .textAlign(TextAlign.Center)
        .backgroundColor('rgb(179,217,235)')
        .layoutWeight(1)
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例6（切换避让模式）

该示例通过调用setKeyboardAvoidMode来实现OFFSET、RESIZE和NONE模式之间的切换，实现三种不同的键盘避让效果。



```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { KeyboardAvoidMode } from '@kit.ArkUI';

@Entry
@Component
struct KeyboardAvoidExample3 {
  build() {
    Column() {
      Row({space:15}) {
        Button('OFFSET')
          .onClick(() => {
            this.getUIContext().setKeyboardAvoidMode(KeyboardAvoidMode.OFFSET);
            hilog.info(0x0000, 'keyboardAvoidMode: %{public}s', JSON.stringify(this.getUIContext().getKeyboardAvoidMode()));
          })
          .layoutWeight(1)
        Button('RESIZE')
          .onClick(() => {
            this.getUIContext().setKeyboardAvoidMode(KeyboardAvoidMode.RESIZE);
            hilog.info(0x0000, 'keyboardAvoidMode: %{public}s', JSON.stringify(this.getUIContext().getKeyboardAvoidMode()));
          })
          .layoutWeight(1)
        Button('NONE')
          .onClick(() => {
            this.getUIContext().setKeyboardAvoidMode(KeyboardAvoidMode.NONE);
            hilog.info(0x0000, 'keyboardAvoidMode: %{public}s', JSON.stringify(this.getUIContext().getKeyboardAvoidMode()));
          })
          .layoutWeight(1)
      }
      .height('30%')
      .width('100%')
      .backgroundColor(Color.Gray)

      TextArea()
        .width('100%')
        .borderWidth(1)
      
      Text('I can see the bottom of the page')
        .width('100%')
        .textAlign(TextAlign.Center)
        .backgroundColor('rgb(179,217,235)')
        .layoutWeight(1)
      
      TextArea()
        .width('100%')
        .borderWidth(1)
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例7（滚动类容器扩展安全区）

该示例通过在滚动类容器内调用expandSafeArea属性实现沉浸式效果，Scroll内的Swiper可以延伸到状态栏上。



```TypeScript
class SwiperDataSource implements IDataSource {
  private list: Array<Color> = []
  constructor(list: Array<Color>) {
    this.list = list
  }
  totalCount(): number {
    return this.list.length
  }
  getData(index: number): Color {
    return this.list[index]
  }
  registerDataChangeListener(listener: DataChangeListener): void {
  }
  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}
@Entry
@Component
struct ExpandSafeAreaTest {
  private swiperController: SwiperController = new SwiperController()
  private swiperData: SwiperDataSource = new SwiperDataSource([])
  private list: Array<Color> = [
    Color.Pink,
    Color.Blue,
    Color.Green
  ]
  aboutToAppear(): void {
    this.swiperData = new SwiperDataSource(this.list)
  }
  build() {
    Scroll() {
      Column() {
        Swiper(this.swiperController) {
          LazyForEach(this.swiperData, (item: Color, index: number) => {
            Column() {
              Text('banner' + index).fontSize(50).fontColor(Color.White)
            }
            .expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM])
            .width('100%')
            .height(400)
            .backgroundColor(item)
          })
        }
        .loop(true)
        .expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM])
        .clip(false)
        Column(){
          Text('Tab页Content').fontSize(50)
        }.width('100%').height(1000)
        .backgroundColor(Color.Grey)
      }.expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM])
    }
    .clip(false)
    .edgeEffect(EdgeEffect.None)
    .width('100%').height('100%')
  }
}
```

### 示例8（ignoreLayoutSafeArea延伸组件布局范围）

该示例利用[ignoreLayoutSafeArea](#ignorelayoutsafearea20)改变组件位置。相比未使用该属性，配置ignoreLayoutSafeArea后，Row组件基于Stack内容区、Stack组件级安全区、系统状态栏共同组成的范围，取其左上部分，作左上对齐。



```TypeScript
import { LengthMetrics } from '@kit.ArkUI'

@Entry
@Component
struct IgnoreLayoutSafeAreaTest1 {
  build() {
    Column() {
      Stack() {
        Row()
          .backgroundColor('rgb(39, 135, 217)')
          .width(75)  // 固定宽度
          .height(75) // 固定高度
          .ignoreLayoutSafeArea([LayoutSafeAreaType.SYSTEM], [LayoutSafeAreaEdge.START, LayoutSafeAreaEdge.TOP])  // 设置布局区域延伸取左和上方向，至系统避让区SYSTEM
        
        Row()
          .backgroundColor('rgb(0, 74, 175)')
          .width(75)
          .height(75)

      }
      .width(200)
      .height(200)
      .backgroundColor(Color.Gray)
      .align(Alignment.TopStart)  // 子组件相对于Stack容器左上对齐
      .padding({
        left: 10  // 设置左侧10vp普通内边距
      })
      .safeAreaPadding(LengthMetrics.vp(10))  // 设置10vp安全区内边距（即组件级安全区）
    }
    .width('100%')
  }
}
```

### 示例9（ignoreLayoutSafeArea配合LayoutPolicy.matchParent延伸组件布局范围）

该示例利用[ignoreLayoutSafeArea](#ignorelayoutsafearea20)和[LayoutPolicy.matchParent](ts-universal-attributes-size.md#layoutpolicy15)同时改变组件大小和位置。相比未使用该属性，配置ignoreLayoutSafeArea后，Row组件基于Stack内容区、Stack组件级安全区，取其右下部分并撑满可用空间。



```TypeScript
import { LengthMetrics } from '@kit.ArkUI'

@Entry
@Component
struct IgnoreLayoutSafeAreaTest2 {
  build() {
    Column() {
      Stack() {
        Row()
          .backgroundColor('rgb(39, 135, 217)')
          .width(LayoutPolicy.matchParent)  // 自适应宽度
          .height(LayoutPolicy.matchParent) // 自适应高度
          .ignoreLayoutSafeArea([LayoutSafeAreaType.SYSTEM], [LayoutSafeAreaEdge.END, LayoutSafeAreaEdge.BOTTOM])  // 设置布局区域延伸取右和下方向，至系统避让区SYSTEM

        Row()
          .backgroundColor('rgb(0, 74, 175)')
          .width(LayoutPolicy.matchParent)
          .height(LayoutPolicy.matchParent)

      }
      .width(200)
      .height(200)
      .backgroundColor(Color.Gray)
      .align(Alignment.TopStart)  // 子组件相对于Stack容器左上对齐
      .padding(10) // 设置10vp普通内边距
      .safeAreaPadding(LengthMetrics.vp(10))  // 设置10vp安全区内边距（即组件级安全区）
    }
    .width('100%')
  }
}
```

### 示例10（expandSafeArea与ignoreLayoutSafeArea的区别）

该示例展示了容器分别设置了expandSafeArea和ignoreLayoutSafeArea的布局效果和各自对子组件布局效果的影响。两种设置下，容器都可见地进行了延伸，但前者的子组件不受延伸影响，后者的子组件因父容器的延伸改变了位置。

```TypeScript
@Entry
@Component
struct IgnoreLayoutSafeAreaTest3 {
  build() {
    Row(){
      Column(){
        Stack(){
          Stack(){

          }
          .width(30)
          .height(30)
          .backgroundColor('rgb(0, 74, 175)')
        }
        .width(100)
        .height(100)
        .backgroundColor('rgb(39, 135, 217)')
        .align(Alignment.TopStart)

        Text('基准效果').fontColor(Color.White)
      }

      Column(){
        Stack(){
          Stack(){

          }
          .width(30)
          .height(30)
          .backgroundColor('rgb(0, 74, 175)')
        }
        .width(100)
        .height(100)
        .backgroundColor('rgb(39, 135, 217)')
        .align(Alignment.TopStart)
        .expandSafeArea()  // 设置绘制区域延伸，自身绘制区域上抬，子组件相对屏幕位置不变

        Text('expandSafeArea').fontColor(Color.White)
      }

      Column(){
        Stack(){
          Stack(){

          }
          .width(30)
          .height(30)
          .backgroundColor('rgb(0, 74, 175)')
        }
        .width(100)
        .height(100)
        .backgroundColor('rgb(39, 135, 217)')
        .align(Alignment.TopStart)
        .ignoreLayoutSafeArea()  // 设置布局区域延伸，自身布局区域上抬，子组件相对容器位置不变

        Text('ignoreLayoutSafeArea').fontColor(Color.White)
      }
    }
    .width('100%')
    .backgroundColor(Color.Gray)
    .justifyContent(FlexAlign.SpaceEvenly)
  }
}
```

该示例通过enabled设置按钮是否可交互。

```TypeScript
// xxx.ets
@Entry
@Component
struct EnabledExample {
  build() {
    Flex({ justifyContent: FlexAlign.SpaceAround }) {
      // 点击时无响应
      Button('disable').enabled(false).backgroundColor(0x317aff).opacity(0.4)
      Button('enable').backgroundColor(0x317aff)
    }
    .width('100%')
    .padding({ top: 5 })
  }
}
```

### 示例1（设置渐变色边框）

通过[borderImage](arkts-arkui-common-comp-commonmethod-c.md#borderimage)接口为组件设置渐变色边框。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('This is gradient color.').textAlign(TextAlign.Center).height(50).width(200)
          .borderImage({
            source: {
              direction: GradientDirection.Left,
              colors: [[0xAEE1E1, 0.0], [0xD3E0DC, 0.3], [0xFCD1D1, 1.0]],
              repeating: false
            },
            slice: { top: 10, bottom: 10, left: 10, right: 10 },
            width: { top: "10px", bottom: "10px", left: "10px", right: "10px" },
            repeat: RepeatMode.Stretch,
            fill: false
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例2（动态调整属性值）

通过[Slider](../../apis-arkui/arkui-js/js-components-basic-slider.md)接口动态调整[borderImage](arkts-arkui-common-comp-commonmethod-c.md#borderimage)接口中属性值。



```TypeScript
// xxx.ets
@Entry
@Component
struct BorderImage {
  @State WidthValue: number = 0
  @State SliceValue: number = 0
  @State OutSetValue: number = 0
  @State RepeatValue: RepeatMode[] = [RepeatMode.Repeat, RepeatMode.Stretch, RepeatMode.Round, RepeatMode.Space]
  @State SelectIndex: number = 0
  @State SelectText: string = 'Repeat'
  @State FillValue: boolean = false

  build() {
    Row() {
      Column({ space: 20 }) {
        Row() {
          Text('This is borderImage.').textAlign(TextAlign.Center).fontSize(50)
        }
        .borderImage({
          source: $r('app.media.icon'),
          slice: this.SliceValue,
          width: this.WidthValue,
          outset: this.OutSetValue,
          repeat: this.RepeatValue[this.SelectIndex],
          fill: this.FillValue
        })

        Column() {
          Text(`borderImageSlice = ${this.SliceValue}px`)
          Slider({
            value: this.SliceValue,
            min: 0,
            max: 100,
            style: SliderStyle.OutSet
          })
            .onChange((value: number, mode: SliderChangeMode) => {
              this.SliceValue = value
            })
        }

        Column() {
          Text(`borderImageWidth = ${this.WidthValue}px`)
          Slider({
            value: this.WidthValue,
            min: 0,
            max: 100,
            style: SliderStyle.OutSet
          })
            .onChange((value: number, mode: SliderChangeMode) => {
              this.WidthValue = value
            })
        }

        Column() {
          Text(`borderImageOutSet = ${this.OutSetValue}px`)
          Slider({
            value: this.OutSetValue,
            min: 0,
            max: 100,
            style: SliderStyle.OutSet
          })
            .onChange((value: number, mode: SliderChangeMode) => {
              this.OutSetValue = value
            })
        }

        Row() {
          Text('borderImageRepeat: ')
          Select([{ value: 'Repeat' }, { value: 'Stretch' }, { value: 'Round' }, { value: 'Space' }])
            .value(this.SelectText)
            .selected(this.SelectIndex)
            .onSelect((index: number, value?: string) => {
              this.SelectIndex = index
              this.SelectText = value as string
            })
        }

        Row() {
          Text(`borderImageFill: ${this.FillValue} `)
          Toggle({ type: ToggleType.Switch, isOn: this.FillValue })
            .onChange((isOn: boolean) => {
              this.FillValue = isOn
            })
        }

      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例3（使用LocalizedEdgeWidths类型值）

通过[borderImage](arkts-arkui-common-comp-commonmethod-c.md#borderimage)接口中的slice、width和outset属性值使用[LocalizedEdgeWidths](ts-types.md#localizededgewidths12)类型。

```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI'

@Entry
@Component
struct BorderImage {
  @State WidthStartValue: number = 0
  @State WidthEndValue: number = 0
  @State SliceStartValue: number = 0
  @State SliceEndValue: number = 0
  @State OutSetStartValue: number = 0
  @State OutSetEndValue: number = 0
  @State RepeatValue: RepeatMode[] = [RepeatMode.Repeat, RepeatMode.Stretch, RepeatMode.Round, RepeatMode.Space]
  @State SelectIndex: number = 0
  @State SelectText: string = 'Repeat'
  @State FillValue: boolean = false

  build() {
    Row() {
      Column({ space: 20 }) {
        Row() {
          Text('This is borderImage.').textAlign(TextAlign.Center).fontSize(50)
        }
        .borderImage({
          source: $r('app.media.startIcon'),
          slice: {
            top: LengthMetrics.px(10),
            bottom: LengthMetrics.px(10),
            start: LengthMetrics.px(this.SliceStartValue),
            end: LengthMetrics.px(this.SliceEndValue) },
          width: {
            top: LengthMetrics.px(10),
            bottom: LengthMetrics.px(10),
            start: LengthMetrics.px(this.WidthStartValue),
            end: LengthMetrics.px(this.WidthEndValue)
          },
          outset: {
            top: LengthMetrics.px(10),
            bottom: LengthMetrics.px(10),
            start: LengthMetrics.px(this.OutSetStartValue),
            end: LengthMetrics.px(this.OutSetEndValue)
          },
          repeat: this.RepeatValue[this.SelectIndex],
          fill: this.FillValue
        })

        Column() {
          Text(`borderImageSliceStart = ${this.SliceStartValue}px`)
          Slider({
            value: this.SliceStartValue,
            min: 0,
            max: 100,
            style: SliderStyle.OutSet
          })
            .onChange((value: number, mode: SliderChangeMode) => {
              this.SliceStartValue = value
            })
        }

        Column() {
          Text(`borderImageSliceEnd = ${this.SliceEndValue}px`)
          Slider({
            value: this.SliceEndValue,
            min: 0,
            max: 100,
            style: SliderStyle.OutSet
          })
            .onChange((value: number, mode: SliderChangeMode) => {
              this.SliceEndValue = value
            })
        }

        Column() {
          Text(`borderImageWidthStart = ${this.WidthStartValue}px`)
          Slider({
            value: this.WidthStartValue,
            min: 0,
            max: 100,
            style: SliderStyle.OutSet
          })
            .onChange((value: number, mode: SliderChangeMode) => {
              this.WidthStartValue = value
            })
        }

        Column() {
          Text(`borderImageWidthEnd = ${this.WidthEndValue}px`)
          Slider({
            value: this.WidthEndValue,
            min: 0,
            max: 100,
            style: SliderStyle.OutSet
          })
            .onChange((value: number, mode: SliderChangeMode) => {
              this.WidthEndValue = value
            })
        }

        Column() {
          Text(`borderImageOutSetStart = ${this.OutSetStartValue}px`)
          Slider({
            value: this.OutSetStartValue,
            min: 0,
            max: 100,
            style: SliderStyle.OutSet
          })
            .onChange((value: number, mode: SliderChangeMode) => {
              this.OutSetStartValue = value
            })
        }

        Column() {
          Text(`borderImageOutSetEnd = ${this.OutSetEndValue}px`)
          Slider({
            value: this.OutSetEndValue,
            min: 0,
            max: 100,
            style: SliderStyle.OutSet
          })
            .onChange((value: number, mode: SliderChangeMode) => {
              this.OutSetEndValue = value
            })
        }

        Row() {
          Text('borderImageRepeat: ')
          Select([{ value: 'Repeat' }, { value: 'Stretch' }, { value: 'Round' }, { value: 'Space' }])
            .value(this.SelectText)
            .selected(this.SelectIndex)
            .onSelect((index: number, value?: string) => {
              this.SelectIndex = index
              this.SelectText = value as string
            })
        }

        Row() {
          Text(`borderImageFill: ${this.FillValue} `)
          Toggle({ type: ToggleType.Switch, isOn: this.FillValue })
            .onChange((isOn: boolean) => {
              this.FillValue = isOn
            })
        }

      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 示例1（父组件优先识别手势和父子组件同时触发手势）

该示例通过配置priorityGesture和parallelGesture分别实现了父组件优先识别手势和父子组件同时触发手势。



```TypeScript
// xxx.ets
@Entry
@Component
struct GestureSettingsExample {
  @State priorityTestValue: string = ''
  @State parallelTestValue: string = ''

  build() {
    Column() {
      Column() {
        Text('TapGesture:' + this.priorityTestValue).fontSize(28)
          .gesture(
            TapGesture()
              .onAction(() => {
                this.priorityTestValue += '\nText';
              }))
      }
      .height(200)
      .width(250)
      .padding(20)
      .margin(20)
      .border({ width: 3 })
      // 设置为priorityGesture时，点击文本会忽略Text组件的TapGesture手势事件，优先识别父组件Column的TapGesture手势事件
      .priorityGesture(
        TapGesture()
          .onAction((event: GestureEvent) => {
            this.priorityTestValue += '\nColumn';
          }), GestureMask.IgnoreInternal)

      Column() {
        Text('TapGesture:' + this.parallelTestValue).fontSize(28)
          .gesture(
            TapGesture()
              .onAction((event: GestureEvent) => {
                this.parallelTestValue += '\nText';
              }))
      }
      .height(200)
      .width(250)
      .padding(20)
      .margin(20)
      .border({ width: 3 })
      // 设置为parallelGesture时，点击文本会同时触发子组件Text与父组件Column的TapGesture手势事件
      .parallelGesture(
        TapGesture()
          .onAction((event: GestureEvent) => {
            this.parallelTestValue += '\nColumn';
          }), GestureMask.Normal)
    }
  }
}
```

### 示例1 (使用onAccessibilityHover事件)

该示例主要演示使用onAccessibilityHover事件，对无障碍模式下的按钮进行设置。

```TypeScript
// xxx.ets
@Entry
@Component
struct OnAccessibilityHoverEventExample {
  @State hoverText: string = 'no hover';
  @State color: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Button(this.hoverText)
        .width(180).height(80)
        .backgroundColor(this.color)
        .onAccessibilityHover((isHover: boolean) => {
          // 通过onAccessibilityHover事件动态修改按钮在无障碍悬浮（手指触摸进入/退出）时的文本内容与背景颜色
          if (isHover) {
            this.hoverText = 'hover';
            this.color = Color.Pink;
          } else {
            this.hoverText = 'no hover';
            this.color = Color.Blue;
          }
        })
    }.padding({ top: 30 }).width('100%')
  }
}
```

### 示例2 (捕获无法无障碍聚焦的组件的触摸事件)

该示例代码在无障碍模式下通过onAccessibilityHoverTransparent接口捕获无法无障碍聚焦的组件的触摸事件，最后再将事件信息显示在组件下方的文本中。

从API version 20开始，新增了[onAccessibilityHoverTransparent](arkts-arkui-common-comp-commonmethod-c.md#onaccessibilityhovertransparent)接口。

```TypeScript
@Entry
@Component
struct OnAccessibilityHoverTransparentExample {
  @State text: string = '';
  @State eventType: string = '';

  build() {
    Column({ space: 50 }) {
      Column() {
        Button('Test Button')
          .accessibilityLevel('no')
      }.margin({ top: 20 })

      Text(this.text)
    }
    .width('100%')
    .height('100%')
    .onAccessibilityHoverTransparent((event: TouchEvent) => {
      if (event) {
        // 手指按下触发
        if (event.type === TouchType.HOVER_ENTER) {
          this.eventType = 'HOVER_ENTER';
        }
        // 触摸移动时触发
        if (event.type === TouchType.HOVER_MOVE) {
          this.eventType = 'HOVER_MOVE';
        }
        // 抬手时触发
        if (event.type === TouchType.HOVER_EXIT) {
          this.eventType = 'HOVER_EXIT';
        }
        // 取消当前触发事件
        if (event.type === TouchType.HOVER_CANCEL) {
          this.eventType = 'HOVER_CANCEL';
        }
        this.text = 'TouchType:' + this.eventType + '\nDistance between touch point and touch element:\nx: '
          + event.touches[0].x + '\n' + 'y: ' + event.touches[0].y + '\nComponent globalPos:('
          + event.target.area.globalPosition.x + ',' + event.target.area.globalPosition.y + ')\nwidth:'
          + event.target.area.width + '\nheight:' + event.target.area.height;
      }
    })
  }
}
```

### 示例1（设置背景基础样式）

该示例通过配置backgroundColor、backgroundImage、backgroundImageSize和backgroundImagePosition设置背景的基础样式。



```TypeScript
// xxx.ets
@Entry
@Component
struct BackgroundExample {
  build() {
    Column({ space: 5 }) {
      Text('background color').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Row().width('90%').height(50).backgroundColor(0xE5E5E5).border({ width: 1 })

      Text('background image repeat along X').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Row()
      // $r('app.media.image')需要替换为开发者所需的图像资源文件。
        .backgroundImage($r('app.media.image'), ImageRepeat.X)
        .backgroundImageSize({ width: '250px', height: '140px' })
        .width('90%')
        .height(70)
        .border({ width: 1 })

      Text('background image repeat along Y').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Row()
      // $r('app.media.image')需要替换为开发者所需的图像资源文件。
        .backgroundImage($r('app.media.image'), ImageRepeat.Y)
        .backgroundImageSize({ width: '500px', height: '120px' })
        .width('90%')
        .height(100)
        .border({ width: 1 })

      Text('background image size').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Row()
        .width('90%')
        .height(150)
        // $r('app.media.image')需要替换为开发者所需的图像资源文件。
        .backgroundImage($r('app.media.image'), ImageRepeat.NoRepeat)
        .backgroundImageSize({ width: 1000, height: 500 })
        .border({ width: 1 })

      Text('background fill the box(Cover)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      // 不保证图片完整的情况下占满盒子
      Row()
        .width(200)
        .height(50)
        // $r('app.media.image')需要替换为开发者所需的图像资源文件。
        .backgroundImage($r('app.media.image'), ImageRepeat.NoRepeat)
        .backgroundImageSize(ImageSize.Cover)
        .border({ width: 1 })

      Text('background fill the box(Contain)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      // 保证图片完整的情况下放到最大
      Row()
        .width(200)
        .height(50)
        // $r('app.media.image')需要替换为开发者所需的图像资源文件。
        .backgroundImage($r('app.media.image'), ImageRepeat.NoRepeat)
        .backgroundImageSize(ImageSize.Contain)
        .border({ width: 1 })

      Text('background image position').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Row()
        .width(100)
        .height(50)
        // $r('app.media.image')需要替换为开发者所需的图像资源文件。
        .backgroundImage($r('app.media.image'), ImageRepeat.NoRepeat)
        .backgroundImageSize({ width: 1000, height: 560 })
        .backgroundImagePosition({ x: -500, y: -300 })
        .border({ width: 1 })
    }
    .width('100%').height('100%').padding({ top: 5 })
  }
}
```

### 示例2（设置背景模糊样式）

该示例通过backgroundBlurStyle设置背景模糊样式。



```TypeScript
// xxx.ets
@Entry
@Component
struct BackgroundBlurStyleDemo {
  build() {
    Column() {
      Row() {
        Text('Thin Material')
      }
      .width('50%')
      .height('50%')
      .backgroundBlurStyle(BlurStyle.Thin,
        { colorMode: ThemeColorMode.LIGHT, adaptiveColor: AdaptiveColor.DEFAULT, scale: 1.0 })
      .position({ x: '15%', y: '30%' })
    }
    .height('100%')
    .width('100%')
    // $r('app.media.bg')需要替换为开发者所需的图像资源文件
    .backgroundImage($r('app.media.bg'))
    .backgroundImageSize(ImageSize.Cover)
  }
}
```

### 示例3（设置组件背景）

该示例通过background设置组件背景。



```TypeScript
// xxx.ets
@Entry
@Component
struct BackgroundExample {
  @Builder
  renderBackground() {
    Column() {
      Progress({ value: 50 })
    }
  }

  build() {
    Column() {
      Text("content")
        .width(100)
        .height(40)
        .fontColor("#FFF")
        .position({ x: 50, y: 80 })
        .textAlign(TextAlign.Center)
        .backgroundColor(Color.Green)
    }
    .width(200).height(200)
    .background(this.renderBackground)
    .backgroundColor(Color.Gray)
  }
}
```

### 示例4（设置组件背景提亮效果）

该示例通过backgroundBrightness设置组件背景提亮效果。

效果图如下：

rate和lightUpDegree参数值为0.5,0.5：



修改rate和lightUpDegree参数值为0.5,-0.1：



去掉backgroundBrightness的设置，效果如下：



```TypeScript
// xxx.ets
@Entry
@Component
struct BackgroundBrightnessDemo {
  build() {
    Column() {
      Row() {
        Text("BackgroundBrightness")
      }
      .width(200)
      .height(100)
      .position({ x: 100, y: 100 })
      .backgroundBlurStyle(BlurStyle.Thin, { colorMode: ThemeColorMode.LIGHT, adaptiveColor: AdaptiveColor.DEFAULT})
      .backgroundBrightness({rate:0.5,lightUpDegree:0.5}) // 背景提亮效果
    }
    .width('100%')
    .height('100%')
    // $r('app.media.image')需要替换为开发者所需的图像资源文件
    .backgroundImage($r('app.media.image'))
    .backgroundImageSize(ImageSize.Cover)
  }
}
```

### 示例5（设置模糊属性）

该示例提供了模糊属性的实现方法。通过blur设置内容模糊，通过backdropBlur设置背景模糊。



```TypeScript
// xxx.ets
@Entry
@Component
struct BlurEffectsExample {
  build() {
    Column({ space: 10 }) {
      // 对字体进行模糊
      Text('font').fontSize(15).fontColor(0xCCCCCC).width('90%')
      Flex({ alignItems: ItemAlign.Center }) {
        Text('original').margin(10)
        Text('blur')
          .blur(5).margin(10)
        Text('blur')
          .blur(10, undefined).margin(10) // 内容模糊半径为10，不设置灰阶。
        Text('blur')
          .blur(15).margin(10)
      }.width('90%').height(40)
      .backgroundColor(0xF9CF93)


      // 对背景进行模糊
      Text('backdropBlur').fontSize(15).fontColor(0xCCCCCC).width('90%')
      Text()
        .width('90%')
        .height(40)
        .fontSize(16)
        .backdropBlur(3)
        // $r('app.media.image')需要替换为开发者所需的图像资源文件
        .backgroundImage($r('app.media.image'))
        .backgroundImageSize({ width: 1200, height: 160 })
    }.width('100%').margin({ top: 5 })
  }
}
```

### 示例6（设置文字异形模糊效果）

该示例通过[blendMode](ts-universal-attributes-image-effect.md#blendmode11)和backgroundEffect实现文字异形模糊效果。如果出现漏线问题，开发者应首先确保两个blendMode所在组件大小严格相同。如果确认相同，可能是组件边界落在浮点数坐标上导致，可尝试设置[pixelRound](ts-universal-attributes-pixelRoundForComponent.md#pixelround)通用属性，使产生的白线、暗线两侧的组件边界对齐到整数像素坐标上。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State shadowColor: Color = Color.White;
  @State dateFontSize: number = 20;
  @State redValue: number = 255;
  @State greenValue: number = 255;
  @State blueValue: number = 255;
  @State alphaValue: number = 0.1;
  @State blurRadius: number = 40;
  @State saturationValue: number = 0.8;
  @State brightnessValue: number = 1.5;
  build() {
    Stack() {
      // $r('app.media.image')需要替换为开发者所需的图像资源文件
      Image($r('app.media.image'))
      Column() {
        Column({ space: 0 }) {
          Column() {
            Text('11')
              .fontSize(144)
              .fontWeight(FontWeight.Bold)
              .fontColor('rgba(255,255,255,1)')
              .fontFamily('HarmonyOS-Sans-Digit')
              .maxLines(1)
              .lineHeight(120 * 1.25)
              .height(120 * 1.25)
              .letterSpacing(4 * 1.25)
            Text('42')
              .fontSize(144)
              .fontWeight(FontWeight.Bold)
              .fontColor('rgba(255,255,255,1)')
              .fontFamily('HarmonyOS-Sans-Digit')
              .maxLines(1)
              .lineHeight(120 * 1.25)
              .height(120 * 1.25)
              .letterSpacing(4 * 1.25)
              .shadow({
                color: 'rgba(0,0,0,0)',
                radius: 20,
                offsetX: 0,
                offsetY: 0
              })
            Row() {
              Text('10月16日')
                .fontSize(this.dateFontSize)
                .height(22)
                .fontWeight('medium')
                .fontColor('rgba(255,255,255,1)')
              Text('星期一')
                .fontSize(this.dateFontSize)
                .height(22)
                .fontWeight('medium')
                .fontColor('rgba(255,255,255,1)')
            }
          }
          // blendMode采用离屏渲染，DST_IN模式下仅显示当前组件与下方画布的重叠区域
          .blendMode(BlendMode.DST_IN, BlendApplyType.OFFSCREEN)
          .pixelRound({
            start: PixelRoundCalcPolicy.FORCE_FLOOR ,
            top: PixelRoundCalcPolicy.FORCE_FLOOR ,
            end: PixelRoundCalcPolicy.FORCE_CEIL,
            bottom: PixelRoundCalcPolicy.FORCE_CEIL
          })
        }
        // blendMode采用离屏渲染，SRC_OVER模式下会将当前组件内容覆盖显示在下方画布之上
        .blendMode(BlendMode.SRC_OVER, BlendApplyType.OFFSCREEN)
        // backgroundEffect配置组件背景的模糊半径、饱和度、亮度及动态RGBA颜色
        .backgroundEffect({
          radius: this.blurRadius,
          saturation: this.saturationValue,
          brightness: this.brightnessValue,
          color: this.getVolumeDialogWindowColor()
        })
        .justifyContent(FlexAlign.Center)
        .pixelRound({
          start: PixelRoundCalcPolicy.FORCE_FLOOR ,
          top: PixelRoundCalcPolicy.FORCE_FLOOR ,
          end: PixelRoundCalcPolicy.FORCE_CEIL,
          bottom: PixelRoundCalcPolicy.FORCE_CEIL
        })
      }
    }
  }
  getVolumeDialogWindowColor(): ResourceColor | string {
    return `rgba(${this.redValue.toFixed(0)}, ${this.greenValue.toFixed(0)}, ${this.blueValue.toFixed(0)}, ${this.alphaValue.toFixed(2)})`;
  }
}
```

### 示例7（模糊效果对比）

该示例对比了[backgroundEffect11+](#backgroundeffect11)、[backdropBlur](arkts-arkui-common-comp-commonmethod-c.md#backdropblur)和[backgroundBlurStyle9+](#backgroundblurstyle9)三种不同的模糊效果。



```TypeScript
// xxx.ets
@Entry
@Component
struct BackgroundBlur {
  private imageSize: number = 150;

  build() {
    Column({ space: 5 }) {
      // backgroundBlurStyle通过枚举值的方式设置模糊参数
      Stack() {
        // $r('app.media.test')需要替换为开发者所需的图像资源文件
        Image($r('app.media.test'))
          .width(this.imageSize)
          .height(this.imageSize)
        Column()
          .width(this.imageSize)
          .height(this.imageSize)
          .backgroundBlurStyle(BlurStyle.Thin)
      }

      // backgroundEffect 可以自定义设置 模糊半径、亮度、饱和度等参数
      Stack() {
        // $r('app.media.test')需要替换为开发者所需的图像资源文件
        Image($r('app.media.test'))
          .width(this.imageSize)
          .height(this.imageSize)
        Column()
          .width(this.imageSize)
          .height(this.imageSize)
          .backgroundEffect({ radius: 20, brightness: 0.6, saturation: 15 })
      }

      // backdropBlur 只能设置模糊半径和灰阶参数
      Stack() {
        // $r('app.media.test')需要替换为开发者所需的图像资源文件
        Image($r('app.media.test'))
          .width(this.imageSize)
          .height(this.imageSize)
        Column()
          .width(this.imageSize)
          .height(this.imageSize)
          .backdropBlur(20, { grayscale: [30, 50] })
      }
    }
    .width('100%')
    .padding({ top: 5 })
  }
}
```

### 示例8（设置P3色域背景效果）

从API version 20开始，该示例通过[backgroundColor](#backgroundcolor20)设置P3色域背景效果。



```TypeScript
// xxx.ets
// 设置P3色域时需要在ets/entryability/EntryAbility.ets中，通过setColorSpace接口将当前窗口设置为广色域。
import { ColorMetrics } from '@kit.ArkUI';

@Entry
@Component
struct P3BackgroundDemo {
  @State p3Color: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0, 0.3, 0.8, 1);

  build() {
    Column({ space: 5 }) {
      Text('background color with colorMetrics').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Row().width('90%').height(50).backgroundColor(this.p3Color)
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例9（设置组件背景扩展）

从API version 20开始，该示例通过[background](#background10)实现组件背景扩展到父组件的安全区。

```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct BackgroundExtension {
  @Builder
  myImages() {
    Column() {
      Image($r('app.media.startIcon'))
        .width('100%')
        .height('100%')
    }
  }

  build() {
    Column({space: 10}) {
      Stack() {
        // CustomBuilder类型的背景设置了ignoresLayoutSafeAreaEdges属性，背景扩展到父组件安全区
        Column()
          .size({ width: '100%', height: '100%' })
          .border({ width: 1, color: Color.Red })
          .background(
            this.myImages(),
            { align: Alignment.Center , ignoresLayoutSafeAreaEdges: [ LayoutSafeAreaEdge.START, LayoutSafeAreaEdge.TOP ] }
          )
      }
      .size({ width: 300, height: 300 })
      .backgroundColor('#004aaf')
      .safeAreaPadding(LengthMetrics.vp(50))

      Stack() {
        // ResourceColor类型的背景未设置ignoresLayoutSafeAreaEdges属性，背景默认扩展到父组件安全区
        Column()
          .size({ width: '100%', height: '100%' })
          .border({ width: 1, color: Color.Red })
          .background('#d5d5d5', { align: Alignment.Center })
      }
      .size({ width: 300, height: 300 })
      .backgroundColor('#707070')
      .safeAreaPadding(LengthMetrics.vp(50))
    }
    .margin(10)
  }
}
```

该示例主要演示通过renderFit设置宽高动画过程中的组件内容不同填充方式。

```TypeScript
// xxx.ets
@Entry
@Component
struct RenderFitExample {
  @State currentWidth: number = 100;
  @State currentHeight: number = 30;
  isExpanded: boolean = true;

  build() {
    Column() {
      Text('Hello')
        .width(this.currentWidth)
        .height(this.currentHeight)
        .borderWidth(1)
        .textAlign(TextAlign.Start)
        .renderFit(RenderFit.LEFT) // 设置LEFT的renderFit，动画过程中，动画的终态内容与组件保持左对齐
        .margin(20)

      Text('Hello')
        .width(this.currentWidth)
        .height(this.currentHeight)
        .textAlign(TextAlign.Center)
        .borderWidth(1)
        .renderFit(RenderFit.CENTER) // 设置CENTER的renderFit，动画过程中，动画的终态内容与组件保持中心对齐
        .margin(20)

      Button('animate')
        .onClick(() => {
          this.getUIContext()?.animateTo({ curve: Curve.Ease }, () => {
            if (this.isExpanded) {
              this.currentWidth = 150;
              this.currentHeight = 50;
            } else {
              this.currentWidth = 100;
              this.currentHeight = 30;
            }
            this.isExpanded = !this.isExpanded;
          })
        })
    }.width('100%').height('100%').alignItems(HorizontalAlign.Center)
  }
}
```

该示例演示背景模糊等特效的绘制合并。

```TypeScript
// Index.ets
@Entry
@Component
struct Index {
  @State isUse: boolean = true;

  build() {
    Stack() {
      Image($r('app.media.mountain'))
        .autoResize(true)
      EffectComponent() {
        Column({ space: 20 }) {
           Column() {
           }
           .position({ x: 0, y: 0 })
           .width(150)
           .height(800)
           .useEffect(this.isUse, EffectType.WINDOW_EFFECT)
         
           Column() {
           }
           .position({ x: 200, y: 20 })
           .width(150)
           .height(300)
           .useEffect(this.isUse, EffectType.DEFAULT)

           Column() {
           }
           .position({ x: 400, y: 20 })
           .width(150)
           .height(300)
           .useEffect(this.isUse)
        }
        .width('100%')
        .height('100%')
      }
      .backgroundBlurStyle(BlurStyle.Thin)

       Column() {
       }
        .position({ x: 600, y: 0 })
        .width(150)
        .height(800)
        .useEffect(this.isUse, EffectType.WINDOW_EFFECT)

      Row() {
        Button('useEffect')
        .margin(30)
        .onClick(() => {
          this.isUse = !this.isUse;
        })
      }
      .position({ x: 300, y: 450 })
    }
    .backgroundColor(Color.Black)
    .width('100%')
  }
}
```

该示例通过reuseId标识自定义组件的复用组。

```TypeScript
// xxx.ets
@Entry
@Component
struct MyComponent {
  @State isShow: boolean = true;
  private type: string = 'type1';

  build() {
    Column() {
      Button('ChangeType')
        .onClick(() => {
          this.type = 'type2';
        })
      Button('Switch')
        .onClick(() => {
          this.isShow = !this.isShow;
        })
      if (this.isShow) {
        ReusableChildComponent({ type: this.type })
          .reuseId(this.type)
      }
    }
    .width('100%')
    .height('100%')
  }
}

@Reusable
@Component
struct ReusableChildComponent {
  @State type: string = '';

  aboutToAppear() {
    console.info(`ReusableChildComponent Appear ${this.type}`);
  }

  aboutToReuse(params: ESObject) {
    console.info(`ReusableChildComponent Reuse ${this.type}`);
    this.type = params.type;
  }

  build() {
    Row() {
      Text(this.type)
        .fontSize(20)
        .margin({ left: 10 })
    }.margin({ left: 10, right: 10 })
  }
}
```

### 示例1（弹出普通菜单）

该示例为bindMenu通过配置[MenuElement](arkts-arkui-common-comp-menuelement-i.md)弹出普通菜单。



```TypeScript
@Entry
@Component
struct MenuExample {
  build() {
    Column() {
      Text('click for Menu')
        .bindMenu([
          {
            value: 'Menu1',
            action: () => {
              console.info('handle Menu1 select');
            }
          },
          {
            value: 'Menu2',
            action: () => {
              console.info('handle Menu2 select');
            }
          },
        ])
    }
    .width('100%')
    .margin({ top: 5 })
  }
}
```

### 示例2（弹出自定义菜单）

该示例为bindMenu通过配置CustomBuilder弹出自定义菜单。同时，从API version 18开始支持通过配置[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中的hapticFeedbackMode属性实现菜单弹出时的振动效果。



```TypeScript
@Entry
@Component
struct MenuExample {
  @State listData: number[] = [0, 0, 0];

  @Builder MenuBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      ForEach(this.listData, (item:number, index) => {
        Column() {
          Row() {
            // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
            Image($r("app.media.icon")).width(20).height(20).margin({ right: 5 })
            Text(`Menu${index as number + 1}`).fontSize(20)
          }
          .width('100%')
          .height(30)
          .justifyContent(FlexAlign.Center)
          .align(Alignment.Center)
          .onClick(() => {
            console.info(`Menu${index as number + 1} Clicked!`);
          })

          if (index != this.listData.length - 1) {
            Divider().height(10).width('80%').color('#ccc')
          }
        }.padding(5).height(40)
      })
    }.width(100)
  }

  build() {
    Column() {
      Text('click for menu')
        .fontSize(20)
        .margin({ top: 20 })
        .bindMenu(this.MenuBuilder, { hapticFeedbackMode: HapticFeedbackMode.ENABLED })
    }
    .height('100%')
    .width('100%')
    .backgroundColor('#f0f0f0')
  }
}
```

### 示例3（长按弹出菜单）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).LongPress弹出菜单。



```TypeScript
@Entry
@Component
struct ContextMenuExample {
  @Builder MenuBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('Test menu item 1')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
      Divider().height(10)
      Text('Test menu item 2')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
    }.width(100)
  }

  build() {
    Column() {
      Text('LongPress for menu')
    }
    .width('100%')
    .margin({ top: 5 })
    .bindContextMenu(this.MenuBuilder, ResponseType.LongPress)
  }
}
```

### 示例4（右键弹出指向型菜单）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).RightClick和[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中的enableArrow属性弹出指向型菜单。同时，从API version 18开始支持通过配置[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中的hapticFeedbackMode属性实现菜单弹出时的振动效果。



```TypeScript
@Entry
@Component
struct DirectiveMenuExample {
  @Builder MenuBuilder() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text('Options')
      Divider().strokeWidth(2).margin(5).color('#F0F0F0')
      Text('Hide')
      Divider().strokeWidth(2).margin(5).color('#F0F0F0')
      Text('Exit')
    }
    .width(200)
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Column() {
        Text("DirectiveMenuExample")
          .fontSize(20)
          .width('100%')
          .height("25%")
          .backgroundColor('#F0F0F0')
          .textAlign(TextAlign.Center)
          .bindContextMenu(this.MenuBuilder, ResponseType.RightClick, {
            enableArrow: true,
            placement: Placement.Bottom,
            hapticFeedbackMode: HapticFeedbackMode.ENABLED
          })
      }
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例5（长按弹出菜单的截图预览样式）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).LongPress和[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中preview属性的[MenuPreviewMode](arkts-arkui-common-comp-menupreviewmode-e.md)类型弹出菜单预览样式。



```TypeScript
@Entry
@Component
struct Index {
  // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
  private iconStr: ResourceStr = $r("app.media.icon");

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
    }
  }

  build() {
    Column({ space: 50 }) {
      Column() {
        Column() {
          Text('preview-image')
            .width(200)
            .height(100)
            .textAlign(TextAlign.Center)
            .margin(100)
            .fontSize(30)
            .bindContextMenu(this.MyMenu, ResponseType.LongPress,
              { preview: MenuPreviewMode.IMAGE,
                previewAnimationOptions: {scale: [0.8, 1.0]},
              })
            .backgroundColor("#ff3df2f5")
        }
      }.width('100%')
    }
  }
}
```

### 示例6（长按弹出菜单的自定义预览样式）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).LongPress和[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中preview属性的[CustomBuilder](ts-types.md#custombuilder8)类型弹出菜单自定义预览样式。



```TypeScript
@Entry
@Component
struct Index {
  // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
  private iconStr: ResourceStr = $r("app.media.icon");

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
    }
  }

  @Builder
  MyPreview() {
    Column() {
      Image($r('app.media.icon'))
        .width(200)
        .height(200)
    }
  }

  build() {
    Column({ space: 50 }) {
      Column() {
        Column() {
          Text('preview-builder')
            .width(200)
            .height(100)
            .textAlign(TextAlign.Center)
            .margin(100)
            .fontSize(30)
            .bindContextMenu(this.MyMenu, ResponseType.LongPress,
              {
                preview: this.MyPreview
              })
        }
      }.width('100%')
    }
  }
}
```

### 示例7（设置状态变量弹出菜单）

该示例为[bindContextMenu](arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenu)通过配置isShown弹出菜单预览样式。



```TypeScript
@Entry
@Component
struct Index {
  // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
  private iconStr: ResourceStr = $r("app.media.icon");
  @State isShown: boolean = false;

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
    }
  }

  @Builder
  MyPreview() {
    Column() {
      Image($r('app.media.icon'))
        .width(200)
        .height(200)
    }
  }

  build() {
    Column({ space: 50 }) {
      Column() {
        Column() {
          Text('preview-builder')
            .width(200)
            .height(100)
            .textAlign(TextAlign.Center)
            .margin(100)
            .fontSize(30)
            .bindContextMenu(this.isShown, this.MyMenu,
              {
                preview: this.MyPreview,
                aboutToDisappear: ()=>{
                  this.isShown = false;
                }
              })
          Button('click')
            .onClick(()=>{
              this.isShown = true;
            })
        }
      }.width('100%')
    }
  }
}
```

### 示例8（设置菜单和预览的动效）

该示例为bindContextMenu通过配置[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中的transition属性，实现自定义菜单以及菜单预览时的显示和退出动效。



```TypeScript
@Entry
@Component
struct MenuExample {
  @Builder
  MenuBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('Menu item 1')
        .fontSize(12)
        .width(200)
        .height(30)
        .textAlign(TextAlign.Center)
      Divider().height(10)
      Text('Menu item 2')
        .fontSize(12)
        .width(100)
        .height(30)
        .textAlign(TextAlign.Center)
    }.width(100)
  }

  @Builder
  MyPreview() {
    Column() {
      // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.startIcon'))
        .width(50)
        .height(50)
    }
  }

  build() {
    Column() {
      Button('LongPress bindContextMenu')
        .margin({ top: 15 })
        .bindContextMenu(
          this.MenuBuilder,
          ResponseType.LongPress, {
          transition: TransitionEffect.OPACITY.animation({ duration: 4000, curve: Curve.Ease }).combine(
            TransitionEffect.rotate({ z: 1, angle: 180 })),
          preview: this.MyPreview,
          previewAnimationOptions: {
            scale: [0.8, 1.0],
            transition: TransitionEffect.OPACITY.animation({ duration: 4000, curve: Curve.Ease }).combine(
              TransitionEffect.rotate({ z: 1, angle: 180 }))
          }
        })
    }
    .width('100%')
    .margin({ top: 5 })
  }
}
```

### 示例9（设置symbol类型图标）

该示例为bindMenu通过配置[MenuElement](arkts-arkui-common-comp-menuelement-i.md)的symbolIcon弹出菜单。



```TypeScript
import { SymbolGlyphModifier } from '@kit.ArkUI';
@Entry
@Component
struct MenuExample {
  @State symbolIconModifier1: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_photo')).fontSize('24vp');
  @State symbolIconModifier2: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_photo')).fontSize('24vp');
  build() {
    Column() {
      Text('click for Menu')
    }
    .width('100%')
    .margin({ top: 5 })
    .bindMenu([
      {
        value: 'Menu1',
        symbolIcon:this.symbolIconModifier1,
        action: () => {
          console.info('handle Menu1 select');
        }
      },
      {
        value: 'Menu2',
        symbolIcon:this.symbolIconModifier2,
        action: () => {
          console.info('handle Menu2 select');
        }
      },
    ])
  }
}
```

### 示例10（设置一镜到底动效）

该示例为bindContextMenu通过配置[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中previewAnimationOptions属性的hoverScale，实现组件截图到自定义预览图的一镜到底过渡动效。



```TypeScript
@Entry
@Component
struct Index {
  // $r('app.media.xxx')需要替换为开发者所需的图像资源文件。
  private iconStr: ResourceStr = $r("app.media.app_icon");

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: "Menu option" })
      MenuItem({ startIcon: this.iconStr, content: "Menu option" })
      MenuItem({ startIcon: this.iconStr, content: "Menu option" })
    }
  }

  @Builder
  MyPreview() {
    Column() {
      Image($r('app.media.example'))
        .width(200)
        .height(200)
    }
  }

  build() {
    Column({ space: 50 }) {
      Column() {
        Column() {
          Image($r('app.media.example'))
            .width(100)
            .height(100)
            .margin(100)
            .bindContextMenu(this.MyMenu, ResponseType.LongPress,
              {
                preview: this.MyPreview,
                previewAnimationOptions: {
                  hoverScale: [1.0, 0.95]
                }
              })
        }
      }.width('100%')
    }
  }
}
```

### 示例11（自定义背景模糊效果参数）

该示例为bindMenu通过配置[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中的backgroundBlurStyleOptions属性，实现了自定义菜单背景模糊效果。

从API version 18开始，在ContextMenuOptions中新增了backgroundBlurStyleOptions属性。



```TypeScript
@Entry
@Component
struct MenuExample {
  build() {
    Stack() {
      // $r('app.media.bg')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.bg'))
      Column() {
        Text('click for Menu')
          .bindMenu([
            {
              value: 'Menu1',
              action: () => {
                console.info('handle Menu1 select')
              }
            },
            {
              value: 'Menu2',
              action: () => {
                console.info('handle Menu2 select')
              }
            },
          ],
            {
              backgroundBlurStyle: BlurStyle.BACKGROUND_THIN,
              backgroundBlurStyleOptions: {
                colorMode: ThemeColorMode.LIGHT,
                blurOptions: { grayscale: [20, 20] },
                policy: BlurStyleActivePolicy.ALWAYS_ACTIVE,
                adaptiveColor: AdaptiveColor.AVERAGE,
                scale: 1
              },
            }
          )
      }
      .width('100%')
      .margin({ top: 5 })
    }
  }
}
```

### 示例12（自定义背景效果参数）

该示例为bindMenu通过配置[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中的backgroundEffect属性，实现了自定义菜单背景效果。

从API version 18开始，在ContextMenuOptions中新增了backgroundEffect属性。



```TypeScript
@Entry
@Component
struct MenuExample {
  build() {
    Stack() {
      // $r('app.media.bg')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.bg'))
      Column() {
        Text('click for Menu')
          .bindMenu([
            {
              value: 'Menu1',
              action: () => {
                console.info('handle Menu1 select');
              }
            },
            {
              value: 'Menu2',
              action: () => {
                console.info('handle Menu2 select');
              }
            },
          ],
            {
              backgroundBlurStyle: BlurStyle.BACKGROUND_THIN,
              backgroundEffect: {
                radius: 60,
                saturation: 10,
                brightness: 1,
                color: '#661A1A1A',
                adaptiveColor: AdaptiveColor.AVERAGE,
                blurOptions:{grayscale:[20,20]}
              }
            }
          )
      }
      .width('100%')
      .margin({ top: 5 })
    }
  }
}
```

### 示例13（设置一镜到底动效支持抬手打断）

该示例通过为bindContextMenu配置[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中的previewAnimationOptions属性实现了一镜到底过渡动效的同时，再配置hoverScaleInterruption控制是否允许长按抬手取消菜单弹出。

从API version 20开始，在previewAnimationOptions的类型[ContextMenuAnimationOptions](arkts-arkui-common-comp-contextmenuanimationoptions-i.md)中新增了hoverScaleInterruption属性。



```TypeScript
@Entry
@Component
struct Index {
  // $r('app.media.xxx')需要替换为开发者所需的图像资源文件。
  private iconStr: ResourceStr = $r("app.media.app_icon");

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
    }
  }

  @Builder
  MyPreview() {
    Column() {
      Image($r('app.media.example'))
        .width(300)
        .height(200)
    }
  }

  build() {
    Column({ space: 50 }) {
      Column() {
        Column() {
          Image($r('app.media.example'))
            .width(100)
            .height(100)
            .margin(100)
            .bindContextMenu(this.MyMenu, ResponseType.LongPress,
              {
                preview: this.MyPreview,
                previewAnimationOptions: {
                  hoverScale: [1.0, 0.8],
                  hoverScaleInterruption: true
                }
              })
            .onClick(() => {
              console.info('trigger onClick')
            })
        }
      }.width('100%')
    }
  }
}
```

### 示例14（设置预览图边框圆角半径）

该示例通过bindContextMenu配置[responseType](ts-appendix-enums.md#responsetype8).LongPress来实现功能。同时，在[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中配置preview属性的[MenuPreviewMode](arkts-arkui-common-comp-menupreviewmode-e.md)类型来设置菜单预览样式。最后，通过设置previewBorderRadius来实现预览图边框的圆角半径。

从API version 19开始，在[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中新增了previewBorderRadius属性。



```TypeScript
@Entry
@Component
struct Index {
  // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
  private iconStr: ResourceStr = $r("app.media.startIcon");

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
    }
  }

  build() {
    Column({ space: 50 }) {
      Column() {
        Column() {
          Text('preview-image')
            .width(200)
            .height(100)
            .textAlign(TextAlign.Center)
            .margin(100)
            .fontSize(30)
            .bindContextMenu(this.MyMenu, ResponseType.LongPress,
              {
                preview: MenuPreviewMode.IMAGE,
                previewBorderRadius: 50
              })
            .backgroundColor("#ff7fcdff")
        }
      }.width('100%')
    }
  }
}
```

### 示例15（bindMenu配置生命周期回调）

该示例为bindMenu11+配置生命周期回调。

从API version 20开始，在[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中新增了onWillAppear、onDidAppear、onWillDisappear和onDidDisappear属性。



```TypeScript
@Entry
@Component
struct Index {
  // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
  private iconStr: ResourceStr = $r("app.media.startIcon");
  @State isShown: boolean = false;
  @State textColor: Color = Color.Black;
  @State blueColor: Color = Color.Blue;
  @State onWillAppear: boolean = false;
  @State onDidAppear: boolean = false;
  @State onWillDisappear: boolean = false;
  @State onDidDisappear: boolean = false;

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
      MenuItem({ startIcon: this.iconStr, content: "菜单选项" })
    }
  }

  build() {
    Column() {
      Column({ space: 30 }) {
        Text('onWillAppear').fontColor(this.onWillAppear ? this.blueColor : this.textColor)
        Text('onDidAppear').fontColor(this.onDidAppear ? this.blueColor : this.textColor)
        Text('onWillDisappear').fontColor(this.onWillDisappear ? this.blueColor : this.textColor)
        Text('onDidDisappear').fontColor(this.onDidDisappear ? this.blueColor : this.textColor)
        Button('click')
          .onClick(() => {
            this.isShown = true;
          })
          .width(100)
          .height(50)
        Text('callback')
          .width(200)
          .height(100)
          .textAlign(TextAlign.Center)
          .fontSize(20)
          .fontColor(this.textColor)
          .bindMenu(this.isShown, this.MyMenu,
            {
              onWillAppear: () => {
                console.info("menu cycle life onWillAppear");
                this.onWillAppear = true;
              },
              onDidAppear: () => {
                console.info("menu cycle life onDidAppear");
                this.onDidAppear = true;
              },
              onWillDisappear: () => {
                this.isShown = false;
                console.info("menu cycle life onWillDisappear");
                this.onWillDisappear = true;
              },
              onDidDisappear: () => {
                console.info("menu cycle life onDidDisappear");
                this.onDidDisappear = true;
              }
            })
      }
    }.width('100%')
  }
}
```

### 示例16（设置菜单蒙层）

该示例为bindMenu通过配置mask属性设置菜单蒙层。

从API version 20开始，在[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中新增了mask属性。



```TypeScript
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State startIconModifier: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_star'))
  @State isShow: boolean = false;

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({
        symbolStartIcon: this.startIconModifier,
        content: "新建文件夹",
      })
      MenuItem({
        symbolStartIcon: this.startIconModifier,
        content: "排序方式",
      })
      MenuItem({
        symbolStartIcon: this.startIconModifier,
        content: "查看方式",
      })
    }
  }

  build() {
    Button('bindMenu')
      .position({ top: 80, left: 80 })
      .onClick(() => {
        this.isShow = !this.isShow;
      })
      .bindMenu(this.isShow, this.MyMenu, {
        mask: { color: 'rgba(23,169,141,0.5)', backgroundBlurStyle: BlurStyle.Thin }
      })
  }
}
```

### 示例17（bindMenu设置下拉菜单外描边样式）

该示例为bindMenu通过配置outlineWidth和outlineColor属性设置下拉菜单外描边样式。

从API version 20开始，在[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中新增了outlineWidth和outlineColor属性。



```TypeScript
@Entry
@Component
struct Index {
  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ content: "菜单选项" })
      MenuItem({ content: "菜单选项" })
      MenuItem({ content: "菜单选项" })
    }.width(200)
  }

  build() {
    Column({ space: 50 }) {
      Column() {
        Column() {
          Text('click for Menu')
            .width(200)
            .height(100)
            .textAlign(TextAlign.Center)
            .margin(100)
            .fontSize(30)
            .bindMenu(this.MyMenu,
              {
                outlineWidth: '5vp',
                outlineColor: Color.Blue
              })
        }
      }
      .width('100%')
      .height('100%')
      .backgroundColor('#F0F2F5')
    }
  }
}
```

### 示例18（bindMenu传入带参数的CustomBuilder）

该示例通过在bindMenu中传入带参数的CustomBuilder来配置菜单的具体属性。



```TypeScript
@Entry
@Component
struct Index {
  @State menuItemList: string[] = ['新建', '历史', '书签', '设置']

  @Builder
  MenuBuilder(itemList: string[]) {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center }) {
      ForEach(itemList, (item: string, index) => {
        Row() {
          Text(item)
            .width('100%')
            .height(32)
            .fontWeight(400)
            .fontSize(14)
            .fontColor(Color.Black)
            .textAlign(TextAlign.Center)
        }
        .onClick(() => {
          console.info('handle' + item + 'Clicked!')
        })
        if (index != itemList.length - 1) {
          Divider().height(10).width('80%').color('#ccc')
        }
      })
    }
    .width(100)
  }

  build() {
    Column() {
      Text('click for Menu')
        .bindMenu(this.MenuBuilder(this.menuItemList))
    }
    .height('100%')
    .width('100%')
    .backgroundColor('#f0f0f0')
  }
}
```

### 示例19（根据触发方式弹出不同内容的菜单）

该示例通过在[bindContextMenuWithResponse](arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenuwithresponse)中传入CustomBuilderT<ResponseType>给目标组件绑定菜单，组件会在UI函数中返回弹出菜单的触发方式，开发者可根据返回的触发方式实现差异化显示。

从API version 23开始，新增了bindContextMenuWithResponse的接口。



```TypeScript
@Entry
@Component
struct Index {
  @State longPress: string = 'LONG_PRESS';
  @State rightClick: string = 'RIGHT_CLICK';

  @Builder
  MenuBuilderWithParam(type: ResponseType) {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('Current ResponseType = ' + (type === ResponseType.RightClick ? 'RIGHT_CLICK' : 'LONG_PRESS'))
      Divider().height(10)
      if (type === ResponseType.LongPress) {
        Text('Item: ' + this.longPress)
          .fontSize(20)
          .width(200)
          .height(20)
          .textAlign(TextAlign.Center)
      }
      if (type === ResponseType.RightClick) {
        Text('Item: ' + this.rightClick)
          .fontSize(20)
          .width(200)
          .height(20)
          .textAlign(TextAlign.Center)
      }
    }
  }

  build() {
    Stack() {
      Button('BindContextMenu长按和右键点击触发菜单')
        .bindContextMenuWithResponse(this.MenuBuilderWithParam, {
          enableArrow: true,
        })
    }
    .height('100%')
    .width('100%')
    .backgroundColor('#f0f0f0')
  }
}
```

### 示例20（设置菜单避让软键盘）

该示例通过在bindMenu中配置keyboardAvoidMode设置菜单避让软键盘，通过minKeyboardAvoidDistance设置菜单避让软键盘的最小距离。

从API version 23开始，[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中新增keyboardAvoidMode、minKeyboardAvoidDistance属性。



```TypeScript
import { inputMethod } from '@kit.IMEKit';
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private inputController: inputMethod.InputMethodController = inputMethod.getController();

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ content: 'MenuItemContent' })
      MenuItem({ content: 'MenuItemContent' })
      MenuItem({ content: 'MenuItemContent' })
      MenuItem({ content: 'MenuItemContent' })
      MenuItem({ content: 'MenuItemContent' })
    }
  }

  build() {
    RelativeContainer() {
      Button('Click Show Menu')
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center },
        })
        .bindMenu(this.MyMenu, {
          keyboardAvoidMode: MenuKeyboardAvoidMode.TRANSLATE_AND_RESIZE,
          minKeyboardAvoidDistance: LengthMetrics.vp(20)
        })
        .onClick(() => {
          setTimeout(() => {
            this.attachAndListener()
          }, 2000)
        })
    }
    .height('100%')
    .width('100%')

  }

  async attachAndListener() {
    focusControl.requestFocus('Index')
    try {
      await this.inputController.attach(true, {
        inputAttribute: {
          textInputType: inputMethod.TextInputType.TEXT,
          enterKeyType: inputMethod.EnterKeyType.SEARCH
        }
      })
    } catch (err) {
      console.error('Fail to attach')
    }
  }
}
```

### 示例21（设置菜单相对于绑定组件左上角的弹出位置）

该示例通过设置[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中的anchorPosition属性，实现了菜单相对于绑定组件左上角弹出的效果。

从API version 20开始，在ContextMenuOptions中新增了anchorPosition属性。



```TypeScript
@Entry
@Component
struct Index {
  // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
  private iconStr: ResourceStr = $r('app.media.startIcon');
  @State isShown: boolean = false;

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: '菜单选项' })
      MenuItem({ startIcon: this.iconStr, content: '菜单选项' })
      MenuItem({ startIcon: this.iconStr, content: '菜单选项' })
    }
  }

  @State menuAnchorPositionIndex: number = 0;
  private menuAnchorPositionArray: Array<Position> = new Array<Position>(
    { x: 0, y: 0 },
    { x: 150, y: 0 },
    { x: 0, y: 150 },
    { x: 150, y: 150 },
  );

  build() {
    Column({ space: 50 }) {
      Column() {
        Column() {
          Text('Test Menu AnchorPosition')
            .width(500)
            .height(100)
            .textAlign(TextAlign.Center)
            .margin(100)
            .fontSize(30)
            .bindContextMenu(this.isShown, this.MyMenu,
              {
                anchorPosition: this.menuAnchorPositionArray[this.menuAnchorPositionIndex],
                aboutToDisappear: () => {
                  this.isShown = false;
                }
              })
          Button('click')
            .margin(5)
            .onClick(() => {
              this.isShown = true;
            })

          Button('AnchorPosition change')
            .margin(5)
            .onClick(() => {
              this.menuAnchorPositionIndex++;
              if (this.menuAnchorPositionIndex >= this.menuAnchorPositionArray.length) {
                this.menuAnchorPositionIndex = 0;
              }
            })
          Text('Current x: ' + this.menuAnchorPositionArray[this.menuAnchorPositionIndex]?.x +
            ' , y: ' + this.menuAnchorPositionArray[this.menuAnchorPositionIndex]?.y)
        }
      }.width('100%')
    }
  }
}
```

### 示例22（设置菜单的最大高度）

该示例为bindContextMenu通过配置[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中的maxHeight属性，设置菜单的最大高度。

未设置maxHeight属性时，默认按照菜单的最大高度（可用高度的80%），可展示全部列表项，通过设置最大高度为窗口可用高度的50%时，仅能显示8个列表项。

从API版本26.0.0开始，在ContextMenuOptions中新增了maxHeight属性。



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
  private iconStr: ResourceStr = $r('app.media.startIcon');

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: 'MenuItem1' })
      MenuItem({ startIcon: this.iconStr, content: 'MenuItem2' })
      MenuItem({ startIcon: this.iconStr, content: 'MenuItem3' })
      MenuItem({ startIcon: this.iconStr, content: 'MenuItem4' })
      MenuItem({ startIcon: this.iconStr, content: 'MenuItem5' })
      MenuItem({ startIcon: this.iconStr, content: 'MenuItem6' })
      MenuItem({ startIcon: this.iconStr, content: 'MenuItem7' })
      MenuItem({ startIcon: this.iconStr, content: 'MenuItem8' })
      MenuItem({ startIcon: this.iconStr, content: 'MenuItem9' })
    }
  }

  build() {
    Column({ space: 50 }) {
      Column() {
        Column() {
          Text('LongPress-image')
            .width(200)
            .height(100)
            .textAlign(TextAlign.Center)
            .margin(100)
            .fontSize(30)
            .bindContextMenu(this.MyMenu, ResponseType.LongPress,
              {
                maxHeight: LengthMetrics.percent(50)
              })
            .backgroundColor('#ff7fcdff')
        }
      }.width('100%')
    }
  }
}
```

### 示例23（设置菜单与目标组件间距）

该示例通过设置[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中的targetSpace属性，介绍如何增加菜单与目标组件之间的间距。

从API版本26.0.0开始，在ContextMenuOptions中新增了targetSpace属性。



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Alone {
  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: $r('app.media.startIcon'), content: '菜单选项1' })
      MenuItem({ startIcon: $r('app.media.startIcon'), content: '菜单选项2' })
      MenuItem({ startIcon: $r('app.media.startIcon'), content: '菜单选项3' })
    }
  }

  build() {
    Column() {
      Stack() {
        Column()
          .width(120 + 40 * 2)
          .height(120 + 40 * 2)
          .borderWidth(2)
          .borderColor(Color.Orange)
          .borderStyle(BorderStyle.Dotted)

        Image($r('app.media.startIcon'))
          .width(120)
          .height(120)
          .bindMenu(this.MyMenu,
            {
              targetSpace: LengthMetrics.vp(40)
            })
      }.height('75%')
      .width('100%')
    }
    .height('100%')
    .width('100%')
  }
}
```

### 示例24（设置菜单的沉浸光感）

该示例通过[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中的systemMaterial属性设置组件的系统材质，实现了菜单的沉浸光感视效。设置系统材质后，Menu弹出过程中会有非线性形变和边缘流光。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在ContextMenuOptions中新增了systemMaterial属性。

未设置系统材质时：



设置系统材质后：



```TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: $r('app.media.startIcon'), content: '菜单选项' })
      MenuItem({ startIcon: $r('app.media.startIcon'), content: '菜单选项' })
      MenuItem({ startIcon: $r('app.media.startIcon'), content: '菜单选项' })
    }
  }

  build() {
    Stack() {
      Button('bindMenu with THICK material')
        .bindMenu(this.MyMenu, {
          systemMaterial: new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.THICK
          })
        })
    }
    .height('100%')
    .width('100%')
    // 请开发者替换为实际资源文件
    .backgroundImage($r("app.media.img"))
  }
}
```

### 示例25（使用gridStyle设置栅格菜单）

该示例展示了如何在[bindContextMenuByIsShow](arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenubyisshow)中使用gridStyle设置栅格菜单样式。通过设置count、horizontalSize和position属性，可以自定义菜单的栅格布局。

从API版本26.0.0开始，新增了[bindContextMenuByIsShow](arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenubyisshow)的接口；在[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)中新增了gridStyle属性。

```TypeScript
@Entry
@Component
struct ContextMenuGridStyleExample {
  @State isShown: boolean = false;

  @Builder
  MyMenu() {
   Menu() {
     MenuItem({ startIcon: $r('app.media.startIcon'), content: '复制' })
     MenuItem({ startIcon: $r('app.media.startIcon'), content: '粘贴' })
     MenuItem({ startIcon: $r('app.media.startIcon'), content: '剪切' })
     MenuItem({ startIcon: $r('app.media.startIcon'), content: '删除' })
     MenuItem({ startIcon: $r('app.media.startIcon'), content: '分享' })
     MenuItem({ startIcon: $r('app.media.startIcon'), content: '全选' })
     MenuItem({ startIcon: $r('app.media.startIcon'), content: '翻译' })
     MenuItem({ startIcon: $r('app.media.startIcon'), content: '收藏' })
   }
   .width(150)
  }

  build() {
    Column({ space: 20 }) {
      Text('bindContextMenuByIsShow grid menu')
        .fontSize(20)
        .bindContextMenuByIsShow(this.isShown, this.MyMenu, {
          gridStyle: {
            count: 4,
            horizontalSize: 3,
            position: MenuGridPosition.BOTTOM
          },
          onWillDisappear: () => {
            this.isShown = false;
          },
        })
        .onClick(() => {
          this.isShown = true;
        })
    }
    .width('100%')
    .margin({ top: 50 })
  }
}
```

### 示例1（获取鼠标事件相关参数）

该示例通过按钮设置了鼠标事件，通过鼠标点击按钮可以触发[onMouse](#onmouse)事件，获取鼠标事件相关参数。从API version 15开始，可以获取鼠标事件[MouseEvent](#mouseevent对象说明)的targetDisplayId、rawDeltaX、rawDeltaY、pressedButtons等参数。

鼠标滚轮的处理请参考[轴事件示例](ts-universal-events-axis.md#示例)。

示意图：

鼠标点击时：



```TypeScript
// xxx.ets
@Entry
@Component
struct MouseEventExample {
  @State hoverText: string = 'no hover';
  @State mouseText: string = '';
  @State action: string = '';
  @State mouseBtn: string = '';
  @State color: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Button(this.hoverText)
        .width(180)
        .height(80)
        .backgroundColor(this.color)
        .fontSize(24)
        .onHover((isHover: boolean) => {
          // 通过onHover事件动态修改按钮在是否有鼠标悬浮时的文本内容与背景颜色
          if (isHover) {
            this.hoverText = 'hover';
            this.color = Color.Pink;
          } else {
            this.hoverText = 'no hover';
            this.color = Color.Blue;
          }
        })
      Button('onMouse')
        .width(180).height(80)
        .fontSize(24)
        // onMouse监听鼠标事件，解析按键、动作、坐标等信息并拼接展示
        .onMouse((event: MouseEvent): void => {
          if (event) {
            // 判断触发的鼠标按键类型
            switch (event.button) {
              case MouseButton.None:
                this.mouseBtn = 'None';
                break;
              case MouseButton.Left:
                this.mouseBtn = 'Left';
                break;
              case MouseButton.Right:
                this.mouseBtn = 'Right';
                break;
              case MouseButton.Back:
                this.mouseBtn = 'Back';
                break;
              case MouseButton.Forward:
                this.mouseBtn = 'Forward';
                break;
              case MouseButton.Middle:
                this.mouseBtn = 'Middle';
                break;
            }
            // 判断触发的鼠标动作类型
            switch (event.action) {
              case MouseAction.Press:
                this.action = 'Press';
                break;
              case MouseAction.Move:
                this.action = 'Move';
                break;
              case MouseAction.Release:
                this.action = 'Release';
                break;
              case MouseAction.ENTER_WINDOW:
                this.action = 'ENTER_WINDOW';
                break;
              case MouseAction.LEAVE_WINDOW:
                this.action = 'LEAVE_WINDOW';
                break;
            }
            // 拼接鼠标事件全量信息并展示
            this.mouseText = 'onMouse:\nButton = ' + this.mouseBtn +
              '\nAction = ' + this.action + '\nXY=(' + event.x + ',' + event.y + ')' +
              '\nwindowXY=(' + event.windowX + ',' + event.windowY + ')' +
              '\ntargetDisplayId = ' + event.targetDisplayId +
              '\nrawDeltaX = ' + event.rawDeltaX +
              '\nrawDeltaY = ' + event.rawDeltaY +
              '\nlength = ' + event.pressedButtons?.length;
          }
        })
      Text(this.mouseText)
    }.padding({ top: 30 }).width('100%')
  }
}
```

### 示例2（获取当前帧历史点）

该示例通过调用[getHistoricalPoints](#gethistoricalpoints)接口，获取当前帧的历史点，可以用来实现更平滑的绘制等操作。

从API版本26.0.0开始，新增getHistoricalPoints接口。

```TypeScript
@Entry
@Component
struct HistoricalPointsExample {
  historicalPointsInfo: string = '';

  build() {
    Column() {
      Button('鼠标移动获取历史点')
        .width(180)
        .height(80)
        .onMouse((event: MouseEvent) => {
          if (event.action === MouseAction.Move) {
            // 调用getHistoricalPoints接口获取当前帧历史点信息
            const historicalPoints = event.getHistoricalPoints?.();
            if (historicalPoints) {
              this.historicalPointsInfo = `历史点数量：${historicalPoints.length}`;
              historicalPoints.forEach((point: MouseHistoricalPoint, index: number) => {
                this.historicalPointsInfo += `\n点${index}: `
                  + `x = ${point.x}, y = ${point.y}, windowX = ${point.windowX}, windowY = ${point.windowY}, `
                  + `displayX = ${point.displayX}, displayY = ${point.displayY}, `
                  + `globalDisplayX = ${point.globalDisplayX}, globalDisplayY = ${point.globalDisplayY}, `
                  + `timestamp = ${point.timestamp}`;
              });
              console.info(this.historicalPointsInfo);
            }
          }
        })
    }.padding({ top: 30 })
    .width('100%')
    .height('100%')
  }
}
```

### 示例3（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取鼠标位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct GetCurrentLocalPositionExample {
  @State positionText: string = '';
  @State textOffsetY: number = 0;

  build() {
    Column() {
      Button('获取鼠标位置相对于当前组件实时位置左上角的坐标').translate({ y: this.textOffsetY })
        .onMouse((event: MouseEvent) => {
          if (event) {
            // 移动组件后延迟获取鼠标相对于组件实时位置左上角的坐标
            this.textOffsetY = -200;
            setTimeout(() => {
              let localPos: Coordinate2D | undefined = event.getCurrentLocalPosition?.();
              this.positionText = `相对于当前组件实时位置左上角的坐标：\n  x: ${localPos?.x}\n  y: ${localPos?.y}`;
            }, 2000);
          }
        })

      Text(this.positionText)
    }.width('100%')
  }
}
```

该示例通过配置visibility的不同值，实现不同的显隐控制效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct VisibilityExample {
  build() {
    Column() {
      Column() {
        // 隐藏不参与占位
        Text('None').fontSize(9).width('90%').fontColor(0xCCCCCC);
        Row().visibility(Visibility.None).width('90%').height(80).backgroundColor(0xAFEEEE);

        // 隐藏参与占位
        Text('Hidden').fontSize(9).width('90%').fontColor(0xCCCCCC);
        Row().visibility(Visibility.Hidden).width('90%').height(80).backgroundColor(0xAFEEEE);

        // 正常显示，组件默认的显示模式
        Text('Visible').fontSize(9).width('90%').fontColor(0xCCCCCC);
        Row().visibility(Visibility.Visible).width('90%').height(80).backgroundColor(0xAFEEEE);
      }.width('90%').border({ width: 1 });
    }.width('100%').margin({ top: 5 });
  }
}
```

### 示例1（设置事件派发策略为FORWARD_COMPETITION）

在该示例中，点击List下方空白区域后拖动，可使List滑动。点击Button按钮时，Button会响应onClick事件。



```TypeScript
// xxx.ets
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct ListExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
  promptAction: PromptAction = this.getUIContext().getPromptAction();
  @State text: string = 'Button';

  build() {
    Column() {
      List({ space: 12, initialIndex: 0 }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('Item ' + item)
              .width('100%')
              .height(56)
              .fontSize(16)
              .textAlign(TextAlign.Start)
          }.borderRadius(24)
          .backgroundColor(Color.White)
          .padding({ left: 12, right: 12 })
        }, (item: number) => item.toString())
      }
      .listDirection(Axis.Vertical)
      .scrollBar(BarState.Off)
      .edgeEffect(EdgeEffect.Spring)
      .onScrollIndex((start: number, end: number) => {
        console.info(`first ${start}`);
        console.info(`last ${end}`);
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onScroll scrollState = ScrollState ${scrollState.toString()}, scrollOffset = ${scrollOffset}`);
      })
      .width('100%')
      .height('65%')
      .id('MyList')

      Button(this.text)
        .width(312)
        .height(40)
        .id('MyButton')
        .fontSize(16)
        .fontWeight(FontWeight.Medium)
        .margin({ top: 80 })
        .onClick(() => {
          this.text = 'click the button';
          this.promptAction.showToast({ message: 'you click the button.', duration: 3000 });
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xF1F3F5)
    .justifyContent(FlexAlign.End)
    .padding({ left: 12, right: 12, bottom: 24 })
    .onChildTouchTest((touchInfo) => {
      for (let info of touchInfo) {
        if (info.id === 'MyList') {
          return { id: info.id, strategy: TouchTestStrategy.FORWARD_COMPETITION }
        }
      }
      return { strategy: TouchTestStrategy.DEFAULT }
    })
  }
}
```

### 示例2（设置事件派发策略为FORWARD）

点击List下方空白区域后拖动，可以滑动List。点击Button按钮时，Button不会响应onClick事件。



```TypeScript
// xxx.ets
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct ListExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
  promptAction: PromptAction = this.getUIContext().getPromptAction();
  @State text: string = 'Button';

  build() {
    Column() {
      List({ space: 12, initialIndex: 0 }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('Item ' + item)
              .width('100%')
              .height(56)
              .fontSize(16)
              .textAlign(TextAlign.Start)
          }.borderRadius(24)
          .backgroundColor(Color.White)
          .padding({ left: 12, right: 12 })
        }, (item: number) => item.toString())
      }
      .listDirection(Axis.Vertical)
      .scrollBar(BarState.Off)
      .edgeEffect(EdgeEffect.Spring)
      .onScrollIndex((start: number, end: number) => {
        console.info(`first ${start}`);
        console.info(`last ${end}`);
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onScroll scrollState = ScrollState ${scrollState.toString()}, scrollOffset = ${scrollOffset}`);
      })
      .width('100%')
      .height('65%')
      .id('MyList')

      Button(this.text)
        .width(312)
        .height(40)
        .id('MyButton')
        .fontSize(16)
        .fontWeight(FontWeight.Medium)
        .margin({ top: 80 })
        .onClick(() => {
          this.text = 'click the button';
          this.promptAction.showToast({ message: 'you click the button.', duration: 3000 });
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xF1F3F5)
    .justifyContent(FlexAlign.End)
    .padding({ left: 12, right: 12, bottom: 24 })
    .onChildTouchTest((touchInfo) => {
      for (let info of touchInfo) {
        if (info.id === 'MyList') {
          return { id: info.id, strategy: TouchTestStrategy.FORWARD }
        }
      }
      return { strategy: TouchTestStrategy.DEFAULT }
    })
  }
}
```

### 示例3（设置事件派发策略为DEFAULT）

点击List下方空白区域后拖动，List不会滑动。点击Button按钮时，Button会响应onClick事件。

```TypeScript
// xxx.ets
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct ListExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
  promptAction: PromptAction = this.getUIContext().getPromptAction();
  @State text: string = 'Button';

  build() {
    Column() {
      List({ space: 12, initialIndex: 0 }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('Item ' + item)
              .width('100%')
              .height(56)
              .fontSize(16)
              .textAlign(TextAlign.Start)
          }.borderRadius(24)
          .backgroundColor(Color.White)
          .padding({ left: 12, right: 12 })
        }, (item: number) => item.toString())
      }
      .listDirection(Axis.Vertical)
      .scrollBar(BarState.Off)
      .edgeEffect(EdgeEffect.Spring)
      .onScrollIndex((start: number, end: number) => {
        console.info(`first ${start}`);
        console.info(`last ${end}`);
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onScroll scrollState = ScrollState ${scrollState.toString()}, scrollOffset = ${scrollOffset}`);
      })
      .width('100%')
      .height('65%')
      .id('MyList')

      Button(this.text)
        .width(312)
        .height(40)
        .id('MyButton')
        .fontSize(16)
        .fontWeight(FontWeight.Medium)
        .margin({ top: 80 })
        .onClick(() => {
          this.text = 'click the button';
          this.promptAction.showToast({ message: 'you click the button.', duration: 3000 });
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xF1F3F5)
    .justifyContent(FlexAlign.End)
    .padding({ left: 12, right: 12, bottom: 24 })
    .onChildTouchTest(() => {
      return { strategy: TouchTestStrategy.DEFAULT }
    })
  }
}
```

```TypeScript
// xxx.ets
@Entry
@Component
struct TouchableExample {
  @State text1: string = '';
  @State text2: string = '';

  build() {
    Stack() {
      Rect()
        .fill(Color.Gray).width(150).height(150)
        .onClick(() => {
          console.info(this.text1 = 'Rect Clicked');
        })
        .overlay(this.text1, { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
      Ellipse()
        .fill(Color.Pink).width(150).height(80)
        .touchable(false) // 点击Ellipse区域，不会打印 “Ellipse Clicked”
        .onClick(() => {
          console.info(this.text2 = 'Ellipse Clicked');
        })
        .overlay(this.text2, { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
    }.margin(100);
  }
}
```

该示例通过restoreId设置了List组件的分布式迁移标识。

```TypeScript
// xxx.ets
@Entry
@Component
struct RestoreIdExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  build() {
    Column() {
      List({ space: 20 }) {
        ForEach(this.arr, (item:number) => {
          ListItem() {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(Color.Pink)
          }
        }, (item:number) => (item.toString()))
      }
      .restoreId(1);
    }
  }
}
```

该示例主要演示使用[animateToImmediately](#animatetoimmediately)接口实现显式动画立即下发。

```TypeScript
// xxx.ets
@Entry
@Component
struct AnimateToImmediatelyExample {
  @State widthSize: number = 250;
  @State heightSize: number = 100;
  @State opacitySize: number = 0;
  private flag: boolean = true;

  build() {
    Column() {
      Column()
      .width(this.widthSize)
      .height(this.heightSize)
      .backgroundColor(Color.Green)
      .opacity(this.opacitySize)
      Button('change size')
        .margin(30)
        .onClick(() => {
          // 通过if/else分支对比演示：animateToImmediately立即下发动画与animateTo延迟下发动画的效果差异
          // flag切换演示场景：true时透明度立即下发、尺寸延迟下发；false时尺寸立即下发、透明度延迟下发
          if (this.flag) {
            animateToImmediately({
              delay: 0,
              duration: 1000
            }, () => {
              this.opacitySize = 1;
            })
            this.getUIContext()?.animateTo({
              delay: 1000,
              duration: 1000
            }, () => {
              this.widthSize = 150;
              this.heightSize = 60;
            })
          } else {
            animateToImmediately({
              delay: 0,
              duration: 1000
            }, () => {
              this.widthSize = 250;
              this.heightSize = 100;
            })
            this.getUIContext()?.animateTo({
              delay: 1000,
              duration: 1000
            }, () => {
              this.opacitySize = 0;
            })
          }
          this.flag = !this.flag;
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

该示例主要演示如何设置组件进行位移动画时的运动路径。此方法仅配置运动路径参数，需配合animateTo等动画触发方法及组件属性状态变化才能产生实际的位移动画效果，单独设置motionPath不会触发动画。

```TypeScript
// xxx.ets
@Entry
@Component
struct MotionPathExample {
  @State toggle: boolean = true;

  build() {
    Column() {
      Button('click me').margin(50)
        .motionPath({
          path: 'Mstart.x start.y L300 200 L300 500 Lend.x end.y',
          from: 0.0,
          to: 1.0,
          rotatable: true
        }) // 设置运动路径：从起点经(300,200)、(300,500)到终点
        .onClick(() => {
          this.getUIContext()?.animateTo({ duration: 4000, curve: Curve.Linear }, () => {
            this.toggle = !this.toggle; // 通过this.toggle变化组件的位置
          });
        })
    }.width('100%').height('100%').alignItems(this.toggle ? HorizontalAlign.Start : HorizontalAlign.Center)
  }
}
```

### 示例1（获取点击事件相关参数）

该示例通过按钮设置点击事件[ClickEvent](arkts-arkui-common-comp-clickevent-i.md)，点击按钮可获取点击事件的相关参数。



```TypeScript
// xxx.ets
@Entry
@Component
struct ClickExample {
  @State text: string = '';

  build() {
    Column() {
      Row({ space: 20 }) {
        Button('Click1').width(100).height(40).id('click1')
          .onClick((event?: ClickEvent) => {
            if (event) {
              this.text =
                `Click Point:\n  windowX:${event.windowX}\n  windowY:${event.windowY}\n  x:${event.x}\n  y:${event.y}\n target:\n  component globalPos:(${event.target.area.globalPosition.x},${event.target.area.globalPosition.y})\n  width:${event.target.area.width}\n  height:${event.target.area.height}\n  id:${event.target.id}\ntargetDisplayId:${event.targetDisplayId}\ntimestamp:${event.timestamp}`;
            }
          }, 20)
        Button('Click2').width(200).height(50).id('click2')
          .onClick((event?: ClickEvent) => {
            if (event) {
              this.text =
                `Click Point:\n  windowX:${event.windowX}\n  windowY:${event.windowY}\n  x:${event.x}\n  y:${event.y}\n target:\n  component globalPos:(${event.target.area.globalPosition.x},${event.target.area.globalPosition.y})\n  width:${event.target.area.width}\n  height:${event.target.area.height}\n  id:${event.target.id}\ntargetDisplayId:${event.targetDisplayId}\ntimestamp:${event.timestamp}`;
            }
          }, 20)
      }.margin(20)

      Text(this.text).margin(15)
    }.width('100%')
  }
}
```

### 示例2（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取当前组件基于其实时位置的左上角坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct GetCurrentLocalPositionExample {
  @State positionText: string = '';
  @State textOffsetY: number = 0;

  build() {
    Column() {
      Button('点击获取点击位置相对于当前组件实时位置左上角的坐标').translate({ y: this.textOffsetY })
        .onClick((event?: ClickEvent) => {
          if (event) {
            this.textOffsetY = -200;
            // 组件位置变化后，延迟获取点击位置相对于组件实时位置左上角的坐标。
            setTimeout(() => {
              let localPos: Coordinate2D | undefined = event.getCurrentLocalPosition?.();
              this.positionText = `相对于当前组件实时位置左上角的坐标:\n  x: ${localPos?.x}\n  y: ${localPos?.y}`;
            }, 2000);
          }
        })

      Text(this.positionText)
    }.width('100%')
  }
}
```

当父组件出现1px的缝隙时，应利用pixelRound来指导布局调整。

```TypeScript
@Entry
@Component
struct PixelRoundExample {
    // 状态变量：记录父组件的当前宽度，用于演示浮点数宽度变化
    @State curWidth : number = 300;

    build() {
        Column() {
            Button() {
                Text(this.curWidth.toString())
            }
            .onClick(() => {
                // 每次点击增加0.1px，模拟浮点数宽度
                this.curWidth += 0.1;
            })
            .height(200)
            .width(200)
            .backgroundColor('rgb(213, 213, 213)')

            Blank().height(20)

            Row() {
                // 子组件：100%填充父容器
                Row() {
                }
                .width('100%')
                .height('100%')
                .backgroundColor(Color.Yellow)
                // 关闭子组件start和end方向的像素取整
                .pixelRound({
                    start : PixelRoundCalcPolicy.NO_FORCE_ROUND,
                    end : PixelRoundCalcPolicy.NO_FORCE_ROUND,
                })
            }
            .width(this.curWidth.toString() + 'px')
            .height('300.6px') // 使用浮点数高度测试上下方向的取整表现
            .backgroundColor(Color.Red)
            // 关闭父组件start和end方向的像素取整
            .pixelRound({
                start : PixelRoundCalcPolicy.NO_FORCE_ROUND,
                end : PixelRoundCalcPolicy.NO_FORCE_ROUND,
            })
        }
        .width('100%')
        .height('100%')
        .backgroundColor('#ffe5e5e5')
    }
}
```

### 示例1（使用同一接口实现图片出现消失）

该示例主要演示如何通过同一[TransitionEffect](#transitioneffect10对象说明)来实现图片的出现与消失，出现和消失互为逆过程。

示意图：

```TypeScript
// xxx.ets
@Entry
@Component
struct TransitionEffectExample1 {
  @State flag: boolean = true;
  @State show: string = 'show';

  build() {
    Column() {
      Button(this.show).width(80).height(30).margin(30)
        .onClick(() => {
          // 点击Button控制Image的显示和消失
          if (this.flag) {
            this.show = 'hide';
          } else {
            this.show = 'show';
          }
          this.flag = !this.flag;
        })
      if (this.flag) {
        // Image的显示和消失配置为相同的过渡效果（出现和消失互为逆过程）
        // 出现时从指定的透明度为0、绕z轴旋转180°的状态，变为默认的透明度为1、旋转角为0的状态，透明度与旋转动画时长都为2000ms
        // 消失时从默认的透明度为1、旋转角为0的状态，变为指定的透明度为0、绕z轴旋转180°的状态，透明度与旋转动画时长都为2000ms
        // $r('app.media.testImg')需要替换为开发者所需的图像资源文件。
        Image($r('app.media.testImg')).width(200).height(200)
          .transition(TransitionEffect.OPACITY.animation({ duration: 2000, curve: Curve.Ease }).combine(
            TransitionEffect.rotate({ z: 1, angle: 180 })
          ))
      }
    }.width('100%')
  }
}
```

### 示例2（使用不同接口实现图片出现消失）

该示例主要演示使用不同[TransitionEffect](#transitioneffect10对象说明)来实现图片的出现和消失。

示意图：

```TypeScript
// xxx.ets
@Entry
@Component
struct TransitionEffectExample2 {
  @State flag: boolean = true;
  @State show: string = 'show';

  build() {
    Column() {
      Button(this.show).width(80).height(30).margin(30)
        .onClick(() => {
          // 点击Button控制Image的显示和消失
          if (this.flag) {
            this.show = 'hide';
          } else {
            this.show = 'show';
          }
          this.getUIContext().animateTo({ duration: 2000 }, () => {
            // 第一张图的TransitionEffect包含了animation，transition的动画参数由TransitionEffect指定
            // 第二张图的TransitionEffect不包含animation，transition的动画参数由animateTo指定
            this.flag = !this.flag;
          });
        })
      if (this.flag) {
        // Image的显示和消失配置为不同的过渡效果
        // 出现时做从指定的透明度为0变为默认的透明度1的动画，该动画时长为1000ms，以及做从指定的绕z轴旋转180°变为默认的旋转角为0的动画，该动画1000ms后播放，时长为1000ms
        // 消失时做从默认的透明度为1变为指定的透明度0的动画，该动画1000ms后播放，时长为1000ms，以及做从默认的旋转角0变为指定的绕z轴旋转180°的动画，该动画时长为1000ms
        // $r('app.media.testImg')需要替换为开发者所需的图像资源文件。
        Image($r('app.media.testImg')).width(200).height(200)
          .transition(
            TransitionEffect.asymmetric(
              TransitionEffect.OPACITY.animation({ duration: 1000 }).combine(
              TransitionEffect.rotate({ z: 1, angle: 180 }).animation({ delay: 1000, duration: 1000 }))
              ,
              TransitionEffect.OPACITY.animation({ delay: 1000, duration: 1000 }).combine(
              TransitionEffect.rotate({ z: 1, angle: 180 }).animation({ duration: 1000 }))
            )
          )
        // 出现时做从x方向和y方向scale都为0变为默认的x方向和y方向scale都为1的动画，该动画时长为animateTo中指定的2000ms
        // 消失时无转场效果
        // $r('app.media.testImg')需要替换为开发者所需的图像资源文件。
        Image($r('app.media.testImg')).width(200).height(200).margin({ top: 100 })
          .transition(
            TransitionEffect.asymmetric(
              TransitionEffect.scale({ x: 0, y: 0 }),
              TransitionEffect.IDENTITY
            )
          )
      }
    }.width('100%')
  }
}
```

### 示例3（设置父子组件为transition）

该示例主要演示通过父子组件都配置[transition](#transition)来实现图片的出现和消失。

示意图：

```TypeScript
// xxx.ets
@Entry
@Component
struct TransitionEffectExample3 {
  @State flag: boolean = true;
  @State show: string = 'show';

  build() {
    Column() {
      Button(this.show).width(80).height(30).margin(30)
        .onClick(() => {
          // 点击Button控制Image的显示和消失
          if (this.flag) {
            this.show = 'hide';
          } else {
            this.show = 'show';
          }
          this.flag = !this.flag;
        })
      if (this.flag) {
        // 当flag条件改变时，会触发id为"column1"、"image1"、"image2"的transition动画。
        // id为"column1"的组件是这棵新出现/消失的子树的根节点。
        Column() {
          Row() {
            // $r('app.media.testImg')需要替换为开发者所需的图像资源文件。
            Image($r('app.media.testImg')).width(150).height(150).id('image1')
              .transition(TransitionEffect.OPACITY.animation({ duration: 1000 }))
          }

          // $r('app.media.testImg')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.testImg'))
            .width(150)
            .height(150)
            .margin({ top: 50 })
            .id('image2')
            .transition(TransitionEffect.scale({ x: 0, y: 0 }).animation({ duration: 1000 }))
          Text('view').margin({ top: 50 })
        }
        .id('column1')
        // 根组件使用opacity(0.99)而非1，避免属性值等于默认值导致转场动画不触发
        .transition(TransitionEffect.opacity(0.99).animation({ duration: 1000 }),
          // 结束回调设置在消失的第一层节点上，确保能有消失的结束回调
          (transitionIn: boolean) => {
            console.info("transition finish, transitionIn:" + transitionIn);
          }
        )
      }
    }.width('100%')
  }
}
```

### 示例4（visibility切换时的双动画复合效果）

该示例演示当[visibility](ts-universal-attributes-visibility.md#visibility)在Visibility.Visible与Visibility.None之间切换时，[transition](#transition)动画与布局动画叠加形成双动画复合表现的效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct TransitionVisibilityExample {
  @State isVisible: boolean = true;

  build() {
    Column() {
      Button('toggle visibility').width(150).height(30).margin(30)
        .onClick(() => {
          this.getUIContext()?.animateTo({ duration: 1000 }, () => {
            this.isVisible = !this.isVisible;
          });
        })
      Column() {
        Text('Hello World')
          .fontSize(20)
          .fontColor(Color.White)
      }
      .width(200)
      .height(100)
      .backgroundColor('#317AF7')
      .justifyContent(FlexAlign.Center)
      .transition(TransitionEffect.OPACITY.animation({ duration: 1000 }))
      .visibility(this.isVisible ? Visibility.Visible : Visibility.None)
    }.width('100%').height('100%').justifyContent(FlexAlign.Center)
  }
}
```

### 示例1（嵌套滚动）

该示例通过shouldBuiltInRecognizerParallelWith和onGestureRecognizerJudgeBegin实现了嵌套滚动的功能。内部组件优先响应滑动手势，当内部组件滑动至顶部或底部时，外部组件能够接替滑动。



```TypeScript
// xxx.ets
@Entry
@Component
struct FatherControlChild {
  scroller: Scroller = new Scroller();
  scroller2: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  private childRecognizer: GestureRecognizer = new GestureRecognizer();
  private currentRecognizer: GestureRecognizer = new GestureRecognizer();
  private lastOffset: number = 0;

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) { // 外部滚动容器
        Column() {
          Text('Scroll Area')
            .width('90%')
            .height(150)
            .backgroundColor(0xFFFFFF)
            .borderRadius(15)
            .fontSize(16)
            .textAlign(TextAlign.Center)
            .margin({ top: 10 })
          Scroll(this.scroller2) { // 内部滚动容器
            Column() {
              Text('Scroll Area2')
                .width('90%')
                .height(150)
                .backgroundColor(0xFFFFFF)
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .margin({ top: 10 })
              Column() {
                ForEach(this.arr, (item: number) => {
                  Text(item.toString())
                    .width('90%')
                    .height(150)
                    .backgroundColor(0xFFFFFF)
                    .borderRadius(15)
                    .fontSize(16)
                    .textAlign(TextAlign.Center)
                    .margin({ top: 10 })
                }, (item: number) => item.toString())
              }.width('100%')
            }
          }
          .id('inner')
          .width('100%')
          .height(800)
        }.width('100%')
      }
      .id('outer')
      .height(600)
      .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
      .scrollBar(BarState.On) // 滚动条常驻显示
      .scrollBarColor(Color.Gray) // 滚动条颜色
      .scrollBarWidth(10) // 滚动条宽度
      .edgeEffect(EdgeEffect.None)
      .shouldBuiltInRecognizerParallelWith((current: GestureRecognizer, others: Array<GestureRecognizer>) => {
        for (let i = 0; i < others.length; i++) {
          let target = others[i].getEventTargetInfo();
          if (target) {
            if (target.getId() == 'inner' && others[i].isBuiltIn() &&
              others[i].getType() == GestureControl.GestureType.PAN_GESTURE) { // 找到将要组成并行手势的识别器
              this.currentRecognizer = current; // 保存当前组件的识别器
              this.childRecognizer = others[i]; // 保存将要组成并行手势的识别器
              return others[i]; // 返回将要组成并行手势的识别器
            }
          }
        }
        return undefined;
      })
      .onGestureRecognizerJudgeBegin((event: BaseGestureEvent, current: GestureRecognizer,
        others: Array<GestureRecognizer>) => { // 在识别器即将要成功时，根据当前组件状态，设置识别器使能状态
        if (current) {
          let target = current.getEventTargetInfo();
          if (target) {
            if (target.getId() == 'outer' && current.isBuiltIn() &&
              current.getType() == GestureControl.GestureType.PAN_GESTURE) {
              if (others) {
                for (let i = 0; i < others.length; i++) {
                  let target = others[i].getEventTargetInfo() as ScrollableTargetInfo;
                  if (target instanceof ScrollableTargetInfo && target.getId() == 'inner') { // 找到响应链上对应并行的识别器
                    let panEvent = event as PanGestureEvent;
                    if (target.isEnd()) { // 根据当前组件状态以及移动方向动态控制识别器使能状态
                      if (panEvent && panEvent.offsetY < 0) {
                        this.childRecognizer.setEnabled(false);
                        this.currentRecognizer.setEnabled(true);
                      } else {
                        this.childRecognizer.setEnabled(true);
                        this.currentRecognizer.setEnabled(false);
                      }
                    } else if (target.isBegin()) {
                      if (panEvent.offsetY > 0) {
                        this.childRecognizer.setEnabled(false);
                        this.currentRecognizer.setEnabled(true);
                      } else {
                        this.childRecognizer.setEnabled(true);
                        this.currentRecognizer.setEnabled(false);
                      }
                    } else {
                      this.childRecognizer.setEnabled(true);
                      this.currentRecognizer.setEnabled(false);
                    }
                  }
                }
              }
            }
          }
        }
        return GestureJudgeResult.CONTINUE;
      })
      .parallelGesture( // 绑定一个Pan手势作为动态控制器
        PanGesture()
          .onActionUpdate((event: GestureEvent) => {
            if (this.childRecognizer.getState() != GestureRecognizerState.SUCCESSFUL ||
              this.currentRecognizer.getState() != GestureRecognizerState.SUCCESSFUL) { // 如果识别器状态不是SUCCESSFUL，则不做控制
              return;
            }
            let target = this.childRecognizer.getEventTargetInfo() as ScrollableTargetInfo;
            let currentTarget = this.currentRecognizer.getEventTargetInfo() as ScrollableTargetInfo;
            if (target instanceof ScrollableTargetInfo && currentTarget instanceof ScrollableTargetInfo) {
              if (target.isEnd()) { // 在移动过程中实时根据当前组件状态，控制识别器的开闭状态
                if ((event.offsetY - this.lastOffset) < 0) {
                  this.childRecognizer.setEnabled(false);
                  if (currentTarget.isEnd()) {
                    this.currentRecognizer.setEnabled(false);
                  } else {
                    this.currentRecognizer.setEnabled(true);
                  }
                } else {
                  this.childRecognizer.setEnabled(true);
                  this.currentRecognizer.setEnabled(false);
                }
              } else if (target.isBegin()) {
                if ((event.offsetY - this.lastOffset) > 0) {
                  this.childRecognizer.setEnabled(false);
                  if (currentTarget.isBegin()) {
                    this.currentRecognizer.setEnabled(false);
                  } else {
                    this.currentRecognizer.setEnabled(true);
                  }
                } else {
                  this.childRecognizer.setEnabled(true);
                  this.currentRecognizer.setEnabled(false);
                }
              } else {
                this.childRecognizer.setEnabled(true);
                this.currentRecognizer.setEnabled(false);
              }
            }
            this.lastOffset = event.offsetY;
          })
      )
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### 示例2（嵌套场景下拦截内部容器手势）

本示例通过将参数exposeInnerGesture设置为true，实现了一级Tabs容器在嵌套二级Tabs的场景下，能够屏蔽二级Tabs内置Swiper的滑动手势，从而触发一级Tabs内置Swiper滑动手势的功能。

开发者自行定义变量记录内层Tabs的索引值，并通过该索引值判断滑动是否达到内层Tabs的边界。达到边界时，触发回调返回拒绝结果，屏蔽内层Tabs的滑动手势，使外层Tabs产生滑动手势。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State currentIndex: number = 0;
  @State selectedIndex: number = 0;
  @State fontColor: string = '#182431';
  @State selectedFontColor: string = '#007DFF';
  innerSelectedIndex: number = 0; // 记录内层Tabs的索引
  controller?: TabsController = new TabsController();

  @Builder
  tabBuilder(index: number, name: string) {
    Column() {
      Text(name)
        .fontColor(this.selectedIndex === index ? this.selectedFontColor : this.fontColor)
        .fontSize(16)
        .fontWeight(this.selectedIndex === index ? 500 : 400)
        .lineHeight(22)
        .margin({ top: 17, bottom: 7 })
      Divider()
        .strokeWidth(2)
        .color('#007DFF')
        .opacity(this.selectedIndex === index ? 1 : 0)
    }.width('100%')
  }

  build() {
    Column() {
      Tabs({ barPosition: BarPosition.Start, index: this.currentIndex, controller: this.controller }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar(this.tabBuilder(0, 'green'))

        TabContent() {
          Tabs() {
            TabContent() {
              Column().width('100%').height('100%').backgroundColor(Color.Blue)
            }.tabBar(new SubTabBarStyle('blue'))

            TabContent() {
              Column().width('100%').height('100%').backgroundColor(Color.Pink)
            }.tabBar(new SubTabBarStyle('pink'))
          }
          .onAnimationStart((_index: number, targetIndex: number) => {
            console.info(`ets onGestureRecognizerJudgeBegin child: ${targetIndex}`);
            this.innerSelectedIndex = targetIndex;
          })
          .onGestureRecognizerJudgeBegin((event: BaseGestureEvent, current: GestureRecognizer,
            others: Array<GestureRecognizer>): GestureJudgeResult => { // 在识别器即将要成功时，根据内层Tabs索引和滑动方向返回手势判定结果
            console.info('ets onGestureRecognizerJudgeBegin child');
            if (current) {
              let target = current.getEventTargetInfo();
              if (target && current.isBuiltIn() && current.getType() == GestureControl.GestureType.PAN_GESTURE) {
                console.info('ets onGestureRecognizerJudgeBegin child PAN_GESTURE');
                let panEvent = event as PanGestureEvent;
                if (panEvent && panEvent.velocityX < 0 && this.innerSelectedIndex === 1) { // 内层Tabs滑动到尽头
                  console.info('ets onGestureRecognizerJudgeBegin child reject end');
                  return GestureJudgeResult.REJECT;
                }
                if (panEvent && panEvent.velocityX > 0 && this.innerSelectedIndex === 0) { // 内层Tabs滑动到开头
                  console.info('ets onGestureRecognizerJudgeBegin child reject begin');
                  return GestureJudgeResult.REJECT;
                }
              }
            }
            return GestureJudgeResult.CONTINUE;
          }, true)
        }.tabBar(this.tabBuilder(1, 'blue and pink'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Brown)
        }.tabBar(this.tabBuilder(2, 'brown'))
      }
      .onAnimationStart((_index: number, targetIndex: number, _event: TabsAnimationEvent) => {
        // 切换动画开始时触发该回调。目标页签显示下划线。
        this.selectedIndex = targetIndex;
      })
    }
  }
}
```

### 示例3（拦截手势获取属性）

该示例通过配置onGestureRecognizerJudgeBegin判定手势，获取手势的距离、手指数、是否限制手指数、重复触发状态、持续时间、点击次数、旋转角度、滑动方向和速度阈值等属性参数。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State message: string = 'Gesture';

  build() {
    Column() {
      Column() {
        Row({ space: 20 }) {
          Text(this.message)
            .width('100%')
            .height(80)
            .fontSize(23)
        }.margin(25)
      }
      .margin(25)
      .padding(20)
      .width('90%')
      .height(250)
      .borderWidth(2)
      .gesture(TapGesture())
      .gesture(LongPressGesture())
      .gesture(PanGesture({ direction: PanDirection.Vertical }))
      .gesture(PinchGesture())
      .gesture(RotationGesture())
      .gesture(SwipeGesture({ direction: SwipeDirection.Horizontal }))
      // 给组件绑定自定义手势识别器判定回调
      .onGestureRecognizerJudgeBegin((event: BaseGestureEvent, current: GestureRecognizer,
        others: Array<GestureRecognizer>) => {
        if (current) {
          // 判断是否为滑动手势
          if (current.getType() === GestureControl.GestureType.PAN_GESTURE) {
            let target = current as PanRecognizer;
            this.message = 'PanGesture\ndistance:' + target.getPanGestureOptions().getDistance() + '\nfingers:' +
            target.getFingerCount() + '\nisFingerCountLimited:' + target.isFingerCountLimit();
          }
          // 判断是否为长按手势
          if (current.getType() === GestureControl.GestureType.LONG_PRESS_GESTURE) {
            let target = current as LongPressRecognizer;
            this.message = 'LongPressGesture\nfingers:' + target.getFingerCount() + '\nisFingerCountLimited:' +
            target.isFingerCountLimit() + '\nrepeat:' + target.isRepeat() + '\nduration:' + target.getDuration();
          }
          // 判断是否为捏合手势
          if (current.getType() === GestureControl.GestureType.PINCH_GESTURE) {
            let target = current as PinchRecognizer;
            this.message = 'PinchGesture\ndistance:' + target.getDistance() + '\nfingers:' +
            target.getFingerCount() + '\nisFingerCountLimited:' + target.isFingerCountLimit();
          }
          // 判断是否为点击手势
          if (current.getType() === GestureControl.GestureType.TAP_GESTURE) {
            let target = current as TapRecognizer;
            this.message = 'TapGesture\ncount:' + target.getTapCount() + '\nfingers:' +
            target.getFingerCount() + '\nisFingerCountLimited:' + target.isFingerCountLimit();
          }
          // 判断是否为旋转手势
          if (current.getType() === GestureControl.GestureType.ROTATION_GESTURE) {
            let target = current as RotationRecognizer;
            this.message = 'RotationGesture\nangle:' + target.getAngle() + '\nfingers:' +
            target.getFingerCount() + '\nisFingerCountLimited:' + target.isFingerCountLimit();
          }
          // 判断是否为快滑手势
          if (current.getType() === GestureControl.GestureType.SWIPE_GESTURE) {
            let target = current as SwipeRecognizer;
            this.message = 'SwipeGesture\ndirection:' + target.getDirection() + '\nfingers:' +
            target.getFingerCount() + '\nisFingerCountLimited:' + target.isFingerCountLimit() + '\nspeed:' +
            target.getVelocityThreshold();
          }
        }
        return GestureJudgeResult.CONTINUE;
      })
    }
    .padding(15)
  }
}
```

### 示例4（手势触发成功时取消子组件上的Touch事件）

该示例通过配置onGestureRecognizerJudgeBegin判定手势，在父容器手势触发成功时，调用cancelTouch()强制取消子组件上的Touch事件，实现父子组件手势控制的精准切换。



```TypeScript
// xxx.ets
@Entry
@Component
struct FatherControlChild {
  scroller: Scroller = new Scroller();
  scroller2: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  private childRecognizer: GestureRecognizer = new GestureRecognizer();
  private currentRecognizer: GestureRecognizer = new GestureRecognizer();
  private lastOffset: number = 0;
  @State outerState: string = 'IDLE';
  @State innerState: string = 'IDLE';
  @State willCancel: boolean = false;

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) { // 外部滚动容器
        Column() {
          Text('Scroll Area')
            .width('90%')
            .height(150)
            .backgroundColor(0xFFFFFF)
            .borderRadius(15)
            .fontSize(16)
            .textAlign(TextAlign.Center)
            .margin({ top: 10 })

          Scroll(this.scroller2) { // 内部滚动容器
            Column() {
              Text('Scroll Area2')
                .width('90%')
                .height(150)
                .backgroundColor(0xFFFFFF)
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .margin({ top: 10 })

              Column() {
                ForEach(this.arr, (item: number) => {
                  Text(item.toString())
                    .width('90%')
                    .height(150)
                    .backgroundColor(0xFFFFFF)
                    .borderRadius(15)
                    .fontSize(16)
                    .textAlign(TextAlign.Center)
                    .margin({ top: 10 })
                }, (item: string) => item)
              }.width('100%')
            }
          }
          .id('inner')
          .width('100%')
          .height(800)
          .onTouch((event) => {
            if (event.type === TouchType.Down) {
              this.innerState = 'TOUCHING';
              this.willCancel = false;
            } else if (event.type === TouchType.Up || event.type === TouchType.Cancel) {
              if (this.willCancel) {
                this.innerState = 'CANCELLED';
                setTimeout(() => {
                  this.innerState = 'IDLE';
                  this.willCancel = false;
                }, 1000);
              } else {
                this.innerState = 'IDLE';
              }
            }
          })
        }.width('100%')
      }
      .id('outer')
      .height('100%')
      .scrollable(ScrollDirection.Vertical)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Gray)
      .scrollBarWidth(10)
      .edgeEffect(EdgeEffect.None)
      .shouldBuiltInRecognizerParallelWith((current: GestureRecognizer, others: Array<GestureRecognizer>) => {
        for (let i = 0; i < others.length; i++) {
          let target = others[i].getEventTargetInfo();
          if (target) {
            if (target.getId() == 'inner' && others[i].isBuiltIn() &&
              others[i].getType() == GestureControl.GestureType.PAN_GESTURE) { // 找到将要组成并行手势的识别器
              this.currentRecognizer = current; // 保存当前组件的识别器
              this.childRecognizer = others[i]; // 保存将要组成并行手势的识别器
              return others[i]; // 返回将要组成并行手势的识别器
            }
          }
        }
        return undefined;
      })
      .onGestureRecognizerJudgeBegin((event: BaseGestureEvent, current: GestureRecognizer,
        others: Array<GestureRecognizer>,
        touchRecognizers?: Array<TouchRecognizer>) => { // 在识别器即将要成功时，查找子组件触摸识别器并取消其Touch事件
        if (current && touchRecognizers) {
          let target = current.getEventTargetInfo();
          if (target) {
            if (target.getId() == 'outer' && current.isBuiltIn() &&
              current.getType() == GestureControl.GestureType.PAN_GESTURE) {
              return GestureJudgeResult.CONTINUE;
            }
            for (let index = 0; index < touchRecognizers.length; index++) {
              const element = touchRecognizers[index];
              let touchTarget = element.getEventTargetInfo();
              if (touchTarget && touchTarget.getId() == 'inner') {
                this.willCancel = true;
                element.cancelTouch();
              }
            }
          }
        }
        return GestureJudgeResult.CONTINUE;
      })
      .onTouch((event) => {
        if (event.type === TouchType.Down) {
          this.outerState = 'TOUCHING';
        } else if (event.type === TouchType.Up || event.type === TouchType.Cancel) {
          this.outerState = 'IDLE';
        }
      })
      .parallelGesture( // 绑定一个Pan手势作为动态控制器
        PanGesture()
          .onActionUpdate((event: GestureEvent) => {
            if (this.childRecognizer.getState() != GestureRecognizerState.SUCCESSFUL ||
              this.currentRecognizer.getState() != GestureRecognizerState.SUCCESSFUL) { // 如果识别器状态不是SUCCESSFUL，则不做控制
              return;
            }
            let target = this.childRecognizer.getEventTargetInfo() as ScrollableTargetInfo;
            let currentTarget = this.currentRecognizer.getEventTargetInfo() as ScrollableTargetInfo;
            if (target instanceof ScrollableTargetInfo && currentTarget instanceof ScrollableTargetInfo) {
              if (target.isEnd()) { // 在移动过程中实时根据当前组件状态，控制识别器的开闭状态
                if ((event.offsetY - this.lastOffset) < 0) {
                  this.childRecognizer.setEnabled(false);
                  if (currentTarget.isEnd()) {
                    this.currentRecognizer.setEnabled(false);
                  } else {
                    this.currentRecognizer.setEnabled(true);
                  }
                } else {
                  this.childRecognizer.setEnabled(true);
                  this.currentRecognizer.setEnabled(false);
                }
              } else if (target.isBegin()) {
                if ((event.offsetY - this.lastOffset) > 0) {
                  this.childRecognizer.setEnabled(false);
                  if (currentTarget.isBegin()) {
                    this.currentRecognizer.setEnabled(false);
                  } else {
                    this.currentRecognizer.setEnabled(true);
                  }
                } else {
                  this.childRecognizer.setEnabled(true)
                  this.currentRecognizer.setEnabled(false)
                }
              } else {
                this.childRecognizer.setEnabled(true)
                this.currentRecognizer.setEnabled(false)
              }
            }
            this.lastOffset = event.offsetY;
          })
      )

      Column() { // 外层状态显示
        Text(`outer: ${this.outerState}`)
          .fontSize(24)
          .fontColor(this.outerState === 'TOUCHING' ? Color.Green : Color.Gray)
          .margin({ bottom: 10 })
        // 内层状态显示
        Text(`inner: ${this.innerState === 'TOUCHING' ? 'TOUCHING' : this.innerState}`)
          .fontSize(24)
          .fontColor(
            this.innerState === 'TOUCHING' ? Color.Blue :
              this.innerState === 'CANCELLED' ? Color.Red : Color.Gray
          )
      }
      .width('90%')
      .backgroundColor(Color.White)
      .border({ width: 1, color: Color.Gray })
      .position({ x: '5%', y: '80%' })
      .padding(20)
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
  }
}
```

### 示例5（自定义手势识别器是否参与手势处理）

从API version 20开始，该示例通过配置[onTouchTestDone](arkts-arkui-common-comp-commonmethod-c.md#ontouchtestdone)指定手势识别器不参与后续手势处理，触发回调时，调用[preventBegin](./ts-gesture-common.md#preventbegin20)阻止手势识别器参与后续处理。点击Tap2和Tap1的重合区域，不调用preventBegin时，触发Tap2对应的手势；调用preventBegin阻止Tap2时，触发Tap1对应的手势。



```TypeScript
// xxx.ets
@Entry
@Component
struct TouchTestDoneExample {
  @State tagList: string[] = ['Null', 'Tap1', 'Tap2', 'Tap3', 'Tap4'];
  @State tagId: number = 0;
  @State textValue: string = '';

  // 多层嵌套场景，为每一层的组件绑定一个Tap手势
  build() {
    Column() {
      Column() {
        Text('Tap1')
          .margin(20)
        Column() {
          Text('Tap2')
            .margin(20)
          Column() {
            Text('Tap3')
              .margin(20)
            Column() {
              Text('Tap4')
                .margin(20)
            }
            .backgroundColor('#D5D5D5')
            .width('80%')
            .height('80%')
            .gesture(TapGesture().tag('Tap4').onAction(() => {
              this.textValue = 'Tap4';
            }))
          }
          .backgroundColor('#F7F7F7')
          .width('80%')
          .height('80%')
          .gesture(TapGesture().tag('Tap3').onAction(() => {
            this.textValue = 'Tap3';
          }))
        }
        .backgroundColor('#707070')
        .width('80%')
        .height('80%')
        .gesture(TapGesture().tag('Tap2').onAction(() => {
          this.textValue = 'Tap2';
        }))
      }
      .backgroundColor('#D5D5D5')
      .width('80%')
      .height('80%')
      .gesture(TapGesture().tag('Tap1').onAction(() => {
        this.textValue = 'Tap1';
      }))
      // 绑定onTouchTestDone，通过调用手势识别器的preventBegin()方法来自定义手势识别器是否参与后续手势处理
      .onTouchTestDone((event, recognizers) => {
        console.info(`event is ${JSON.stringify(event)}`);
        for (let i = 0; i < recognizers.length; i++) {
          let recognizer = recognizers[i];
          console.info(`type is ${JSON.stringify(recognizer.getType())}`);
          // 根据tag的值屏蔽不同的手势识别器
          if (recognizer.getTag() == this.tagList[this.tagId]) {
            recognizer.preventBegin();
          }
        }
      })

      Text('Current Gesture: ' + this.textValue)
        .margin(5)

      Button('Click to change preventGesture')
        .margin(5)
        .onClick(() => {
          this.tagId++;
          this.tagId %= 5;
        })
      Text('Current prevent gesture tag: ' + this.tagList[this.tagId])
        .margin(5)
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例6（自定义干预事件和手势的收集结果）

该示例通过配置[onGestureCollectIntercept](arkts-arkui-common-comp-commonmethod-c.md#ongesturecollectintercept)指定手势识别器或者触摸识别器是否透传到其他节点。点击button2时，不透传触摸事件到Column。点击button1时，透传触摸事件到Column，Column变色。

从API版本26.0.0开始，新增onGestureCollectIntercept接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State backgroundColorButton1: string = '#D5D5D5';
  @State backgroundColorButton2: string = '#D5D5D5';
  @State backgroundColorRow: string = '#FFFFFF';
  @State backgroundColorColumn: string = '#FFFFFF';

  build() {
    Column() {
      Column() {
        Row({ space: 20 } as RowOptions) {
          // 组件button1未设置点击事件
          Button('button1')
            .width('30%')
            .height(40)
            .id('button1')
            .onTouch((touchEvent?: TouchEvent) => {
              this.backgroundColorButton1 = '#E5E5E5';
            })
            .backgroundColor(this.backgroundColorButton1)
          // 组件button2设置了点击事件
          Button('button2')
            .width('30%')
            .height(40)
            .id('button2')
            .onTouch((touchEvent?: TouchEvent) => {
              this.backgroundColorButton2 = '#E5E5E5';
            })
            .onClick((clickEvent?: ClickEvent) => {
              console.info('button2 is clicked');
            })
            .backgroundColor(this.backgroundColorButton2)
        }
        .justifyContent(FlexAlign.Center)
        .width('90%')
        .height(200)
        .margin(25)
        .onTouch((e?: TouchEvent) => {
          this.backgroundColorRow = '#666666';
        })
        .backgroundColor(this.backgroundColorRow)
        .onGestureCollectIntercept((recognizers: Array<GestureRecognizer>,
          touchRecognizers?: Array<TouchRecognizer> | undefined) => {
          if (!touchRecognizers) {
            return GestureCollectIntervention.CONTINUE;
          } else {
            for (let i = 0; i < touchRecognizers.length; i++) {
              let id = touchRecognizers[i].getEventTargetInfo().getId();
              // 当命中存在点击事件区域button2时，事件无需透传给Column
              if (id == 'button2') {
                return GestureCollectIntervention.DISCARD_LOWER;
              }
            }
          }
          return GestureCollectIntervention.CONTINUE;
        })
      }
      .margin(25)
      .padding(20)
      .width('90%')
      .height(250)
      .borderWidth(2)
      .onTouch((e?: TouchEvent) => {
        this.backgroundColorColumn = '#E5E5E5';
      })
      .backgroundColor(this.backgroundColorColumn)
    }
    .padding(15)
  }
}
```



示例对应的组件树如下图所示。

```TypeScript
graph TD
    A((Column))
    B((Column))
    C((Row))
    D((Button1))
    E((Button2))

    A --> B
    A --> C
    C --> D
    C --> E
```

### 示例7（非内置手势嵌套滚动）

该示例通过[shouldRecognizerParallelWith](arkts-arkui-common-comp-commonmethod-c.md#shouldrecognizerparallelwith)和[onGestureRecognizerJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturerecognizerjudgebegin)实现了嵌套滚动的功能。内部组件优先响应滑动手势，当内部组件滑动至顶部或底部时，外部组件能够接替滑动。

从API版本26.0.0开始，新增shouldRecognizerParallelWith接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct FatherControlChild {
  scroller: Scroller = new Scroller();
  scroller2: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  private childRecognizer: GestureRecognizer = new GestureRecognizer();
  private currentRecognizer: GestureRecognizer = new GestureRecognizer();
  private lastOffset: number = 0;

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) { // 外部滚动容器
        Column() {
          Text('Scroll Area')
            .width('90%')
            .height(150)
            .backgroundColor(0xFFFFFF)
            .borderRadius(15)
            .fontSize(16)
            .textAlign(TextAlign.Center)
            .margin({ top: 10 })
          Scroll(this.scroller2) { // 内部滚动容器
            Column() {
              Text('Scroll Area2')
                .width('90%')
                .height(150)
                .backgroundColor(0xFFFFFF)
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .margin({ top: 10 })
              Column() {
                ForEach(this.arr, (item: number) => {
                  Text(item.toString())
                    .width('90%')
                    .height(150)
                    .backgroundColor(0xFFFFFF)
                    .borderRadius(15)
                    .fontSize(16)
                    .textAlign(TextAlign.Center)
                    .margin({ top: 10 })
                }, (item: string) => item)
              }.width('100%')
            }
          }
          .id('inner')
          .width('100%')
          .height(800)
        }.width('100%')
      }
      .id('outer')
      .height(600)
      .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
      .scrollBar(BarState.On) // 滚动条常驻显示
      .scrollBarColor(Color.Gray) // 滚动条颜色
      .scrollBarWidth(10) // 滚动条宽度
      .edgeEffect(EdgeEffect.None)
      .enableScrollInteraction(false)
      .gesture(
        PanGesture()
          .onActionStart(() => {
            this.lastOffset = this.scroller.currentOffset().yOffset; // 手势开始时，记录当前滚动位置
          })
          .onActionUpdate((event: GestureEvent) => {
            let moveY = event.offsetY; // 手势移动时，计算新位置
            let targetOffset = this.lastOffset - moveY; // 目标位置 = 初始位置 - 移动距离
            this.scroller.scrollTo({ xOffset: 0, yOffset: targetOffset });
          })
      )
      .shouldRecognizerParallelWith((current: GestureRecognizer, others: Array<GestureRecognizer>) => {
        for (let i = 0; i < others.length; i++) {
          let target = others[i].getEventTargetInfo();
          if (target) {
            if (target.getId() == 'inner' && others[i].isBuiltIn() &&
              others[i].getType() == GestureControl.GestureType.PAN_GESTURE) { // 找到将要组成并行手势的识别器
              this.currentRecognizer = current; // 保存当前组件的识别器
              this.childRecognizer = others[i]; // 保存将要组成并行手势的识别器
              return others[i]; // 返回将要组成并行手势的识别器
            }
          }
        }
        return undefined;
      })
      .onGestureRecognizerJudgeBegin((event: BaseGestureEvent, current: GestureRecognizer,
        others: Array<GestureRecognizer>) => { // 在识别器即将要成功时，根据当前组件状态，设置识别器使能状态
        if (current) {
          let target = current.getEventTargetInfo();
          if (target) {
            if (target.getId() == 'outer' &&
              current.getType() == GestureControl.GestureType.PAN_GESTURE) {
              if (others) {
                for (let i = 0; i < others.length; i++) {
                  let target = others[i].getEventTargetInfo() as ScrollableTargetInfo;
                  if (target instanceof ScrollableTargetInfo && target.getId() == 'inner') { // 找到响应链上对应并行的识别器
                    let panEvent = event as PanGestureEvent;
                    if (target.isEnd()) { // 根据当前组件状态以及移动方向动态控制识别器使能状态
                      if (panEvent && panEvent.offsetY < 0) {
                        this.childRecognizer.setEnabled(false);
                        this.currentRecognizer.setEnabled(true);
                      } else {
                        this.childRecognizer.setEnabled(true);
                        this.currentRecognizer.setEnabled(false);
                      }
                    } else if (target.isBegin()) {
                      if (panEvent.offsetY > 0) {
                        this.childRecognizer.setEnabled(false);
                        this.currentRecognizer.setEnabled(true);
                      } else {
                        this.childRecognizer.setEnabled(true);
                        this.currentRecognizer.setEnabled(false);
                      }
                    } else {
                      this.childRecognizer.setEnabled(true);
                      this.currentRecognizer.setEnabled(false);
                    }
                  }
                }
              }
            }
          }
        }
        return GestureJudgeResult.CONTINUE;
      })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### 示例1（设置跟手变形拖拽动画）

该示例通过设置[dragAnimationType](#focuscontrol)为FOLLOW_HAND_MORPH实现跟手变形拖拽动画效果，并在拖拽结束时通过[executeFollowHandMorphDropAnimation](arkts-arkui-common-comp-dragevent-i-sys.md#executefollowhandmorphdropanimation)执行自定义落位动效。

从API版本26.0.0开始，新增[dragAnimationType](#focuscontrol)属性、[executeFollowHandMorphDropAnimation](arkts-arkui-common-comp-dragevent-i-sys.md#executefollowhandmorphdropanimation)方法、[interruptFollowHandMorphDropAnimation](../arkts-apis/arkts-arkui-arkui-uicontext-dragcontroller-c-sys.md#interruptfollowhandmorphdropanimation)方法。

```TypeScript
// xxx.ets
// 动画参数类
class AnimationOption {
  CubicCurveEnable: boolean = false;
  SpringEnable: boolean = false;
  dropAnimationCurve: number[] = [];
  dropPosition: number[] = [];
  dropSize: number[] = [];
}

@Entry
@Component
struct FollowHandMorphDemo {
  @State dragInfo: string = '未拖拽';
  @State animationInfo: string = '';
  @State interruptResult: string = '';

  build() {
    Column({ space: 20 }) {
      Text('跟手变形拖拽动画示例')
        .fontSize(20)
        .fontWeight(FontWeight.Bold)

      Text('操作说明：长按左侧方块拖拽到右侧区域')
        .fontSize(14)
        .fontColor('#666666')

      Row({ space: 30 }) {
        // 拖拽源
        Column() {
          Text('拖拽源')
            .fontSize(14)
          Text('长按拖拽')
            .fontSize(12)
            .fontColor('#999999')
        }
        .width(100)
        .height(100)
        .backgroundColor('#DDEEFF')
        .borderRadius(12)
        .justifyContent(FlexAlign.Center)
        .draggable(true)
        .onDragStart((event: DragEvent) => {
          // 设置为跟手变形动画模式
          event.dragAnimationType = DragAnimationType.FOLLOW_HAND_MORPH;
          this.dragInfo = 'onDragStart: dragAnimationType=1';
        })

        // 目标区域
        Column() {
          Text('目标区域')
            .fontSize(14)
          Text('在此松手')
            .fontSize(12)
            .fontColor('#999999')
        }
        .width(100)
        .height(100)
        .backgroundColor('#EAF8EA')
        .borderRadius(12)
        .justifyContent(FlexAlign.Center)
        .onDrop((event: DragEvent) => {
          this.dragInfo = 'onDrop触发';

          // 构建动画参数
          let animationOption = new AnimationOption();
          animationOption.CubicCurveEnable = false;
          animationOption.SpringEnable = true;
          animationOption.dropAnimationCurve = [0.416, 0.99, 0];
          animationOption.dropPosition = [830, 600];
          animationOption.dropSize = [100, 100];

          // 执行跟手变形落位动效
          event.executeFollowHandMorphDropAnimation(() => {
            this.animationInfo = '跟手变形动效完成';
          }, JSON.stringify(animationOption));
        })
      }

      // 状态显示
      Column({ space: 8 }) {
        Text(`拖拽状态：${this.dragInfo}`).fontSize(12)
        Text(`动效状态：${this.animationInfo}`).fontSize(12)
        Text(`中断结果：${this.interruptResult}`).fontSize(12)
      }
      .width('100%')
      .padding(12)
      .backgroundColor('#F7F7F7')
      .borderRadius(8)

      // 中断动画按钮
      Button('中断待执行的跟手变形动效')
        .onClick(() => {
          let result = this.getUIContext().getDragController().interruptFollowHandMorphDropAnimation();
          this.interruptResult = result ? '中断成功' : '无待中断的动效';
        })
    }
    .width('100%')
    .height('100%')
    .padding(20)
    .backgroundColor('#FFFFFF')
  }
}
```

### 示例1（获取触摸事件相关参数）

该示例中，按钮设置触摸事件，在点击按钮时可获取事件的相关参数。



```TypeScript
// xxx.ets
@Entry
@Component
struct TouchExample {
  @State text: string = '';
  @State eventType: string = '';

  build() {
    Column() {
      Button('Touch').height(40).width(100)
        .onTouch((event?: TouchEvent) => {
          if (event && event.sourceTool === SourceTool.Finger) {
            if (event.type === TouchType.Down) {
              this.eventType = 'Down';
            }
            if (event.type === TouchType.Up) {
              this.eventType = 'Up';
            }
            if (event.type === TouchType.Move) {
              this.eventType = 'Move';
            }
            // 1. 手指按住屏幕同时点击Home键返回桌面，此时会触发Cancel
            // 2. 折叠屏手机，应用在按住屏幕的情况下折叠手机切换到外屏，此时会触发Cancel
            if (event.type === TouchType.Cancel) {
              this.eventType = 'Cancel';
            }
            if (event.touches.length > 0) {
              this.text = 'TouchType:' + this.eventType
                + '\nDistance between touch point and touch element:'
                + '\n  id: ' + event.touches[0].id
                + '\n  x: ' + event.touches[0].x + '\n  y: ' + event.touches[0].y
                + '\n  width: ' + event.touches[0].width + '\n  height: ' + event.touches[0].height
                + '\n  pressedTime: ' + event.touches[0].pressedTime
                + '\n  pressure: ' + event.touches[0].pressure
                + '\nComponent globalPos:'
                + '\n  x: ' + event.target.area.globalPosition.x + '\n  y: ' + event.target.area.globalPosition.y
                + '\n  width: ' + event.target.area.width + '\n  height: ' + event.target.area.height
                + '\ntargetDisplayId: ' + event.targetDisplayId;
            }
          }
        })
      Button('Touch').height(50).width(200).margin(20)
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type === TouchType.Down) {
              this.eventType = 'Down';
            }
            if (event.type === TouchType.Up) {
              this.eventType = 'Up';
            }
            if (event.type === TouchType.Move) {
              this.eventType = 'Move';
            }
            // 1. 手指按住屏幕同时点击Home键返回桌面，此时会触发Cancel
            // 2. 折叠屏手机，应用在按住屏幕的情况下折叠手机切换到外屏，此时会触发Cancel
            if (event.type === TouchType.Cancel) {
              this.eventType = 'Cancel';
            }
            if (event.touches.length > 0) {
              this.text = 'TouchType:' + this.eventType
                + '\nDistance between touch point and touch element:'
                + '\n  id: ' + event.touches[0].id
                + '\n  x: ' + event.touches[0].x + '\n  y: ' + event.touches[0].y
                + '\n  width: ' + event.touches[0].width + '\n  height: ' + event.touches[0].height
                + '\n  pressedTime: ' + event.touches[0].pressedTime
                + '\n  pressure: ' + event.touches[0].pressure
                + '\nComponent globalPos:'
                + '\n  x: ' + event.target.area.globalPosition.x + '\n  y: ' + event.target.area.globalPosition.y
                + '\n  width: ' + event.target.area.width + '\n  height: ' + event.target.area.height
                + '\ntargetDisplayId: ' + event.targetDisplayId;
            }
          }
        })
      Text(this.text)
    }.width('100%').padding(30)
  }
}
```

### 示例2（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取触摸位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct GetCurrentLocalPositionExample {
  @State positionText: string = '';
  @State textOffsetY: number = 0;

  build() {
    Column() {
      Button('点击获取点击位置相对于当前组件实时位置左上角的坐标').translate({ y: this.textOffsetY })
        .onTouch((event?: TouchEvent) => {
          if (event) {
            this.textOffsetY = -200;
            setTimeout(() => {
              let localPos: Coordinate2D | undefined = event.touches.length > 0 ? event.touches[0].getCurrentLocalPosition?.() : undefined;
              this.positionText = `相对于当前组件实时位置左上角的坐标：\n  x: ${localPos?.x}\n  y: ${localPos?.y}`;
            }, 2000);
          }
        })

      Text(this.positionText)
    }.width('100%')
  }
}
```

### 示例1（颜色线性渐变）

该示例通过[linearGradient](#lineargradient)来实现组件的颜色线性渐变。



```TypeScript
// xxx.ets
@Entry
@Component
struct ColorGradientExample {
  build() {
    Column({ space: 5 }) {
      Text('linearGradient').fontSize(12).width('90%').fontColor(0xCCCCCC)
      Row()
        .width('90%')
        .height(50)
        .linearGradient({
          angle: 90,
          colors: [[0xff0000, 0.0], [0x0000ff, 0.3], [0xffff00, 1.0]]
        })
      Text('linearGradient Repeat').fontSize(12).width('90%').fontColor(0xCCCCCC)
      Row()
        .width('90%')
        .height(50)
        .linearGradient({
          direction: GradientDirection.Left, // 渐变方向
          repeating: true, // 渐变颜色是否重复
          colors: [[0xff0000, 0.0], [0x0000ff, 0.3], [0xffff00, 0.5]] // 数组末尾元素占比小于1时满足重复着色效果
        })
    }
    .width('100%')
    .padding({ top: 5 })
  }
}
```

### 示例2（颜色按旋转角度渐变）

该示例通过[sweepGradient](arkts-arkui-common-comp-commonmethod-c.md#sweepgradient)来实现组件颜色旋转角度渐变。



```TypeScript
// 设置P3色域时需要在ets/entryability/EntryAbility.ets中，通过setColorSpace接口将当前窗口设置为广色域。
import { ColorMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ColorGradientExample {
  @State p3Red: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 1, 0, 0, 1);
  @State p3Green: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0, 1, 0, 1);
  @State p3Blue: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0, 0, 1, 1);

  build() {
    Column({ space: 5 }) {
      Text('sweepGradient').fontSize(12).width('90%').fontColor(0xCCCCCC)
      Row()
        .width(100)
        .height(100)
        .sweepGradient({
          center: [50, 50],
          start: 0,
          end: 359,
          colors: [[0xff0000, 0.0], [0x0000ff, 0.3], [0xffff00, 1.0]]
        })
      
      Text('sweepGradient Repeat').fontSize(12).width('90%').fontColor(0xCCCCCC)
      Row()
        .width(100)
        .height(100)
        .sweepGradient({
          center: [50, 50],
          start: 0,
          end: 359,
          rotation: 45, // 旋转角度
          repeating: true, // 渐变颜色是否重复
          colors: [[0xff0000, 0.0], [0x0000ff, 0.3], [0xffff00, 0.5]] // 数组末尾元素占比小于1时满足重复着色效果
        })

      Text('sweepGradient with metricsColors').fontSize(12).width('90%').fontColor(0xCCCCCC)
      Row()
        .width(100)
        .height(100)
        .sweepGradient({
          center: [50, 50],
          start: 0,
          end: 359,
          rotation: 45,
          repeating: true,
          colors: [[0xff0000, 0.0], [0x0000ff, 0.3], [0xffff00, 0.5]], // 数组末尾元素占比小于1时满足重复着色效果
          metricsColors: [[this.p3Red, 0.0], [this.p3Green, 0.5], [this.p3Blue, 1.0]]  // 设置metricsColors时colors设置的颜色失效，metricsColors的颜色生效
        })
    }
    .width('100%')
    .padding({ top: 5 })
  }
}
```

### 示例3（颜色按径向渐变）

该示例通过[radialGradient](arkts-arkui-common-comp-commonmethod-c.md#radialgradient)来实现组件颜色径向渐变。

```TypeScript
// xxx.ets
@Entry
@Component
struct ColorGradientExample {
  build() {
    Column({ space: 5 }) {
      Text('radialGradient').fontSize(12).width('90%').fontColor(0xCCCCCC)
      Row()
        .width(100)
        .height(100)
        .radialGradient({
          center: [50, 50],
          radius: 60,
          colors: [[0xff0000, 0.0], [0x0000ff, 0.3], [0xffff00, 1.0]]
        })
      Text('radialGradient Repeat').fontSize(12).width('90%').fontColor(0xCCCCCC)
      Row()
        .width(100)
        .height(100)
        .radialGradient({
          center: [50, 50],
          radius: 60,
          repeating: true,
          colors: [[0xff0000, 0.0], [0x0000ff, 0.3], [0xffff00, 0.5]] // 数组末尾元素占比小于1时满足重复着色效果
        })
    }
    .width('100%')
    .padding({ top: 5 })
  }
}
```

```TypeScript
@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      ReusableV2Component()
        .reuse({reuseId: () => 'reuseComponent'}) // 使用'reuseComponent'作为reuseId
      ReusableV2Component()
        .reuse({reuseId: () => ''}) // 使用空字符串将默认使用组件名'ReusableV2Component'作为reuseId
      ReusableV2Component() // 未指定reuseId将默认使用组件名'ReusableV2Component'作为reuseId
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  build() {
    Text('content')
  }
}
```

### 示例1（通过string设置浮层）

该示例通过传入string设置浮层。



```TypeScript
// xxx.ets
@Entry
@Component
struct OverlayExample {
  build() {
    Column() {
      Column() {
        Text('floating layer')
          .fontSize(12).fontColor(0xCCCCCC).maxLines(1)
        Column() {
          // $r('app.media.img')需要替换为开发者所需的图像资源文件
          Image($r('app.media.img'))
            .width(240).height(240)
            .overlay('Winter is a beautiful season, especially when it snows.', {
              align: Alignment.Bottom,
              offset: { x: 0, y: -15 }
            })
        }.border({ color: Color.Black, width: 2 })
      }.width('100%')
    }.padding({ top: 20 })
  }
}
```

### 示例2（通过builder设置浮层）

该示例通过传入builder设置浮层。



```TypeScript
// xxx.ets
@Entry
@Component
struct OverlayExample {
  @Builder
  overlayNode() {
    Column() {
      // $r('app.media.img1')需要替换为开发者所需的图像资源文件
      Image($r('app.media.img1'))
      Text('This is overlayNode').fontSize(20).fontColor(Color.White)
    }
    .width(180)
    .height(180)
    .alignItems(HorizontalAlign.Center)
    .hitTestBehavior(HitTestMode.Transparent) // 配置浮层不阻塞交互
  }

  build() {
    Column() {
      // $r('app.media.img2')需要替换为开发者所需的图像资源文件
      Image($r('app.media.img2'))
        .overlay(this.overlayNode(), { align: Alignment.Center })
        .objectFit(ImageFit.Contain)
    }.width('100%')
    .border({ color: Color.Black, width: 2 }).padding(20)
  }
}
```

### 示例3（通过ComponentContent设置浮层）

该示例通过overlay传入ComponentContent，并通过update方法更新ComponentContent参数，使backgroundColor不断发生变化。

```TypeScript
// xxx.ets
import { ComponentContent } from '@kit.ArkUI';

class Params {
  backgroundColor: string | Resource = '';

  constructor(backgroundColor: string | Resource) {
    this.backgroundColor = backgroundColor;
  }
}

@Builder
function overlayBuilder(params: Params) {
  Row() {
  }.width('100%').height('100%').backgroundColor(params.backgroundColor)
}

@Entry
@Component
struct OverlayContentPage {
  @State overlayColor: string = 'rgba(0, 0, 0, 0.6)';
  private uiContext: UIContext = this.getUIContext();
  private overlayNode: ComponentContent<Params> =
    new ComponentContent(this.uiContext, wrapBuilder(overlayBuilder), new Params(this.overlayColor));

  aboutToAppear(): void {
    setInterval(() => {
      if (this.overlayColor.includes('0.6')) {
        this.overlayColor = 'rgba(0, 0, 0, 0.1)';
        this.overlayNode.update(new Params(this.overlayColor));
      } else {
        this.overlayColor = 'rgba(0, 0, 0, 0.6)';
        this.overlayNode.update(new Params(this.overlayColor));
      }
    }, 1000);
  }

  build() {
    Row() {
      Column() {
        Text(this.overlayColor)
          .fontSize(40)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
    .overlay(this.overlayNode)
  }
}
```

### 示例1（在组件出现时创建动画）

> 说明：
> 
> 直接使用animateTo可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用getUIContext()获取[UIContext](../arkts-apis-uicontext-uicontext.md)实例，并使用[animateTo](../arkts-apis-uicontext-uicontext.md#animateto)调用绑定实例的animateTo。

该示例通过在onAppear方法中创建组件出现时的动画效果。



```TypeScript
// xxx.ets
@Entry
@Component
struct AnimateToExample {
  @State widthSize: number = 250;
  @State heightSize: number = 100;
  @State rotateAngle: number = 0;
  private flag: boolean = true;

  build() {
    Column() {
      Button('change size')
        .width(this.widthSize)
        .height(this.heightSize)
        .margin(30)
        .onClick(() => {
          if (this.flag) {
            // 建议使用this.getUIContext()?.animateTo()
            animateTo({
              duration: 2000,
              curve: Curve.EaseOut,
              iterations: 3,
              playMode: PlayMode.Normal,
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.widthSize = 150;
              this.heightSize = 60;
            })
          } else {
            // 建议使用this.getUIContext()?.animateTo()
            animateTo({}, () => {
              this.widthSize = 250;
              this.heightSize = 100;
            })
          }
          this.flag = !this.flag;
        })
      Button('stop rotating')
        .margin(50)
        .rotate({ x: 0, y: 0, z: 1, angle: this.rotateAngle })
        .onAppear(() => {
          // 组件出现时开始做动画
          // 建议使用this.getUIContext()?.animateTo()
          animateTo({
            duration: 1200,
            curve: Curve.Friction,
            delay: 500,
            iterations: -1, // 设置-1表示动画无限循环
            playMode: PlayMode.Alternate,
            expectedFrameRateRange: {
              min: 10,
              max: 120,
              expected: 60,
            }
          }, () => {
            this.rotateAngle = 90;
          })
        })
        .onClick(() => {
          // 建议使用this.getUIContext()?.animateTo()
          animateTo({ duration: 0 }, () => {
            // this.rotateAngle之前为90，在duration为0的动画中修改属性，可以停止该属性之前的动画，按新设置的属性显示
            this.rotateAngle = 0;
          })
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

### 示例2（动画执行结束后组件消失）

该示例主要演示如何实现在动画执行结束后组件消失。

```TypeScript
// xxx.ets
@Entry
@Component
struct AttrAnimationExample {
  @State heightSize: number = 100;
  @State isShow: boolean = true;
  @State count: number = 0;
  private isToBottom: boolean = true; // 向下

  build() {
    Column() {
      if (this.isShow) {
        Column()
          .width(200)
          .height(this.heightSize)
          .backgroundColor('blue')
          .onClick(() => {
            // 建议使用this.getUIContext()?.animateTo()
            animateTo({
              duration: 2000,
              curve: Curve.EaseOut,
              iterations: 1,
              playMode: PlayMode.Normal,
              onFinish: () => {
                // 动画完成时减少计数，计数归零表示所有动画已结束
                this.count--;
                if (this.count == 0 && !this.isToBottom) { // 组件只有在向下做完动画才会消失
                  this.isShow = false;
                }
              }
            }, () => {
              // 动画开始时增加计数，用于在onFinish回调中判断动画是否完成
              this.count++;
              if (this.isToBottom) {
                this.heightSize = 60;
              } else {
                this.heightSize = 100;
              }
              this.isToBottom = !this.isToBottom;
            })
          })
      }
    }.width('100%').height('100%').margin({ top: 5 })
    .justifyContent(FlexAlign.End)
  }
}
```

通过配置flexBasis/flexGrow/flexShrink/alignSelf属性设置Flex布局。

```TypeScript
// xxx.ets
@Entry
@Component
struct FlexExample {
  build() {
    Column({ space: 5 }) {
      Text('flexBasis').fontSize(9).fontColor(0xCCCCCC).width('90%')
      // 基于主轴的基准尺寸
      // flexBasis()值可以是字符串'auto'，表示基准尺寸是元素本来的大小，也可以是长度设置，相当于.width()/.height()
      Flex() {
        Text('flexBasis(100)')
          .flexBasis(100) // 这里表示宽度为100vp
          .height(100)
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
        Text(`flexBasis('auto')`)
          .flexBasis('auto') // 这里表示宽度保持原本设置的60%的宽度
          .width('60%')
          .height(100)
          .backgroundColor(0xD2B48C)
          .textAlign(TextAlign.Center)
      }.width('90%').height(120).padding(10).backgroundColor(0xAFEEEE)

      Text('flexGrow').fontSize(9).fontColor(0xCCCCCC).width('90%')
      // flexGrow()表示剩余空间分配给该元素的比例
      Flex() {
        Text('flexGrow(2)')
          .flexGrow(2) // 父容器分配给该Text的宽度为剩余宽度的2/3
          .height(100)
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
        Text('flexGrow(1)')
          .flexGrow(1) // 父容器分配给该Text的宽度为剩余宽度的1/3
          .height(100)
          .backgroundColor(0xD2B48C)
          .textAlign(TextAlign.Center)
      }.width('90%').height(120).padding(10).backgroundColor(0xAFEEEE)

      Text('flexShrink').fontSize(9).fontColor(0xCCCCCC).width('90%')
      // flexShrink()表示该元素的压缩比例，基于超出的总尺寸进行计算
      // 第一个text压缩比例是0，另外两个都是1，因此放不下时等比例压缩后两个，第一个不压缩
      Flex({ direction: FlexDirection.Row }) {
        Text('flexShrink(0)')
          .flexShrink(0)
          .width('50%')
          .height(100)
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
        Text('default flexShrink') // 默认值为1
          .width('40%')
          .height(100)
          .backgroundColor(0xD2B48C)
          .textAlign(TextAlign.Center)
        Text('flexShrink(1)')
          .flexShrink(1)
          .width('40%')
          .height(100)
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
      }.width('90%').height(120).padding(10).backgroundColor(0xAFEEEE)

      Text('alignSelf').fontSize(9).fontColor(0xCCCCCC).width('90%')
      // alignSelf会覆盖Flex布局容器中的alignItems设置
      Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center }) {
        Text('no alignSelf,height:70')
          .width('33%')
          .height(70)
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
        Text('alignSelf End')
          .alignSelf(ItemAlign.End)
          .width('33%')
          .height(70)
          .backgroundColor(0xD2B48C)
          .textAlign(TextAlign.Center)
        Text('no alignSelf,height:100%')
          .width('34%')
          .height('100%')
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
      }.width('90%').height(120).padding(10).backgroundColor(0xAFEEEE)
    }.width('100%').margin({ top: 5 })
  }
}
```

### 示例1（设置图片不同属性效果）

设置图片的效果，包括阴影、灰度、高光、饱和度、对比度、图像反转、叠色、色相旋转等。



```TypeScript
// xxx.ets
@Entry
@Component
struct ImageEffectsExample {
  build() {
    Column({ space: 5 }) {
      // 添加阴影效果，图片效果不变
      Text('shadow').fontSize(15).fontColor(0xCCCCCC).width('90%')
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image'))
        .width('90%')
        .height(30)
        .shadow({
          radius: 10,
          color: Color.Green,
          offsetX: 20,
          offsetY: 20
        })

      // 添加内部阴影效果
      Text('shadow').fontSize(15).fontColor(0xCCCCCC).width('90%')
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image'))
        .width('90%')
        .height(30)
        .shadow({
          radius: 5,
          color: Color.Green,
          offsetX: 20,
          offsetY: 20,
          fill: true
        }).opacity(0.5)

      // 灰度效果0~1，越接近1，灰度越明显
      Text('grayscale').fontSize(15).fontColor(0xCCCCCC).width('90%')
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).grayscale(0.3)
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).grayscale(0.8)

      // 高光效果，1为正常图片，<1变暗，>1亮度增大
      Text('brightness').fontSize(15).fontColor(0xCCCCCC).width('90%')
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).brightness(1.2)

      // 饱和度，原图为1
      Text('saturate').fontSize(15).fontColor(0xCCCCCC).width('90%')
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).saturate(2.0)
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).saturate(0.7)

      // 对比度，1为原图，>1值越大越清晰，<1值越小越模糊
      Text('contrast').fontSize(15).fontColor(0xCCCCCC).width('90%')
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).contrast(2.0)
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).contrast(0.8)

      // 图像反转比例
      Text('invert').fontSize(15).fontColor(0xCCCCCC).width('90%')
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).invert(0.2)
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).invert(0.8)

      // 叠色添加
      Text('colorBlend').fontSize(15).fontColor(0xCCCCCC).width('90%')
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).colorBlend(Color.Green)
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).colorBlend(Color.Blue)

      // 深褐色
      Text('sepia').fontSize(15).fontColor(0xCCCCCC).width('90%')
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).sepia(0.8)

      // 色相旋转
      Text('hueRotate').fontSize(15).fontColor(0xCCCCCC).width('90%')
      // $r("app.media.image")需要替换为开发者所需的图像资源文件。
      Image($r('app.media.image')).width('90%').height(30).hueRotate(90)
    }.width('100%').margin({ top: 5 })
  }
}
```

### 示例2（设置组件线性渐变模糊效果）

该示例主要演示通过[linearGradientBlur](arkts-arkui-common-comp-commonmethod-c.md#lineargradientblur)设置组件的内容线性渐变模糊效果。



```TypeScript
// xxx.ets
@Entry
@Component
struct LinearGradientBlurExample {
  // $r('app.media.testlinearGradientBlurOrigin')需要替换为开发者所需的资源文件。
  privateResource1: Resource = $r('app.media.testlinearGradientBlurOrigin')
  @State imageSrc: Resource = this.privateResource1

  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Image(this.imageSrc)
            .blur(0) // 设置图片模糊效果为不模糊
            .linearGradientBlur(60,
              { fractionStops: [[0, 0], [0, 0.33], [1, 0.66], [1, 1]], direction: GradientDirection.Bottom })
        }
      }
    }
  }
}
```

### 示例3（设置离屏渲染效果）

该示例主要演示通过[renderGroup](arkts-arkui-common-comp-commonmethod-c.md#rendergroup)来设置组件是否先整体离屏渲染绘制后，再与父组件融合绘制。



```TypeScript
// xxx.ets
@Component
struct RenderGroupChildComponent {
  @Prop renderGroupValue: boolean;

  build() {
    Row() {
      Row() {
        Row()
          .backgroundColor(Color.Black)
          .width(100)
          .height(100)
          .opacity(1)
      }
      .backgroundColor(Color.White)
      .width(150)
      .height(150)
      .justifyContent(FlexAlign.Center)
      .opacity(0.6)
      .renderGroup(this.renderGroupValue)
    }
    .backgroundColor(Color.Black)
    .width(200)
    .height(200)
    .justifyContent(FlexAlign.Center)
    .opacity(1)
  }
}

@Entry
@Component
struct RenderGroupExample {
  build() {
    Column() {
      RenderGroupChildComponent({ renderGroupValue: true })
        .margin(20)
      RenderGroupChildComponent({ renderGroupValue: false })
        .margin(20)
    }
    .width("100%")
    .height("100%")
    .alignItems(HorizontalAlign.Center)
  }
}
```

### 示例4（当前组件内容与下方画布内容混合）

该示例主要演示通过[blendMode](#blendmode11)将当前组件内容与下方画布内容混合。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      Text("blendMode")
        .fontSize(20)
        .fontWeight(FontWeight.Bold)
        .fontColor('#ffff0101')
      Row() {
        Circle()
          .width(200)
          .height(200)
          .fill(Color.Green)
          .position({ x: 50, y: 50 })
        Circle()
          .width(200)
          .height(200)
          .fill(Color.Blue)
          .position({ x: 150, y: 50 })
      }
      .blendMode(BlendMode.OVERLAY, BlendApplyType.OFFSCREEN)
      .alignItems(VerticalAlign.Center)
      .height(300)
      .width('100%')
    }
    .height('100%')
    .width('100%')
    // $r("app.media.image")需要替换为开发者所需的图像资源文件。
    .backgroundImage($r('app.media.image'))
    .backgroundImageSize(ImageSize.Cover)
  }
}
```

### 示例5（前景智能取反色）

该示例主要通过[InvertOptions](#invertoptions11对象说明)来实现前景智能取反色。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Stack() {
      Column()
      Stack() {
        // $r("app.media.r")需要替换为开发者所需的图像资源文件。
        // 该示例中图片为从左到右，颜色由浅到深。
        Image($r('app.media.r')).width('100%')
        Column() {
          Column().width("100%").height(30).invert({
            low: 0,
            high: 1,
            threshold: 0.5,
            thresholdRange: 0.2
          })
          Column().width("100%").height(30).invert({
            low: 0.2,
            high: 0.5,
            threshold: 0.3,
            thresholdRange: 0.2
          })
        }
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

### 示例6（设置同层阴影不重叠效果）

该示例主要通过[useShadowBatching](arkts-arkui-common-comp-commonmethod-c.md#useshadowbatching)搭配[shadow](#shadow)实现同层阴影不重叠效果。



```TypeScript
// xxx.ets
@Entry
@Component
struct UseShadowBatchingExample {
  build() {
    Column() {
      Column({ space: 10 }) {
        Stack() {

        }
        .width('90%')
        .height(50)
        .margin({ top: 5 })
        .backgroundColor(0xFFE4C4)
        .shadow({
          radius: 120,
          color: Color.Green,
          offsetX: 0,
          offsetY: 0
        })
        .align(Alignment.TopStart)
        .shadow({
          radius: 120,
          color: Color.Green,
          offsetX: 0,
          offsetY: 0
        })

        Stack() {

        }
        .width('90%')
        .height(50)
        .margin({ top: 5 })
        .backgroundColor(0xFFE4C4)
        .align(Alignment.TopStart)
        .shadow({
          radius: 120,
          color: Color.Red,
          offsetX: 0,
          offsetY: 0
        })
        .width('90%')
        .backgroundColor(Color.White)

        Column() {
          Text()
            .fontWeight(FontWeight.Bold)
            .fontSize(20)
            .fontColor(Color.White)
        }
        .justifyContent(FlexAlign.Center)
        .width(150)
        .height(150)
        .borderRadius(10)
        .backgroundColor(0xf56c6c)
        .shadow({
          radius: 300,
          color: Color.Yellow,
          offsetX: 0,
          offsetY: 0
        })

        Column() {
          Text()
            .fontWeight(FontWeight.Bold)
            .fontSize(20)
            .fontColor(Color.White)
        }
        .justifyContent(FlexAlign.Center)
        .width(150)
        .height(150)
        .backgroundColor(0x67C23A)
        .borderRadius(10)
        .translate({ y: -50 })
        .shadow({
          radius: 220,
          color: Color.Blue,
          offsetX: 0,
          offsetY: 0
        })
      }
      .useShadowBatching(true)
    }
    .width('100%').margin({ top: 5 })
  }
}
```

### 示例7（设置组件图像球面效果）

该示例主要演示通过[sphericalEffect](arkts-arkui-common-comp-commonmethod-c.md#sphericaleffect)设置组件的图像球面效果。

效果图如下：



去掉sphericalEffect的设置，效果如下：



```TypeScript
// xxx.ets
@Entry
@Component
struct SphericalEffectExample {
  build() {
    Stack() {
      TextInput({ placeholder: "请输入变化范围百分比（[0%,100%]）" })
        .width('50%')
        .height(35)
        .type(InputType.Number)
        .enterKeyType(EnterKeyType.Done)
        .caretColor(Color.Red)
        .placeholderColor(Color.Blue)
        .placeholderFont({
          size: 20,
          style: FontStyle.Italic,
          weight: FontWeight.Bold
        })
        .sphericalEffect(0.5)
    }.alignContent(Alignment.Center).width("100%").height("100%")
  }
}
```

### 示例8（设置组件图像渐亮效果）

该示例主要演示通过[lightUpEffect](arkts-arkui-common-comp-commonmethod-c.md#lightupeffect)设置组件的图像渐亮效果。

效果图如下：



修改lightUpEffect参数值为0.2：



去掉lightUpEffect的设置，效果如下：



```TypeScript
// xxx.ets
@Entry
@Component
struct LightUpExample {
  build() {
    Stack() {
      Text('This is the text content with letterSpacing 0.')
        .letterSpacing(0)
        .fontSize(12)
        .border({ width: 1 })
        .padding(10)
        .width('50%')
        .lightUpEffect(0.6)
    }.alignContent(Alignment.Center).width("100%").height("100%")
  }
}
```

### 示例9（设置组件图像边缘像素扩展效果）

该示例主要演示通过[pixelStretchEffect](arkts-arkui-common-comp-commonmethod-c.md#pixelstretcheffect)设置组件的图像边缘像素扩展效果。

效果图如下：



去掉pixelStretchEffect的设置，原图效果如下：



```TypeScript
// xxx.ets
@Entry
@Component
struct PixelStretchExample {
  build() {
    Stack() {
      Text('This is the text content with letterSpacing 0.')
        .letterSpacing(0)
        .fontSize(12)
        .border({ width: 1 })
        .padding(10)
        .clip(false)
        .width('50%')
        .pixelStretchEffect({
          top: 10,
          left: 10,
          right: 10,
          bottom: 10
        })
    }.alignContent(Alignment.Center).width("100%").height("100%")
  }
}
```

### 示例10（系统导航条智能反色）

该示例主要演示通过[systemBarEffect](arkts-arkui-common-comp-commonmethod-c.md#systembareffect)来实现系统导航条智能反色。

效果图如下：



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      Stack() {
        // $r("app.media.testImage")需要替换为开发者所需的图像资源文件。
        Image($r('app.media.testImage')).width('100%').height('100%')
        Column()
          .width(150)
          .height(10)
          .systemBarEffect()
          .border({ radius: 5 })
          .margin({ bottom: 80 })
      }.alignContent(Alignment.Center)
    }
  }
}
```

### 示例11（设置组件是否双面绘制）

该示例主要演示通过[doubleSided](arkts-arkui-common-comp-commonmethod-c.md#doublesided)来设置组件是否双面绘制。

从API版本26.0.0开始，新增doubleSided方法。

```TypeScript
// xxx.ets
@Entry
@Component
struct DoubleSided {
  @State angleY: number = 0;
  @State isAnimating: boolean = false;
  @State isDoubleSided: boolean = true;
  build() {
    Column({space: 30}) {
      Text('DoubleSided 背面剔除验证')
        .fontSize(24)
        .fontWeight(FontWeight.Bold)
        .fontColor(Color.White)
      Stack() {
        Stack() {
          Text('FRONT')
            .fontSize(32)
            .fontColor(Color.White)
        }
        .width(300)
        .height(300)
        .backgroundColor(Color.Blue)
        .border({ width: 2, color: Color.Gray })
        .doubleSided(this.isDoubleSided)
        .rotate({ x: 0, y: 1, z: 0, angle: this.angleY})
      }
      .width(300)
      .height(300)
      Text(`Y轴旋转： ${Math.round(this.angleY)}°`)
        .fontSize(16)
        .fontColor(Color.White)
      Button(this.isAnimating ? '复原' : '翻转')
        .onClick(() => {
          if (this.isAnimating) {
            this.angleY = 0
            this.isAnimating = false
          } else {
            this.isAnimating = true
            this.angleY = 180
          }
        })
      Button(`doubleSided: ${this.isDoubleSided ? 'true (双面)' : 'false (单面)'}`)
        .backgroundColor(this.isDoubleSided ? '#4CAF50' : '#F44336')
        .onClick(() => {
          this.isDoubleSided = !this.isDoubleSided
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .backgroundColor('#1a1a1a')
  }
}
```

通过ContentModifier实现自定义复选框样式的功能，用一个五边形复选框替换原本Checkbox的样式。如果选中，内部会出现红色三角图案，标题会显示选中字样；如果取消选中，红色三角图案消失，标题会显示非选中字样。

```TypeScript
// xxx.ets
class MyCheckboxStyle implements ContentModifier<CheckBoxConfiguration> {
  selectedColor: Color = Color.White;

  constructor(selectedColor: Color) {
    this.selectedColor = selectedColor;
  }

  applyContent(): WrappedBuilder<[CheckBoxConfiguration]> {
    return wrapBuilder(buildCheckbox);
  }
}

@Builder
function buildCheckbox(config: CheckBoxConfiguration) {
  Column({ space: 10 }) {
    Text(config.name + (config.selected ? "（选中）" : "（非选中）"))
    Shape() {
      // 五边形复选框样式
      Path()
        .width(200)
        .height(60)
        .commands('M100 0 L0 100 L50 200 L150 200 L200 100 Z')
        .fillOpacity(0)
        .strokeWidth(3)
      // 红色三角图案样式
      Path()
        .width(10)
        .height(10)
        .commands('M50 0 L100 100 L0 100 Z')
        .visibility(config.selected ? Visibility.Visible : Visibility.Hidden)
        .fill(config.selected ? (config.contentModifier as MyCheckboxStyle).selectedColor : Color.Black)
        .stroke((config.contentModifier as MyCheckboxStyle).selectedColor)
        .margin({ left: 11, top: 10 })
    }
    .width(300)
    .height(200)
    .viewPort({
      x: 0,
      y: 0,
      width: 310,
      height: 310
    })
    .strokeLineJoin(LineJoinStyle.Miter)
    .strokeMiterLimit(5)
    .onClick(() => {
      // 点击后，触发复选框点击状态变化
      if (config.selected) {
        config.triggerChange(false);
      } else {
        config.triggerChange(true);
      }
    })
    .margin({ left: 150 })
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Checkbox({ name: '复选框状态', group: 'checkboxGroup' })
          .select(true)
          .contentModifier(new MyCheckboxStyle(Color.Red))
          .onChange((value: boolean) => {
            console.info('Checkbox change is' + value);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

```TypeScript
// 组件添加allowForceDark(false)属性后，说明对当前组件及其所有子组件均不使用反色相关能力。
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Column() {
        Text("Hello World")
          .fontSize(20)
          .fontColor(Color.Blue)
          .onClick(() => {
            console.info(`Text is clicked`);
          })
      }
      .allowForceDark(false) // Column及其子组件Text不使用反色能力，不受父组件Column使用反色能力的影响。

      Row() {
        Button('BUTTON')
          .backgroundColor(Color.Grey)
          .allowForceDark(true)
          .onClick(() => {
            console.info(`Button is clicked`);
          })
      }
      .allowForceDark(false) // Row及其子组件Button不使用反色能力，不受父组件Column使用反色能力的影响。
    }
    .allowForceDark(true)
    .width('100%')
    .height('100%')
  }
}
```

该示例演示如何通过配置monopolizeEvents设置组件是否独占事件。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State message: string = 'set monopolizeEvents false';
  @State messageOut: string = ' ';
  @State messageInner: string = ' ';
  @State monopolize: boolean = false;

  build() {
    Column() {
      Text(this.message)
        .fontSize(22)
        .margin(10)
      Text(this.messageOut)
        .fontSize(22)
        .margin(10)
      Text(this.messageInner)
        .fontSize(22)
        .margin(10)
      Button('clean')
        .fontSize(22)
        .margin(10)
        // 通过button的点击事件清空内外层column的触摸事件提示信息。
        .onClick(() => {
          this.messageOut = ' ';
          this.messageInner = ' ';
        })
      Button('change monopolizeEvents')
        .fontSize(22)
        .margin(10)
        // 通过button的点击事件来切换内层column的独占控制属性。
        .onClick(() => {
          this.monopolize = !this.monopolize;
          if (!this.monopolize) {
            this.message = 'set monopolizeEvents false';
          } else {
            this.message = 'set monopolizeEvents true';
          }
        })
      Column() {
        Column() {
        }
        // this.monopolize是true时，点击内层column只会触发自身的触摸事件，不会触发外层column的触摸事件。
        // this.monopolize是false时，点击内层column会同时触发自身的触摸事件和外层column的触摸事件。
        .monopolizeEvents(this.monopolize)
        .width('100%')
        .height('40%')
        .backgroundColor(Color.Blue)
        // 内层column绑定触摸事件。
        .onTouch((event: TouchEvent) => {
          if (event.type == TouchType.Down) {
            console.info('inner column touch down');
            this.messageInner = 'inner column touch down';
          }
        })
      }
      .backgroundColor(Color.Gray)
      .height('100%')
      .width('100%')
      // 外层column绑定触摸事件。
      .onTouch((event) => {
        if (event.type == TouchType.Down) {
          console.info('outside column touch down');
          this.messageOut = 'outside column touch down';
        }
      })
    }
    .height('100%')
  }
}
```

### 示例1（设置组件拖拽和落入）

示例1展示了部分组件（如Image和Text等）拖拽和可落入区域的设置。



```TypeScript
// xxx.ets
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

@Entry
@Component
struct Index {
  @State targetImage: string = '';
  @State targetText: string = 'Drag Text';
  @State imageWidth: number = 100;
  @State imageHeight: number = 100;
  @State imgState: Visibility = Visibility.Visible;
  @State abstractContent: string = 'abstract';
  @State textContent: string = '';
  @State backGroundColor: Color = Color.Transparent;

  // 获取Udmf数据
  getDataFromUdmfRetry(event: DragEvent, callback: (data: DragEvent) => void) {
    try {
      let data: UnifiedData = event.getData();
      if (!data) {
        return false;
      }
      let records: Array<unifiedDataChannel.UnifiedRecord> = data.getRecords();
      if (!records || records.length <= 0) {
        return false;
      }
      callback(event);
      return true;
    } catch (error) {
      console.error(`Failed to get data. Code: ${error.code}, message: ${error.message}`);
      return false;
    }
  }

  // 首次获取Udmf数据失败后自动重试
  getDataFromUdmf(event: DragEvent, callback: (data: DragEvent) => void) {
    if (this.getDataFromUdmfRetry(event, callback)) {
      return;
    }
    setTimeout(() => {
      this.getDataFromUdmfRetry(event, callback);
    }, 1500);
  }

  // 根据拖拽发起前的不同阶段更改背景色
  private preDragChange(preDragStatus: PreDragStatus): void {
    if (preDragStatus == PreDragStatus.READY_TO_TRIGGER_DRAG_ACTION) {
      this.backGroundColor = Color.Red;
    } else if (preDragStatus == PreDragStatus.ACTION_CANCELED_BEFORE_DRAG
      || preDragStatus == PreDragStatus.PREVIEW_LANDING_FINISHED) {
      this.backGroundColor = Color.Blue;
    }
  }

  build() {
    Row() {
      Column() {
        Text('start Drag')
          .fontSize(18)
          .width('100%')
          .height(40)
          .margin(10)
          .backgroundColor('#008888')
        // $r('app.media.icon')需要替换为开发者所需的图像资源文件
        Image($r('app.media.icon'))
          .width(100)
          .height(100)
          .draggable(true)
          .margin({ left: 15 })
          .visibility(this.imgState)
          .onDragEnd((event) => {
            // onDragEnd里取到的result值在接收方onDrop设置
            if (event.getResult() === DragResult.DRAG_SUCCESSFUL) {
              this.getUIContext().getPromptAction().showToast({ duration: 100, message: 'Drag Success' });
            } else if (event.getResult() === DragResult.DRAG_FAILED) {
              this.getUIContext().getPromptAction().showToast({ duration: 100, message: 'Drag failed' });
            }
          })
        Text('test drag event')
          .width('100%')
          .height(100)
          .draggable(true)
          .margin({ left: 15 })
          .copyOption(CopyOptions.InApp)
        TextArea({ placeholder: 'please input words' })
          .copyOption(CopyOptions.InApp)
          .width('100%')
          .height(50)
          .draggable(true)
        Search({ placeholder: 'please input your word' })
          .searchButton('Search')
          .width('100%')
          .height(80)
          .textFont({ size: 20 })

        Column() {
          Text('this is abstract')
            .fontSize(20)
            .width('100%')
        }
        .margin({ left: 40, top: 20 })
        .width('100%')
        .height(100)
        .onDragStart((event) => {
          this.backGroundColor = Color.Transparent;
          let data: unifiedDataChannel.PlainText = new unifiedDataChannel.PlainText();
          data.abstract = 'this is abstract';
          data.textContent = 'this is content this is content';
          (event as DragEvent).setData(new unifiedDataChannel.UnifiedData(data));
        })
        .onPreDrag((status: PreDragStatus) => {
          this.preDragChange(status);
        })
        .backgroundColor(this.backGroundColor)
      }.width('45%')
      .height('100%')

      Column() {
        Text('Drag Target Area')
          .fontSize(20)
          .width('100%')
          .height(40)
          .margin(10)
          .backgroundColor('#008888')
        Image(this.targetImage)
          .width(this.imageWidth)
          .height(this.imageHeight)
          .draggable(true)
          .margin({ left: 15 })
          .border({ color: Color.Black, width: 1 })
          .allowDrop([uniformTypeDescriptor.UniformDataType.IMAGE])
          .onDrop((dragEvent?: DragEvent) => {
            this.getDataFromUdmf((dragEvent as DragEvent), (event: DragEvent) => {
              let records: Array<unifiedDataChannel.UnifiedRecord> = event.getData().getRecords();
              let rect: Rectangle = event.getPreviewRect();
              this.imageWidth = Number(rect.width);
              this.imageHeight = Number(rect.height);
              this.targetImage = (records[0] as unifiedDataChannel.Image).imageUri;
              event.useCustomDropAnimation = false;
              this.imgState = Visibility.None;
              // 显式设置result为successful，则将该值传递给拖出方的onDragEnd
              event.setResult(DragResult.DRAG_SUCCESSFUL);
            });
          })

        Text(this.targetText)
          .width('100%')
          .height(100)
          .border({ color: Color.Black, width: 1 })
          .margin(15)
          .allowDrop([uniformTypeDescriptor.UniformDataType.PLAIN_TEXT])
          .onDrop((dragEvent?: DragEvent) => {
            this.getDataFromUdmf((dragEvent as DragEvent), (event: DragEvent) => {
              let records: Array<unifiedDataChannel.UnifiedRecord> = event.getData().getRecords();
              let plainText: unifiedDataChannel.PlainText = records[0] as unifiedDataChannel.PlainText;
              this.targetText = plainText.textContent;
            });
          })

        Column() {
          Text(this.abstractContent).fontSize(20).width('100%')
          Text(this.textContent).fontSize(15).width('100%')
        }
        .width('100%')
        .height(100)
        .margin(20)
        .border({ color: Color.Black, width: 1 })
        .allowDrop([uniformTypeDescriptor.UniformDataType.PLAIN_TEXT])
        .onDrop((dragEvent?: DragEvent) => {
          this.getDataFromUdmf((dragEvent as DragEvent), (event: DragEvent) => {
            let records: Array<unifiedDataChannel.UnifiedRecord> = event.getData().getRecords();
            let plainText: unifiedDataChannel.PlainText = records[0] as unifiedDataChannel.PlainText;
            this.abstractContent = plainText.abstract as string;
            this.textContent = plainText.textContent;
          });
        })
      }.width('45%')
      .height('100%')
      .margin({ left: '5%' });
    }
    .height('100%')
  }
}
```

### 示例2（自定义落位动效）

从API version 18开始，示例2展示了通过[executeDropAnimation](arkts-arkui-common-comp-dragevent-i.md#executedropanimation)接口，实现自定义落位动效。



```TypeScript
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

@Entry
@Component
struct DropAnimationExample {
  @State targetImage: string = '';
  @State imageWidth: number = 100;
  @State imageHeight: number = 100;
  @State imgState: Visibility = Visibility.Visible;
  customDropAnimation =
    () => {
      this.getUIContext().animateTo({ duration: 1000, curve: Curve.EaseOut, playMode: PlayMode.Normal }, () => {
        this.imageWidth = 200;
        this.imageHeight = 200;
        this.imgState = Visibility.None;
      })
    }

  build() {
    Row() {
      Column() {
        // $r('app.media.app_icon')需要替换为开发者所需的图像资源文件
        Image($r('app.media.app_icon'))
          .width(100)
          .height(100)
          .draggable(true)
          .margin({ left: 15, top: 40 })
          .visibility(this.imgState)
          .onDragStart((event) => {
          })
          .onDragEnd((event) => {
            if (event.getResult() === DragResult.DRAG_SUCCESSFUL) {
              console.info('Drag Success');
            } else if (event.getResult() === DragResult.DRAG_FAILED) {
              console.error('Drag failed');
            }
          })
      }.width('45%')
      .height('100%')

      Column() {
        Text('Drag Target Area')
          .fontSize(20)
          .width(180)
          .height(40)
          .textAlign(TextAlign.Center)
          .margin(10)
          .backgroundColor('rgb(240,250,255)')
        Column() {
          Image(this.targetImage)
            .width(this.imageWidth)
            .height(this.imageHeight)
        }
        .draggable(true)
        .margin({ left: 15 })
        .border({ color: Color.Black, width: 1 })
        .allowDrop([uniformTypeDescriptor.UniformDataType.IMAGE])
        // onDrop回调，获取拖拽图片的信息和尺寸并更新显示，同时启用并执行自定义下落动画
        .onDrop((dragEvent: DragEvent) => {
          let records: Array<unifiedDataChannel.UnifiedRecord> = dragEvent.getData().getRecords();
          let rect: Rectangle = dragEvent.getPreviewRect();
          this.imageWidth = Number(rect.width);
          this.imageHeight = Number(rect.height);
          this.targetImage = (records[0] as unifiedDataChannel.Image).imageUri;
          dragEvent.useCustomDropAnimation = true;
          dragEvent.executeDropAnimation(this.customDropAnimation);
        })
        .width(this.imageWidth)
        .height(this.imageHeight)
      }.width('45%')
      .height('100%')
      .margin({ left: '5%' })
    }
    .height('100%')
  }
}
```

### 示例3（拖拽异步获取数据）

从API version 15开始，示例3展示了通过[startDataLoading](arkts-arkui-common-comp-dragevent-i.md#startdataloading)实现拖拽异步获取数据。

```TypeScript
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';
import { fileUri, fileIo } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct ImageExample {
  @State uri: string = '';
  @State blockArr: string[] = [];
  uiContext = this.getUIContext();
  udKey: string = '';

  build() {
    Column() {
      Text('Image拖拽')
        .fontSize('30dp')
      Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center, justifyContent: FlexAlign.SpaceAround }) {
        // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件
        Image($r('app.media.startIcon'))
          .width(100)
          .height(100)
          .border({ width: 1 })
          .draggable(true)
          .onDragStart((event: DragEvent) => {
            const context: Context | undefined = this.uiContext.getHostContext();
            if (context) {
              let data = context.resourceManager.getMediaContentSync($r('app.media.startIcon').id, 120);
              const arrayBuffer: ArrayBuffer = data.buffer.slice(data.byteOffset, data.byteLength + data.byteOffset);
              let filePath = context.filesDir + '/test.png';
              let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
              try {
                fileIo.writeSync(file.fd, arrayBuffer);
              } finally {
                fileIo.closeSync(file.fd);
              }
              // 获取图片的uri
              let uri = fileUri.getUriFromPath(filePath);
              let image: unifiedDataChannel.Image = new unifiedDataChannel.Image();
              image.imageUri = uri;
              let dragData: unifiedDataChannel.UnifiedData = new unifiedDataChannel.UnifiedData(image);
              (event as DragEvent).setData(dragData);
            }
          })
      }
      .margin({ bottom: 20 })

      Row() {
        Column() {
          Text('可释放区域')
            .fontSize('15dp')
            .height('10%')
          List() {
            ForEach(this.blockArr, (item: string, index) => {
              ListItem() {
                Image(item)
                  .width(100)
                  .height(100)
                  .border({ width: 1 })
              }
              .margin({ left: 30, top: 30 })
            }, (item: string) => item)
          }
          .border({ width: 1 })
          .height('90%')
          .width('100%')
          .onDrop((event?: DragEvent, extraParams?: string) => {
            console.info('enter onDrop');
            let context = this.uiContext.getHostContext() as common.UIAbilityContext;
            let pathDir: string = context.distributedFilesDir;
            let destUri = fileUri.getUriFromPath(pathDir);
            // 创建DataProgressListener监听数据传输进度
            let progressListener: unifiedDataChannel.DataProgressListener =
              (progress: unifiedDataChannel.ProgressInfo, dragData: UnifiedData | null) => {
                if (dragData != null) {
                  // 获取数据记录数组
                  let arr: Array<unifiedDataChannel.UnifiedRecord> = dragData.getRecords();
                  if (arr.length > 0) {
                    // 检查首记录类型是否为IMAGE
                    if (arr[0].getType() === uniformTypeDescriptor.UniformDataType.IMAGE) {
                      // 类型匹配成功，记录数据Uri
                      let image = arr[0] as unifiedDataChannel.Image;
                      this.uri = image.imageUri;
                      this.blockArr.splice(JSON.parse(extraParams as string).insertIndex, 0, this.uri);
                    }
                  } else {
                    console.info('dragData arr is null');
                  }
                } else {
                  console.info('dragData is undefined');
                }
                console.info(`percentage: ${progress.progress}`);
              };
            // 设置异步数据加载参数项
            let options: DataSyncOptions = {
              destUri: destUri,
              fileConflictOptions: unifiedDataChannel.FileConflictOptions.OVERWRITE,
              progressIndicator: unifiedDataChannel.ProgressIndicator.DEFAULT,
              dataProgressListener: progressListener,
            }
            try {
              // 启动数据传输
              this.udKey = (event as DragEvent).startDataLoading(options);
              console.info(`udKey: ${this.udKey}`);
            } catch (e) {
              console.error(`Failed to start data loading. Code: ${e.code}, message: ${e.message}`);
            }
          }, { disableDataPrefetch: true })
        }
        .height('50%')
        .width('90%')
        .border({ width: 1 })
      }

      Button('取消数据传输')
        .onClick(() => {
          try {
            this.getUIContext().getDragController().cancelDataLoading(this.udKey);
          } catch (e) {
            console.error(`Failed to cancel data loading. Code: ${e.code}, message: ${e.message}`);
          }
        })
        .margin({ top: 10 })
    }.width('100%')
  }
}
```

### 示例4（获取当前拖拽的屏幕ID）

从API version 20开始，示例4展示了通过onDragXXX（不支持onDragEnd）接口获取拖拽事件，并调用拖拽事件的[getDisplayId](#getdisplayid20)接口获取屏幕ID。



```TypeScript
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

@Entry
@Component
struct Index {
  @State targetImage: string = '';
  @State imageWidth: number = 100;
  @State imageHeight: number = 100;
  @State imgState: Visibility = Visibility.Visible;
  @State backGroundColor: Color = Color.Transparent;
  @State startDisplayId: number = -1;
  @State enterDisplayId: number = -1;
  @State moveDisplayId: number = -1;
  @State leaveDisplayId: number = -1;
  @State dropDisplayId: number = -1;

  getDataFromUdmfRetry(event: DragEvent, callback: (data: DragEvent) => void) {
    try {
      let data: UnifiedData = event.getData();
      if (!data) {
        return false;
      }
      let records: Array<unifiedDataChannel.UnifiedRecord> = data.getRecords();
      if (!records || records.length <= 0) {
        return false;
      }
      callback(event);
      return true;
    } catch (error) {
      console.error(`Failed to get data. Code: ${error.code}, message: ${error.message}`);
      return false;
    }
  }

  getDataFromUdmf(event: DragEvent, callback: (data: DragEvent) => void) {
    if (this.getDataFromUdmfRetry(event, callback)) {
      return;
    }
    setTimeout(() => {
      this.getDataFromUdmfRetry(event, callback);
    }, 1500);
  }

  private preDragChange(preDragStatus: PreDragStatus): void {
    if (preDragStatus == PreDragStatus.READY_TO_TRIGGER_DRAG_ACTION) {
      this.backGroundColor = Color.Red;
    } else if (preDragStatus == PreDragStatus.ACTION_CANCELED_BEFORE_DRAG
      || preDragStatus == PreDragStatus.PREVIEW_LANDING_FINISHED) {
      this.backGroundColor = Color.Blue;
    }
  }

  build() {
    Row() {
      Column() {
        Text('start Drag')
          .fontSize(18)
          .width('100%')
          .height(40)
          .margin(10)
          .backgroundColor('#008888')
        // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件
        Image($r('app.media.startIcon'))
          .width(100)
          .height(100)
          .draggable(true)
          .margin({ left: 15 })
          .visibility(this.imgState)
          .onDragStart((event) => {
            let id = event.getDisplayId();
            this.startDisplayId = id;
          })

          .onDragEnd((event) => {
            if (event.getResult() === DragResult.DRAG_SUCCESSFUL) {
              this.getUIContext().getPromptAction().showToast({ duration: 100, message: 'Drag Success' });
            } else if (event.getResult() === DragResult.DRAG_FAILED) {
              this.getUIContext().getPromptAction().showToast({ duration: 100, message: 'Drag failed' });
            }
          })

        Text('displayID in onDragStart: ' + this.startDisplayId.toString())
          .width('100%')
          .height(50)
          .draggable(true)
          .margin({ left: 15 })
        Text('displayID in onDragEnter: ' + this.enterDisplayId.toString())
          .width('100%')
          .height(50)
          .draggable(true)
          .margin({ left: 15 })
        Text('displayID in onDragMove: ' + this.moveDisplayId.toString())
          .width('100%')
          .height(50)
          .draggable(true)
          .margin({ left: 15 })
        Text('displayID in onDragLeave: ' + this.leaveDisplayId.toString())
          .width('100%')
          .height(50)
          .draggable(true)
          .margin({ left: 15 })
        Text('displayID in onDrop: ' + this.dropDisplayId.toString())
          .width('100%')
          .height(50)
          .draggable(true)
          .margin({ left: 15 })
          .onPreDrag((status: PreDragStatus) => {
            this.preDragChange(status);
          })
      }.width('45%')
      .height('100%')

      Column() {
        Text('Drag Target Area')
          .fontSize(20)
          .width('100%')
          .height(40)
          .margin(10)
          .backgroundColor('#008888')
        Image(this.targetImage)
          .width(this.imageWidth)
          .height(this.imageHeight)
          .draggable(true)
          .margin({ left: 15 })
          .border({ color: Color.Black, width: 1 })
          .allowDrop([uniformTypeDescriptor.UniformDataType.IMAGE])
          .onDragEnter((event) => {
            let id = event.getDisplayId();
            this.enterDisplayId = id;
          })
          .onDragMove((event) => {
            let id = event.getDisplayId();
            this.moveDisplayId = id;
          })
          .onDragLeave((event) => {
            let id = event.getDisplayId();
            this.leaveDisplayId = id;
          })
          .onDrop((dragEvent: DragEvent) => {
            let id = dragEvent.getDisplayId();
            this.dropDisplayId = id;
            this.getDataFromUdmf((dragEvent as DragEvent), (event: DragEvent) => {
              let records: Array<unifiedDataChannel.UnifiedRecord> = event.getData().getRecords();
              let rect: Rectangle = event.getPreviewRect();
              this.imageWidth = Number(rect.width);
              this.imageHeight = Number(rect.height);
              this.targetImage = (records[0] as unifiedDataChannel.Image).imageUri;
              event.useCustomDropAnimation = false;
              this.imgState = Visibility.None;
              event.setResult(DragResult.DRAG_SUCCESSFUL);
            });
          })
      }.width('45%')
      .height('100%')
      .margin({ left: '5%' })
    }
    .height('100%')
  }
}
```

### 示例5（获取包名和是否是跨设备）

从API version 20开始，示例5展示了通过onDragXXX接口获取拖拽事件，调用拖拽事件的[getDragSource](arkts-arkui-common-comp-dragevent-i.md#getdragsource)接口获取包名，调用isRemote接口判断是否为跨设备拖拽。



```TypeScript
@Entry
@Component
struct Index {
  @State targetImage: string = '';
  @State startDragSource: string = '';
  @State startIsRemote: boolean = true;
  @State enterDragSource: string = '';
  @State enterIsRemote: boolean = true;

  build() {
    Column() {
      Row() {
        Column() {
          Text('start Drag Area')
            .fontSize(18)
            .width('100%')
            .height(40)
            .margin(10)
            .backgroundColor('#008888')
          // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件
          Image($r('app.media.startIcon'))
            .onDragStart((event) => {
              this.startDragSource = (event as DragEvent).getDragSource();
              this.startIsRemote = (event as DragEvent).isRemote();
            })
            .width(100)
            .height(100)
            .draggable(true)
            .margin({ left: 15 })
        }
        .border({ color: Color.Black, width: 1 })
        .width('45%')
        .height('50%')

        Column() {
          Text('Drag Target Area')
            .fontSize(20)
            .width('100%')
            .height(40)
            .margin(10)
            .backgroundColor('#008888')
          Image(this.targetImage)
            .width(100)
            .height(100)
            .draggable(true)
            .margin({ left: 15 })
            .border({ color: Color.Black, width: 1 })
            .onDragEnter((event) => {
              this.enterDragSource = (event as DragEvent).getDragSource();
              this.enterIsRemote = (event as DragEvent).isRemote();
            })
            .onDrop(() => {
            })
        }
        .border({ color: Color.Black, width: 1 })
        .width('45%')
        .height('50%')
        .margin({ left: '5%' })
      }
      .height('70%')

      Text('onDragStart dragSource: ' + this.startDragSource.toString() + '\n' + 'onDragStart isRemote: ' +
      this.startIsRemote.toString())
        .width('100%')
        .height(50)
        .margin({ left: 15 })
      Text('onDragEnter dragSource: ' + this.enterDragSource.toString() + '\n' + 'onDragEnter isRemote: ' +
      this.enterIsRemote.toString())
        .width('100%')
        .height(50)
        .margin({ left: 15 })
    }
  }
}
```

### 示例6（拖拽支持悬停检测）

从API version 20开始，示例6展示了通过[onDragSpringLoading](arkts-arkui-common-comp-commonmethod-c.md#ondragspringloading)接口注册回调，并通过回调中的[SpringLoadingContext](#springloadingcontext20)获取上下文信息（当前状态、通知序列）。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State state: number = 0;
  @State currentNotifySequence: number = 0;
  @State config: DragSpringLoadingConfiguration = {
    stillTimeLimit: 200,
    updateInterval: 300,
    updateNotifyCount: 4,
    updateToFinishInterval: 300
  };

  build() {
    Row() {
      Column() {
        Text('start Drag')
          .fontSize(18)
          .width('100%')
          .height(40)
          .margin(10)
          .backgroundColor('#008888')
        // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件
        Image($r('app.media.startIcon'))
          .id('ori_image')
          .width(100)
          .height(100)
          .draggable(true)
          .margin({ left: 15 })
        Text('当前状态是: ' + this.state)
          .fontSize(18)
          .width('100%')
          .height(40)
          .margin(10)
        Text('当前通知序列是: ' + this.currentNotifySequence)
          .fontSize(18)
          .width('100%')
          .height(40)
          .margin(10)
      }
      .width('45%')
      .height('100%')

      Column() {
        Text('Drag Target Area')
          .fontSize(20)
          .width('100%')
          .height(40)
          .margin(10)
          .backgroundColor('#008888')
          .id('text')
        Image('')
          .width(100)
          .height(100)
          .draggable(true)
          .margin({ left: 15 })
          .border({ color: Color.Black, width: 2 })
          .onDragSpringLoading((context: SpringLoadingContext) => {
            this.state = context.state;
            this.currentNotifySequence = context.currentNotifySequence;
          }, this.config)
      }
      .width('45%')
      .height('100%')
      .margin({ left: '5%' })
      .onDragSpringLoading((context: SpringLoadingContext) => {
        this.state = context.state;
        this.currentNotifySequence = context.currentNotifySequence;
      }, this.config)
      .id('column')
      .backgroundColor(Color.Grey)
    }
    .height('100%')
  }
}
```

### 示例7（拖起方延迟提供数据）

从API version 20开始，示例7展示了在[onDragStart](#ondragstart)中调用[setDataLoadParams](arkts-arkui-common-comp-dragevent-i.md#setdataloadparams)延迟提供数据接口，并在[onDrop](#ondrop)中调用[startDataLoading](arkts-arkui-common-comp-dragevent-i.md#startdataloading)异步获取数据接口。



```TypeScript
import { unifiedDataChannel, uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { fileUri, fileIo } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct VideoExample {
  @State uri: string = '';
  @State blockArr: string[] = [];
  uiContext = this.getUIContext();
  udKey: string = '';

  build() {
    Column() {
      Text('video拖拽')
        .fontSize('30dp')
      Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center, justifyContent: FlexAlign.SpaceAround }) {
        // $rawfile('test1.mp4')需要替换为开发者所需的资源文件
        Video({ src: $rawfile('test1.mp4'), controller: new VideoController() })
          .width(200)
          .height(200)
          .border({ width: 1 })
          .draggable(true)
          .onDragStart((event: DragEvent) => {
            const context: Context | undefined = this.uiContext.getHostContext();
            if (context) {
              // 定义延迟数据加载回调，在目标端请求数据时读取视频资源并封装为UnifiedData。
              let loadHandler: unifiedDataChannel.DataLoadHandler = (acceptableInfo) => {
                console.info(`acceptableInfo recordCount ${acceptableInfo?.recordCount}`);
                if (acceptableInfo?.types) {
                  console.info(`acceptableInfo types ${Array.from(acceptableInfo.types)}`);
                } else {
                  console.error('acceptableInfo types is undefined');
                }
                let data = context.resourceManager.getRawFdSync('test1.mp4');
                let filePath = context.filesDir + '/test1.mp4';
                let file: fileIo.File = null!;
                try {
                  file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
                  let bufferSize = data.length as number;
                  let buf = new ArrayBuffer(bufferSize);
                  fileIo.readSync(data.fd, buf, { offset: data.offset, length: bufferSize });
                  fileIo.writeSync(file.fd, buf, { offset: 0, length: bufferSize });
                } catch (error) {
                  console.error(`Failed to open file. Code: ${error.code}, message: ${error.message}`);
                } finally {
                  if (file !== null) {
                    fileIo.closeSync(file.fd);
                  }
                }
                context.resourceManager.closeRawFdSync('test1.mp4');
                this.uri = fileUri.getUriFromPath(filePath);
                let videoMp: uniformDataStruct.FileUri = {
                  uniformDataType: 'general.file-uri',
                  oriUri: this.uri,
                  fileType: 'general.video',
                };
                let unifiedRecord = new unifiedDataChannel.UnifiedRecord();
                let unifiedData = new unifiedDataChannel.UnifiedData();
                unifiedRecord.addEntry(uniformTypeDescriptor.UniformDataType.FILE_URI, videoMp);
                unifiedData.addRecord(unifiedRecord);
                return unifiedData;
              }
              (event as DragEvent).setDataLoadParams({
                loadHandler: loadHandler,
                dataLoadInfo: { types: new Set([uniformTypeDescriptor.UniformDataType.FILE_URI]), recordCount: 1 }
              });
            }
          })
      }
      .margin({ bottom: 20 })

      Row() {
        Column() {
          Text('可释放区域')
            .fontSize('15dp')
            .height('10%')
          List() {
            ForEach(this.blockArr, (item: string, index) => {
              ListItem() {
                Video({ src: item, controller: new VideoController() })
                  .width(100)
                  .height(100)
                  .border({ width: 1 })
              }
              .margin({ left: 30, top: 30 })
            }, (item: string) => item)
          }
          .border({ width: 1 })
          .height('90%')
          .width('100%')
          .onDrop((event: DragEvent, extraParams?: string) => {
            let context = this.uiContext.getHostContext() as common.UIAbilityContext;
            let pathDir: string = context.distributedFilesDir;
            let destUri = fileUri.getUriFromPath(pathDir);
            let progressListener: unifiedDataChannel.DataProgressListener =
              (progress: unifiedDataChannel.ProgressInfo, dragData: UnifiedData | null) => {
                if (dragData != null) {
                  let arr: Array<unifiedDataChannel.UnifiedRecord> = dragData.getRecords();
                  if (arr.length > 0) {
                    if (arr[0].getType() === uniformTypeDescriptor.UniformDataType.VIDEO) {
                      this.blockArr.splice(JSON.parse(extraParams as string).insertIndex, 0, this.uri);
                    }
                  } else {
                    console.info('dragData arr is null');
                  }
                } else {
                  console.info('dragData is undefined');
                }
                console.info(`percentage: ${progress.progress}`);
              };
            let info: unifiedDataChannel.DataLoadInfo =
              { types: new Set([uniformTypeDescriptor.UniformDataType.VIDEO]), recordCount: 100 };
            let options: DataSyncOptions = {
              destUri: destUri,
              fileConflictOptions: unifiedDataChannel.FileConflictOptions.OVERWRITE,
              progressIndicator: unifiedDataChannel.ProgressIndicator.DEFAULT,
              dataProgressListener: progressListener,
              acceptableInfo: info,
            }
            try {
              // 启动异步数据加载，并保存数据加载标识用于后续取消传输。
              this.udKey = (event as DragEvent).startDataLoading(options);
              console.info(`udKey: ${this.udKey}`);
            } catch (error) {
              console.error(`startDataLoading errorCode: ${error.code}, errorMessage: ${error.message}`);
            }
          }, { disableDataPrefetch: true })
        }
        .height('50%')
        .width('90%')
        .border({ width: 1 })
      }

      Button('取消数据传输')
        .onClick(() => {
          try {
            this.getUIContext().getDragController().cancelDataLoading(this.udKey);
          } catch (error) {
            console.error(`cancelDataLoading errorCode: ${error.code}, errorMessage: ${error.message}`);
          }
        })
        .margin({ top: 10 })
    }.width('100%')
  }
}
```

### 示例8（拖拽自动隐藏指定组件）

该示例通过DragEvent的[autoHideComponentUniqueIds](#focuscontrol)属性，在拖拽成功发起后自动隐藏指定组件。

从API版本26.0.0开始，DragEvent新增autoHideComponentUniqueIds属性。

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@Component
struct DragEventAutoHideSample {
  @State sourceVisibility: Visibility = Visibility.Visible;
  @State badgeVisibility: Visibility = Visibility.Visible;
  @State statusText: string = '状态：等待拖拽';

  private buildData(textValue: string): unifiedDataChannel.UnifiedData {
    let plainText = new unifiedDataChannel.PlainText();
    plainText.textContent = textValue;
    plainText.abstract = textValue;
    return new unifiedDataChannel.UnifiedData(plainText);
  }

  private collectHideIds(): number[] {
    let hideIds: number[] = [];
    let sourceNode = this.getUIContext().getFrameNodeById('drag_source');
    let badgeNode = this.getUIContext().getFrameNodeById('drag_badge');
    if (sourceNode?.getUniqueId() !== undefined) {
      hideIds.push(sourceNode.getUniqueId());
    }
    if (badgeNode?.getUniqueId() !== undefined) {
      hideIds.push(badgeNode.getUniqueId());
    }
    return hideIds;
  }

  private hideTargets(): void {
    this.sourceVisibility = Visibility.Hidden;
    this.badgeVisibility = Visibility.Hidden;
    this.statusText = '状态：拖拽中，目标组件已隐藏';
  }

  private restoreTargets(): void {
    this.sourceVisibility = Visibility.Visible;
    this.badgeVisibility = Visibility.Visible;
    this.statusText = '状态：拖拽结束，组件已恢复显示';
  }

  build() {
    Column({ space: 12 }) {
      Text(this.statusText)
        .width('100%')
        .fontSize(14)
        .fontColor('#BF360C')

      Row({ space: 12 }) {
        Column() {
          Text('拖拽源')
            .fontColor(Color.White)
            .fontWeight(FontWeight.Medium)
          Text('id: drag_source')
            .fontSize(10)
            .fontColor('#E8F5E9')
        }
          .id('drag_source')
          .width(140)
          .height(90)
          .backgroundColor('#2E7D32')
          .borderRadius(12)
          .justifyContent(FlexAlign.Center)
          .visibility(this.sourceVisibility)
          .draggable(true)
          .onDragStart((event: DragEvent) => {
            let hideIds = this.collectHideIds();
            event.autoHideComponentUniqueIds = hideIds;
            event.setData(this.buildData('drag event auto hide test data'));
            this.hideTargets();
            return () => {
              Text('拖拽预览')
            };
          })
          .onDragEnd(() => {
            this.restoreTargets();
          })

        Column() {
          Text('跟随隐藏组件')
            .fontColor(Color.White)
            .fontWeight(FontWeight.Medium)
          Text('id: drag_badge')
            .fontSize(10)
            .fontColor('#E3F2FD')
        }
          .id('drag_badge')
          .width(140)
          .height(90)
          .backgroundColor('#1565C0')
          .borderRadius(12)
          .justifyContent(FlexAlign.Center)
          .visibility(this.badgeVisibility)
      }

      Column() {
        Text('拖拽落点')
          .fontWeight(FontWeight.Medium)
        Text('松手后恢复组件显示')
          .fontSize(10)
          .fontColor('#6D4C41')
      }
        .width('100%')
        .height(120)
        .backgroundColor('#FFE082')
        .borderRadius(12)
        .justifyContent(FlexAlign.Center)
        .onDrop(() => {
          this.restoreTargets();
        })
    }
    .width('100%')
    .padding(16)
  }
}
```

### 示例1（自定义布局代码示例）

自定义布局代码示例。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      CustomLayout({ builder: ColumnChildren })
    }
  }
}

// 通过builder的方式传递多个组件，作为自定义组件的一级子组件（即不包含容器组件，如Column）
@Builder
function ColumnChildren() {
  ForEach([1, 2, 3], (index: number) => { // 目前不支持使用lazyForEach语法。
    Text('S' + index)
      .fontSize(30)
      .width(100)
      .height(100)
      .borderWidth(2)
      .offset({ x: 10, y: 20 })
  })
}

@Component
struct CustomLayout {
  @Builder
  doNothingBuilder() {
  };

  @BuilderParam builder: () => void = this.doNothingBuilder;
  result: SizeResult = {
    width: 0,
    height: 0
  };

  // 第一步：计算各子组件的大小
  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let size = 100;
    // 设置初始约束基准值为100vp，每次迭代累加子组件宽度的一半，逐步递增约束。
    children.forEach((child) => {
      let result: MeasureResult = child.measure({
        minHeight: size,
        minWidth: size,
        maxWidth: size,
        maxHeight: size
      })
      size += result.width / 2;
    })
    this.result.width = 100;
    this.result.height = 400;
    return this.result;
  }
  // 第二步：放置各子组件的位置
  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    // 从固定起始位置反向计算子组件位置，实现从下到上的反向布局效果。
    let startPos = 300;
    children.forEach((child) => {
      let pos = startPos - child.measureResult.height;
      child.layout({ x: pos, y: pos })
    })
  }

  build() {
    this.builder()
  }
}
```

### 示例2（判断是否参与布局计算）

通过组件的位置灵活判断是否参与布局计算。



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      CustomLayout({ builder: ColumnChildren })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}

@Builder
function ColumnChildren() {
  ForEach([1, 2, 3], (item: number, index: number) => { // 目前不支持使用lazyForEach语法。
    Text('S' + item)
      .fontSize(20)
      .width(60 + 10 * index)
      .height(100)
      .borderWidth(2)
      .margin({ left:10 })
      .padding(10)
  })
}

@Component
struct CustomLayout {
  // 只布局一行，如果布局空间不够的子组件不显示的demo。
  @Builder
  doNothingBuilder() {
  };

  @BuilderParam builder: () => void = this.doNothingBuilder;
  result: SizeResult = {
    width: 0,
    height: 0
  };
  overFlowIndex: number = -1;

  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    let currentX = 0;
    let infinity = 100000;
    if (this.overFlowIndex == -1) {
      this.overFlowIndex = children.length;
    }
    for (let index = 0; index < children.length; ++index) {
      let child = children[index];
      if (index >= this.overFlowIndex) {
        // 如果子组件超出父组件范围，将它布局到较偏的位置，达到不显示的目的。
        child.layout({x: infinity, y: 0});
        continue;
      }
      child.layout({ x: currentX, y: 0 })
      let margin = child.getMargin();
      currentX += child.measureResult.width + margin.start + margin.end;
    }
  }

  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let width = 0;
    let height = 0;
    this.overFlowIndex = -1;
    // 假定该组件的宽度不能超过200vp，也不能超过最大约束。
    let maxWidth = Math.min(200, constraint.maxWidth as number);
    for (let index = 0; index < children.length; ++index) {
      let child = children[index];
      let childResult: MeasureResult = child.measure({
          minHeight: constraint.minHeight,
          minWidth: constraint.minWidth,
          maxWidth: constraint.maxWidth,
          maxHeight: constraint.maxHeight
      })
      let margin = child.getMargin();
      let newWidth = width + childResult.width + margin.start + margin.end;
      if (newWidth > maxWidth) {
        // 记录不该布局的组件的下标。
        this.overFlowIndex = index;
        break;
      }
      // 累积父组件的宽度和高度。
      width = newWidth;
      height = Math.max(height, childResult.height + margin.top + margin.bottom);
    }
    this.result.width = width;
    this.result.height = height;
    return this.result;
  }

  build() {
    this.builder()
  }
}
```

### 示例3（获取子组件FrameNode并设置相关属性）

通过uniqueId获取子组件的FrameNode，并调用FrameNode的API接口修改尺寸、背景颜色。



```TypeScript
import { FrameNode, NodeController } from '@kit.ArkUI';
@Entry
@Component
struct Index {
  build() {
    Column() {
      CustomLayout()
    }
  }
}

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext)
    return this.rootNode
  }
}

@Component
struct CustomLayout {
  @Builder
  childrenBuilder() {
    ForEach([1, 2, 3], (index: number) => { // 目前不支持使用LazyForEach语法。
      NodeContainer(new MyNodeController())
    })
  };

  @BuilderParam builder: () => void = this.childrenBuilder;
  result: SizeResult = {
    width: 0,
    height: 0
  };

  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    // 水平排列子组件，每个子组件间隔10vp。
    let prev = 0;
    children.forEach((child) => {
      let pos = prev + 10;
      prev = pos + child.measureResult.width
      child.layout({ x: pos, y: 0 })
    })
  }

  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    let size = 100;
    children.forEach((child) => {
      console.info('child uniqueId: ', child.uniqueId)
      const uiContext = this.getUIContext()
      if (uiContext) {
        let node: FrameNode | null = uiContext.getFrameNodeByUniqueId(child.uniqueId) // 获取NodeContainer组件的FrameNode。
        if (node) {
          node.getChild(0)!.commonAttribute.width(100)
          node.getChild(0)!.commonAttribute.height(100)
          node.getChild(0)!.commonAttribute.backgroundColor(Color.Pink) // 修改FrameNode的尺寸与背景颜色。
        }
      }
      child.measure({ minHeight: size, minWidth: size, maxWidth: size, maxHeight: size })
    })
    this.result.width = 320;
    this.result.height = 100;
    return this.result;
  }

  build() {
    this.builder()
  }
}
```

### 示例4（子组件超过父组件大小约束）

在自定义布局的自定义组件中，为子组件设置了[LayoutPolicy](./ts-universal-attributes-size.md#layoutpolicy15)对象的fixAtIdealSize属性。

```TypeScript
@Entry
@Component
struct Index {
  @Builder
  ColumnChildrenText() {
    Text('=====Text=====Text=====Text=====Text=====Text=====Text=====Text=====Text' )
      .fontSize(16).fontColor(Color.Black)
      .borderWidth(2).backgroundColor('#fff8dc')
      .width(LayoutPolicy.fixAtIdealSize) // 设置子组件宽度不受到父组件限制。
      .height(LayoutPolicy.fixAtIdealSize)  // 设置子组件高度不受到父组件限制。
  }

  build() {
    Column() {
      Column() {
        CustomLayoutText({ builder: this.ColumnChildrenText })
          .backgroundColor('#f0ffff').borderRadius(20).margin(10)
      }
      .width(300)
      .height(150)
      .margin(10)
      .backgroundColor(Color.Pink)
    }
    .width(350)
    .height(680)
    .margin(20)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
struct CustomLayoutText {
  @Builder
  doSomethingBuilder() {
  };

  @BuilderParam
  builder: () => void = this.doSomethingBuilder;
  result: SizeResult = {
    width: 0,
    height: 0
  };
  // 自定义组件进行自定义布局。
  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions) {
    let posY = 20;
    children.forEach((child) => {
      let posX = (selfLayoutInfo.width - child.measureResult.width) / 2;
      child.layout({ x: posX, y: posY })
      posY += child.measureResult.height + 30;
    })
  }

  onMeasureSize(selfLayoutInfo: GeometryInfo, children: Array<Measurable>, constraint: ConstraintSizeOptions) {
    children.forEach((child) => {
      child.measure({ maxWidth: 335, maxHeight: 50 }) // 设置自定义组件子组件大小的限制。
    })
    this.result.width = 200;
    this.result.height = 130;
    return this.result;
  }

  build() {
    this.builder()
  }
}
```
