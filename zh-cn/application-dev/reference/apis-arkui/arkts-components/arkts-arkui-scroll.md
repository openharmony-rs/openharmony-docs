# Scroll

可滚动的容器组件，当子组件的布局尺寸超过父组件的尺寸时，内容可以滚动。支持设置滚动方向、滚动条、边缘效果、嵌套滚动以及自由滚动缩放等能力，适用于内容超出显示区域或需要复杂滚动交互的场景。
> **说明：** > > - 该组件嵌套List子组件滚动时，若List不设置宽高，则默认全部加载。在对性能有要求的场景下，开发者应指定List的宽高，以避免默认全部加载影响性能。 > > - 该组件滚动的前提是主轴方向大小小于内容大小。 > > - Scroll组件通用属性clip的默认值为true。 > > - Scroll组件的高度超出屏幕显示范围时，可以通过设置通用属性[layoutWeight](arkts-arkui-commonmethod-c.md#layoutweight)让Scroll高度适应主轴的剩余空间。 > > - 手指触摸屏幕时，会停止当前触摸范围内所有滚动组件的滚动动画（[scrollTo](arkts-arkui-scroller-c.md#scrollto)和[scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex)接口 > 触发的滚动动画除外），包括边缘回弹动画。 > > - 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。

## 子组件

支持单个子组件。

> 从API version 21开始，Scroll单个子组件的宽高最大为16777216px；API version 20及之前，Scroll单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。

## Scroll

```TypeScript
Scroll(scroller?: Scroller)
```

创建Scroll滚动容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | [Scroller](arkts-arkui-scroller-c.md) | 否 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [OffsetOptions](arkts-arkui-offsetoptions-i.md) | 初始滚动偏移量的参数选项。 |
| [OffsetResult](arkts-arkui-offsetresult-i.md) | 滑动偏移量对象。 |
| [OnScrollFrameBeginHandlerResult](arkts-arkui-onscrollframebeginhandlerresult-i.md) | [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md)返回的实际相对上一帧滚动偏移量。 |
| [ScrollAnimationOptions](arkts-arkui-scrollanimationoptions-i.md) | 自定义滚动动效的参数选项。 |
| [ScrollEdgeOptions](arkts-arkui-scrolledgeoptions-i.md) | 滚动到边缘位置的参数选项。 |
| [ScrollOptions](arkts-arkui-scrolloptions-i.md) | 滚动到指定位置的参数选项。 |
| [ScrollPageOptions](arkts-arkui-scrollpageoptions-i.md) | 翻页模式的参数选项。 |
| [ScrollSnapOptions](arkts-arkui-scrollsnapoptions-i.md) | 限位滚动模式对象。 |
| [ScrollToIndexOptions](arkts-arkui-scrolltoindexoptions-i.md) | 滑动到指定Index的参数选项。 |
| [UIScrollEvent](arkts-arkui-uiscrollevent-i.md) | frameNode中[getEvent('Scroll')](../arkts-apis/arkts-arkui-typenode-getevent-f.md) 方法的返回值，可用于给Scroll节点设置滚动事件。UIScrollEvent继承于[UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md)。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnScrollEdgeCallback](arkts-arkui-onscrolledgecallback-t.md) | 滚动到边缘时触发的回调。 |
| [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md) | Scroll每帧滚动前触发的回调。 |
| [ScrollOnDidZoomCallback](arkts-arkui-scrollondidzoomcallback-t.md) | Scroll每帧缩放完成时触发的回调。 |
| [ScrollOnScrollCallback](arkts-arkui-scrollonscrollcallback-t.md) | Scroll滚动时触发的回调。 |
| [ScrollOnWillScrollCallback](arkts-arkui-scrollonwillscrollcallback-t.md) | Scroll滚动前触发的回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ScrollAlign](arkts-arkui-scrollalign-e.md) | 对齐方式枚举。 |
| [ScrollDirection](arkts-arkui-scrolldirection-e.md) | 滚动方向枚举。FREE（自由滚动）模式下支持的能力： |

## 示例

