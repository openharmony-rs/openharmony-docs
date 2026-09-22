# UIContext

```TypeScript
export class UIContext
```

Implements a **UIContext** instance.

> **NOTE:** 
> 
> - You can preview how this component looks on a real device, but not in DevEco Studio Previewer.
> 
> - The following APIs must be called through a corresponding UIContext instance. There are three ways to obtain a
> **UIContext** instance: (1) using the
> [getUIContext()](../../../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10) method from
> ohos.window; (2) using the built-in method
> [getUIContext()](../../../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext) of a custom
> component; (3) using static methods of the UIContext class such as
> [getCallingScopeUIContext](#getcallingscopeuicontext). In this document, the **UIContext** instance
> is represented by **uiContext**.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## addLocalInputEventMonitor

```TypeScript
addLocalInputEventMonitor(eventMask: number, listener: InputEventListener): InputEventMonitor
```

Registers a local input event monitor.

The "Local" in the interface name indicates that the monitor is only valid within the current UIContext, and does not affect other UIContext instances. Each UIContext maintains its own independent list of monitors.

Performance Warning: Do not perform time-consuming operations in the callback!

Monitor Object Notes:

- The returned Monitor object is a unique identifier created by the system.  
- Developers cannot actively construct or forge this object.  
- Must save the returned monitor object reference for subsequent cancellation.  
- It is recommended to use a variable to save it to avoid losing the reference.

Usage Examples:

```typescript
// Monitor a single event type
const monitor1 = uiContext.addLocalInputEventMonitor(
InputEventSubTypeMask.LEFT_MOUSE_DOWN,
(wrapper: RawInputEventWrapper) =&gt; {
if (wrapper.isMouseEvent()) {
const mouseEvent = wrapper.asMouseEvent();
console.log(`Mouse: (${mouseEvent.windowX}, ${mouseEvent.windowY})`);
return { action: InputEventInterceptAction.CONTINUE }; // Allow event to continue
}
return { action: InputEventInterceptAction.BLOCK }; // Block event
}
);
// Monitor multiple event types (using bitwise operations)
const monitor2 = uiContext.addLocalInputEventMonitor(
InputEventSubTypeMask.LEFT_MOUSE_DOWN | InputEventSubTypeMask.RIGHT_MOUSE_DOWN,
(wrapper: RawInputEventWrapper) =&gt; {
if (wrapper.isMouseEvent()) {
const mouseEvent = wrapper.asMouseEvent()!;
console.log(`Mouse button: ${mouseEvent.button}`);
return { action: InputEventInterceptAction.BLOCK };
}
return { action: InputEventInterceptAction.CONTINUE };
}
);
// When unregistering the monitor, use the returned Monitor object
uiContext.removeLocalInputEventMonitor(monitor1);
uiContext.removeLocalInputEventMonitor(monitor2);
```

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventMask | number | Yes | Event type mask, specifying the types of events to monitor through bitwise operations. |
| listener | [InputEventListener](../arkts-components/arkts-arkui-common-comp-inputeventlistener-t.md) | Yes | Event listener callback function. |

**Return value:**

| Type | Description |
| --- | --- |
| [InputEventMonitor](../arkts-components/arkts-arkui-common-comp-inputeventmonitor-i.md) | Unique identifier object for the monitor, used for subsequent cancellation of registration. |

**Examples**

```TypeScript
@Entry
@Component
struct InputEventMonitorSample {
  private uiContext: UIContext | undefined = undefined;
  private monitor: InputEventMonitor | null = null;
  aboutToAppear() {
    this.uiContext = this.getUIContext();
    // Listen for mouse left button down events.
    this.monitor = this.uiContext.addLocalInputEventMonitor(
      InputEventSubTypeMask.LEFT_MOUSE_DOWN,
      (wrapper: RawInputEventWrapper) => {
        if (wrapper.isMouseEvent()) {
          const event = wrapper.asMouseEvent()!;
          console.info(`Mouse down at (${event.windowX}, ${event.windowY})`);
          return { action: InputEventInterceptAction.CONTINUE };  // Allow the event to continue propagating.
        }
        return { action: InputEventInterceptAction.BLOCK };  // Prevents event propagating.
      }
    );
  }
  aboutToDisappear() {
    if (this.monitor && this.uiContext) {
      this.uiContext.removeLocalInputEventMonitor(this.monitor);
    }
  }
  build() {
    Column() {
      Text('Input Event Monitor Sample')
        .fontSize(20)
        .margin(20)
    }
    .width('100%')
    .height('100%')
  }
}
```

## animateTo

```TypeScript
animateTo(value: AnimateParam, event: () => void): void
```

Adds transition animations for state changes in closure code.

> **NOTE:** 
> 
> - Avoid using **animateTo** in **aboutToAppear** or **aboutToDisappear**.
> 
> - When **animateTo** is called in [aboutToAppear](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear), the component's build method is not executed yet, and internal components are not created. This means the animation has no initial values to work with and will not function as expected.
> 
> - During execution of [aboutToDisappear](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttodisappear),the component is being destroyed, so animations should not be used.
> 
> - When a component appears or disappears, animation effects can be added through [component transition](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-common.md).
> 
> - For properties that component transitions do not support, refer to [Example 2: Enabling Component Disappearance After Animation Completion](../../../reference/apis-arkui/arkui-ts/ts-explicit-animation.md#example-2-enabling-component-disappearance-after-animation-completion),which uses **animateTo** to achieve the effect of the component disappearing after the animation finishes.
> 
> - In certain scenarios, using animateTo with [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2) may produce unexpected results. For details, see [Using animateTo Failed in State Management V2](../../../ui/state-management/arkts-new-local.md#using-animateto-failed-in-state-management-v2).
> 
> 
> - When a UIAbility switches from the foreground to the background, any limited iteration animations that are currently running will end immediately, thereby triggering the [onFinish animation completion callback](../arkts-components/arkts-arkui-common-comp-animateparam-i.md).
> 
> - If transition animations are turned off in Developer options, animations end on the current frame, and the
> **onFinish** callback is executed immediately. Avoid placing timing-dependent functional logic inside this
> callback.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [AnimateParam](../arkts-components/arkts-arkui-common-comp-animateparam-i.md) | Yes | Animation settings. |
| event | () =&gt; void | Yes | Closure function that displays the animation. The system automatically inserts the transition animation if the state changes in the closure function. |

**Examples**

```TypeScript
// xxx.ets
@Entry
@Component
struct AnimateToExample {
  @State widthSize: number = 250;
  @State heightSize: number = 100;
  @State rotateAngle: number = 0;
  private flag: boolean = true;
  uiContext: UIContext | undefined = undefined;

  aboutToAppear() {
    this.uiContext = this.getUIContext();
    if (!this.uiContext) {
      console.warn("no uiContext");
      return;
    }
  }

  build() {
    Column() {
      Button('change size')
        .width(this.widthSize)
        .height(this.heightSize)
        .margin(30)
        .onClick(() => {
          if (this.flag) {
            this.uiContext?.animateTo({
              duration: 2000,
              curve: Curve.EaseOut,
              iterations: 3,
              playMode: PlayMode.Normal,
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.widthSize = 150;
              this.heightSize = 60;
            });
          } else {
            this.uiContext?.animateTo({}, () => {
              this.widthSize = 250;
              this.heightSize = 100;
            });
          }
          this.flag = !this.flag;
        })
      Button('stop rotating')
        .margin(50)
        .rotate({ x: 0, y: 0, z: 1, angle: this.rotateAngle })
        .onAppear(() => {
          // The animation starts when the component appears.
          this.uiContext?.animateTo({
            duration: 1200,
            curve: Curve.Friction,
            delay: 500,
            iterations: -1, // The value -1 indicates that the animation is played for an unlimited number of times.
            playMode: PlayMode.Alternate,
            expectedFrameRateRange: {
              min: 10,
              max: 120,
              expected: 60,
            }
          }, () => {
            this.rotateAngle = 90
          });
        })
        .onClick(() => {
          this.uiContext?.animateTo({ duration: 0 }, () => {
            // The value of this.rotateAngle is 90 before the animation. In an animation with a duration of 0, changing the property stops any previous animations for that property and applies the new value immediately.
            this.rotateAngle = 0;
          });
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

## animateToImmediately

```TypeScript
animateToImmediately(param: AnimateParam, processor: Callback<void>): void
```

Specifies a clear animation host instance context via the UIContext object and triggers the explicit animation to be dispatched immediately. This avoids issues where animations are not executed or animation end callbacks are not triggered due to inability to locate the instance or using an incorrect instance. This API uses an asynchronous callback to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [AnimateParam](../arkts-components/arkts-arkui-common-comp-animateparam-i.md) | Yes | Animation settings. |
| processor | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback function. It specifies the closure function that displays the animation. The system automatically inserts the transition animation if the state changes in the closure function. |

**Examples**

This example shows how to use animateToImmediately to implement immediate delivery of an explicit animation through a UIContext object.

```TypeScript
// xxx.ets
@Entry
@Component
struct AnimateToImmediatelyExample {
  @State widthSize: number = 250
  @State heightSize: number = 100
  @State opacitySize: number = 0
  private flag: boolean = true
  uiContext: UIContext | null | undefined = this.getUIContext();

  build() {
    Column() {
      Column()
        .width(this.widthSize)
        .height(this.heightSize)
        .backgroundColor(Color.Green)
        .opacity(this.opacitySize)
      Button('change size')
        .margin(30)
        .onClick(() => {
          if (this.flag) {
            this.uiContext?.animateToImmediately({
              delay: 0,
              duration: 1000
            }, () => {
              this.opacitySize = 1
            })
            this.uiContext?.animateTo({
              delay: 1000,
              duration: 1000
            }, () => {
              this.widthSize = 150
              this.heightSize = 60
            })
          } else {
            this.uiContext?.animateToImmediately({
              delay: 0,
              duration: 1000
            }, () => {
              this.widthSize = 250
              this.heightSize = 100
            })
            this.uiContext?.animateTo({
              delay: 1000,
              duration: 1000
            }, () => {
              this.opacitySize = 0
            })
          }
          this.flag = !this.flag
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

## applyDefaultImmersiveStrategy

```TypeScript
applyDefaultImmersiveStrategy(...types: ImmersiveStrategy[]): void
```

Applies the default safe area immersive strategy on the current page. This API applies to scenarios such as full-screen or immersive applications. You can centrally configure the safe area immersive strategy before the first layout. After the strategies are applied, the way the page handles the safe area is adjusted based on the specified strategies.

> **NOTE:** 
> 
> - Dynamic update is not supported. This API takes effect only when called before the first layout process starts on the current page. If it is called after the page enters the first layout process, the applied strategies remain unchanged and this API does not take effect.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| types | [ImmersiveStrategy](arkts-arkui-immersivestrategy-e.md)[] | Yes | Immersive strategies to apply. An empty array clears all applied immersive strategies. |

## bindTabsToNestedScrollable

```TypeScript
bindTabsToNestedScrollable(tabsController: TabsController, parentScroller: Scroller, childScroller: Scroller): void
```

Bind tabs to nested scrollable container components to automatically hide tab bar.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabs-comp-tabscontroller-c.md) | Yes | The controller of the tabs. |
| parentScroller | [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) | Yes | The controller of the parent scrollable container component. |
| childScroller | [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) | Yes | The controller of the child scrollable container component. |

**Examples**

See the example for [bindTabsToScrollable](#bindtabstoscrollable).

## bindTabsToScrollable

```TypeScript
bindTabsToScrollable(tabsController: TabsController, scroller: Scroller): void
```

Bind tabs to scrollable container component to automatically hide tab bar.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabs-comp-tabscontroller-c.md) | Yes | The controller of the tabs. |
| scroller | [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) | Yes | The controller of the scrollable container component. |

**Examples**

```TypeScript
@Entry
@Component
struct TabsExample {
  private arr: string[] = [];
  private parentTabsController: TabsController = new TabsController();
  private childTabsController: TabsController = new TabsController();
  private listScroller: Scroller = new Scroller();
  private parentScroller: Scroller = new Scroller();
  private childScroller: Scroller = new Scroller();

  aboutToAppear(): void {
    for (let i = 0; i < 20; i++) {
      this.arr.push(i.toString());
    }
    let context = this.getUIContext();
    context.bindTabsToScrollable(this.parentTabsController, this.listScroller);
    context.bindTabsToScrollable(this.childTabsController, this.listScroller);
    context.bindTabsToNestedScrollable(this.parentTabsController, this.parentScroller, this.childScroller);
  }

  aboutToDisappear(): void {
    let context = this.getUIContext();
    context.unbindTabsFromScrollable(this.parentTabsController, this.listScroller);
    context.unbindTabsFromScrollable(this.childTabsController, this.listScroller);
    context.unbindTabsFromNestedScrollable(this.parentTabsController, this.parentScroller, this.childScroller);
  }

  build() {
    Tabs({ barPosition: BarPosition.End, controller: this.parentTabsController }) {
      TabContent() {
        Tabs({ controller: this.childTabsController }) {
          TabContent() {
            List({ space: 20, initialIndex: 0, scroller: this.listScroller }) {
              ForEach(this.arr, (item: string) => {
                ListItem() {
                  Text(item)
                    .width('100%')
                    .height(100)
                    .fontSize(16)
                    .textAlign(TextAlign.Center)
                    .borderRadius(10)
                    .backgroundColor(Color.Gray)
                }
              }, (item: string) => item)
            }
            .scrollBar(BarState.Off)
            .width('90%')
            .height('100%')
            .contentStartOffset(56)
            .contentEndOffset(52)
          }.tabBar(SubTabBarStyle.of('Top tab'))
        }
        .width('100%')
        .height('100%')
        .barOverlap (true) // Make the tab bar overlap the TabContent component. This means that when the tab bar is hidden upwards or downwards, the area it occupies will not appear empty.
        .clip (true) // Clip any child components that extend beyond the Tabs component's boundaries, preventing accidental touches on the tab bar when it is hidden.
      }.tabBar(BottomTabBarStyle.of($r('app.media.startIcon'), 'Scroller linked with TabsControllers'))

      TabContent() {
        Scroll(this.parentScroller) {
            List({ space: 20, initialIndex: 0, scroller: this.childScroller }) {
              ForEach(this.arr, (item: string) => {
                ListItem() {
                  Text(item)
                    .width('100%')
                    .height(100)
                    .fontSize(16)
                    .textAlign(TextAlign.Center)
                    .borderRadius(10)
                    .backgroundColor(Color.Gray)
                }
              }, (item: string) => item)
            }
            .scrollBar(BarState.Off)
            .width('90%')
            .height('100%')
            .contentEndOffset(52)
            .nestedScroll({ scrollForward: NestedScrollMode.SELF_FIRST, scrollBackward: NestedScrollMode.SELF_FIRST })
        }
        .width('100%')
        .height('100%')
        .scrollBar(BarState.Off)
        .scrollable(ScrollDirection.Vertical)
        .edgeEffect(EdgeEffect.Spring)
      }.tabBar(BottomTabBarStyle.of($r('app.media.startIcon'), 'Nested Scroller linked with TabsController'))
    }
    .width('100%')
    .height('100%')
    .barOverlap (true) // Make the tab bar overlap the TabContent component. This means that when the tab bar is hidden upwards or downwards, the area it occupies will not appear empty.
    .clip (true) // Clip any child components that extend beyond the Tabs component's boundaries, preventing accidental touches on the tab bar when it is hidden.
  }
}
```

## closeBindSheet

```TypeScript
closeBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>): Promise<void>
```

Closes the sheet corresponding to **bindSheetContent**. This API uses a promise to return the result.

> **NOTE:** 
> 
> Closing a sheet using this API will not invoke the **shouldDismiss** callback.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bindSheetContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content to display on the sheet. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [120001](../errorcode-bindSheet.md#120001-incorrect-bindsheetcontent) | The bindSheetContent is incorrect. |
| [120003](../errorcode-bindSheet.md#120003-no-matching-modal-found) | The bindSheetContent cannot be found. |

**Examples**

```TypeScript
import { FrameNode, ComponentContent } from "@kit.ArkUI";
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

let contentNode: ComponentContent<Params>;
let gUIContext: UIContext;

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
    Button('Update BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.updateBindSheet(contentNode, {
          backgroundColor: Color.Pink,
        }, true)
          .then(() => {
            console.info('updateBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('updateBindSheet error: ' + err.code + ' ' + err.message);
          })
      })

    Button('Close BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.closeBindSheet(contentNode)
          .then(() => {
            console.info('closeBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('closeBindSheet error: ' + err.code + ' ' + err.message);
          })
      })
  }
}

@Entry
@Component
struct UIContextBindSheet {
  @State message: string = 'BindSheet';

  aboutToAppear() {
    gUIContext = this.getUIContext();
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    RelativeContainer() {
      Column() {
        Button('Open BindSheet')
          .fontSize(20)
          .onClick(() => {
            let uiContext = this.getUIContext();
            let uniqueId = this.getUniqueId();
            let frameNode: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
            let targetId = frameNode?.getFirstChild()?.getUniqueId();
            uiContext.openBindSheet(contentNode, {
              height: SheetSize.MEDIUM,
              backgroundColor: Color.Green,
              title: { title: "Title", subtitle: "subtitle" }
            }, targetId)
              .then(() => {
                console.info('openBindSheet success');
              })
              .catch((err: BusinessError) => {
                console.error('openBindSheet error: ' + err.code + ' ' + err.message);
              })
          })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

## constructor

```TypeScript
constructor()
```

Construct a **UIContext** object.

> **NOTE:** 
> 
> A **UIContext** object created using the constructor points to an ambiguous UI context, meaning it is not bound
> to any specific UI instance. The unique ID of such a UIContext instance is -1.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

function getUIContextByAtomicInterface(): UIContext {
  let callingScopeUIContext = UIContext.getCallingScopeUIContext();
  if (callingScopeUIContext) {
    hilog.info(0x00, 'testTag', `Get UIContext of calling scope.`)
    return callingScopeUIContext;
  }
  let allContexts = UIContext.getAllUIContexts();
  let length = allContexts.length;
  if (length === 1) {
    hilog.info(0x00, 'testTag', `Get UIContext of unique UI instance.`)
    return allContexts[0];
  }
  let lastFocusedUIContext = UIContext.getLastFocusedUIContext();
  if (lastFocusedUIContext) {
    hilog.info(0x00, 'testTag', `Get UIContext of last focused instance.`)
    return lastFocusedUIContext;
  }
  let lastForegroundUIContext = UIContext.getLastForegroundUIContext();
  if (lastForegroundUIContext) {
    hilog.info(0x00, 'testTag', `Get UIContext of last foregrounded instance.`)
    return lastForegroundUIContext;
  }
  if (length !== 0) {
    hilog.info(0x00, 'testTag', `Get UIContext with maximum instanceId.`)
    return allContexts[length - 1];
  }
  hilog.info(0x00, 'testTag', `Get UIContext of undefined calling scope.`)
  return new UIContext();
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  aboutToAppear() {
    let uiContext = this.getUIContext();
    hilog.info(0x00, 'testTag', `aboutToAppear UIContext: ${uiContext.getId()}`)
  }

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let resolvedUIContext = UIContext.resolveUIContext();
          let contextByAtomicInterface = getUIContextByAtomicInterface();
          hilog.info(0x00, 'testTag',
            `UIContext id: ${resolvedUIContext.getId()}, strategy: ${resolvedUIContext.strategy}, contextByAtomicInterface: ${contextByAtomicInterface.getId()}`);
          this.message = 'Welcome';
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## createAnimator

```TypeScript
createAnimator(options: AnimatorOptions): AnimatorResult
```

Creates an **Animator** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | Yes | Animator options. |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { AnimatorOptions, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Create the main window and set the home page for this ability.
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', err.message);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
      let uiContext = windowStage.getMainWindowSync().getUIContext();
      let options:AnimatorOptions = {
        duration: 1500,
        easing: "friction",
        delay: 0,
        fill: "forwards",
        direction: "normal",
        iterations: 3,
        begin: 200.0,
        end: 400.0
      };
      uiContext.createAnimator(options);
    });
  }
}
```

<a id="createanimator-1"></a>

## createAnimator

```TypeScript
createAnimator(options: AnimatorOptions | SimpleAnimatorOptions): AnimatorResult
```

Creates an **AnimatorResult** object for animations. Compared to the previous [createAnimator](#createanimator) API, this API adds support for the [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) &#124; [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | Yes | Animator options. |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { SimpleAnimatorOptions, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Create the main window and set the home page for this ability.
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', err.message);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
      let uiContext = windowStage.getMainWindowSync().getUIContext();
      let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).duration(2000);
      uiContext.createAnimator(options);
    });
  }
}
```

## createUIContextWithoutWindow

```TypeScript
static createUIContextWithoutWindow(context: common.UIAbilityContext | common.ExtensionContext) : UIContext | undefined
```

Creates a UI instance that does not depend on a window and returns its UI context. The created UI instance is a singleton.

> **NOTE:** 
> 
> The returned UI context can only be used to create [custom nodes](../../../ui/arkts-user-defined-node.md). It
> cannot be used for other UI operations.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [common.UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) &#124; [common.ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-extensioncontext-t.md) | Yes | Context corresponding to [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md) or [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) &#124; undefined | Context of the created UI instance, or **undefined** if creation fails. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. The number of parameters is incorrect. <br> 2. Invalid parameter type of context. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |

**Examples**

```TypeScript
// EntryAbility.ets
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    let uiContext: UIContext | undefined = UIContext.createUIContextWithoutWindow(this.context);
  }

  // ......
}
```

## destroyUIContextWithoutWindow

```TypeScript
static destroyUIContextWithoutWindow(): void
```

Destroys the UI instance created using [createUIContextWithoutWindow](#createuicontextwithoutwindow).

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
// EntryAbility.ets
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    let uiContext: UIContext | undefined = UIContext.createUIContextWithoutWindow(this.context);
    UIContext.destroyUIContextWithoutWindow();
  }

  // ......
}
```

## dispatchKeyEvent

```TypeScript
dispatchKeyEvent(node: number | string, event: KeyEvent): boolean
```

Dispach keyboard event to the frameNode with inspector key.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | number &#124; string | Yes | The uniqueId or inspector key of the target FrameNode. |
| event | [KeyEvent](../arkts-components/arkts-arkui-common-comp-keyevent-i.md) | Yes | The key event to be sent. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns whether the key event is consumed. |

**Examples**

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Row() {
      Row() {
        Button('Button1').id('Button1').onKeyEvent((event) => {
          console.info("Button1");
          return true;
        })
        Button('Button2').id('Button2').onKeyEvent((event) => {
          console.info("Button2");
          return true;
        })
      }
      .width('100%')
      .height('100%')
      .id('Row1')
      .onKeyEventDispatch((event) => {
        let context = this.getUIContext();
        context.getFocusController().requestFocus('Button1');
        return context.dispatchKeyEvent('Button1', event);
      })

    }
    .height('100%')
    .width('100%')
    .onKeyEventDispatch((event) => {
      if (event.type == KeyType.Down) {
        let context = this.getUIContext();
        context.getFocusController().requestFocus('Row1');
        return context.dispatchKeyEvent('Row1', event);
      }
      return true;
    })
  }
}
```

## enableEventPassthrough

```TypeScript
enableEventPassthrough(enabled: boolean, eventType: RawInputEventType): void
```

Whether to enable or disable event passthrough.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | enable or disable event passthrough. The default value is false. |
| eventType | [RawInputEventType](arkts-arkui-rawinputeventtype-e.md) | Yes | the type of raw input event. |

**Examples**

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('Enable Event Passthrough')
        .onClick(() => {
          this.getUIContext()?.enableEventPassthrough(true, RawInputEventType.TOUCH);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## enableSwipeBack

```TypeScript
enableSwipeBack(enabled: Optional<boolean>): void
```

whether to enable or disable swipe to back event.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](../arkts-components/arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | enable or disable swipe to back event. |

**Examples**

```TypeScript
@Entry
@Component
struct Index {
  @State isEnable: boolean = true;

  build() {
    RelativeContainer() {
      Button(`enable swipe back: ${this.isEnable}`).onClick(() => {
        this.isEnable = !this.isEnable;
        this.getUIContext().enableSwipeBack(this.isEnable);
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

## fp2px

```TypeScript
fp2px(value: number): number
```

Converts a value in fp units to a value in px.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Examples**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().fp2px(50),
          centerY: this.getUIContext().fp2px(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

## getAllUIContexts

```TypeScript
static getAllUIContexts(): UIContext[]
```

Obtains all currently valid UIContext instances.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)[] | Array of all currently valid UIContext instances. Returns an empty array if no valid UIContext instance exists. |

**Examples**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
          let uiContexts = UIContext.getAllUIContexts();
          hilog.info(0x00, 'testTag', `There are ${uiContexts.length} UIContext(s)`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## getAtomicServiceBar

```TypeScript
getAtomicServiceBar(): Nullable<AtomicServiceBar>
```

Get AtomicServiceBar.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Nullable](arkts-arkui-nullable-t.md)&lt;[AtomicServiceBar](arkts-arkui-arkui-uicontext-atomicservicebar-i.md)&gt; | The atomic service bar. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    console.info('Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        console.info('Get AtomServiceBar Successfully.');
      } else {
        console.error('Get AtomicServiceBar failed.');
      }
    });
  }
}
```

## getAttachedFrameNodeById

```TypeScript
getAttachedFrameNodeById(id: string): FrameNode | null
```

Get the FrameNode attached to current window by id.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | The id of FrameNode. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | The instance of FrameNode. |

**Examples**

```TypeScript
@Entry
@Component
struct MyComponent {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let node = this.getUIContext().getAttachedFrameNodeById("HelloWorld");
          console.info(`Find HelloWorld Tag:${node!.getNodeType()} id:${node!.getUniqueId()}`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## getCallingScopeUIContext

```TypeScript
static getCallingScopeUIContext(): UIContext | undefined
```

Obtains the UIContext of this [calling scope](../../../ui/arkts-global-interface.md#basic-concepts). This API returns **undefined** if the calling scope is ambiguous.

> **NOTE:** 
> 
> The returned UIContext object may point to a destroyed UI instance, which usually occurs when an asynchronous
> task is dispatched from an instance that has already been destroyed. As such, you are advised to verify its
> validity via the [isAvailable](#isavailable) API.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) &#124; undefined | UIContext of the current [calling scope](../../../ui/arkts-global-interface.md#basic-concepts). Returns **undefined** if the calling scope is ambiguous. |

**Examples**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
          let uiContext = UIContext.getCallingScopeUIContext();
          hilog.info(0x00, 'testTag', 'Current calling UIContext is : ' + uiContext?.isAvailable());
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## getComponentSnapshot

```TypeScript
getComponentSnapshot(): ComponentSnapshot
```

Get ComponentSnapshot.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c.md) | the ComponentSnapshot |

**Examples**

See the example for [ComponentSnapshot](arkts-apis-uicontext-componentsnapshot.md).

## getComponentUtils

```TypeScript
getComponentUtils(): ComponentUtils
```

get object ComponentUtils.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ComponentUtils](arkts-arkui-arkui-uicontext-componentutils-c.md) | object ComponentUtils. |

**Examples**

For the complete example, see [Example 1: Obtaining the ComponentUtils Object](arkts-arkui-arkui-componentutils.md#example-1-obtaining-the-componentutils-object).

## getContextMenuController

```TypeScript
getContextMenuController(): ContextMenuController
```

Get object context menu controller.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ContextMenuController](arkts-arkui-arkui-uicontext-contextmenucontroller-c.md) | object context menu controller. |

## getCursorController

```TypeScript
getCursorController(): CursorController
```

Get object cursor controller.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [CursorController](arkts-arkui-arkui-uicontext-cursorcontroller-c.md) | object cursor controller. |

**Examples**

See the example for [CursorController](arkts-apis-uicontext-cursorcontroller.md).

## getDialogPresenter

```TypeScript
getDialogPresenter(): DialogPresenter
```

Get the Dialog object.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DialogPresenter](arkts-arkui-arkui-uicontext-dialogpresenter-c.md) | Dialog object. |

**Examples**

See the example for [DialogPresenter](arkts-apis-uicontext-dialogpresenter.md).

## getDragController

```TypeScript
getDragController(): DragController
```

Get DragController.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md) | the DragController |

**Examples**

See the example for [DragController](./arkts-apis-uicontext-dragcontroller.md).

## getFilteredInspectorTree

```TypeScript
getFilteredInspectorTree(filters?: Array<string>): string
```

Obtains the component tree and component attributes. This API has a long processing time and is intended for <br>testing scenarios only.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filters | Array&lt;string&gt; | No | List of component attributes used for filtering. Currently, only the following filter fields are supported:<br>**"id"**: unique ID of the component. <br>**"src"**: source of the resource. <br>**"content"**: information or data contained in the element, component, or object. <br>**"editable"**: whether the component is editable. <br>**"scrollable"**: whether the component is scrollable. <br>**"selectable"**: whether the component is selectable. <br>**"focusable"**: whether the component is focusable. <br>**"focused"**: whether the component is currently focused. <br>If **filters** includes one or more fields, unspecified fields will be filtered out from the results. <br>If **filters** is not provided or is an empty array, none of the aforementioned fields <br>will be filtered out. <br>The following filter field is supported since API version 20: <br>**"isLayoutInspector"**: whether the component tree contains custom components. <br>If **filters** is omitted or <br>does not contain **"isLayoutInspector"**, the returned component tree <br>will not include custom component details. <br>Other filter fields are used only in testing scenarios. |

**Return value:**

| Type | Description |
| --- | --- |
| string | JSON string of the component tree and component attributes. For details about each field in the component, see the return value description of [getInspectorInfo](arkts-arkui-framenode-c.md#getinspectorinfo). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**Examples**

```TypeScript
uiContext.getFilteredInspectorTree(['id', 'src', 'content']);
```

```TypeScript
// xxx.ets
import { UIContext } from '@kit.ArkUI';
@Entry
@Component
struct ComponentPage {
  loopConsole(inspectorStr: string, i: string) {
    console.info(`InsTree ${i}| type: ${JSON.parse(inspectorStr).$type}, ID: ${JSON.parse(inspectorStr).$ID}`);
    if (JSON.parse(inspectorStr).$children) {
      i += '-';
      for (let index = 0; index < JSON.parse(inspectorStr).$children.length; index++) {
        this.loopConsole(JSON.stringify(JSON.parse(inspectorStr).$children[index]), i);
      }
    }
  }

  build() {
    Column() {
      Button('content').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        let inspectorStr = uiContext.getFilteredInspectorTree(['content']);
        console.info(`InsTree : ${inspectorStr}`);
        inspectorStr = JSON.stringify(JSON.parse(inspectorStr));
        this.loopConsole(inspectorStr, '-');
      })
      Button('isLayoutInspector').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        let inspectorStr = uiContext.getFilteredInspectorTree(['isLayoutInspector']);
        console.info(`InsTree : ${inspectorStr}`);
        inspectorStr = JSON.stringify(JSON.parse(inspectorStr).content);
        this.loopConsole(inspectorStr, '-');
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

When the "content" filter field is passed, the returned JSON string has the following structure:

```TypeScript
InsTree : {"$type":"root","width":"720.000000","height":"1280.000000","$resolution":"1.500000","$children":[{"$type":"Column","$ID":15,"type":"build-in","$rect":"[0.00, 72.00],[720.00,1208.00]","$debugLine":"","$attrs":{},"$children":[{"$type":"Button","$ID":16,"type":"build-in","$rect":"[293.00, 72.00],[427.00,132.00]","$debugLine":"","$attrs":{}},{"$type":"Button","$ID":18,"type":"build-in","$rect":"[237.00, 132.00],[484.00,192.00]","$debugLine":"","$attrs":{}}]}]}\
InsTree -| type: root, ID: undefined
InsTree --| type: Column, ID: 15
InsTree ---| type: Button, ID: 16
InsTree ---| type: Button, ID: 18
```

Since API version 20, when the "isLayoutInspector" filter field is passed, the returned JSON string structure includes an outer layer with "type" and "content" fields, where "content" contains the original JSON structure (as returned without this field), and the return value structure includes custom components. This JSON string structure is as follows:

```TypeScript
InsTree : {"type":"root","content":{"$type":"root","width":"720.000000","height":"1280.000000","$resolution":"1.500000","$children":[{"$type":"JsView","$ID":13,"type":"custom","state":{"observedPropertiesInfo":[],"viewInfo":{"componentName":"ComponentPage","id":14,"isV2":false,"isViewActive_":true}},"$rect":"[0.00, 72.00],[720.00,1208.00]","$debugLine":"{\"$line\":\"(0:0)\"}","viewTag":"ComponentPage","$attrs":{"viewKey":"13"},"$children":[{"$type":"Column","$ID":15, "type":"build-in","$rect":"[0.00, 72.00],[720.00,1208.00]","$debugLine":"","$attrs":{ ...
InsTree -| type: root, ID: undefined
InsTree --| type: JsView, ID: 13
InsTree ---| type: Column, ID: 15
InsTree ----| type: Button, ID: 16
InsTree ----| type: Button, ID: 18
```

## getFilteredInspectorTreeById

```TypeScript
getFilteredInspectorTreeById(id: string, depth: number, filters?: Array<string>): string
```

Obtains the attributes of the specified component and its child components. This API has a long processing time <br>and is intended for testing scenarios only.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | [ID](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id) of the target component. |
| depth | number | Yes | Number of layers of child components. If the value is **0**, the attributes of the specified component and all its child components are obtained. If the value is **1**, only the attributes of<br>the specified component are obtained. If the value is **2**, the attributes of <br>the specified component and its <br>level-1 child components are obtained. The rest can be deduced by analogy. |
| filters | Array&lt;string&gt; | No | List of component attributes used for filtering. Currently, only the following filter fields are supported:<br>**"id"**: unique ID of the component. <br>**"src"**: source of the resource. <br>**"content"**: information or data contained in the element, component, or object. <br>**"editable"**: whether the component is editable. <br>**"scrollable"**: whether the component is scrollable. <br>**"selectable"**: whether the component is selectable. <br>**"focusable"**: whether the component is focusable. <br>**"focused"**: whether the component is currently focused. <br>If **filters** includes one or more fields, unspecified fields will be filtered out from the results. <br>If **filters** is not provided or is an empty array, none of the aforementioned fields <br>will be filtered out. <br>Other filter fields are used only in testing scenarios. |

**Return value:**

| Type | Description |
| --- | --- |
| string | JSON string of the attributes of the specified component and its child components. For details about each field in the component, see the return value <br>description of [getInspectorInfo](arkts-arkui-framenode-c.md#getinspectorinfo). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**Examples**

```TypeScript
uiContext.getFilteredInspectorTreeById('testId', 0, ['id', 'src', 'content']);
```

```TypeScript
import { UIContext } from '@kit.ArkUI';
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Text("Hello World")
        .fontSize(20)
        .id("TEXT")
      Button('getFilteredInspectorTreeById').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        try {
          let inspectorStr = uiContext.getFilteredInspectorTreeById('TEXT', 1, ["id", "src"]);
          console.info(`result1: ${inspectorStr}`);
          inspectorStr = JSON.stringify(JSON.parse(inspectorStr)['$children'][0]);
          console.info(`result2: ${inspectorStr}`);
          inspectorStr = uiContext.getFilteredInspectorTreeById('TEXT', 1, ["src"]);
          inspectorStr = JSON.stringify(JSON.parse(inspectorStr)['$children'][0]);
          console.info(`result3: ${inspectorStr}`);
        } catch(e) {
          console.error(`getFilteredInspectorTreeById error: ${e}`);
        }
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

This JSON string structure is as follows:

```TypeScript
result1: {"$type":"root","width":"1260.000000","height":"2720.000000","$resolution":"3.250000","$children":[{"$type":"Text","$ID":6,"type":"build-in","$rect":"[457.00, 123.00],[804.00,199.00]","$debugLine":"","$attrs":{"id":"TEXT","isLayoutDirtyMarked":false,"isRenderDirtyMarked":false,"isMeasureBoundary":false,"hasPendingRequest":false,"isFirstBuilding":false}}]}
result2: {"$type":"Text","$ID":6,"type":"build-in","$rect":"[457.00, 123.00],[804.00,199.00]","$debugLine":"","$attrs":{"id":"TEXT","isLayoutDirtyMarked":false,"isRenderDirtyMarked":false,"isMeasureBoundary":false,"hasPendingRequest":false,"isFirstBuilding":false}}
result3: {"$type":"Text","$ID":6,"type":"build-in","$rect":"[457.00, 123.00],[804.00,199.00]","$debugLine":"","$attrs":{"isLayoutDirtyMarked":false,"isRenderDirtyMarked":false,"isMeasureBoundary":false,"hasPendingRequest":false,"isFirstBuilding":false}}
```

## getFocusController

```TypeScript
getFocusController(): FocusController
```

Get FocusController.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [FocusController](arkts-arkui-arkui-uicontext-focuscontroller-c.md) | the FocusController |

**Examples**

See the example for [FocusController](arkts-apis-uicontext-focuscontroller.md).

## getFont

```TypeScript
getFont(): Font
```

Obtains a **Font** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Font](arkts-arkui-arkui-uicontext-font-c.md) | **Font** object. |

**Examples**

See the example for [Font](arkts-apis-uicontext-font.md).

## getFrameNodeById

```TypeScript
getFrameNodeById(id: string): FrameNode | null
```

Get FrameNode by id.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | The id of FrameNode. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | The instance of FrameNode. |

**Examples**

See Example of Obtaining the Root Node.

## getFrameNodeByUniqueId

```TypeScript
getFrameNodeByUniqueId(id: number): FrameNode | null
```

Get FrameNode by uniqueId. Obtains the entity node, FrameNode, of a component on the component tree using its uniqueId. The return value depends on the type of component associated with the uniqueId.

1. If the uniqueId corresponds to a built-in component, the associated FrameNode is returned.
2. If the uniqueId corresponds to a custom component: If the component has rendered content, its root node is
returned, with the type __Common__; if the component has no rendered content, the FrameNode of its first child component is returned.
3. If the uniqueId does not correspond to any component, null is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | The uniqueId of the FrameNode. |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | The FrameNode with the target uniqueId, or null if the frameNode is not existed. |

**Examples**

```TypeScript
import { UIContext, FrameNode } from '@kit.ArkUI';

@Entry
@Component
struct MyComponent {
  aboutToAppear() {
    let uniqueId: number = this.getUniqueId();
    let uiContext: UIContext = this.getUIContext();
    if (uiContext) {
      let node: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
    }
  }

  build() {
    // ...
  }
}
```

## getHostContext

```TypeScript
getHostContext(): Context | undefined
```

Obtains the context of this ability.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Context](arkts-arkui-context-t.md) &#124; undefined | Context of the ability. The context type depends on the ability type. For example, if this API is called in a page within a UIAbility window, the returned context type is [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md). If this API is called in a page within an ExtensionAbility window, the returned context type is [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md). If the ability context does not exist, **undefined** is returned. |

**Examples**

```TypeScript
@Entry
@Component
struct Index {
  uiContext = this.getUIContext();

  build() {
    Row() {
      Column() {
        Text("cacheDir='" + this.uiContext?.getHostContext()?.cacheDir + "'")
          .fontSize(25)
          .border({ color: Color.Red, width: 2 })
          .padding(50)
        Text("bundleCodeDir='" + this.uiContext?.getHostContext()?.bundleCodeDir + "'")
          .fontSize(25)
          .border({ color: Color.Red, width: 2 })
          .padding(50)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## getId

```TypeScript
getId(): number
```

Obtains the unique ID of a UI instance object. In multi-instance scenarios, you can use this unique ID to distinguish between different UI instance objects for easier management.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Unique ID of the backend instance. The value range is [-1, +∞). |

**Examples**

```TypeScript
@Entry
@Component
struct Index{
  build(){
    Column()
      .width("100%")
      .height("100%")
      .onClick(() => {
      console.info(`id:${this.getUIContext()?.getId()}`);
    })
  }
}
```

## getKeyboardAvoidMode

```TypeScript
getKeyboardAvoidMode(): KeyboardAvoidMode
```

Obtains the avoidance mode of the virtual keyboard.

> **NOTE:** 
> 
> Since API version 18, the **getKeyboardAvoidMode** API returns an enumeration value of **KeyboardAvoidMode**,
> which is an integer. Before API version 18, the **getKeyboardAvoidMode** API returns a string.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [KeyboardAvoidMode](arkts-arkui-arkui-uicontext-keyboardavoidmode-e.md) | Avoidance mode of the virtual keyboard. |

**Examples**

See [Example 4: Setting the Keyboard Avoidance Mode to Resize](../arkui-ts/ts-universal-attributes-expand-safe-area.md#example-4-setting-the-keyboard-avoidance-mode-to-resize), [Example 5: Setting Keyboard Avoidance Mode to Offset](../arkui-ts/ts-universal-attributes-expand-safe-area.md#example-5-setting-keyboard-avoidance-mode-to-offset), and [Example 6: Switching Avoidance Modes](../arkui-ts/ts-universal-attributes-expand-safe-area.md#example-6-switching-avoidance-modes).

```TypeScript
// EntryAbility.ets
import { KeyboardAvoidMode, UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility{
  onWindowStageCreate(windowStage: window.WindowStage) {

      windowStage.loadContent('pages/Index', (err, data) => {
        let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
        let currentKeyboardAvoidMode = uiContext.getKeyboardAvoidMode();
        console.info("KeyboardAvoidMode:", JSON.stringify(currentKeyboardAvoidMode));
      });
    }
}
```

## getLastFocusedUIContext

```TypeScript
static getLastFocusedUIContext(): UIContext | undefined
```

Obtains the UIContext of the UI instance that most recently switched to the focused state.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) &#124; undefined | UIContext of the UI instance that most recently switched to the focused state. Returns **undefined** if the most recently focused instance has been destroyed or if no instance has ever been focused. |

**Examples**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
          let uiContext = UIContext.getLastFocusedUIContext();
          hilog.info(0x00, 'testTag', 'Current calling UIContext is : ' + uiContext?.isAvailable());
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## getLastForegroundUIContext

```TypeScript
static getLastForegroundUIContext(): UIContext | undefined
```

Obtains the UIContext of the UI instance that most recently switched to the foreground state.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) &#124; undefined | UIContext of the UI instance that most recently switched to the foreground state. Returns **undefined** if the most recently foreground UI instance has been destroyed or if no UI instance has ever been in the foreground. |

**Examples**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
          let uiContext = UIContext.getLastForegroundUIContext();
          hilog.info(0x00, 'testTag', 'Current calling UIContext is : ' + uiContext?.isAvailable());
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## getMagnifier

```TypeScript
getMagnifier(): Magnifier
```

Obtains a [Magnifier](arkts-arkui-arkui-uicontext-magnifier-c.md) object, which can be used to control the display and hiding of a magnifier.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Magnifier](arkts-arkui-arkui-uicontext-magnifier-c.md) | **Magnifier** object, which can be used to control the display and hiding of a magnifier. |

**Examples**

See the example of the bind API in [Magnifier](arkts-apis-uicontext-magnifier.md).

## getMaxFontScale

```TypeScript
getMaxFontScale(): number
```

Get the max font scale.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | The max font scale. |

**Examples**

Refer to the [configuration tag](../../../quick-start/app-configuration-file.md#configuration) and set the value of fontSizeMaxScale to "1.75".

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('getMaxFontScale').onClick(() => {
        console.info('getMaxFontScale', this.getUIContext().getMaxFontScale().toFixed(2));
      });
    }
  }
}
```

## getMeasureUtils

```TypeScript
getMeasureUtils(): MeasureUtils
```

Obtains a **MeasureUtils** object for text calculation.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [MeasureUtils](arkts-arkui-arkui-uicontext-measureutils-c.md) | Text metrics, such as text height and width. |

**Examples**

See the example for [MeasureUtils](arkts-apis-uicontext-measureutils.md).

## getMediaQuery

```TypeScript
getMediaQuery(): MediaQuery
```

get object mediaQuery.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [MediaQuery](arkts-arkui-arkui-uicontext-mediaquery-c.md) | object MediaQuery. |

**Examples**

See the mediaquery Example.

## getNavigationInfoByUniqueId

```TypeScript
getNavigationInfoByUniqueId(id: number): observer.NavigationInfo | undefined
```

Get navigation information of the frameNode with uniqueId.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | The uniqueId of the target FrameNode. |

**Return value:**

| Type | Description |
| --- | --- |
| [observer.NavigationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md) &#124; undefined | The navigation information of the frameNode with the target uniqueId, or undefined if the frameNode is not existed or does not have navigation information. |

**Examples**

See the example of [getPageInfoByUniqueId](#getpageinfobyuniqueid).

## getOverlayManager

```TypeScript
getOverlayManager(): OverlayManager
```

Obtains the OverlayManager object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [OverlayManager](arkts-arkui-arkui-uicontext-overlaymanager-c.md) | OverlayManager instance obtained. |

**Examples**

See the example for [OverlayManager](arkts-apis-uicontext-overlaymanager.md).

## getOverlayManagerOptions

```TypeScript
getOverlayManagerOptions(): OverlayManagerOptions
```

Get object OverlayManagerOptions.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [OverlayManagerOptions](arkts-arkui-arkui-uicontext-overlaymanageroptions-i.md) | object OverlayManagerOptions. |

**Examples**

See the example for [OverlayManager](arkts-apis-uicontext-overlaymanager.md).

## getPageInfoByUniqueId

```TypeScript
getPageInfoByUniqueId(id: number): PageInfo
```

Get page information of the frameNode with uniqueId.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | The uniqueId of the target FrameNode. |

**Return value:**

| Type | Description |
| --- | --- |
| [PageInfo](arkts-arkui-arkui-uicontext-pageinfo-i.md) | The page information of the frameNode with the target uniqueId, includes navDestination and router page information. If the frame node does not have navDestination and router page information, it will return an empty object. |

**Examples**

```TypeScript
import { UIContext, PageInfo } from '@kit.ArkUI';

@Entry
@Component
struct PageInfoExample {
  @Provide('pageInfos') pageInfos: NavPathStack = new NavPathStack();

  build() {
    Column() {
      Navigation(this.pageInfos) {
        NavDestination() {
          MyComponent()
        }
      }.id('navigation')
    }
  }
}

@Component
struct MyComponent {
  @State content: string = '';

  build() {
    Column() {
      Text('PageInfoExample')
      Button('click').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        const uniqueId: number = this.getUniqueId();
        const pageInfo: PageInfo = uiContext.getPageInfoByUniqueId(uniqueId);
        console.info('pageInfo: ' + JSON.stringify(pageInfo));
        console.info('navigationInfo: ' + JSON.stringify(uiContext.getNavigationInfoByUniqueId(uniqueId)));
      })
      TextArea({
        text: this.content
      })
      .width('100%')
      .height(100)
    }
    .width('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

## getPageRootNode

```TypeScript
getPageRootNode(): FrameNode | null
```

Obtains the root node of the page corresponding to the UIContext.

**Since:** 24

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) &#124; null | FrameNode of the root node of the page or **null**.<br>If no valid FrameNode is available, **null** is returned. <br>If no page is loaded in the window, **null** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [120007](../errorcode-uicontext.md#120007-instance-not-exist) | The UIContext is not available. |

**Examples**

```TypeScript
@Entry
@Component
struct NavigationExample {
  @Provide('pageInfos') pageInfos: NavPathStack = new NavPathStack();
  private arr: number[] = [1, 2, 3];
  @State pageRootNode: FrameNode | null = null;

  @Builder
  pageMap(name: string) {
    if (name === 'NavDestinationTitle1') {
      PageOne();
    } else if (name === 'NavDestinationTitle2') {
      PageTwo();
    } else if (name === 'NavDestinationTitle3') {
      PageThree();
    }
  }

  onPageShow(): void {
    setTimeout(() => {
      this.pageRootNode = this.getUIContext()?.getPageRootNode();
      console.info('NavigationExample' + JSON.stringify(this.getUIContext().getPageRootNode()));
    });
  }

  build() {
    Column() {
      Navigation(this.pageInfos) {
        Text(`CurrentPageRootNode info: Tag ${this.pageRootNode?.getNodeType()}, NodeId: ${this.pageRootNode?.getUniqueId()}`)
          .width('90%')
          .height(40)
          .backgroundColor('#FFFFFF')
        List({ space: 12 }) {
          ForEach(this.arr, (item: number) => {
            ListItem() {
              Text('Page' + item)
                .width('100%')
                .height(72)
                .backgroundColor('#FFFFFF')
                .borderRadius(24)
                .fontSize(16)
                .fontWeight(500)
                .textAlign(TextAlign.Center)
                .onClick(() => {
                  this.pageInfos.pushPath({ name: 'NavDestinationTitle' + item });
                })
            }
          }, (item: number) => item.toString())
        }
        .width('100%')
        .margin({ top: 12 })
      }
      .title('Main Title')
      .mode(NavigationMode.Stack)
      .navDestination(this.pageMap)
    }
    .height('100%')
    .width('100%')
    .backgroundColor('#F1F3F5')
  }
}

@Component
export struct PageOne {
  @Consume('pageInfos') pageInfos: NavPathStack;

  aboutToDisappear(): void {
    console.info('PageOne', 'aboutToDisappear');
  }

  build() {
    NavDestination() {
      Column() {
        Text('PageOne')
        Text(`CurrentPageRootNode info: Tag ${this.getUIContext()?.getPageRootNode()?.getNodeType()}, NodeId: ${this.getUIContext()?.getPageRootNode()?.getUniqueId()}`)
      }.width('100%').height('100%')
    }.title('NavDestinationTitle1')
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // Pop the top entry of the route stack.
      console.info('pop' + 'return value' + JSON.stringify(popDestinationInfo));
      return true;
    })
  }
}

@Component
export struct PageTwo {
  @Consume('pageInfos') pageInfos: NavPathStack;

  build() {
    NavDestination() {
      Column() {
        Text('PageTwo')
        Text(`CurrentPageRootNode info: Tag ${this.getUIContext()?.getPageRootNode()?.getNodeType()}, NodeId: ${this.getUIContext()?.getPageRootNode()?.getUniqueId()}`)
      }.width('100%').height('100%')
    }.title('NavDestinationTitle2')
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // Pop the top entry of the route stack.
      console.info('pop' + 'return value' + JSON.stringify(popDestinationInfo));
      return true;
    })
  }
}

@Component
export struct PageThree {
  @Consume('pageInfos') pageInfos: NavPathStack;

  build() {
    NavDestination() {
      Column() {
        Text('PageThree')
        Text(`CurrentPageRootNode info: Tag ${this.getUIContext()?.getPageRootNode()?.getNodeType()}, NodeId: ${this.getUIContext()?.getPageRootNode()?.getUniqueId()}`)
      }.width('100%').height('100%')
    }.title('NavDestinationTitle3')
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // Pop the top entry of the route stack.
      console.info('pop' + 'return value' + JSON.stringify(popDestinationInfo));
      return true;
    })
  }
}
```

## getPixelRoundMode

```TypeScript
getPixelRoundMode(): PixelRoundMode
```

Obtains the pixel rounding mode for this page.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PixelRoundMode](arkts-arkui-pixelroundmode-e.md) | Pixel rounding mode of the current page. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility{
  onWindowStageCreate(windowStage: window.WindowStage) {

      windowStage.loadContent('pages/Index', (err, data) => {
        let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
        console.info("pixelRoundMode : " + uiContext.getPixelRoundMode().valueOf());
      });
    }
}
```

## getPromptAction

```TypeScript
getPromptAction(): PromptAction
```

Obtains a PromptAction object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md) | PromptAction object. |

**Examples**

See the example for [PromptAction](arkts-apis-uicontext-promptaction.md).

## getRouter

```TypeScript
getRouter(): Router
```

Obtains a Router object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Router](arkts-arkui-arkui-uicontext-router-c.md) | Router object. |

**Examples**

See the example for pushUrl.

## getSharedLocalStorage

```TypeScript
getSharedLocalStorage(): LocalStorage | undefined
```

Obtains the **LocalStorage** instance shared by this stage.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LocalStorage](arkts-arkui-localstorage-c.md) &#124; undefined | **LocalStorage** instance if it exists; **undefined** if it does not exist. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  storage: LocalStorage = new LocalStorage();

  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', this.storage);
  }
}
```

```TypeScript
// Index.ets

