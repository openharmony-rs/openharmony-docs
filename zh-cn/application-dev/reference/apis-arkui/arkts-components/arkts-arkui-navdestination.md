# NavDestination

作为子页面的根容器，用于显示Navigation的内容区。
> **说明：**
> - 该组件从API version 11开始默认支持安全区避让特性(默认值为：expandSafeArea([SafeAreaType.SYSTEM], > [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM]))，开发者可以重写该属性覆盖默认行为，API version 11之前的版本需配合expandSafeArea属性实现 > 安全区避让。 > > - NavDestination组件必须配合Navigation使用，作为Navigation目的页面的根节点，单独使用只能作为普通容器组件，不具备路由相关属性能力。 > > - 如果路由栈中间页面的生命周期发生变化，跳转之前的栈顶NavDestination的生命周期(onWillShow, onShown, onHidden, onWillDisappear)与跳转之后的栈顶 > NavDestination的生命周期(onWillShow, onShown, onHidden, onWillDisappear)均在最后触发。 > > - NavDestination未设置主副标题并且没有返回键时，不显示标题栏。 > > - 不建议设置位置、大小等布局相关属性，可能会造成页面显示异常。例如在NavDestination上添加zIndex属性时，会覆盖掉系统设置的层级，可能导致出现显示异常。

## 子组件


> **说明：**
> 
> - 子组件类型：系统组件和自定义组件，支持渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、
> [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和
> [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。
> 
> - 子组件个数：多个。

## NavDestination

```TypeScript
NavDestination()
```

创建Navigation子页面的根容器。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [NavDestinationCommonTitle](arkts-arkui-navdestinationcommontitle-i.md) | NavDestination通用标题。 |
| [NavDestinationContext](arkts-arkui-navdestinationcontext-i.md) | NavDestination上下文信息。 |
| [NavDestinationCustomTitle](arkts-arkui-navdestinationcustomtitle-i.md) | NavDestination自定义标题。 |
| [NavDestinationTransition](arkts-arkui-navdestinationtransition-i.md) | NavDestination自定义动画接口。 |
| [NestedScrollInfo](arkts-arkui-nestedscrollinfo-i.md) | 嵌套可滚动容器组件信息。 |
| [RouteMapConfig](arkts-arkui-routemapconfig-i.md) | 路由配置信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [NavDestinationTransitionDelegate](arkts-arkui-navdestinationtransitiondelegate-t.md) | NavDestination自定义转场动画的代理函数。 |
| [Orientation](arkts-arkui-orientation-t.md) | 页面显示方向的枚举类型。 |
| [RestoreStateCallback](arkts-arkui-restorestatecallback-t.md) | 自定义页面状态恢复回调。 |
| [SaveStateCallback](arkts-arkui-savestatecallback-t.md) | 自定义页面状态保存回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NavDestinationActiveReason](arkts-arkui-navdestinationactivereason-e.md) | NavDestination激活态或者非激活态变化的原因。 |
| [NavDestinationMode](arkts-arkui-navdestinationmode-e.md) | NavDestination类型。 |
| [NavigationSystemTransitionType](arkts-arkui-navigationsystemtransitiontype-e.md) | 系统转场动画类型。 |
| [VisibilityChangeReason](arkts-arkui-visibilitychangereason-e.md) | NavDestination可见性发生变化的原因。 |

## 示例

以下示例主要演示NavDestination绑定可滚动容器组件来实现滚动内容时触发标题栏和工具栏显示隐藏的效果。

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
            }, (item: number) => item.toString());
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
          }, (item: number) => item.toString());
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
        // $r('sys.symbol.phone_badge_star')需要替换为开发者所需的资源文件
        value: 'item1',
        symbolIcon: new SymbolGlyphModifier($r('sys.symbol.phone_badge_star'))
      }
    ], { backgroundColor: Color.Orange, barStyle: BarStyle.STACK })
    // 绑定有父子关系的可滚动容器组件
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
        }, (item: number) => item.toString());
      }.width('100%')
    }
    .title('PageTwo', { backgroundColor: Color.Yellow, barStyle: BarStyle.STACK })
    .toolbarConfiguration([
      {
        // $r('sys.symbol.phone_badge_star')需要替换为开发者所需的资源文件
        value: 'item1',
        symbolIcon: new SymbolGlyphModifier($r('sys.symbol.phone_badge_star'))
      }
    ], { backgroundColor: Color.Orange, barStyle: BarStyle.STACK })
    // 绑定可滚动容器组件
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

以下示例主要演示NavDestination设置自定义转场动画属性[customTransition](arkts-arkui-navdestination-attribute.md#customtransition)的效果。

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
            this.stack.pushPath({ name: this.name == 'PageOne' ? 'PageTwo' : 'PageOne' });
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

以下示例主要演示NavDestination设置系统转场动画[systemTransition](arkts-arkui-navdestination-attribute.md#systemtransition)为Fade、Explode、SlideBottom与SlideRight时的转场效果。

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
        .width(85)
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

从API version 19开始，新增了preferredOrientation属性。

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
    .preferredOrientation(window.Orientation.PORTRAIT) // 竖屏方向
    .enableStatusBar(true) // 显示状态栏
    .enableNavigationIndicator(true) // 显示导航条
    .backgroundColor('#ffbaece9')
    .onResult((result: ESObject) => {
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
    .preferredOrientation(window.Orientation.LANDSCAPE) // 横屏方向
    .enableStatusBar(false) // 隐藏状态栏
    .enableNavigationIndicator(false) // 隐藏导航条
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
    this.stack.pushPath({name: 'portrait'});
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

从API version 17开始，NavDestination新增onActive、onInactive属性。该示例演示onActive与onInactive生命周期的各种触发场景。

```TypeScript
import { promptAction, ComponentContent, OverlayManager } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = '';
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
      // API version 17版本，请替换为promptAction.showToast接口。从API version 18开始，请使用示例中的promptAction.openToast接口。
      promptAction.openToast({ message: onActiveMsg }).catch((err: BusinessError) => {
        console.error(`Failed to open toast. Code: ${err.code}, message: ${err.message}`);
      });
    })
    .onInactive((reason: NavDestinationActiveReason) => {
      let onInActiveMsg: string = `[activeTest] ${this.name} onInactive, reason: ${reason}`;
      console.info(onInActiveMsg);
      // API version 17版本，请替换为promptAction.showToast接口。从API version 18开始，请使用示例中的promptAction.openToast接口。
      promptAction.openToast({ message: onInActiveMsg }).catch((err: BusinessError) => {
        console.error(`Failed to open toast. Code: ${err.code}, message: ${err.message}`);
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
          Button('open Modal')
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
          Button('open BindSheet')
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
          Button('open Dialog')
            .onClick(() => {
              let componentContent = new ComponentContent(
                this.getUIContext(), wrapBuilder<[Params]>(builderText),
                new Params('dialog', {y: '10%'}));
              this.getUIContext().getPromptAction().openCustomDialog(componentContent)
                .then(() => {
                  console.info('[activeTest] open custom dialog success');
                })
                .catch((err: BusinessError) => {
                  console.error(`Failed to open custom dialog. Code: ${err.code}, message: ${err.message}`);
                })
            })
            .fontColor(Color.Black)
            .backgroundColor('#ccc')
            .margin(5)
          Button('open Overlay')
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