该示例展示了Scroll组件部分属性和scroller控制器的使用。

```TypeScript
// xxx.ets
import { curves } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) {
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
      .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
      .scrollBar(BarState.On) // 滚动条常驻显示
      .scrollBarColor(Color.Gray) // 滚动条颜色
      .scrollBarWidth(10) // 滚动条宽度
      .friction(0.6)
      .edgeEffect(EdgeEffect.None)
      .onWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
        console.info(`onWillScroll xOffset = ${xOffset}, yOffset = ${yOffset}, scrollState = ${scrollState}`);
      })
      .onScrollEdge((side: Edge) => {
        console.info('To the edge');
      })
      .onScrollStop(() => {
        console.info('Scroll Stop');
      })

      Button('scroll 150')
        .height('5%')
        .onClick(() => { // 下滑150.0vp
          this.scroller.scrollBy(0, 150);
        })
        .margin({ top: 10, left: 20 })
      Button('scroll 100')
        .height('5%')
        .onClick(() => { // 点击后滑动到指定位置，即下滑100.0vp的距离
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({ xOffset: 0, yOffset: yOffset + 100 });
        })
        .margin({ top: 60, left: 20 })
      Button('scroll 100')
        .height('5%')
        .onClick(() => { // 点击后滑动到指定位置，即下滑100.0vp的距离，滑动过程配置有动画
          let curve = curves.interpolatingSpring(10, 1, 228, 30); // 创建一个弹簧曲线
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({ xOffset: 0, yOffset: yOffset + 100, animation: { duration: 1000, curve: curve } });
        })
        .margin({ top: 110, left: 20 })
      Button('back top')
        .height('5%')
        .onClick(() => { // 点击后回到顶部
          this.scroller.scrollEdge(Edge.Top);
        })
        .margin({ top: 160, left: 20 })
      Button('next page')
        .height('5%')
        .onClick(() => { // 点击后滑到下一页
          this.scroller.scrollPage({ next: true ,animation: true });
        })
        .margin({ top: 210, left: 20 })
      Button('fling -3000')
        .height('5%')
        .onClick(() => { // 点击后触发初始速度为-3000vp/s的惯性滚动
          try {
            this.scroller.fling(-3000);
          } catch (error) {
            let err: BusinessError = error as BusinessError;
            console.error(`Failed to execute fling scroll. Code: ${err.code}, message: ${err.message}`);
          }
        })
        .margin({ top: 260, left: 20 })
      Button('scroll to bottom 700')
        .height('5%')
        .onClick(() => { // 点击后滑到下边缘，速度值是700vp/s
          this.scroller.scrollEdge(Edge.Bottom, { velocity: 700 });
        })
        .margin({ top: 310, left: 20 })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

该示例使用onScrollFrameBegin事件实现了内层List组件和外层Scroll组件的嵌套滚动。

```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct NestedScroll {
  @State listPosition: number = 0; // 0代表滚动到List顶部，1代表中间值，2代表滚动到List底部。
  private arr: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  private scrollerForScroll: Scroller = new Scroller();
  private scrollerForList: Scroller = new Scroller();

  build() {
    Flex() {
      Scroll(this.scrollerForScroll) {
        Column() {
          Text('Scroll Area')
            .width('100%')
            .height('40%')
            .backgroundColor(0X330000FF)
            .fontSize(16)
            .textAlign(TextAlign.Center)
            .onClick(() => {
              this.scrollerForList.scrollToIndex(5, false, ScrollAlign.START, { extraOffset: LengthMetrics.vp(5) });
            })

          List({ space: 20, scroller: this.scrollerForList }) {
            ForEach(this.arr, (item: number) => {
              ListItem() {
                Text('ListItem' + item)
                  .width('100%')
                  .height('100%')
                  .borderRadius(15)
                  .fontSize(16)
                  .textAlign(TextAlign.Center)
                  .backgroundColor(Color.White)
              }.width('100%').height(100)
            }, (item: number) => item.toString())
          }
          .width('100%')
          .height('50%')
          .edgeEffect(EdgeEffect.None)
          .friction(0.6)
          .onReachStart(() => {
            this.listPosition = 0;
          })
          .onReachEnd(() => {
            this.listPosition = 2;
          })
          .onScrollFrameBegin((offset: number) => {
            if ((this.listPosition == 0 && offset <= 0) || (this.listPosition == 2 && offset >= 0)) {
              this.scrollerForScroll.scrollBy(0, offset);
              return { offsetRemain: 0 };
            }
            this.listPosition = 1;
            return { offsetRemain: offset };
          })

          Text('Scroll Area')
            .width('100%')
            .height('40%')
            .backgroundColor(0X330000FF)
            .fontSize(16)
            .textAlign(TextAlign.Center)
        }
      }
      .width('100%').height('100%')
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding(20)
  }
}
```

该示例使用nestedScroll属性实现了内层List组件和外层Scroll组件的嵌套滚动。

```TypeScript
@Entry
@Component
struct StickyNestedScroll {
  @State arr: number[] = [];

  @Styles
  listCard() {
    .backgroundColor(Color.White)
    .height(72)
    .width('100%')
    .borderRadius(12)
  }

  build() {
    Scroll() {
      Column() {
        Text('Scroll Area')
          .width('100%')
          .height('40%')
          .backgroundColor('#0080DC')
          .textAlign(TextAlign.Center)
        Tabs({ barPosition: BarPosition.Start }) {
          TabContent() {
            List({ space: 10 }) {
              ForEach(this.arr, (item: number) => {
                ListItem() {
                  Text('item' + item)
                    .fontSize(16)
                }.listCard()
              }, (item: number) => item.toString())
            }.width('100%')
            .edgeEffect(EdgeEffect.Spring)
            .nestedScroll({
              scrollForward: NestedScrollMode.PARENT_FIRST,
              scrollBackward: NestedScrollMode.SELF_FIRST
            })
          }.tabBar('Tab1')

          TabContent() {
          }.tabBar('Tab2')
        }
        .vertical(false)
        .height('100%')
      }.width('100%')
    }
    .edgeEffect(EdgeEffect.Spring)
    .friction(0.6)
    .backgroundColor('#DCDCDC')
    .scrollBar(BarState.Off)
    .width('100%')
    .height('100%')
  }

  aboutToAppear() {
    for (let i = 0; i < 30; i++) {
      this.arr.push(i);
    }
  }
}
```

该示例使用enableScrollInteraction属性和onScrollFrameBegin事件实现了父组件向子组件传递滚动。

```TypeScript
@Entry
@Component
struct NestedScroll {
  private headerHeight: number = 0;
  private arr: number[] = [];
  private scrollerForParent: Scroller = new Scroller();
  private scrollerForChild: Scroller = new Scroller();

  aboutToAppear(): void {
    for (let i = 0; i < 10; i++) {
      this.arr.push(i);
    }
  }

  build() {
    Scroll(this.scrollerForParent) {
      Column() {
        Text('Scroll Area')
          .width('100%')
          .height('40%')
          .backgroundColor(0X330000FF)
          .fontSize(16)
          .textAlign(TextAlign.Center)
          .onClick(() => {
            this.scrollerForChild.scrollToIndex(5);
          })
          .onSizeChange((oldValue: SizeOptions, newValue: SizeOptions) => {
            this.headerHeight = newValue.height! as number;
          })
        List({ space: 20, scroller: this.scrollerForChild }) {
          ForEach(this.arr, (item: number) => {
            ListItem() {
              Text('ListItem' + item)
                .width('100%')
                .height('100%')
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .backgroundColor(Color.White)
            }.width('100%').height(100)
          }, (item: number) => item.toString())
        }
        .width('100%')
        .height('100%')
        .edgeEffect(EdgeEffect.None)
        .scrollBar(BarState.Off)
        .enableScrollInteraction(false)

        Text('Scroll Area')
          .width('100%')
          .height('40%')
          .backgroundColor(0X330000FF)
          .fontSize(16)
          .textAlign(TextAlign.Center)
      }
    }
    .scrollBar(BarState.Off)
    .edgeEffect(EdgeEffect.Spring)
    .onScrollFrameBegin((offset: number, state: ScrollState) => {
      let retOffset = offset;
      let currOffset = this.scrollerForParent.currentOffset().yOffset;
      let newOffset = currOffset + offset;
      if (offset > 0) {
        if (this.scrollerForChild.isAtEnd()) {
          return { offsetRemain: offset };
        }
        if (newOffset > this.headerHeight) {
          retOffset = this.headerHeight - currOffset;
        }
        this.scrollerForChild.scrollBy(0, offset - retOffset);
      } else {
        if (this.scrollerForChild.currentOffset().yOffset <= 0) {
          return { offsetRemain: offset };
        }
        if (newOffset < this.headerHeight) {
          retOffset = this.headerHeight - currOffset;
        }
        this.scrollerForChild.scrollBy(0, offset - retOffset);
      }
      return { offsetRemain: retOffset };
    })
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
  }
}
```

该示例实现了Scroll组件的限位滚动。

```TypeScript
@Entry
@Component
struct Index {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15];
  build() {
    Scroll(this.scroller) {
      Column() {
        ForEach(this.arr, (item: number) => {
          Text(item.toString())
            .width('90%')
            .height(200)
            .backgroundColor(0xFFFFFF)
            .borderWidth(1)
            .borderColor(Color.Black)
            .borderRadius(15)
            .fontSize(16)
            .textAlign(TextAlign.Center)
        }, (item: number) => item.toString())
      }.width('100%').backgroundColor(0xDCDCDC)
    }
    .backgroundColor(Color.Yellow)
    .height('100%')
    .edgeEffect(EdgeEffect.Spring)
    .scrollSnap({snapAlign:ScrollSnapAlign.START, snapPagination:400, enableSnapToStart:true, enableSnapToEnd:true})
  }
}
```

该示例展示了如何获得List组件的子组件索引。

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ListExample {
  private arr: number[] = [];
  private scroller: ListScroller = new ListScroller();
  @State listSpace: number = 10;
  @State listChildrenSize: ChildrenMainSize = new ChildrenMainSize(120);
  @State listIndex: number = -1;
  @State itemBackgroundColorArr: boolean[] = [];
  aboutToAppear(){
    // 初始化数据源。
    for (let i = 0; i < 10; i++) {
      this.arr.push(i);
      this.itemBackgroundColorArr.push(false);
    }
    try {
      this.listChildrenSize.splice(0, 5, [100, 100, 100, 100, 100]);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`Failed to splice childrenMainSize for first 5 items. Code: ${err.code}, message: ${err.message}`);
    }
  }
  build() {
    Column() {
      List({ space: this.listSpace, initialIndex: 4, scroller: this.scroller }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('item-' + item)
              .height( item < 5 ? 100 : this.listChildrenSize.childDefaultSize)
              .width('90%')
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor( this.itemBackgroundColorArr[item] ? 0x68B4FF: 0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .backgroundColor(Color.Gray)
      .layoutWeight(1)
      .scrollBar(BarState.On)
      .childrenMainSize(this.listChildrenSize)
      .alignListItem(ListItemAlign.Center)
      .gesture(
        PanGesture()
          .onActionUpdate((event: GestureEvent) => {
            if (event.fingerList[0] != undefined && event.fingerList[0].localX != undefined && event.fingerList[0].localY != undefined) {
              try {
                this.listIndex = this.scroller.getItemIndex(event.fingerList[0].localX, event.fingerList[0].localY);
              } catch (error) {
                let err: BusinessError = error as BusinessError;
                console.error(`Failed to get item index from scroller. Code: ${err.code}, message: ${err.message}`);
              }
              if (this.listIndex >= 0 && this.listIndex < this.itemBackgroundColorArr.length) {
                this.itemBackgroundColorArr[this.listIndex] = true;
              }
            }
          })
      )
      .gesture(
        TapGesture({ count: 1 })
          .onAction((event: GestureEvent) => {
            if (event) {
              this.itemBackgroundColorArr = this.arr.map(() => false);
            }
          })
      )

      Text('您当前位置Item索引为：'+ this.listIndex)
        .fontColor(Color.Red)
        .height(50)
    }
  }
}
```

