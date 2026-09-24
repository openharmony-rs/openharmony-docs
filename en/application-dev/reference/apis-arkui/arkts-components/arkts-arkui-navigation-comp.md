# Navigation

The **Navigation** component is the root view container for navigation. It typically functions as the root container of a page and includes a title bar, content area, and toolbar. The content area switches between the home page content (child components of **Navigation**) and non-home page content (child components of NavDestination) through routing.

> **NOTE**

> - Since API version 11, this component supports the safe area attribute by default, with the default attribute > value being > **expandSafeArea([SafeAreaType.SYSTEM, SafeAreaType.KEYBOARD, SafeAreaType.CUTOUT], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM])**. > You can override this attribute to change the default behavior. In earlier versions, you need to use the > [expandSafeArea](arkts-arkui-common-comp-commonmethod-c.md#expandsafearea) attribute to implement the safe area feature. > > - When [NavBar](arkts-arkui-navigation-comp-navbar-t.md) is nested within a **Navigation** component, the lifecycle of the inner > **NavDestination** component does not synchronize with the outer **NavDestination** component or the lifecycle of a > modal. > > - If the [title](arkts-arkui-navigation-comp-attribute.md#title) and [subTitle](arkts-arkui-navigation-comp-attribute.md#subtitle) are not set > and [hideBackButton](arkts-arkui-navigation-comp-attribute.md#hidebackbutton) is set to **true**, the title bar is not displayed. > > - During subpage navigation within **Navigation**, the new page actively requests focus. > > - You are not advised to use stack operations in [aboutToAppear](arkts-arkui-common-comp-basecustomcomponent-c.md#abouttoappear), as the > page has not yet finished building at this stage, which may lead to issues such as white screens or navigation > failures.

## Child Components

Supported

Since API version 9, it is recommended that this component be used together with the NavRouter component.

Since API version 10, it is recommended that this component be used together with the [NavPathStack](arkts-arkui-navigation-comp-navpathstack-c.md) component and [navDestination](arkts-arkui-navigation-comp-attribute.md#navdestination) attribute for page routing.

## Navigation

```TypeScript
Navigation()
```

Creates a root view container for route navigation, suitable for page routing using the NavRouter component.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack)
```

Binds a navigation controller to the **Navigation** component, suitable for page routing using [NavPathStack](arkts-arkui-navigation-comp-navpathstack-c.md) with the [navDestination](arkts-arkui-navigation-comp-attribute.md#navdestination) attribute.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pathInfos | [NavPathStack](arkts-arkui-navigation-comp-navpathstack-c.md) | Yes | Navigation controller object. |

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack, homeDestination: HomePathInfo)
```

Binds a routing stack to the **Navigation** component and specifies a **NavDestination** component as the navigation page (home page) for **Navigation**. This is suitable for page routing using [NavPathStack](arkts-arkui-navigation-comp-navpathstack-c.md) with the [navDestination](arkts-arkui-navigation-comp-attribute.md#navdestination) attribute or the system routing table. For the usage example, see [Example 16: Using NavDestination as a Navigation Page in Navigation](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-16-using-navdestination-as-a-navigation-page-in-navigation).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pathInfos | [NavPathStack](arkts-arkui-navigation-comp-navpathstack-c.md) | Yes | Information about the routing stack. |
| homeDestination | [HomePathInfo](arkts-arkui-navigation-comp-homepathinfo-i.md) | Yes | Home page **NavDestination** information. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [HomePathInfo](arkts-arkui-navigation-comp-homepathinfo-i.md) | Defines the home page **NavDestination** information. |
| [MoreButtonOptions](arkts-arkui-navigation-comp-morebuttonoptions-i.md) | Defines the options for the more button menu. |
| [NavContentInfo](arkts-arkui-navigation-comp-navcontentinfo-i.md) | Provides the destination information. |
| [NavigationAnimatedTransition](arkts-arkui-navigation-comp-navigationanimatedtransition-i.md) | Defines the custom transition animation protocol. You need to implement this protocol to define the redirection animation of the navigation route. |
| [NavigationCommonTitle](arkts-arkui-navigation-comp-navigationcommontitle-i.md) | Defines a general title for the **Navigation** component. |
| [NavigationConfiguration](arkts-arkui-navigation-comp-navigationconfiguration-i.md) | Navigation configuration options. |
| [NavigationCustomTitle](arkts-arkui-navigation-comp-navigationcustomtitle-i.md) | Defines a custom title for the **Navigation** component. |
| [NavigationDividerStyle](arkts-arkui-navigation-comp-navigationdividerstyle-i.md) | Color of the navigation divider and the upper and lower margins of the **Navigation** component. |
| [NavigationInterception](arkts-arkui-navigation-comp-navigationinterception-i.md) | Describes the object to be intercepted during navigation redirection. |
| [NavigationMenuItem](arkts-arkui-navigation-comp-navigationmenuitem-i.md) | Defines the navigation menu item, including the menu icon and menu information. |
| [NavigationMenuOptions](arkts-arkui-navigation-comp-navigationmenuoptions-i.md) | Defines options for menu items in the upper right corner of the page. |
| [NavigationOptions](arkts-arkui-navigation-comp-navigationoptions-i.md) | Defines the routing stack operation options. |
| [NavigationTitleOptions](arkts-arkui-navigation-comp-navigationtitleoptions-i.md) | Defines the title bar options. |
| [NavigationToolbarOptions](arkts-arkui-navigation-comp-navigationtoolbaroptions-i.md) | Defines the toolbar options. |
| [NavigationTransitionProxy](arkts-arkui-navigation-comp-navigationtransitionproxy-i.md) | Implements a custom transition animation proxy. |
| [PopInfo](arkts-arkui-navigation-comp-popinfo-i.md) | Provides the callback information returned when a page is popped out of the routing stack. |
| [PreloadOptions](arkts-arkui-navigation-comp-preloadoptions-i.md) | Indicates options for preloading a page. |
| [ScrollEffectOptions](arkts-arkui-navigation-comp-scrolleffectoptions-i.md) | Defines the scroll effect options for the title bar. |
| [ToolbarItem](arkts-arkui-navigation-comp-toolbaritem-i.md) | Provides customizable parameters of the toolbar. |

### Types

| Name | Description |
| --- | --- |
| [InterceptionCallback](arkts-arkui-navigation-comp-interceptioncallback-t.md) | Defines the callback triggered before a navigation page is redirected. |
| [InterceptionModeCallback](arkts-arkui-navigation-comp-interceptionmodecallback-t.md) | Implements an interception callback invoked when the display mode of the **Navigation** component switches between single-column and split-column. |
| [InterceptionShowCallback](arkts-arkui-navigation-comp-interceptionshowcallback-t.md) | Represents the interception callback invoked before and after page redirection. |
| [Material](arkts-arkui-navigation-comp-material-t.md) | Import the Material type for Navigation. |
| [NavBar](arkts-arkui-navigation-comp-navbar-t.md) | Defines the name of the navigation home page. |
| [SystemBarStyle](arkts-arkui-navigation-comp-systembarstyle-t.md) | Describes the properties of the status bar. These properties are valid for the page-level status bar. |

### Enums

| Name | Description |
| --- | --- |
| [BarStyle](arkts-arkui-navigation-comp-barstyle-e.md) | Enumerates the layout styles of the title bar and toolbar. Note that this API is not supported for the toolbar in **NavDestination**. |
| [LaunchMode](arkts-arkui-navigation-comp-launchmode-e.md) | Enumerates the operation modes for the routing stack. |
| [NavBarPosition](arkts-arkui-navigation-comp-navbarposition-e.md) | Position of the navigation page. |
| [NavigationMode](arkts-arkui-navigation-comp-navigationmode-e.md) | Display mode of the navigation page. When **Navigation** is displayed in split-column mode, a divider is displayed between the navigation page and the content area. |
| [NavigationOperation](arkts-arkui-navigation-comp-navigationoperation-e.md) | Enumerates the page redirection types. |
| [NavigationTitleMode](arkts-arkui-navigation-comp-navigationtitlemode-e.md) | Enumerates the display modes of the title bar. |
| [ScrollEffectType](arkts-arkui-navigation-comp-scrolleffecttype-e.md) | Enumerates the scroll effect types. |
| [ToolbarItemStatus](arkts-arkui-navigation-comp-toolbaritemstatus-e.md) | Enumerates the toolbar item states. |

## Examples

### Example 1: Implementing a Navigation Page Layout

This example demonstrates the layout of a navigation page, including the title bar ([title](#title)), menu bar ([menus](#menus)), content area, and toolbar ([toolbarConfiguration](#toolbarconfiguration10)).



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
      // Replace 'resources/base/media/ic_public_add.svg' with the resource file you use.
      Image('resources/base/media/ic_public_add.svg')
        .width(24)
        .height(24)
      // Replace 'resources/base/media/ic_public_add.svg' with the resource file you use.
      Image('resources/base/media/ic_public_add.svg')
        .width(24)
        .height(24)
        .margin({ left: 24 })
      // Replace 'resources/base/media/ic_public_more.svg' with the image resource file you use.
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
          // Replace $r('app.string.navigation_toolbar_add') and $r('app.media.ic_public_highlights_ed') with the image resource file you use.
          value: $r('app.string.navigation_toolbar_add'),
          icon: $r('app.media.ic_public_highlights_ed')
        },
        {
          // Replace $r('app.string.navigation_toolbar_app') and $r('app.media.ic_public_highlights') with the image resource file you use.
          value: $r('app.string.navigation_toolbar_app'),
          icon: $r('app.media.ic_public_highlights')
        },
        {
          // Replace $r('app.string.navigation_toolbar_collect') and $r('app.media.ic_public_highlights') with the image resource file you use.
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

### Example 2: Using NavPathStack APIs

This example demonstrates the use of methods in [NavPathStack](#navpathstack10) and route interception.

```TypeScript
// Index.ets
@Entry
@Component
struct NavigationExample {
  pageInfos: NavPathStack = new NavPathStack();
  isUseInterception: boolean = false;

  registerInterception() {
    this.pageInfos.setInterception({
      // Interception before page redirection, allowing for stack operations. The setting takes effect in the current redirection.
      willShow: (from: NavDestinationContext | 'navBar', to: NavDestinationContext | 'navBar',
        operation: NavigationOperation, animated: boolean) => {
        if (!this.isUseInterception) {
          return;
        }
        if (typeof to === 'string') {
          console.info('target page is navigation home');
          return;
        }
        // Redirect the target page from pageTwo to pageOne.
        let target: NavDestinationContext = to as NavDestinationContext;
        if (target.pathInfo.name === 'pageTwo') {
          target.pathStack.pop();
          target.pathStack.pushPathByName('pageOne', null);
        }
      },
      // Callback invoked after the page is navigated. Stack operations in this callback are effective in the next navigation.
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
      // Callback invoked when the display mode of the Navigation component switches between single-column and split-column.
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
            this.pageInfos.pushPath({ name: 'pageOne' }); // Push the navigation destination page specified by name to the stack.
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
            this.pageInfos.pushPathByName('pageTwo', pageParam); // Push the navigation destination page specified by name, with the data specified by param, to the stack.
          })
        Button('singletonLaunchMode', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.pushPath({ name: 'pageOne' },
              { launchMode: LaunchMode.MOVE_TO_TOP_SINGLETON }); // Search from the bottom to the top of the stack. If the page with the specified name exists, move that page to the top of the stack.
          })
        Button('popToname', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.popToName('pageTwo'); // Pop the routing stack back to the first navigation destination page that matches the value of name.
            console.info(`popToName ${JSON.stringify(this.pageInfos)},` + 
              `Return value ${JSON.stringify(this.pageInfos.popToName('pageTwo'))}`); 
          })
        Button('popToIndex', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.popToIndex(1); // Return the routing stack to the navigation destination page that matches the value of index.
            console.info(`popToIndex ${JSON.stringify(this.pageInfos)}`);
          })
        Button('moveToTop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.moveToTop('pageTwo'); // Move the first navigation destination page that matches the value of name to the top of the routing stack.
            console.info(`moveToTop ${JSON.stringify(this.pageInfos)},` + 
              `Return value ${JSON.stringify(this.pageInfos.popToName('pageTwo'))}`); 
          })
        Button('moveIndexToTop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.moveIndexToTop(1); // Move to the top of the routing stack the navigation destination page that matches the value of index.
            console.info(`moveIndexToTop ${JSON.stringify(this.pageInfos)}`);
          })
        Button('clear', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.clear(); // Clear the routing stack.
          })
        Button('get', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            console.info('-------------------');
            console.info(`Obtain names of all NavDestination pages in the stack ${JSON.stringify(this.pageInfos.getAllPathName())}`);
            console.info(`Obtained parameter information of the navigation destination page specified by index ${JSON.stringify(this.pageInfos.getParamByIndex(1))}`);
            console.info(`Obtained parameter information of all the navigation destination pages specified by name ${JSON.stringify(this.pageInfos.getParamByName('pageTwo'))}`);
            console.info(`Obtained the index information of all the navigation destination pages specified by name ${JSON.stringify(this.pageInfos.getIndexByName('pageOne'))}`);
            console.info(`Obtain the stack size ${JSON.stringify(this.pageInfos.size())}`);
          })
      }.width('100%').height('100%')
    }.title('pageOne')
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // Pop the top element out of the routing stack.
      console.info(`pop return value ${JSON.stringify(popDestinationInfo)}`);
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
      // Replace 'resources/base/media/undo.svg' with the image resource file you use.
      value: '1',
      icon: 'resources/base/media/undo.svg',
    },
    {
      // Replace 'resources/base/media/redo.svg' with the image resource file you use.
      value: '2',
      icon: 'resources/base/media/redo.svg',
      isEnabled: false,
    },
    {
      // Replace 'resources/base/media/ic_public_ok.svg' with the image resource file you use.
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

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 3: Setting an Interactive Transition Animation

This sample demonstrates how to set a custom transition animation and an interactive transition animation for each [NavDestination](ts-basic-components-navdestination.md) page.

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

      // No custom animation for the home page
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
        // Called when transition starts. The transition context proxy object is passed in.
        transition: (transitionProxy: NavigationTransitionProxy) => {
          if (!from.navDestinationId || !to.navDestinationId) {
            return;
          }
          // Obtain the corresponding transition animation callback from the CustomTransition class by subpage ID.
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
            // Push the navigation destination page specified by name, with the data specified by param, to the routing stack.
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
            // Push the navigation destination page specified by name, with the data specified by param, to the routing stack.
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
// Custom API to save the transition animation callback and parameters related to a page.

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

  /* Register animation callbacks for a page.
   * name: unique ID of the target page
   * startCallback: used to set the page state at the start of the animation.
   * endCallback: used to set the page state at the end of the animation.
   * onFinish: used to perform other operations after the animation ends.
   * interactiveCallback: used to handle the interactive part of the transition.
   * timeout: timeout for ending the transition.
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

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 4: Implementing a Navigation Component with Parameter Returning

This example demonstrates how to use the APIs in [NavPathStack](#navpathstack10) to pass parameters back to the previous page.

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
            this.pageInfo.pushPath({ name: 'pageOne' }); // Push the navigation destination page specified by name to the routing stack.
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
            }); // Push the navigation destination page specified by name, with the data specified by param, to the routing stack. Use the onPop callback to receive the page processing result.
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
            }); // Push the navigation destination page specified by name, with the data specified by param, to the routing stack. Use the onPop callback to receive the page processing result.
          })

        Button('pushDestination', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            let pageParam = new PageParam();
            // Push the navigation destination page specified by name, with the data specified by param, to the routing stack. Use the onPop callback to receive the page processing result.
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
            // Push the navigation destination page specified by name, with the data specified by param, to the routing stack. Use the onPop callback to receive the page processing result.
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
            this.pageInfo.pushPath({ name: 'pageTwo', param: new ParamWithOp() }); // Push the navigation destination page specified by name to the routing stack.
          })

        Button('pushPathByNameWithoutOnPop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            let pageParam = new PageParam();
            this.pageInfo.pushPathByName('pageTwo', pageParam); // Push the navigation destination page specified by name, with the data specified by param, to the routing stack.
          })

        Button('pushDestinationWithoutOnPop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(10)
          .onClick(() => {
            let pageParam = new PageParam();
            // Push the navigation destination page specified by name, with the data specified by param, to the routing stack.
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
            // Push the navigation destination page specified by name, with the data specified by param, to the routing stack.
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
            this.pageInfo.clear(); // Clear the routing stack.
          })
      }.width('100%').height('100%')
    }.title('pageOne')
    .onBackPressed(() => {
      this.pageInfo.pop({ number: 1 }); // Pop the top element out of the routing stack.
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
            this.pathStack.pop(new ResultClass(1)); // Return to the previous page and pass in the processing result to the onPop callback of push.
          })

        Button('popToName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.popToName('pageOne',
              new ResultClass(11)); // Pop the routing stack back to the first navigation destination page specified by name and pass the processing result to the onPop callback of push.
          })

        Button('popToIndex', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.popToIndex(0, new ResultClass(111)); // Pop the routing stack back to the navigation destination page specified by index and pass the processing result to the onPop callback of push.
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
      this.pathStack.pop(new ResultClass(0)); // Pop to the previous page and pass in the processing result to the onPop callback of push.
      return true;
    }).onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
    })
  }
}
```

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 5: Setting the Background Color and Blur Effect

This example demonstrates how to set the background color and background blur effect for the title bar of the home page in Navigation, as well as for the toolbar and the title bars on the [NavDestination](ts-basic-components-navdestination.md) pages.

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
    // You can set the background color and background blur style of the title bar.
    .title('NavTitle', {
      backgroundColor: this.useColor1 ? COLOR1 : COLOR2,
      backgroundBlurStyle: this.useBlur1 ? BLUR_STYLE_1 : BLUR_STYLE_2,
      barStyle: BarStyle.STACK,
      backgroundBlurStyleOptions: this.useBlurOption1 ? BLUR_STYLE_OPTION_1 : BLUR_STYLE_OPTION_2,
    })
    // You can set the background color and background blur style for the menu
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
    // You can set the background color and background blur style of the toolbar.
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
      // You can set the background color and background blur style for the menu in the toolbar.
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
    // You can set the background color and background blur style of the title bar.
    .title('Destination Title', {
      backgroundColor: this.useColor1 ? COLOR1 : COLOR2,
      backgroundBlurStyle: this.useBlur1 ? BLUR_STYLE_1 : BLUR_STYLE_2,
      barStyle: BarStyle.STACK,
      backgroundEffect: this.useEffect1 ? EFFECT_OPTION_1 : EFFECT_OPTION_2,
    })
    // You can set the background color and background blur style for the menu
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
    // You can set the background color and background blur style of the toolbar.
    .toolbarConfiguration([
      { value: 'A' },
      { value: 'B' },
      { value: 'C' },
      { value: 'D' },
      { value: 'E' },
      { value: 'F' }
    ], {
      backgroundEffect: this.useEffect1 ? EFFECT_OPTION_1 : EFFECT_OPTION_2,
      // You can set the background color and background blur style for the menu in the toolbar.
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

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 6: Obtaining the Outer Stack for a Nested Navigation Component

This example shows how to obtain the parent [NavPathStack](#navpathstack10) for a nested Navigation component.

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
              // The parent navigation path stack can be obtained.
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

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 7: Obtaining the Stack Through onReady

This example demonstrates the following:

The routing stack operation can be conducted even when [NavPathStack](#navpathstack10) is not declared as a state variable.

[NavDestination](ts-basic-components-navdestination.md) can obtain the corresponding [NavPathInfo](arkts-arkui-navigation-comp-navpathinfo-c.md) and its belonging [NavPathStack](#navpathstack10) via the [onReady](ts-basic-components-navdestination.md#onready11) event.

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
      // The passed NavPathInfo and the owning NavPathStack objects can be obtained for <NavDestination>.
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

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 8: Using NavDestination Lifecycle Callbacks

This example demonstrates the timing of the [NavDestination](ts-basic-components-navdestination.md) component lifecycle callbacks: [onAppear](ts-universal-events-show-hide.md#onappear), [onDisAppear](ts-universal-events-show-hide.md#ondisappear), [onShown](ts-basic-components-navdestination.md#onshown10), [onHidden](ts-basic-components-navdestination.md#onhidden10), [onWillAppear](ts-basic-components-navdestination.md#onwillappear12), [onWillDisappear](ts-basic-components-navdestination.md#onwilldisappear12), [onWillShow](ts-basic-components-navdestination.md#onwillshow12), and [onWillHide](ts-basic-components-navdestination.md#onwillhide12).

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
    // onReady is called before onAppear.
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

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 9: Configuring the Title Bar Stack Layout

This example demonstrates the stack layout of the title bar in the Navigation component.



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
              // Replace $r('app.media.image_1') with the resource file you use.
              Image($r('app.media.image_1'))// Set the height to be the same as that of the title bar to observe the STACK effect.
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

### Example 10: Defining a Derived Class of NavPathStack

This example demonstrates how to define a derived class of [NavPathStack](#navpathstack10) and the basic usage of the derived class in Navigation.

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
      // Obtain the derived stack from navdestinationContext.
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
  // Set the custom unique ID.
  id: string = '__default__';

  // Custom method for the derived class.
  setId(id: string) {
    this.id = id;
  }

  // Custom method for the derived class.
  getInfo(): string {
    return `this page used Derived NavPathStack, id: ${this.id}`;
  }

  // Overload the method inherited from the NavPathStack base class.
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

  // Override and overload the method inherited from the NavPathStack base class.
  pop(animated?: boolean | undefined): NavPathInfo | undefined
  pop(result: Object, animated?: boolean | undefined): NavPathInfo | undefined
  pop(result?: Object, animated?: boolean | undefined): NavPathInfo | undefined {
    console.info('[derive-test] reached DerivedNavPathStack\'s pop');
    return super.pop(result, animated);
  }

  // Remaining methods inherited from the base class
}

export class NewParam {
  info: string = '__default_param__';

  constructor(info: string) {
    this.info = info;
  }
}
```

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 11: Using Symbol Icons

This example demonstrates how to use the Symbol components in Navigation and [NavDestination](ts-basic-components-navdestination.md).

```TypeScript
// Index.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct NavigationExample {
  @Provide('navPathStack') navPathStack: NavPathStack = new NavPathStack();
  @State menuItems: Array<NavigationMenuItem> = [
    {
      // Replace 'resources/base/media/ic_public_ok.svg' with the image resource file you use.
      value: 'menuItem1',
      icon: 'resources/base/media/ic_public_ok.svg' // Icon resource path.
    },
    {
      // Replace 'resources/base/media/ic_public_ok.svg' with the image resource file you use.
      value: 'menuItem2',
      icon: 'resources/base/media/ic_public_ok.svg', // Icon resource path.
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
      // Replace 'resources/base/media/ic_public_ok.svg' with the image resource file you use.
      value: 'toolItem1',
      icon: 'resources/base/media/ic_public_ok.svg', // Icon resource path.
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_lungs')),
      status: ToolbarItemStatus.ACTIVE,
      activeSymbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_folder_badge_plus')).fontColor([Color.Red,
        Color.Green]).renderingStrategy(SymbolRenderingStrategy.MULTIPLE_COLOR),
      action: () => {
      }
    },
    {
      // Replace 'resources/base/media/ic_public_more.svg' with the image resource file you use.
      value: 'toolItem2',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_star')),
      status: ToolbarItemStatus.ACTIVE,
      activeIcon: 'resources/base/media/ic_public_more.svg', // Icon resource path.
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
        Button('Go').onClick(() => {
          this.navPathStack.pushPathByName('NavigationMenu', null);
        })
      }
    }
    .backButtonIcon(new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')))
    .titleMode(NavigationTitleMode.Mini)
    .menus(this.menuItems)
    .toolbarConfiguration(this.toolItems)
    .title('Level-1 page')
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
      // Replace 'resources/base/media/ic_public_ok.svg' with the image resource file you use.
      value: 'menuItem1',
      icon: 'resources/base/media/ic_public_ok.svg', // Icon resource path.
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

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 12: Setting the Custom Title Bar Margin

This example demonstrates how to set custom title bar padding in Navigation and [NavDestination](ts-basic-components-navdestination.md), and how to modify the main title and subtitle text styles through TextModifier.

```TypeScript
// Index.ets
import { LengthMetrics } from '@kit.ArkUI';
import { MainTitleTextModifier, SubTitleTextModifier } from './Utils';

@Entry
@Component
struct NavigationExample {
  private navPathStack: NavPathStack = new NavPathStack();
  // Assign an initial padding at the start of the title bar.
  @State paddingStart: LengthMetrics = LengthMetrics.vp(0);
  // Assign an initial padding at the end of the title bar.
  @State paddingEnd: LengthMetrics = LengthMetrics.vp(0);
  // Main title attribute modifier.
  @State mainTitleModifier: MainTitleTextModifier = new MainTitleTextModifier();
  // Subtitle attribute modifier.
  @State subTitleModifier: SubTitleTextModifier = new SubTitleTextModifier();
  @State applyModifier: boolean = false;
  @State useStyle1: boolean = true;

  build() {
    Navigation(this.navPathStack) {
      Column() {
        // Switch between padding values for the title bar.
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
      // Replace 'resources/base/media/ic_public_ok.svg' with the image resource file you use.
      value: 'menuItem1',
      icon: 'resources/base/media/ic_public_ok.svg', // Icon resource path.
      action: () => {
      }
    }
  ];
  @State paddingStart: LengthMetrics = LengthMetrics.vp(0);
  @State paddingEnd: LengthMetrics = LengthMetrics.vp(0);
  // Main title attribute modifier.
  @State mainTitleModifier: MainTitleTextModifier = new MainTitleTextModifier();
  // Subtitle attribute modifier.
  @State subTitleModifier: SubTitleTextModifier = new SubTitleTextModifier();
  @State applyModifier: boolean = false;
  @State useStyle1: boolean = true;

  build() {
    NavDestination() {
      Column() {
        // Switch between padding values for the title bar.
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

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 13: Implementing a Custom Transition Animation

This example shows how to implement a custom transition animation for navigation between pages.

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
      // No custom animation for the home page
      if (from.index === -1 || to.index === -1) {
        return undefined;
      }

      let customAnimation: NavigationAnimatedTransition = {
        timeout: 2000,
        // Called when transition starts. The transition context proxy object is passed in.
        transition: (transitionProxy: NavigationTransitionProxy) => {
          if (!from.navDestinationId || !to.navDestinationId) {
            return;
          }
          // Obtain the corresponding transition animation callback from the CustomTransition class by subpage ID.
          let fromParam: AnimateCallback = CustomTransition.getInstance().getAnimateParam(from.navDestinationId);
          let toParam: AnimateCallback = CustomTransition.getInstance().getAnimateParam(to.navDestinationId);
          // Push animation
          if (operation == NavigationOperation.PUSH) {
            if (fromParam.start && toParam.start) {
              // Set the animation start for both pages in the push transition.
              fromParam.start(true, true);
              toParam.start(true, false);
            }
            this.getUIContext()?.animateTo({
              duration: 500, curve: Curve.Friction, onFinish: () => {
                // Manually call the finishTransition API after the animation ends. Otherwise, the system will automatically call the API after the specified timeout period.
                transitionProxy.finishTransition();
              }
            }, () => {
              if (fromParam.finish && toParam.finish) {
                // Set the animation end for both pages in the push transition.
                fromParam.finish(true, true);
                toParam.finish(true, false);
              }

            })
          } else if (operation == NavigationOperation.POP) {
            // Pop animation
            if (fromParam.start && toParam.start) {
              // Set the animation start for both pages in the pop transition.
              fromParam.start(false, true);
              toParam.start(false, false);
            }
            this.getUIContext()?.animateTo({
              duration: 500, curve: Curve.Friction, onFinish: () => {
                // Manually call the finishTransition API after the animation ends. Otherwise, the system will automatically call the API after the specified timeout period.
                transitionProxy.finishTransition();
              }
            }, () => {
              if (fromParam.finish && toParam.finish) {
                // Set the animation end for both pages in the pop transition.
                fromParam.finish(false, true);
                toParam.finish(false, false);
              }
            })
          } else {
            // No animation for the replacement operation
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
      // Set the start point of the transition animation based on the transition type.
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
      // Set the end point of the transition animation based on the transition type.
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
      // Unregister the custom transition animation parameters when the page is destroyed.
      CustomTransition.getInstance().unRegisterNavParam(this.pageId);
    })
    .onReady((context: NavDestinationContext) => {
      this.pageInfos = context.pathStack;
      if (context.navDestinationId) {
        this.pageId = context.navDestinationId;
        // Register the custom transition animation parameters when the page is created.
        this.registerCallback();
      }
    })
    .translate({ y: this.translateY })
    .backgroundColor(this.title == 'PageOne' ? '#F1F3F5' : '#ff11dee5')
  }
}
```

```TypeScript
// The src/main/pages/CustomTransitionUtils.ts file defines a utility class for managing custom animation parameters for different pages.
// Custom API to save the transition animation callback and parameters related to a page.
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

  /* Register animation callbacks for a page.
   * name: unique ID of the target page
   * startCallback: used to set the page state at the start of the animation.
   * endCallback: used to set the page state at the end of the animation.
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

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 14: Setting the Navigation Split-Column Mode

This example demonstrates the effect of the Navigation component in the split-column mode. The [splitPlaceholder](arkts-arkui-navigation-comp-attribute.md#splitplaceholder) attribute is used to set the default placeholder page on the right side of the split column, the [navBarWidthRange](#navbarwidthrange10) attribute is used to configure the width range of the navigation bar, and the [divider](#divider23) attribute is used to customize the style of the divider between the navigation bar and the content area.

The splitPlaceholder attribute is added since API version 20, and the divider attribute is added since API version 23.

Before running this example, you need to set orientation to auto_rotation in the abilities field of the project configuration file [module.json5](../../../quick-start/module-configuration-file.md).



```TypeScript
import { ComponentContent } from '@kit.ArkUI';

@Builder function PlaceholderPage() {
  Column() {
    Text('Split-column mode placeholder page')
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
      // Replace $r('sys.media.ohos_ic_public_add') with the resource file you use.
      Image($r('sys.media.ohos_ic_public_add'))
        .width(24)
        .height(24)
      // Replace $r('sys.media.ohos_ic_public_add') with the resource file you use.
      Image($r('sys.media.ohos_ic_public_add'))
        .width(24)
        .height(24)
        .margin({ left: 24 })
      // Replace $r('sys.media.ohos_ic_public_more') with the resource file you use.
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
          // Replace $r('app.string.navigation_toolbar_add') and $r('app.media.startIcon') with the image resource file you use.
          value: $r('app.string.navigation_toolbar_add'),
          icon: $r('app.media.startIcon')
        },
        {
          // Replace $r('app.string.navigation_toolbar_app') and $r('app.media.startIcon') with the image resource file you use.
          value: $r('app.string.navigation_toolbar_app'),
          icon: $r('app.media.startIcon')
        },
        {
          // Replace $r('app.string.navigation_toolbar_collect') and $r('app.media.startIcon') with the image resource file you use.
          value: $r('app.string.navigation_toolbar_collect'),
          icon: $r('app.media.startIcon')
        }
      ])
      .mode(NavigationMode.Split) // Set the navigation mode to Split.
      .navBarWidthRange([this.minNavBarWidth, this.maxNavBarWidth]) // Set the navigation page width range: [minimum width, maximum width].
      .minContentWidth(this.minContentWidth)
      .hideTitleBar(false)
      .hideToolBar(false)
      .onTitleModeChange((titleModel: NavigationTitleMode) => {
        console.info('titleMode' + titleModel)
      })
      .splitPlaceholder(this.placeholder)
      .divider({ startMargin: 20, endMargin: 20, color: Color.Red}) // Added the divider attribute since API version 23.
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F1F3F5')
  }
}
```

### Example 15: Enabling and Disabling Navigation Toolbar Adaptation

This example demonstrates how to enable and disable the self-adaptation capability of the navigation toolbar using the [enableToolBarAdaptation](arkts-arkui-navigation-comp-attribute.md#enabletoolbaradaptation) attribute.

The enableToolBarAdaptation attribute is added since API version 19.

In the [module.json5](../../../quick-start/module-configuration-file.md) file, set orientation to landscape in the abilities field. (This configuration is used only to demonstrate the toolbar adaptation capability of Navigation in landscape mode. You can set orientation to auto_rotation as required.)



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
        Button('Enable/Disable Adaptation').onClick(()=> {
          this.enable = !this.enable;
        })
        Text(`Toolbar adaptation enabled: ${this.enable}`)
      }
    }
    .mode(NavigationMode.Stack)
    .enableToolBarAdaptation(this.enable) // Specify whether to enable toolbar adaptation.
    .backButtonIcon(new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')))
    .titleMode(NavigationTitleMode.Mini)
    .menus(this.menuItems)
    .toolbarConfiguration(this.toolItems)
    .title('Level-1 page')
  }
}
```

### Example 16: Using NavDestination as a Navigation Page in Navigation

This example demonstrates how to configure the [homeDestination](#navigation) parameter to implement the [NavDestination](ts-basic-components-navdestination.md) root navigation page effect of the Navigation component.

This new way to create the Navigation component is added since API version 20.

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
    // Configure home page NavDestination information here.
    Navigation(this.stack, { name: 'PageHome' }) {
    }
    .width('100%').height('100%')
  }
}
```

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. The following is an example of router_map.json:



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

### Example 17: Using New Navigation Controller APIs

This example demonstrates how to implement route interception by setting the [setInterception](arkts-arkui-navigation-comp-navpathstack-c.md#setinterception) method and obtain mode using the [NavDestinationContext](ts-basic-components-navdestination.md#navdestinationcontext11) object.

The interception API is added to the [NavigationInterception](arkts-arkui-navigation-comp-navigationinterception-i.md) parameter type of setInterception since API version 22.

```TypeScript
// Index.ets
@Entry
@Component
struct NavigationExample {
  pageInfos: NavPathStack = new NavPathStack();
  isUseInterception: boolean = false;

  registerInterception() {
    this.pageInfos.setInterception({
      // Intercept navigation behavior before page creation. Stack operations take effect for the current navigation process.
      interception: (from: NavPathInfo | 'navBar', to: NavPathInfo | NavBar, navStack: NavPathStack,
        operation: NavigationOperation, animated: boolean) => {
        if (!this.isUseInterception) {
          return;
        }
        if (typeof to === 'string') {
          return;
        }
        // Redirect the target page from pageTwo to pageOne.
        let target: NavPathInfo = to as NavPathInfo;
        let navStacktarget: NavPathStack = navStack as NavPathStack;
        if (target.name === 'pageTwo') {
          navStacktarget.pop();
          navStacktarget.pushPathByName('pageOne', null);
        }
      },
      // Callback invoked after the page is navigated. Stack operations in this callback are effective in the next navigation.
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
      // Callback invoked when the display mode of the Navigation component switches between single-column and split-column.
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
            this.pageInfos.pushPath({ name: 'pageOne' }); // Push the navigation destination page specified by name to the navigation stack.
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
            this.pageInfos.pushPathByName('pageTwo', pageParam); // Push the navigation destination page specified by name, with the data specified by param, to the stack.
          })
        Button('singletonLaunchMode', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.pushPath({ name: 'pageOne' },
              { launchMode: LaunchMode.MOVE_TO_TOP_SINGLETON }); // Search from the bottom to the top of the stack. If the page with the specified name exists, move that page to the top of the stack.
          })
        Button('popToname', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.popToName('pageTwo'); // Pop the routing stack back to the first navigation destination page that matches the value of name.
            console.info('popToName' + JSON.stringify(this.pageInfos),
              'Return value' + JSON.stringify(this.pageInfos.popToName('pageTwo')));
          })
        Button('popToIndex', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.popToIndex(1); // Return the routing stack to the navigation destination page that matches the value of index.
            console.info('popToIndex' + JSON.stringify(this.pageInfos));
          })
        Button('moveToTop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.moveToTop('pageTwo'); // Move the first navigation destination page that matches the value of name to the top of the routing stack.
            console.info('moveToTop' + JSON.stringify(this.pageInfos),
              'Return value' + JSON.stringify(this.pageInfos.moveToTop('pageTwo')));
          })
        Button('moveIndexToTop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.moveIndexToTop(1); // Move to the top of the routing stack the navigation destination page that matches the value of index.
            console.info('moveIndexToTop' + JSON.stringify(this.pageInfos));
          })
        Button('clear', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfos.clear(); // Clear the routing stack.
          })
        Button('get', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            console.info('-------------------');
            console.info('Obtain names of all NavDestination pages in the stack', JSON.stringify(this.pageInfos.getAllPathName()));
            console.info('Obtain parameter information of the NavDestination page at the specified index',
              JSON.stringify(this.pageInfos.getParamByIndex(1)));
            console.info('Obtain the parameter information of all NavDestination pages with the specified name',
              JSON.stringify(this.pageInfos.getParamByName('pageTwo')));
            console.info('Obtain the position indexes of all NavDestination pages with the specified name',
              JSON.stringify(this.pageInfos.getIndexByName('pageOne')));
            console.info('Obtain the stack size', JSON.stringify(this.pageInfos.size()));
          })
      }.width('100%').height('100%')
    }.title('pageOne')
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // Pop the top element out of the routing stack.
      console.info('pop' + 'return value' + JSON.stringify(popDestinationInfo));
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

