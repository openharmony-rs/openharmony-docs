# Navigation Transition Animation
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--Designer: @jiangdayuan-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

[Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) provides default transition animations, as well as custom transition animations and shared element transition animations.

## Default Transition Animations

The system provides multiple default transition types, which can be implemented through the [NavDestination.systemTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#systemtransition14) API. For details, see [Setting Default Transition Animations for the NavDestination Component](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#example-3-setting-system-transition-animations-for-the-navdestination-component).

> **NOTE**
>
> - The default transition uses a [spring curve](./arkts-spring-curve.md). Its duration depends on the curve's physical parameters and may vary across devices. Therefore, the default animation duration is not controllable. Avoid coupling the default duration with service logic. To listen for animation completion, implement a [custom transition](#defining-a-custom-transition).
> - Since API version 13, default transition animations are provided for the **NavDestination** component of the [Dialog](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationmode11) type. In earlier versions, such animations are not provided.

You can disable the default transition animations in either of the following ways:

- On a Global Basis
  
  You can call the [disableAnimation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#disableanimation11) API provided by **NavPathStack** to disable or enable all transition animations for the current **Navigation** component.

  <!-- @[PageAnimated](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageAnimated.ets) -->
  
  ``` TypeScript
  pageStack: NavPathStack = new NavPathStack();
  
  aboutToAppear(): void {
    this.pageStack.disableAnimation(true);
  }
  ```

- On a One-Time Basis
  
  The [pushPath](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushpath10), [pop](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pop10), and [replacePath](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#replacepath11) APIs provided by **NavPathStack** accept an optional **animated** parameter. If you want to disable the transition animation on a one-time basis, set **animated** to **false**. The setting does not affect the next transition animation.

## Defining a Custom Transition

**Navigation** provides two levels of custom transition support: one for the entire **Navigation** component, and one for individual **NavDestination** pages.

- A custom transition animation for the **Navigation** component is provided by **[customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11)**, which can control all pages in **Navigation** and unify the transition animation effect. The procedure is as follows. For details about the sample code, see [Setting an Interactive Transition Animation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-3-setting-an-interactive-transition-animation).

  1. Implement a custom transition animation utility class **CustomNavigationUtils** to manage custom animation objects **CustomTransition** for each page via a **Map**. A page registers its custom transition animation object when created and unregisters it when destroyed.
  2. Implement a transition protocol object [NavigationAnimatedTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationanimatedtransition11), where: **transition** contains the custom animation logic. The system calls this method when the transition starts. **timeout** specifies the maximum duration of the transition (default: 1000 ms). **onTransitionEnd** represents the callback invoked when the transition finishes.
  3. Call the **customNavContentTransition** API and return the implemented transition protocol object. If **undefined** is returned, the system default transition will be used.

- The **NavDestination** component supports custom transition animations, which are used to control the transition effect of a single page. You can set the [customTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#customtransition15) attribute to implement the custom transition effect of a single page. The procedure is as follows. For details about the sample code, see [Setting a Custom Transitions for the NavDestination Component](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#example-2-setting-a-custom-transitions-for-the-navdestination-component).

  1. Implement the [transition delegate for NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationtransitiondelegate15), returning custom transition protocol objects [NavDestinationTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationtransition15) for different stack operation types. **event** is a required parameter where the logic for custom transition animations should be implemented; **onTransitionEnd**, **duration**, **curve**, and **delay** are optional parameters corresponding to the callback after animation completion, animation duration, animation curve type, and delay before start, respectively. If multiple transition protocol objects are returned in the transition delegate, these animation effects will be applied incrementally.
  2. Complete the custom transition setup by calling the **customTransition** attribute of the **NavDestination** component and passing in the implemented transition delegate.

> **NOTE**
>
> When both [customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11) and [customTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#customtransition15) are used, **customNavContentTransition** takes precedence.

## Shared Element Transition

You can implement shared element transitions between **NavDestination** components using [geometryTransition](../reference/apis-arkui/arkui-ts/ts-transition-animation-geometrytransition.md#geometrytransition). The following is an example. Ensure that the default transition animations are disabled for pages configured with shared element transitions. Otherwise, the default animations and shared element animations will be superimposed, resulting in an abnormal effect.

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
       // Replace $r('app.string.ToPage') with the actual resource file. The value in the resource file is "Go to target page."

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