@Entry
@Component
struct SharedLocalStorage {
  localStorage = this.getUIContext().getSharedLocalStorage();

  build() {
    Row() {
      Column() {
        Button("Change Local Storage to 47")
          .onClick(() => {
            this.localStorage?.setOrCreate("propA", 47);
          })
        Button("Get Local Storage")
          .onClick(() => {
            console.info(`localStorage: ${this.localStorage?.get("propA")}`);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## getSmartGestureController

```TypeScript
getSmartGestureController(): SmartGestureController
```

Get object smart gesture controller.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [SmartGestureController](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md) | object smart gesture controller. |

**Examples**

For details, see Example 1: Enabling Smart Gestures and Customizing Action Handling.

## getTextMenuController

```TypeScript
getTextMenuController(): TextMenuController
```

Obtains a [TextMenuController](arkts-arkui-arkui-uicontext-textmenucontroller-c.md) object, which can be used to control the context menu on selection.

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 16.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [TextMenuController](arkts-arkui-arkui-uicontext-textmenucontroller-c.md) | Obtained **TextMenuController** object. |

**Examples**

See the example for [TextMenuController](arkts-apis-uicontext-textmenucontroller.md).

## getUIInspector

```TypeScript
getUIInspector(): UIInspector
```

Obtains the **UIInspector** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIInspector](arkts-arkui-arkui-uicontext-uiinspector-c.md) | **UIInspector** object. |

**Examples**

See the example for [UIInspector](./arkts-apis-uicontext-uiinspector.md).

## getUIObserver

```TypeScript
getUIObserver(): UIObserver
```

Obtains the **UIObserver** object.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIObserver](arkts-arkui-arkui-uicontext-uiobserver-c.md) | **UIObserver** object. |

**Examples**

```TypeScript
@Component
struct PageOne {
  build() {
    NavDestination() {
      Text("pageOne")
    }.title("pageOne")
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  PageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    this.getUIContext().getUIObserver().on('navDestinationUpdate', (info) => {
      console.info('NavDestination state update', JSON.stringify(info));
    });
  }

  aboutToDisappear() {
    this.getUIContext().getUIObserver().off('navDestinationUpdate');
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button("push").onClick(() => {
          this.stack.pushPath({ name: "pageOne" });
        })
      }
      .title("Navigation")
      .navDestination(this.PageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## getWindowHeightBreakpoint

```TypeScript
getWindowHeightBreakpoint(): HeightBreakpoint
```

Obtains the height breakpoint value of the window where this instance is located. The specific value is determined based on the window aspect ratio. For details, see [HeightBreakpoint](arkts-arkui-heightbreakpoint-e.md).

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [HeightBreakpoint](arkts-arkui-heightbreakpoint-e.md) | Height breakpoint value of the window where the current instance is located. If the window aspect ratio is 0, **HEIGHT_SM** is returned. |

**Examples**

```TypeScript
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
        Button() {
          Text('test')
            .fontSize(30)
        }
        .onClick(() => {
          let uiContext: UIContext = this.getUIContext();
          let heightBp: HeightBreakpoint = uiContext.getWindowHeightBreakpoint();
          let widthBp: WidthBreakpoint = uiContext.getWindowWidthBreakpoint();
          console.info(`Window heightBP: ${heightBp}, widthBp: ${widthBp}`);
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## getWindowId

```TypeScript
getWindowId(): number | undefined
```

Obtains the ID of the window to which the current application instance belongs.

> **NOTE:** 
> 
> If the UIContext resides inside a
> [UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) that runs in the main
> application process, the top-level window ID of the main application is returned.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number &#124; undefined | ID of the window to which the current application instance belongs. If the window does not exist, **undefined** is returned. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  aboutToAppear() {
    const windowId = this.getUIContext().getWindowId();
    hilog.info(0x0000, 'testTag', 'current window id: %{public}d', windowId ?? -1);
  }

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## getWindowName

```TypeScript
getWindowName(): string | undefined
```

Obtains the name of the window where this instance is located.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; undefined | Name of the window where the current instance is located. If the window does not exist, **undefined** is returned. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  aboutToAppear() {
    const windowName = this.getUIContext().getWindowName();
    console.info('WindowName ' + windowName);
    if (windowName) {
      const currWindow = window.findWindow(windowName);
      const windowProperties = currWindow.getWindowProperties();
      console.info(`Window width ${windowProperties.windowRect.width}, height ${windowProperties.windowRect.height}`);
    }
  }

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## getWindowWidthBreakpoint

```TypeScript
getWindowWidthBreakpoint(): WidthBreakpoint
```

Obtains the width breakpoint value of the window where this instance is located. The specific value is determined by the vp value of the window width. For details, see [WidthBreakpoint](arkts-arkui-widthbreakpoint-e.md).

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [WidthBreakpoint](arkts-arkui-widthbreakpoint-e.md) | Width breakpoint value of the window where the current instance is located. If the window width is 0 vp, **WIDTH_XS** is returned. |

**Examples**

```TypeScript
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
        Button() {
          Text('test')
            .fontSize(30)
        }
        .onClick(() => {
          let uiContext: UIContext = this.getUIContext();
          let widthBp: WidthBreakpoint = uiContext.getWindowWidthBreakpoint();
          console.info(`Window widthBp: ${widthBp}`);
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## isAvailable

```TypeScript
isAvailable(): boolean
```

Checks whether the UI instance corresponding to this **UIContext** object is valid. The **UIContext** object can be obtained using the [getUIContext](../../../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10) API. A UI instance is considered valid when the backend UI instance exists. UIContext objects created using **new UIContext()** have no corresponding UI instance. After multiple [loadContent](../../../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9) operations, old UI instances become invalid. In multi-window scenarios, when a window is closed, its UI instance becomes invalid. In summary, a UIContext object is invalid when it has no corresponding backend UI instance.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the UI instance corresponding to the current **UIContext** object is valid. The value **true** indicates yes, and the value **false** indicates no. |

**Examples**

```TypeScript
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct UIContextCompare {
  @State result1: string = '';
  @State result2: string = '';

  build() {
    Column() {
      Text('getUIContext() result: ' + this.result1)
        .fontSize(20)
        .margin(10)

      Text('new UIContext() result: ' + this.result2)
        .fontSize(20)
        .margin(10)

      Divider().margin(20)

      Button('getUIContext()')
        .width('70%')
        .height(50)
        .margin(10)
        .onClick(() => {
          try {
            const ctx: UIContext = this.getUIContext();
            const available: boolean = ctx.isAvailable();
            this.result1 = `Status: ${available} (Valid UI instance)`;
            console.info('getUIContext test:', available);
          } catch (error) {
            this.result1 = 'Error: ' + (error instanceof Error ? error.message : String(error));
          }
        })

      Button('new UIContext()')
        .width('70%')
        .height(50)
        .margin(10)
        .onClick(() => {
          try {
            const ctx: UIContext = new UIContext();
            const available: boolean = ctx.isAvailable();
            this.result2 = `Status: ${available} (Invalid UI instance)`;
            console.info('new UIContext test:', available);
          } catch (error) {
            this.result2 = 'Error: ' + (error instanceof Error ? error.message : String(error));
          }
        })
    }
    .width('100%')
    .height('100%')
    .padding(20)
  }
}
```

## isEasySplit

```TypeScript
isEasySplit(): boolean
```

Checks whether the current UI instance is in easy split mode.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the current UI instance is in easy split mode; returns false otherwise. |

**Examples**

```TypeScript
@Entry
@Component
struct Index {
  @State isEasySplit: boolean = false;

  build() {
    Column() {
      Text(`${this.isEasySplit ? 'current is easy split mode' : 'current is not easy split mode'}`)
        .fontSize(20)
        .margin(10)
      Button('Check EasySplit')
        .onClick(() => {
          this.isEasySplit = this.getUIContext()?.isEasySplit();
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## isFollowingSystemFontScale

```TypeScript
isFollowingSystemFontScale(): boolean
```

Checks whether current font scale follows the system.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if current font scale follows the system; returns false otherwise. |

**Examples**

Refer to the [configuration tag](../../../quick-start/app-configuration-file.md#configuration) and set the value of fontSizeScale to "followSystem".

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('isFollowingSystemFontScale').onClick(() => {
        console.info('isFollowingSystemFontScale', this.getUIContext().isFollowingSystemFontScale());
      });
    }
  }
}
```

## keyframeAnimateTo

```TypeScript
keyframeAnimateTo(param: KeyframeAnimateParam, keyframes: Array<KeyframeState>): void
```

Generates a key frame animation. For details about how to use this API, see [keyframeAnimateTo](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-common.md).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [KeyframeAnimateParam](../arkts-components/arkts-arkui-common-comp-keyframeanimateparam-i.md) | Yes | Overall animation parameter of the keyframe animation. |
| keyframes | Array&lt;[KeyframeState](../arkts-components/arkts-arkui-common-comp-keyframestate-i.md)&gt; | Yes | List of all keyframe states. |

**Examples**

```TypeScript
// xxx.ets
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct KeyframeDemo {
  @State myScale: number = 1.0;
  uiContext: UIContext | undefined = undefined;

  aboutToAppear() {
    this.uiContext = this.getUIContext();
  }

  build() {
    Column() {
      Circle()
        .width(100)
        .height(100)
        .fill("#46B1E3")
        .margin(100)
        .scale({ x: this.myScale, y: this.myScale })
        .onClick(() => {
          if (!this.uiContext) {
            console.error("no uiContext, keyframe failed");
            return;
          }
          this.myScale = 1;
          // Configure the keyframe animation to play three times.
          this.uiContext.keyframeAnimateTo({
              iterations: 3,
              expectedFrameRateRange: {
                min: 10,
                max: 120,
                expected: 60,
              }
            }, [
            {
              // The first keyframe animation lasts for 800 ms, during which the scale attribute changes from 1 to 1.5.
              duration: 800,
              event: () => {
                this.myScale = 1.5;
              }
            },
            {
              // The second keyframe animation lasts for 500 ms, during which the scale attribute changes from 1.5 to 1.
              duration: 500,
              event: () => {
                this.myScale = 1;
              }
            }
          ]);
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

## lpx2px

```TypeScript
lpx2px(value: number): number
```

Converts a value in lpx units to a value in px.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Examples**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().lpx2px(50),
          centerY: this.getUIContext().lpx2px(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

## openBindSheet

```TypeScript
openBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>, sheetOptions?: SheetOptions, targetId?: number): Promise<void>
```

Creates a sheet whose content is as defined in **bindSheetContent** and displays the sheet. This API uses a promise to return the result.

> **NOTE:** 
> 
> 1. When calling this API, if no valid value is provided for **targetId**, you won't be able to set
> **SheetOptions.preferType** to **POPUP** or **SheetOptions.mode** to **EMBEDDED**.
> 
> 2. Since [updateBindSheet](#updatebindsheet) and [closeBindSheet](#closebindsheet)depend on **bindSheetContent**, you need to maintain the passed **bindSheetContent** yourself.
> 
> 3. Setting **SheetOptions.UIContext** is not supported.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bindSheetContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content to display on the sheet. |
| sheetOptions | [SheetOptions](../arkts-components/arkts-arkui-common-comp-sheetoptions-i.md) | No | Style of the sheet.<br>**NOTE:** <br>1. **SheetOptions.uiContext** cannot be set. Its value is fixed to the **UIContext** object of the current instance.<br>2. If **targetId** is not passed in, **SheetOptions.preferType** cannot be set to **POPUP**; if **POPUP** is set, it will be replaced with **CENTER**.<br>3. If **targetId** is not passed in, **SheetOptions.mode** cannot be set to **EMBEDDED**; the default mode is **OVERLAY**.<br>4. For the default values of other attributes, see [SheetOptions](../arkts-components/arkts-arkui-common-comp-sheetoptions-i.md). |
| targetId | number | No | ID of the component to be bound. If this parameter is not set, no component is bound. If the ID does not exist, the error code 120004 is returned. Returns error code 401 if **undefined** is passed in. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [120001](../errorcode-bindSheet.md#120001-incorrect-bindsheetcontent) | The bindSheetContent is incorrect. |
| [120002](../errorcode-bindSheet.md#120002-modal-for-bindsheetcontent-already-exists) | The bindSheetContent already exists. |
| [120004](../errorcode-bindSheet.md#120004-specified-targetid-does-not-exist) | The targetId does not exist. |
| [120005](../errorcode-bindSheet.md#120005-node-specified-by-targetid-is-not-mounted-on-the-component-tree) | The node of targetId is not in the component tree. |
| [120006](../errorcode-bindSheet.md#120006-node-specified-by-targetid-is-not-a-child-of-a-page-node-or-navdestination-node) | The node of targetId is not a child of the page node or NavDestination node. |

**Examples**

```TypeScript
import { FrameNode, ComponentContent } from "@kit.ArkUI";
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

let contentNode: ComponentContent<Params>;
let gUIContext: UIContext;

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
    Button('Update BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.updateBindSheet(contentNode, {
          backgroundColor: Color.Pink,
        }, true)
          .then(() => {
            console.info('updateBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('updateBindSheet error: ' + err.code + ' ' + err.message);
          })
      })

    Button('Close BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.closeBindSheet(contentNode)
          .then(() => {
            console.info('closeBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('closeBindSheet error: ' + err.code + ' ' + err.message);
          })
      })
  }
}

@Entry
@Component
struct UIContextBindSheet {
  @State message: string = 'BindSheet';

  aboutToAppear() {
    gUIContext = this.getUIContext();
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    RelativeContainer() {
      Column() {
        Button('Open BindSheet')
          .fontSize(20)
          .onClick(() => {
            let uiContext = this.getUIContext();
            let uniqueId = this.getUniqueId();
            let frameNode: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
            let targetId = frameNode?.getFirstChild()?.getUniqueId();
            uiContext.openBindSheet(contentNode, {
              height: SheetSize.MEDIUM,
              backgroundColor: Color.Green,
              title: { title: "Title", subtitle: "subtitle" }
            }, targetId)
              .then(() => {
                console.info('openBindSheet success');
              })
              .catch((err: BusinessError) => {
                console.error('openBindSheet error: ' + err.code + ' ' + err.message);
              })
          })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

## postDelayedFrameCallback

```TypeScript
postDelayedFrameCallback(frameCallback: FrameCallback, delayTime: number): void
```

Post a frame callback to run on the next frame after the specified delay.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| frameCallback | [FrameCallback](arkts-arkui-arkui-uicontext-framecallback-c.md) | Yes | The frame callback to run on the next frame. |
| delayTime | number | Yes | The delay time in milliseconds, |

**Examples**

```TypeScript
import { FrameCallback } from '@kit.ArkUI';

class MyFrameCallback extends FrameCallback {
  private tag: string;

  constructor(tag: string) {
    super();
    this.tag = tag;
  }

  onFrame(frameTimeNanos: number) {
    console.info('MyFrameCallback ' + this.tag + ' ' + frameTimeNanos.toString());
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Button('Invoke postDelayedFrameCallback')
        .onClick(() => {
          this.getUIContext().postDelayedFrameCallback(new MyFrameCallback('delayTask'), 5);
        })
    }
  }
}
```

## postFrameCallback

```TypeScript
postFrameCallback(frameCallback: FrameCallback): void
```

Post a frame callback to run on the next frame.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| frameCallback | [FrameCallback](arkts-arkui-arkui-uicontext-framecallback-c.md) | Yes | The frame callback to run on the next frame. |

**Examples**

```TypeScript
import { FrameCallback } from '@kit.ArkUI';

class MyFrameCallback extends FrameCallback {
  private tag: string;

  constructor(tag: string) {
    super();
    this.tag = tag;
  }

  onFrame(frameTimeNanos: number) {
    console.info('MyFrameCallback ' + this.tag + ' ' + frameTimeNanos.toString());
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Button('Invoke postFrameCallback')
        .onClick(() => {
          this.getUIContext().postFrameCallback(new MyFrameCallback('normTask'));
        })
    }
  }
}
```

## px2fp

```TypeScript
px2fp(value: number): number
```

Converts a value in px units to a value in fp.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Examples**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().px2fp(50),
          centerY: this.getUIContext().px2fp(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

## px2lpx

```TypeScript
px2lpx(value: number): number
```

Converts a value in px units to a value in lpx.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Examples**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().px2lpx(50),
          centerY: this.getUIContext().px2lpx(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

## px2vp

```TypeScript
px2vp(value: number): number
```

Converts a value in px units to a value in vp.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Examples**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().px2vp(50),
          centerY: this.getUIContext().px2vp(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

## removeLocalInputEventMonitor

```TypeScript
removeLocalInputEventMonitor(monitor: InputEventMonitor): void
```

Removes a local input event monitor.

**Important Notes**:

- Only Monitor objects returned by addLocalInputEventMonitor can be removed.  
- Cannot unregister a monitor by manually constructing an object.  
- If an invalid object is passed, the system silently ignores it.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| monitor | [InputEventMonitor](../arkts-components/arkts-arkui-common-comp-inputeventmonitor-i.md) | Yes | Monitor identifier object (returned by addLocalInputEventMonitor). |

**Examples**

```TypeScript
@Entry
@Component
struct RemoveMonitorSample {
  private uiContext: UIContext | undefined = undefined;
  private monitor: InputEventMonitor | null = null;
  aboutToAppear() {
    this.uiContext = this.getUIContext();
    this.monitor = this.uiContext.addLocalInputEventMonitor(
      InputEventSubTypeMask.LEFT_MOUSE_DOWN,
      (wrapper: RawInputEventWrapper) => {
        return { action: InputEventInterceptAction.CONTINUE };
      }
    );
  }
  aboutToDisappear() {
    // Remove the listener when destroying the component.
    if (this.monitor && this.uiContext) {
      this.uiContext.removeLocalInputEventMonitor(this.monitor);
    }
  }
  build() {
    Column() {
      Button('Remove Monitor')
        .onClick(() => {
          if (this.monitor && this.uiContext) {
            this.uiContext.removeLocalInputEventMonitor(this.monitor);
            this.monitor = null;
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## requireDynamicSyncScene

```TypeScript
requireDynamicSyncScene(id: string): Array<DynamicSyncScene>
```

Require DynamicSyncScene by id.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | The id of DynamicSyncScene. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[DynamicSyncScene](arkts-arkui-arkui-uicontext-dynamicsyncscene-c.md)&gt; | The instance of SwiperDynamicSyncScene. |

**Examples**

```TypeScript
import { SwiperDynamicSyncSceneType, SwiperDynamicSyncScene } from '@kit.ArkUI';

@Entry
@Component
struct Frame {
  @State animationFrameRateRange: ExpectedFrameRateRange = { min: 0, max: 120, expected: 90 };
  @State gestureFrameRateRange: ExpectedFrameRateRange = { min: 0, max: 120, expected: 30 };
  private scenes: SwiperDynamicSyncScene[] = [];

  build() {
    Column() {
      Text("Animation "+ JSON.stringify(this.animationFrameRateRange))
      Text ("Gesture: " + JSON.stringify (this.gestureFrameRateRange))
      Row() {
        Swiper() {
          Text("one")
          Text("two")
          Text("three")
        }
        .width('100%')
        .height('300vp')
        .id("dynamicSwiper")
        .backgroundColor(Color.Blue)
        .autoPlay(true)
        .onAppear(() => {
          this.scenes = this.getUIContext().requireDynamicSyncScene("dynamicSwiper") as SwiperDynamicSyncScene[];
        })
      }

      Button("set frame")
        .onClick(() => {
          this.scenes.forEach((scenes: SwiperDynamicSyncScene) => {

            if (scenes.type == SwiperDynamicSyncSceneType.ANIMATION) {
              scenes.setFrameRateRange(this.animationFrameRateRange);
            }

            if (scenes.type == SwiperDynamicSyncSceneType.GESTURE) {
              scenes.setFrameRateRange(this.gestureFrameRateRange);
            }
          });
        })
    }
  }
}
```

## resolveUIContext

```TypeScript
static resolveUIContext(): ResolvedUIContext
```

Obtains a UIContext instance along with its resolution strategy using a predefined priority order.

> **NOTE:** 
> 
> This API resolves and returns a UIContext instance together with the strategy used to determine it,
> 
> based on the following priority rules (in order):
> 
> 1. UIContext in the current calling scope.
> 
> 2. If only one UI instance exists, its UIContext is returned.
> 
> 3. If a UI instance has switched to the focused state, and the most recently focused UI instance has not been destroyed, the UIContext of that most recently focused instance is returned.
> 
> 4. If a UI instance has switched to the foreground state, and the most recently foreground UI instance has not been destroyed, the UIContext of that most recently foreground instance is returned.
> 
> 5. If multiple UI instances exist, the UIContext with the largest unique instance ID is returned.
> 
> 6. If none of the above conditions are met, an invalid UIContext instance is returned.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ResolvedUIContext](arkts-arkui-arkui-uicontext-resolveduicontext-c.md) | UIContext instance along with its resolution strategy. |

**Examples**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('click').onClick(() => {
        let resolvedUIContext = UIContext.resolveUIContext();
        hilog.info(0x00, 'testTag', `UIContext id: ${resolvedUIContext.getId()}, strategy: ${resolvedUIContext.strategy}`);
      })
    }
    .width(UIContext.resolveUIContext().px2vp(100))
    .height('100%')
  }
}
```

## runScopedTask

```TypeScript
runScopedTask(callback: () => void): void
```

Run custom functions inside the UIContext scope.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | () =&gt; void | Yes | The function called through UIContext. |

**Examples**

```TypeScript
@Entry
@Component
struct Index {
  private selectedDate: Date = new Date('2025-10-01');

  build() {
    Button('Show CalendarPicker Dialog')
      .onClick(() => {
        const uiContext = this.getUIContext();
        uiContext.runScopedTask(() => {
          CalendarPickerDialog.show({
            selected: this.selectedDate
          });
        });
      });
  }
}
```

## setCustomKeyboardContinueFeature

```TypeScript
setCustomKeyboardContinueFeature(feature: CustomKeyboardContinueFeature): void
```

Set custom keyboard continue feature.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| feature | [CustomKeyboardContinueFeature](arkts-arkui-arkui-uicontext-customkeyboardcontinuefeature-e.md) | Yes | The custom keyboard continue feature. |

**Examples**

```TypeScript
// xxx.ets
import { CustomKeyboardContinueFeature } from '@ohos.arkui.UIContext';

@Entry
@Component
struct Index {
  controller: TextInputController = new TextInputController();
  controller2: TextInputController = new TextInputController();
  @State inputValue: string = '';
  @State inputValue2: string = '';
  @State supportAvoidance: boolean = true;
  @State isValue: CustomKeyboardContinueFeature = CustomKeyboardContinueFeature.DISABLED;
  @State str: string = 'No';

  // Customize a keyboard.
  @Builder
  CustomKeyboardBuilder() {
    Column() {
      Row() {
        Button('x').onClick(() => {
          // Disable the custom keyboard.
          this.controller.stopEditing();
        }).margin(10)
        Button('delete').onClick(() => {
          this.inputValue = this.inputValue.slice(0, -1);
        }).margin(10)
      }

      Grid() {
        ForEach([1, 2, 3, 4, 5, 6, 7, 8, 9, '*', 0, '#'], (item: number | string) => {
          GridItem() {
            Button(item + '')
              .width(110).onClick(() => {
              this.inputValue += item;
            })
          }
        })
      }.maxCount(3).columnsGap(10).rowsGap(10).padding(5)
    }.backgroundColor('rgb(213, 213, 213)').height(300)
  }

  // Customize a keyboard.
  @Builder
  CustomKeyboardBuilder2() {
    Column() {
      Row() {
        Button('x').onClick(() => {
          // Disable the custom keyboard.
          this.controller2.stopEditing();
        }).margin(10)
        Button('delete').onClick(() => {
          this.inputValue2 = this.inputValue2.slice(0, -1);
        }).margin(10)
      }

      Grid() {
        ForEach([1, 2, 3, 4, 5, 6, 7, 8, 9, '*', 0, '#'], (item: number | string) => {
          GridItem() {
            Button(item + '')
              .width(110).onClick(() => {
              this.inputValue2 += item;
            })
          }
        })
      }.maxCount(3).columnsGap(10).rowsGap(10).padding(5)
    }.backgroundColor('rgb(227, 248, 249)').height(150)
  }

  build() {
    Scroll() {
      Column() {
        Button ('Persist Input:' this.str).onClick(() => {
          if (this.isValue == CustomKeyboardContinueFeature.ENABLED) {
            this.isValue = CustomKeyboardContinueFeature.DISABLED
            this.str = 'No'
          } else {
            this.isValue = CustomKeyboardContinueFeature.ENABLED
            this.str = 'Yes'
          }
          this.getUIContext().setCustomKeyboardContinueFeature(this.isValue);
        }).fontSize(20).width('80%').key('button')

        TextInput({
          placeholder: 'TextInput1 bind CustomKeyboardBuilder',
          controller: this.controller,
          text: this.inputValue
        }) // Bind a custom keyboard.
          .customKeyboard(this.CustomKeyboardBuilder(), { supportAvoidance: this.supportAvoidance })
          .margin(10)
          .border({ width: 1 })
        TextInput({
          placeholder: 'TextInput2 bind CustomKeyboardBuilder2',
          controller: this.controller2,
          text: this.inputValue2
        }) // Bind a custom keyboard.
          .customKeyboard(this.CustomKeyboardBuilder2(), { supportAvoidance: this.supportAvoidance })
          .margin(10)
          .border({ width: 1 })
      }
    }
  }
}
```

## setImageCacheCount

```TypeScript
setImageCacheCount(value: number): void
```

Set image cache capacity of decoded image count. if not set, the application will not cache any decoded image.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | capacity of decoded image count. |

**Examples**

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  onPageShow() {
    // Set the maximum number of decoded images that can be cached in the memory to 100.
    this.getUIContext().setImageCacheCount(100);
    console.info('Application onPageShow');
  }
  onDestroy() {
    console.info('Application onDestroy');
  }

  build() {
    Row(){
      Image('https://www.example.com/xxx.png') // Enter a specific online image URL.
        .width(200)
        .height(50)
    }.width('100%')
  }
}
```

## setImageRawDataCacheSize

```TypeScript
setImageRawDataCacheSize(value: number): void
```

Set image cache capacity of raw image data size in bytes before decode. if not set, the application will not cache any raw image data.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | capacity of raw image data size in bytes. |

**Examples**

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  onPageShow() {
    // Set the upper limit of the memory for caching image data before decoding to 100 MB. (100 x 1024 x 1024 B =104857600 B = 100 MB).
    this.getUIContext().setImageRawDataCacheSize(104857600); 
    console.info('Application onPageShow');
  }
  onDestroy() {
    console.info('Application onDestroy');
  }

  build() {
    Row(){
      Image('https://www.example.com/xxx.png') // Enter a specific online image URL.
        .width(200)
        .height(50)
    }.width('100%')
  }
}
```

## setKeyboardAvoidMode

```TypeScript
setKeyboardAvoidMode(value: KeyboardAvoidMode): void
```

Sets the avoidance mode for the virtual keyboard.

> **NOTE:** 
> 
> With **KeyboardAvoidMode.RESIZE**, the page is resized to prevent the virtual keyboard from obstructing the
> view. Regarding components on the page, those whose width and height are set in percentage are resized with the
> page, and those whose width and height are set to specific values are laid out according to their settings.
> With **KeyboardAvoidMode.RESIZE**, **expandSafeArea([SafeAreaType.KEYBOARD],[SafeAreaEdge.BOTTOM])** does not
> take effect.
> 
> With **KeyboardAvoidMode.NONE**, keyboard avoidance is disabled, and the page will be covered by the displayed
> keyboard.
> 
> **setKeyboardAvoidMode** only affects page layouts. It does not apply to popup components, including the
> following: **Dialog**, **Popup**, **Menu**, **BindSheet**, **BindContentCover**, **Toast**, **OverlayManager**.
> For details about the avoidance mode of popup components, see
> [CustomDialogControllerOptions](../../../reference/arkui-ts/ts-methods-custom-dialog-box.md).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [KeyboardAvoidMode](arkts-arkui-arkui-uicontext-keyboardavoidmode-e.md) | Yes | Avoidance mode of the virtual keyboard.<br>Default value: **KeyboardAvoidMode.OFFSET**. |

**Examples**

See [Example 4: Setting the Keyboard Avoidance Mode to Resize](../arkui-ts/ts-universal-attributes-expand-safe-area.md#example-4-setting-the-keyboard-avoidance-mode-to-resize), [Example 5: Setting Keyboard Avoidance Mode to Offset](../arkui-ts/ts-universal-attributes-expand-safe-area.md#example-5-setting-keyboard-avoidance-mode-to-offset), and [Example 6: Switching Avoidance Modes](../arkui-ts/ts-universal-attributes-expand-safe-area.md#example-6-switching-avoidance-modes).

```TypeScript
// EntryAbility.ets
import { KeyboardAvoidMode, UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility{
  onWindowStageCreate(windowStage: window.WindowStage) {

      windowStage.loadContent('pages/Index', (err, data) => {
        let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
        uiContext.setKeyboardAvoidMode(KeyboardAvoidMode.RESIZE);
      });
    }
}
```

## setOverlayManagerOptions

```TypeScript
setOverlayManagerOptions(options: OverlayManagerOptions): boolean
```

Init OverlayManager.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [OverlayManagerOptions](arkts-arkui-arkui-uicontext-overlaymanageroptions-i.md) | Yes | Options. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if it is called first and before getting an OverlayManager instance; returns false otherwise. |

**Examples**

See the example for [OverlayManager](arkts-apis-uicontext-overlaymanager.md).

## setPixelRoundMode

```TypeScript
setPixelRoundMode(mode: PixelRoundMode): void
```

Sets the pixel rounding mode of the current page.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [PixelRoundMode](arkts-arkui-pixelroundmode-e.md) | Yes | Pixel rounding mode.<br>Default value:**PixelRoundMode.PIXEL_ROUND_ON_LAYOUT_FINISH**. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {

    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      uiContext.setPixelRoundMode(PixelRoundMode.PIXEL_ROUND_ON_LAYOUT_FINISH);
    });
  }
}
```

## setResourceManagerCacheMaxCountForHSP

```TypeScript
static setResourceManagerCacheMaxCountForHSP(count: number): void
```

Set the upper limit for the cache count of HSP resource management objects.

If the upper limit of the cache is set too high, there is a risk of excessive memory overhead. It is recommended to configure it according to actual needs.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | The cache limit of resource manager for HSP, must be non negative integers. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100101](../errorcode-uicontext.md#100101-invalid-negative-parameter-value) | The parameter is less than 0. |
| [100102](../errorcode-uicontext.md#100102-incorrect-parameter-type) | The parameter value cannot be a floating point number. |
| [100103](../errorcode-uicontext.md#100103-invalid-thread-context) | The function cannot be called from a non main thread. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { UIContext, window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', err.message);
        return;
      }
      UIContext.setResourceManagerCacheMaxCountForHSP(5);
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```

## setTextSelectionClearPolicy

```TypeScript
setTextSelectionClearPolicy(policy: TextSelectionClearPolicy): void
```

Sets the text selection clear policy for text component. Default policy: **TextSelectionClearPolicy.KEEP_SELECTED_TEXT_ON_EXTERNAL_TOUCH**

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policy | [TextSelectionClearPolicy](arkts-arkui-arkui-uicontext-textselectionclearpolicy-e.md) | Yes | The text selection clear policy. |

**Examples**

## showActionSheet

```TypeScript
showActionSheet(value: ActionSheetOptions): void
```

Shows an action sheet in the given settings.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md) | Yes | Parameters of the action sheet. |

**Examples**

```TypeScript
@Entry
@Component
struct Index {
  uiContext: UIContext = this.getUIContext()

  build() {
    Column() {
      Button('showActionSheet')
        .onClick(() => {
          this.uiContext.showActionSheet({
            title: 'ActionSheet title',
            message: 'message',
            autoCancel: true,
            confirm: {
              value: 'Confirm button',
              action: () => {
                console.info('Get ActionSheet handled');
              }
            },
            cancel: () => {
              console.info('ActionSheet canceled');
            },
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -10 },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          });
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

## showAlertDialog

```TypeScript
showAlertDialog(options: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions): void
```

Shows an alert dialog box.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AlertDialogParamWithConfirm](arkts-arkui-alertdialogparamwithconfirm-i.md) &#124; [AlertDialogParamWithButtons](arkts-arkui-alertdialogparamwithbuttons-i.md) &#124; [AlertDialogParamWithOptions](arkts-arkui-alertdialogparamwithoptions-i.md) | Yes | Shows an AlertDialog component in the given settings. |

**Examples**

```TypeScript
@Entry
@Component
struct Index {
  uiContext: UIContext = this.getUIContext()

  build() {
    Column() {
      Button('showAlertDialog')
        .onClick(() => {
          this.uiContext.showAlertDialog(
            {
              title: 'title',
              message: 'text',
              autoCancel: true,
              alignment: DialogAlignment.Bottom,
              offset: { dx: 0, dy: -20 },
              gridCount: 3,
              confirm: {
                value: 'button',
                action: () => {
                  console.info('Button-clicking callback');
                }
              },
              cancel: () => {
                console.info('Closed callbacks');
              }
            }
          );
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

## showDatePickerDialog

```TypeScript
showDatePickerDialog(options: DatePickerDialogOptions): void
```

datePickerDialog display.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DatePickerDialogOptions](../arkts-components/arkts-arkui-datepicker-comp-datepickerdialogoptions-i.md) | Yes | Options. |

**Examples**

```TypeScript
// xxx.ets
@Entry
@Component
struct DatePickerDialogExample {
  selectedDate: Date = new Date("2010-1-1");

  build() {
    Row(){
      Column() {
        Button("DatePickerDialog")
          .margin(20)
          .onClick(() => {
            this.getUIContext().showDatePickerDialog({
              start: new Date("2000-1-1"),
              end: new Date("2100-12-31"),
              selected: this.selectedDate,
              showTime: true,
              useMilitaryTime: false,
              dateTimeOptions: { hour: "numeric", minute: "2-digit" },
              onDateAccept: (value: Date) => {
                // Use the setFullYear method to set the date when the OK button is touched. In this way, when the date picker dialog box is displayed again, the selected date is the date last confirmed.
                this.selectedDate = value;
                console.info("DatePickerDialog:onDateAccept()" + value.toString());
              },
              onCancel: () => {
                console.info("DatePickerDialog:onCancel()");
              },
              onDateChange: (value: Date) => {
                console.info("DatePickerDialog:onDateChange()" + value.toString());
              },
              onDidAppear: () => {
                console.info("DatePickerDialog:onDidAppear()");
              },
              onDidDisappear: () => {
                console.info("DatePickerDialog:onDidDisappear()");
              },
              onWillAppear: () => {
                console.info("DatePickerDialog:onWillAppear()");
              },
              onWillDisappear: () => {
                console.info("DatePickerDialog:onWillDisappear()");
              }
            })
          })
      }.width('100%')
    }.height('100%')
  }
}
```

## showTextPickerDialog

```TypeScript
showTextPickerDialog(options: TextPickerDialogOptions): void
```

textPickerDialog display.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TextPickerDialogOptions](../arkts-components/arkts-arkui-textpicker-comp-textpickerdialogoptions-i.md) | Yes | Options. |

**Examples**

```TypeScript
// xxx.ets

class SelectedValue{
  select: number = 2;
  set(val: number){
    this.select = val;
  }
}
class SelectedArray{
  select: number[] = [];
  set(val: number[]){
    this.select = val;
  }
}
@Entry
@Component
struct TextPickerDialogExample {
  @State selectTime: Date = new Date('2023-12-25T08:30:00');
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4', 'banana5'];
  private select: number  = 0;
  build() {
    Row(){
      Column() {
        Button('showTextPickerDialog')
          .margin(30)
          .onClick(() => {
            this.getUIContext().showTextPickerDialog({
              range: this.fruits,
              selected: this.select,
              onAccept: (value: TextPickerResult) => {
                // Set select to the index of the item selected when the OK button is touched. In this way, when the text picker dialog box is displayed again, the selected item is the one last confirmed.
                let selectedVal = new SelectedValue();
                let selectedArr = new SelectedArray();
                if (value.index){
                  value.index instanceof Array?selectedArr.set(value.index) : selectedVal.set(value.index);
                }
                console.info("TextPickerDialog:onAccept()" + JSON.stringify(value));
              },
              onCancel: () => {
                console.info("TextPickerDialog:onCancel()");
              },
              onChange: (value: TextPickerResult) => {
                console.info("TextPickerDialog:onChange()" + JSON.stringify(value));
              }
            });
          })
      }.width('100%').margin({ top: 5 })
    }.height('100%')
  }
}
```

<a id="showtextpickerdialog-1"></a>

## showTextPickerDialog

```TypeScript
showTextPickerDialog(style: TextPickerDialogOptions | TextPickerDialogOptionsExt): void
```

textPickerDialog display.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [TextPickerDialogOptions](../arkts-components/arkts-arkui-textpicker-comp-textpickerdialogoptions-i.md) &#124; [TextPickerDialogOptionsExt](../arkts-components/arkts-arkui-textpicker-comp-textpickerdialogoptionsext-i.md) | Yes | Dialog style. |

**Examples**

See [showTextPickerDialog](#showtextpickerdialog)

## showTimePickerDialog

```TypeScript
showTimePickerDialog(options: TimePickerDialogOptions): void
```

timePickerDialog display.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TimePickerDialogOptions](../arkts-components/arkts-arkui-timepicker-comp-timepickerdialogoptions-i.md) | Yes | Options. |

**Examples**

```TypeScript
// xxx.ets

class SelectTime{
  selectTime: Date = new Date('2020-12-25T08:30:00');
  hours(h:number,m:number){
    this.selectTime.setHours(h, m);
  }
}

@Entry
@Component
struct TimePickerDialogExample {
  @State selectTime: Date = new Date('2023-12-25T08:30:00');

  build() {
    Column() {
      Button('showTimePickerDialog')
        .margin(30)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            selected: this.selectTime,
            onAccept: (value: TimePickerResult) => {
              // Set selectTime to the time when the OK button is clicked. In this way, when the dialog box is displayed again, the selected time is the time when the operation was confirmed last time.
              let time = new SelectTime();
              if(value.hour && value.minute){
                time.hours(value.hour, value.minute);
              }
              console.info("TimePickerDialog:onAccept()" + JSON.stringify(value));
            },
            onCancel: () => {
              console.info("TimePickerDialog:onCancel()");
            },
            onChange: (value: TimePickerResult) => {
              console.info("TimePickerDialog:onChange()" + JSON.stringify(value));
            }
          });
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

## unbindTabsFromNestedScrollable

```TypeScript
unbindTabsFromNestedScrollable(tabsController: TabsController, parentScroller: Scroller, childScroller: Scroller): void
```

Unbind tabs from nested scrollable container components.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabs-comp-tabscontroller-c.md) | Yes | The controller of the tabs. |
| parentScroller | [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) | Yes | The controller of the parent scrollable container component. |
| childScroller | [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) | Yes | The controller of the child scrollable container component. |

**Examples**

See the example for [bindTabsToScrollable](#bindtabstoscrollable).

## unbindTabsFromScrollable

```TypeScript
unbindTabsFromScrollable(tabsController: TabsController, scroller: Scroller): void
```

Unbind tabs from scrollable container component.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabs-comp-tabscontroller-c.md) | Yes | The controller of the tabs. |
| scroller | [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) | Yes | The controller of the scrollable container component. |

**Examples**

See the example for [bindTabsToScrollable](#bindtabstoscrollable).

## updateBindSheet

```TypeScript
updateBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>, sheetOptions: SheetOptions, partialUpdate?: boolean): Promise<void>
```

Updates the style of the sheet corresponding to the provided **bindSheetContent**. This API uses a promise to return the result.

> **NOTE:** 
> 
> **SheetOptions.UIContext**, **SheetOptions.mode**, and callback functions cannot be updated.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bindSheetContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | Yes | Content to display on the sheet. |
| sheetOptions | [SheetOptions](../arkts-components/arkts-arkui-common-comp-sheetoptions-i.md) | Yes | Style of the sheet.<br>**NOTE:** <br>**SheetOptions.UIContext** and **SheetOptions.mode** cannot be updated. |
| partialUpdate | boolean | No | Whether to update the sheet in incremental mode.<br>Default value: **false**<br> **NOTE:** <br>1. **true**: incremental update, where the specified properties in **SheetOptions** are updated, and other properties stay at their current value.<br>2. **false**: full update, where all properties except those specified in **SheetOptions** are restored to default values. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [120001](../errorcode-bindSheet.md#120001-incorrect-bindsheetcontent) | The bindSheetContent is incorrect. |
| [120003](../errorcode-bindSheet.md#120003-no-matching-modal-found) | The bindSheetContent cannot be found. |

**Examples**

```TypeScript
import { FrameNode, ComponentContent } from "@kit.ArkUI";
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

let contentNode: ComponentContent<Params>;
let gUIContext: UIContext;

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
    Button('Update BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.updateBindSheet(contentNode, {
          backgroundColor: Color.Pink,
        }, true)
          .then(() => {
            console.info('updateBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('updateBindSheet error: ' + err.code + ' ' + err.message);
          })
      })

    Button('Close BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.closeBindSheet(contentNode)
          .then(() => {
            console.info('closeBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('closeBindSheet error: ' + err.code + ' ' + err.message);
          })
      })
  }
}

@Entry
@Component
struct UIContextBindSheet {
  @State message: string = 'BindSheet';

  aboutToAppear() {
    gUIContext = this.getUIContext();
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    RelativeContainer() {
      Column() {
        Button('Open BindSheet')
          .fontSize(20)
          .onClick(() => {
            let uiContext = this.getUIContext();
            let uniqueId = this.getUniqueId();
            let frameNode: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
            let targetId = frameNode?.getFirstChild()?.getUniqueId();
            uiContext.openBindSheet(contentNode, {
              height: SheetSize.MEDIUM,
              backgroundColor: Color.Green,
              title: { title: "Title", subtitle: "subtitle" }
            }, targetId)
              .then(() => {
                console.info('openBindSheet success');
              })
              .catch((err: BusinessError) => {
                console.error('openBindSheet error: ' + err.code + ' ' + err.message);
              })
          })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

## vp2px

```TypeScript
vp2px(value: number): number
```

Converts a value in vp units to a value in px.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| number |  |

**Examples**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().vp2px(50),
          centerY: this.getUIContext().vp2px(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```
