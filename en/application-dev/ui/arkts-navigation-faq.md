# Navigation FAQs
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @huangxiaolinabc-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=0cac84d6c80b64a4f9d6b0bbd0525523825d33a0 translatedAt=2026-10-10T06:15:23.293Z pushedAt=2026-10-12T08:44:33.391Z -->

## Dialog-Type NavDestination Mask Animation Is Not Smooth

**Symptom**

When the default transition animation of [NavDestinationMode.DIALOG](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationmode11) is used, the following two issues occur:

- When the mask background color is set on the page: When the page is popped, the mask does not disappear immediately. Instead, it disappears only after the content slides down and exits.

  ![normal](figures/DialogNavDesAnimation-normal.gif)

- When the mask background color is set on the content area: The mask exits from top to bottom together with the content.

  ![content](figures/DialogNavDesAnimation-content.gif)

It is expected that the mask fades out while the content area exits downward.

**Solution**

Execute the background color animation in the [onWillAppear](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onwillappear12) and [onWillDisappear](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onwilldisappear12) lifecycle callbacks. The following is an example:

<!-- @[DialogNavDesAnimation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/animation/DialogNavDestination.ets) -->

``` TypeScript
@Builder
export function DialogNavDestinationBuilder() {
  DialogNavDestination();
}

@Component
export struct DialogNavDestination {
  stack: NavPathStack = AppStorage.get<NavPathStack>('basicNavigationStack')!;
  @State backColor: ResourceColor = '#00000000';

  build() {
    NavDestination() {
      Stack() {
        Text('Dialog')
          .fontSize(44)
          .backgroundColor(Color.White)
      }
      .width('100%')
      .height('100%')
    }
    .hideTitleBar(true)
    .backgroundColor(this.backColor)
    .mode(NavDestinationMode.DIALOG)
    .onWillAppear(() => {
      // Fade in the mask on startup.
      this.getUIContext().animateTo({ duration:450 }, () => {
        this.backColor = '#66000000';
      });
    })
    .onWillDisappear(() => {
      // Fade out the mask on disappearance.
      this.getUIContext().animateTo({ duration: 450 }, () => {
        this.backColor = '#00000000';
      });
    })
  }
}
```

  ![modify](figures/DialogNavDesAnimation-modify.gif)

## Router and Navigation Animation Conflict

**Symptom**

When `router` navigates to a `navigation` page, and `navigation` immediately pushes a `NavDestination` page in the `aboutToAppear` callback, the `Page` and the `NavDestination` page display animations at the same time, resulting in a poor effect.

**Solution**

Disable the animation of the push in `aboutToAppear`:

<!-- @[NavigationAnimation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/animation/NavigationPage.ets) -->

``` TypeScript
@Entry
@Component
struct NavigationPage {
  navStack: NavPathStack = new NavPathStack();

  aboutToAppear(): void {
    AppStorage.setOrCreate<NavPathStack>('basicNavigationStack', this.navStack);
    this.navStack.pushPath({ name: 'animation-BasicNavDestination' }, false); // Disable the animation for this push.
  }

  build() {
    Navigation(this.navStack) {
      // ...
    }
  }
}
```

## Pop and Push Performed Simultaneously but Pop Animation Executed

**Symptom**

When you pop the top page of the stack and then immediately push a page, the animation effect is the pop animation of the top page, not the push animation of PageOne.

<!-- @[PopAndPush-Normal](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/animation/PageTwoNavDes.ets) -->

``` TypeScript
this.stack.pop();
this.stack.pushPath({ name: 'animation-BasicNavDestination' });
```

**Solution**

In a single operation, regardless of how many times the `pop` and `push` APIs are called, Navigation calculates the final result and performs only one animation.

The page transition animation of the current Navigation is determined primarily by the top page of the stack before the operation. If the top page is no longer in the stack after the operation, the pop animation is executed; if it is still in the stack, the push animation is executed.

For example, suppose the current top page is `PageTop`. If you first call `pop` to remove `PageTop` and then call `push` to add `PageNew` to the stack, `PageTop` is no longer in the stack after the operation, so the animation finally executed is the pop animation.

If you want to remove a page while pushing another page and execute the push animation, you can set the pushed page to `NEW_INSTANCE`, which executes the push animation by default:

<!-- @[PopAndPush-NEW_INSTANCE](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/animation/PageTwoNavDes.ets) -->

``` TypeScript
this.stack.pop();
this.stack.pushPath({ name: 'animation-BasicNavDestination' }, { launchMode: LaunchMode.NEW_INSTANCE });
```

## Is There an End Callback for the Transition Animation?

