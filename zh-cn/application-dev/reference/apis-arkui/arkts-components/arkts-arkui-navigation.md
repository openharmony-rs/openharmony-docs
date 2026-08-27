# Navigation

Navigation组件是路由导航的根视图容器，一般作为Page页面的根容器使用，其内部默认包含了标题栏、内容区和工具栏，其中内容区默认首页显示导航内容（Navigation的子组件）或非首页显示（ NavDestination的子组件），首页和非首页通过路由进行切换。
> **说明：**
> - 该组件从API version 11开始默认支持安全区避让特性(默认值为：expandSafeArea( > [SafeAreaType.SYSTEM, SafeAreaType.KEYBOARD, SafeAreaType.CUTOUT], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM]))，开发者可以重 > 写该属性覆盖默认行为，API version 11之前的版本需配合[expandSafeArea](arkts-arkui-commonmethod-c.md#expandsafearea)属性实现安全区避让。 > > - [NavBar](arkts-arkui-navbar-t.md)嵌套使用Navigation时，内层NavDestination的生命周期不和外层NavDestination以及全模态的生命周期进行联动。 > > - Navigation未设置主副标题（[title](arkts-arkui-navigation-attribute.md#title)或[subTitle](arkts-arkui-navigation-attribute.md#subtitle)）且 > [hideBackButton](arkts-arkui-navigation-attribute.md#hidebackbutton)属性设置为true时，不显示标题栏。 > > - Navigation的子页面切换时，新页面会主动请求焦点。 > > - 不建议在aboutToAppear中使用栈操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

## 子组件

可以包含子组件。从API version 9开始，推荐与NavRouter组件搭配使用。从API version 10开始，推荐使用[NavPathStack](arkts-arkui-navpathstack-c.md)配合[navDestination](arkts-arkui-navigation-attribute.md#navdestination)属 性进行页面路由。

## Navigation

```TypeScript
Navigation()
```

创建路由导航的根视图容器，适用于使用NavRouter组件进行页面路由。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack)
```

绑定导航控制器到Navigation组件，适用于使用[NavPathStack](arkts-arkui-navpathstack-c.md)配合 [navDestination](arkts-arkui-navigation-attribute.md#navdestination)属性进行页面路由。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | [NavPathStack](arkts-arkui-navpathstack-c.md) | 是 | 导航控制器对象。 |

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack, homeDestination: HomePathInfo)
```

绑定路由栈到Navigation组件，指定一个NavDestination作为Navigation的导航页（主页），适用于使用[NavPathStack](arkts-arkui-navpathstack-c.md)配合 [navDestination](arkts-arkui-navigation-attribute.md#navdestination)属性或者系统路由表进行页面路由。使用示例参考 示例16（Navigation使用NavDestination作为导航页）。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | [NavPathStack](arkts-arkui-navpathstack-c.md) | 是 | 路由栈信息。 |
| homeDestination | [HomePathInfo](arkts-arkui-homepathinfo-i.md) | 是 | 主页NavDestination信息。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [HomePathInfo](arkts-arkui-homepathinfo-i.md) | 主页NavDestination的信息。 |
| [MoreButtonOptions](arkts-arkui-morebuttonoptions-i.md) | 更多图标的菜单选项。设置后，可自定义更多按钮的背景模糊样式、背景效果等。 |
| [NavContentInfo](arkts-arkui-navcontentinfo-i.md) | 跳转Destination信息。 |
| [NavigationAnimatedTransition](arkts-arkui-navigationanimatedtransition-i.md) | 自定义转场动画协议，开发者需实现该协议来定义Navigation路由跳转的跳转动画。 |
| [NavigationCommonTitle](arkts-arkui-navigationcommontitle-i.md) | Navigation通用标题。 |
| [NavigationConfiguration](arkts-arkui-navigationconfiguration-i.md) | 导航配置选项。 |
| [NavigationCustomTitle](arkts-arkui-navigationcustomtitle-i.md) | Navigation自定义标题。 |
| [NavigationDividerStyle](arkts-arkui-navigationdividerstyle-i.md) | Navigation分割线颜色及上下边距。 |
| [NavigationInterception](arkts-arkui-navigationinterception-i.md) | Navigation跳转拦截对象。 |
| [NavigationMenuItem](arkts-arkui-navigationmenuitem-i.md) | 导航菜单项，包括菜单图标和菜单信息。 |
| [NavigationMenuOptions](arkts-arkui-navigationmenuoptions-i.md) | 页面右上角菜单选项。 |
| [NavigationOptions](arkts-arkui-navigationoptions-i.md) | 路由栈操作选项。 |
| [NavigationTitleOptions](arkts-arkui-navigationtitleoptions-i.md) | 标题栏选项。 |
| [NavigationToolbarOptions](arkts-arkui-navigationtoolbaroptions-i.md) | 工具栏选项。 |
| [NavigationTransitionProxy](arkts-arkui-navigationtransitionproxy-i.md) | 自定义转场动画代理对象。 |
| [PopInfo](arkts-arkui-popinfo-i.md) | 下一个页面返回的回调信息载体。 |
| [ScrollEffectOptions](arkts-arkui-scrolleffectoptions-i.md) | 定义标题栏的滑动模糊效果选项。 |
| [ToolbarItem](arkts-arkui-toolbaritem-i.md) | 工具栏可配置参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [InterceptionCallback](arkts-arkui-interceptioncallback-t.md) | Navigation页面跳转前的拦截回调。 |
| [InterceptionModeCallback](arkts-arkui-interceptionmodecallback-t.md) | Navigation单双栏显示状态发生变更时的拦截回调。 |
| [InterceptionShowCallback](arkts-arkui-interceptionshowcallback-t.md) | Navigation页面跳转前和页面跳转后的拦截回调。 |
| [Material](arkts-arkui-material-t.md) | 导入用于Navigation组件的材质类型。 |
| [NavBar](arkts-arkui-navbar-t.md) | Navigation首页名字。 |
| [SystemBarStyle](arkts-arkui-systembarstyle-t.md) | 状态栏的属性。在设置页面级状态栏属性时使用。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BarStyle](arkts-arkui-barstyle-e.md) | 标题栏或工具栏的布局样式。NavDestination的工具栏不支持设置该属性。 |
| [LaunchMode](arkts-arkui-launchmode-e.md) | 路由栈操作模式。 |
| [NavBarPosition](arkts-arkui-navbarposition-e.md) | 导航页位置。 |
| [NavigationMode](arkts-arkui-navigationmode-e.md) | 导航页显示模式。Navigation处于分栏显示状态时，导航页和内容区之间会显示分割线。 |
| [NavigationOperation](arkts-arkui-navigationoperation-e.md) | 页面跳转类型。 |
| [NavigationTitleMode](arkts-arkui-navigationtitlemode-e.md) | 标题栏显示模式。 |
| [ScrollEffectType](arkts-arkui-scrolleffecttype-e.md) | 滑动模糊效果类型。 |
| [ToolbarItemStatus](arkts-arkui-toolbaritemstatus-e.md) | 工具栏单个选项的状态。 |

## 示例

该示例主要演示Navigation页面的布局包括标题栏[title](#title)，菜单栏[menus](#menus)，内容区和工具栏[toolbarConfiguration](#toolbarconfiguration10)。

```TypeScript
// xxx.ets

@Entry
@Component
struct NavigationExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  @Builder
  NavigationTitle() {
    Column() {
      Text('Title')
        .fontColor('#182431')
        .fontSize(30)
        .lineHeight(41)
        .fontWeight(700)
      Text('subtitle')
        .fontColor('#182431')
        .fontSize(14)
        .lineHeight(19)
        .opacity(0.4)
        .margin({ top: 2, bottom: 20 })
    }.alignItems(HorizontalAlign.Start)
  }

  @Builder
  NavigationMenus() {
    Row() {
      // 'resources/base/media/ic_public_add.svg'需要替换为开发者所需的资源文件
      Image('resources/base/media/ic_public_add.svg')
        .width(24)
        .height(24)
      // 'resources/base/media/ic_public_add.svg'需要替换为开发者所需的资源文件
      Image('resources/base/media/ic_public_add.svg')
        .width(24)
        .height(24)
        .margin({ left: 24 })
      // 'resources/base/media/ic_public_more.svg'需要替换为开发者所需的资源文件
      Image('resources/base/media/ic_public_more.svg')
        .width(24)
        .height(24)
        .margin({ left: 24 })
    }
  }

  build() {
    Column() {
      Navigation() {
        TextInput({ placeholder: 'search...' })
          .width('90%')
          .height(40)
          .backgroundColor('#FFFFFF')
          .margin({ top: 8 })

        List({ space: 12, initialIndex: 0 }) {
          ForEach(this.arr, (item: number) => {
            ListItem() {
              Text('' + item)
                .width('90%')
                .height(72)
                .backgroundColor('#FFFFFF')
                .borderRadius(24)
                .fontSize(16)
                .fontWeight(500)
                .textAlign(TextAlign.Center)
            }
          }, (item: number) => item.toString())
        }
        .height(324)
        .width('100%')
        .margin({ top: 12, left: '10%' })
      }
      .title(this.NavigationTitle)
      .menus(this.NavigationMenus)
      .titleMode(NavigationTitleMode.Full)
      .toolbarConfiguration([
        {
          // $r('app.string.navigation_toolbar_add')和$r('app.media.ic_public_highlights_ed')需要替换为开发者所需的资源文件
          value: $r('app.string.navigation_toolbar_add'),
          icon: $r('app.media.ic_public_highlights_ed')
        },
        {
          // $r('app.string.navigation_toolbar_app')和$r('app.media.ic_public_highlights')需要替换为开发者所需的资源文件
          value: $r('app.string.navigation_toolbar_app'),
          icon: $r('app.media.ic_public_highlights')
        },
        {
          // $r('app.string.navigation_toolbar_collect')和$r('app.media.ic_public_highlights')需要替换为开发者所需的资源文件
          value: $r('app.string.navigation_toolbar_collect'),
          icon: $r('app.media.ic_public_highlights')
        }
      ])
      .hideTitleBar(false)
      .hideToolBar(false)
      .onTitleModeChange((titleModel: NavigationTitleMode) => {
        console.info('titleMode' + titleModel)
      })
    }.width('100%').height('100%').backgroundColor('#F1F3F5')
  }
}
```

该示例主要演示[NavPathStack](#navpathstack10)中方法的使用及路由拦截。

```TypeScript
// Index.ets
@Entry
@Component
struct NavigationExample {
  pageInfos: NavPathStack = new NavPathStack();
  isUseInterception: boolean = false;

  registerInterception() {
    this.pageInfos.setInterception({
      // 页面跳转前拦截，允许操作栈，在当前跳转中生效。
      willShow: (from: NavDestinationContext | 'navBar', to: NavDestinationContext | 'navBar',
        operation: NavigationOperation, animated: boolean) => {
        if (!this.isUseInterception) {
          return;
        }
        if (typeof to === 'string') {
          console.info('target page is navigation home');
          return;
        }
        // 重定向目标页面，更改为pageTwo页面到pageOne页面。
        let target: NavDestinationContext = to as NavDestinationContext;
        if (target.pathInfo.name === 'pageTwo') {
          target.pathStack.pop();
          target.pathStack.pushPathByName('pageOne', null);
        }
      },
      // 页面跳转后回调，在该回调中操作栈在下一次跳转中刷新。
      didShow: (from: NavDestinationContext | 'navBar', to: NavDestinationContext | 'navBar',
        operation: NavigationOperation, isAnimated: boolean) => {
        if (!this.isUseInterception) {
          return;
        }
        if (typeof from === 'string') {
          console.info('current transition is from navigation home');
        } else {
          console.info(`current transition is from  ${(from as NavDestinationContext).pathInfo.name}`);
        }
        if (typeof to === 'string') {
          console.info('current transition to is navBar');
        } else {
          console.info(`current transition is to ${(to as NavDestinationContext).pathInfo.name}`);
        }
      },
      // Navigation单双栏显示状态发生变更时触发该回调。
      modeChange: (mode: NavigationMode) => {
        if (!this.isUseInterception) {
          return;
        }
        console.info(`current navigation mode is ${mode}`);
      }
    })
  }

  build() {
    Navigation(this.pageInfos) {
      Column() {
        Button('pushPath', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.pushPath({ name: 'pageOne' }); // 将name指定的NavDestination页面信息入栈
          })
        Button('use interception', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.isUseInterception = !this.isUseInterception;
            if (this.isUseInterception) {
              this.registerInterception();
            } else {
              this.pageInfos.setInterception(undefined);
            }
          })
      }
    }.title('NavIndex')
  }
}
```

```TypeScript
// PageOne.ets
class PageParam {
  count: number = 10;
}

@Builder
export function PageOneBuilder(name: string, param: Object) {
  PageOne()
}

@Component
export struct PageOne {
  pageInfos: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Button('pushPathByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            let pageParam = new PageParam();
            this.pageInfos.pushPathByName('pageTwo', pageParam); // 将name指定的NavDestination页面信息入栈，传递的数据为param
          })
        Button('singletonLaunchMode', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.pushPath({ name: 'pageOne' },
              { launchMode: LaunchMode.MOVE_TO_TOP_SINGLETON }); // 从栈底向栈顶查找，如果指定的名称已经存在，则将对应的NavDestination页面移到栈顶
          })
        Button('popToname', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.popToName('pageTwo'); // 回退路由栈到第一个名为name的NavDestination页面
            console.info(`popToName ${JSON.stringify(this.pageInfos)}，` + 
              `返回值 ${JSON.stringify(this.pageInfos.popToName('pageTwo'))}`); 
          })
        Button('popToIndex', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.popToIndex(1); // 回退路由栈到index指定的NavDestination页面
            console.info(`popToIndex ${JSON.stringify(this.pageInfos)}`);
          })
        Button('moveToTop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.moveToTop('pageTwo'); // 将第一个名为name的NavDestination页面移到栈顶
            console.info(`moveToTop ${JSON.stringify(this.pageInfos)}，` + 
              `返回值 ${JSON.stringify(this.pageInfos.popToName('pageTwo'))}`); 
          })
        Button('moveIndexToTop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.moveIndexToTop(1); // 将index指定的NavDestination页面移到栈顶
            console.info(`moveIndexToTop ${JSON.stringify(this.pageInfos)}`);
          })
        Button('clear', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.clear(); // 清除栈中所有页面
          })
        Button('get', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            console.info('-------------------');
            console.info(`获取栈中所有NavDestination页面的名称 ${JSON.stringify(this.pageInfos.getAllPathName())}`);
            console.info(`获取index指定的NavDestination页面的参数信息 ${JSON.stringify(this.pageInfos.getParamByIndex(1))}`);
            console.info(`获取全部名为name的NavDestination页面的参数信息 ${JSON.stringify(this.pageInfos.getParamByName('pageTwo'))}`);
            console.info(`获取全部名为name的NavDestination页面的位置索引 ${JSON.stringify(this.pageInfos.getIndexByName('pageOne'))}`);
            console.info(`获取栈大小 ${JSON.stringify(this.pageInfos.size())}`);
          })
      }.width('100%').height('100%')
    }.title('pageOne')
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // 弹出路由栈栈顶元素
      console.info(`pop 返回值 ${JSON.stringify(popDestinationInfo)}`);
      return true;
    }).onReady((context: NavDestinationContext) => {
      this.pageInfos = context.pathStack;
    })
  }
}
```

```TypeScript
// PageTwo.ets
@Builder
export function PageTwoBuilder(name: string, param: Object) {
  PageTwo()
}

@Component
export struct PageTwo {
  pathStack: NavPathStack = new NavPathStack();
  private menuItems: Array<NavigationMenuItem> = [
    {
      // 'resources/base/media/undo.svg'需要替换为开发者所需的资源文件
      value: '1',
      icon: 'resources/base/media/undo.svg',
    },
    {
      // 'resources/base/media/redo.svg'需要替换为开发者所需的资源文件
      value: '2',
      icon: 'resources/base/media/redo.svg',
      isEnabled: false,
    },
    {
      // 'resources/base/media/ic_public_ok.svg'需要替换为开发者所需的资源文件
      value: '3',
      icon: 'resources/base/media/ic_public_ok.svg',
      isEnabled: true,
    }
  ];

  build() {
    NavDestination() {
      Column() {
        Button('pushPathByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.pushPathByName('pageOne', null);
          })
      }.width('100%').height('100%')
    }.title('pageTwo')
    .menus(this.menuItems)
    .onBackPressed(() => {
      this.pathStack.pop();
      return true;
    })
    .onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
      console.info(`current page config info is ${JSON.stringify(context.getConfigInRouteMap())}`);
    })
  }
}
```

在src/main目录下的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的module字段里配置"routerMap": "$profile:router_map"，并在src/main/resources/base/profile目录下新增router_map.json。router_map.json示例如下。

```TypeScript
{
  "routerMap": [
    {
      "name": "pageOne",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "PageOneBuilder",
      "data": {
        "description": "this is pageOne"
      }
    },
    {
      "name": "pageTwo",
      "pageSourceFile": "src/main/ets/pages/PageTwo.ets",
      "buildFunction": "PageTwoBuilder"
    }
  ]
}
```

该示例主要演示设置每个[NavDestination](ts-basic-components-navdestination.md)子页面的自定义转场动画及可交互转场动画。

```TypeScript
// Index.ets
import { CustomTransition, AnimateCallback } from './CustomNavigationUtils'

@Entry
@Component
struct NavigationExample {
  pageInfos: NavPathStack = new NavPathStack();

  aboutToAppear() {
    if (this.pageInfos === undefined) {
      this.pageInfos = new NavPathStack();
    }
    this.pageInfos.pushPath({ name: 'pageOne', param: CustomTransition.getInstance().getAnimationId() });
  }

  build() {
    Navigation(this.pageInfos) {
    }
    .title('NavIndex')
    .hideNavBar(true)
    .customNavContentTransition((from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) => {
      if (from.mode == NavDestinationMode.DIALOG || to.mode == NavDestinationMode.DIALOG) {
        return undefined;
      }

      // 首页不进行自定义动画
      if (from.index === -1 || to.index === -1) {
        return undefined;
      }

      CustomTransition.getInstance().operation = operation;
      if (CustomTransition.getInstance().interactive) {
        let customAnimation: NavigationAnimatedTransition = {
          onTransitionEnd: (isSuccess: boolean) => {
            console.info(`===== current transition is ${isSuccess}`);
            CustomTransition.getInstance().recoverState();
            CustomTransition.getInstance().proxy = undefined;
          },
          transition: (transitionProxy: NavigationTransitionProxy) => {
            CustomTransition.getInstance().proxy = transitionProxy;
            let targetIndex: string | undefined = operation == NavigationOperation.PUSH ?
              (to.navDestinationId) : (from.navDestinationId);
            if (targetIndex) {
              CustomTransition.getInstance().fireInteractiveAnimation(targetIndex, operation);
            }
          },
          isInteractive: CustomTransition.getInstance().interactive
        }
        return customAnimation;
      }
      let customAnimation: NavigationAnimatedTransition = {
        onTransitionEnd: (isSuccess: boolean) => {
          console.info(`current transition result is ${isSuccess}`);
        },
        timeout: 7000,
        // 转场开始时系统调用该方法，并传入转场上下文代理对象
        transition: (transitionProxy: NavigationTransitionProxy) => {
          if (!from.navDestinationId || !to.navDestinationId) {
            return;
          }
          // 从封装类CustomTransition中根据子页面的序列获取对应的转场动画回调
          let fromParam: AnimateCallback = CustomTransition.getInstance().getAnimateParam(from.navDestinationId);
          let toParam: AnimateCallback = CustomTransition.getInstance().getAnimateParam(to.navDestinationId);
          if (operation == NavigationOperation.PUSH) {
            if (toParam.start) {
              toParam.start(true, false);
            }
            this.getUIContext()?.animateTo({
              duration: 500, onFinish: () => {
                transitionProxy.finishTransition();
              }
            }, () => {
              if (toParam.finish) {
                toParam.finish(true, false);
              }
            })
          } else {
            if (fromParam.start) {
              fromParam.start(true, true);
            }
            this.getUIContext()?.animateTo({
              duration: 500, onFinish: () => {
                transitionProxy.finishTransition();
              }
            }, () => {
              if (fromParam.finish) {
                fromParam.finish(true, true);
              }
            })
          }
        }
      };
      return customAnimation;
    })
  }
}
```

```TypeScript
// PageOne.ets
import { CustomTransition } from './CustomNavigationUtils';

@Builder
export function PageOneBuilder(name: string, param: Object) {
  PageOne()
}

@Component
export struct PageOne {
  pageInfos: NavPathStack = new NavPathStack();
  @State translateX: string = '0';
  pageId: string = '';
  rectWidth: number = 0;
  interactive: boolean = false;

  registerCallback() {
    CustomTransition.getInstance().registerNavParam(this.pageId, (isPush: boolean, isExit: boolean) => {
      if (isPush) {
        this.translateX = '100%';
      } else {
        this.translateX = '0';
      }
    }, (isPush: boolean, isExit: boolean) => {
      if (isPush) {
        this.translateX = '0';
      } else {
        this.translateX = '100%';
      }
    }, (isPush: boolean, isExit: boolean) => {
      this.translateX = '0';
    }, (operation: NavigationOperation) => {
      if (operation == NavigationOperation.PUSH) {
        this.translateX = '100%';
        this.getUIContext()?.animateTo({
          duration: 1000,
          onFinish: () => {
            this.translateX = '0';
          }
        }, () => {
          this.translateX = '0';
        })
      } else {
        this.translateX = '0';
        this.getUIContext()?.animateTo({
          duration: 1000,
          onFinish: () => {
            this.translateX = '0';
          }
        }, () => {
          this.translateX = '100%';
        })
      }
    }, 200);
  }

  build() {
    NavDestination() {
      Column() {
        Button(`setInteractive`)
          .onClick(() => {
            CustomTransition.getInstance().interactive = !CustomTransition.getInstance().interactive;
            this.interactive = CustomTransition.getInstance().interactive;
          })

        Button('pushPathByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            // 将name指定的NavDestination页面信息入栈，传递的数据为param
            this.pageInfos.pushDestinationByName('pageTwo', CustomTransition.getInstance().getAnimationId());
          })
      }
      .size({ width: '100%', height: '100%' })
    }
    .title('pageOne')
    .onDisAppear(() => {
      CustomTransition.getInstance().unRegisterNavParam(this.pageId);
    })
    .onReady((context: NavDestinationContext) => {
      this.pageInfos = context.pathStack;
      if (context.navDestinationId) {
        this.pageId = context.navDestinationId;
        this.registerCallback();
      }
    })
    .translate({ x: this.translateX })
    .backgroundColor('#F1F3F5')
    .gesture(PanGesture()
      .onActionStart((event: GestureEvent) => {
        this.rectWidth = event.target.area.width as number;
        if (event.offsetX < 0) {
          this.pageInfos.pushPath({ name: 'pageTwo', param: CustomTransition.getInstance().getAnimationId() });
        } else {
          this.pageInfos.pop();
        }
      })
      .onActionUpdate((event: GestureEvent) => {
        let rate = event.fingerList[0].localX / this.rectWidth;
        CustomTransition.getInstance().updateProgress(rate);
      })
      .onActionEnd((event: GestureEvent) => {
        let rate: number = event.fingerList[0].localX / this.rectWidth;
        CustomTransition.getInstance().finishInteractiveAnimation(rate);
      }))
  }
}
```

```TypeScript
// PageTwo.ets
import { CustomTransition } from './CustomNavigationUtils'

@Builder
export function PageTwoBuilder(name: string, param: Object) {
  PageTwo({ param: param as number })
}

@Component
export struct PageTwo {
  pageInfos: NavPathStack = new NavPathStack();
  @State translateX: string = '0';
  pageId: string = '';
  rectWidth: number = 0;
  param: number = 0;

  registerCallback() {
    CustomTransition.getInstance().registerNavParam(this.pageId, (isPush: boolean, isExit: boolean) => {
      if (isPush) {
        this.translateX = '100%'
      } else {
        this.translateX = '0';
      }
    }, (isPush: boolean, isExit: boolean) => {
      if (isPush) {
        this.translateX = '0';
      } else {
        this.translateX = '100%';
      }
    }, (isPush: boolean, isExit: boolean) => {
      this.translateX = '0';
    }, (operation: NavigationOperation) => {
      if (operation == NavigationOperation.PUSH) {
        this.translateX = '100%';
        this.getUIContext()?.animateTo({
          duration: 500, onFinish: () => {
            this.translateX = '0';
          }
        }, () => {
          this.translateX = '0';
        })
      } else {
        this.translateX = '0';
        this.getUIContext()?.animateTo({
          duration: 500, onFinish: () => {
            this.translateX = '0';
          }
        }, () => {
          this.translateX = '100%';
        })
      }
    }, 2000)
  }

  build() {
    NavDestination() {
      Column() {
        Button('pushPathByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            // 将name指定的NavDestination页面信息入栈，传递的数据为param
            this.pageInfos.pushPath({ name: 'pageOne', param: CustomTransition.getInstance().getAnimationId() });
          })
      }
      .size({ width: '100%', height: '100%' })
    }
    .title('pageTwo')
    .gesture(PanGesture()
      .onActionStart((event: GestureEvent) => {
        this.rectWidth = event.target.area.width as number;
        if (event.offsetX < 0) {
          this.pageInfos.pushPath({ name: 'pageOne', param: CustomTransition.getInstance().getAnimationId() });
        } else {
          this.pageInfos.pop();
        }
      })
      .onActionUpdate((event: GestureEvent) => {
        let rate = event.fingerList[0].localX / this.rectWidth;
        CustomTransition.getInstance().updateProgress(rate);
      })
      .onActionEnd((event: GestureEvent) => {
        let rate = event.fingerList[0].localX / this.rectWidth;
        CustomTransition.getInstance().finishInteractiveAnimation(rate);
      }))
    .onAppear(() => {
      this.registerCallback();
    })
    .onDisAppear(() => {
      CustomTransition.getInstance().unRegisterNavParam(this.pageId);
    })
    .onReady((context: NavDestinationContext) => {
      this.pageInfos = context.pathStack;
      if (context.navDestinationId) {
        this.pageId = context.navDestinationId;
        this.registerCallback();
      }
    })
    .translate({ x: this.translateX })
    .backgroundColor(Color.Yellow)
  }
}
```

```TypeScript
// src/main/pages/CustomNavigationUtils.ets
// 自定义接口，用来保存某个页面相关的转场动画回调和参数

export interface AnimateCallback {
  finish: ((isPush: boolean, isExit: boolean) => void | undefined) | undefined;
  start: ((isPush: boolean, isExit: boolean) => void | undefined) | undefined;
  onFinish: ((isPush: boolean, isExit: boolean) => void | undefined) | undefined;
  interactive: ((operation: NavigationOperation) => void | undefined) | undefined;
  timeout: (number | undefined) | undefined;
}

const customTransitionMap: Map<string, AnimateCallback> = new Map();

export class CustomTransition {
  static delegate = new CustomTransition();
  interactive: boolean = false;
  proxy: NavigationTransitionProxy | undefined = undefined;
  private animationId: number = 0;
  operation: NavigationOperation = NavigationOperation.PUSH;

  static getInstance() {
    return CustomTransition.delegate;
  }

  /* 注册某个页面的动画回调
   * name: 注册页面的唯一id
   * startCallback：用来设置动画开始时页面的状态
   * endCallback：用来设置动画结束时页面的状态
   * onFinish：用来执行动画结束后页面的其他操作
   * interactiveCallback: 注册的可交互转场的动效
   * timeout：转场结束的超时时间
   */
  registerNavParam(name: string, startCallback: (operation: boolean, isExit: boolean) => void,
    endCallback: (operation: boolean, isExit: boolean) => void,
    onFinish: (operation: boolean, isExit: boolean) => void,
    interactiveCallback: (operation: NavigationOperation) => void,
    timeout: number): void {
    if (customTransitionMap.has(name)) {
      let param = customTransitionMap.get(name);
      if (param != undefined) {
        param.start = startCallback;
        param.finish = endCallback;
        param.timeout = timeout;
        param.onFinish = onFinish;
        param.interactive = interactiveCallback;
        return;
      }
    }
    let params: AnimateCallback = {
      timeout: timeout,
      start: startCallback,
      finish: endCallback,
      onFinish: onFinish,
      interactive: interactiveCallback
    };
    customTransitionMap.set(name, params);
  }

  getAnimationId() {
    return Date.now();
  }

  unRegisterNavParam(name: string): void {
    customTransitionMap.delete(name);
  }

  fireInteractiveAnimation(id: string, operation: NavigationOperation) {
    let animation = customTransitionMap.get(id)?.interactive;
    if (!animation) {
      return;
    }
    animation(operation);
  }

  updateProgress(progress: number) {
    if (!this.proxy?.updateTransition) {
      return;
    }
    progress = this.operation == NavigationOperation.PUSH ? 1 - progress : progress;
    this.proxy?.updateTransition(progress);
  }

  cancelTransition() {
    if (this.proxy?.cancelTransition) {
      this.proxy.cancelTransition();
    }
  }

  recoverState() {
    if (!this.proxy?.from.navDestinationId || !this.proxy?.to.navDestinationId) {
      return;
    }
    let fromParam = customTransitionMap.get(this.proxy.from.navDestinationId);
    if (fromParam?.onFinish) {
      fromParam.onFinish(false, false);
    }
    let toParam = customTransitionMap.get(this.proxy?.to.navDestinationId);
    if (toParam?.onFinish) {
      toParam.onFinish(true, true);
    }
  }

  finishTransition() {
    this.proxy?.finishTransition();
  }

  finishInteractiveAnimation(rate: number) {
    if (this.operation == NavigationOperation.PUSH) {
      if (rate > 0.5) {
        if (this.proxy?.cancelTransition) {
          this.proxy.cancelTransition();
        }
      } else {
        this.proxy?.finishTransition();
      }
    } else {
      if (rate > 0.5) {
        this.proxy?.finishTransition();
      } else {
        if (this.proxy?.cancelTransition) {
          this.proxy.cancelTransition();
        }
      }
    }
  }

  getAnimateParam(name: string): AnimateCallback {
    let result: AnimateCallback = {
      start: customTransitionMap.get(name)?.start,
      finish: customTransitionMap.get(name)?.finish,
      timeout: customTransitionMap.get(name)?.timeout,
      onFinish: customTransitionMap.get(name)?.onFinish,
      interactive: customTransitionMap.get(name)?.interactive,
    };
    return result;
  }
}
```

该示例主要演示Navigation通过[NavPathStack](#navpathstack10)提供的接口来实现将设置的参数传给上一级页面。

```TypeScript
// Index.ets
@Entry
@Component
struct NavigationExample {
  pageInfo: NavPathStack = new NavPathStack();

  build() {
    Navigation(this.pageInfo) {
      Column() {
        Button('StartTest', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPath({ name: 'pageOne' }); // 将name指定的NavDestination页面信息入栈。
          })
      }
    }.title('NavIndex')
  }
}
```

```TypeScript
// PageOne.ets
import { BusinessError } from '@kit.BasicServicesKit';

class PageParam {
  count: number = 10;
}

class ParamWithOp {
  operation: number = 1;
  count: number = 10;
}

@Builder
export function PageOneBuilder(name: string, param: Object) {
  PageOne()
}

@Component
export struct PageOne {
  pageInfo: NavPathStack = new NavPathStack();
  @State message: string = 'Hello World';

  build() {
    NavDestination() {
      Column() {
        Text(this.message)
          .width('80%')
          .height(50)
          .margin(10)

        Button('pushPath', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            this.pageInfo.pushPath({
              name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
                this.message =
                  `[pushPath]last page is: ${popInfo.info.name},result: ${JSON.stringify(popInfo.result)}`;
              }
            }); // 将name指定的NavDestination页面信息入栈，传递的数据为param，添加接收处理结果的onPop回调。
          })

        Button('pushPathByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            let pageParam = new PageParam();
            this.pageInfo.pushPathByName('pageTwo', pageParam, (popInfo) => {
              this.message =
                `[pushPathByName]last page is: ${popInfo.info.name}, result: ${JSON.stringify(popInfo.result)}`;
            }); // 将name指定的NavDestination页面信息入栈，传递的数据为param，添加接收处理结果的onPop回调。
          })

        Button('pushDestination', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            let pageParam = new PageParam();
            // 将name指定的NavDestination页面信息入栈，传递的数据为param，添加接收处理结果的onPop回调。
            this.pageInfo.pushDestination({
              name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
                this.message =
                  `[pushDestination]last page is: ${popInfo.info.name}, result: ${JSON.stringify(popInfo.result)}`;
              }
            }).catch((error: BusinessError) => {
              console.error(`[pushDestination]failed, error code = ${error.code}, error.message = ${error.message}.`);
            }).then(() => {
              console.info('[pushDestination]success.');
            });
          })

        Button('pushDestinationByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            let pageParam = new pageParam();
            // 将name指定的NavDestination页面信息入栈，传递的数据为param，添加接收处理结果的onPop回调。
            this.pageInfo.pushDestinationByName('pageTwo', pageParam, (popInfo) => {
              this.message = 
                `[pushDestinationByName]last page is: ${popInfo.info.name}, result: ${JSON.stringify(popInfo.result)}`;
            }).catch((error: BusinessError) => {
              console.error(`[pushDestinationByName]failed, error code = ${error.code}, error.message = ${error.message}.`);
            }).then(() => {
              console.info('[pushDestinationByName]success.');
            });
          })

        Button('pushPathWithoutOnPop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            this.pageInfo.pushPath({ name: 'pageTwo', param: new ParamWithOp() }); // 将name指定的NavDestination页面信息入栈。
          })

        Button('pushPathByNameWithoutOnPop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            let pageParam = new PageParam();
            this.pageInfo.pushPathByName('pageTwo', pageParam); // 将name指定的NavDestination页面信息入栈，传递的数据为param。
          })

        Button('pushDestinationWithoutOnPop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            let pageParam = new PageParam();
            // 将name指定的NavDestination页面信息入栈，传递的数据为param。
            this.pageInfo.pushDestination({ name: 'pageTwo', param: new ParamWithOp() })
              .catch((error: BusinessError) => {
                console.error(`[pushDestinationWithoutOnPop]failed, error code = ${error.code}, error.message = ${error.message}.`);
              }).then(() => {
              console.info('[pushDestinationWithoutOnPop]success.');
            });
          })

        Button('pushDestinationByNameWithoutOnPop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            let pageParam = new PageParam();
            // 将name指定的NavDestination页面信息入栈，传递的数据为param。
            this.pageInfo.pushDestinationByName('pageTwo', pageParam)
              .catch((error: BusinessError) => {
                console.error(`[pushDestinationByNameWithoutOnPop]failed, error code = ${error.code}, error.message = ${error.message}.`);
              }).then(() => {
              console.info('[pushDestinationByNameWithoutOnPop]success.');
            });
          })

        Button('clear', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            this.pageInfo.clear(); // 清除栈中所有页面。
          })
      }.width('100%').height('100%')
    }.title('pageOne')
    .onBackPressed(() => {
      this.pageInfo.pop({ number: 1 }); // 弹出路由栈栈顶元素。
      return true;
    }).onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
    })
  }
}
```

```TypeScript
// PageTwo.ets
class ResultClass {
  constructor(count: number) {
    this.count = count;
  }

  count: number = 10;
}

@Builder
export function PageTwoBuilder() {
  PageTwo();
}

@Component
export struct PageTwo {
  pathStack: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Button('pop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.pop(new ResultClass(1)); // 回退到上一个页面，将处理结果传入push的onPop回调中。
          })

        Button('popToName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.popToName('pageOne',
              new ResultClass(11)); // 回退路由栈到第一个名为name的NavDestination页面，将处理结果传入push的onPop回调中。
          })

        Button('popToIndex', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.popToIndex(0, new ResultClass(111)); // 回退路由栈到index指定的NavDestination页面，将处理结果传入push的onPop回调中。
          })

        Button('popWithoutResult', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.pop();
          })

        Button('popToNameWithoutResult', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.popToName('pageOne');
          })

        Button('popToIndexWithoutResult', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.popToIndex(0);
          })
      }.width('100%').height('100%')
    }.title('pageTwo')
    .onBackPressed(() => {
      this.pathStack.pop(new ResultClass(0)); // 回退到上一个页面，将处理结果传入push的onPop回调。
      return true;
    }).onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
    })
  }
}
```

该示例主要演示设置Navigation主页的标题栏、工具栏和[NavDestination](ts-basic-components-navdestination.md)页面的标题栏的背景颜色和背景模糊效果。

```TypeScript
// Index
import {
  COLOR1,
  COLOR2,
  BLUR_STYLE_1,
  BLUR_STYLE_2,
  BLUR_STYLE_OPTION_1,
  BLUR_STYLE_OPTION_2,
} from './Utils';

@Entry
@Component
struct Index {
  @Provide('navPathStack') navPathStack: NavPathStack = new NavPathStack();
  @State useColor1: boolean = true;
  @State useBlur1: boolean = true;
  @State useBlurOption1: boolean = true;

  build() {
    Navigation(this.navPathStack) {
      Stack({ alignContent: Alignment.Center }) {
        BackComponent()
          .width('100%')
          .height('100%')
        Column() {
          Stack({ alignContent: Alignment.Center }) {
            Button('switch color')
              .onClick(() => {
                this.useColor1 = !this.useColor1;
              })
          }
          .width('100%')
          .layoutWeight(1)

          Stack({ alignContent: Alignment.Center }) {
            Button('switch blur')
              .onClick(() => {
                this.useBlur1 = !this.useBlur1;
              })
          }
          .width('100%')
          .layoutWeight(1)

          Stack({ alignContent: Alignment.Center }) {
            Button('switch blurOption')
              .onClick(() => {
                this.useBlurOption1 = !this.useBlurOption1;
              })
          }
          .width('100%')
          .layoutWeight(1)

          Stack({ alignContent: Alignment.Center }) {
            Button('push page')
              .onClick(() => {
                this.navPathStack.pushPathByName('NavigationMenu', null);
              })
          }
          .width('100%')
          .layoutWeight(1)
        }
        .width('100%')
        .height('80%')
      }.width('100%')
      .height('100%')
    }
    .width('100%')
    .height('100%')
    // 开发者可以设置标题栏的背景颜色和背景模糊效果
    .title('NavTitle', {
      backgroundColor: this.useColor1 ? COLOR1 : COLOR2,
      backgroundBlurStyle: this.useBlur1 ? BLUR_STYLE_1 : BLUR_STYLE_2,
      barStyle: BarStyle.STACK,
      backgroundBlurStyleOptions: this.useBlurOption1 ? BLUR_STYLE_OPTION_1 : BLUR_STYLE_OPTION_2,
    })
    // 开发者可以设置菜单的背景颜色和背景模糊效果
    .menus([
      { value: 'A' },
      { value: 'B' },
      { value: 'C' },
      { value: 'D' },
    ], {
      moreButtonOptions: {
        backgroundBlurStyle: this.useBlur1 ? BLUR_STYLE_1 : BLUR_STYLE_2,
        backgroundBlurStyleOptions: this.useBlurOption1 ? BLUR_STYLE_OPTION_1 : BLUR_STYLE_OPTION_2,
      }
    })
    // 开发者可以设置工具栏的背景颜色和背景模糊效果
    .toolbarConfiguration([
      { value: 'A' },
      { value: 'B' },
      { value: 'C' },
      { value: 'D' },
      { value: 'E' },
      { value: 'F' }
    ], {
      backgroundColor: this.useColor1 ? COLOR1 : COLOR2,
      backgroundBlurStyle: this.useBlur1 ? BLUR_STYLE_1 : BLUR_STYLE_2,
      // 开发者可以设置工具栏的菜单的背景颜色和背景模糊效果
      moreButtonOptions: {
        backgroundBlurStyle: this.useBlur1 ? BLUR_STYLE_1 : BLUR_STYLE_2,
        backgroundBlurStyleOptions: this.useBlurOption1 ? BLUR_STYLE_OPTION_1 : BLUR_STYLE_OPTION_2,
      }
    })
  }
}

@Component
export struct BackComponent {
  build() {
    Row() {
      Column() {
      }
      .height('100%')
      .backgroundColor('#3D9DB4')
      .layoutWeight(9)

      Column() {
      }
      .height('100%')
      .backgroundColor('#17A98D')
      .layoutWeight(9)

      Column() {
      }
      .height('100%')
      .backgroundColor('#FFC000')
      .layoutWeight(9)
    }
    .height('100%')
    .width('100%')
  }
}
```

```TypeScript
// PageOne.ets
import {
  COLOR1,
  COLOR2,
  BLUR_STYLE_1,
  BLUR_STYLE_2,
  EFFECT_OPTION_1,
  EFFECT_OPTION_2
} from './Utils';
import { BackComponent } from './Index';

@Builder
export function PageBuilder(name: string, param?: Object) {
  ColorAndBlur();
}

@Component
struct ColorAndBlur {
  @State useColor1: boolean = true;
  @State useBlur1: boolean = true;
  @State useEffect1: boolean = true;

  build() {
    NavDestination() {
      Stack({ alignContent: Alignment.Center }) {
        BackComponent()
          .width('100%')
          .height('100%')
        Column() {
          Stack({ alignContent: Alignment.Center }) {
            Button('switch color')
              .onClick(() => {
                this.useColor1 = !this.useColor1;
              })
          }
          .width('100%')
          .layoutWeight(1)

          Stack({ alignContent: Alignment.Center }) {
            Button('switch blur')
              .onClick(() => {
                this.useBlur1 = !this.useBlur1;
              })
          }
          .width('100%')
          .layoutWeight(1)

          Stack({ alignContent: Alignment.Center }) {
            Button('switch effect')
              .onClick(() => {
                this.useEffect1 = !this.useEffect1;
              })
          }
          .width('100%')
          .layoutWeight(1)
        }
        .width('100%')
        .height('100%')
      }.width('100%')
      .height('100%')
    }
    .width('100%')
    .height('100%')
    // 开发者可以设置标题栏的背景颜色和背景模糊效果
    .title('Destination Title', {
      backgroundColor: this.useColor1 ? COLOR1 : COLOR2,
      backgroundBlurStyle: this.useBlur1 ? BLUR_STYLE_1 : BLUR_STYLE_2,
      barStyle: BarStyle.STACK,
      backgroundEffect: this.useEffect1 ? EFFECT_OPTION_1 : EFFECT_OPTION_2,
    })
    // 开发者可以设置菜单的背景颜色和背景模糊效果
    .menus([
      { value: 'A' },
      { value: 'B' },
      { value: 'C' },
      { value: 'D' },
    ], {
      moreButtonOptions: {
        backgroundEffect: this.useEffect1 ? EFFECT_OPTION_1 : EFFECT_OPTION_2,
      }
    })
    // 开发者可以设置工具栏的背景颜色和背景模糊效果
    .toolbarConfiguration([
      { value: 'A' },
      { value: 'B' },
      { value: 'C' },
      { value: 'D' },
      { value: 'E' },
      { value: 'F' }
    ], {
      backgroundEffect: this.useEffect1 ? EFFECT_OPTION_1 : EFFECT_OPTION_2,
      // 开发者可以设置工具栏的菜单的背景颜色和背景模糊效果
      moreButtonOptions: {
        backgroundEffect: this.useEffect1 ? EFFECT_OPTION_1 : EFFECT_OPTION_2,
      }
    })
  }
}
```

```TypeScript
// Utils.ets
export const COLOR1: string = '#80004AAF';
export const COLOR2: string = '#802787D9';
export const BLUR_STYLE_1: BlurStyle = BlurStyle.BACKGROUND_THIN;
export const BLUR_STYLE_2: BlurStyle = BlurStyle.BACKGROUND_THICK;
export const BLUR_STYLE_OPTION_1: BackgroundBlurStyleOptions = {
  colorMode: ThemeColorMode.DARK,
  adaptiveColor: AdaptiveColor.DEFAULT,
  blurOptions: { grayscale: [20, 20] },
  scale: 1
};
export const BLUR_STYLE_OPTION_2: BackgroundBlurStyleOptions = {
  colorMode: ThemeColorMode.LIGHT,
  adaptiveColor: AdaptiveColor.AVERAGE,
  blurOptions: { grayscale: [20, 20] },
  scale: 1
};
export const EFFECT_OPTION_1: BackgroundEffectOptions = {
  radius: 20,
  saturation: 10,
  brightness: 0,
  color: '#66FFFFFF',
  adaptiveColor: AdaptiveColor.DEFAULT,
  blurOptions: { grayscale: [0, 0] },
};
export const EFFECT_OPTION_2: BackgroundEffectOptions = {
  radius: 60,
  saturation: 40,
  brightness: 1,
  color: '#661A1A1A',
  adaptiveColor: AdaptiveColor.AVERAGE,
  blurOptions: { grayscale: [20, 20] },
};
```

在src/main目录下的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的module字段里配置"routerMap": "$profile:router_map"，并在src/main/resources/base/profile目录下新增router_map.json。router_map.json示例如下。

```TypeScript
{
  "routerMap": [
    {
      "name": "NavigationMenu",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "PageBuilder",
      "data": {
        "description": "this is pageOne"
      }
    }
  ]
}
```

该示例主要演示在嵌套Navigation场景下，如何获取父[NavPathStack](#navpathstack10)。

```TypeScript
@Entry
@Component
struct NavigationExample1 {
  @State childNavStack: NavPathStack = new NavPathStack();

  build() {
    Navigation() {
      Stack({ alignContent: Alignment.Center }) {
        Navigation(this.childNavStack) {
          Button('push Path to parent Navigation', { stateEffect: true, type: ButtonType.Capsule })
            .width('80%')
            .height(40)
            .margin(20)
            .onClick(() => {
              // 可以获取父NavPathStack
              let parentStack = this.childNavStack.getParent();
              parentStack?.pushPath({ name: 'pageOne' });
            })
        }
        .clip(true)
        .backgroundColor(Color.Orange)
        .width('80%')
        .height('80%')
        .title('ChildNavigation')
      }
      .width('100%')
      .height('100%')
    }
    .backgroundColor(Color.Green)
    .width('100%')
    .height('100%')
    .title('ParentNavigation')
  }
}
```

```TypeScript
// PageOne.ets
@Builder
export function PageOneBuilder(name: string) {
  NavDestination() {
    Text(`this is ${name}`)
  }
  .title(name)
}
```

在src/main目录下的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的module字段里配置"routerMap": "$profile:router_map"，并在src/main/resources/base/profile目录下新增router_map.json。router_map.json示例如下。

```TypeScript
{
  "routerMap": [
    {
      "name": "pageOne",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "PageOneBuilder",
      "data": {
        "description": "this is pageOne"
      }
    }
  ]
}
```

[NavDestination](ts-basic-components-navdestination.md)通过[onReady](ts-basic-components-navdestination.md#onready11)事件能够拿到对应的[NavPathInfo](arkts-arkui-navpathinfo-c.md)和所属的[NavPathStack](#navpathstack10)。

```TypeScript
class PageParam {
  constructor(num_: number) {
    this.num = num_;
  }

  num: number = 0;
}

@Builder
export function PageOneBuilder(name: string, param: Object) {
  PageOne();
}

@Component
struct PageOne {
  private stack: NavPathStack | null = null;
  private name: string = '';
  private paramNum: number = 0;

  build() {
    NavDestination() {
      Column() {
        Text('NavPathInfo: name: ' + this.name + ', paramNum: ' + this.paramNum)
        Button('pushPath', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            if (this.stack) {
              let pageParam = new PageParam(this.paramNum + 1);
              this.stack.pushPath({ name: 'pageOne', param: pageParam });
            }
          })
        Button('pop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.stack?.pop();
          })
      }
      .width('100%')
      .height('100%')
    }
    .title('pageOne')
    .onReady((ctx: NavDestinationContext) => {
      // 在NavDestination中能够拿到传来的NavPathInfo和当前所处的NavPathStack
      try {
        this.name = ctx?.pathInfo?.name;
        this.paramNum = (ctx?.pathInfo?.param as PageParam)?.num;
        this.stack = ctx.pathStack;
      } catch (err) {
        console.error(`testTag onReady catch exception.Code:${err.Code}, message: ${err.message}`);
      }
    })
  }
}

@Entry
@Component
struct NavigationExample2 {
  private stack: NavPathStack = new NavPathStack();

  build() {
    Navigation(this.stack) {
      Stack({ alignContent: Alignment.Center }) {
        Button('pushPath', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            let pageParam = new PageParam(1);
            this.stack.pushPath({ name: 'pageOne', param: pageParam });
          })
      }
      .width('100%')
      .height('100%')
    }
    .width('100%')
    .height('100%')
    .title('Navigation')
  }
}
```

在src/main目录下的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的module字段里配置"routerMap": "$profile:router_map"，并在src/main/resources/base/profile目录下新增router_map.json。router_map.json示例如下。

```TypeScript
{
  "routerMap": [
    {
      "name": "pageOne",
      "pageSourceFile": "src/main/ets/pages/Index.ets",
      "buildFunction": "PageOneBuilder",
      "data": {
        "description": "this is pageOne"
      }
    }
  ]
}
```

该示例演示[NavDestination](ts-basic-components-navdestination.md)的[onAppear](ts-universal-events-show-hide.md#onappear)，[onDisAppear](ts-universal-events-show-hide.md#ondisappear)，[onShown](ts-basic-components-navdestination.md#onshown10)，[onHidden](ts-basic-components-navdestination.md#onhidden10)，[onWillAppear](ts-basic-components-navdestination.md#onwillappear12)，[onWillDisappear](ts-basic-components-navdestination.md#onwilldisappear12)，[onWillShow](ts-basic-components-navdestination.md#onwillshow12)，[onWillHide](ts-basic-components-navdestination.md#onwillhide12)接口的生命周期时序。

```TypeScript
@Builder
export function PageOneBuilder(name: string, param: Object) {
  PageOneComponent();
}

@Component
struct PageOneComponent {
  private stack: NavPathStack | null = null;
  @State eventStr: string = '';

  build() {
    NavDestination() {
      Column() {
        Text('event: ' + this.eventStr)
        Button('pushPath', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            if (this.stack) {
              this.stack.pushPath({ name: 'pageOne' });
            }
          })
        Button('pop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.stack?.pop();
          })
      }
      .width('100%')
      .height('100%')
    }
    .title('pageOne')
    .onAppear(() => {
      this.eventStr += '<onAppear>';
    })
    .onDisAppear(() => {
      this.eventStr += '<onDisAppear>';
    })
    .onShown(() => {
      this.eventStr += '<onShown>';
    })
    .onHidden(() => {
      this.eventStr += '<onHidden>';
    })
    .onWillAppear(() => {
      this.eventStr += '<onWillAppear>';
    })
    .onWillDisappear(() => {
      this.eventStr += '<onWillDisappear>';
    })
    .onWillShow(() => {
      this.eventStr += '<onWillShow>';
    })
    .onWillHide(() => {
      this.eventStr += '<onWillHide>';
    })
    // onReady会在onAppear之前调用
    .onReady((ctx: NavDestinationContext) => {
      try {
        this.eventStr += '<onReady>';
        this.stack = ctx.pathStack;
      } catch (err) {
        console.error(`testTag onReady catch exception.Code:${err.code}, message:${err.message}`);
      }
    })
  }
}

@Entry
@Component
struct NavigationExample3 {
  private stack: NavPathStack = new NavPathStack();

  build() {
    Navigation(this.stack) {
      Stack({ alignContent: Alignment.Center }) {
        Button('pushPath', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.stack.pushPath({ name: 'pageOne' });
          })
      }
      .width('100%')
      .height('100%')
    }
    .width('100%')
    .height('100%')
    .title('Navigation')
  }
}
```

该示例演示Navigation标题栏STACK布局效果。

```TypeScript
@Entry
@Component
struct NavigationExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11];
  private scrollerForScroll: Scroller = new Scroller();
  @State barStyle: BarStyle = BarStyle.STANDARD;

  build() {
    Column() {
      Navigation() {
        Column() {
          Scroll(this.scrollerForScroll) {
            Column() {
              // $r('app.media.image_1')需要替换为开发者所需的资源文件
              Image($r('app.media.image_1'))// 设置与标题栏高度一致，以便观察STACK效果
                .height(138)
                .width('100%')
              Button('BarStyle.STANDARD')
                .height('50vp')
                .onClick(() => {
                  this.barStyle = BarStyle.STANDARD;
                })
              Button('BarStyle.STACK')
                .height('50vp')
                .margin({ top: 12 })
                .onClick(() => {
                  this.barStyle = BarStyle.STACK;
                })

              ForEach(this.arr, (item: number) => {
                ListItem() {
                  Text('' + item)
                    .width('100%')
                    .height(100)
                    .fontSize(16)
                    .textAlign(TextAlign.Center)
                    .borderRadius(10)
                    .backgroundColor(Color.Orange)
                    .margin({ top: 12 })
                }
              }, (item: number) => item.toString())
            }
          }
        }
        .width('100%')
        .height('100%')
        .backgroundColor(0xDCDCDC)
      }
      .title(
        {
          main: 'NavTitle',
          sub: 'subtitle'
        },
        {
          backgroundBlurStyle: BlurStyle.COMPONENT_THICK,
          barStyle: this.barStyle,
        }
      )
      .titleMode(NavigationTitleMode.Free)
      .hideTitleBar(false)
    }.width('100%').height('100%').backgroundColor('#F1F3F5')
  }
}
```

该示例主要演示如何定义[NavPathStack](#navpathstack10)的派生类和派生类在Navigation中的基本用法。

```TypeScript
// Index.ets
import { DerivedNavPathStack, NewParam } from './Utils';

@Entry
@Component
struct Index {
  derivedStack: DerivedNavPathStack = new DerivedNavPathStack();

  aboutToAppear(): void {
    this.derivedStack.setId('origin stack');
  }
  
  build() {
    Navigation(this.derivedStack) {
      Button('to Page One').margin(20).onClick(() => {
        this.derivedStack.pushPath({
          name: 'pageOne',
          param: new NewParam('push pageOne in homePage when stack size: ' + this.derivedStack.size())
        });
      })
    }
    .title('Home Page')
  }
}
```

```TypeScript
// PageOne.ets
import { DerivedNavPathStack, NewParam } from './Utils';

@Builder
export function pageMap(name: string) {
  PageOne();
}

@Component
struct PageOne {
  derivedStack: DerivedNavPathStack = new DerivedNavPathStack();
  curStringifyParam: string = 'NA';

  build() {
    NavDestination() {
      Column() {
        Text(this.derivedStack.getInfo())
          .margin(10)
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Start)
        Text('current page param info:')
          .margin(10)
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Start)
        Text(this.curStringifyParam)
          .margin(20)
          .fontSize(20)
          .textAlign(TextAlign.Start)
      }.backgroundColor(Color.Pink)

      Button('to Page One').margin(20).onClick(() => {
        this.derivedStack.pushPath({
          name: 'pageOne',
          param: new NewParam('push pageOne in pageOne when stack size: ' + this.derivedStack.size())
        });
      })
    }.title('Page One')
    .onReady((context: NavDestinationContext) => {
      console.info('[derive-test] reached PageOne\'s onReady');
      // 从navdestinationContext获取派生堆栈
      this.derivedStack = context.pathStack as DerivedNavPathStack;
      console.info('[derive-test] -- got derivedStack: ' + this.derivedStack.id);
      this.curStringifyParam = JSON.stringify(context.pathInfo.param);
      console.info('[derive-test] -- got param: ' + this.curStringifyParam);
    })
  }
}
```

```TypeScript
// Utils.ets
export class DerivedNavPathStack extends NavPathStack {
  // 用户定义的属性'id'
  id: string = '__default__';

  // 派生类中的新功能
  setId(id: string) {
    this.id = id;
  }

  // 派生类中的新功能
  getInfo(): string {
    return `this page used Derived NavPathStack, id: ${this.id}`;
  }

  // 重载NavPathStack的功能
  pushPath(info: NavPathInfo, animated?: boolean): void
  pushPath(info: NavPathInfo, options?: NavigationOptions): void
  pushPath(info: NavPathInfo, secArg?: boolean | NavigationOptions): void {
    console.info('[derive-test] reached DerivedNavPathStack\'s pushPath');
    if (typeof secArg === 'boolean') {
      super.pushPath(info, secArg);
    } else {
      super.pushPath(info, secArg);
    }
  }

  // 重写和重载NavPathStack的函数
  pop(animated?: boolean | undefined): NavPathInfo | undefined
  pop(result: Object, animated?: boolean | undefined): NavPathInfo | undefined
  pop(result?: Object, animated?: boolean | undefined): NavPathInfo | undefined {
    console.info('[derive-test] reached DerivedNavPathStack\'s pop');
    return super.pop(result, animated);
  }

  // 基类的其他功能...
}

export class NewParam {
  info: string = '__default_param__';

  constructor(info: string) {
    this.info = info;
  }
}
```

在src/main目录下的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的module字段里配置"routerMap": "$profile:router_map"，并在src/main/resources/base/profile目录下新增router_map.json。router_map.json示例如下。

```TypeScript
{
  "routerMap": [
    {
      "name": "pageOne",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "pageMap",
      "data": {
        "description": "this is pageOne"
      }
    }
  ]
}
```

该示例主要演示Navigation和[NavDestination](ts-basic-components-navdestination.md)如何使用Symbol组件。

```TypeScript
// Index.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct NavigationExample {
  @Provide('navPathStack') navPathStack: NavPathStack = new NavPathStack();
  @State menuItems: Array<NavigationMenuItem> = [
    {
      // 'resources/base/media/ic_public_ok.svg'需要替换为开发者所需的资源文件
      value: 'menuItem1',
      icon: 'resources/base/media/ic_public_ok.svg' // 图标资源路径
    },
    {
      // resources/base/media/ic_public_ok.svg'需要替换为开发者所需的资源文件
      value: 'menuItem2',
      icon: 'resources/base/media/ic_public_ok.svg', // 图标资源路径
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_folder_badge_plus')).fontColor([Color.Red, Color.Green])
        .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_COLOR),
    },
    {
      value: 'menuItem3',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_lungs')),
    },
  ];
  @State toolItems: Array<ToolbarItem> = [
    {
      // 'resources/base/media/ic_public_ok.svg'需要替换为开发者所需的资源文件
      value: 'toolItem1',
      icon: 'resources/base/media/ic_public_ok.svg', // 图标资源路径
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_lungs')),
      status: ToolbarItemStatus.ACTIVE,
      activeSymbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_folder_badge_plus')).fontColor([Color.Red,
        Color.Green]).renderingStrategy(SymbolRenderingStrategy.MULTIPLE_COLOR),
      action: () => {
      }
    },
    {
      // 'resources/base/media/ic_public_more.svg'需要替换为开发者所需的资源文件
      value: 'toolItem2',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_star')),
      status: ToolbarItemStatus.ACTIVE,
      activeIcon: 'resources/base/media/ic_public_more.svg', // 图标资源路径
      action: () => {
      }
    },
    {
      value: 'toolItem3',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_star')),
      status: ToolbarItemStatus.ACTIVE,
      activeSymbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_lungs')),
      action: () => {
      }
    }
  ];

  build() {
    Navigation(this.navPathStack) {
      Column() {
        Button('跳转').onClick(() => {
          this.navPathStack.pushPathByName('NavigationMenu', null);
        })
      }
    }
    .backButtonIcon(new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')))
    .titleMode(NavigationTitleMode.Mini)
    .menus(this.menuItems)
    .toolbarConfiguration(this.toolItems)
    .title('一级页面')
  }
}
```

```TypeScript
// PageOne.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Builder
export function myRouter(name: string, param?: Object) {
  NavigationMenu();
}

@Component
export struct NavigationMenu {
  @Consume('navPathStack') navPathStack: NavPathStack;
  @State menuItems: Array<NavigationMenuItem> = [
    {
      // 'resources/base/media/ic_public_ok.svg'需要替换为开发者所需的资源文件
      value: 'menuItem1',
      icon: 'resources/base/media/ic_public_ok.svg', // 图标资源路径
      action: () => {
      }
    },
    {
      value: 'menuItem2',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_folder_badge_plus')).fontColor([Color.Red, Color.Green])
        .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_COLOR),
      action: () => {
      }
    },
    {
      value: 'menuItem3',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.repeat_1')),
      action: () => {
      }
    },
  ];

  build() {
    NavDestination() {
      Row() {
        Column() {
        }
        .width('100%')
      }
      .height('100%')
    }
    .hideTitleBar(false)
    .title('NavDestination title')
    .backgroundColor($r('sys.color.ohos_id_color_titlebar_sub_bg'))
    .backButtonIcon(new SymbolGlyphModifier($r('sys.symbol.ohos_star'))
      .fontColor([Color.Blue]))
    .menus(this.menuItems)
  }
}
```

在src/main目录下的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的module字段里配置"routerMap": "$profile:router_map"，并在src/main/resources/base/profile目录下新增router_map.json。router_map.json示例如下。

```TypeScript
{
  "routerMap": [
    {
      "name": "NavigationMenu",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "myRouter",
      "data": {
        "description": "this is pageOne"
      }
    }
  ]
}
```

该示例主要演示Navigation和[NavDestination](ts-basic-components-navdestination.md)如何设置自定义标题栏边距，如何通过TextModifier修改主副标题文本样式。

```TypeScript
// Index.ets
import { LengthMetrics } from '@kit.ArkUI';
import { MainTitleTextModifier, SubTitleTextModifier } from './Utils';

@Entry
@Component
struct NavigationExample {
  private navPathStack: NavPathStack = new NavPathStack();
  // 初始化标题栏起始端内间距
  @State paddingStart: LengthMetrics = LengthMetrics.vp(0);
  // 初始化标题栏结束端内间距
  @State paddingEnd: LengthMetrics = LengthMetrics.vp(0);
  // 主标题样式修改器
  @State mainTitleModifier: MainTitleTextModifier = new MainTitleTextModifier();
  // 副标题样式修改器
  @State subTitleModifier: SubTitleTextModifier = new SubTitleTextModifier();
  @State applyModifier: boolean = false;
  @State useStyle1: boolean = true;

  build() {
    Navigation(this.navPathStack) {
      Column() {
        // 标题栏内间距切换
        Button('apply padding 32vp')
          .onClick(() => {
            this.paddingStart = LengthMetrics.vp(32);
            this.paddingEnd = LengthMetrics.vp(32);
          })
          .margin({ top: 70 })
          .width(180)
        Button('apply padding 20vp')
          .onClick(() => {
            this.paddingStart = LengthMetrics.vp(20);
            this.paddingEnd = LengthMetrics.vp(20);
          })
          .margin({ top: 40 })
          .width(180)
        Button('pushPage')
          .onClick(() => {
            this.navPathStack.pushPath({ name: 'NavDestinationExample' });
          })
          .margin({ top: 40 })
          .width(180)
        Row() {
          Text(`apply Modifier`)
          Toggle({ isOn: this.applyModifier, type: ToggleType.Switch }).onChange((isOn: boolean) => {
            this.applyModifier = isOn;
          })
        }
        .padding({ top: 95, left: 5, right: 5 })
        .width(180)
        .justifyContent(FlexAlign.SpaceBetween)

        Row() {
          Text(`use Style1`)
          Toggle({ isOn: this.useStyle1, type: ToggleType.Switch }).onChange((isOn: boolean) => {
            this.mainTitleModifier.useStyle1 = isOn;
            this.subTitleModifier.useStyle1 = isOn;
            this.useStyle1 = isOn;
          })
        }
        .padding({ top: 40, left: 5, right: 5 })
        .width(180)
        .justifyContent(FlexAlign.SpaceBetween)
      }
      .width('100%')
      .height('100%')
    }
    .titleMode(NavigationTitleMode.Full)
    .title(
      { main: 'Title', sub: 'subTitle' },
      this.applyModifier ?
        {
          paddingStart: this.paddingStart,
          paddingEnd: this.paddingEnd,
          mainTitleModifier: this.mainTitleModifier,
          subTitleModifier: this.subTitleModifier,
        } : {
        paddingStart: this.paddingStart,
        paddingEnd: this.paddingEnd
      })
  }
}
```

```TypeScript
// PageOne.ets
import { LengthMetrics } from '@kit.ArkUI';
import { MainTitleTextModifier, SubTitleTextModifier } from './Utils';

@Builder
export function myRouter(name: string, param?: Object) {
  NavDestinationExample();
}
@Component
export struct NavDestinationExample {
  @State menuItems: Array<NavigationMenuItem> = [
    {
      // 'resources/base/media/ic_public_ok.svg'需要替换为开发者所需的资源文件
      value: 'menuItem1',
      icon: 'resources/base/media/ic_public_ok.svg', // 图标资源路径
      action: () => {
      }
    }
  ];
  @State paddingStart: LengthMetrics = LengthMetrics.vp(0);
  @State paddingEnd: LengthMetrics = LengthMetrics.vp(0);
  // 主标题样式修改器
  @State mainTitleModifier: MainTitleTextModifier = new MainTitleTextModifier();
  // 副标题样式修改器
  @State subTitleModifier: SubTitleTextModifier = new SubTitleTextModifier();
  @State applyModifier: boolean = false;
  @State useStyle1: boolean = true;

  build() {
    NavDestination() {
      Column() {
        // 标题栏内间距切换
        Button('apply padding 32vp')
          .onClick(() => {
            this.paddingStart = LengthMetrics.vp(32);
            this.paddingEnd = LengthMetrics.vp(32);
          })
          .margin({ top: 150 })
          .width(180)
        Button('apply padding 20vp')
          .onClick(() => {
            this.paddingStart = LengthMetrics.vp(20);
            this.paddingEnd = LengthMetrics.vp(20);
          })
          .margin({ top: 40 })
          .width(180)
        Row() {
          Text(`apply Modifier`)
          Toggle({ isOn: this.applyModifier, type: ToggleType.Switch }).onChange((isOn: boolean) => {
            this.applyModifier = isOn;
          })
        }
        .padding({ top: 95, left: 5, right: 5 })
        .width(180)
        .justifyContent(FlexAlign.SpaceBetween)

        Row() {
          Text(`use Style1`)
          Toggle({ isOn: this.useStyle1, type: ToggleType.Switch }).onChange((isOn: boolean) => {
            this.mainTitleModifier.useStyle1 = isOn;
            this.subTitleModifier.useStyle1 = isOn;
            this.useStyle1 = isOn;
          })
        }
        .padding({ top: 40, left: 5, right: 5 })
        .width(180)
        .justifyContent(FlexAlign.SpaceBetween)
      }
      .width('100%')
      .height('90%')
    }
    .hideTitleBar(false)
    .title(
      { main: 'Title', sub: 'subTitle' },
      this.applyModifier ?
        {
          paddingStart: this.paddingStart,
          paddingEnd: this.paddingEnd,
          mainTitleModifier: this.mainTitleModifier,
          subTitleModifier: this.subTitleModifier,
        } : {
        paddingStart: this.paddingStart,
        paddingEnd: this.paddingEnd
      })
    .menus(this.menuItems)
  }
}
```

```TypeScript
// Utils.ets
import { TextModifier } from '@kit.ArkUI';

export class MainTitleTextModifier extends TextModifier {
  useStyle1: boolean = true;

  applyNormalAttribute(instance: TextModifier): void {
    if (this.useStyle1) {
      console.info(`testTag mainTitle use style1`);
      instance.fontColor('#FFFFC000');
      instance.fontSize(35);
      instance.fontWeight(FontWeight.Bolder);
      instance.fontStyle(FontStyle.Normal);
      instance.textShadow({ radius: 5, offsetX: 9 });
    } else {
      console.info(`testTag mainTitle use style2`);
      instance.fontColor('#FF23A98D');
      instance.fontSize(20);
      instance.heightAdaptivePolicy(TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST);
      instance.fontWeight(FontWeight.Lighter);
      instance.fontStyle(FontStyle.Italic);
      instance.textShadow({ radius: 3, offsetX: 3 });
    }
  }
}

export class SubTitleTextModifier extends TextModifier {
  useStyle1: boolean = true;

  applyNormalAttribute(instance: TextModifier): void {
    if (this.useStyle1) {
      console.info(`testTag subTitle use style1`);
      instance.fontColor('#FFFFC000');
      instance.fontSize(15);
      instance.fontWeight(FontWeight.Bolder);
      instance.fontStyle(FontStyle.Normal);
      instance.textShadow({ radius: 5, offsetX: 9 });
    } else {
      console.info(`testTag subTitle use style2`);
      instance.fontColor('#FF23A98D');
      instance.fontSize(10);
      instance.fontWeight(FontWeight.Lighter);
      instance.fontStyle(FontStyle.Italic);
      instance.textShadow({ radius: 3, offsetX: 3 });
    }
  }
}
```

在src/main目录下的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的module字段里配置"routerMap": "$profile:router_map"，并在src/main/resources/base/profile目录下新增router_map.json。router_map.json示例如下。

```TypeScript
{
  "routerMap": [
    {
      "name": "NavDestinationExample",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "myRouter",
      "data": {
        "description": "this is pageOne"
      }
    }
  ]
}
```

该示例主要实现Navigation简单的自定义转场动画。

```TypeScript
// Index.ets
import { AnimateCallback, CustomTransition } from './CustomTransitionUtils'

@Entry
@Component
struct NavigationCustomTransitionExample {
  pageInfos: NavPathStack = new NavPathStack();

  aboutToAppear() {
    this.pageInfos.pushPath({ name: 'PageOne' }, false);
  }

  build() {
    Navigation(this.pageInfos) {
    }
    .hideNavBar(true)
    .customNavContentTransition((from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) => {
      // 首页不进行自定义动画
      if (from.index === -1 || to.index === -1) {
        return undefined;
      }

      let customAnimation: NavigationAnimatedTransition = {
        timeout: 2000,
        // 转场开始时系统调用该方法，并传入转场上下文代理对象
        transition: (transitionProxy: NavigationTransitionProxy) => {
          if (!from.navDestinationId || !to.navDestinationId) {
            return;
          }
          // 从封装类CustomTransition中根据子页面的序列获取对应的转场动画回调
          let fromParam: AnimateCallback = CustomTransition.getInstance().getAnimateParam(from.navDestinationId);
          let toParam: AnimateCallback = CustomTransition.getInstance().getAnimateParam(to.navDestinationId);
          // Push动画
          if (operation == NavigationOperation.PUSH) {
            if (fromParam.start && toParam.start) {
              // 设置Push转场的两个页面的动画起点
              fromParam.start(true, true);
              toParam.start(true, false);
            }
            this.getUIContext()?.animateTo({
              duration: 500, curve: Curve.Friction, onFinish: () => {
                // 动画结束后需要手动调用finishTransition，否则在timeout时间后由系统调用
                transitionProxy.finishTransition();
              }
            }, () => {
              if (fromParam.finish && toParam.finish) {
                // 设置Push转场的两个页面的动画终点
                fromParam.finish(true, true);
                toParam.finish(true, false);
              }

            })
          } else if (operation == NavigationOperation.POP) {
            // Pop动画
            if (fromParam.start && toParam.start) {
              // 设置Pop转场的两个页面的动画起点
              fromParam.start(false, true);
              toParam.start(false, false);
            }
            this.getUIContext()?.animateTo({
              duration: 500, curve: Curve.Friction, onFinish: () => {
                // 动画结束后需要手动调用finishTransition，否则在timeout时间后由系统调用
                transitionProxy.finishTransition();
              }
            }, () => {
              if (fromParam.finish && toParam.finish) {
                // 设置Pop转场的两个页面的动画终点
                fromParam.finish(false, true);
                toParam.finish(false, false);
              }
            })
          } else {
            // Replace不做动画
          }
        }
      };
      return customAnimation;
    })
  }
}


// PageOne
@Builder
export function PageOneBuilder() {
  PageContainer({ title: 'PageOne' });
}

// PageTwo
@Builder
export function PageTwoBuilder() {
  PageContainer({ title: 'PageTwo' });
}

@Component
export struct PageContainer {
  pageInfos: NavPathStack = new NavPathStack();
  @State translateY: string = '0';
  pageId: string = '';
  title: string = ''

  registerCallback() {
    CustomTransition.getInstance().registerNavParam(this.pageId,
      // 设置转场动画起点，根据不同的转场类型分别设置
      (isPush: boolean, isExit: boolean) => {
        if (isPush) {
          if (isExit) {
            this.translateY = '0';
          } else {
            this.translateY = '100%';
          }
        } else {
          if (isExit) {
            this.translateY = '0';
          } else {
            this.translateY = '0';
          }
        }
      },
      // 设置转场动画终点，根据不同的转场类型分别设置
      (isPush: boolean, isExit: boolean) => {
        if (isPush) {
          if (isExit) {
            this.translateY = '0';
          } else {
            this.translateY = '0';
          }
        } else {
          if (isExit) {
            this.translateY = '100%';
          } else {
            this.translateY = '0';
          }
        }
      });
  }

  build() {
    NavDestination() {
      Column() {
        Button('push next page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.pushPath({ name: this.title == 'PageOne' ? 'PageTwo' : 'PageOne' });
          })
      }
      .size({ width: '100%', height: '100%' })
    }
    .title(this.title)
    .onDisAppear(() => {
      // 页面销毁时解注册自定义转场动画参数
      CustomTransition.getInstance().unRegisterNavParam(this.pageId);
    })
    .onReady((context: NavDestinationContext) => {
      this.pageInfos = context.pathStack;
      if (context.navDestinationId) {
        this.pageId = context.navDestinationId;
        // 页面创建时注册自定义转场动画参数
        this.registerCallback();
      }
    })
    .translate({ y: this.translateY })
    .backgroundColor(this.title == 'PageOne' ? '#F1F3F5' : '#ff11dee5')
  }
}
```

```TypeScript
// src/main/pages/CustomTransitionUtils.ts 工具类，用来管理所有页面的自定义动画参数注册和获取等
// 自定义接口，用来保存某个页面相关的转场动画回调和参数
export interface AnimateCallback {
  start: ((isPush: boolean, isExit: boolean) => void | undefined) | undefined;
  finish: ((isPush: boolean, isExit: boolean) => void | undefined) | undefined;
}

const customTransitionMap: Map<string, AnimateCallback> = new Map();

export class CustomTransition {
  static delegate = new CustomTransition();

  static getInstance() {
    return CustomTransition.delegate;
  }

  /* 注册某个页面的动画回调
   * name: 注册页面的唯一id
   * startCallback：用来设置动画开始时页面的状态
   * endCallback：用来设置动画结束时页面的状态
   */
  registerNavParam(name: string, startCallback: (isPush: boolean, isExit: boolean) => void,
    endCallback: (isPush: boolean, isExit: boolean) => void): void {
    if (customTransitionMap.has(name)) {
      let param = customTransitionMap.get(name);
      if (param != undefined) {
        param.start = startCallback;
        param.finish = endCallback;
        return;
      }
    }
    let params: AnimateCallback = { start: startCallback, finish: endCallback };
    customTransitionMap.set(name, params);
  }

  unRegisterNavParam(name: string): void {
    customTransitionMap.delete(name);
  }

  getAnimateParam(name: string): AnimateCallback {
    let result: AnimateCallback = {
      start: customTransitionMap.get(name)?.start,
      finish: customTransitionMap.get(name)?.finish
    };
    return result;
  }
}
```

在src/main目录下的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的module字段里配置"routerMap": "$profile:router_map"，并在src/main/resources/base/profile目录下新增router_map.json。router_map.json示例如下。

```TypeScript
{
  "routerMap": [
    {
      "name": "PageOne",
      "pageSourceFile": "src/main/ets/pages/Index.ets",
      "buildFunction": "PageOneBuilder",
      "data": {
        "description": "this is pageOne"
      }
    },
    {
      "name": "PageTwo",
      "pageSourceFile": "src/main/ets/pages/Index.ets",
      "buildFunction": "PageTwoBuilder"
    }
  ]
}
```

此示例在运行前需要在工程配置文件[module.json5](../../../quick-start/module-configuration-file.md)中的abilities字段里配置"orientation": "auto_rotation"。

```TypeScript
import { ComponentContent } from '@kit.ArkUI';

@Builder function PlaceholderPage() {
  Column() {
    Text('分栏模式占位页')
      .fontSize(28)
      .fontWeight(700)
      .margin({ top: 200 })
  }.width('100%')
  .height('100%')
}

@Entry
@Component
struct NavigationExample {
  @State minNavBarWidth: Dimension | undefined = undefined;
  @State maxNavBarWidth: Dimension | undefined = undefined;
  @State minContentWidth: Dimension|undefined = undefined;
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  @State currentIndex: number = 0;
  placeholder = new ComponentContent(this.getUIContext(), wrapBuilder(PlaceholderPage))

  @Builder
  NavigationTitle() {
    Column() {
      Text('Title')
        .fontColor('#182431')
        .fontSize(30)
        .lineHeight(41)
        .fontWeight(700)
      Text('subtitle')
        .fontColor('#182431')
        .fontSize(14)
        .lineHeight(19)
        .opacity(0.4)
        .margin({ top: 2, bottom: 20 })
    }.alignItems(HorizontalAlign.Start)
  }

  @Builder
  NavigationMenus() {
    Row() {
      // $r('sys.media.ohos_ic_public_add')需要替换为开发者所需的资源文件
      Image($r('sys.media.ohos_ic_public_add'))
        .width(24)
        .height(24)
      // $r('sys.media.ohos_ic_public_add')需要替换为开发者所需的资源文件
      Image($r('sys.media.ohos_ic_public_add'))
        .width(24)
        .height(24)
        .margin({ left: 24 })
      // $r('sys.media.ohos_ic_public_more')需要替换为开发者所需的资源文件
      Image($r('sys.media.ohos_ic_public_more'))
        .width(24)
        .height(24)
        .margin({ left: 24 })
    }.margin({ top: 30 })
  }

  build() {
    Column() {
      Navigation() {
        TextInput({ placeholder: 'search...' })
          .width('90%')
          .height(40)
          .backgroundColor('#FFFFFF')
          .margin({ top: 8 })

        List({ space: 12, initialIndex: 0 }) {
          ForEach(this.arr, (item: number) => {
            ListItem() {
              Text('' + item)
                .width('90%')
                .height(72)
                .backgroundColor('#FFFFFF')
                .borderRadius(24)
                .fontSize(16)
                .fontWeight(500)
                .textAlign(TextAlign.Center)
            }
          }, (item: number) => item.toString())
        }
        .height(324)
        .width('100%')
        .margin({ top: 12, left: '10%' })
      }
      .title(this.NavigationTitle)
      .padding({ left: 12 })
      .menus(this.NavigationMenus)
      .titleMode(NavigationTitleMode.Full)
      .toolbarConfiguration([
        {
          // $r('app.string.navigation_toolbar_add')和$r('app.media.startIcon')需要替换为开发者所需的图像资源文件
          value: $r('app.string.navigation_toolbar_add'),
          icon: $r('app.media.startIcon')
        },
        {
          // $r('app.string.navigation_toolbar_app')和$r('app.media.startIcon')需要替换为开发者所需的图像资源文件
          value: $r('app.string.navigation_toolbar_app'),
          icon: $r('app.media.startIcon')
        },
        {
          // $r('app.string.navigation_toolbar_collect')和$r('app.media.startIcon')需要替换为开发者所需的图像资源文件
          value: $r('app.string.navigation_toolbar_collect'),
          icon: $r('app.media.startIcon')
        }
      ])
      .mode(NavigationMode.Split) // 设置Navigation模式为Split
      .navBarWidthRange([this.minNavBarWidth, this.maxNavBarWidth]) // 设置导航页宽度范围：[最小宽度, 最大宽度]
      .minContentWidth(this.minContentWidth)
      .hideTitleBar(false)
      .hideToolBar(false)
      .onTitleModeChange((titleModel: NavigationTitleMode) => {
        console.info('titleMode' + titleModel)
      })
      .splitPlaceholder(this.placeholder)
      .divider({ startMargin: 20, endMargin: 20, color: Color.Red}) // 从API version 23开始，新增divider属性。
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F1F3F5')
  }
}
```

在工程配置文件[module.json5](../../../quick-start/module-configuration-file.md)中的abilities字段里配置"orientation": "landscape"（该工程配置仅方便演示在横屏模式下的Navigation工具栏自适应能力，实际配置可自行设置为"auto_rotation"）。

```TypeScript
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct NavigationExample {
  @Provide('navPathStack') navPathStack:NavPathStack = new NavPathStack();
  @State enable: boolean = false
  @State menuItems:Array<NavigationMenuItem> = [
    {
      value:'menuItem1',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.card_writer')),
    },
    {
      value:'menuItem2',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_folder_badge_plus'))
    },
    {
      value:'menuItem3',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_lungs')),
    },
  ]

  @State toolItems:Array<ToolbarItem> = [
    {
      value:'toolItem1',
      symbolIcon:new SymbolGlyphModifier($r('sys.symbol.ohos_lungs')),
      action:()=>{}
    },
    {
      value:'toolItem2',
      symbolIcon:new SymbolGlyphModifier($r('sys.symbol.card_migration')),
      action:()=>{}
    },
    {
      value:'toolItem3',
      symbolIcon:new SymbolGlyphModifier($r('sys.symbol.ohos_star')),
      action:()=>{}
    }
  ]

  build() {
    Navigation(this.navPathStack) {
      Column() {
        Button('启用/关闭自适应').onClick(()=> {
          this.enable = !this.enable;
        })
        Text(`启用自适应能力：${this.enable}`)
      }
    }
    .mode(NavigationMode.Stack)
    .enableToolBarAdaptation(this.enable) // 是否启用工具栏自适应能力
    .backButtonIcon(new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')))
    .titleMode(NavigationTitleMode.Mini)
    .menus(this.menuItems)
    .toolbarConfiguration(this.toolItems)
    .title('一级页面')
  }
}
```

从API version 20开始，新增创建Navigation组件的方式。

```TypeScript
@Component
struct PageHome {
  private stack: NavPathStack | undefined = undefined;

  build() {
    NavDestination() {
      Stack({alignContent: Alignment.Center}) {
        Button('push PageOne').onClick(() => {
          this.stack?.pushPath({name: 'PageOne'});
        })
      }.width('100%').height('100%')
    }.title('PageHome')
    .onReady((ctx: NavDestinationContext) => {
      this.stack = ctx.pathStack;
    })
  }
}

@Builder
function PageHomeBuilder() {
  PageHome()
}

@Component
struct PageOne {
  build() {
    NavDestination() {
      Stack({alignContent: Alignment.Center}) {
        Text('PageOne')
      }.width('100%').height('100%')
    }.title('PageOne')
  }
}

@Builder
function PageOneBuilder() {
  PageOne()
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  build() {
    // 在这里配置主页NavDestination信息
    Navigation(this.stack, { name: 'PageHome' }) {
    }
    .width('100%').height('100%')
  }
}
```

在src/main目录下的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的module字段里配置"routerMap": "$profile:router_map"，并在src/main/resources/base/profile目录下新增router_map.json。router_map.json示例如下。

```TypeScript
{
  "routerMap": [
    {
      "name": "PageHome",
      "pageSourceFile": "src/main/ets/pages/Index.ets",
      "buildFunction": "PageHomeBuilder",
      "data": {
        "description": "this is PageHome"
      }
    },
    {
      "name": "PageOne",
      "pageSourceFile": "src/main/ets/pages/Index.ets",
      "buildFunction": "PageOneBuilder",
      "data": {
        "description": "this is PageOne"
      }
    }
  ]
}
```

从API version 22开始，在setInterception的参数类型[NavigationInterception](arkts-arkui-navigationinterception-i.md)中新增了interception接口。

```TypeScript
// Index.ets
@Entry
@Component
struct NavigationExample {
  pageInfos: NavPathStack = new NavPathStack();
  isUseInterception: boolean = false;

  registerInterception() {
    this.pageInfos.setInterception({
      // 页面创建前拦截，允许操作栈，在当前跳转中生效。
      interception: (from: NavPathInfo | 'navBar', to: NavPathInfo | NavBar, navStack: NavPathStack,
        operation: NavigationOperation, animated: boolean) => {
        if (!this.isUseInterception) {
          return;
        }
        if (typeof to === 'string') {
          return;
        }
        // 重定向目标页面，更改为pageTwo页面到pageOne页面。
        let target: NavPathInfo = to as NavPathInfo;
        let navStacktarget: NavPathStack = navStack as NavPathStack;
        if (target.name === 'pageTwo') {
          navStacktarget.pop();
          navStacktarget.pushPathByName('pageOne', null);
        }
      },
      // 页面跳转后回调，在该回调中操作栈在下一次跳转中刷新。
      didShow: (from: NavDestinationContext | 'navBar', to: NavDestinationContext | 'navBar',
        operation: NavigationOperation, isAnimated: boolean) => {
        if (!this.isUseInterception) {
          return;
        }
        if (typeof from === 'string') {
          console.info('current transition is from navigation home');
        } else {
          console.info(`current transition is from  ${(from as NavDestinationContext).pathInfo.name}`);
          console.info(`current transition mode is to ${(to as NavDestinationContext).mode?.toString()}`);
        }
        if (typeof to === 'string') {
          console.info('current transition to is navBar');
        } else {
          console.info(`current transition is to ${(to as NavDestinationContext).pathInfo.name}`);
          console.info(`current transition mode is to ${(to as NavDestinationContext).mode?.toString()}`);
        }
      },
      // Navigation单双栏显示状态发生变更时触发该回调。
      modeChange: (mode: NavigationMode) => {
        if (!this.isUseInterception) {
          return;
        }
        console.info(`current navigation mode is ${mode}`);
      }
    })
  }

  build() {
    Navigation(this.pageInfos) {
      Column() {
        Button('pushPath', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.pushPath({ name: 'pageOne' }); // 将name指定的NavDestination页面信息入栈。
          })
        Button('use interception', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.isUseInterception = !this.isUseInterception;
            if (this.isUseInterception) {
              this.registerInterception();
            } else {
              this.pageInfos.setInterception(undefined);
            }
          })
      }
    }.title('NavIndex')
  }
}
```

```TypeScript
// PageOne.ets
class PageParam {
  count: number = 10;
}

@Builder
export function PageOneBuilder(name: string, param: Object) {
  PageOne()
}

@Component
export struct PageOne {
  pageInfos: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Button('pushPathByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            let pageParam = new PageParam();
            this.pageInfos.pushPathByName('pageTwo', pageParam); // 将name指定的NavDestination页面信息入栈，传递的数据为param。
          })
        Button('singletonLaunchMode', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.pushPath({ name: 'pageOne' },
              { launchMode: LaunchMode.MOVE_TO_TOP_SINGLETON }); // 从栈底向栈顶查找，如果指定的名称已经存在，则将对应的NavDestination页面移到栈顶。
          })
        Button('popToname', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.popToName('pageTwo'); // 回退路由栈到第一个名为name的NavDestination页面。
            console.info('popToName' + JSON.stringify(this.pageInfos),
              '返回值' + JSON.stringify(this.pageInfos.popToName('pageTwo')));
          })
        Button('popToIndex', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.popToIndex(1); // 回退路由栈到index指定的NavDestination页面。
            console.info('popToIndex' + JSON.stringify(this.pageInfos));
          })
        Button('moveToTop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.moveToTop('pageTwo'); // 将第一个名为name的NavDestination页面移到栈顶。
            console.info('moveToTop' + JSON.stringify(this.pageInfos),
              '返回值' + JSON.stringify(this.pageInfos.moveToTop('pageTwo')));
          })
        Button('moveIndexToTop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.moveIndexToTop(1); // 将index指定的NavDestination页面移到栈顶。
            console.info('moveIndexToTop' + JSON.stringify(this.pageInfos));
          })
        Button('clear', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.clear(); // 清除栈中所有页面。
          })
        Button('get', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            console.info('-------------------');
            console.info('获取栈中所有NavDestination页面的名称', JSON.stringify(this.pageInfos.getAllPathName()));
            console.info('获取index指定的NavDestination页面的参数信息',
              JSON.stringify(this.pageInfos.getParamByIndex(1)));
            console.info('获取全部名为name的NavDestination页面的参数信息',
              JSON.stringify(this.pageInfos.getParamByName('pageTwo')));
            console.info('获取全部名为name的NavDestination页面的位置索引',
              JSON.stringify(this.pageInfos.getIndexByName('pageOne')));
            console.info('获取栈大小', JSON.stringify(this.pageInfos.size()));
          })
      }.width('100%').height('100%')
    }.title('pageOne')
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // 弹出路由栈栈顶元素。
      console.info('pop' + '返回值' + JSON.stringify(popDestinationInfo));
      return true;
    }).onReady((context: NavDestinationContext) => {
      this.pageInfos = context.pathStack;
    })
  }
}
```

```TypeScript
// PageTwo.ets
@Builder
export function PageTwoBuilder(name: string, param: Object) {
  PageTwo()
}

@Component
export struct PageTwo {
  pathStack: NavPathStack = new NavPathStack();
  private menuItems: Array<NavigationMenuItem> = [
    {
      value: '1',
      icon: 'resources/base/media/undo.svg',
    },
    {
      value: '2',
      icon: 'resources/base/media/redo.svg',
      isEnabled: false,
    },
    {
      value: '3',
      icon: 'resources/base/media/ic_public_ok.svg',
      isEnabled: true,
    }
  ];

  build() {
    NavDestination() {
      Column() {
        Button('pushPathByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.pushPathByName('pageOne', null);
          })
      }.width('100%').height('100%')
    }.title('pageTwo')
    .menus(this.menuItems)
    .onBackPressed(() => {
      this.pathStack.pop();
      return true;
    })
    .onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
      console.info('current page config info is ' + JSON.stringify(context.getConfigInRouteMap()));
    })
  }
}
```

在src/main目录下的工程配置文件[module.json5](../../../quick-start/module-configuration-file.md)中的module字段里配置"routerMap": "$profile:router_map"。

```TypeScript
// src/main/resources/base/profile/router_map.json
{
  "routerMap": [
    {
      "name": "pageOne",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "PageOneBuilder",
      "data": {
        "description": "this is pageOne"
      }
    },
    {
      "name": "pageTwo",
      "pageSourceFile": "src/main/ets/pages/PageTwo.ets",
      "buildFunction": "PageTwoBuilder"
    }
  ]
}
```

从API version 14开始，新增recoverable接口。

```TypeScript
// Index.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct NavigationExample {
  navPathStack: NavPathStack = new NavPathStack();
  @State menuItems: Array<NavigationMenuItem> = [
    {
      // 'resources/base/media/startIcon.png'需要替换为开发者所需的资源文件
      value: 'menuItem1',
      icon: 'resources/base/media/startIcon.png' // 图标资源路径
    },
    {
      // resources/base/media/ic_public_ok.svg'需要替换为开发者所需的资源文件
      value: 'menuItem2',
      icon: 'resources/base/media/ic_public_ok.svg', // 图标资源路径
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_folder_badge_plus')).fontColor([Color.Red, Color.Green])
        .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_COLOR),
    },
    {
      value: 'menuItem3',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_lungs')),
    },
  ];
  @State toolItems: Array<ToolbarItem> = [
    {
      // 'resources/base/media/ic_public_ok.svg'需要替换为开发者所需的资源文件
      value: 'toolItem1',
      icon: 'resources/base/media/ic_public_ok.svg', // 图标资源路径
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_lungs')),
      status: ToolbarItemStatus.ACTIVE,
      activeSymbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_folder_badge_plus')).fontColor([Color.Red,
        Color.Green]).renderingStrategy(SymbolRenderingStrategy.MULTIPLE_COLOR),
      action: () => {
      }
    },
    {
      // 'resources/base/media/startIcon.png'需要替换为开发者所需的资源文件
      value: 'toolItem2',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_star')),
      status: ToolbarItemStatus.ACTIVE,
      activeIcon: 'resources/base/media/startIcon.png', // 图标资源路径
      action: () => {
      }
    },
    {
      value: 'toolItem3',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_star')),
      status: ToolbarItemStatus.ACTIVE,
      activeSymbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_lungs')),
      action: () => {
      }
    }
  ];

  build() {
    Navigation(this.navPathStack) {
      Column() {
        Button('跳转').onClick(() => {
          this.navPathStack.pushPathByName('NavigationMenu', null);
        })
      }
    }
    .backButtonIcon(new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')))
    .titleMode(NavigationTitleMode.Mini)
    .menus(this.menuItems)
    .toolbarConfiguration(this.toolItems)
    .title('一级页面')
    .id('test')
    .recoverable(true)
  }
}
```

```TypeScript
// PageOne.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Builder
export function myRouter(name: string, param?: Object) {
  NavigationMenu();
}

@Component
export struct NavigationMenu {
  navPathStack: NavPathStack = new NavPathStack();
  @State menuItems: Array<NavigationMenuItem> = [
    {
      // 'resources/base/media/startIcon.png'需要替换为开发者所需的资源文件
      value: 'menuItem1',
      icon: 'resources/base/media/startIcon.png', // 图标资源路径
      action: () => {
      }
    },
    {
      value: 'menuItem2',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_folder_badge_plus')).fontColor([Color.Red, Color.Green])
        .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_COLOR),
      action: () => {
      }
    },
    {
      value: 'menuItem3',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.repeat_1')),
      action: () => {
      }
    },
  ];

  build() {
    NavDestination() {
      Row() {
        Column() {
        }
        .width('100%')
      }
      .height('100%')
    }
    .onReady((context: NavDestinationContext) => {
      this.navPathStack = context.pathStack;
    })
    .hideTitleBar(false)
    .title('NavDestination title')
    .backgroundColor($r('sys.color.ohos_id_color_titlebar_sub_bg'))
    .backButtonIcon(new SymbolGlyphModifier($r('sys.symbol.ohos_star'))
    .fontColor([Color.Blue]))
    .menus(this.menuItems)
    .recoverable(true)
  }
}
```

在src/main目录下[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的module字段里配置"routerMap": "$profile:router_map"，并在src/main/resources/base/profile目录下新增router_map.json文件。示例如下：

```TypeScript
{
  "routerMap": [
    {
      "name": "NavigationMenu",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "myRouter",
      "data": {
        "description": "this is pageOne"
      }
    }
  ]
}
```

从API版本26.0.0开始，[title](#title)接口的参数options，新增了[scrollEffectOptions](#scrolleffectoptions)属性。

```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI'

@Entry
@Component
struct NavigationExample {
  private arr: number[] = [];

  aboutToAppear(): void {
    for (let i = 0; i < 50; i++) {
      this.arr.push(i)
    }
  }

  build() {
    Column() {
      Navigation() {
        Column() {
          List({ space: 12, initialIndex: 0 }) {
            ListItem() {
              Column() {
                Blank()
                  .width('100%')
                  .height(128)
              }
            }
            ForEach(this.arr, (item: number) => {
              ListItem() {
                Text('' + item)
                  .width('90%')
                  .height(72)
                  .backgroundColor($r('sys.color.brand'))
                  .borderRadius(24)
                  .fontSize(16)
                  .fontWeight(500)
                  .textAlign(TextAlign.Center)
              }
            }, (item: number) => item.toString())
          }
          .height('100%')
          .width('100%')
        }
        .width('100%')
        .height('100%')
      }
      .title({ main: 'Main Title', sub: 'Sub Title' }, {
        barStyle: BarStyle.STACK,
        scrollEffectOptions: {
          scrollEffectType: ScrollEffectType.COMMON_BLUR,
          blurEffectiveStartOffset: LengthMetrics.vp(8),
          blurEffectiveEndOffset: LengthMetrics.vp(56)
        }
      })
      .titleMode(NavigationTitleMode.Full)
      .hideTitleBar(false)
      .hideToolBar(false)
    }.width('100%').height('100%').backgroundColor('#F1F3F5')
  }
}
```

从API版本26.0.0开始，[NavigationTitleOptions](arkts-arkui-navigationtitleoptions-i.md)新增了systemMaterial属性。

```TypeScript
// xxx.ets
import { SymbolGlyphModifier, uiMaterial } from '@kit.ArkUI';

function BuildMenu(): Array<NavigationMenuItem> {
  return [
    {
      value: 'menu1',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_circle'))
    },
    {
      value: 'menu2',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_star'))
    },
    {
      value: 'menu3',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_folder_badge_plus'))
    },
    {
      value: 'menu4',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_lock'))
    }
  ]
}

@Component
struct TestComponent {
  private arr: number[] = new Array<number>();

  aboutToAppear(): void {
    for (let i = 0; i < 20; i++) {
      this.arr.push(i);
    }
  }

  build() {
    Scroll() {
      Column() {
        ForEach(this.arr, (item: number) => {
          Stack() {
            Text(item.toString())
              .fontSize(20)
              .fontWeight(FontWeight.Bold)
              .fontColor((item % 2) == 1 ? '#fff5e4e4' : '#ff302a2a')
          }.width('100%')
          .height(180)
          .backgroundColor((item % 2) == 0 ? '#fff5e4e4' : '#ff302a2a')
        }, (item: number) => item.toString())
      }
    }
  }
}

@Component
struct MyDest {
  build() {
    NavDestination() {
      TestComponent().width('100%').height('100%')
    }.width('100%').height('100%')
    .title('', {
      systemMaterial: new uiMaterial.ImmersiveMaterial({
        style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
        colorInvert: true,
        interactive: true,
        lightEffect: {}
      }),
      // systemMaterial和barStyle没有关联性，但是同时设置barStyle为STACK样式可获得最佳沉浸效果
      barStyle: BarStyle.STACK
    })
    .menus(BuildMenu())
  }
}

@Entry
@Component
struct NavigationTitleMaterialDemo {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  MyMap(name: string) {
    MyDest()
  }

  build() {
    RelativeContainer() {
      Navigation(this.stack) {
        Column() {
          TestComponent()
            .width('100%')
        }.width('100%').height('100%')
      }
      .width('100%')
      .height('100%')
      .mode(NavigationMode.Stack)
      .navDestination(this.MyMap)
      .title('', {
        systemMaterial: new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          colorInvert: true,
          interactive: true,
          lightEffect: {}
        }),
        // systemMaterial和barStyle没有关联性，但是同时设置barStyle为STACK样式可获得最佳沉浸效果
        barStyle: BarStyle.STACK
      })
      .menus(BuildMenu())
      Column() {
        Stack({alignContent: Alignment.Center}) {
          Text('push page').fontSize(25)
        }
        .width(150)
        .height(50)
        .borderRadius(22)
        .backgroundColor(Color.Orange)
        .margin({left: 50, bottom: 100})
        .onClick(() => {
          this.stack.pushPath({name: 'one'})
        })
      }
      .alignRules({
        bottom: {anchor: '__container__', align: VerticalAlign.Bottom},
        left: {anchor: '__container__', align: HorizontalAlign.Start},
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

从API版本26.1.0开始，[NavigationConfiguration](arkts-arkui-navigationconfiguration-i.md)新增了clearContentStackOnPrimaryNavigation属性。

```TypeScript
// xxx.ets
@Component
struct MyControlPanel {
  private stack: NavPathStack | undefined = undefined;

  aboutToAppear(): void {
    let info = this.queryNavigationInfo();
    if (info) {
      this.stack = info.pathStack;
    }
  }

  build() {
    Column() {
      Button('push pageOne').onClick(() => {
        this.stack?.pushPath({name: 'one'})
      })
        .margin({top: 25})
      Button('push pageTwo').onClick(() => {
        this.stack?.pushPath({name: 'two'})
      })
        .margin({top: 25})
      Button('pop').onClick(() => {
        this.stack?.pop()
      })
        .margin({top: 25})
    }
  }
}

@Component
struct MyPageOne {
  build() {
    NavDestination() {
      Column() {
        MyControlPanel()
      }
      .width('100%')
      .height('100%')
    }
    .width('100%')
    .height('100%')
    .title('PageOne')
  }
}

@Component
struct MyPageTwo {
  build() {
    NavDestination() {
      Column() {
        MyControlPanel()
      }
      .width('100%')
      .height('100%')
    }
    .width('100%')
    .height('100%')
    .title('PageTwo')
  }
}

@Entry
@Component
struct NavigationConfig {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  MyDestMap(name: string) {
    if (name === 'one') {
      MyPageOne()
    } else {
      MyPageTwo()
    }
  }

  build() {
    Navigation(this.stack) {
      Column() {
        MyControlPanel()
      }
      .width('100%')
      .height('100%')
    }
    .width('100%')
    .height('100%')
    .title('NavBar')
    .titleMode(NavigationTitleMode.Mini)
    .mode(NavigationMode.Split)
    .navDestination(this.MyDestMap)
    .configuration({
      clearContentStackOnPrimaryNavigation: true
    })
  }
}
```
