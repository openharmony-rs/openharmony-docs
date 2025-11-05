# UI组件适配（滚动与滑动）

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## List

### onScroll

ArkTS-Dyn接口声明：[onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void)](../reference/apis-arkui/arkui-ts/ts-container-list.md#onscrolldeprecated)

替代的ArkTS-Sta接口声明：[onDidScroll(handler: OnScrollCallback): T](../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#ondidscroll12)



ArkTS-Dyn示例：
<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct ListComponent {
  build() {
    Column() {
      List() {
      }
      .onScroll((scrollOffset: number, scrollState: ScrollState) => {
        // some logic
      })
    }
  }
}
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct ListComponent {
  build() {
    Column() {
      List() {
      }
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        // some logic
      })
    }
  }
}
```

### onItemDelete

ArkTS-Dyn接口声明：[onItemDelete(event: (index: number) => boolean)](../reference/apis-arkui/arkui-ts/ts-container-list.md#onitemdeletedeprecated)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。

### editMode

ArkTS-Dyn接口声明：[editMode(value: boolean)](../reference/apis-arkui/arkui-ts/ts-container-list.md#editmodedeprecated)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。

## ListItem

### ListItem

ArkTS-Dyn接口声明：[ListItem(value?: string)](../reference/apis-arkui/arkui-ts/ts-container-listitem.md#listitemdeprecated)

替代的ArkTS-Sta接口声明：[ListItem(value?: ListItemOptions)](../reference/apis-arkui/arkui-ts/ts-container-listitem.md#listitem10)



ArkTS-Dyn示例：
<!--code_no_check-->
```ts
// xxx.ets
export class ListDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}

@Entry
@Component
struct ListItemExample {
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);

  build() {
    Column() {
      List({ space: 20, initialIndex: 0 }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem("") {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: string) => item)
      }.width('90%')
      .scrollBar(BarState.Off)
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
export class ListDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}

