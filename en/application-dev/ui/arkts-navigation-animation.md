# Navigation Transition Animation
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--Designer: @jiangdayuan-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

The **Navigation** component provides default transition animations for page switching. When you use the navigation controller to perform operations, different transition effects are automatically applied. For example, before API version 13, **NavDestination** components of the [Dialog](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationmode11) type do not have transition animations by default. Starting from API version 13, they support the system's default transition animations.

**Navigation** also offers capabilities to disable the system transition, create custom transitions, and implement shared element transitions.

## Disabling Transitions

You can disable navigation transition animations in two ways:

- On a Global Basis
  
  To enable or disable all transition animations in the current **Navigation** component, use the [disableAnimation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#disableanimation11) API provided in **NavPathStack**.

  <!-- @[PageAnimated](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageAnimated.ets) -->
  
  ``` TypeScript
  pageStack: NavPathStack = new NavPathStack();
  
  aboutToAppear(): void {
    this.pageStack.disableAnimation(true);
  }
  ```

- On a One-Time Basis
  
  The [pushPath](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushpath10), [pop](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pop10), and [replacePath](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#replacepath11) APIs provided by **NavPathStack** accept an optional **animated** parameter. Setting **animated** to **false** disables the transition for that single operation, without affecting subsequent animations.

  <!-- @[PageOnceClose](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageOnceClose.ets) -->
  
  ``` TypeScript
  @Provide('pageStack') pageStack: NavPathStack = new NavPathStack();
  ```
  <!-- @[PageOnceCloseOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageOnceClose.ets) -->
  
  ``` TypeScript
  this.pageStack.pushPath({ name: 'MyComponent' }, false);
  ```
  <!-- @[PageOnceCloseTwo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageOnceClose.ets) -->
  
  ``` TypeScript
  this.pageStack.pop(false);
  ```

## Defining a Custom Transition

**Navigation** provides two levels of custom transition support: one for the entire **Navigation** component, and one for individual **NavDestination** pages.

- Use the [customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11) event to define a transition that applies to all pages within the **Navigation** component.

  1. Build a custom transition animation utility class **CustomNavigationUtils** that maintains a **Map** of custom transition objects (**CustomTransition**) for each page. A page registers its custom transition animation object when created and unregisters it when destroyed.
  2. Implement a transition protocol object [NavigationAnimatedTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationanimatedtransition11), where: **transition** contains the custom animation logic. The system calls this method when the transition starts. **timeout** specifies the maximum duration of the transition (default: 1000 ms). **onTransitionEnd** represents the callback invoked when the transition finishes.
  3. Call the **customNavContentTransition** API and return the implemented transition protocol object. If **undefined** is returned, the system default transition will be used.

  For a complete code sample, see [Example 3: Setting an Interactive Transition Animation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-3-setting-an-interactive-transition-animation).

- Use the [customTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#customtransition15) attribute to define a transition specific to a particular **NavDestination** page. The implementation is as follows:

  1. Implement the [transition delegate for NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationtransitiondelegate15), returning custom transition protocol objects [NavDestinationTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationtransition15) for different stack operation types. **event** is a required parameter where the logic for custom transition animations should be implemented; **onTransitionEnd**, **duration**, **curve**, and **delay** are optional parameters corresponding to the callback after animation completion, animation duration, animation curve type, and delay before start, respectively. If multiple transition protocol objects are returned in the transition delegate, these animation effects will be applied incrementally.
  2. Complete the custom transition setup by calling the **customTransition** attribute of the **NavDestination** component and passing in the implemented transition delegate.

  For details about the sample code, see [Example 2: Setting a Custom Transitions for the NavDestination Component](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#example-2-setting-a-custom-transitions-for-the-navdestination-component).

> **NOTE**
>
>   1. [customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11) controls all pages within the **Navigation** component and provides unified transition animation effects.
>   2. [customTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#customtransition15) controls the transition effect for individual pages.
>   3. When both [customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11) and [customTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#customtransition15) are used, **customNavContentTransition** takes precedence.

## Shared Element Transition

You can implement shared element transitions between navigation destination pages using [geometryTransition](../reference/apis-arkui/arkui-ts/ts-transition-animation-geometrytransition.md#geometrytransition). Ensure that the default transition animations are disabled for pages configured with shared element transitions.

1. Add the **geometryTransition** attribute to the components that need to implement shared element transitions, ensuring that the **id** parameter is consistent between the two **NavDestination** components.

   <!-- @[GeometryTransitionFromPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/GeometryTransition.ets) -->
   
   ``` TypeScript
   // Set id of the source page.
   NavDestination() {
     Column() {
       // ...
       // Replace $r('app.media.startIcon') with the resource file you use.
       Image($r('app.media.startIcon'))
         .geometryTransition('sharedId')
         .width(100)
         .height(100)
     }
   }.title('FromPage')
   ```

   <!-- @[GeometryTransitionToPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/GeometryTransition.ets) -->
   
   ``` TypeScript
   // Set id of the destination page.
   NavDestination() {
     Column() {
       // Replace $r('app.media.startIcon') with the resource file you use.
       Image($r('app.media.startIcon'))
         .geometryTransition('sharedId')
         .width(200)
         .height(200)
     }
   }
   .title('ToPage')
   ```

2. Wrap the navigation operation inside an [animateTo](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#animateto) closure, and then configure the animation parameters and disable the default transition.

   <!-- @[GeometryTransitionFromPageOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/GeometryTransition.ets) -->
   
   ``` TypeScript
   NavDestination() {
     Column() {
       // The value in the $r('app.string.ToPage') resource file is "Go to destination page."
       Button($r('app.string.ToPage'))
         .width('80%')
         .height(40)
         .margin(20)
         .onClick(() => {
           this.getUIContext()?.animateTo({ duration: 1000 }, () => {
             this.navPathStack.pushPath({ name: 'ToPage' }, false)
           });
         })
       // ...
     }
   }.title('FromPage')
   ```
