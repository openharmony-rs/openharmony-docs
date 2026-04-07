# Grid (系统接口)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zcdqs-->
<!--Designer: @zcdqs-->
<!--Tester: @huchuyun-->
<!--Adviser: @Brilliantry_Rui-->

网格容器，由“行”和“列”分割的单元格所组成，通过指定“项目”所在的单元格做出各种各样的布局。

> **说明：**
>
> - 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[Grid](ts-container-grid.md)。


## GridLayoutOptions<sup>10+</sup>对象说明

Grid布局选项。

为提高Grid在包含大小不规则节点场景布局性能和准确性，可以使用onGetStartIndexByOffset和onGetStartIndexByIndex两个回调类型参数，两个回调必须同时设置才能生效。该场景下，建议设置[onScrollBarUpdate](ts-container-grid.md#onscrollbarupdate10)来精准定位滚动条的位置。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称    | 类型      | 只读   | 可选 | 说明                    |
| ----- | ------- | ---- | --  | --------------------- |
| onGetStartIndexByOffset<sup>23+</sup> | [OnGetStartIndexByOffsetCallback](#ongetstartindexbyoffsetcallback23类型) | 否 | 是 | 根据Grid滚动的总偏移量，计算Grid当前页面起始行位置，用于快速滑动或反向滑动场景。<br/>**系统接口：** 此接口为系统接口。<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |
| onGetStartIndexByIndex<sup>23+</sup> | [OnGetStartIndexByIndexCallback](#ongetstartindexbyindexcallback23类型) | 否 | 是 | 根据指定的目标索引，计算Grid滚动到该位置时页面内的起始行，用于支持[scrollToIndex](ts-container-scroll.md#scrolltoindex)等操作。<br/>**系统接口：** 此接口为系统接口。<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |

## StartLineInfo<sup>23+</sup>对象说明  

用于记录Grid页面内起始行的位置信息。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
|------|------|------|------|------|
| startIndex | number | 否 | 否 | 目标索引或目标偏移量所在行的起始索引。 |
| startLine | number | 否 | 否 | startIndex对应的GridItem所在的起始行，一般为Grid视窗内的起始行，对于跨多行的GridItem需要找到该节点的起始行，可能在视窗外。 |
| startOffset | number | 否 | 否 | startIndex对应的GridItem的顶部与Grid顶部之间的偏移量。<br/>单位：vp |
| totalOffset | number | 否 | 否 | 总滚动偏移量，即Grid中第一个GridItem的顶部与Grid顶部之间的偏移量。<br/>单位：vp  |

## OnGetStartIndexByOffsetCallback<sup>23+</sup>类型

type OnGetStartIndexByOffsetCallback = (totalOffset: number) => StartLineInfo

根据Grid的总偏移量，计算当前页面起始行的位置，用于快速滑动或反向滑动场景。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| totalOffset | number | 是 | 总滚动偏移量，即Grid当中第一个GridItem的顶部与Grid顶部之间的偏移量。<br/>单位：vp  |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [StartLineInfo](#startlineinfo23对象说明) | 用于记录Grid页面内起始行的位置信息。 |

## OnGetStartIndexByIndexCallback<sup>23+</sup>类型

type OnGetStartIndexByIndexCallback = (targetIndex: number) => StartLineInfo

根据指定的目标索引，计算Grid滚动到该位置时页面内对应的起始行，用于支持[scrollToIndex](ts-container-scroll.md#scrolltoindex)等操作。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| targetIndex | number | 是 | 要滚动到的目标GridItem的索引。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [StartLineInfo](#startlineinfo23对象说明) | 用于记录Grid页面内起始行的位置信息。 |

## 示例

### 示例1(基本用法)
本示例介绍如何使用[GridLayoutOptions](#gridlayoutoptions10对象说明)中的onGetStartIndexByOffset和onGetStartIndexByIndex快速定位滚动位置。

从API version 23开始，GridLayoutOptions新增支持onGetStartIndexByOffset和onGetStartIndexByIndex。
```ts
@Entry
@Component
struct Index {
  numbers: GridDataSource = new GridDataSource([]);
  scroller: Scroller = new Scroller();
  crossCount: number = 3;
  itemHeight: number = 100;
  childrenCount: number = 500;
  @State options: GridLayoutOptions = {
    regularSize: [1, 1],
    irregularIndexes: [],
    onGetIrregularSizeByIndex: (index: number) => {
      return [2, 2]
    },
    // 设置两个回调函数来准确计算Grid的滚动位置
    onGetStartIndexByOffset: (offset: number) => {
      if (offset < 0) {
        return {
          startIndex: 0,
          startLine: 0,
          startOffset: -offset,
          totalOffset: offset
        }
      }
      let line = Math.floor(offset / (this.itemHeight * 2))
      let startOffset = -offset % (this.itemHeight * 2)
      return {
        startIndex: line * this.crossCount,
        startLine: line * 2,
        startOffset: startOffset,
        totalOffset: offset
      }
    },
    onGetStartIndexByIndex: (index: number) => {
      let line = Math.floor(index / this.crossCount)
      let offset = index % 3 == 2 ? -this.itemHeight : 0
      return {
        startIndex: line * 3,
        startLine: line * 2,
        startOffset: offset,
        totalOffset: line * this.itemHeight * 2 - offset
      }
    }
  }

  // 在aboutToAppear中初始化数据源和不规则节点索引
  aboutToAppear() {
    let list: string[] = [];
    let irregularList: number[] = []
    for (let i = 0; i <= this.childrenCount; i++) {
      list.push(i.toString())
      if (i % 3 == 0) {
        irregularList.push(i)
      }
    }
    this.numbers = new GridDataSource(list);
    this.options.irregularIndexes = irregularList
  }

  build() {
    Column({ space: 5 }) {
      Text('Custom').fontColor(0xCCCCCC).fontSize(9).width('90%')
      Grid(this.scroller, this.options) {
        LazyForEach(this.numbers, (day: string, index: number) => {
          if (index % 3 == 0) {
            GridItem() {
              Text(day)
                .fontSize(16)
                .backgroundColor(0xF9CF93)
                .width(200)
                .height(190)
                .textAlign(TextAlign.Center)
            }
          } else {
            GridItem() {
              Text(day)
                .fontSize(16)
                .backgroundColor(0xF9CF93)
                .width(100)
                .height(90)
                .textAlign(TextAlign.Center)
            }
          }
        }, (index: number) => index.toString())
      }
      .columnsTemplate('1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .edgeEffect(EdgeEffect.Spring)
      .width(320)
      .backgroundColor(0xFAEEE0)
      .height(300)
      .onScrollBarUpdate((index: number, offset: number) => {
        console.info('XXX' + 'Grid onScrollBarUpdate,index : ' + index.toString() + ',offset' + offset.toString());
        return {
          totalOffset: (index / this.crossCount) * (this.itemHeight) * 2 - offset,
          totalLength: this.itemHeight * 2 * (this.childrenCount + 1) / this.crossCount
        };
      }) // 只适用于当前示例代码数据源，如果数据源有变化，则需要修改该部分代码
    }.width('100%').margin({ top: 5 })
  }
}


// GridDataSource.ets
export class GridDataSource implements IDataSource {
  private list: string[] = [];
  private listeners: DataChangeListener[] = [];

  constructor(list: string[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): string {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
    if (this.listeners.indexOf(listener) < 0) {
      this.listeners.push(listener);
    }
  }

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
}
```
![gridCustomScroll](figures/gridCustomScroll.gif)