@Entry
@Component
struct ListItemExample {
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);

  build() {
    Column() {
      List({ space: 20, initialIndex: 0 }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem({style: ListItemStyle.NONE}) {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: string) => item)
      }.width('90%')
      .scrollBar(BarState.Off)
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

### sticky

ArkTS-Dyn接口声明：[sticky(value: Sticky)](../reference/apis-arkui/arkui-ts/ts-container-listitem.md#stickydeprecated)

替代的ArkTS-Sta接口声明：[sticky(value: StickyStyle)](../reference/apis-arkui/arkui-ts/ts-container-list.md#sticky9)



ArkTS-Dyn示例：
<!--code_no_check-->
```ts
// xxx.ets
export class ListDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}

@Entry
@Component
struct ListItemExample {
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
          .sticky(Sticky.None)
        }, (item: string) => item)
      }.width('90%')
      .scrollBar(BarState.Off)
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
export class ListDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}

@Entry
@Component
struct ListItemExample {
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
        }, (item: string) => item)
      }.width('90%')
      .sticky(StickyStyle.None)
      .scrollBar(BarState.Off)
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

### editable

ArkTS-Dyn接口声明：[editable(value: boolean | EditMode)](../reference/apis-arkui/arkui-ts/ts-container-listitem.md#editabledeprecated)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。


### Sticky

ArkTS-Dyn接口声明：[Sticky](../reference/apis-arkui/arkui-ts/ts-container-listitem.md#stickydeprecated枚举说明)

替代的ArkTS-Sta接口声明：[StickyStyle](../reference/apis-arkui/arkui-ts/ts-container-list.md#stickystyle9枚举说明)



ArkTS-Dyn示例：
<!--code_no_check-->
```ts
// xxx.ets
const stickTypeNone : Sticky = Sticky.None;
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
const stickTypeNone : StickyStyle = StickyStyle.None;
```

### EditMode

ArkTS-Dyn接口声明：[EditMode](../reference/apis-arkui/arkui-ts/ts-container-listitem.md#editmodedeprecated枚举说明)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。
## Grid

### onScroll

ArkTS-Dyn接口声明：[onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void)](../reference/apis-arkui/arkui-ts/ts-container-grid.md#onscrolldeprecated)

替代的ArkTS-Sta接口声明：[onDidScroll(handler: OnScrollCallback): T](../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#ondidscroll12)



ArkTS-Dyn示例：
<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct GridComponent {
  build() {
    Column() {
      Grid() {
      }
      .onScroll((scrollOffset: number, scrollState: ScrollState) => {
        // some logic
      })
    }
  }
}
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct GridComponent {
  build() {
    Column() {
      Grid() {
      }
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        // some logic
      })
    }
  }
}
```

## GridItem

### forceRebuild

ArkTS-Dyn接口声明：[forceRebuild(value: boolean)](../reference/apis-arkui/arkui-ts/ts-container-griditem.md#forcerebuilddeprecated)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。

## Scroll

### scrollPage

ArkTS-Dyn接口声明：[scrollPage(value: { next: boolean, direction?: Axis })](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#scrollpagedeprecated)

替代的ArkTS-Sta接口声明：[scrollPage(value: ScrollPageOptions)](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#scrollpage9)



ArkTS-Dyn示例：
<!--code_no_check-->
```ts
// xxx.ets
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

      Button('next page')
        .height('5%')
        .onClick(() => { // 点击后滑到下一页
          this.scroller.scrollPage({ next: true ,direction: Axis.Vertical });
        })
        .margin({ top: 210, left: 20 })
    
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
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

      Button('next page')
        .height('5%')
        .onClick(() => { // 点击后滑到下一页
          this.scroller.scrollPage({ next: true ,animation: true });
        })
        .margin({ top: 210, left: 20 })
    
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### ScrollDirection.Free

ArkTS-Dyn接口声明：[ScrollDirection.Free](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#scrolldirection枚举说明)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。

### onScrollEnd

ArkTS-Dyn接口声明：[onScrollEnd(event: () => void)](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#onscrollenddeprecated)

替代的ArkTS-Sta接口声明：[onScrollStop(event: VoidCallback)](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#onscrollstop9)



ArkTS-Dyn示例：
<!--code_no_check-->
```ts
// xxx.ets
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
      .onScrollEnd(() => {
        console.info('Scroll end');
      })
    
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
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
      .onScrollStop(()=>{
        console.info('Scroll stop');
      })
      
    
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### onScroll

ArkTS-Dyn接口声明：[onScroll(event: (xOffset: number, yOffset: number) => void)](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#onscrolldeprecated)

替代的ArkTS-Sta接口声明：[onWillScroll(handler: ScrollOnWillScrollCallback)](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#onwillscroll12)



ArkTS-Dyn示例：
<!--code_no_check-->
```ts
// xxx.ets
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
      .onScroll((xOffset: number, yOffset: number) => {
        console.info('onScroll');
      })
    
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
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
      .onWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => {
        console.info('onWillScroll');
      })
      
    
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

## Swiper

### indicatorStyle
ArkTS-Dyn接口声明：[indicatorStyle(value?: IndicatorStyle): SwiperAttribute](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated)

替代的ArkTS-Sta接口声明：[indicator(value: DotIndicator | DigitIndicator | boolean): SwiperAttribute](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicator)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle()
```

ArkTS-Sta示例：

```ts
 Swiper().indicator(true)
```

### IndicatorStyle
ArkTS-Dyn接口声明：[declare interface IndicatorStyle](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[declare class DotIndicator extends Indicator<DotIndicator>](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
let a: IndicatorStyle = {color: "#FFFF00FF"}
```

ArkTS-Sta示例：

```ts
let a: DotIndicator = new DotIndicator().color("#FFFF00FF")
```


### color
ArkTS-Dyn接口声明：[IndicatorStyle.color?: ResourceColor](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[color(value: ResourceColor): DotIndicator](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({color: "#FFFF00FF"})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().color("#FFFF00FF"))
```


### right
ArkTS-Dyn接口声明：[IndicatorStyle.right?: Length](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[right(value: Length): T](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({right: 0})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().right(0))
```


### left
ArkTS-Dyn接口声明：[IndicatorStyle.left?: Length](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[left(value: Length): T](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({left: 0})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().left(0))
```


### top
ArkTS-Dyn接口声明：[IndicatorStyle.top?: Length](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[top(value: Length): T](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({top: 0})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().top(0))
```


### bottom
ArkTS-Dyn接口声明：[IndicatorStyle.bottom?: Length](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[bottom(value: Length): T](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({bottom: 0})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().bottom(0))
```


### selectedColor
ArkTS-Dyn接口声明：[IndicatorStyle.selectedColor?: ResourceColor](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[selectedColor(value: ResourceColor): DotIndicator](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({selectedColor: "#FFFF00FF"})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().selectedColor("#FFFF00FF"))
```


### mask
ArkTS-Dyn接口声明：[IndicatorStyle.mask?: boolean](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[mask(value: boolean): DotIndicator](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({mask: true})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().mask(true))
```


### size
ArkTS-Dyn接口声明：[IndicatorStyle.size?: Length](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[itemWidth(value: Length): DotIndicator](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({size: 100})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().itemWidth(100).itemHeight(100).selectedItemWidth(100).selectedItemHeight(100))
```


### Stretch
ArkTS-Dyn接口声明：[SwiperDisplayMode.Stretch](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#swiperdisplaymode枚举说明)

替代的ArkTS-Sta接口声明：[SwiperDisplayMode.STRETCH](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#swiperdisplaymode枚举说明)



ArkTS-Dyn示例：

```ts
Swiper().displayMode(SwiperDisplayMode.Stretch)
```

ArkTS-Sta示例：

```ts
Swiper().displayMode(SwiperDisplayMode.STRETCH)
```


### AutoLinear
ArkTS-Dyn接口声明：[SwiperDisplayMode.AutoLinear](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#swiperdisplaymode枚举说明)

替代的ArkTS-Sta接口声明：[scrollTo(options: ScrollOptions)](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#scrollto)


适配方案详见[AUTO_LINEAR](./arkts-sta-deprecated-scroll-and-swipe.md#auto_linear)的示例。


### AUTO_LINEAR
ArkTS-Dyn接口声明：[SwiperDisplayMode.AUTO_LINEAR](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#swiperdisplaymode枚举说明)

替代的ArkTS-Sta接口声明：[scrollTo(options: ScrollOptions)](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#scrollto)

ArkTS-Dyn示例：

```ts
@Entry
@Component
struct SwiperExample {
  private data: number[] = [1, 2, 3, 4, 5, 6, 7, 8];
  private swiperController: SwiperController = new SwiperController();

  build() {
    Column() {
      Swiper(this.swiperController) {
        ForEach(this.data, (item: number) => {
          Column() {
            Text(item.toString())
              .width('100%')
              .height('100%')
              .textAlign(TextAlign.Center)
          }
          .width(90)
          .height(160)
          .backgroundColor(0xAFEEEE)
        })
      }
      .displayMode(SwiperDisplayMode.AUTO_LINEAR)
      //.displayMode(SwiperDisplayMode.AutoLinear)
      .itemSpace(20)
      .curve(Curve.Linear)
      .duration(1000)
      .loop(false)
      .indicator(false)
      .onChange((index: number) => {
        console.info(index.toString())
      })
      Row({ space: 12 }) {
        Button('showNext')
          .onClick(() => {
            this.swiperController.showNext();
          })
        Button('showPrevious')
          .onClick(() => {
            this.swiperController.showPrevious();
          })
      }.margin(5)
    }.width('100%')
  }
}
```

ArkTS-Sta示例：

```ts
@Entry
@Component
struct ScrollExample {
  private data: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8];
  private scroller: Scroller = new Scroller();

  build() {
    Column() {
      Scroll(this.scroller) {
        Row() {
          ForEach(this.data, (item: number) => {
            Column() {
              Text(item.toString())
                .width('100%')
                .height('100%')
                .textAlign(TextAlign.Center)
            }
            .width(90)
            .height(160)
            .backgroundColor(0xAFEEEE)
            .margin({ right: item === this.data[this.data.length - 1] ? 0 : 20 })
          })
        }.height(160)
      }
      .scrollable(ScrollDirection.Horizontal)
      .scrollBar(BarState.Off)
      .edgeEffect(EdgeEffect.Spring)
      Row({ space: 12 }) {
        Button('showNext')
          .onClick(() => {
            const xOffset: number = this.scroller.currentOffset().xOffset;
            this.scroller.scrollTo({ xOffset: xOffset + 90 + 20, yOffset: 0, animation: { duration: 1000, curve: Curve.Linear } });
          })
        Button('showPrevious')
          .onClick(() => {
            const xOffset: number = this.scroller.currentOffset().xOffset;
            this.scroller.scrollTo({ xOffset: xOffset - 90 - 20, yOffset: 0, animation: { duration: 1000, curve: Curve.Linear } });
          })
      }.margin(5)
    }.width('100%')
  }
}
```

## Refresh

### RefreshOptions-offset

ArkTS-Dyn接口声明：[RefreshOptions-offset](../reference/apis-arkui/arkui-ts/ts-container-refresh.md#refreshoptions对象说明)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。

### RefreshOptions-friction

ArkTS-Dyn接口声明：[RefreshOptions-friction](../reference/apis-arkui/arkui-ts/ts-container-refresh.md#refreshoptions对象说明)

替代的ArkTS-Sta接口声明：[pullDownRatio(ratio: Optional<number>)](../reference/apis-arkui/arkui-ts/ts-container-refresh.md#pulldownratio12)



ArkTS-Dyn示例：
<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct RefreshComponent {
  build() {
    Column() {
      Refresh({ refreshing: true ,friction: 62 }) {
      }
    }
  }
}
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct RefreshComponent {
  build() {
    Column() {
      Refresh({ refreshing: true }) {
      }
      .pullDownRatio(62)
    }
  }
}
```

## 滚动组件通用接口

### onScroll

ArkTS-Dyn接口声明：[onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T](../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onscrolldeprecated)

替代的ArkTS-Sta接口声明：

Scroll组件的onScroll事件在布局之前触发，建议使用[onWillScroll](../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onwillscroll12)。

List、Grid和WaterFlow组件的onScroll事件在布局之后触发，建议使用[onDidScroll](../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#ondidscroll12)。



ArkTS-Dyn示例：
<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct ScrollComponent {
  build() {
    Column() {
      Scroll() {
      }
      .onScroll((scrollOffset: number, scrollState: ScrollState) => {
        // some logic
      })
    }
  }
}

@Component
struct ListComponent {
  build() {
    Column() {
      List() {
      }
      .onScroll((scrollOffset: number, scrollState: ScrollState) => {
        // some logic
      })
    }
  }
}

@Component
struct GridComponent {
  build() {
    Column() {
      Grid() {
      }
      .onScroll((scrollOffset: number, scrollState: ScrollState) => {
        // some logic
      })
    }
  }
}

@Component
struct WaterFlowComponent {
  build() {
    Column() {
      WaterFlow() {
      }
      .onScroll((scrollOffset: number, scrollState: ScrollState) => {
        // some logic
      })
    }
  }
}

```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
// xxx.ets
@Entry
@Component
struct ScrollComponent {
  build() {
    Column() {
      Scroll() {
      }
      .onWillScroll((scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => {
        // some logic
      })
    }
  }
}

@Component
struct ListComponent {
  build() {
    Column() {
      List() {
      }
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        // some logic
      })
    }
  }
}

@Component
struct GridComponent {
  build() {
    Column() {
      Grid() {
      }
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        // some logic
      })
    }
  }
}

@Component
struct WaterFlowComponent {
  build() {
    Column() {
      WaterFlow() {
      }
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        // some logic
      })
    }
  }
}
```

## 枚举说明

### Edge.Center

ArkTS-Dyn接口声明：[Edge.Center](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#edge)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。

### Edge.Middle

ArkTS-Dyn接口声明：[Edge.Middle](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#edge)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。

### Edge.Baseline

ArkTS-Dyn接口声明：[Edge.Baseline](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#edge)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。