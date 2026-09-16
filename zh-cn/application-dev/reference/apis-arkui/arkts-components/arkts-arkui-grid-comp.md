# Grid

网格容器，由“行”和“列”分割的单元格所组成，通过指定“项目”所在的单元格做出各种各样的布局。

> **说明：** > > 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。

## 子组件

仅支持GridItem子组件和自定义组件。自定义组件在Grid下使用时，建议使用GridItem作为自定义组件的顶层组件，不建议给自定义组件设置属性和事件方法。

支持通过渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和[Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)）动态生成子组件，更推荐使用LazyForEach或Repeat以优化性能。

> **说明：** 
> 
> Grid子组件的索引值计算规则：
> 
> 按子组件的顺序依次递增。
> 
> if/else语句中，只有条件成立分支内的子组件会参与索引值计算，条件不成立分支内的子组件不计算索引值。
> 
> ForEach/LazyForEach和Repeat语句中，会计算展开所有子组件索引值。
> 
> [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、
> [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、
> [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和
> [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)发生变化以后，会更新子组件索引值。
> 
> Grid子组件的visibility属性设置为Hidden或None时依然会计算索引值。
> 
> Grid子组件的visibility属性设置为None时不显示，但依然会占用子组件对应的网格。
> 
> Grid子组件设置position属性，会占用子组件对应的网格，子组件将显示在相对Grid左上角偏移position的位置。该子组件不会随其对应网格滚动，在对应网格滑出Grid显示范围外后不显示。
> 
> 当Grid子组件之间留有空隙时，会根据当前的展示区域尽可能填补空隙，因此GridItem可能会随着网格滚动而改变相对位置。
> 
> 从API version 21开始，Grid单个子组件的宽高最大为16777216px；API version 20及之前，Grid单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。

## Grid

```TypeScript
Grid(scroller?: Scroller, layoutOptions?: GridLayoutOptions)
```

创建网格容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | [Scroller](arkts-arkui-scroller-c.md) | 否 | 可滚动组件的控制器。用于与可滚动组件进行绑定。不设置时不绑定外部控制器，组件自行管理滚动行为。<br>**说明：** <br>不允许和其他滚动类组件，如：ArcList、List、Grid、Scroll和WaterFlow绑定同一个滚动控制对象。 |
| layoutOptions | [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) | 否 | Grid布局选项，用于配置GridItem跨行跨列等布局信息。不传入时，Grid按照rowsTemplate、columnsTemplate等常规属性以及GridItem自身属性进行布局，不启用GridLayoutOptions提供的布局选项。<br> |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ComputedBarAttribute](arkts-arkui-computedbarattribute-i.md) | 滚动条位置和长度对象。 |
| [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) | Grid布局选项。其中，irregularIndexes和onGetIrregularSizeByIndex可对仅设置rowsTemplate或columnsTemplate的Grid使用，可以指定一个index数组，并为其中的index对应的GridItem设置其占据的行数与列数，使用方法参见示例3；onGetRectByIndex可对同时设置rowsTemplate和columnsTemplate的Grid使用，为指定的index对应的GridItem设置位置和大小，使用方法参见示例1。 |
| [StartLineInfo](arkts-arkui-startlineinfo-i-sys.md) | 用于记录Grid页面内起始行的位置信息。 |
| [UIGridEvent](arkts-arkui-uigridevent-i.md) | frameNode中[getEvent('Grid')](../arkts-apis/arkts-arkui-typenode-getevent-f.md)方法的返回值，可用于给Grid节点设置滚动事件。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnGetStartIndexByIndexCallback](arkts-arkui-ongetstartindexbyindexcallback-t-sys.md) | 根据指定的目标索引，计算Grid滚动到该位置时页面内对应的起始行，用于支持[scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex)等操作。此回调需与onGetStartIndexByOffset同时设置才能生效。 |
| [OnGetStartIndexByOffsetCallback](arkts-arkui-ongetstartindexbyoffsetcallback-t-sys.md) | 根据Grid的总偏移量，计算当前页面起始行的位置，用于快速滑动或反向滑动场景。此回调需与onGetStartIndexByIndex同时设置才能生效。 |
| [OnGridScrollIndexCallback](arkts-arkui-ongridscrollindexcallback-t.md) | Grid组件可见区域item变化事件的回调类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GridDirection](arkts-arkui-griddirection-e.md) | 主轴布局方向枚举。 |
| [GridItemAlignment](arkts-arkui-griditemalignment-e.md) | GridItem的对齐方式枚举。 |

## 示例

```TypeScript
### 示例1（固定行列Grid）

可以使用[GridLayoutOptions](#gridlayoutoptions10对象说明)中的onGetRectByIndex指定GridItem的位置和大小。


```

```TypeScript
### 示例2（可滚动Grid和滚动事件）

可滚动Grid，包括所有滚动属性和事件。

GridDataSource实现了LazyForEach数据源接口[IDataSource](ts-rendering-control-lazyforeach.md#idatasource)，用于通过LazyForEach给Grid提供子组件。
```

```TypeScript

```

