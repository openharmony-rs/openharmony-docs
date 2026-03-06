# ListItemGroup

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong-->
<!--Designer: @yylong-->
<!--Tester: @liuzhenshuo-->
<!--Adviser: @Brilliantry_Rui-->

The **ListItemGroup** component is used to display list item groups. It must be used with the [List](ts-container-list.md) component. Unless specified otherwise, it spans the entire width of the **List** component.

Lazy loading of ListItemGroup indicates that child components in the visible area are loaded on demand. Compared with full loading, lazy loading can improve the application startup speed and reduce the memory consumption. The lazy loading capabilities of ListItemGroup and [ForEach ](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach ](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat ](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) are different.

 - When ListItemGroup is combined with ForEach, all child nodes are created at a time. The nodes within the screen range are laid out and rendered when required. When a user swipes, the nodes that are out of the screen range are not removed from the tree, and the nodes that are within the screen range are laid out and rendered.

 - When ListItemGroup is combined with LazyForEach, nodes within the screen range are created, laid out, and rendered at a time. When a user swipes, the nodes that are out of the screen range are removed from the tree, and the nodes that are within the screen range are created, laid out, and rendered.

 - When ListItemGroup is combined with Repeat with [virtualScroll](./ts-rendering-control-repeat.md#virtualscroll), the lazy loading behavior is the same as that of LazyForEach. When ListItemGroup is combined with Repeat without virtualScroll, the lazy loading behavior is the same as that of ForEach.

ListItemGroup preloading refers to the process of loading child components that are not visible in the display area in advance when idle timeslots are available. Preloading can reduce frame loss during scrolling and improve smoothness. Preloading takes effect only when it is used together with lazy loading. The preloading capability varies depending on the combination of ListItemGroup and [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md).

 - When ListItemGroup is combined with ForEach, if [cachedCount](./ts-container-list.md#cachedcount) is set, in addition to child components in the display area, subnodes within the cachedCount range outside the display area are pre-arranged based on the cachedCount attribute of the List component in idle timeslots.

 - When ListItemGroup is combined with LazyForEach, if [cachedCount](./ts-container-list.md#cachedcount) is set, in addition to child components in the display area, subnodes within the cachedCount range outside the display area are pre-created and pre-arranged based on the cachedCount attribute of the List component in idle timeslots.

 - When ListItemGroup is combined with Repeat with [virtualScroll](./ts-rendering-control-repeat.md#virtualscroll), its preloading behavior is the same as that of LazyForEach. When ListItemGroup is combined with Repeat without virtualScroll, its preloading behavior is the same as that of ForEach.

> **NOTE**
>
> - This component is supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
> - This component can be used only as a child of [List](ts-container-list.md).
> - The **ListItemGroup** component does not support the universal attribute [aspectRatio](ts-universal-attributes-layout-constraints.md#aspectratio).
> - If the parent **List** component of **ListItemGroup** has its [listDirection](./ts-container-list.md#listdirection) attribute set to **Axis.Vertical**, setting the [universal attribute height](ts-universal-attributes-size.md#height) has no effect. In this case, the height of the **ListItemGroup** component is fixed at the sum of the component's header height, footer height, and total height of the list items.
> - If the parent **List** component of **ListItemGroup** has its **listDirection** attribute set to **Axis.Horizontal**, setting the [universal attribute width](ts-universal-attributes-size.md#width) has no effect. In this case, the width of the **ListItemGroup** component is fixed at the sum of the component's header width, footer width, and total width of the list items.
> - The list items in the **ListItemGroup** component cannot be edited or dragged. This means that their [editable](./ts-container-listitem.md#editabledeprecated) attribute does not take effect.
> - The **ListItemGroup** ignores the **direction** attribute for setting the layout direction; instead, it adopts the layout direction of its parent **List** component.

## Child Components

This component supports the [ListItem](ts-container-listitem.md) child component. Child components can be dynamically generated using the rendering control types ([if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)). LazyForEach or Repeat is recommended to optimize performance.

## APIs

ListItemGroup(options?: ListItemGroupOptions)

Create a **ListItemGroup** component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options |  [ListItemGroupOptions](#listitemgroupoptions)| No| Parameters of the list item group.|

## ListItemGroupOptions

ListItemGroup component parameter.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name             | Type                                           | Read-Only| Optional  | Description                                                    |
| ------------------- | --------------------------------------------------- | ---- | -- | ------------------------------------------------------------ |
| header              | [CustomBuilder](ts-types.md#custombuilder8) &nbsp;   | No  | Yes| Header of the list item group.<br>**NOTE**<br>One child component, or no child component at all, can be placed inside.<br>**Atomic service API**: This API can be used in atomic services since API version 11.              |
| headerComponent<sup>13+</sup>              | [ComponentContent](../js-apis-arkui-ComponentContent.md)       | No  | Yes| Header of the list item group, in the type of ComponentContent.<br>**NOTE**<br>One child component, or no child component at all, can be placed inside. This parameter takes precedence over the **header** parameter. This means that, if both **header** and **headerComponent** are set, the value of **headerComponent** is used.<br>You are not advised to use the same headerComponent for different ListItemGroups at the same time. Otherwise, display problems may occur.<br>**Atomic service API**: This API can be used in atomic services since API version 13.             |
| footer              | [CustomBuilder](ts-types.md#custombuilder8) &nbsp;     | No  | Yes| Footer of the list item group.<br>**NOTE**<br>One child component, or no child component at all, can be placed inside.<br>**Atomic service API**: This API can be used in atomic services since API version 11.              |
| footerComponent<sup>13+</sup>              | [ComponentContent](../js-apis-arkui-ComponentContent.md)       | No  | Yes| Footer of the list item group, in the type of ComponentContent.<br>**NOTE**<br>One child component, or no child component at all, can be placed inside. This parameter takes precedence over the **footer** parameter. This means that, if both **footer** and **footerComponent** are set, the value of **footerComponent** is used.<br>You are not advised to use the same footerComponent for different ListItemGroups at the same time. Otherwise, the display may be affected.<br>**Atomic service API**: This API can be used in atomic services since API version 13.                          |
| space               | number&nbsp;\|&nbsp;string                          | No  | Yes| Spacing between list items. This parameter only affects the spacing between list items, but not spacing between the header and list items or between the footer and list items.<br>Default value: **0**<br>Unit: vp<br>**NOTE**<br>If this parameter is set to a negative number or a value greater than or equal to the length of the list content area, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| style<sup>10+</sup> | [ListItemGroupStyle](#listitemgroupstyle10) | No  | Yes| Style of the list item group.<br>Default value: ListItemGroupStyle.NONE<br>If this parameter is set to **ListItemGroupStyle.NONE**, no style is applied.<br>When **ListItemGroupStyle.CARD** is used, you are advised to pair it with **ListItemStyle.CARD** from [ListItem](ts-container-listitem.md) to apply the default card style.<br>In the card style, the default specifications for the **ListItemGroup** are as follows: horizontal margin of 12 vp on both left and right sides, and vertical as well as horizontal padding of 4 vp.<br>In the card style, the default focus, hover, press, selected, and disable styles are provided for the list options in the card.<br>**NOTE**<br>When **ListItemStyle.CARD** is set, the **listDirection** attribute of **List** must be **Axis.Vertical**. If **listDirection** is set to **Axis.Horizontal**, the display will be disordered. The default value of [alignListItem](./ts-container-list.md#alignlistitem9) is **ListItemAlign.Center**, which centers the items vertically.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|

## Attributes

### divider

divider(value: [ListDividerOptions](ts-container-list.md#listdivideroptions18) | null)

Sets the style of the divider for the list items. By default, there is no divider.

strokeWidth, startMargin, and endMargin do not support percentage setting.

When a list item has [polymorphic styles](ts-universal-attributes-polymorphic-style.md) applied, the dividers above and below the pressed child component are not rendered.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [ListDividerOptions](ts-container-list.md#listdivideroptions18)&nbsp;\|&nbsp;null | Yes  | Style of the divider for the list items.<br> Default value: **null**|

### childrenMainSize<sup>12+</sup>

childrenMainSize(value: ChildrenMainSize)

Sets the size information of the child components of a **ListItemGroup** component along the main axis.

> **NOTE**
>
> - The childrenMainSize attribute must be set for the List component to take effect.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type  | Mandatory| Description                           |
| ---------- | ------ | ---- | ------------------------------- |
| value | [ChildrenMainSize](ts-container-scrollable-common.md#childrenmainsize12) | Yes  | This object is used to maintain the size information of child components in the main axis direction.|

## ListItemGroupStyle<sup>10+</sup>

List component card style enumeration.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value | Description            |
| ---- | ---- | ------------------ |
| NONE | 0 | No style.          |
| CARD | 1 | Default card style.|



## Example

### Example 1: Setting a Sticky Header and Footer

This example uses [sticky](ts-container-list.md#sticky9) to implement the header sticking and footer sticking effects.

ListDataSource implements the LazyForEach data source interface [IDataSource](ts-rendering-control-lazyforeach.md#idatasource) to provide child components for List and ListItemGroup through LazyForEach.

<!--code_no_check-->
```ts
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

  // Notify the controller that data has changed.
  notifyDataChange(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    });
  }

  //Modify the first element.
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

<!--code_no_check-->
```ts
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
    Text ('Total' + num + 'lessons')
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

![en-us_image_0000001219864159](figures/en-us_image_listitemgroup.gif)

### Example 2: Setting the Card Style

This example illustrates the card-style effect of the **ListItemGroup** component.

```ts
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
                  Text('Item ' (itemIndex + 1) + 'n group ' (index + 1))
                    .width('100%')
                    .textAlign(TextAlign.Center)
                }
              }
            }, (item: string) => item)
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
![ListItemGroupStyle](figures/listItemGroup2.jpeg)

### Example 3: Setting Header and Footer

This example uses [ComponentContent](../js-apis-arkui-ComponentContent.md#componentcontent-1) to set the header/footer.

For details about **ListDataSource** and the complete code, see [Example 1: Setting a Sticky Header and Footer](#example-1-setting-a-sticky-header-and-footer).

<!--code_no_check-->
```ts
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
  GetHeader() {
    this.header?.update(new HeadBuilderParams(this.item.title));
    return this.header;
  }

  GetFooter() {
    this.footer?.update(new FootBuilderParams(this.item.projects.length));
    return this.footer;
  }

  build() {
    ListItemGroup({
      headerComponent: this.GetHeader(),
      footerComponent: this.GetFooter()
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
          title: 'Monday after update',
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

This example shows how to use ListItemGroup in a multi-column layout. You can set the [lanes](./ts-container-list.md#lanes9) attribute of the List component to implement a multi-column layout.

For details about ListDataSource and the complete code, see [Example 1: Setting a Sticky Header and Footer](#example-1-setting-a-sticky-header-and-footer).

<!--code_no_check-->
```ts
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

  GetHeader() {
    this.header?.update(new HeadBuilderParams(this.item.title));
    return this.header;
  }

  GetFooter() {
    this.footer?.update(new FootBuilderParams(this.item.projects.length));
    return this.footer;
  }

  build() {
    ListItemGroup({
      headerComponent: this.GetHeader(),
      footerComponent: this.GetFooter()
    }) {
      LazyForEach(this.itemArr, (project: string) => {
        ListItem() {
          //Modify the ListItem style to adapt to the multi-column layout.
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
      .lanes(3) // Set the layout to three columns.
      .alignListItem(ListItemAlign.Center) // Align items in the cross axis.
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


