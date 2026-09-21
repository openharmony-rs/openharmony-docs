# Tabs

The **Tabs** component is a container component that allows users to switch between content views through tabs. Each tab page corresponds to a content view.

> **NOTE** > > - > > - Since API version 11, this component supports the safe area avoidance feature. The default value of the > [expandSafeArea]{} > **expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.BOTTOM])**. You can override the default behavior by > rewriting this attribute. For versions earlier than API version 11, you need to manually implement safe area > avoidance together with the **expandSafeArea** attribute.

## Child Components

Only the child component TabContent and rendering control types [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) and [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md) are supported. You are advised not to use custom components as child components. If **if/else** or **ForEach** is used, only **TabContent** can be used as the child component. You are advised not to use custom components as child components.

> **NOTE:** 
> 
> If the child component has the **visibility** attribute set to **None** or **Hidden**, it is hidden but still takes
> up space in the layout.
> 
> When a displayed **Tabs** child component **TabContent** is hidden, it is not destroyed. For details about how to
> implement lazy loading and release on the page, see
> [Example 13](../../../reference/apis-arkui/arkui-ts/ts-container-tabs.md#example-13-implementing-lazy-loading-and-resource-release-of-pages).
> 
> 
> If [height](arkts-arkui-common-comp-commonmethod-c.md#height) is set to **auto** for **Tabs**, the tab height can be
> automatically adjusted based on that of the child component. When [width](arkts-arkui-common-comp-commonmethod-c.md#width)
> is set to **auto**, the tab width can be automatically adjusted based on that of the child component.

## Tabs

```TypeScript
Tabs(options?: TabsOptions)
```

Create a **Tabs** container.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TabsOptions](arkts-arkui-tabs-comp-tabsoptions-i.md) | No | Options of the **Tabs** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BarGridColumnOptions](arkts-arkui-tabs-comp-bargridcolumnoptions-i.md) | Implements a **BarGridColumnOptions** object for setting the visible area of the tab bar in grid mode, including the column margin and gutter, as well as the number of columns occupied by tabs under small, medium, and large screen sizes. |
| [DividerStyle](arkts-arkui-tabs-comp-dividerstyle-i.md) | Describes the divider style. |
| [FloatingTabBarStyle](arkts-arkui-tabs-comp-floatingtabbarstyle-i.md) | Provides an interface for the options for the floating bar mode. |
| [FloatingTabBarWidth](arkts-arkui-tabs-comp-floatingtabbarwidth-i.md) | Provides an interface for the options for the floating bar width of the tab width at different breakpoints. |
| [ScrollableBarModeOptions](arkts-arkui-tabs-comp-scrollablebarmodeoptions-i.md) | Implements a **ScrollableBarModeOptions** object. |
| [TabContentAnimatedTransition](arkts-arkui-tabs-comp-tabcontentanimatedtransition-i.md) | Provides the information about the custom tab switching animation. |
| [TabContentTransitionProxy](arkts-arkui-tabs-comp-tabcontenttransitionproxy-i.md) | Implements the proxy object returned during the execution of the custom switching animation of the **Tabs** component. You can use this object to obtain the start and target pages for the custom tab switching animation. In addition, you can call the **finishTransition** API of this object to notify the **Tabs** component of the ending of the custom animation. |
| [TabsAnimationEvent](arkts-arkui-tabs-comp-tabsanimationevent-i.md) | Describes the animation information of the **Tabs** component. |
| [TabsBreakpointType](arkts-arkui-tabs-comp-tabsbreakpointtype-i.md) | Defines the value type for different Tabs container sizes. |
| [TabsOptions](arkts-arkui-tabs-comp-tabsoptions-i.md) | Provides parameters for configuring the **Tabs** component, including tab positions, the current index of the displayed tab, the **Tabs** controller, and universal attributes for the **TabBar**. |
| [TabsSidebarSearchableOptions](arkts-arkui-tabs-comp-tabssidebarsearchableoptions-i.md) | Defines the options for the searchable sidebar tab bar. |

### Types

| Name | Description |
| --- | --- |
| [CommonModifier](arkts-arkui-tabs-comp-commonmodifier-t.md) | Defines a parameter object for the **Tabs** component. |
| [OnTabsAnimationEndCallback](arkts-arkui-tabs-comp-ontabsanimationendcallback-t.md) | Defines the callback triggered when the tab switching animation ends. |
| [OnTabsAnimationStartCallback](arkts-arkui-tabs-comp-ontabsanimationstartcallback-t.md) | Defines the callback triggered when the tab switching animation starts. |
| [OnTabsContentDidScrollCallback](arkts-arkui-tabs-comp-ontabscontentdidscrollcallback-t.md) | Defines the callback triggered when content in the **Tabs** component scrolls. |
| [OnTabsContentWillChangeCallback](arkts-arkui-tabs-comp-ontabscontentwillchangecallback-t.md) | Defines the callback invoked when a new page is about to be displayed. |
| [OnTabsGestureSwipeCallback](arkts-arkui-tabs-comp-ontabsgestureswipecallback-t.md) | Defines the callback triggered on a frame-by-frame basis during a swipe-based page turn. |
| [TabsCustomContentTransitionCallback](arkts-arkui-tabs-comp-tabscustomcontenttransitioncallback-t.md) | Defines the callback invoked when the custom tab transition animation starts. |
| [TabsSidebarSearchFilterCallback](arkts-arkui-tabs-comp-tabssidebarsearchfiltercallback-t.md) | Search filter callback. |
| [UIMaterial](arkts-arkui-tabs-comp-uimaterial-t.md) | [UIMaterial](arkts-arkui-tabs-comp-uimaterial-t.md) |

### Enums

| Name | Description |
| --- | --- |
| [AnimationMode](arkts-arkui-tabs-comp-animationmode-e.md) | Enumerates the animation modes for switching between tabs. |
| [BarMode](arkts-arkui-tabs-comp-barmode-e.md) | Enumerates layout modes of the tab bar. |
| [BarPosition](arkts-arkui-tabs-comp-barposition-e.md) | Enumerates the positions of the **Tabs** component. |
| [LayoutStyle](arkts-arkui-tabs-comp-layoutstyle-e.md) | Enumerates the tab layout styles of the tab bar when not scrolling in scrollable mode. |
| [TabBarDisplayMode](arkts-arkui-tabs-comp-tabbardisplaymode-e.md) | Enumerates the actual display modes of the tab bar under different Tabs container sizes. This enum is used in [barDisplayModeBreakpoint](arkts-arkui-tabs-comp-attribute.md#bardisplaymodebreakpoint) to specify the display mode for different breakpoint sizes. It is only meaningful when **TabBarStyle** is set to **SIDEBAR_ADAPTABLE** or **SIDEBAR**. |
| [TabBarStyle](arkts-arkui-tabs-comp-tabbarstyle-e.md) | Enumerates the display styles of the tab bar. |
| [TabsCacheMode](arkts-arkui-tabs-comp-tabscachemode-e.md) | Enumerates the caching modes for child components. |
| [TabsNestedScrollMode](arkts-arkui-tabs-comp-tabsnestedscrollmode-e.md) | Enumerates the nested scrolling modes of the **Tabs** component and its parent container. |
| [TabsSidebarDisplayStyle](arkts-arkui-tabs-comp-tabssidebardisplaystyle-e.md) | Enumerates the display styles of the tab side bar. |

## Examples

### Example 1: Setting the Layout Mode of Tab Bar

This example uses [barMode](#barmode) to implement the evenly distributed layout of tabs and the layout by actual length, and demonstrates the scrollable effect when the total length of the tab layout exceeds the total length of the tab bar.



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsExample {
  @State text: string = 'Text';
  @State barMode: BarMode = BarMode.Fixed;

  build() {
    Column() {
      Row() {
        Button('Add Text')
          .width('47%')
          .height(50)
          .onClick((event?: ClickEvent) => {
            this.text += 'Add Text';
          })
          .margin({ right: '6%', bottom: '12vp' })

        Button('Reset text')
          .width('47%')
          .height(50)
          .onClick((event?: ClickEvent) => {
            this.text = 'Text';
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('BarMode.Fixed')
          .width('47%')
          .height(50)
          .onClick((event?: ClickEvent) => {
            this.barMode = BarMode.Fixed;
          })
          .margin({ right: '6%', bottom: '12vp' })

        Button('BarMode.Scrollable')
          .width('47%')
          .height(50)
          .onClick((event?: ClickEvent) => {
            this.barMode = BarMode.Scrollable;
          })
          .margin({ bottom: '12vp' })
      }

      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar(SubTabBarStyle.of(this.text))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar(SubTabBarStyle.of(this.text))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Blue)
        }.tabBar(SubTabBarStyle.of(this.text))
      }
      .height('60%')
      .backgroundColor(0xf1f3f5)
      .barMode(this.barMode) // Set the layout mode of the tab bar.
    }
    .width('100%')
    .height(500)
    .padding('24vp')
  }
}
```

### Example 2: Setting the Layout Style for a Scrollable TabBar

This example implements the ScrollableBarModeOptions parameter of [barMode](#barmode10-1), which is valid only in Scrollable mode.



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsExample6 {
  private controller: TabsController = new TabsController();
  @State scrollMargin: number = 0;
  @State layoutStyle: LayoutStyle = LayoutStyle.ALWAYS_CENTER;
  @State text: string = 'Text';

  build() {
    Column() {
      Row() {
        Button('scrollMargin+10 ' + this.scrollMargin)
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.scrollMargin += 10;
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('scrollMargin-10 ' + this.scrollMargin)
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.scrollMargin -= 10;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('Add Text')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.text += 'Add Text';
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('Reset text')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.text = 'Text';
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('layoutStyle.ALWAYS_CENTER')
          .width('100%')
          .height(50)
          .margin({ top: 5 })
          .fontSize(15)
          .onClick((event?: ClickEvent) => {
            this.layoutStyle = LayoutStyle.ALWAYS_CENTER;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('layoutStyle.ALWAYS_AVERAGE_SPLIT')
          .width('100%')
          .height(50)
          .margin({ top: 5 })
          .fontSize(15)
          .onClick((event?: ClickEvent) => {
            this.layoutStyle = LayoutStyle.ALWAYS_AVERAGE_SPLIT;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('layoutStyle.SPACE_BETWEEN_OR_CENTER')
          .width('100%')
          .height(50)
          .margin({ top: 5 })
          .fontSize(15)
          .onClick((event?: ClickEvent) => {
            this.layoutStyle = LayoutStyle.SPACE_BETWEEN_OR_CENTER;
          })
          .margin({ bottom: '12vp' })
      }

      Tabs({ barPosition: BarPosition.End, controller: this.controller }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar(SubTabBarStyle.of(this.text))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar(SubTabBarStyle.of(this.text))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Blue)
        }.tabBar(SubTabBarStyle.of(this.text))
      }
      .animationDuration(300)
      .height('60%')
      .backgroundColor(0xf1f3f5)
      .barMode(BarMode.Scrollable, { margin: this.scrollMargin, nonScrollableLayoutStyle: this.layoutStyle }) // Set the layout style of tab bar in Scrollable mode.
    }
    .width('100%')
    .height(500)
    .margin({ top: 5 })
    .padding('24vp')
  }
}
```

### Example 3: Implementing Custom Tab Switching Synchronization

This example uses [onAnimationStart](#onanimationstart11) and [onChange](#onchange) to implement the linkage between the custom tab bar and tab content during switching.



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsExample {
  @State fontColor: string = '#182431';
  @State selectedFontColor: string = '#007DFF';
  @State currentIndex: number = 0;
  @State selectedIndex: number = 0;
  private controller: TabsController = new TabsController();

  @Builder tabBuilder(index: number, name: string) {
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
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar(this.tabBuilder(0, 'green'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar(this.tabBuilder(1, 'blue'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar(this.tabBuilder(2, 'yellow'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar(this.tabBuilder(3, 'pink'))
      }
      .vertical(false)
      .barMode(BarMode.Fixed)
      .barWidth(360)
      .barHeight(56)
      .animationDuration(400) // Set the Tabs page switching animation duration to 400 ms.
      .onChange((index: number) => {
        // currentIndex controls the tab displayed by TabContent.
        this.currentIndex = index;
        this.selectedIndex = index;
      })
      .onAnimationStart((index: number, targetIndex: number, event: TabsAnimationEvent) => {
        if (index === targetIndex) {
          return;
        }
        // selectedIndex controls the text color switching in the custom tab bar.
        this.selectedIndex = targetIndex;
      })
      .width(360)
      .height(296)
      .margin({ top: 52 })
      .backgroundColor('#F1F3F5')
    }.width('100%')
  }
}
```

### Example 4: Setting the Basic Attributes of the Divider

This example uses [divider](#divider10) to demonstrate various attributes of the divider.



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsDivider1 {
  private controller1: TabsController = new TabsController();
  @State dividerColor: string = 'red';
  @State strokeWidth: number = 2;
  @State startMargin: number = 0;
  @State endMargin: number = 0;
  @State nullFlag: boolean = false;

  build() {
    Column() {
      Tabs({ controller: this.controller1 }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar('pink')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Yellow)
        }.tabBar('yellow')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Blue)
        }.tabBar('blue')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar('green')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Red)
        }.tabBar('red')
      }
      .vertical(true)
      .scrollable(true)
      .barMode(BarMode.Fixed)
      .barWidth(70)
      .barHeight(200)
      .animationDuration(400)
      .onChange((index: number) => {
        console.info(index.toString());
      })
      .height('200vp')
      .margin({ bottom: '12vp' })
      .divider(this.nullFlag ? null : {
        strokeWidth: this.strokeWidth,
        color: this.dividerColor,
        startMargin: this.startMargin,
        endMargin: this.endMargin
      }) // Set the divider style.

      Button('Regular Divider').width('100%').margin({ bottom: '12vp' })
        .onClick(() => {
          this.nullFlag = false;
          this.strokeWidth = 2;
          this.dividerColor = 'red';
          this.startMargin = 0;
          this.endMargin = 0;
        })
      Button('Empty Divider').width('100%').margin({ bottom: '12vp' })
        .onClick(() => {
          this.nullFlag = true;
        })
      Button('Change to Blue').width('100%').margin({ bottom: '12vp' })
        .onClick(() => {
          this.dividerColor = 'blue';
        })
      Button('Increase Width').width('100%').margin({ bottom: '12vp' })
        .onClick(() => {
          this.strokeWidth += 2;
        })
      Button('Decrease Width').width('100%').margin({ bottom: '12vp' })
        .onClick(() => {
          if (this.strokeWidth > 2) {
            this.strokeWidth -= 2;
          }
        })
      Button('Increase Top Margin').width('100%').margin({ bottom: '12vp' })
        .onClick(() => {
          this.startMargin += 2;
        })
      Button('Decrease Top Margin').width('100%').margin({ bottom: '12vp' })
        .onClick(() => {
          if (this.startMargin > 2) {
            this.startMargin -= 2;
          }
        })
      Button('Increase Bottom Margin').width('100%').margin({ bottom: '12vp' })
        .onClick(() => {
          this.endMargin += 2;
        })
      Button('Decrease Bottom Margin').width('100%').margin({ bottom: '12vp' })
        .onClick(() => {
          if (this.endMargin > 2) {
            this.endMargin -= 2;
          }
        })
    }.padding({ top: '24vp', left: '24vp', right: '24vp' })
  }
}
```

### Example 5: Setting Tab Bar Fading

This example uses [fadingEdge](#fadingedge10) to implement fading and non-fading when switching child tabs.



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsOpaque {
  private controller: TabsController = new TabsController();
  private controller1: TabsController = new TabsController();
  @State selfFadingFade: boolean = true;

  build() {
    Column() {
      Button('Set Tab to Fade').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          this.selfFadingFade = true;
        })
      Button('Set Tab Not to Fade').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          this.selfFadingFade = false;
        })
      Tabs({ barPosition: BarPosition.End, controller: this.controller }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar('pink')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Yellow)
        }.tabBar('yellow')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Blue)
        }.tabBar('blue')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar('green')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar('green')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar('green')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar('green')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar('green')
      }
      .vertical(false)
      .scrollable(true)
      .barMode(BarMode.Scrollable)
      .barHeight(80)
      .animationDuration(400)
      .onChange((index: number) => {
        console.info(index.toString());
      })
      .fadingEdge(this.selfFadingFade) // Set whether tabs fade out when they exceed the container width
      .height('30%')
      .width('100%')

      Tabs({ barPosition: BarPosition.Start, controller: this.controller1 }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar('pink')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Yellow)
        }.tabBar('yellow')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Blue)
        }.tabBar('blue')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar('green')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar('green')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar('green')
      }
      .vertical(true)
      .scrollable(true)
      .barMode(BarMode.Scrollable)
      .barHeight(200)
      .barWidth(80)
      .animationDuration(400)
      .onChange((index: number) => {
        console.info(index.toString());
      })
      .fadingEdge(this.selfFadingFade)
      .height('30%')
      .width('100%')
    }
    .padding({ top: '24vp', left: '24vp', right: '24vp' })
  }
}
```

### Example 6: Implementing TabBar Overlay on TabContent

This example uses [barOverlap](#baroverlap10) to set whether the tab bar is blurred behind and overlays the TabContent.



```TypeScript
// xxx.ets
@Entry
@Component
struct barHeightTest {
  @State arr: number[] = [0, 1, 2, 3];
  @State barOverlap: boolean = true;

