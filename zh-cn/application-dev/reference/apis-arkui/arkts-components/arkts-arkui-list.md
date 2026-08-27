# List

List是ArkUI中的列表容器组件，用于呈现连续、多行或多列的同类数据，例如图片和文本，支持垂直或水平滚动。配合LazyForEach或Repeat可实现懒加载，提升长列表场景下的启动速度并减少内存消耗；支持预加载以减少滚动丢帧、提 升流畅性；支持单列/多列布局、分组列表、吸顶吸底等能力，适用于消息列表、商品列表、设置页面等场景。
List的懒加载是指组件按需加载显示区域内的子组件。相比全量加载，使用懒加载可以提升应用启动速度，减少内存消耗。List和 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)、 [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)结合，懒加载能力存在差异：
- 当List和ForEach结合，会一次性创建所有的子组件，在需要的时候布局和渲染屏幕范围内的节点。当用户滑动时，划出屏幕范围的节点不会下树销毁，划入屏幕范围的节点会布局和渲染。
- 当List和LazyForEach结合，会一次性创建、布局、渲染屏幕范围的节点。当用户滑动时，划出屏幕范围的节点会下树销毁，划入屏幕范围的节点会创建、布局、渲染。
- 当List和带[virtualScroll](../arkts-apis/arkts-arkui-repeatattribute-c.md#virtualscroll)的Repeat结合，它的懒加载行为和LazyForEach一致。当List和不带virtualScroll的
Repeat结合，它的懒加载行为和ForEach一致。
如果可滚动组件嵌套List组件，并且滚动方向相同，List组件又没有设置主轴尺寸时，List组件会全量加载子组件，导致懒加载失效。该场景推荐使用List嵌套 ListItemGroup组件以优化性能。
List的预加载是指除了加载显示区域内可见的子组件外，还支持在空闲时隙提前加载部分显示区域外不可见的子组件。使用预加载可以减少滚动丢帧，提升流畅性。预加载需要结合懒加载才会生效。List支持通过 [cachedCount](arkts-arkui-list-attribute.md#cachedcount)设置预加载的数量。默认会预加载显示区域上下各一屏子组件（最大预加载16行子组件）。List和 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)、 [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)结合，预加载能力存在差异：
- 当List和ForEach结合，如果设置了cachedCount，除了会布局显示区域内子组件外，还会在空闲时隙预布局显示区域外cachedCount范围内的子组件。
- 当List和LazyForEach结合，如果设置了cachedCount，除了会创建和布局显示区域内子组件外，还会在空闲时隙预创建和预布局显示区域外cachedCount范围内的子组件。
- 当List和带[virtualScroll](../arkts-apis/arkts-arkui-repeatattribute-c.md#virtualscroll)的Repeat结合，它的预加载行为和LazyForEach一致。当List和不带virtualScroll的
Repeat结合，它的预加载行为和ForEach一致。
> **说明：** > > 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。

## 子组件

仅支持ListItem、ListItemGroup子组件和自定义组件。自定义组件在List下使用时，请使用ListItem或 ListItemGroup作为自定义组件的顶层组件，请勿直接给自定义组件设置属性和事件方法，因为List通过ListItem或ListItemGroup管理子组件的布局和事件处理，直接设置可能导致部分功能无法正常生效。支持通过渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和 [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)）动态生成子组件，更推荐使用LazyForEach或Repeat以优化性能。

> **说明：**
> 
> 在处理大量子组件时遇到卡顿问题，请采用懒加载、缓存列表项、动态预加载、组件复用和布局优化等方法进行优化。
> 
> 从API version 21开始，List单个子组件的宽高最大为16777216px；API version 20及之前，List单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异常。
> 
> List的子组件的索引值计算规则：
> 
> - 按子组件的顺序依次递增。
> 
> - if/else语句中，只有条件成立的分支内的子组件会参与索引值计算，条件不成立的分支内子组件不计算索引值。
> 
> - ForEach/LazyForEach/Repeat语句中，会计算展开所有子组件索引值。
> 
> - [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、
> [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、
> [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和
> [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)发生变化以后，会更新子组件索引值。
> 
> - ListItemGroup作为一个整体计算一个索引值，ListItemGroup内部的ListItem不计算索引值。
> 
> - List子组件的visibility属性设置为Hidden或None依然会计算索引值。

## List

```TypeScript
List(options?: ListOptions)
```

创建List列表容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ListOptions](arkts-arkui-listoptions-i.md) | 否 | 设置List组件参数。不传入时使用默认配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChainAnimationOptions](arkts-arkui-chainanimationoptions-i-sys.md) | 链式联动动效属性集合，用于设置List最大间距、最小间距、动效强度、传导系数、边缘效果、刚度和阻尼。当列表需要精细控制链式联动弹性效果时，可通过调整本对象中的参数实现不同动效手感。 |
| [CloseSwipeActionOptions](arkts-arkui-closeswipeactionoptions-i.md) | 收起[EXPANDED](arkts-arkui-swipeactionstate-e.md)状态ListItem回调事件集合，用于设置收起动画完成后回调事件。 |
| [ListBackPressBehavior](arkts-arkui-listbackpressbehavior-i.md) | 定义List组件的系统返回键行为。 |
| [ListDividerOptions](arkts-arkui-listdivideroptions-i.md) | 用于设置List或ListItemGroup组件的分割线样式。 |
| [ListOptions](arkts-arkui-listoptions-i.md) | 用于设置List组件参数。 |
| [UIListEvent](arkts-arkui-uilistevent-i.md) | frameNode中[getEvent('List')](../arkts-apis/arkts-arkui-typenode-getevent-f.md)方法的返 回值，可用于给List节点设置滚动事件。UIListEvent继承于[UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md)。 |
| [VisibleListContentInfo](arkts-arkui-visiblelistcontentinfo-i.md) | 用于表示List可见内容区子组件的详细信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnListScrollIndexCallback](arkts-arkui-onlistscrollindexcallback-t.md) | List组件可见区域item变化事件的回调类型。 |
| [OnScrollVisibleContentChangeCallback](arkts-arkui-onscrollvisiblecontentchangecallback-t.md) | 有子组件划入或划出List显示区域时触发。API版本26.0.0开始，List从有子组件变成空的List时，上报的start和end参数的index成员为-1，itemGroupArea和itemIndexInGroup成员为undefined。API版本26.0.0以前， List从有子组件变成空的List时，上报的start和end参数会保留上次有子组件时的值。start和end的index同时返回0，代表List内只有一个子组件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ChainEdgeEffect](arkts-arkui-chainedgeeffect-e-sys.md) | 设置链式动效的边缘效果，用于决定列表滚动到边缘后继续拖动时列表项间距的变化方式。 |
| [ListItemAlign](arkts-arkui-listitemalign-e.md) | 设置子组件在List交叉轴方向的对齐方式。 |
| [ListItemGroupArea](arkts-arkui-listitemgrouparea-e.md) | 枚举了ListItemGroup各个区域。 |
| [ScrollSnapAlign](arkts-arkui-scrollsnapalign-e.md) | 设置列表项滚动结束对齐效果。 |
| [ScrollSnapAnimationSpeed](arkts-arkui-scrollsnapanimationspeed-e.md) | 设置列表项滚动限位动画速度。 |
| [ScrollState](arkts-arkui-scrollstate-e.md) | 滑动状态枚举。 |
| [StickyStyle](arkts-arkui-stickystyle-e.md) | ListItemGroup吸顶或吸底效果枚举。 |

## 示例

ListDataSource实现了LazyForEach数据源接口[IDataSource](ts-rendering-control-lazyforeach.md#idatasource)，用于通过LazyForEach给List提供子组件。

```TypeScript
// ListDataSource.ets
export class ListDataSource implements IDataSource {
  private list: number[] = [];
  private listeners: DataChangeListener[] = [];

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

  // 通知LazyForEach组件需要重载所有子组件
  notifyDataReload(): void {
    this.listeners.forEach(listener => {
      listener.onDataReloaded();
    });
  }

  // 通知控制器数据删除
  notifyDataDelete(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataDelete(index);
    });
  }

  // 通知控制器添加数据
  notifyDataAdd(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    });
  }

  // 在指定索引位置删除一个元素
  public deleteItem(index: number): void {
    this.list.splice(index, 1);
    this.notifyDataDelete(index);
  }

  // 在指定索引位置插入一个元素
  public insertItem(index: number, data: number): void {
    this.list.splice(index, 0, data);
    this.notifyDataAdd(index);
  }

  public reloadData(): void {
    this.notifyDataReload();
  }
}
```

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
              .width('100%').height(100).fontSize(16)
              .textAlign(TextAlign.Center).borderRadius(10).backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .listDirection(Axis.Vertical) // 排列方向
      .scrollBar(BarState.Off)
      .friction(0.6)
      .divider({ strokeWidth: 2, color: 0xFFFFFF, startMargin: 20, endMargin: 20 }) // 每行之间的分界线
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
        console.info(`onScroll scrollState = ScrollState` + scrollState + `, scrollOffset = ` + scrollOffset);
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

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](#示例1添加滚动事件)。

```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListLanesExample {
  arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]);
  @State alignListItem: ListItemAlign = ListItemAlign.Start;

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
          .border({ width: 2, color: Color.Green })
        }, (item: number) => item.toString())
      }
      .height(300)
      .width('90%')
      .friction(0.6)
      .border({ width: 3, color: Color.Red })
      .lanes({ minLength: 40, maxLength: 40 })
      .alignListItem(this.alignListItem)
      .scrollBar(BarState.Off)

      Button('点击更改alignListItem:' + this.alignListItem).onClick(() => {
        if (this.alignListItem == ListItemAlign.Start) {
          this.alignListItem = ListItemAlign.Center;
        } else if (this.alignListItem == ListItemAlign.Center) {
          this.alignListItem = ListItemAlign.End;
        } else {
          this.alignListItem = ListItemAlign.Start;
        }
      })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](#示例1添加滚动事件)。

```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);
  @State editFlag: boolean = false;

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Column() {
        List({ space: 20, initialIndex: 0 }) {
          LazyForEach(this.arr, (item: number, index: number) => {
            ListItem() {
              Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center }) {
                Text('' + item)
                  .width('100%')
                  .height(80)
                  .fontSize(20)
                  .textAlign(TextAlign.Center)
                  .borderRadius(10)
                  .backgroundColor(0xFFFFFF)
                  .flexShrink(1)
                if (this.editFlag) {
                  Button() {
                    Text('delete').fontSize(16)
                  }.width('30%').height(40)
                  .onClick(() => {
                    if (index != undefined) {
                      console.info(this.arr.getData(index) + 'Delete');
                      this.arr.deleteItem(index);
                      this.arr.reloadData();
                      console.info(JSON.stringify(this.arr));
                      this.editFlag = false;
                    }
                  }).stateEffect(true)
                }
              }
            }
          }, (item: number, index: number) => item.toString() + index.toString())
        }.width('90%')
        .scrollBar(BarState.Off)
        .friction(0.6)
      }.width('100%')

      Button('edit list')
        .onClick(() => {
          this.editFlag = !this.editFlag;
        }).margin({ top: 5, left: 20 })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](#示例1添加滚动事件)。

```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource=new ListDataSource([]);
  private scrollerForList: Scroller = new Scroller();

  aboutToAppear() {
    let list: number[] = [];
    for (let i = 0; i < 20; i++) {
      list.push(i);
    }
    this.arr = new ListDataSource(list);
  }

  build() {
    Column() {
      Row() {
        List({ space: 20, initialIndex: 3, scroller: this.scrollerForList }) {
          LazyForEach(this.arr, (item: number) => {
            ListItem() {
              Text('' + item)
                .width('100%').height(100).fontSize(16)
                .textAlign(TextAlign.Center)
            }
            .borderRadius(10).backgroundColor(0xFFFFFF)
            .width('60%')
            .height('80%')
          }, (item: number) => JSON.stringify(item))
        }
        .chainAnimation(true)
        .edgeEffect(EdgeEffect.Spring)
        .listDirection(Axis.Horizontal)
        .height('100%')
        .width('100%')
        .scrollSnapAlign(ScrollSnapAlign.CENTER)
        .borderRadius(10)
        .backgroundColor(0xDCDCDC)
      }
      .width('100%')
      .height('100%')
      .backgroundColor(0xDCDCDC)
      .padding({ top: 10 })
    }
  }
}
```

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](#示例1添加滚动事件)。

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([]);
  private scroller: ListScroller = new ListScroller();
  @State listSpace: number = 10;
  @State listChildrenSize: ChildrenMainSize = new ChildrenMainSize(100);
  aboutToAppear(){
    // 初始化数据源。
    let list: number[] = [];
    for (let i = 0; i < 10; i++) {
      list.push(i);
    }
    this.arr = new ListDataSource(list);
    // 前5个item的主轴大小不是默认大小100，因此需要通过ChildrenMainSize通知List。
    try {
      this.listChildrenSize.splice(0, 5, [300, 300, 300, 300, 300]);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`Failed to splice childrenMainSize for first 5 items. Code: ${err.code}, message: ${err.message}`);
    }
  }

  build() {
    Column() {
      List({ space: this.listSpace, initialIndex: 4, scroller: this.scroller }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('item-' + item)
              .height( item < 5 ? 300 : this.listChildrenSize.childDefaultSize)
              .width('90%')
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .backgroundColor(Color.Gray)
      .layoutWeight(1)
      .scrollBar(BarState.On)
      .childrenMainSize(this.listChildrenSize)
      .alignListItem(ListItemAlign.Center)
      Row({ space: 18 }) {
        Button() { Text('item size + 50') }.onClick(()=>{
          this.listChildrenSize.childDefaultSize += 50;
        }).height('50%').width('30%').backgroundColor(0xADD8E6)
        Button() { Text('item size - 50') }.onClick(()=>{
          if (this.listChildrenSize.childDefaultSize === 0) {
            return;
          }
          this.listChildrenSize.childDefaultSize -= 50;
        }).height('50%').width('30%').backgroundColor(0xADD8E6)
        Button() { Text('scrollTo (0, 310)') }.onClick(()=>{
          // 310: 跳转到item 1顶部与List顶部平齐的位置。
          // 如果不设置childrenMainSize，item高度不一致时scrollTo会不准确。
          this.scroller.scrollTo({ xOffset: 0, yOffset: 310 })
        }).height('50%').width('30%').backgroundColor(0xADD8E6)
      }.height('20%')
    }
  }
}
```

该示例展示了含有group时，获得List组件的Item索引相关信息。

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

class TimeTableDataSource implements IDataSource {
  private list: TimeTable[] = [];

  constructor(list: TimeTable[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): TimeTable {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}

class ProjectsDataSource implements IDataSource {
  private list: string[] = [];

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
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}

@Entry
@Component
struct ListItemGroupExample {
  private timeTable: TimeTable[] = [
  {
    title: '星期一',
    projects: ['语文', '数学', '英语']
  },
  {
    title: '星期二',
    projects: ['物理', '化学', '生物']
  },
  {
    title: '星期三',
    projects: ['历史', '地理', '政治']
  },
  {
    title: '星期四',
    projects: ['美术', '音乐', '体育']
  }
];
  private scroller: ListScroller = new ListScroller();
  @State listIndexInfo: VisibleListContentInfo = { index: -1 };
  @State mess:string = 'null';
  @State itemBackgroundColorArr: boolean[] = [false];
  @Builder
  itemHead(text: string) {
    Text(text)
      .fontSize(20)
      .backgroundColor(0xAABBCC)
      .width('100%')
      .padding(10)
  }

  @Builder
  itemFoot(num: number) {
    Text('共' + num + '节课')
      .fontSize(16)
      .backgroundColor(0xAABBCC)
      .width('100%')
      .padding(5)
  }

  build() {
    Column() {
      List({ space: 20, scroller: this.scroller}) {
        LazyForEach(new TimeTableDataSource(this.timeTable), (item: TimeTable, index: number) => {
          ListItemGroup({ header: this.itemHead(item.title), footer: this.itemFoot(item.projects.length) }) {
            LazyForEach(new ProjectsDataSource(item.projects), (project: string, subIndex: number) => {
              ListItem() {
                Text(project)
                  .width('100%')
                  .height(100)
                  .fontSize(20)
                  .textAlign(TextAlign.Center)
                  .backgroundColor(this.itemBackgroundColorArr[index * 3 +subIndex] ? 0x68B4FF: 0xFFFFFF)
              }
            }, (item: string) => item)
          }
          .divider({ strokeWidth: 1, color: Color.Blue }) // 每行之间的分界线
        }, (item: TimeTable) => item.title)
      }
      .width('90%')
      .sticky(StickyStyle.Header | StickyStyle.Footer)
      .scrollBar(BarState.Off)
      .gesture(
        PanGesture()
          .onActionUpdate((event: GestureEvent) => {
            if (event.fingerList[0] != undefined && event.fingerList[0].localX != undefined && event.fingerList[0].localY != undefined) {
              try {
                this.listIndexInfo =
                  this.scroller.getVisibleListContentInfo(event.fingerList[0].localX, event.fingerList[0].localY);
              } catch (error) {
                let err: BusinessError = error as BusinessError;
                console.error(`Failed to get visible list content info. Code: ${err.code}, message: ${err.message}`);
              }
              let itemIndex:string = 'undefined';
              if (this.listIndexInfo.itemIndexInGroup != undefined ) {
                itemIndex = this.listIndexInfo.itemIndexInGroup.toString();
                if (this.listIndexInfo.index != undefined && this.listIndexInfo.index >= 0 &&
                  this.listIndexInfo.itemIndexInGroup >= 0 ) {
                  this.itemBackgroundColorArr[this.listIndexInfo.index * 3 + this.listIndexInfo.itemIndexInGroup] = true;
                }
              }
              this.mess = 'index:' + this.listIndexInfo.index.toString() + ' itemIndex:' + itemIndex;
            }
          }))
      .gesture(
        TapGesture({ count: 1 })
          .onAction((event: GestureEvent) => {
            if (event) {
              this.itemBackgroundColorArr.splice(0,this.itemBackgroundColorArr.length);
            }
          })
      )
      Text('您当前位置Item索引为'+ this.mess)
        .fontColor(Color.Red)
        .height(50)
    }.width('100%').height('90%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}

interface TimeTable {
  title: string;
  projects: string[];
}
```

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](#示例1添加滚动事件)。

```TypeScript
import { LengthMetrics } from '@kit.ArkUI'
import { ListDataSource } from './ListDataSource';
@Entry
@Component
struct ListExample {
  private arr: ListDataSource=new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]);
  scrollerForList: Scroller = new Scroller();

  build() {
    Column() {

      List({ space: 20, initialIndex: 0, scroller: this.scrollerForList }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%').height(100).fontSize(16)
              .textAlign(TextAlign.Center).borderRadius(10).backgroundColor(0xFFFFFF)
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

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](#示例1添加滚动事件)。

```TypeScript
// xxx.ets
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
              .width('100%').height(100).fontSize(16)
              .textAlign(TextAlign.Center).borderRadius(10).backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .edgeEffect(EdgeEffect.Spring, {alwaysEnabled: true, effectEdge: EffectEdge.START})
      .width('90%').height('90%')
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

从API version 20开始，该示例通过[focusWrapMode](#focuswrapmode20)接口，实现了List组件方向键走焦换行效果。

```TypeScript
@Entry
@Component
struct ListExample {
  @State arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Column() {
        List({ space: 40, initialIndex: 0 }) {
          ForEach(this.arr, (item: number, index: number) => {
            ListItem() {
              Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center }) {
                Text('' + item)
                  .width(150)
                  .height(93)
                  .fontSize(30)
                  .textAlign(TextAlign.Center)
                  .borderRadius(10)
                  .backgroundColor(0xFFFFFF)
                  .flexShrink(1)
                  .focusable(true)
                  .offset({ left: 5 })
              }
            }
          }, (item: number, index: number) => item.toString() + index.toString())
        }
        .lanes(2)
        .contentStartOffset(20)
        .contentEndOffset(20)
        .width('100%')
        .scrollBar(BarState.Off)
        .friction(0.6)
        .focusWrapMode(FocusWrapMode.WRAP_WITH_ARROW)
        .alignListItem(ListItemAlign.Center)
        .offset({ left: 20 })
      }.width('90%')
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](#示例1添加滚动事件)。

```TypeScript
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([990, 991, 992, 993, 994, 995, 996, 997, 998, 999]);
  build() {
    Column() {
      List({ space: 20, initialIndex: 9 }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('message:' + item)
              .width('100%').height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .maintainVisibleContentPosition(true)
      .onScrollIndex((start:number)=>{
        if (start < 5) {
          for (let i = 0; i < 10; i++) {
            this.arr.insertItem(0, this.arr.getData(0) - 1);
          }
        }
      })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding(12)
  }
}
```

从API version 20开始，该示例展示了通过[scrollBarMargin](./ts-container-scrollable-common.md#scrollbarmargin20)属性设置滚动条边距并避让[contentStartOffset](#contentstartoffset11)、[contentEndOffset](#contentendoffset11)区域的效果。

```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ListScrollBarMarginExample {
  @State arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  build() {
    Column() {
      List({ space: 40, initialIndex: 0 }) {
        ForEach(this.arr, (item: number, index: number) => {
          ListItem() {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: number, index: number) => item.toString() + index.toString())
      }
      .contentStartOffset(20)
      .contentEndOffset(20)
      .scrollBar(BarState.On)
      .scrollBarMargin({ start: LengthMetrics.vp(20), end: LengthMetrics.vp(20) })
      .width('90%')
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

从API version 12开始，该示例展示了使用ForEach的[onMove](./ts-universal-attributes-drag-sorting.md#onmove)接口进行拖拽排序的效果，支持拖动到List边缘时触发List的自动滚动。

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
            Text(item.toString())
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .size({ height: 100, width: '100%' })
          }.margin(10)
          .borderRadius(10)
          .backgroundColor('#FFFFFFFF')
        }, (item: string) => item)
          .onMove((from: number, to: number) => {
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

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](#示例1添加滚动事件)。

```TypeScript
// xxx.ets
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
              .width('100%').height(100).fontSize(16)
              .textAlign(TextAlign.Center).borderRadius(10).backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .lanes({ fillType: PresetFillType.BREAKPOINT_SM2MD3LG5}, 10)
      .width('90%').height(600)
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

从API version 22 开始，该示例实现了List组件获取内容总大小的功能。

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ListExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
  scrollerForList: Scroller = new Scroller()
  @State contentWidth: number = -1;
  @State contentHeight: number = -1;

  build() {
    Column() {
      List({ space: 20, initialIndex: 0, scroller: this.scrollerForList }) {
        ForEach(this.arr, (item: number) => {
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
      .width('90%').height('90%')

      // 点击按钮来调用contentSize函数获取内容尺寸
      Button('GetContentSize')
        .onClick(() => {
          // Scroller未绑定组件时会抛异常，需要加上try catch保护
          try {
            // 通过调用contentSize函数获取内容尺寸的宽度值
            this.contentWidth = this.scrollerForList.contentSize().width;
            // 通过调用contentSize函数获取内容尺寸的高度值
            this.contentHeight = this.scrollerForList.contentSize().height;
          } catch (error) {
            let err: BusinessError = error as BusinessError;
            console.error(`Failed to get contentSize of the List. Code: ${err.code}, message: ${err.message}`);
          }
        })
      // 将获取到的内容尺寸信息通过文本进行呈现
      Text('Width：' + this.contentWidth + '，Height：' + this.contentHeight)
        .fontColor(Color.Red)
        .height(50)
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

该示例通过onItemDragStart等事件实现了ListItem在两个List组件间的拖拽效果。

```TypeScript
// xxx.ets
@ObservedV2
class ListData {
  @Trace public title: string = '';
  @Trace public data: string[] = [];

  constructor(title: string, data: string[]) {
    this.title = title;
    this.data = data;
  }
}

class DraggingData {
  public data?: string;
}

@ComponentV2
struct DraggableList {
  @Require @Param data: string[];
  @Require @Param draggingData: DraggingData;

  @Builder
  ItemBuilder(data: string, size: SizeOptions, event: ItemDragInfo): void {
    Stack() {
      Text(data)
    }
    .backgroundColor(Color.White)
    .borderRadius(4)
    .size(size)
  }

  viewWidth: number = 0;
  lastInsertIndex: number = 0;
  scroller: Scroller = new Scroller();

  build() {
    List({ scroller: this.scroller }) {
      ForEach(this.data, (item: string) => {
        ListItem() {
          Text(item)
        }
        .width('100%')
        .height('10%')
        .margin(10)
        .backgroundColor(Color.White)
        .borderRadius(4)
        .aspectRatio(1)
      }, (item: string) => item)
    }
    .width('50%')
    .layoutWeight(1)
    .padding(10)
    .onItemDragStart((event: ItemDragInfo, itemIndex: number) => {
      let rect = this.scroller.getItemRect(itemIndex);
      let size: SizeOptions = {
        width: rect.width,
        height: rect.height
      };
      this.lastInsertIndex = itemIndex;
      this.draggingData.data = this.data[itemIndex];
      this.data.splice(itemIndex, 1);

      return this.ItemBuilder(this.draggingData.data, size, event);
    })
    .onItemDragEnter((event: ItemDragInfo) => {
      console.info('Item drag enter at position:', event.x, event.y);
    })
    .onItemDragMove((event: ItemDragInfo, itemIndex: number, insertIndex: number) => {
      if (this.lastInsertIndex != insertIndex){
        console.info('insertIndex change from ', this.lastInsertIndex, 'to', insertIndex);
        this.lastInsertIndex = insertIndex;
      }
    })
    .onItemDragLeave((event: ItemDragInfo, itemIndex: number) => {
      console.info('Item ' + itemIndex + ' drag leave at position:', event.x, event.y);
    })
    .onItemDrop((event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => {
      if (!isSuccess) {
        this.draggingData.data = undefined;
        return;
      }
      if (insertIndex >= 0) {
        this.data.splice(insertIndex, 0, this.draggingData.data!);
      }
      this.draggingData.data = undefined;
    })
    .onSizeChange((oldValue: SizeOptions, newValue: SizeOptions) => {
      this.viewWidth = newValue.width as number;
    })
  }
}

@Entry
@ComponentV2
struct Index {
  @Local data: ListData[] = [
    new ListData('A', ['A1', 'A2', 'A3', 'A4', 'A5', 'A6', 'A7', 'A8']),
    new ListData('B', ['B1', 'B2', 'B3', 'B4', 'B5', 'B6', 'B7', 'B8']),
  ]
  @Local draggingData: DraggingData = new DraggingData();

  build() {
    Stack() {
      Row() {
        DraggableList({ data: this.data[0].data, draggingData: this.draggingData })
        DraggableList({ data: this.data[1].data, draggingData: this.draggingData })
      }
    }
    .backgroundColor('#FFDCDCDC')
  }
}
```

该示例使用[scrollToItemInGroup](arkts-arkui-listscroller-c.md#scrolltoitemingroup)接口，实现了点击[ListItemGroup](./ts-container-listitemgroup.md)中的[ListItem](./ts-container-listitem.md)时将其居中的效果。

```TypeScript
import { util } from '@kit.ArkTS';

class Contact {
  key: string = util.generateRandomUUID(true);
  name: string;
  icon: Resource;

  constructor(name: string, icon: Resource) {
    this.name = name;
    this.icon = icon;
  }
}

class ContactsGroup {
  title: string = '';
  contacts: Array<object> | null = null;
  key: string = '';
}

@Entry
@Component
struct ContactsList {
  private scroller: ListScroller = new ListScroller();
  private contactsGroups: ContactsGroup[] = [
    {
      title: 'A',
      contacts: [
        new Contact('艾佳', $r('app.media.icon')),  // $r('app.media.icon')需要替换为开发者所需的图像资源文件
        new Contact('安安', $r('app.media.icon')),
        new Contact('Angela', $r('app.media.icon'))
        // ...
      ],
      key: util.generateRandomUUID(true)
    } as ContactsGroup,
    {
      title: 'B',
      contacts: [
        new Contact('白叶', $r('app.media.icon')),
        new Contact('伯明', $r('app.media.icon'))
        // ...
      ],
      key: util.generateRandomUUID(true)
    } as ContactsGroup,
    // ...
  ]

  @Builder
  itemHead(text: string) {
    Text(text)
      .fontSize(20)
      .backgroundColor('#fff1f3f5')
      .width('100%')
      .padding(5)
  }

  build() {
    List({ scroller: this.scroller }) {
      ForEach(this.contactsGroups, (item: ContactsGroup, index: number) => {
        ListItemGroup({ header: this.itemHead(item.title) }) {
          ForEach(item.contacts, (contact: Contact, subIndex: number) => {
            ListItem() {
              Row() {
                Image(contact.icon)
                  .width(40)
                  .height(40)
                  .margin(10)
                Text(contact.name).fontSize(20)
              }
              .width('100%')
              .justifyContent(FlexAlign.Start)
              .margin(10)
            }
            .gesture(
              TapGesture({ count: 1 })
                .onAction((event: GestureEvent) => {
                  if (event) {
                    const itemRect = this.scroller.getItemRectInGroup(index, subIndex);
                    console.info('第', index + 1, '个ListItemGroup的第', subIndex + 1, '个ListItem的 x:', itemRect.x,
                      ' y:', itemRect.y, ' width:', itemRect.width, ' height:', itemRect.height)
                    this.scroller.scrollToItemInGroup(index, subIndex, true, ScrollAlign.CENTER);
                  }
                })
            )
          }, (contact: Contact) => JSON.stringify(contact))
        }
        .divider({ strokeWidth: 4 })
        .width('100%')
      }, (item: ContactsGroup) => JSON.stringify(item))
    }
    .onScrollFrameBegin((offset: number, state: ScrollState) => {
      console.info('List scrollFrameBegin offset: ' + offset + ' state: ' + state.toString());
      return { offsetRemain: offset };
    })
  }
}
```

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](#示例1添加滚动事件)。

```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);
  @State isSelected: boolean[] = [];
  selectedCount: number = 0;

  @Styles
  normalStyles(): void {
    .opacity(1.0)
  }

  @Styles
  selectStyles(): void {
    .opacity(0.4)
  }

  onPageShow(): void {
    let i: number = 0;
    for (i = 0; i < 10; i++) {
      this.isSelected.push(false);
    }
  }

  @Builder
  MenuBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('menu item 1')
        .fontSize(18)
        .width(120)
        .height(50)
        .textAlign(TextAlign.Center)
      Divider().height(10)
      Text('menu item 2')
        .fontSize(18)
        .width(120)
        .height(50)
        .textAlign(TextAlign.Center)
    }.width(100)
  }

  build() {
    Column({ space: 5 }) {
      List({ space: 10 }) {
        LazyForEach(this.arr, (item: number) => {
            ListItem() {
              Text(item.toString())
                .fontSize(16)
                .backgroundColor(Color.White)
                .width('100%')
                .height(50)
                .textAlign(TextAlign.Center)
            }
            .selected(this.isSelected[item])
            // 设置多选显示效果
            .stateStyles({
              normal: this.normalStyles,
              selected: this.selectStyles
            })
            .bindContextMenu(this.MenuBuilder, ResponseType.LongPress,
              { preview: MenuPreviewMode.IMAGE, hapticFeedbackMode: HapticFeedbackMode.ENABLED })
            .onClick(() => {
              this.isSelected[item] = !this.isSelected[item];
              console.info(`item:${item}, this.isSelected[item]:${this.isSelected[item]}`)
              if (this.isSelected[item]) {
                ++this.selectedCount;
              } else {
                --this.selectedCount;
              }
            })
        }, (item: number) => item.toString())
      }
      .editModeOptions({
        enableGatherSelectedItemsAnimation: true, onGetPreviewBadge: () => {
          return this.selectedCount;
        }
      })
      .width('90%')
      .height(300)
      .scrollBar(BarState.Off)
    }.width('100%').margin({ top: 5 }).backgroundColor('#FFDCDCDC')
  }
}
```

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](#示例1添加滚动事件)。

```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([]);
  @State @Watch('onEditModeChanged') enableEditMode: boolean = false;
  @State selectedIndexes: number[] = [];

  onEditModeChanged() {
    console.info(`enableEditMode changed to: ${this.enableEditMode}`);
    if (!this.enableEditMode) {
      console.info('enableEditMode changed to false, clearing selectedIndexes');
      this.selectedIndexes = [];
    }
  }

  aboutToAppear() {
    let list: number[] = [];
    for (let i = 0; i < 10; i++) {
        list.push(i);
    }
    this.arr = new ListDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      List({ space: 10 }) {
        LazyForEach(this.arr, (item: number, index: number) => {
          ListItem() {
            Text(item.toString())
              .fontSize(16)
              .width('100%')
              .height(50)
              .textAlign(TextAlign.Center)
          }
          .backgroundColor(Color.White)
          .selected(this.selectedIndexes.includes(index))
          .onSelect((isSelected: boolean) => {
            if (isSelected) {
              this.selectedIndexes.push(index);
            } else {
              let deleted = this.selectedIndexes.findIndex((value) => value === index);
              if (deleted !== -1) {
                this.selectedIndexes.splice(deleted, 1);
              }
            }
          })
        }, (item: number) => item.toString())
      }
      .width('90%')
      .height(300)
      .scrollBar(BarState.Off)
      .enableEditMode(this.enableEditMode!!)
      .onEditModeChange((data: boolean) => {
        // 在此处也可实现onEditModeChanged中的业务逻辑
        console.info(`onEditModeChange:${data}`)
      })
      .editModeOptions({ useDefaultMultiSelectStyle: true, enableTwoFingerMultiSelect: true })
    }.width('100%').padding({ top: 10 }).backgroundColor('#FFDCDCDC')
  }
}
```