```TypeScript
### 示例3（可滚动Grid设置跨行跨列节点）

[GridLayoutOptions](#gridlayoutoptions10对象说明)的使用：irregularIndexes与onGetIrregularSizeByIndex。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例4（Grid嵌套滚动）

[nestedScroll](#nestedscroll10)和[onScrollFrameBegin](#onscrollframebegin10)的使用。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例5（Grid拖拽场景）

通过属性[editMode](#editmode8)设置Grid是否进入编辑模式，进入编辑模式可以拖拽Grid组件内部GridItem。

在[onItemDragStart](#onitemdragstart8)回调中设置拖拽过程中显示的图片。

在[onItemDrop](#onitemdrop8)中获取拖拽起始位置，和拖拽插入位置，并在[onItemDrop](#onitemdrop8)中完成交换数组位置逻辑。

设置属性支持动画。

> 说明：
> 
> 预览器窗口不支持显示拖拽跟手。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。

示例图：

网格子组件开始拖拽：



网格子组件拖拽过程中：



网格子组件1与子组件6拖拽交换位置后：



拖拽动画：


```

```TypeScript
### 示例6（自适应Grid）

[layoutDirection](#layoutdirection8)、[maxCount](#maxcount8)、[minCount](#mincount8)、[cellLength](arkts-arkui-grid-comp-attribute.md#celllength)的使用。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例7（双指缩放修改Grid列数）

双指缩放修改Grid列数。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例8（设置自适应列数）

属性[columnsTemplate](#columnstemplate)中auto-fill、auto-fit和auto-stretch的使用示例。


```

```TypeScript
### 示例9（以当前行最高的GridItem的高度为其他GridItem的高度）

下面的Grid中包含两列，每列中的GridItem包括高度确定的两个Column和一个高度不确定的Text共三个子组件。

在默认情况下，左右两个GridItem的高度可能是不同的；在设置了Grid的[alignItems](#alignitems12)属性为GridItemAlignment.STRETCH后，一行左右两个GridItem中原本高度较小的GridItem会以另一个高度较大的GridItem的高度作为自己的高度。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例10（设置边缘渐隐）

通过[fadingEdge](ts-container-scrollable-common.md#fadingedge14)属性来设置边缘渐隐效果。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例11（单边边缘效果）

该示例通过[edgeEffect](#edgeeffect10)接口，实现了Grid组件设置单边边缘效果。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例12（方向键走焦换行模式）

从API version 20开始，该示例通过[focusWrapMode](#focuswrapmode20)接口，实现了Grid组件方向键走焦换行效果。


```

```TypeScript
### 示例13（设置滚动事件）

该示例通过FrameNode中的getEvent('Grid')获取[UIGridEvent](arkts-arkui-uigridevent-i.md)，并为Grid设置滚动事件回调，用于事件监听方因无法直接修改页面代码而无法使用声明式接口设置回调的场景。

从API version 19开始，新增UIGridEvent接口。
```

```TypeScript
### 示例14（滚动到指定位置）

该示例通过[scrollToIndex](ts-container-scroll.md#scrolltoindex)接口，实现了Grid组件滚动到指定位置。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例15（实现Grid滑动选择）

该示例通过[PanGesture](./ts-basic-gestures-pangesture.md#pangesture-1)接口，实现了Grid组件一边滑动一边选择的效果。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例16（实现GridItem自定义拖拽）

该示例通过[gesture](./ts-gesture-settings.md#gesture)接口，实现了GridItem组件自定义拖拽效果。


```

```TypeScript
### 示例17（通过拖拽事件实现GridItem拖拽）

该示例通过[拖拽事件](./ts-universal-events-drag-drop.md)实现拖拽GridItem到Grid边缘时Grid自动滚动的功能。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例18（Grid组件基于断点配置列数）

从API version 22开始，该示例展示了Grid组件支持基于断点配置列数效果。

Grid宽度属于sm及更小的断点区间时显示2列。



Grid宽度属于md断点区间时显示3列。



Grid宽度属于lg及更大的断点区间时显示5列。


```

```TypeScript
### 示例19（获取内容总大小）

从API version 22 开始，该示例实现了获取内容总大小的功能。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例20（设置多选聚拢动画）

该示例通过打开Grid多选聚拢动画开关，实现了在GridItem上长按弹出菜单时，通过[bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu8)聚拢显示范围内被选中的GridItem的效果。

从API version 23开始，Grid组件新增[editModeOptions](#editmodeoptions23)接口，可以设置多选聚拢动画开关。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例21（设置滑动多选）

该示例通过使用双向绑定和事件监听在Grid上双指滑动进入多选模式的通知，实现了在Grid上边滑动边选择的效果。

从API版本26.0.0开始，Grid组件新增[enableEditMode](#enableeditmode)接口和[onEditModeChange](#oneditmodechange)事件。

GridDataSource说明及完整代码参考[示例2（可滚动Grid和滚动事件）](#示例2可滚动grid和滚动事件)。


```

```TypeScript
### 示例22（使用OnMove进行拖拽）

从API版本26.0.0开始，该示例展示了Grid使用LazyForEach的[onMove](./ts-universal-attributes-drag-sorting.md#onmove)接口进行拖拽排序的效果，支持拖动到Grid边缘时触发Grid的自动滚动，同时Grid存在跨行跨列节点。
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
