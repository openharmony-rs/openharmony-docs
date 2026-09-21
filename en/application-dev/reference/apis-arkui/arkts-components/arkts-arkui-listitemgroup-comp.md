# ListItemGroup

The **ListItemGroup** component is used to display list item groups. It must be used with the List component. Unless specified otherwise, it spans the entire width of the **List** component.

Lazy loading of **ListItemGroup** loads the child components in the visible area as required. Compared with full loading, lazy loading can improve the application startup speed and reduce the memory usage. The lazy loading capabilities vary when the **ListItemGroup** component is used together with [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md).

- When **ListItemGroup** is used together with **ForEach**, all child nodes are created at a time. The nodes within
the screen range are laid out and rendered when needed. When a user swipes, the nodes that are out of the screen range are not removed from the tree, and the nodes that are within the screen range are laid out and rendered.
- When **ListItemGroup** is used together with **LazyForEach**, all nodes within the screen range are created, laid
out, and rendered at a time. When a user swipes, the nodes that are out of the screen range are removed from the tree, and the nodes that are within the screen range are created, laid out, and rendered.
- When the **ListItemGroup** component is used together with **Repeat** with
[virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll), the lazy loading behavior is the same as that of **LazyForEach**. When the **ListItemGroup** component is used together with **Repeat** without **virtualScroll**, the lazy loading behavior is the same as that of **ForEach**.

Preloading in **ListItemGroup** refers to loading not only the visible child components within the display area but also some invisible child components outside the display area during idle time. Preloading can reduce frame loss during scrolling and improve smoothness. Preloading takes effect only when lazy loading is used. The preloading capabilities vary when the **ListItemGroup** component is used together with [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md).

