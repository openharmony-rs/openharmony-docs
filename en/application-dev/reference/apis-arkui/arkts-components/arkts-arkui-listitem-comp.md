# ListItem

The ListItem component displays specific items in the list. It must be used together with List.

> **NOTE** > > - This component is supported since API version 7. Updates will be marked with a superscript to indicate > their earliest API version. > > - The parent of this component can only be List or ListItemGroup. > > - When this component is used with LazyForEach, its child components are created when it is created. > When this component is used with if/else or ForEach, or when the parent component is List or ListItemGroup, > its child components are created when it is laid out.

## Child Components

This component can contain a single child component.

## ListItem

```TypeScript
ListItem(value?: ListItemOptions)
```

Creates a ListItem component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ListItemOptions](arkts-arkui-listitem-comp-listitemoptions-i.md) | No |  |

## ListItem

```TypeScript
ListItem(value?: string)
```

Creates a ListItem component.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** listItem/ListItemInterface

**Model restriction:** This API can be used in both the stage model and FA model.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | No |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ListItemOptions](arkts-arkui-listitem-comp-listitemoptions-i.md) | Defines ListItem component configuration options. |
| [SwipeActionItem](arkts-arkui-listitem-comp-swipeactionitem-i.md) | Describes the swipe action item. For a list in vertical layout, it refers to the delete option displayed on the left (or right) of the list item when the list item is swiped right (or left). |
| [SwipeActionOptions](arkts-arkui-listitem-comp-swipeactionoptions-i.md) | The top layer of the @builder function corresponding to start and end must be a single component. Otherwise, undefined behavior occurs. If the top layer of the @builder function is a statement such as if/else or ForEach, ensure that these statements can generate a single component. |

### Enums

| Name | Description |
| --- | --- |
| [EditMode](arkts-arkui-listitem-comp-editmode-e.md) | Enumerates the edit modes of list items. |
| [ListItemStyle](arkts-arkui-listitem-comp-listitemstyle-e.md) | Enumerates the card styles of the List component. |
| [ListItemSwipeActionDirection](arkts-arkui-listitem-comp-listitemswipeactiondirection-e.md) | Enumerates the swipe action menu display directions for ListItem components. |
| [Sticky](arkts-arkui-listitem-comp-sticky-e.md) | Enumerates the sticky effects for list items. |
| [SwipeActionState](arkts-arkui-listitem-comp-swipeactionstate-e.md) | Enumerates swipe states of list items. |
| [SwipeEdgeEffect](arkts-arkui-listitem-comp-swipeedgeeffect-e.md) | Enumerates the edge effects. |

## Examples

### Example 1: Creating a List Item

This example demonstrates the basic usage of creating a list item.



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

### Example 2: Setting the Swipe Action Item

This example shows how to set the swipe action item for a list item using swipeAction.



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

### Example 3: Applying a Card-style Effect

This example illustrates the card-style effect of the ListItem component.



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

### Example 4: Setting the Swipe Action Item Using ComponentContent

This example demonstrates how to set the action items displayed during swipe operations in ListItem using ComponentContent.



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

### Example 5: Managing the Swipe Action Menu Through ListItemSwipeActionManager

This example demonstrates how to manage the swipe action menu of a list item using [ListItemSwipeActionManager](arkts-arkui-listitem-comp-listitemswipeactionmanager-c.md), available since API version 21.

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