Configure "routerMap": "$profile:router_map" in the module field of the project configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory.



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

### Example 18: Setting Navigation as Recoverable

This example demonstrates how to set Navigation as recoverable by using the [recoverable](#recoverable14) API. You need to enable the [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md) backup and restore function during module initialization. For details, see [UIAbility Backup and Restore](../../../application-models/ability-recover-guideline.md).

The recoverable API is supported since API version 14.

```TypeScript
// Index.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct NavigationExample {
  navPathStack: NavPathStack = new NavPathStack();
  @State menuItems: Array<NavigationMenuItem> = [
    {
      // Replace 'resources/base/media/startIcon.png' with the resource file you use.
      value: 'menuItem1',
      icon: 'resources/base/media/startIcon.png' // Icon resource path.
    },
    {
      // Replace 'resources/base/media/ic_public_ok.svg' with the image resource file you use.
      value: 'menuItem2',
      icon: 'resources/base/media/ic_public_ok.svg', // Icon resource path.
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
      // Replace 'resources/base/media/ic_public_ok.svg' with the image resource file you use.
      value: 'toolItem1',
      icon: 'resources/base/media/ic_public_ok.svg', // Icon resource path.
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_lungs')),
      status: ToolbarItemStatus.ACTIVE,
      activeSymbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_folder_badge_plus')).fontColor([Color.Red,
        Color.Green]).renderingStrategy(SymbolRenderingStrategy.MULTIPLE_COLOR),
      action: () => {
      }
    },
    {
      // Replace 'resources/base/media/startIcon.png' with the resource file you use.
      value: 'toolItem2',
      symbolIcon: new SymbolGlyphModifier($r('sys.symbol.ohos_star')),
      status: ToolbarItemStatus.ACTIVE,
      activeIcon: 'resources/base/media/startIcon.png', // Icon resource path.
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
        Button('Go').onClick(() => {
          this.navPathStack.pushPathByName('NavigationMenu', null);
        })
      }
    }
    .backButtonIcon(new SymbolGlyphModifier($r('sys.symbol.ohos_wifi')))
    .titleMode(NavigationTitleMode.Mini)
    .menus(this.menuItems)
    .toolbarConfiguration(this.toolItems)
    .title('Level-1 page')
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
      // Replace 'resources/base/media/startIcon.png' with the resource file you use.
      value: 'menuItem1',
      icon: 'resources/base/media/startIcon.png', // Icon resource path.
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

Configure "routerMap": "$profile:router_map" in the module field of the configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the src/main directory, and add the router_map.json file to the src/main/resources/base/profile directory. Example:

> NOTE
> 
> To simulate the scenario where a process exits unexpectedly and is cold started again, perform the following steps:
> 
> After the project is successfully executed, click the jump button.
> 
> Swipe up the application to return to the background and open the CLI.
> 
> Run hdc shell, and then run pidof <package_name> to query the value of pid.
> 
> Run the aa force-stop Project name -p Value of pid -r RESOURCE_CONTROL command to simulate the scenario where the app exits due to improper resource usage.
> 
> Click the application. The displayed page is still the page after the jump button is clicked.



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

### Example 19: Setting ScrollEffectOptions to Enable the Scroll Blur Effect for the Title Bar

This example demonstrates how to use [ScrollEffectOptions](#scrolleffectoptions) item to enable the scroll blur effect for the title bar.

Since API version 26.0.0, the [scrollEffectOptions](#scrolleffectoptions) attribute has been added to the options parameter of the [title](#title) API.



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

### Example 20: Setting systemMaterial to Enable the Material Effect for the Title Bar

This example demonstrates how to use the systemMaterial attribute to set the system material of the component and enable the immersive light effect for the title bar.

The systemMaterial attribute is added to [NavigationTitleOptions](arkts-arkui-navigation-comp-navigationtitleoptions-i.md) since API version 26.0.0.



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
      // systemMaterial and barStyle are not associated. However, setting barStyle to STACK can achieve the best immersive effect.
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
        // systemMaterial and barStyle are not associated. However, setting barStyle to STACK can achieve the best immersive effect.
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

### Example 21: Enabling the Stack Clearing Effect from Left to Right

This example demonstrates how to use the clearContentStackOnPrimaryNavigation attribute to enable the stack clearing effect from left to right on the navigation page.

The clearContentStackOnPrimaryNavigation attribute is added to [NavigationConfiguration](arkts-arkui-navigation-comp-navigationconfiguration-i.md) since API version 26.1.0.

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