该示例实现了Scroll组件开启边缘渐隐效果并设置边缘渐隐长度。

```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';
@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) {
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
      .fadingEdge(true,{fadingEdgeLength:LengthMetrics.vp(80)})



    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

该示例通过edgeEffect接口，实现了Scroll组件设置单边边缘效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) {
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
      .edgeEffect(EdgeEffect.Spring,{alwaysEnabled:true,effectEdge:EffectEdge.START})
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

该示例通过[enablePaging](arkts-arkui-scroll-attribute.md#enablepaging)接口，实现了Scroll组件滑动翻页效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct EnablePagingExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

  build() {
    Stack({ alignContent: Alignment.Center }) {
      Scroll() {
        Column() {
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('100%')
              .height('100%')
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .backgroundColor(0xFFFFFF)
          }, (item: number) => item.toString())
        }
      }.width('90%').height('90%')
      .enablePaging(true)
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

该示例通过scrollTo接口，实现了Scroll组件设置过界停留效果。

```TypeScript
// xxx.ets
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct StickyNestedScroll {
  scroller: Scroller = new Scroller();

  build() {
    Column() {
      Row() {
        Button('有动画scrollTo').onClick(() => {
          let curve = curves.interpolatingSpring(0.5, 5, 10, 15) // 创建一个弹簧曲线
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({
            xOffset: 0,
            yOffset: yOffset - 100,
            animation: { duration: 1000, curve: curve, canOverScroll: true },
            canOverScroll: true
          })
        }).margin({ top: 10 })
        Button('无动画scrollTo').onClick(() => {
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({
            xOffset: 0,
            yOffset: yOffset - 100,
            animation: false,
            canOverScroll: true
          })
        }).margin({ top: 10, left: 20 })
      }.margin({ bottom: 20 })

      Scroll(this.scroller) {
        Column() {
          Text('Scroll Area')
            .width('100%')
            .height('100%')
            .backgroundColor('#0080DC')
            .textAlign(TextAlign.Center)
        }
        .width('100%')
        .height('100%')
      }
      .scrollable(ScrollDirection.Vertical)
      .edgeEffect(EdgeEffect.Spring) // 设置边缘效果
      .fadingEdge(false) // 关闭边缘渐隐效果
      .scrollBar(BarState.Auto)
      .friction(undefined)
      .backgroundColor('#DCDCDC')
      .width('100%')
      .height('50%')
    }
  }
}
```

从API version 20开始，该示例实现了Scroll组件自由滚动和缩放效果。

```TypeScript
@Entry
@Component
struct ScrollZoomExample {
  @State currScale:number = 1;
  build() {
    Column() {
      Scroll() {
        Image($r('app.media.image1')) // 'app.media.image1'仅作示例，请替换实际图片。
      }
      .height(400)
      .scrollable(ScrollDirection.FREE)
      .minZoomScale(1)
      .maxZoomScale(2)
      .zoomScale(this.currScale!!)
      .enableBouncesZoom(true)
      .onDidZoom((scale: number) => {
        console.info(`onDidZoom:${scale}`);
      })
      .onZoomStart(() => {
        console.info('onZoomStart');
      })
      .onZoomStop(() => {
        console.info('onZoomStop');
      })
    }.width('100%').height('100%')
  }
}
```

从API version 22 开始，该示例实现了获取内容总大小的功能。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ScrollExample1 {
  scroller: Scroller = new Scroller();
  private arr: number[] = []

  aboutToAppear() {
    for (let j = 0; j < 10; j++) {
      this.arr.push(j);
    }
  }

  @State contentWidth: number = -1;
  @State contentHeight: number = -1;

  build() {
    Column() {
      Text('设置scroller控制器和ForEach')
      Row() {
        // 点击按钮来调用contentSize函数获取内容尺寸
        Button('GetContentSize')
          .onClick(() => {
            // Scroller未绑定组件时会抛异常，需要加上try catch保护
            try {
              // 通过调用contentSize函数获取内容尺寸的宽度值
              this.contentWidth = this.scroller.contentSize().width;
              // 通过调用contentSize函数获取内容尺寸的高度值
              this.contentHeight = this.scroller.contentSize().height;
            } catch (error) {
              let err: BusinessError = error as BusinessError;
              console.error(`Failed to get contentSize. Code: ${err.code}, message: ${err.message}`);
            }
          })
        // 将获取到的内容尺寸信息通过文本进行呈现
        Text('Width：' + this.contentWidth + '，Height：' + this.contentHeight)
          .fontColor(Color.Red)
          .height(50)
      }

      Stack({ alignContent: Alignment.TopStart }) {
        Scroll(this.scroller) {
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
        .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
        .scrollBar(BarState.On) // 滚动条常驻显示
        .scrollBarColor(Color.Gray) // 滚动条颜色
        .scrollBarWidth(10) // 滚动条宽度
        .friction(0.6)
        .edgeEffect(EdgeEffect.None)
      }.width('100%').height('100%').backgroundColor(0xDCDCDC)
    }
  }
}
```

