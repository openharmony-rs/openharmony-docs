# NavDestination

**NavDestination** is the root container of a destination page and represents the content area of the Navigation component.

> **NOTE**

> - Since API version 11, this component supports the safe area attribute by default, with the default attribute > value being **expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM])**. You can override > this attribute to change the default behavior. In earlier versions, you need to use the > expandSafeArea attribute to implement the safe area feature. > > - The **NavDestination** component must be used in conjunction with the **Navigation** component to act as the root > node for the navigation destination page. When used alone, it can only function as a standard container component > and does not possess any routing-related attributes or capabilities. > > - If the lifecycle of an intermediate page in the routing stack changes, the lifecycle callbacks (**onWillShow**, > **onShown**, **onHidden**, **onWillDisappear**) of the top **NavDestination** in the stack both before and after > the navigation will be triggered last in the sequence. > > - If no main title or subtitle is set for **NavDestination** and there is no back button, the title bar is not > displayed. > > - Avoid setting layout-related attributes such as the position and size. They may result in display issues on the > page. For example, do not apply the [zIndex](arkts-arkui-common-comp-commonmethod-c.md#zindex) attribute to a **NavDestination** > component. This will override the system-defined stacking order and may cause display anomalies.

## Child Components


> **NOTE:** 
> 
> - Allowed child component types: built-in and custom components, including rendering control types ([if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), and [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)).
> 
> - Number of child components: multiple.

## NavDestination

```TypeScript
NavDestination()
```

Creates the root container for a subpage in Navigation.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [NavDestinationCommonTitle](arkts-arkui-navdestination-comp-navdestinationcommontitle-i.md) | Defines a general title for the **NavDestination** component. |
| [NavDestinationContext](arkts-arkui-navdestination-comp-navdestinationcontext-i.md) | Defines the context information for the **NavDestination** component. |
| [NavDestinationCustomTitle](arkts-arkui-navdestination-comp-navdestinationcustomtitle-i.md) | Defines a custom title for the **NavDestination** component. |
| [NavDestinationTransition](arkts-arkui-navdestination-comp-navdestinationtransition-i.md) | Defines a custom transition animation for the **NavDestination** component. |
| [NestedScrollInfo](arkts-arkui-navdestination-comp-nestedscrollinfo-i.md) | Provides the information about the nested scrollable containers. |
| [RouteMapConfig](arkts-arkui-navdestination-comp-routemapconfig-i.md) | Defines the routing configuration. |

### Types

| Name | Description |
| --- | --- |
| [NavDestinationTransitionDelegate](arkts-arkui-navdestination-comp-navdestinationtransitiondelegate-t.md) | Defines the delegate function for custom transition animations of the **NavDestination** component. |
| [Orientation](arkts-arkui-navdestination-comp-orientation-t.md) | Defines an instance object of the Orientation type. |
| [RestoreStateCallback](arkts-arkui-navdestination-comp-restorestatecallback-t.md) | Custom page state restore callback. |
| [SaveStateCallback](arkts-arkui-navdestination-comp-savestatecallback-t.md) | Custom page state save callback. |

### Enums

| Name | Description |
| --- | --- |
| [NavDestinationActiveReason](arkts-arkui-navdestination-comp-navdestinationactivereason-e.md) | Enumerates reasons for the activation state changes of the **NavDestination** component. |
| [NavDestinationMode](arkts-arkui-navdestination-comp-navdestinationmode-e.md) | Mode of the **NavDestination** component. |
| [NavigationSystemTransitionType](arkts-arkui-navdestination-comp-navigationsystemtransitiontype-e.md) | Type of the system transition animation. |
| [VisibilityChangeReason](arkts-arkui-navdestination-comp-visibilitychangereason-e.md) | Enumerates reasons for **NavDestination** visibility changes. |

## Examples

### Example 1: Linking the Title Bar and Toolbar with Scrollable Components

This example shows how to bind a NavDestination component to scrollable containers so that scrolling in the scrollable containers triggers the animations for showing or hiding the title bar and toolbar of the NavDestination component.



```TypeScript
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Component
struct MyPageOne {
  private listScroller: Scroller = new Scroller();
  private scrollScroller: Scroller = new Scroller();
  private arr: number[] = [];

  aboutToAppear(): void {
    for (let i = 0; i < 30; i++) {
      this.arr.push(i);
    }
  }

  build() {
    NavDestination() {
      Scroll(this.scrollScroller) {
        Column() {
          List({ space: 0, initialIndex: 0, scroller: this.listScroller }) {
            ForEach(this.arr, (item: number, index: number) => {
              ListItem() {
                Text('' + item)
                  .height(100)
                  .fontSize(16)
                  .textAlign(TextAlign.Center)
                  .width('90%')
                  .margin({ left: '5%' })
                  .borderRadius(10)
                  .backgroundColor(Color.Gray)
              }
            }, (item: string) => item);
          }.width('100%').height('80%').scrollBar(BarState.Off)
          .nestedScroll({ scrollForward: NestedScrollMode.SELF_FIRST, scrollBackward: NestedScrollMode.SELF_FIRST })

          ForEach(this.arr, (item: number, index: number) => {
            ListItem() {
              Text('' + item)
                .height(100)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .width('90%')
                .margin({ top: '5%' })
                .borderRadius(10)
                .backgroundColor(Color.Pink)
            }
          }, (item: string) => item);
        }
      }
      .width('100%')
      .scrollBar(BarState.Off)
      .scrollable(ScrollDirection.Vertical)
      .edgeEffect(EdgeEffect.Spring)
    }
    .title('PageOne', { backgroundColor: Color.Yellow, barStyle: BarStyle.STACK })
    .toolbarConfiguration([
      {
        // Replace $r('sys.symbol.phone_badge_star') with the resource file you use.
        value: 'item1',
        symbolIcon: new SymbolGlyphModifier($r('sys.symbol.phone_badge_star'))
      }
    ], { backgroundColor: Color.Orange, barStyle: BarStyle.STACK })
    // Bind the component to nested scrollable containers.
    .bindToNestedScrollable([{ parent: this.scrollScroller, child: this.listScroller }])
  }
}

@Component
struct MyPageTwo {
  private listScroller: Scroller = new Scroller();
  private arr: number[] = [];

  aboutToAppear(): void {
    for (let i = 0; i < 30; i++) {
      this.arr.push(i);
    }
  }

  build() {
    NavDestination() {
      List({ scroller: this.listScroller }) {
        ForEach(this.arr, (item: number, index: number) => {
          ListItem() {
            Text('' + item)
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .width('90%')
              .margin({ left: '5%' })
              .borderRadius(10)
              .backgroundColor(Color.Gray)
          }
        }, (item: string) => item);
      }.width('100%')
    }
    .title('PageTwo', { backgroundColor: Color.Yellow, barStyle: BarStyle.STACK })
    .toolbarConfiguration([
      {
        // Replace $r('sys.symbol.phone_badge_star') with the resource file you use.
        value: 'item1',
        symbolIcon: new SymbolGlyphModifier($r('sys.symbol.phone_badge_star'))
      }
    ], { backgroundColor: Color.Orange, barStyle: BarStyle.STACK })
    // Bind the component to a scrollable container.
    .bindToScrollable([this.listScroller])
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  MyPageMap(name: string) {
    if (name === 'myPageOne') {
      MyPageOne();
    } else {
      MyPageTwo();
    }
  }

  build() {
    Navigation(this.stack) {
      Column() {
        Button('push PageOne').onClick(() => {
          this.stack.pushPath({ name: 'myPageOne' });
        })
        Button('push PageTwo').onClick(() => {
          this.stack.pushPath({ name: 'myPageTwo' });
        })
      }.height('40%').justifyContent(FlexAlign.SpaceAround)
    }.width('100%')
    .height('100%')
    .title({ main: 'MainTitle', sub: 'subTitle' })
    .navDestination(this.MyPageMap)
  }
}
```

### Example 2: Setting a Custom Transitions for the NavDestination Component

The following example demonstrates how to set a custom transition animation for the NavDestination component using [customTransition](arkts-arkui-navdestination-comp-attribute.md#customtransition).



```TypeScript
@Entry
@Component
struct NavDestinationCustomTransition {
  stack: NavPathStack = new NavPathStack();

  @Builder
  pageMap(name: string) {
    if (name) {
      NavDest();
    }
  }

  aboutToAppear(): void {
    this.stack.pushPath({name: 'dest0'});
  }

  build() {
    Navigation(this.stack) {
      // empty
    }
    .navDestination(this.pageMap)
    .hideNavBar(true)
    .title('Main Page')
    .titleMode(NavigationTitleMode.Mini)
  }
}

declare type voidFunc = () => void;

@Component
struct NavDest {
  @State name: string = 'NA';
  @State destWidth: string = '100%';
  stack: NavPathStack = new NavPathStack();
  @State translateY: string = '0';

  @Builder
  titleBuilder() {
    Text(this.name)
      .fontSize(20)
      .height(55)
      .fontWeight(FontWeight.Bold)
      .width('100%')
      .padding({ left: 16, right: 16 })
  }

  build() {
    NavDestination() {
      Column() {
        Button('push next page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.stack.pushPath({ name: this.name == 'PageOne' ? "PageTwo" : "PageOne" });
          })
      }
      .size({ width: '100%', height: '100%' })
    }
    .title(this.titleBuilder)
    .translate({ y: this.translateY })
    .onReady((context) => {
      this.name = context.pathInfo.name;
      this.stack = context.pathStack;
    })
    .backgroundColor(this.name == 'PageOne' ? '#F1F3F5' : '#ff11dee5')
    .customTransition(
      (op: NavigationOperation, isEnter: boolean)
        : Array<NavDestinationTransition> | undefined => {
        console.info('[NavDestinationTransition]', 'reached delegate in frontend, op: ' + op + ', isEnter: ' + isEnter);

        let transitionOneEvent: voidFunc = () => { console.info('[NavDestinationTransition]', 'reached transitionOne, empty now!'); }
        let transitionOneFinishEvent: voidFunc = () => { console.info('[NavDestinationTransition]', 'reached transitionOneFinish, empty now!'); }
        let transitionOneDuration: number = 500;
        if (op === NavigationOperation.PUSH) {
          if (isEnter) {
            // ENTER_PUSH
            this.translateY = '100%';
            transitionOneEvent = () => {
              console.info('[NavDestinationTransition]', 'transitionOne, push & isEnter');
              this.translateY = '0';
            }
          } else {
            // EXIT_PUSH
            this.translateY = '0';
            transitionOneEvent = () => {
              console.info('[NavDestinationTransition]', 'transitionOne, push & !isEnter');
              this.translateY = '0';
            }
            transitionOneDuration = 450;
          }
        } else if (op === NavigationOperation.POP) {
          if (isEnter) {
            // ENTER_POP
            this.translateY = '0';
            transitionOneEvent = () => {
              console.info('[NavDestinationTransition]', 'transitionOne, pop & isEnter');
              this.translateY = '0';
            }
          } else {
            // EXIT_POP
            this.translateY = '0';
            transitionOneEvent = () => {
              console.info('[NavDestinationTransition]', 'transitionOne, pop & !isEnter');
              this.translateY = '100%';
            }
          }
        }

        let transitionOne: NavDestinationTransition = {
          duration: transitionOneDuration,
          delay: 0,
          curve: Curve.Friction,
          event: transitionOneEvent,
          onTransitionEnd: transitionOneFinishEvent
        };

        let transitionTwoEvent: voidFunc = () => { console.info('[NavDestinationTransition]', 'reached transitionTwo, empty now!'); }
        let transitionTwo: NavDestinationTransition = {
          duration: 1000,
          delay: 0,
          curve: Curve.EaseInOut,
          event: transitionTwoEvent,
          onTransitionEnd: () => { console.info('[NavDestinationTransition]', 'reached Two\'s finish'); }
        };

        return [
          transitionOne,
          transitionTwo,
        ];
      })
  }
}
```

### Example 3: Setting System Transition Animations for the NavDestination Component

The following example demonstrates how to set system transition animations using [systemTransition](arkts-arkui-navdestination-comp-attribute.md#systemtransition) with Fade, Explode, SlideBottom, and SlideRight effects.









```TypeScript
@Entry
@Component
struct NavDestinationSystemTransition {
  @Provide stack: NavPathStack = new NavPathStack()
  @Provide homePageTransitionType: NavigationSystemTransitionType = NavigationSystemTransitionType.DEFAULT;

  @Builder
  pageMap(name: string) {
    if (name === 'Fade') {
      Fade();
    } else if (name === 'Explode') {
      Explode();
    } else if (name === 'SlideRight') {
      SlideRight();
    } else if (name === 'SlideBottom') {
      SlideBottom();
    } else {
      Dest();
    }
  }

  aboutToAppear(): void {
    this.stack.pushPath({name: 'Dest'});
  }

  build() {
    Navigation(this.stack) {
      // empty
    }
    .navDestination(this.pageMap)
    .hideNavBar(true)
  }
}

@Component
struct Dest {
  @Consume stack: NavPathStack;
  @Consume homePageTransitionType: NavigationSystemTransitionType;
  @State name: string = 'NA';

  build() {
    NavDestination() {
      HomeBody();
    }
    .title('Navigation System Animation')
    .onReady((context) => {
      this.name = context.pathInfo.name;
    })
    .systemTransition(this.homePageTransitionType)
  }
}

@Component
struct Fade {
  @Consume stack: NavPathStack;
  @State name: string = 'NA';

  build() {
    NavDestination() {
      DestBody({
        name: this.name
      })
    }
    .title(this.name)
    .onReady((context) => {
      this.name = context.pathInfo.name;
    })
    .systemTransition(NavigationSystemTransitionType.FADE)
  }
}

@Component
struct Explode {
  @Consume stack: NavPathStack;
  @State name: string = 'NA';

  build() {
    NavDestination() {
      DestBody({
        name: this.name
      })
    }
    .title(this.name)
    .onReady((context) => {
      this.name = context.pathInfo.name;
    })
    .systemTransition(NavigationSystemTransitionType.EXPLODE)
  }
}

@Component
struct SlideRight {
  @Consume stack: NavPathStack;
  @State name: string = 'NA';

  build() {
    NavDestination() {
      DestBody({
        name: this.name
      })
    }
    .title(this.name)
    .onReady((context) => {
      this.name = context.pathInfo.name;
    })
    .systemTransition(NavigationSystemTransitionType.SLIDE_RIGHT)
  }
}

@Component
struct SlideBottom {
  @Consume stack: NavPathStack;
  @State name: string = 'NA';

  build() {
    NavDestination() {
      DestBody({
        name: this.name
      })
    }
    .title(this.name)
    .onReady((context) => {
      this.name = context.pathInfo.name;
    })
    .systemTransition(NavigationSystemTransitionType.SLIDE_BOTTOM)
  }
}

@Component
struct DestBody {
  name: string = 'NA';

  columnTextSize: number = 22;
  columnTextFontWeight: FontWeight = FontWeight.Bolder;
  columnWidth: string = '65%';
  columnPadding: number = 22;
  columnMargin: number = 10;
  columnBorderRadius: number = 10;

  build() {
    Column() {
      Column()
        .width('85')
        .height(50)
        .backgroundColor(Color.White)
      Column() {
        Text(this.name)
          .fontSize(this.columnTextSize)
          .fontWeight(this.columnTextFontWeight)
      }
      .width(this.columnWidth)
      .padding(this.columnPadding)
      .margin(this.columnMargin)
      .borderRadius(this.columnBorderRadius)
      .shadow(ShadowStyle.OUTER_DEFAULT_LG)
    }
  }
}

@Component
struct HomeBody {
  @Consume stack: NavPathStack;
  @Consume homePageTransitionType: NavigationSystemTransitionType;

  columnTextSize: number = 22;
  columnTextFontWeight: FontWeight = FontWeight.Bolder;
  columnWidth: string = '85%';
  columnPadding: number = 22;
  columnMargin: number = 10;
  columnBorderRadius: number = 10;
  columnShadow: ShadowStyle = ShadowStyle.OUTER_DEFAULT_MD;

  build() {
    Column() {
      Search({ value: 'Search' })
        .width(this.columnWidth)

      Column() {
        Text('fade')
          .fontSize(this.columnTextSize)
          .fontWeight(this.columnTextFontWeight)
      }
      .width(this.columnWidth)
      .padding(this.columnPadding)
      .margin(this.columnMargin)
      .borderRadius(this.columnBorderRadius)
      .shadow(this.columnShadow)
      .onClick(() => {
        this.homePageTransitionType = NavigationSystemTransitionType.FADE;
        this.stack.pushPath({name: 'Fade'});
      })

      Column() {
        Text('explode')
          .fontSize(this.columnTextSize)
          .fontWeight(this.columnTextFontWeight)
      }
      .width(this.columnWidth)
      .padding(this.columnPadding)
      .margin(this.columnMargin)
      .borderRadius(this.columnBorderRadius)
      .shadow(this.columnShadow)
      .onClick(() => {
        this.homePageTransitionType = NavigationSystemTransitionType.EXPLODE;
        this.stack.pushPath({name: 'Explode'});
      })

      Column() {
        Text('slide right')
          .fontSize(this.columnTextSize)
          .fontWeight(this.columnTextFontWeight)
      }
      .width(this.columnWidth)
      .padding(this.columnPadding)
      .margin(this.columnMargin)
      .borderRadius(this.columnBorderRadius)
      .shadow(this.columnShadow)
      .onClick(() => {
        this.homePageTransitionType = NavigationSystemTransitionType.SLIDE_RIGHT;
        this.stack.pushPath({name: 'SlideRight'});
      })

      Column() {
        Text('slide bottom')
          .fontSize(this.columnTextSize)
          .fontWeight(this.columnTextFontWeight)
      }
      .width(this.columnWidth)
      .padding(this.columnPadding)
      .margin(this.columnMargin)
      .borderRadius(this.columnBorderRadius)
      .shadow(this.columnShadow)
      .onClick(() => {
        this.homePageTransitionType = NavigationSystemTransitionType.SLIDE_BOTTOM;
        this.stack.pushPath({name: 'SlideBottom'});
      })
    }
  }
}
```

### Example 4: Configuring Display Orientation and Status Bar and Navigation Bar Visibility

This example demonstrates how to configure each NavDestination component with specific display orientations and control the visibility of the status bar and navigation bar.



```TypeScript
import { window } from '@kit.ArkUI';

@Component
struct PortraitPage {
  @State info: string = '';
  private stack: NavPathStack | undefined = undefined;
  build() {
    NavDestination() {
      Stack({alignContent: Alignment.Center}) {
        Button('push LANDSCAPE page').onClick(() => {
          this.stack?.pushPath({name: 'landscape'});
        })
      }.width('100%').height('100%')
    }
    .width('100%').height('100%')
    .title('PortraitPage')
    .preferredOrientation(window.Orientation.PORTRAIT) // Portrait orientation.
    .enableStatusBar (true) // Show the status bar.
    .enableNavigationIndicator(true) // Show the navigation bar.
    .backgroundColor('#ffbaece9')
    .onResult((result: ESObject)=>{
      this.info = result as string;
    })
    .onReady((ctx: NavDestinationContext) => {
      this.stack = ctx.pathStack;
    })
  }
}

@Component
struct LandscapePage {
  private stack: NavPathStack | undefined = undefined;
  build() {
    NavDestination() {
      Stack({alignContent: Alignment.Center}) {
        Button('push PORTRAIT page').onClick(() => {
          this.stack?.pushPath({name: 'portrait'});
        })
      }.width('100%').height('100%')
    }
    .width('100%').height('100%')
    .title('LandscapePage')
    .preferredOrientation(window.Orientation.LANDSCAPE) // Landscape orientation.
    .enableStatusBar(false) // Hide the status bar.
    .enableNavigationIndicator(false) // Hide the navigation bar.
    .backgroundColor('#ffecb8b8')
    .ignoreLayoutSafeArea([LayoutSafeAreaType.SYSTEM], [LayoutSafeAreaEdge.TOP, LayoutSafeAreaEdge.BOTTOM])
    .onReady((ctx: NavDestinationContext) => {
      this.stack = ctx.pathStack;
    })
  }
}

@Entry
@Component
struct ExamplePage {
  private stack: NavPathStack = new NavPathStack();

  aboutToAppear(): void {
    this.stack.pushPath({name: "portrait"});
  }

  @Builder
  MyPageMap(name: string) {
    if (name === 'portrait') {
      PortraitPage();
    } else {
      LandscapePage();
    }
  }

  build() {
    Navigation(this.stack) {
    }
    .width('100%')
    .height('100%')
    .hideNavBar(true)
    .navDestination(this.MyPageMap)
  }
}
```

### Example 5: Handling NavDestination onActive and onInActive Lifecycle Events

Starting from API version 17, the NavDestination component includes the [onActive](#onactive17) and [onInactive](#oninactive17) lifecycle events. This example demonstrates various triggering scenarios for the onActive and onInactive lifecycle callbacks.

```TypeScript
import { promptAction, ComponentContent, OverlayManager } from '@kit.ArkUI';

class Params {
  text: string = "";
  offset: Position;

  constructor(text: string, offset: Position) {
    this.text = text;
    this.offset = offset;
  }
}

let overlayShownTag: boolean = false;

@Builder
function builderText(params: Params) {
  Column() {
    Text('I am ' + params.text)
      .fontWeight(FontWeight.Bolder)
      .align(Alignment.Center)
      .fontSize(25)
      .offset({ y: '10%' })
  }
  .backgroundColor(params.text === 'overlay' ? '#ffc' : '#ccf')
  .width('100%')
  .height('100%')
  .offset(params.offset)
}

@Entry
@Component
struct Index {
  stack: NavPathStack = new NavPathStack();

  @Builder
  pageMap(name: string) {
    if (name === 'standard' || name === 'Home') {
      NavDest({
        name: name
      })
    }
    else if (name === 'dialog') {
      NavDest({
        name: name,
        mode: NavDestinationMode.DIALOG,
        positionY: '40%'
      })
    }
  }

  aboutToAppear(): void {
    this.stack.pushPath({name: 'Home'});
  }

  build() {
    Navigation(this.stack) {

    }
    .hideNavBar(true)
    .navDestination(this.pageMap)
  }
}

@Component
struct NavDest {
  @State positionY: string = '0%';
  name: string = 'NA';
  mode: NavDestinationMode = NavDestinationMode.STANDARD;

  build() {
    NavDestination() {
      NavBody()
    }
    .backgroundColor(this.mode === NavDestinationMode.DIALOG ? Color.Pink : undefined)
    .height(this.mode === NavDestinationMode.DIALOG ? '65%' : '100%')
    .mode(this.mode)
    .title(this.name)
    .position({ y: this.positionY })
    .onActive((reason: NavDestinationActiveReason) => {
      let onActiveMsg: string = `[activeTest] ${this.name} onActive, reason: ${reason}`;
      console.info(onActiveMsg);
      // Use promptAction.showToast for API version 17, and promptAction.openToast for API version 18 or later.
      promptAction.openToast({ message: onActiveMsg }).catch(() => {
        console.info('open toast failed');
      });
    })
    .onInactive((reason: NavDestinationActiveReason) => {
      let onInActiveMsg: string = `[activeTest] ${this.name} onInactive, reason: ${reason}`;
      console.info(onInActiveMsg);
      // Use promptAction.showToast for API version 17, and promptAction.openToast for API version 18 or later.
      promptAction.openToast({ message: onInActiveMsg }).catch(() => {
        console.info('open toast failed');
      });
    })
    .onBackPressed(() => {
      if (overlayShownTag) {
        overlayShownTag = false;
        this.getUIContext().getOverlayManager().hideAllComponentContents();
        return true;
      }
      return false;
    })
  }
}

@Component
struct NavBody {
  @State isShow: boolean = false;
  @State isBindSheetShow: boolean = false;
  stack: NavPathStack = new NavPathStack();

  aboutToAppear(): void {
    this.stack = this.queryNavigationInfo()?.pathStack!;
  }

  @Builder
  myBuilder(id: string) {
    Column() {
      Text('I am ' + id)
        .fontWeight(FontWeight.Bolder)
        .align(Alignment.Center)
        .fontSize(25)
        .offset({ y: '10%' })
    }
    .width('100%')
    .height('100%')
  }

  build() {
    Column() {
      Row() {
        Button('pushPath standard')
          .margin(5)
          .onClick(() => {
            this.stack.pushPath({name: 'standard'});
          })
        Button('pushPath dialog')
          .margin(5)
          .onClick(() => {
            this.stack.pushPath({name: 'dialog'});
          })
      }
      Column() {
        Row() {
          Button("open Modal")
            .onClick(() => {
              this.isShow = true;
            })
            .fontColor(Color.Black)
            .backgroundColor('#ccc')
            .margin(5)
            .bindContentCover(
              this.isShow,
              this.myBuilder('modal'), {
                backgroundColor: '#fcf',
                onDisappear: () => {
                  this.isShow = false;
                }
              })
          Button("open BindSheet")
            .onClick(() => {
              this.isBindSheetShow = true;
            })
            .fontColor(Color.Black)
            .backgroundColor('#ccc')
            .margin(5)
            .bindSheet($$this.isBindSheetShow, this.myBuilder('bindSheet'), {
              height: '60%',
              backgroundColor: '#cfc'
            })
        }
        Row() {
          Button("open Dialog")
            .onClick(() => {
              let componentContent = new ComponentContent(
                this.getUIContext(), wrapBuilder<[Params]>(builderText),
                new Params('dialog', {y: '10%'}));
              this.getUIContext().getPromptAction().openCustomDialog(componentContent)
                .then(() => {
                  console.info('[activeTest] open custom dialog success');
                })
                .catch(() => {
                  console.info('[activeTest] open custom dialog failed');
                })
            })
            .fontColor(Color.Black)
            .backgroundColor('#ccc')
            .margin(5)
          Button("open Overlay")
            .onClick(() => {
              let componentContent = new ComponentContent(
                this.getUIContext(), wrapBuilder<[Params]>(builderText),
                new Params('overlay', {y: '10%'}));
              this.getUIContext().getOverlayManager().addComponentContent(componentContent);
              this.getUIContext().getOverlayManager().showComponentContent(componentContent);
              overlayShownTag = true;
            })
            .fontColor(Color.Black)
            .backgroundColor('#ccc')
            .margin(5)
        }
      }
      .width('95%')
    }
    .width('100%')
    .height('100%')
  }
}
```
