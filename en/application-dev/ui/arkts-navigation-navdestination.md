# Subpage
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--Designer: @jiangdayuan-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

[NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md) is the root container for **Navigation** subpages and is used to hold special attributes as well as lifecycles of subpages. You can set separate attributes such as the title bar and menu bar for **NavDestination**, in the same way you set attributes for **Navigation**. You can also set different display modes for **NavDestination** through the **mode** attribute to meet different page requirements.

## Page Display Mode

**NavDestination** is divided into two modes:

- Standard mode

  By default, subpages in the **NavDestination** component are in standard mode, which corresponds to the [NavDestinationMode.STANDARD](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationmode11) value of the [mode](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#mode11) attribute. Only one standard **NavDestination** page can be displayed in **Navigation**.

- Dialog mode
  
  With **mode** set to **NavDestinationMode.DIALOG**, a **NavDestination** is displayed transparently by default. The appearance and disappearance of the **NavDestination** in dialog mode do not affect the display and lifecycle of the underlying **NavDestination** in standard mode, and both can be displayed at the same time.

  <!-- @[PageDisplayType](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageDisplayType.ets) -->
  
  ``` TypeScript
  // Dialog NavDestination
  @Entry
  @Component
  struct PageDisplayType {
    @Provide('NavPathStack') pageStack: NavPathStack = new NavPathStack();
  
    @Builder
    PagesMap(name: string) {
      if (name == 'DialogPage') {
        DialogPage();
      }
    }
  
    build() {
      Navigation(this.pageStack) {
        Button('Push DialogPage')
          .margin(20)
          .width('80%')
          .onClick(() => {
            this.pageStack.pushPathByName('DialogPage', '');
          })
      }
      .mode(NavigationMode.Stack)
      .title('Main')
      .navDestination(this.PagesMap)
    }
  }
  
  @Component
  export struct DialogPage {
    @Consume('NavPathStack') pageStack: NavPathStack;
  
    build() {
      NavDestination() {
        Stack({ alignContent: Alignment.Center }) {
          Column() {
            Text('Dialog NavDestination')
              .fontSize(20)
              .margin({ bottom: 100 })
            Button('Close').onClick(() => {
              this.pageStack.pop();
            }).width('30%')
          }
          .justifyContent(FlexAlign.Center)
          .backgroundColor(Color.White)
          .borderRadius(10)
          .height('30%')
          .width('80%')
        }.height('100%').width('100%')
      }
      .backgroundColor('rgba(0,0,0,0.5)')
      .hideTitleBar(true)
      .mode(NavDestinationMode.DIALOG)
    }
  }
  ```

  ![dialog_navdestination](figures/DialogNavDestinationExample.gif)

## Page Lifecycle

The lifecycle of **Navigation** can be divided into three categories: custom component lifecycle, universal component lifecycle, and [NavDestination lifecycle](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#events). [aboutToAppear](../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear) and [aboutToDisappear](../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttodisappear) are the lifecycle callbacks of custom components (custom components contained in the outer layer of **NavDestination**); [OnAppear](../reference/apis-arkui/arkui-ts/ts-universal-events-show-hide.md#onappear) and [OnDisappear](../reference/apis-arkui/arkui-ts/ts-universal-events-show-hide.md#ondisappear) are universal component lifecycle callbacks. The remaining lifecycle events are unique to **NavDestination**.

The sequence of these lifecycle events is illustrated in the figure below.

![navigation_lifecycle](figures/navigation_lifecycle.png)

- [aboutToAppear](../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear): invoked when the custom component is about to appear. Specifically, it is invoked after a new instance of the custom component is created and before its **build()** function is executed (before the creation of **NavDestination**). You can change state variables in this callback, and the changes take effect in the subsequent execution of **build()**.
- [onWillAppear](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onwillappear12): invoked after the **NavDestination** component is created and before it is mounted to the component tree. Changing the state variable in this callback takes effect in the current frame.
- [OnAppear](../reference/apis-arkui/arkui-ts/ts-universal-events-show-hide.md#onappear): invoked when the **NavDestination** component is mounted to the component tree. It is a universal lifecycle event.
- [onWillShow](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onwillshow12): invoked before the **NavDestination** component layout is displayed. In this case, the page is invisible. (This callback is not invoked when the application is switched to the foreground.)
- [onShown](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onshown10): invoked after the **NavDestination** component layout is displayed. At this time, the page layout is complete.
- [onActive](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onactive17): invoked when the **NavDestination** component becomes active (on top of the stack and operable, with no special components blocking it).
- [onWillHide](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onwillhide12): invoked when the **NavDestination** component is about to be hidden (it is not invoked when the application is switched to the background).
- [onInactive](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#oninactive17): invoked when the **NavDestination** component becomes inactive (not on top of the stack and inoperable, or on top but blocked by special components).
- [onHidden](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onhidden10): invoked after the **NavDestination** component is hidden (when a non-top page is pushed into the stack, the top page pops out of the stack, or the application is switched to the background).
- [onWillDisappear](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onwilldisappear12): invoked before the **NavDestination** component is about to be destroyed. If there is a transition animation, this callback is invoked before the animation (when the top page of the stack pops out of the stack).
- [onDisAppear](../reference/apis-arkui/arkui-ts/ts-universal-events-show-hide.md#ondisappear): invoked when the **NavDestination** component is unloaded and destroyed from the component tree. It is a universal lifecycle event.
- [aboutToDisappear](../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttodisappear): invoked before the custom component is destroyed. The state variable cannot be changed in this callback.

In addition, there are two special lifecycle callbacks:

- **onResult**: invoked when you return from another **NavDestination** page by swiping left or right or by pressing the back button.
- **onNewParam**: invoked when a **NavDestination** page that previously exists in the stack is moved to the top of the stack through [launchMode.MOVE_TO_TOP_SINGLETON](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#launchmode12) or [launchMode.POP_TO_SINGLETON](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#launchmode12).

## Page Listening and Query

To facilitate the decoupling of components from pages, custom components within **NavDestination** subpages can listen for or query some page status information through global APIs.

- Page information query

  Custom components provide the [queryNavDestinationInfo](../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#querynavdestinationinfo) API, which can be used to query the information of the current page within **NavDestination**. The return value is [NavDestinationInfo](../reference/apis-arkui/js-apis-arkui-observer.md#navdestinationinfo). If the query fails, the return value is **undefined**.

  <!-- @[MyComponent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/observer/template1/Index.ets) -->
  
  ``` TypeScript
  import { uiObserver } from '@kit.ArkUI';
  
  // Custom components within NavDestination
  @Component
  struct MyComponent {
    navDesInfo: uiObserver.NavDestinationInfo | undefined;
    context = this.getUIContext().getHostContext();
  
    aboutToAppear() {
      this.navDesInfo = this.queryNavDestinationInfo();
    }
  
    build() {
      // ...
        Column() {
          // The value in the $r('app.string.onPageName') resource file is "Page name:".
          Text(this.context!.resourceManager.getStringSync($r('app.string.onPageName').id) + `${this.navDesInfo?.name}`)
        }.width('100%').height('100%')
        // ...
    }
  }
  ```

- Page status listening
  
  You can register a listener for **NavDestination** lifecycle changes using the [observer.on('navDestinationUpdate')](../reference/apis-arkui/js-apis-arkui-observer.md#uiobserveronnavdestinationupdate) API.

  Alternatively, you can register a callback for page transition states through [observer.on('navDestinationSwitch')](../reference/apis-arkui/js-apis-arkui-observer.md#uiobserveronnavdestinationswitch12). This callback can be used to obtain page information during route changes using [NavDestinationSwitchInfo](../reference/apis-arkui/js-apis-arkui-observer.md#navdestinationswitchinfo12). This registration supports different scopes: [UIAbilityContext](../reference//apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) and [UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md).
  