  build() {
    Column() {
      Text(`barOverlap ${this.barOverlap}`).fontSize(16)
      Button('Change barOverlap').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          if (this.barOverlap) {
            this.barOverlap = false;
          } else {
            this.barOverlap = true;
          }
        })

      Tabs({ barPosition: BarPosition.End }) {
        TabContent() {
          Column() {
            List({ space: 10 }) {
              ForEach(this.arr, (item: number) => {
                ListItem() {
                  Text('item' + item).width('80%').height(200).fontSize(16).textAlign(TextAlign.Center).backgroundColor('#fff8b81e')
                }
              }, (item: string) => item)
            }.width('100%').height('100%')
            .lanes(2).alignListItem(ListItemAlign.Center)
          }.width('100%').height('100%')
          .backgroundColor(Color.Pink)
        }
        .tabBar(new BottomTabBarStyle($r('sys.media.ohos_icon_mask_svg'), 'Test 0'))
      }
      .scrollable(false)
      .height('60%')
      .barOverlap(this.barOverlap) // Set whether the tab bar is blurred behind and overlays the TabContent.
    }
    .height(500)
    .padding({ top: '24vp', left: '24vp', right: '24vp' })
  }
}
```

### Example 7: Setting the Visible Area for the Tab Bar in Responsive Grid Mode

This example uses [barGridAlign](arkts-arkui-tabs-comp-attribute.md#bargridalign) to set the visible area of the tab bar in a grid-based manner.



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsExample5 {
  private controller: TabsController = new TabsController();
  @State gridMargin: number = 10;
  @State gridGutter: number = 10;
  @State sm: number = -2;
  @State clickedContent: string = '';

  build() {
    Column() {
      Row() {
        Button('gridMargin+10 ' + this.gridMargin)
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.gridMargin += 10;
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('gridMargin-10 ' + this.gridMargin)
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.gridMargin -= 10;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('gridGutter+10 ' + this.gridGutter)
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.gridGutter += 10;
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('gridGutter-10 ' + this.gridGutter)
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.gridGutter -= 10;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('sm+2 ' + this.sm)
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.sm += 2;
          })
          .margin({ right: '6%' })
        Button('sm-2 ' + this.sm).width('47%').height(50).margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.sm -= 2;
          })
      }

      Text('Tapped content:' + this.clickedContent).width('100%').height(200).margin({ top: 5 })


      Tabs({ barPosition: BarPosition.End, controller: this.controller }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar(BottomTabBarStyle.of($r('sys.media.ohos_app_icon'), '1'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar(BottomTabBarStyle.of($r('sys.media.ohos_app_icon'), '2'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Blue)
        }.tabBar(BottomTabBarStyle.of($r('sys.media.ohos_app_icon'), '3'))
      }
      .width('350vp')
      .animationDuration(300)
      .height('60%')
      .barGridAlign({ sm: this.sm, margin: this.gridMargin, gutter: this.gridGutter }) // Set the visible area of the tab bar in a grid-based manner.
      .backgroundColor(0xf1f3f5)
      .onTabBarClick((index: number) => {
        this.clickedContent += 'now index ' + index + ' is clicked\n';
      })
    }
    .width('100%')
    .height(500)
    .margin({ top: 5 })
    .padding('10vp')
  }
}
```

