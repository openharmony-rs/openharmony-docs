# ListItem

ListItem用于展示列表中的具体列表项，支持设置划出菜单、选中状态、鼠标框选和卡片样式等能力，必须配合List组件使用，适用于需要在列表中展示内容并对单个列表项进行交互操作（如滑动删除、选中标记）的场景。
> **说明：** > > - 该组件的父组件只能是List或者ListItemGroup。 > > - 当ListItem配合[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，ListItem子组件在 > ListItem创建时创建。配合[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或父组件为List/ListItemGroup时，ListItem子组 > 件在ListItem布局时创建。

## 子组件

可以包含单个子组件。

## ListItem

```TypeScript
ListItem(value?: ListItemOptions)
```

创建ListItem组件。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ListItemOptions](arkts-arkui-listitemoptions-i.md) | 否 |  |

## ListItem

```TypeScript
ListItem(value?: string)
```

创建ListItem组件。

> **说明：**
> 
> 从API version 7开始支持，从API version 10开始废弃。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** listItem/ListItemInterface

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 否 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ListItemOptions](arkts-arkui-listitemoptions-i.md) | ListItem组件参数。 |
| [SwipeActionItem](arkts-arkui-swipeactionitem-i.md) | SwipeActionItem用于配置[SwipeActionOptions](arkts-arkui-swipeactionoptions-i.md)中的start或end划出项，包括划出时显示的操作项、长距离操作区域的距离阈值，以及进入、退出长距离操作 区域、抬手触发操作和状态变化时的回调。作为start划出项时，List为垂直布局时显示在ListItem左侧，List为水平布局时显示在ListItem上方；作为end划出项时，List为垂直布局时显示在ListItem右侧，List为水平布局时显示在ListItem下 方。 |
| [SwipeActionOptions](arkts-arkui-swipeactionoptions-i.md) | start和end对应的@builder函数中顶层必须是单个组件（如果顶层是if/else、ForEach等渲染控制语句，则必须保证其仅能生成单个组件），否则会引发未定义行为。滑动手势只在ListItem区域上生效，如果子组件滑出ListItem区域外，在ListItem以外部分不会响应滑动手势。所以在多列模式下，建议不要将划出组件设置太宽。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EditMode](arkts-arkui-editmode-e.md) | ListItem元素编辑模式枚举。 |
| [ListItemStyle](arkts-arkui-listitemstyle-e.md) | ListItem组件卡片样式枚举。 |
| [ListItemSwipeActionDirection](arkts-arkui-listitemswipeactiondirection-e.md) | ListItem划出菜单的展开方向。 |
| [Sticky](arkts-arkui-sticky-e.md) | ListItem吸顶效果枚举。 |
| [SwipeActionState](arkts-arkui-swipeactionstate-e.md) | 列表项滑动状态枚举。 |
| [SwipeEdgeEffect](arkts-arkui-swipeedgeeffect-e.md) | 滑动效果枚举。 |

## 示例

该示例实现了创建ListItem的基本用法。

```TypeScript
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
        }, (item: number) => item.toString())
      }.width('90%')
      .scrollBar(BarState.Off)
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

该示例展示了ListItem设置了swipeAction的横滑效果。

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ListItemExample2 {
  @State arr: number[] = [0, 1, 2, 3, 4];
  @State enterEndDeleteAreaString: string = 'not enterEndDeleteArea';
  @State exitEndDeleteAreaString: string = 'not exitEndDeleteArea';
  private scroller: ListScroller = new ListScroller();

  @Builder
  itemEnd() {
    Row() {
      Button('Delete').margin(4)
      Button('Set').margin(4).onClick(() => {
        try {
          this.scroller.closeAllSwipeActions();
        } catch (error) {
          console.error(`Failed to close all swipe actions. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
        }
      })
    }.padding(4).justifyContent(FlexAlign.SpaceEvenly)
  }

  build() {
    Column() {
      List({ space: 10, scroller: this.scroller }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('item' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
          .transition(TransitionEffect.OPACITY)
          .swipeAction({
            end: {
              builder: () => {
                this.itemEnd()
              },
              onAction: () => {
                this.getUIContext()?.animateTo({ duration: 1000 }, () => {
                  let index = this.arr.indexOf(item);
                  this.arr.splice(index, 1);
                });
              },
              actionAreaDistance: 56,
              onEnterActionArea: () => {
                this.enterEndDeleteAreaString = 'enterEndDeleteArea';
                this.exitEndDeleteAreaString = 'not exitEndDeleteArea';
              },
              onExitActionArea: () => {
                this.enterEndDeleteAreaString = 'not enterEndDeleteArea';
                this.exitEndDeleteAreaString = 'exitEndDeleteArea';
              }
            }
          })
        }, (item: number) => item.toString())
      }

      Text(this.enterEndDeleteAreaString).fontSize(20)
      Text(this.exitEndDeleteAreaString).fontSize(20)
    }
    .padding(10)
    .backgroundColor(0xDCDCDC)
    .width('100%')
    .height('100%')
  }
}
```

该示例展示了ListItem的卡片样式效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct ListItemExample3 {
  build() {
    Column() {
      List({ space: 4, initialIndex: 0 }) {
        ListItemGroup({ style: ListItemGroupStyle.CARD }) {
          ForEach([ListItemStyle.CARD, ListItemStyle.CARD, ListItemStyle.NONE], (itemStyle: ListItemStyle, index?: number) => {
            ListItem({ style: itemStyle }) {
              Text('' + index)
                .width('100%')
                .textAlign(TextAlign.Center)
            }
          })
        }

        ForEach([ListItemStyle.CARD, ListItemStyle.CARD, ListItemStyle.NONE], (itemStyle: ListItemStyle, index?: number) => {
          ListItem({ style: itemStyle }) {
            Text('' + index)
              .width('100%')
              .textAlign(TextAlign.Center)
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
```