- When the **ListItemGroup** component is used together with **ForEach** and
[cachedCount](arkts-arkui-list-comp-attribute.md#cachedcount) is set, in addition to laying out child components within the display area, child components within the range of **cachedCount** outside the display area are pre-laid out during idle time based on the **cachedCount** attribute of the **List** component.
- When the **ListItemGroup** component is used together with **LazyForEach** and
[cachedCount](arkts-arkui-list-comp-attribute.md#cachedcount) is set, in addition to creating and laying out child components within the display area, child components within the range of **cachedCount** outside the display area are created and pre-laid out during idle time based on the **cachedCount** attribute of the **List** component.
- When the **ListItemGroup** component is used together with **Repeat** with
[virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll), the preloading behavior is the same as that of **LazyForEach**. When the **ListItemGroup** component is used together with **Repeat** without **virtualScroll**, the preloading behavior is the same as that of **ForEach**.

> **NOTE**

> - This component can be used only as a child of List. > > - The **ListItemGroup** component does not support the universal attribute > [aspectRatio](arkts-arkui-common-comp-commonmethod-c.md#aspectratio). > > - If the parent **List** component of **ListItemGroup** has its [listDirection](arkts-arkui-list-comp-attribute.md#listdirection) > attribute set to **Axis.Vertical**, setting the > [universal attribute height](arkts-arkui-common-comp-commonmethod-c.md#height) has no effect. In this case, the height of > the **ListItemGroup** component is fixed at the sum of the component's header height, footer height, and total > height of the list items. > > - If the parent **List** component of **ListItemGroup** has its **listDirection** attribute set to > **Axis.Horizontal**, setting the [universal attribute width](arkts-arkui-common-comp-commonmethod-c.md#width) has no > effect. In this case, the width of the **ListItemGroup** component is fixed at the sum of the component's header > width, footer width, and total width of the list items. > > - The list items in the **ListItemGroup** component cannot be edited or dragged. This means that their > [editable](arkts-arkui-listitem-comp-attribute.md#editable) attribute does not take effect. > > - The **ListItemGroup** ignores the **direction** attribute for setting the layout direction; instead, it adopts > the layout direction of its parent **List** component.

## Child Components

Contains the ListItem child component. Child components can be dynamically generated using rendering control types [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md). **LazyForEach** or **Repeat** is recommended to optimize performance.

## ListItemGroup

```TypeScript
ListItemGroup(options?: ListItemGroupOptions)
```

Creates a **ListItemGroup** component.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ListItemGroupOptions](arkts-arkui-listitemgroup-comp-listitemgroupoptions-i.md) | No | Parameters of the list item group. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ListItemGroupOptions](arkts-arkui-listitemgroup-comp-listitemgroupoptions-i.md) | Describes the **ListItemGroup** component parameter. |

### Enums

| Name | Description |
| --- | --- |
| [ListItemGroupHeaderFooterStyle](arkts-arkui-listitemgroup-comp-listitemgroupheaderfooterstyle-e.md) | Enumerates the header and footer styles of **ListItemGroup**. |
| [ListItemGroupStyle](arkts-arkui-listitemgroup-comp-listitemgroupstyle-e.md) | Enumerates the card styles of the **ListItemGroup** component. |

## Examples

### Example 1: Setting a Sticky Header and Footer

This example uses [sticky](ts-container-list.md#sticky9) to implement the sticky header and footer.

ListDataSource implements the LazyForEach data source API [IDataSource](ts-rendering-control-lazyforeach.md#idatasource), which is used to provide child components for List and ListItemGroup through LazyForEach.

```TypeScript
// ListDataSource.ets
export class TimeTableDataSource implements IDataSource {
  private list: TimeTable[] = [];
  private listeners: DataChangeListener[] = [];

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

  // Notify the controller of data changes.
  notifyDataChange(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    });
  }

  // Modify the first element.
  public change1stItem(temp: TimeTable): void {
    this.list[0] = temp;
    this.notifyDataChange(0);
  }
}

export class ProjectsDataSource implements IDataSource {
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

export interface TimeTable {
  title: string;
  projects: string[];
}
```



```TypeScript
// xxx.ets
import { TimeTable, ProjectsDataSource, TimeTableDataSource } from './ListDataSource';
@Entry
@Component
struct ListItemGroupExample {
  itemGroupArray: TimeTableDataSource = new TimeTableDataSource([]);

  aboutToAppear(): void {
    let timeTable: TimeTable[] = [
      {
        title: 'Monday',
        projects: ['Language', 'Math', 'English']
      },
      {
        title: 'Tuesday',
        projects: ['Physics', 'Chemistry', 'Biology']
      },
      {
        title: 'Wednesday',
        projects: ['History', 'Geography', 'Politics']
      },
      {
        title: 'Thursday',
        projects: ['Art', 'Music', 'Sports']
      }
    ];
    this.itemGroupArray = new TimeTableDataSource(timeTable);
  }

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
    Text('Total lessons: ' + num)
      .fontSize(16)
      .backgroundColor(0xAABBCC)
      .width('100%')
      .padding(5)
  }

  build() {
    Column() {
      List({ space: 20 }) {
        LazyForEach(this.itemGroupArray, (item: TimeTable) => {
          ListItemGroup({ header: this.itemHead(item.title), footer: this.itemFoot(item.projects.length) }) {
            LazyForEach(new ProjectsDataSource(item.projects), (project: string) => {
              ListItem() {
                Text(project)
                  .width('100%')
                  .height(100)
                  .fontSize(20)
                  .textAlign(TextAlign.Center)
                  .backgroundColor(0xFFFFFF)
              }
            }, (item: string) => item)
          }
          .divider({ strokeWidth: 1, color: Color.Blue }) // Divider between lines
        })
      }
      .width('90%')
      .sticky(StickyStyle.Header | StickyStyle.Footer)
      .scrollBar(BarState.Off)
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

### Example 2: Applying a Card-style Effect

This example illustrates the card-style effect of the ListItemGroup component.



```TypeScript
// xxx.ets
@Entry
@Component
struct ListItemGroupExample2 {
  private arr: ArrObject[] = [
    {
      style: ListItemGroupStyle.CARD,
      itemStyles: [ListItemStyle.CARD, ListItemStyle.CARD, ListItemStyle.CARD]
    },
    {
      style: ListItemGroupStyle.CARD,
      itemStyles: [ListItemStyle.CARD, ListItemStyle.CARD, ListItemStyle.NONE]
    },
    {
      style: ListItemGroupStyle.CARD,
      itemStyles: [ListItemStyle.CARD, ListItemStyle.NONE, ListItemStyle.CARD]
    },
    {
      style: ListItemGroupStyle.NONE,
      itemStyles: [ListItemStyle.CARD, ListItemStyle.CARD, ListItemStyle.NONE]
    }
  ];

  build() {
    Column() {
      List({ space: '4vp', initialIndex: 0 }) {
        ForEach(this.arr, (item: ArrObject, index?: number) => {
          ListItemGroup({ style: item.style }) {
            ForEach(item.itemStyles, (itemStyle: number, itemIndex?: number) => {
              ListItem({ style: itemStyle }) {
                if (index != undefined && itemIndex != undefined) {
                  Text('Item ' + (itemIndex + 1) + ' in group ' + (index + 1))
                    .width('100%')
                    .textAlign(TextAlign.Center)
                }
              }
            }, (item: number) => item.toString())
          }
        })
      }
      .width('100%')
      .multiSelectable(true)
      .backgroundColor(0xDCDCDC)
    }
    .width('100%')
    .padding({ top: 5 })
  }
}

interface ArrObject {
  style: number;
  itemStyles: number[];
}
```

### Example 3: Setting Header and Footer

This example uses ComponentContent to set the header and footer.

For details about ListDataSource and the complete code, see [Example 1: Setting a Sticky Header and Footer](#example-1-setting-a-sticky-header-and-footer).



```TypeScript
// xxx.ets
import { ComponentContent } from '@kit.ArkUI';
import { TimeTable, ProjectsDataSource, TimeTableDataSource } from './ListDataSource';

class HeadBuilderParams {
  text: string | Resource;
  constructor(text: string | Resource) {
    this.text = text;
  }
}

class FootBuilderParams {
  num: number | Resource;
  constructor(num: number | Resource) {
    this.num = num;
  }
}

@Builder
function itemHead(params: HeadBuilderParams) {
  Text(params.text)
    .fontSize(20)
    .height('48vp')
    .width('100%')
    .padding(10)
    .backgroundColor($r('sys.color.background_tertiary'))
}

@Builder
function itemFoot(params: FootBuilderParams) {
  Text('Total lessons: ' + params.num.toString())
    .fontSize(20)
    .height('48vp')
    .width('100%')
    .padding(10)
    .backgroundColor($r('sys.color.background_tertiary'))
}

@Component
struct MyItemGroup {
  item: TimeTable = { title: '', projects: [] };
  header?: ComponentContent<HeadBuilderParams> = undefined;
  footer?: ComponentContent<FootBuilderParams> = undefined;
  headerParam = new HeadBuilderParams(this.item.title);
  footerParam = new FootBuilderParams(this.item.projects.length);
  itemArr: ProjectsDataSource = new ProjectsDataSource([]);

  aboutToAppear(): void {
    this.header = new ComponentContent(this.getUIContext(), wrapBuilder(itemHead), this.headerParam);
    this.footer = new ComponentContent(this.getUIContext(), wrapBuilder(itemFoot), this.footerParam);
    this.itemArr = new ProjectsDataSource(this.item.projects);
  }
  getHeader() {
    this.header?.update(new HeadBuilderParams(this.item.title));
    return this.header;
  }

  getFooter() {
    this.footer?.update(new FootBuilderParams(this.item.projects.length));
    return this.footer;
  }

  build() {
    ListItemGroup({
      headerComponent: this.getHeader(),
      footerComponent: this.getFooter()
    }) {
      LazyForEach(this.itemArr, (project: string) => {
        ListItem() {
          Text(project)
            .width('100%')
            .height(100)
            .fontSize(20)
            .textAlign(TextAlign.Center)
        }
      }, (item: string) => item)
    }
    .divider({ strokeWidth: 1, color: Color.Blue }) // Divider between lines
  }
}

@Entry
@Component
struct ListItemGroupExample {
  itemGroupArray: TimeTableDataSource = new TimeTableDataSource([]);
  aboutToAppear(): void {
    let timeTable: TimeTable[] = [
      {
        title: 'Monday',
        projects: ['Language', 'Math', 'English']
      },
      {
        title: 'Tuesday',
        projects: ['Physics', 'Chemistry', 'Biology']
      },
      {
        title: 'Wednesday',
        projects: ['History', 'Geography', 'Politics', 'Sports']
      },
      {
        title: 'Thursday',
        projects: ['Art', 'Music']
      }
    ];
    this.itemGroupArray = new TimeTableDataSource(timeTable);
  }

  build() {
    Column() {
      Button('update').width(100).height(50).onClick(() => {
        this.itemGroupArray.change1stItem({
          title: 'Updated Monday',
          projects: ['Language', 'Physics', 'History', 'Art']
        });
      })
      List({ space: 20 }) {
        LazyForEach(this.itemGroupArray, (item: TimeTable) => {
          MyItemGroup({ item: item })
        }, (item: TimeTable) => item.title) // LazyForEach determines whether to refresh the child component based on the key value.
      }
      .layoutWeight(1)
      .sticky(StickyStyle.Header | StickyStyle.Footer)
      .scrollBar(BarState.Off)
    }
    .backgroundColor($r('sys.color.background_primary'))
  }
}
```

### Example 4: Setting a Multi-Column Layout

This example shows how ListItemGroup is used in a multi-column layout. The multi-column layout is implemented by setting the [lanes](ts-container-list.md#lanes9) attribute of the List component.

For details about ListDataSource and the complete code, see [Example 1: Setting a Sticky Header and Footer](#example-1-setting-a-sticky-header-and-footer).



```TypeScript
// xxx.ets
import { ComponentContent } from '@kit.ArkUI';
import { TimeTable, ProjectsDataSource, TimeTableDataSource } from './ListDataSource';

class HeadBuilderParams {
  text: string | Resource;

  constructor(text: string | Resource) {
    this.text = text;
  }
}

class FootBuilderParams {
  num: number | Resource;

  constructor(num: number | Resource) {
    this.num = num;
  }
}

@Builder
function itemHead(params: HeadBuilderParams) {
  Text(params.text)
    .fontSize(20)
    .height('48vp')
    .width('100%')
    .padding(10)
    .backgroundColor($r('sys.color.background_tertiary'))
}

@Builder
function itemFoot(params: FootBuilderParams) {
  Text('Total lessons: ' + params.num.toString())
    .fontSize(20)
    .height('48vp')
    .width('100%')
    .padding(10)
    .backgroundColor($r('sys.color.background_tertiary'))
}

@Component
struct MyItemGroup {
  item: TimeTable = { title: '', projects: [] };
  header?: ComponentContent<HeadBuilderParams> = undefined;
  footer?: ComponentContent<FootBuilderParams> = undefined;
  headerParam = new HeadBuilderParams(this.item.title);
  footerParam = new FootBuilderParams(this.item.projects.length);
  itemArr: ProjectsDataSource = new ProjectsDataSource([]);

  aboutToAppear(): void {
    this.header = new ComponentContent(this.getUIContext(), wrapBuilder(itemHead), this.headerParam);
    this.footer = new ComponentContent(this.getUIContext(), wrapBuilder(itemFoot), this.footerParam);
    this.itemArr = new ProjectsDataSource(this.item.projects);
  }

  getHeader() {
    this.header?.update(new HeadBuilderParams(this.item.title));
    return this.header;
  }

  getFooter() {
    this.footer?.update(new FootBuilderParams(this.item.projects.length));
    return this.footer;
  }

  build() {
    ListItemGroup({
      headerComponent: this.getHeader(),
      footerComponent: this.getFooter()
    }) {
      LazyForEach(this.itemArr, (project: string) => {
        ListItem() {
          // Modify the ListItem style to adapt to the multi-column layout.
          Column() {
            Text(project)
              .fontSize(20)
              .textAlign(TextAlign.Center)
          }
          .width('100%')
          .height(80)
          .padding(8)
          .justifyContent(FlexAlign.Center)
          .backgroundColor($r('sys.color.background_secondary'))
          .borderRadius(12)
          .shadow({
            radius: 4,
            color: '#20000000',
            offsetX: 0,
            offsetY: 2
          })
        }
      }, (item: string) => item)
    }
    .divider({
      strokeWidth: 2,
      color: $r('sys.color.background_tertiary'),
      startMargin: 20,
      endMargin: 20
    })
  }
}

@Entry
@Component
struct ListItemGroupExample {
  itemGroupArray: TimeTableDataSource = new TimeTableDataSource([]);

  aboutToAppear(): void {
    let timeTable: TimeTable[] = [
      {
        title: 'Monday',
        projects: ['Chinese', 'Math', 'English', 'Physics', 'Chemistry', 'Biology']
      },
      {
        title: 'Tuesday',
        projects: ['History', 'Geography', 'Politics', 'Physical Education', 'Art', 'Music']
      },
      {
        title: 'Wednesday',
        projects: ['Computer', 'Programming', 'Algorithm', 'Data Structure', 'Network']
      },
      {
        title: 'Thursday',
        projects: ['Literature', 'Writing', 'Reading', 'Calligraphy']
      },
      {
        title: 'Friday',
        projects: ['Experiment', 'Life', 'Olympiad Mathematics', 'Advanced Mathematics', 'Traditional Chinese Medicine']
      }
    ];
    this.itemGroupArray = new TimeTableDataSource(timeTable);
  }

  build() {
    Column() {
      List({ space: 15 }) {
        LazyForEach(this.itemGroupArray, (item: TimeTable) => {
          MyItemGroup({ item: item })
        }, (item: TimeTable) => item.title)
      }
      .lanes(3) // Set the three-column layout.
      .alignListItem(ListItemAlign.Center) // Align items in the center of the cross axis.
      .layoutWeight(1)
      .scrollBar(BarState.Auto)
      .width('100%')
      .margin(10)
    }
    .backgroundColor($r('sys.color.background_primary'))
    .width('100%')
    .height('100%')
    .padding(10)
  }
}
```

### Example 5: Setting Floating State

This example sets the [headerStyle](arkts-arkui-listitemgroup-comp-listitemgroupoptions-i.md) of ListItemGroup to [ListItemGroupHeaderFooterStyle.FLOATING](arkts-arkui-listitemgroup-comp-listitemgroupheaderfooterstyle-e.md) to implement the floating display effect of the group header during scrolling.

```TypeScript
// xxx.ets
export interface ContactGroup {
  letter: string;
  names: string[];
}

@Entry
@Component
struct Index {
  private scroller: Scroller = new Scroller();
  @State groups: ContactGroup[] = [];

  aboutToAppear(): void {
    this.groups = [
      {
        letter: 'A',
        names: ['Alice', 'Anna', 'Aaron']
      },
      {
        letter: 'B',
        names: ['Bob', 'Bella', 'Brian']
      },
      {
        letter: 'C',
        names: ['Cindy', 'Charlie']
      },
      {
        letter: 'D',
        names: ['David', 'Diana', 'Doris']
      }
    ]
  }

  @Builder
  private GroupHeader(letter: string) {
    Row() {
      Text(letter)
        .fontSize("16.0fp")
        .size({width: 40, height: 28})
        .textAlign(TextAlign.Center)
    }.margin({left: 14, right: 14})
  }

  build() {
    List({ scroller: this.scroller , space: 8}) {
      ForEach(this.groups, (group: ContactGroup) => {
        ListItemGroup({ header: this.GroupHeader(group.letter), headerStyle: ListItemGroupHeaderFooterStyle.FLOATING }) {
          ForEach(group.names, (name: string) => {
            ListItem() {
              Text(name)
                .fontSize(16)
                .fontColor('#182431')
                .width('100%')
                .height(72)
                .padding({ left: 16 })
            }
          }, (name: string) => name)
        }
      }, (group: ContactGroup) => group.letter)
    }
    .height('100%')
    .width('100%')
    .scrollBar(BarState.Off)
    .sticky(StickyStyle.Header)
  }
}
```