### Example 8: Implementing a Custom Tab Switching Animation

In this example, the [customContentTransition](#customcontenttransition11) API is used to define a custom switching animation for the Tabs page.



```TypeScript
// xxx.ets
interface itemType {
  text: string,
  backgroundColor: Color
}

@Entry
@Component
struct TabsCustomAnimationExample {
  @State data: itemType[] = [
    {
      text: 'Red',
      backgroundColor: Color.Red
    },
    {
      text: 'Yellow',
      backgroundColor: Color.Yellow
    },
    {
      text: 'Blue',
      backgroundColor: Color.Blue
    }];
  @State opacityList: number[] = [];
  @State scaleList: number[] = [];

  private durationList: number[] = [];
  private timeoutList: number[] = [];
  private customContentTransition: (from: number, to: number) => TabContentAnimatedTransition = (from: number, to: number) => {
    let tabContentAnimatedTransition = {
      timeout: this.timeoutList[from],
      transition: (proxy: TabContentTransitionProxy) => {
        this.scaleList[from] = 1.0;
        this.scaleList[to] = 0.5;
        this.opacityList[from] = 1.0;
        this.opacityList[to] = 0.5;
        this.getUIContext()?.animateTo({
          duration: this.durationList[from],
          onFinish: () => {
            proxy.finishTransition();
          }
        }, () => {
          this.scaleList[from] = 0.5;
          this.scaleList[to] = 1.0;
          this.opacityList[from] = 0.5;
          this.opacityList[to] = 1.0;
        });
      }
    } as TabContentAnimatedTransition;
    return tabContentAnimatedTransition;
  };

  aboutToAppear(): void {
    let duration = 1000;
    let timeout = 1000;
    for (let i = 1; i <= this.data.length; i++) {
      this.opacityList.push(1.0);
      this.scaleList.push(1.0);
      this.durationList.push(duration * i);
      this.timeoutList.push(timeout * i);
    }
  }

  build() {
    Column() {
      Tabs() {
        ForEach(this.data, (item: itemType, index: number) => {
          TabContent() {}
          .tabBar(item.text)
          .backgroundColor(item.backgroundColor)
          // Customize the animation to change opacity, scale pages, and so on.
          .opacity(this.opacityList[index])
          .scale({ x: this.scaleList[index], y: this.scaleList[index] })
        })
      }
      .backgroundColor(0xf1f3f5)
      .width('100%')
      .height(500)
      .customContentTransition(this.customContentTransition) // Set the custom Tabs page switching animation.
    }
  }
}
```

### Example 9: Implementing Tab Switching Interception

This example implements custom interception of page switching via gesture swiping through [onContentWillChange](#oncontentwillchange12).



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsExample {
  @State selectedIndex: number = 2;
  @State currentIndex: number = 2;
  private controller: TabsController = new TabsController();

  @Builder tabBuilder(title: string,targetIndex: number) {
    Column(){
      // Replace $r('app.media.star_fill') with the image resource file required.
      // Replace $r('app.media.star') with the image resource file required.
      Image(this.selectedIndex === targetIndex ? $r('app.media.star_fill') : $r('app.media.star'))
        .width(24)
        .height(24)
        .margin({ bottom: 4 })
        .objectFit(ImageFit.Contain)
      Text(title).fontColor(this.selectedIndex === targetIndex ? '#1698CE' : '#6B6B6B')
    }.width('100%')
    .height(50)
    .justifyContent(FlexAlign.Center)
  }
  
  build() {
    Column() {
      Tabs({ barPosition: BarPosition.End, index: this.currentIndex, controller: this.controller }) {
        TabContent() {
          Column(){
            Text('Content of the Home tab')
          }.width('100%').height('100%').backgroundColor('#00CB87').justifyContent(FlexAlign.Center)
        }.tabBar(this.tabBuilder('Home',0))

        TabContent() {
          Column(){
            Text('Discovered content')
          }.width('100%').height('100%').backgroundColor('#007DFF').justifyContent(FlexAlign.Center)
        }.tabBar(this.tabBuilder('Discover',1))

        TabContent() {
          Column(){
            Text('Content of the Recommended tab')
          }.width('100%').height('100%').backgroundColor('#FFBF00').justifyContent(FlexAlign.Center)
        }.tabBar(this.tabBuilder('Recommended',2))

        TabContent() {
          Column(){
            Text('Content of the Me tab')
          }.width('100%').height('100%').backgroundColor('#E67C92').justifyContent(FlexAlign.Center)
        }.tabBar(this.tabBuilder('Me',3))
      }
      .vertical(false)
      .barMode(BarMode.Fixed)
      .barWidth(360)
      .barHeight(60)
      .animationDuration(0)
      .onChange((index: number) => {
        this.currentIndex = index;
        this.selectedIndex = index;
      })
      .width(360)
      .height(600)
      .backgroundColor('#F1F3F5')
      .scrollable(true)
      .onContentWillChange((currentIndex, comingIndex) => {
        // Intercept page switching: return false to block the switch when the target page index is 2, otherwise return true to allow the switch.
        if (comingIndex == 2) {
          return false;
        }
        return true;
      })

      Button('Change Index').width('50%').margin({ top: 20 })
        .onClick(()=>{
          this.currentIndex = (this.currentIndex + 1) % 4;
        })

      Button('changeIndex').width('50%').margin({ top: 20 })
        .onClick(()=>{
          this.currentIndex = (this.currentIndex + 1) % 4;
          this.controller.changeIndex(this.currentIndex);
        })
    }.width('100%')
  }
}
```

### Example 10: Customizing the Tab Bar Switching Animation

This example implements the switching animation of a custom tab bar through APIs such as [onChange](#onchange), [onAnimationStart](#onanimationstart11), [onAnimationEnd](#onanimationend11), and [onGestureSwipe](#ongestureswipe11).

```TypeScript
// EntryAbility.ets
import { Configuration, UIAbility } from '@kit.AbilityKit';
import { i18n } from '@kit.LocalizationKit';
import { CommonUtil } from '../common/CommonUtil';

export default class EntryAbility extends UIAbility {
  onConfigurationUpdate(newConfig: Configuration): void {
    // Listen for system configuration changes.
    if (newConfig.language) {
      CommonUtil.setIsRTL(i18n.isRTL(newConfig.language));
    }
  }
}
```

```TypeScript
// CommonUtil.ets
export class CommonUtil {
  private static isRTL: boolean = false;

  public static setIsRTL(isRTL: boolean): void {
    CommonUtil.isRTL = isRTL;
  }

  public static getIsRTL(): boolean {
    return CommonUtil.isRTL;
  }
}
```



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';
import { CommonUtil } from '../common/CommonUtil';

@Entry
@Component
struct TabsExample {
  @State colorArray: [string, string][] =
    [['green', '#00CB87'], ['blue', '#007DFF'], ['yellow', '#FFBF00'], ['pink', '#E67C92']];
  @State currentIndex: number = 0;
  @State animationDuration: number = 300;
  @State indicatorLeftMargin: number = 0;
  @State indicatorWidth: number = 0;
  private tabsWidth: number = 0;
  private textInfos: [number, number][] = [];
  private isStartAnimateTo: boolean = false;

  aboutToAppear():void {
    for (let i = 0; i < this.colorArray.length; i++) {
      this.textInfos.push([0, 0]);
    }
  }

  @Builder
  tabBuilder(index: number, name: string) {
    Column() {
      Text(name)
        .fontSize(16)
        .fontColor(this.currentIndex === index ? '#007DFF' : '#182431')
        .fontWeight(this.currentIndex === index ? 500 : 400)
        .id(index.toString())
        .onAreaChange((oldValue: Area, newValue: Area) => {
          this.textInfos[index] = [newValue.globalPosition.x as number, newValue.width as number];
          if (!this.isStartAnimateTo && this.currentIndex === index && this.tabsWidth > 0) {
            this.setIndicatorAttr(this.textInfos[this.currentIndex][0], this.textInfos[this.currentIndex][1]);
          }
        })
    }.width('100%')
  }

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Tabs({ barPosition: BarPosition.Start }) {
        ForEach(this.colorArray, (item: [string, string], index:number) => {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor(item[1])
          }.tabBar(this.tabBuilder(index, item[0]))
        })
      }
      .onAreaChange((oldValue: Area, newValue: Area)=> {
        this.tabsWidth = newValue.width as number;
        if (!this.isStartAnimateTo) {
          this.setIndicatorAttr(this.textInfos[this.currentIndex][0], this.textInfos[this.currentIndex][1]);
        }
      })
      .barWidth('100%')
      .barHeight(56)
      .width('100%')
      .height(296)
      .backgroundColor('#F1F3F5')
      .animationDuration(this.animationDuration)
      .onChange((index: number) => {
        // currentIndex controls the tab content displayed by TabContent.
        this.currentIndex = index;
      })
      .onAnimationStart((index: number, targetIndex: number, event: TabsAnimationEvent) => {
        // Triggered when the switching animation starts: update currentIndex to the target index and start the underline animation to follow the page swipe.
        this.currentIndex = targetIndex;
        this.startAnimateTo(this.animationDuration, this.textInfos[targetIndex][0], this.textInfos[targetIndex][1]);
      })
      .onAnimationEnd((index: number, event: TabsAnimationEvent) => {
        // This callback is triggered when the switching animation ends. The underline animation stops.
        let currentIndicatorInfo = this.getCurrentIndicatorInfo(index, event);
        this.startAnimateTo(0, currentIndicatorInfo.left, currentIndicatorInfo.width);
      })
      .onGestureSwipe((index: number, event: TabsAnimationEvent) => {
        // This callback is triggered frame by frame while the page follows the swipe gesture.
        let currentIndicatorInfo = this.getCurrentIndicatorInfo(index, event);
        this.currentIndex = currentIndicatorInfo.index;
        this.setIndicatorAttr(currentIndicatorInfo.left, currentIndicatorInfo.width);
      })

      Column()
        .height(2)
        .width(this.indicatorWidth)
        .margin({ start: LengthMetrics.vp(this.indicatorLeftMargin), top: LengthMetrics.vp(48) })
        .backgroundColor('#007DFF')
    }.width('100%')
  }

  private getCurrentIndicatorInfo(index: number, event: TabsAnimationEvent): Record<string, number> {
    let nextIndex = index;
    if (index > 0 && (CommonUtil.getIsRTL() ? event.currentOffset < 0 : event.currentOffset > 0)) {
      nextIndex--;
    } else if (index < this.textInfos.length - 1 &&
        (CommonUtil.getIsRTL() ? event.currentOffset > 0 : event.currentOffset < 0)) {
      nextIndex++;
    }
    let indexInfo = this.textInfos[index];
    let nextIndexInfo = this.textInfos[nextIndex];
    let swipeRatio = Math.abs(event.currentOffset / this.tabsWidth);
    let currentIndex = swipeRatio > 0.5 ? nextIndex : index; // When the page is swiped more than halfway, the tabBar switches to the next page.
    let currentLeft = indexInfo[0] + (nextIndexInfo[0] - indexInfo[0]) * swipeRatio;
    let currentWidth = indexInfo[1] + (nextIndexInfo[1] - indexInfo[1]) * swipeRatio;
    return { 'index': currentIndex, 'left': currentLeft, 'width': currentWidth };
  }

  private startAnimateTo(duration: number, leftMargin: number, width: number) {
    this.isStartAnimateTo = true;
    this.getUIContext()?.animateTo({
      duration: duration, // Animation duration
      curve: Curve.Linear, // Animation curve
      iterations: 1, // Number of playbacks.
      playMode: PlayMode.Normal, // Animation mode.
      onFinish: () => {
        this.isStartAnimateTo = false;
        console.info('play end');
      }
    }, () => {
      this.setIndicatorAttr(leftMargin, width);
    });
  }

  private setIndicatorAttr(leftMargin: number, width: number) {
    this.indicatorWidth = width;
    if (CommonUtil.getIsRTL()) {
      this.indicatorLeftMargin = this.tabsWidth - leftMargin - width;
    } else {
      this.indicatorLeftMargin = leftMargin;
    }
  }
}
```

### Example 11: Preloading Child Nodes

This example demonstrates how to use the [preloadItems](#preloaditems12) API to preload specified child nodes.

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct TabsPreloadItems {
  @State currentIndex: number = 1;
  private tabsController: TabsController = new TabsController();

  build() {
    Column() {
      Tabs({ index: this.currentIndex, controller: this.tabsController }) {
        TabContent() {
          MyComponent({ color: '#00CB87' })
        }.tabBar(SubTabBarStyle.of('green'))

        TabContent() {
          MyComponent({ color: '#007DFF' })
        }.tabBar(SubTabBarStyle.of('blue'))

        TabContent() {
          MyComponent({ color: '#FFBF00' })
        }.tabBar(SubTabBarStyle.of('yellow'))

        TabContent() {
          MyComponent({ color: '#E67C92' })
        }.tabBar(SubTabBarStyle.of('pink'))
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .onChange((index: number) => {
        this.currentIndex = index;
      })

      Button('preload items: [0, 2, 3]')
        .margin(5)
        .onClick(() => {
          // Preload child nodes 0, 2, and 3 to improve the performance when switching to these nodes by swiping or tapping.
          this.tabsController.preloadItems([0, 2, 3])
            .then(() => {
              console.info('preloadItems success.');
            })
            .catch((error: BusinessError) => {
              console.error('preloadItems failed, error code: ' + error.code + ', error message: ' + error.message);
            })
        })
    }
  }
}

@Component
struct MyComponent {
  private color: string = '';

  aboutToAppear(): void {
    console.info('aboutToAppear backgroundColor:' + this.color);
  }

  aboutToDisappear(): void {
    console.info('aboutToDisappear backgroundColor:' + this.color);
  }

  build() {
    Column()
      .width('100%')
      .height('100%')
      .backgroundColor(this.color)
  }
}
```

### Example 12: Setting Tab Bar Translation and Opacity

This example sets the translation distance and opacity of the tab bar through APIs such as [setTabBarTranslate](arkts-arkui-tabs-comp-tabscontroller-c.md#settabbartranslate) and [setTabBarOpacity](arkts-arkui-tabs-comp-tabscontroller-c.md#settabbaropacity).



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsExample {
  private controller: TabsController = new TabsController();

  build() {
    Column() {
      Button('Set TabBar Translation Distance').margin({ top: 20 })
        .onClick(() => {
          this.controller.setTabBarTranslate({ x: -20, y: -20 }); // Set the tab bar to translate 20 vp left and up
        })

      Button('Set TabBar Opacity').margin({ top: 20 })
        .onClick(() => {
          this.controller.setTabBarOpacity(0.5); // Set the tab bar opacity to 0.5 (semi-transparent).
        })

      Tabs({ barPosition: BarPosition.End, controller: this.controller }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar(BottomTabBarStyle.of($r('app.media.startIcon'), 'green'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar(BottomTabBarStyle.of($r('app.media.startIcon'), 'blue'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar(BottomTabBarStyle.of($r('app.media.startIcon'), 'yellow'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar(BottomTabBarStyle.of($r('app.media.startIcon'), 'pink'))
      }
      .width(360)
      .height(296)
      .margin({ top: 20 })
      .barBackgroundColor('#F1F3F5')
    }
    .width('100%')
  }
}
```

### Example 13: Implementing Lazy Loading and Resource Release of Pages

This example uses a custom [TabBar](ts-container-tabcontent.md#tabbar) and [Swiper](ts-container-swiper.md) together with [LazyForEach](ts-rendering-control-lazyforeach.md) to implement page lazy loading and release.



```TypeScript
// xxx.ets
class MyDataSource implements IDataSource {
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

  unregisterDataChangeListener() {
  }
}

@Entry
@Component
struct TabsSwiperExample {
  @State fontColor: string = '#182431';
  @State selectedFontColor: string = '#007DFF';
  @State currentIndex: number = 0;
  private list: number[] = [];
  private tabsController: TabsController = new TabsController();
  private swiperController: SwiperController = new SwiperController();
  private swiperData: MyDataSource = new MyDataSource([]);

  aboutToAppear(): void {
    for (let i = 0; i <= 9; i++) {
      this.list.push(i);
    }
    this.swiperData = new MyDataSource(this.list);
  }

  @Builder tabBuilder(index: number, name: string) {
    Column() {
      Text(name)
        .fontColor(this.currentIndex === index ? this.selectedFontColor : this.fontColor)
        .fontSize(16)
        .fontWeight(this.currentIndex === index ? 500 : 400)
        .lineHeight(22)
        .margin({ top: 17, bottom: 7 })
      Divider()
        .strokeWidth(2)
        .color('#007DFF')
        .opacity(this.currentIndex === index ? 1 : 0)
    }.width('20%')
  }

  build() {
    Column() {
      Tabs({ barPosition: BarPosition.Start, controller: this.tabsController }) {
        ForEach(this.list, (item: number) => {
          TabContent().tabBar(this.tabBuilder(item, 'Tab ' + this.list[item]))
        })
      }
      .onTabBarClick((index: number) => {
        this.currentIndex = index;
        this.swiperController.changeIndex(index, true);
      })
      .barMode(BarMode.Scrollable)
      .backgroundColor('#F1F3F5')
      .height(56)
      .width('100%')

      Swiper(this.swiperController) {
        LazyForEach(this.swiperData, (item: string) => {
          Text(item.toString())
            .onAppear(()=>{
              console.info('onAppear ' + item.toString());
            })
            .onDisAppear(()=>{
              console.info('onDisAppear ' + item.toString());
            })
            .width('100%')
            .height('100%')
            .backgroundColor(0xAFEEEE)
            .textAlign(TextAlign.Center)
            .fontSize(30)
        }, (item: string) => item)
      }
      .loop(false)
      .onChange((index: number) => {
        this.currentIndex = index;
      })
      .onAnimationStart((index: number, targetIndex: number, extraInfo: SwiperAnimationEvent) => {
        this.currentIndex = targetIndex;
        this.tabsController.changeIndex(targetIndex);
      })
    }
  }
}
```

### Example 14: Implementing the Tab Switching Animation

This example sets the [animationMode](#animationmode12) attribute to implement the page-turning animation.



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsExample {
  @State currentIndex: number = 0;
  @State currentAnimationMode: AnimationMode = AnimationMode.CONTENT_FIRST;
  private controller: TabsController = new TabsController();
  private data: number[] = [];

  aboutToAppear(): void {
    for (let i = 0; i < 10; i++) {
      this.data.push(i);
    }
  }

  @Builder
  tabBuilder(title: string, targetIndex: number) {
    Column() {
      Text(title).fontColor(this.currentIndex === targetIndex ? '#FF0000' : '#6B6B6B')
    }.width('100%')
    .height(50)
    .justifyContent(FlexAlign.Center)
  }

  build() {
    Column() {
      Tabs({ barPosition: BarPosition.End, controller: this.controller, index: this.currentIndex }) {
        ForEach(this.data, (item: number) => {
          TabContent() {
            Column() {
              Text('' + item)
            }.width('100%').height('100%').backgroundColor('#00CB87').justifyContent(FlexAlign.Center)
          }.tabBar(this.tabBuilder('P' + item, item))
        }, (item: number) => item.toString())
      }
      .barWidth(360)
      .barHeight(60)
      .animationMode(this.currentAnimationMode)
      .animationDuration(4000)
      .onChange((index: number) => {
        this.currentIndex = index;
      })
      .width(360)
      .height(120)
      .backgroundColor('#F1F3F5')

      Text('AnimationMode:' + AnimationMode[this.currentAnimationMode])

      Button('AnimationMode').width('50%').margin({ top: 1 }).height(25)
        .onClick(() => {
          if (this.currentAnimationMode === AnimationMode.CONTENT_FIRST) {
            this.currentAnimationMode = AnimationMode.ACTION_FIRST;
          } else if (this.currentAnimationMode === AnimationMode.ACTION_FIRST) {
            this.currentAnimationMode = AnimationMode.NO_ANIMATION;
          } else if (this.currentAnimationMode === AnimationMode.NO_ANIMATION) {
            this.currentAnimationMode = AnimationMode.CONTENT_FIRST_WITH_JUMP;
          } else if (this.currentAnimationMode === AnimationMode.CONTENT_FIRST_WITH_JUMP) {
            this.currentAnimationMode = AnimationMode.ACTION_FIRST_WITH_JUMP;
          } else if (this.currentAnimationMode === AnimationMode.ACTION_FIRST_WITH_JUMP) {
            this.currentAnimationMode = AnimationMode.CONTENT_FIRST;
          }
        })
    }.width('100%')
  }
}
```

### Example 15: Enabling Tabs to Exceed the Tab Bar Area

This example uses the barModifier in [TabsOptions](arkts-arkui-tabs-comp-tabsoptions-i.md) to set the clip attribute of the TabBar to display tabs beyond the tab bar area.

Since API version 15, the barModifier API has been added to TabsOptions.



```TypeScript
// xxx.ets
import { CommonModifier } from '@kit.ArkUI';

@Entry
@Component
struct TabsBarModifierExample {
  @State selectedIndex: number = 2;
  @State currentIndex: number = 2;
  @State isClip: boolean = false;
  @State tabBarModifier: CommonModifier = new CommonModifier();
  private controller: TabsController = new TabsController();

  aboutToAppear(): void {
    this.tabBarModifier.clip(this.isClip);
  }

  @Builder
  tabBuilder(title: string, targetIndex: number) {
    Column() {
      Image($r('app.media.startIcon')).width(30).height(30)
      Text(title).fontColor(this.selectedIndex === targetIndex ? '#1698CE' : '#6B6B6B')
    }.width('100%')
    .height(50)
    .justifyContent(FlexAlign.Center)
    .offset({ y: this.selectedIndex === targetIndex ? -15 : 0 })
  }

  build() {
    Column() {
      Tabs({
        barPosition: BarPosition.End,
        index: this.currentIndex,
        controller: this.controller,
        barModifier: this.tabBarModifier
      }) {
        TabContent() {
          Column() {
            Text('Content of the Home tab')
          }.width('100%').height('100%').backgroundColor('#00CB87').justifyContent(FlexAlign.Center)
        }.tabBar(this.tabBuilder('Home', 0))

        TabContent() {
          Column() {
            Text('Content of the Discover tab')
          }.width('100%').height('100%').backgroundColor('#007DFF').justifyContent(FlexAlign.Center)
        }.tabBar(this.tabBuilder('Discover', 1))

        TabContent() {
          Column() {
            Text('Content of the Recommended tab')
          }.width('100%').height('100%').backgroundColor('#FFBF00').justifyContent(FlexAlign.Center)
        }.tabBar(this.tabBuilder('Recommended', 2))

        TabContent() {
          Column() {
            Text('Content of the Me tab')
          }.width('100%').height('100%').backgroundColor('#E67C92').justifyContent(FlexAlign.Center)
        }.tabBar(this.tabBuilder('Me', 3))
      }
      .vertical(false)
      .barMode(BarMode.Fixed)
      .barWidth(340)
      .barHeight(60)
      .onChange((index: number) => {
        this.currentIndex = index;
        this.selectedIndex = index;
      })
      .width(340)
      .height(400)
      .backgroundColor('#F1F3F5')
      .scrollable(true)

      Button('isClip: ' + this.isClip)
        .margin({ top: 30 })
        .onClick(() => {
          this.isClip = !this.isClip;
          this.tabBarModifier.clip(this.isClip);
        })
    }.width('100%')
  }
}
```

### Example 16: Aligning Tabs

This example uses the barModifier in [TabsOptions](arkts-arkui-tabs-comp-tabsoptions-i.md) to set the align attribute of the TabBar to implement the tab alignment layout effect.

Since API version 15, the barModifier API is added to TabsOptions.



```TypeScript
// xxx.ets
import { CommonModifier } from '@kit.ArkUI';

@Entry
@Component
struct TabsBarModifierExample {
  private controller: TabsController = new TabsController();
  @State text: string = 'Text';
  @State isVertical: boolean = false;
  @State tabBarModifier: CommonModifier = new CommonModifier();

  build() {
    Column() {
      Row() {
        Button('Alignment.Start ')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.tabBarModifier.align(Alignment.Start);
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('Alignment.End')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.tabBarModifier.align(Alignment.End);
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('Alignment.Center')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.tabBarModifier.align(Alignment.Center);
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('isVertical: ' + this.isVertical)
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.isVertical = !this.isVertical;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('Alignment.Top')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.tabBarModifier.align(Alignment.Top);
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('Alignment.Bottom')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.tabBarModifier.align(Alignment.Bottom);
          })
          .margin({ bottom: '12vp' })
      }

      Tabs({ barPosition: BarPosition.End, controller: this.controller, barModifier: this.tabBarModifier }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar(SubTabBarStyle.of(this.text))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar(SubTabBarStyle.of(this.text))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Blue)
        }.tabBar(SubTabBarStyle.of(this.text))
      }
      .vertical(this.isVertical)
      .height('60%')
      .backgroundColor(0xf1f3f5)
      .barMode(BarMode.Scrollable)
    }
    .width('100%')
    .height(500)
    .margin({ top: 5 })
    .padding('24vp')
  }
}
```

### Example 17: Synchronizing Tabs and TabBar Synchronously

This example uses the [onSelected](#onselected18) API to implement synchronized switching between Tabs and TabBar.

Since API version 18, the onSelected API is added.



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsExample {
  @State fontColor: string = '#182431';
  @State selectedFontColor: string = '#007DFF';
  @State currentIndex: number = 0;
  @State selectedIndex: number = 0;
  private controller: TabsController = new TabsController();

  @Builder tabBuilder(index: number, name: string) {
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
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar(this.tabBuilder(0, 'green'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar(this.tabBuilder(1, 'blue'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar(this.tabBuilder(2, 'yellow'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar(this.tabBuilder(3, 'pink'))
      }
      .vertical(false)
      .barMode(BarMode.Fixed)
      .barWidth(360)
      .barHeight(56)
      .animationDuration(400)
      .animationMode(AnimationMode.CONTENT_FIRST)
      .onChange((index: number) => {
        console.info('onChange index:' + index);
        this.currentIndex = index;
      })
      .onSelected((index: number) => {
        console.info('onSelected index:' + index);
        this.selectedIndex = index;
      })
      .onUnselected((index: number) => {
        console.info('onUnselected index:' + index);
      })
      .width('100%')
      .height('100%')
      .backgroundColor('#F1F3F5')
    }.width('100%')
  }
}
```

### Example 18: Releasing the Tabs Child Components

This example releases the child components of Tabs by setting the [cachedMaxCount](arkts-arkui-tabs-comp-attribute.md#cachedmaxcount) attribute.

Since API version 19, the cachedMaxCount API is added.

```TypeScript
@Entry
@Component
struct TabsExample {
  build() {
    Tabs() {
      TabContent() {
        MyComponent({ color: '#00CB87' })
      }.tabBar(SubTabBarStyle.of('green'))

      TabContent() {
        MyComponent({ color: '#007DFF' })
      }.tabBar(SubTabBarStyle.of('blue'))

      TabContent() {
        MyComponent({ color: '#FFBF00' })
      }.tabBar(SubTabBarStyle.of('yellow'))

      TabContent() {
        MyComponent({ color: '#E67C92' })
      }.tabBar(SubTabBarStyle.of('pink'))
    }
    .width(360)
    .height(296)
    .backgroundColor('#F1F3F5')
    .cachedMaxCount(1, TabsCacheMode.CACHE_BOTH_SIDE) // Set a maximum of 3 cached child components (the current page and one on each side).
  }
}

@Component
struct MyComponent {
  private color: string = '';

  aboutToAppear(): void {
    console.info('aboutToAppear backgroundColor:' + this.color);
  }

  aboutToDisappear(): void {
    console.info('aboutToDisappear backgroundColor:' + this.color);
  }

  build() {
    Column()
      .width('100%')
      .height('100%')
      .backgroundColor(this.color)
  }
}
```

### Example 19: Setting the Tab Bar Background Blur Effect

This example sets the background blur style and effect of the tab bar through [barBackgroundBlurStyle](arkts-arkui-tabs-comp-attribute.md#barbackgroundblurstyle) and [barBackgroundEffect](arkts-arkui-tabs-comp-attribute.md#barbackgroundeffect), respectively.

Since API version 18, the barBackgroundBlurStyle and barBackgroundEffect APIs are added.



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsExample {
  build() {
    Column() {
      // barBackgroundBlurStyle can set blur parameters through enum values.
      Stack() {
        Image($r('app.media.startIcon'))
        Tabs() {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor('#00CB87')
          }.tabBar('green')

          TabContent() {
            Column().width('100%').height('100%').backgroundColor('#007DFF')
          }.tabBar('blue')

          TabContent() {
            Column().width('100%').height('100%').backgroundColor('#FFBF00')
          }.tabBar('yellow')

          TabContent() {
            Column().width('100%').height('100%').backgroundColor('#E67C92')
          }.tabBar('pink')
        }
        .barBackgroundBlurStyle(BlurStyle.COMPONENT_THICK,
          { colorMode: ThemeColorMode.LIGHT, adaptiveColor: AdaptiveColor.DEFAULT, scale: 1.0 }) // Set the component thick blur style, light theme, default adaptive color, and scale 1.0.
      }
      .width(300)
      .height(300)
      .margin(10)

      // barBackgroundEffect can be used to customize the blur radius, brightness, saturation, and other parameters of the tabBar.
      Stack() {
        Image($r('app.media.startIcon'))
        Tabs() {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor('#00CB87')
          }.tabBar('green')

          TabContent() {
            Column().width('100%').height('100%').backgroundColor('#007DFF')
          }.tabBar('blue')

          TabContent() {
            Column().width('100%').height('100%').backgroundColor('#FFBF00')
          }.tabBar('yellow')

          TabContent() {
            Column().width('100%').height('100%').backgroundColor('#E67C92')
          }.tabBar('pink')
        }
        .barBackgroundEffect({ radius: 20, brightness: 0.6, saturation: 15 }) // Set the blur radius to 20, brightness to 0.6, and saturation to 15.
      }
      .width(300)
      .height(300)
      .margin(10)
    }
  }
}
```

### Example 20: Setting the Edge Sliding Effect

This example uses [edgeEffect](#edgeeffect12) to implement different edge rebound effects.



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsExample {
  @State edgeEffect: EdgeEffect = EdgeEffect.Spring;

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink')
      }
      .width(360)
      .height(296)
      .margin({ top: 52 })
      .backgroundColor('#F1F3F5')
      .edgeEffect(this.edgeEffect) // Set the edge sliding effect.

      Button('EdgeEffect.Spring').width('50%').margin({ top: 20 })
        .onClick(() => {
          this.edgeEffect = EdgeEffect.Spring; // Set the spring rebound effect.
        })

      Button('EdgeEffect.Fade').width('50%').margin({ top: 20 })
        .onClick(() => {
          this.edgeEffect = EdgeEffect.Fade; // Set the fade effect.
        })

      Button('EdgeEffect.None').width('50%').margin({ top: 20 })
        .onClick(() => {
          this.edgeEffect = EdgeEffect.None; // Set to no edge effect.
        })
    }.width('100%')
  }
}
```

### Example 21: Setting the Tab Switching Animation Curve

This example shows how to set the page switching animation curve of Tabs through the [animationCurve](arkts-arkui-tabs-comp-attribute.md#animationcurve) API, and set the duration of the page switching animation in combination with animationDuration.

Since API version 20, the animationCurve API is added.



```TypeScript
import { curves } from '@kit.ArkUI';

interface TabsItemType {
  text: string,
  backgroundColor: ResourceColor
}

@Entry
@Component
struct TabsExample {
  private tabsController: TabsController = new TabsController();
  private curves: (Curve | ICurve) [] = [
    curves.interpolatingSpring(-1, 1, 328, 34),
    curves.springCurve(10, 1, 228, 30),
    curves.cubicBezierCurve(0.25, 0.1, 0.25, 1.0),
  ];
  private curveNames: string[] = [
    'interpolatingSpring(-1, 1, 328, 34)',
    'springCurve(10, 1, 228, 30)',
    'cubicBezierCurve(0.25, 0.1, 0.25, 1.0)'
  ];
  @State curveIndex: number = 0;
  private data: TabsItemType[] = [
    { text: '1', backgroundColor: '#004AAF' },
    { text: '2', backgroundColor: '#2787D9' },
    { text: '3', backgroundColor: '#D5D5D5' },
    { text: '4', backgroundColor: '#707070' },
    { text: '5', backgroundColor: '#F7F7F7' },
  ];
  @State duration: number = 0;

  build() {
    Column({ space: 2 }) {
      Tabs({ controller: this.tabsController }) {
        ForEach(this.data, (item: TabsItemType, index: number) => {
          TabContent() {
          }
          .tabBar(item.text)
          .backgroundColor(item.backgroundColor)
        })
      }
      .backgroundColor(0xf1f3f5)
      .width('100%')
      .height(500)
      .animationCurve(this.curves[this.curveIndex]) // Set the page switching animation curve.
      .animationDuration(this.duration) // Set the page switching animation duration.

      Column({ space: 2 }) {
        Text('Curve:' + this.curveNames[this.curveIndex])
        Row({ space: 2 }) {
          // Switching animation curve.
          Button('++').onClick(() => {
            this.curveIndex = (this.curveIndex + 1) % this.curves.length;
          })
          Button('reset').onClick(() => {
            this.curveIndex = 0;
          })
        }
      }
      .margin({ left: '10vp' })
      .width('100%')

      Row({ space: 2 }) {
        Text('Duration:' + this.duration)
        // Increase the animation duration.
        Button('+100').onClick(() => {
          this.duration = (this.duration + 100) % 10000;
        })
        Button('+1000').onClick(() => {
          this.duration = (this.duration + 1000) % 10000;
        })
        Button('reset').onClick(() => {
          this.duration = 0;
        })
      }
      .margin({ left: '10vp' })
      .width('100%')
    }
    .margin('10vp')
  }
}
```

### Example 22: Listening for Swipe Events on the Tabs Page

This example shows how to set a callback for Tabs swiping through the [onContentDidScroll](#oncontentdidscroll23) API.

Since API version 23, the onContentDidScroll API is added.

```TypeScript
// xxx.ets
@Entry
@Component
struct TabsDidScrollExample {
  @State fontColor: string = '#182431';
  @State selectedFontColor: string = '#007DFF';
  @State currentIndex: number = 0;
  @State selectedIndex: number = 0;
  @State didScrollStr: string = '';
  private controller: TabsController = new TabsController();

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
      Text('Swipe page to trigger callback')
        .width("80%")
        .fontSize(20)
        .margin(5)
        .textAlign(TextAlign.Center)

      Text(this.didScrollStr)
        .width("80%")
        .fontSize(20)
        .margin(5)
        .textAlign(TextAlign.Center)

      Tabs({ barPosition: BarPosition.Start, index: this.currentIndex, controller: this.controller }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar(this.tabBuilder(0, 'green'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar(this.tabBuilder(1, 'blue'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar(this.tabBuilder(2, 'yellow'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar(this.tabBuilder(3, 'pink'))
      }
      .vertical(false)
      .barMode(BarMode.Fixed)
      .barWidth(360)
      .barHeight(56)
      .animationDuration(400)
      .onChange((index: number) => {
        // Control the tab displayed in TabContent through currentIndex.
        this.currentIndex = index;
        this.selectedIndex = index;
      })
      .onAnimationStart((index: number, targetIndex: number, event: TabsAnimationEvent) => {
        if (index === targetIndex) {
          return;
        }
        // Control the Text color switching in the custom tab bar through selectedIndex.
        this.selectedIndex = targetIndex;
      })
      .width(360)
      .height(296)
      .margin({ top: 15 })
      .backgroundColor('#F1F3F5')
      .onContentDidScroll((selectedIndex: number, index: number, position: number, mainAxisLength: number) => {
        // Listen for the Tabs page sliding event. In this callback, you can implement custom navigation dot switching animations and more.
        console.info("onContentDidScroll selectedIndex: " + selectedIndex + ", index: " + index + ", position: " +
          position + ", mainAxisLength: " + mainAxisLength);
        this.didScrollStr =
          "onContentDidScroll selectedIndex: " + selectedIndex + ", index: " + index + ", position: " +
            position + ", mainAxisLength: " + mainAxisLength
      })
    }.width('100%')
  }
}
```

### Example 23: Implementing Nested Scrolling of Tabs

This example shows how to set the nested scrolling effect of Tabs through the [nestedScroll](#nestedscroll24) API.

Since API version 24, the nestedScroll API is added.

```TypeScript
// xxx.ets
@Entry
@Component
struct TabsExample {
  @State text: string = 'Text';
  @State barMode: BarMode = BarMode.Fixed;
  build() {
    Column() {
      Row() {

        Tabs() {
          TabContent() {
            Tabs() {
              TabContent() {
                Column().width('100%').height('100%').backgroundColor(Color.Blue)
              }.tabBar(SubTabBarStyle.of('Subpage a'))

              TabContent() {
                Column().width('100%').height('100%').backgroundColor(Color.Green)
              }.tabBar(SubTabBarStyle.of('Subpage b'))

              TabContent() {
                Column().width('100%').height('100%').backgroundColor(Color.Pink)
              }.tabBar(SubTabBarStyle.of('Subpage c'))
            }
            .nestedScroll(TabsNestedScrollMode.SELF_FIRST) // Set Tabs to scroll first, and the parent component scrolls after Tabs reaches the edge.
          }.tabBar(SubTabBarStyle.of('Homepage 1'))


          TabContent() {
            Tabs() {
              TabContent() {
                Column().width('100%').height('100%').backgroundColor(Color.Blue)
              }.tabBar(SubTabBarStyle.of('Subpage d'))

              TabContent() {
                Column().width('100%').height('100%').backgroundColor(Color.Green)
              }.tabBar(SubTabBarStyle.of('Subpage e'))

              TabContent() {
                Column().width('100%').height('100%').backgroundColor(Color.Pink)
              }.tabBar(SubTabBarStyle.of('Subpage f'))
            }
            .nestedScroll(TabsNestedScrollMode.SELF_FIRST)
          }.tabBar(SubTabBarStyle.of('Homepage 2'))

        }
        .height('100%')
        .backgroundColor(0xf1f3f5)
        .barMode(this.barMode)
      }
      .width('100%')
      .height('100%')
      .padding('24vp')
    }
  }
}
```

### Example 24 Setting the TabBar Floating Style

This example shows how to set the floating style and immersive material of the back panel for the tab bar through the [barFloatingStyle](arkts-arkui-tabs-comp-attribute.md#barfloatingstyle) API.

Since API version 26.0.0, the barFloatingStyle API is added.

```TypeScript
// xxx.ets
import { uiMaterial } from '@kit.ArkUI';
@Entry
@Component
struct TabsFloatingStyleExample {
  build() {
    Column() {
      Tabs({ barPosition: BarPosition.End }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Blue)
        }.tabBar('Blue')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar('Green')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Orange)
        }.tabBar('Orange')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar('Pink')
      }
      .barFloatingStyle({
        adaptToHandedness: true, systemMaterial: new uiMaterial.ImmersiveMaterial(
          {
            style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
            applyShadow: true,
            interactive: true,
            lightEffect: { color: Color.White }
          }
        )
      })
      .barOverlap(true)
      .height('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```