该示例通过ComponentContent设置ListItem中的划出组件操作时显示的操作项。

```TypeScript
// xxx.ets
import { ComponentContent } from '@kit.ArkUI';

class BuilderParams {
  text: string | Resource;
  scroller: ListScroller;

  constructor(text: string | Resource, scroller: ListScroller) {
    this.text = text;
    this.scroller = scroller;
  }
}

@Builder
function itemBuilder(params: BuilderParams) {
  Row() {
    Button(params.text).margin(4)
    Button('Set').margin(4).onClick(() => {
      params.scroller.closeAllSwipeActions();
    })
  }.padding(4).justifyContent(FlexAlign.SpaceEvenly)
}

@Component
struct MyListItem {
  scroller: ListScroller = new ListScroller();
  @State arr: number[] = [0, 1, 2, 3, 4];
  @State project: number = 0;
  startBuilder?: ComponentContent<BuilderParams> = undefined;
  endBuilder?: ComponentContent<BuilderParams> = undefined;
  builderParam = new BuilderParams('delete', this.scroller);

  aboutToAppear(): void {
    this.startBuilder = new ComponentContent(this.getUIContext(), wrapBuilder(itemBuilder), this.builderParam);
    this.endBuilder = new ComponentContent(this.getUIContext(), wrapBuilder(itemBuilder), this.builderParam);
  }

  getStartBuilder() {
    this.startBuilder?.update(new BuilderParams('StartDelete', this.scroller));
    return this.startBuilder;
  }

  getEndBuilder() {
    this.endBuilder?.update(new BuilderParams('EndDelete', this.scroller));
    return this.endBuilder;
  }

  build() {
    ListItem() {
      Text('item' + this.project)
        .width('100%')
        .height(100)
        .fontSize(16)
        .textAlign(TextAlign.Center)
        .borderRadius(10)
        .backgroundColor(0xFFFFFF)
    }
    .transition(TransitionEffect.OPACITY)
    .swipeAction({
      end: {
        builderComponent: this.getEndBuilder(),
        onAction: () => {
          this.getUIContext()?.animateTo({ duration: 1000 }, () => {
            let index = this.arr.indexOf(this.project);
            this.arr.splice(index, 1);
          });
        },
        actionAreaDistance: 56
      },
      start: {
        builderComponent: this.getStartBuilder(),
        onAction: () => {
          this.getUIContext()?.animateTo({ duration: 1000 }, () => {
            let index = this.arr.indexOf(this.project);
            this.arr.splice(index, 1);
          });
        },
        actionAreaDistance: 56
      }
    })
    .padding(5)
  }
}

@Entry
@Component
struct ListItemExample {
  @State arr: number[] = [0, 1, 2, 3, 4];
  private scroller: ListScroller = new ListScroller();

  build() {
    Column() {
      List({ space: 10, scroller: this.scroller }) {
        ListItemGroup() {
          ForEach(this.arr, (project: number) => {
            MyListItem({ scroller: this.scroller, project: project, arr: this.arr })
          }, (item: number) => item.toString())
        }
      }
    }
    .padding(10)
    .backgroundColor(0xDCDCDC)
    .width('100%')
    .height('100%')
  }
}
```

从API version 21开始，该示例通过[ListItemSwipeActionManager](arkts-arkui-listitemswipeactionmanager-c.md)管理ListItem的划出菜单。

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ListItemExample5 {
  @Builder
  itemAction(str: string) {
    Row() {
      Button(str).margin(4)
    }.padding(4).justifyContent(FlexAlign.SpaceEvenly)
  }

  build() {
    Flex({ wrap: FlexWrap.Wrap }) {
      Flex({ wrap: FlexWrap.Wrap, justifyContent: FlexAlign.SpaceBetween }) {
        Button('expand start')
          .onClick(() => {
            try {
              let node: FrameNode | null = this.getUIContext().getAttachedFrameNodeById('listItem');
              if (!node) {
                return;
              }
              ListItemSwipeActionManager.expand(node, ListItemSwipeActionDirection.START);
            } catch (error) {
              console.error(`Error expand item. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
            }
          })
        Button('expand end')
          .onClick(() => {
            try {
              let node: FrameNode | null = this.getUIContext().getAttachedFrameNodeById('listItem');
              if (!node) {
                return;
              }
              ListItemSwipeActionManager.expand(node, ListItemSwipeActionDirection.END);
            } catch (error) {
              console.error(`Error expand item. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
            }
          })
        Button('collapse')
          .onClick(() => {
            try {
              let node: FrameNode | null = this.getUIContext().getAttachedFrameNodeById('listItem');
              if (!node) {
                return;
              }
              ListItemSwipeActionManager.collapse(node);
            } catch (error) {
              console.error(`Error collapse item. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
            }
          })
      }
      .margin({ bottom: 10 })

      List({ space: 10 }) {
        ListItem() {
          Text('item')
            .width('100%')
            .height(100)
            .fontSize(16)
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
        }
        .id('listItem')
        .transition(TransitionEffect.OPACITY)
        .swipeAction({
          start: {
            builder: () => {
              this.itemAction('start')
            },
          },
          end: {
            builder: () => {
              this.itemAction('end')
            },
          }
        })
      }
      .height('80%')

    }
    .padding(10)
    .backgroundColor(0xDCDCDC)
    .width('100%')
    .height('100%')
  }
}
```