The current system animation does not provide an animation end callback. Only custom transition animations provide an end callback. You need to implement [custom transition animation](./arkts-navigation-animation.md#defining-a-custom-transition) yourself. Related APIs: [NavDestinationTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationtransition15), [NavigationAnimatedTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationanimatedtransition11).

## How to Implement a Shared Element Transition Between Navigation and NavDestination

Currently, only transitions between NavDestination components support the shared element transition effect. The system does not yet support the shared element effect for transitions between NavBar and NavDestination.

The shared element transition of NavDestination must be implemented together with the [geometryTransition](../reference/apis-arkui/arkui-ts/ts-transition-animation-geometrytransition.md) API, and the following conditions must be met:

- [Disable the transition](./arkts-navigation-animation.md).
- The navigation API must be called within the [animateTo](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#animateto) animation closure.
- Set the [geometryTransition](../reference/apis-arkui/arkui-ts/ts-transition-animation-geometrytransition.md) attribute on the content component, not on NavDestination.

For a sample, see [Shared Element Transition](./arkts-navigation-animation.md#defining-a-shared-element-transition).

## Navigation Animation Anomaly After Setting zIndex on NavDestination

[zIndex](../reference/apis-arkui/arkui-ts/ts-universal-attributes-z-order.md#zindex) is used to modify the display level of a component. Setting this attribute on `NavDestination` overrides the level set by the system, which disrupts the animation. Therefore, setting `zIndex` on `NavDestination` is not recommended.

In addition, setting special attributes such as [transition](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transition), [geometryTransition](../reference/apis-arkui/arkui-ts/ts-transition-animation-geometrytransition.md), [sharedTransition](../reference/apis-arkui/arkui-ts/ts-transition-animation-shared-elements.md#sharedtransition), and [animation](../reference/apis-arkui/arkui-ts/ts-animatorproperty.md) is also not recommended, as they may conflict with the system default animation. If your business requires these attributes, set them on the content node of `NavDestination` to achieve the same effect.

## Page Is Blank When Multiple if Statements Are Used in the NavDestination Builder

**Symptom**

When multiple independent `if` statements are used in the builder specified by the `navDestination` property of `Navigation` to build `NavDestination` pages separately, some pages appear blank after navigation. For example, in the following usage, the page is blank when `name` is `PageC`:

<!-- @[ExamplePage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Navigation/entry/src/main/ets/pages/navDestination/template5/Index.ets) -->

``` TypeScript
@Entry
@Component
struct ExamplePage {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  pageMap(name: string) {
    if (name === 'PageA') {
      NavDestination()
        .backgroundColor(Color.Red)
        .title('PageA')
    }
    if (name === 'PageB') {
      NavDestination()
        .backgroundColor(Color.Green)
        .title('PageB')
    }
    if (name === 'PageC') {
      NavDestination()
        .backgroundColor(Color.Blue)
        .title('PageC')
    }
  }

  build() {
    Navigation(this.stack) {
      Button("push PageA").onClick((event: ClickEvent) => {
        this.stack.pushPathByName("PageA", null)
      })
      Button("push PageB").onClick((event: ClickEvent) => {
        this.stack.pushPathByName("PageB", null)
      })
      Button("push PageC").onClick((event: ClickEvent) => {
        this.stack.pushPathByName("PageC", null)
      })
    }
    .navDestination(this.pageMap)
  }
}
```

**Cause Analysis**

The mechanism by which `Navigation` builds `NavDestination` is as follows:

1. After the builder is executed, the first node serves as the root node, and the remaining nodes are mounted under this root node in code order. (Nodes that are siblings of the first node are mounted as child nodes.)
2. When `Navigation` searches for the `NavDestination` node, it traverses downward from the root node along the first child node of each level until it finds the `NavDestination`. If the first child node at a certain level has no child nodes, the traversal terminates and cannot continue to search subsequent sibling nodes.

Each independent `if` statement produces an `IfElseNode`. The second and third `IfElseNode` nodes are mounted as sibling child nodes of the first `IfElseNode`, and the `NavDestination` is mounted under the `IfElseNode` whose condition is `true`.

- When `name === 'PageA'`, `IfElseNode1` is `true`, and `IfElseNode2` and `IfElseNode3` are `false`. The resulting component tree is as follows:

  ```text
  IfElseNode1                    ← Root node
   ├── NavDestination(PageA)    ← IfElseNode1 is true, and NavDestination is the first child node of IfElseNode1
   ├── IfElseNode2               ← IfElseNode2 is false, no child nodes
   └── IfElseNode3               ← IfElseNode3 is false, no child nodes
  ```

  The Navigation component traverses from IfElseNode1 along the first child node and finds NavDestination(PageA), so the page displays normally.

- When name === 'PageB', IfElseNode2 is true, and IfElseNode1 and IfElseNode3 are false, the resulting component tree is:

  ```text
  IfElseNode1                    ← root node
   ├── IfElseNode2               ← IfElseNode2 is true
   │    └── NavDestination(PageB)
   └── IfElseNode3               ← IfElseNode3 is false, no child nodes
  ```

  The Navigation component traverses from IfElseNode1 along the first child node: IfElseNode1 → IfElseNode2 → NavDestination(PageB), so the page displays normally.

- When name === 'PageC', IfElseNode3 is true, and IfElseNode1 and IfElseNode2 are false, the resulting component tree is:

  ```text
  IfElseNode1                    ← root node
   ├── IfElseNode2               ← IfElseNode2 is false, no child nodes (the first child node!)
   └── IfElseNode3               ← IfElseNode3 is true
        └── NavDestination(PageC)
  ```

  The `Navigation` component traverses `IfElseNode1` along the first child node: `IfElseNode1` → `IfElseNode2` (no child nodes, traversal terminates), so it cannot find `NavDestination(PageC)`, and the page is blank.

**Solution**

Change the multiple independent `if` statements in the builder to an `if-else if-else` judgment, which produces only one `IfElseNode` as the root node, ensuring that `Navigation` can traverse to find the `NavDestination`:

<!-- @[NavDestinationSystemTransition](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Navigation/entry/src/main/ets/pages/navDestination/template3/Index.ets) -->

``` TypeScript
@Entry
@Component
struct NavDestinationSystemTransition {
  // ...

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
      // ...
    }
    .navDestination(this.pageMap)
    .hideNavBar(true)
  }
}
```