从API version 19开始，新增UIScrollEvent接口。

```TypeScript
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.rootNode.commonAttribute.width(100);
    return this.rootNode;
  }

  addCommonEvent(frameNode: FrameNode) {
    // 获取Scroll事件
    let scrollEvent: UIScrollEvent | undefined = typeNode.getEvent(frameNode, 'Scroll');

    // 设置OnWillScroll事件
    scrollEvent?.setOnWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState,
      scrollSource: ScrollSource) => {
      console.info(`onWillScroll xOffset = ${xOffset}, yOffset = ${yOffset}, scrollState = ${scrollState}, scrollSource = ${scrollSource}`);
    });

    // 设置OnDidScroll事件
    scrollEvent?.setOnDidScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
      console.info(`onDidScroll xOffset = ${xOffset}, yOffset = ${yOffset}, scrollState = ${scrollState}`);
    });

    // 设置OnReachStart事件
    scrollEvent?.setOnReachStart(() => {
      console.info('onReachStart');
    });

    // 设置OnReachEnd事件
    scrollEvent?.setOnReachEnd(() => {
      console.info('onReachEnd');
    });

    // 设置OnScrollStart事件
    scrollEvent?.setOnScrollStart(() => {
      console.info('onScrollStart');
    });

    // 设置OnScrollStop事件
    scrollEvent?.setOnScrollStop(() => {
      console.info('onScrollStop');
    });

    // 设置OnScrollFrameBegin事件
    scrollEvent?.setOnScrollFrameBegin((offset: number, state: ScrollState) => {
      console.info(`onScrollFrameBegin offset = ${offset}, state = ${state}`);
      return undefined;
    });
  }
}

@Entry
@Component
struct Index {
  @State index: number = 0;
  private myNodeController: MyNodeController = new MyNodeController();
  @State numbers: string[] = [];

  aboutToAppear() {
    for (let i = 0; i < 30; i++) {
      this.numbers.push(`${i + 1}`);
    }
  }

  build() {
    Column() {
      Button('add CommonEvent to Scroll')
        .onClick(() => {
          this.myNodeController!.addCommonEvent(this.myNodeController!.rootNode!.getParent()!.getPreviousSibling()!)
        })
      Scroll() {
        Column() {
          ForEach(this.numbers, (day: string, index: number) => {
            Column() {
              Text(day)
                .fontSize(16)
                .backgroundColor(0xF9CF93)
                .width('90%')
                .height(80)
                .textAlign(TextAlign.Center)
                .margin({ top: 10 })
            }
            .width('100%')
            .justifyContent(FlexAlign.Center)
            .alignItems(HorizontalAlign.Center)
          }, (day: string, index: number) => index.toString() + day)
        }
      }
      .scrollable(ScrollDirection.Vertical)
      .edgeEffect(EdgeEffect.Spring)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)
      NodeContainer(this.myNodeController)
    }
  }
}
```
