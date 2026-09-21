# UIObserver

```TypeScript
export class UIObserver
```

Provides APIs for listening for UI component behavior changes.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 11.
> 
> - In the following API examples, you must first use [getUIObserver()](arkts-arkui-arkui-uicontext-uicontext-c.md#getuiobserver) in
> **UIContext** to obtain a **UIObserver** instance, and then call the APIs using the obtained instance.
> 
> - UIObserver can only listen for relevant information within the current process and does not support obtaining information in cross-process scenarios<!--Del--> such as UIExtensionComponent<!-- > DelEnd-->.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## addGlobalGestureListener

```TypeScript
addGlobalGestureListener(type: GestureListenerType,
      option: GestureObserverConfigs, callback: GestureListenerCallback): void
```

Registers a callback to listen for gesture triggering information.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [GestureListenerType](arkts-arkui-arkui-uicontext-gesturelistenertype-e.md) | Yes | Type of gesture to listen for. |
| option | [GestureObserverConfigs](arkts-arkui-arkui-uicontext-gestureobserverconfigs-i.md) | Yes | Configuration options for binding the global listener. |
| callback | [GestureListenerCallback](arkts-arkui-gesturelistenercallback-t.md) | Yes | Callback triggered when the gesture state updates. |

**Examples**

This example uses global gesture listeners to monitor the trigger status of three independent areas (Tap, Pan, and LongPress) in real time, records the trigger count and last operation information for each gesture, and automatically manages the registration and unregistration of listeners during the component's lifecycle.

```TypeScript
// Index.ets
// Example usage of uiObserver.addGlobalGestureListener(type, option, callback)
// uiObserver.removeGlobalGestureListener(type, callback)

import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureListenerCallback } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State tapCount: number = 0;
  @State panCount: number = 0;
  @State longPressCount: number = 0;
  @State lastAction: string = 'None';
  @State lastArea: string = 'None';

  // Store listener callback references.
  private tapCallback?: GestureListenerCallback;
  private panCallback?: GestureListenerCallback;
  private longPressCallback?: GestureListenerCallback;

  // Enable global listeners.
  aboutToAppear() {
    this.addGlobalListeners();
  }
  // Disable global listeners.
  aboutToDisappear() {
    this.removeGlobalListeners();
  }

  private addGlobalListeners() {
    const observer = this.getUIContext().getUIObserver();

    // Tap listener.
    this.tapCallback = (info: GestureTriggerInfo) => {
      if (info.event?.target?.id === 'tap-area') {
        this.tapCount++;
        this.lastAction = 'Tap';
        this.lastArea = 'Tap area';
      }
    };
    observer.addGlobalGestureListener(
      GestureListenerType.TAP,
      { actionPhases: [GestureActionPhase.WILL_START, GestureActionPhase.WILL_END] },
      this.tapCallback
    );

    // Pan listener.
    this.panCallback = (info: GestureTriggerInfo) => {
      if (info.event?.target?.id === 'pan-area') {
        this.panCount++;
        this.lastAction = 'Pan';
        this.lastArea = 'Pan area';
      }
    };
    observer.addGlobalGestureListener(
      GestureListenerType.PAN,
      {
        actionPhases: [GestureActionPhase.WILL_START, GestureActionPhase.WILL_END]
      },
      this.panCallback
    );

    // LongPress listener.
    this.longPressCallback = (info: GestureTriggerInfo) => {
      if (info.event?.target?.id === 'longpress-area') {
        this.longPressCount++;
        this.lastAction = 'Long press';
        this.lastArea = 'Long press area';
      }
    };
    observer.addGlobalGestureListener(
      GestureListenerType.LONG_PRESS,
      {
        actionPhases: [GestureActionPhase.WILL_START, GestureActionPhase.WILL_END]
      },
      this.longPressCallback
    );
  }

  private removeGlobalListeners() {
    const observer = this.getUIContext().getUIObserver();
// 0, 2, and 1 indicate the tap, pan, and long-press gesture types, respectively, which are used to remove the corresponding global listeners.
    if (this.tapCallback) {
      observer.removeGlobalGestureListener(GestureListenerType.TAP, this.tapCallback);
    }
    if (this.panCallback) {
      observer.removeGlobalGestureListener(GestureListenerType.PAN, this.panCallback);
    }
    if (this.longPressCallback) {
      observer.removeGlobalGestureListener(GestureListenerType.LONG_PRESS, this.longPressCallback);
    }
  }

  build() {
    Column() {
      // Gesture data statistics panel.
      Row({ space: 30 }) {
        Column() {
          Text('Tap count:').fontSize(16)
          Text(`${this.tapCount}`).fontSize(24).fontColor('#FF6B81')
        }
        Column() {
          Text('Pan count:').fontSize(16)
          Text(`${this.panCount}`).fontSize(24).fontColor('#7BED9F')
        }
        Column() {
          Text('Long-press count:').fontSize(16)
          Text(`${this.longPressCount}`).fontSize(24).fontColor('#70A1FF')
        }
      }
      .margin(10)

      Text(`Last action: ${this.lastAction} (${this.lastArea})`)
        .fontSize(18)
        .margin(10)

      // Gesture areas.
      Row() {
        Text('Tap area').fontSize(18)
      }
      .id('tap-area')
      .width('90%')
      .height(120)
      .margin(10)
      .border({ width: 2, color: '#FF6B81' })
      .justifyContent(FlexAlign.Center)
      .gesture(TapGesture().onAction((event: GestureEvent) => {
        // Implementation details.
      }))

      Row() {
        Text('Pan area').fontSize(18)
      }
      .id('pan-area')
      .width('90%')
      .height(120)
      .margin(10)
      .border({ width: 2, color: '#7BED9F' })
      .justifyContent(FlexAlign.Center)
      .gesture(
        PanGesture()
          .onActionStart((event: GestureEvent) => {
            // Implementation details.
          })
          .onActionEnd((event: GestureEvent) => {
            // Implementation details.
          })
      )

      Row() {
        Text('LongPress area').fontSize(18)
      }
      .id('longpress-area')
      .width('90%')
      .height(120)
      .margin(10)
      .border({ width: 2, color: '#70A1FF' })
      .justifyContent(FlexAlign.Center)
      .gesture(
        LongPressGesture()
          .onAction((event: GestureEvent) => {
            // Implementation details.
          })
          .onActionEnd((event: GestureEvent) => {
            // Implementation details.
          })
      )
    }
    .width('100%')
    .height('100%')
  }
}
```

## off('navDestinationUpdate')

```TypeScript
off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | Yes | The type of event to remove the listener for. Must be 'navDestinationUpdate'. |
| options | { navigationId: ResourceStr } | Yes | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type and navigation ID will be removed. |

**Examples**

See the example for [on('navDestinationUpdate')](#onnavdestinationupdate).

## off('navDestinationUpdate')

```TypeScript
off(type: 'navDestinationUpdate', callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | Yes | The type of event to remove the listener for. Must be 'navDestinationUpdate'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for [on('navDestinationUpdate')](#onnavdestinationupdate).

## off('navDestinationUpdateByUniqueId')

```TypeScript
off(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationUpdateByUniqueId' | Yes | The type of event to remove the listener for. Must be 'navDestinationUpdateByUniqueId'. |
| navigationUniqueId | number | Yes | The uniqueId of the navigation. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for [on('navDestinationUpdateByUniqueId')](#onnavdestinationupdatebyuniqueid).

## off('scrollEvent')

```TypeScript
off(type: 'scrollEvent', options: observer.ObserverOptions, callback?: Callback<observer.ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'scrollEvent' | Yes | The type of event to remove the listener for. Must be 'scrollEvent'. |
| options | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type and scroll ID will be removed. |

**Examples**

See the example for [on('scrollEvent')](#onscrollevent).

## off('scrollEvent')

```TypeScript
off(type: 'scrollEvent', callback?: Callback<observer.ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'scrollEvent' | Yes | The type of event to remove the listener for. Must be 'scrollEvent'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for [on('scrollEvent')](#onscrollevent).

## off('routerPageUpdate')

```TypeScript
off(type: 'routerPageUpdate', callback?: Callback<observer.RouterPageInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | Yes | The type of event to remove the listener for. Must be 'routerPageUpdate'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.RouterPageInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for [on('routerPageUpdate')](#onrouterpageupdate).

## off('densityUpdate')

```TypeScript
off(type: 'densityUpdate', callback?: Callback<observer.DensityInfo>): void
```

Unregisters the listener for screen pixel density changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'densityUpdate' | Yes | Event type. The value **'densityUpdate'** indicates the pixel density changes of the screen. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md)&gt; | No | Target listener to unregister. If no parameter is provided, all screen pixel density change listeners for the current [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) are removed. |

**Examples**

See the example for [on('densityUpdate')](#ondensityupdate).

## off('willDraw')

```TypeScript
off(type: 'willDraw', callback?: Callback<void>): void
```

Unregisters the listener for drawing instruction dispatch in each frame.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'willDraw' | Yes | Event event. The value **'willDraw'** indicates whether drawing is about to occur. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Target listener to unregister. If no parameter is provided, all drawing instruction dispatch listeners are unregistered. |

**Examples**

See the example for [on('willDraw')](#onwilldraw).

## off('didLayout')

```TypeScript
off(type: 'didLayout', callback?: Callback<void>): void
```

Unregisters the listener for layout completion status in each frame.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'didLayout' | Yes | Event type. The value **'didLayout'** indicates whether the layout has been completed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Target listener to unregister. If no parameter is provided, all layout completion listeners are unregistered. |

**Examples**

See the example for [on('didLayout')](#ondidlayout).

## off('navDestinationSwitch')

```TypeScript
off(
    type: 'navDestinationSwitch',
    callback?: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | Yes | The type of event to remove the listener for. Must be 'navDestinationSwitch'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for [on('navDestinationSwitch')](#onnavdestinationswitch).

## off('navDestinationSwitch')

```TypeScript
off(
    type: 'navDestinationSwitch',
    observerOptions: observer.NavDestinationSwitchObserverOptions,
    callback?: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | Yes | The type of event to remove the listener for. Must be 'navDestinationSwitch'. |
| observerOptions | [observer.NavDestinationSwitchObserverOptions](arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | Yes | Options. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for [on('navDestinationSwitch')](#onnavdestinationswitch).

## off('willClick')

```TypeScript
off(type: 'willClick', callback?: ClickEventListenerCallback): void
```

Removes a callback function to be called before clickEvent is called.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'willClick' | Yes | The type of event to remove the listener for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for [on('willClick')](#onwillclick).

## off('didClick')

```TypeScript
off(type: 'didClick', callback?: ClickEventListenerCallback): void
```

Removes a callback function to be called after clickEvent is called.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'didClick' | Yes | The type of event to remove the listener for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for [on('willClick')](#onwillclick).

## off('willClick')

```TypeScript
off(type: 'willClick', callback?: GestureEventListenerCallback): void
```

Removes a callback function to be called before tapGesture is called.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'willClick' | Yes | The type of event to remove the listener for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for [on('willClick')](#onwillclick).

## off('didClick')

```TypeScript
off(type: 'didClick', callback?: GestureEventListenerCallback): void
```

Removes a callback function to be called after tapGesture is called.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'didClick' | Yes | The type of event to remove the listener for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for [on('willClick')](#onwillclick).

## off('beforePanStart')

```TypeScript
off(type: 'beforePanStart', callback?: PanListenerCallback): void
```

Unregisters the listener for pan gesture [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) pre-execution events, canceling callbacks registered via [on('beforePanStart')](#onbeforepanstart).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'beforePanStart' | Yes | Event type. The value is fixed at **'beforePanStart'**, indicating command dispatch before the execution of the pan gesture [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) event. |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | No | Target listener to unregister. If no parameter is provided, all callback listeners for command dispatch before the execution of the pan gesture [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) event will be removed. |

**Examples**

See the example for [on('beforePanStart')](#onbeforepanstart).

## off('beforePanEnd')

```TypeScript
off(type: 'beforePanEnd', callback?: PanListenerCallback): void
```

Unregisters the listener for pan gesture [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) pre-execution events, canceling callbacks registered via [on('beforePanEnd')](#onbeforepanend).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'beforePanEnd' | Yes | Event type. The value is fixed at **'beforePanEnd'**, indicating command dispatch before the execution of the pan gesture [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) event. |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | No | Target listener to unregister. If no parameter is provided, all callback listeners for command dispatch before the execution of the pan gesture [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) event will be removed. |

**Examples**

See the example for [on('beforePanStart')](#onbeforepanstart).

## off('afterPanStart')

```TypeScript
off(type: 'afterPanStart', callback?: PanListenerCallback): void
```

Unregisters the listener for pan gesture [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) post-execution events, canceling callbacks registered via [on('afterPanStart')](#onafterpanstart).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'afterPanStart' | Yes | Event type. The value is fixed at **'afterPanStart'**, indicating command dispatch after the execution of the pan gesture [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) event. |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | No | Target listener to unregister. If no parameter is provided, all callback listeners for command dispatch after the execution of the pan gesture [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) event will be removed. |

**Examples**

See the example for [on('beforePanStart')](#onbeforepanstart).

## off('afterPanEnd')

```TypeScript
off(type: 'afterPanEnd', callback?: PanListenerCallback): void
```

Unregisters the listener for pan gesture [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) post-execution events, canceling callbacks registered via [on('afterPanEnd')](#onafterpanend).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'afterPanEnd' | Yes | Event type. The value is fixed at **'afterPanEnd'**, indicating command dispatch after the execution of the pan gesture [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) event. |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | No | Target listener to unregister. If no parameter is provided, all callback listeners for command dispatch after the execution of the pan gesture [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) event will be removed. |

**Examples**

See the example for [on('beforePanStart')](#onbeforepanstart).

## off('tabContentUpdate')

```TypeScript
off(type: 'tabContentUpdate', options: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | Yes | The type of event to remove the listener for. Must be 'tabContentUpdate'. |
| options | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type and Tabs ID will be removed. |

**Examples**

See the example for [on('tabContentUpdate')](#ontabcontentupdate).

## off('tabContentUpdate')

```TypeScript
off(type: 'tabContentUpdate', callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | Yes | The type of event to remove the listener for. Must be 'tabContentUpdate'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type and Tabs ID will be removed. |

**Examples**

See the example for [on('tabContentUpdate')](#ontabcontentupdate).

## off('tabChange')

```TypeScript
off(type: 'tabChange', config: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'tabChange' | Yes | The type of event to remove the listener for. Must be 'tabChange'. |
| config | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | The config object. Includes the observed component id. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type and Tabs ID will be removed. |

**Examples**

See the example for [on('tabChange')](#ontabchange).

## off('tabChange')

```TypeScript
off(type: 'tabChange', callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'tabChange' | Yes | The type of event to remove the listener for. Must be 'tabChange'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for [on('tabChange')](#ontabchange).

## off('windowSizeLayoutBreakpointChange')

```TypeScript
off(type: 'windowSizeLayoutBreakpointChange', callback?: Callback<observer.WindowSizeLayoutBreakpointInfo>): void
```

Unregisters previously registered window size layout breakpoint change listeners. If no callback is specified, all listeners for the current UI context are removed. This API uses an asynchronous callback to return the result.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowSizeLayoutBreakpointChange' | Yes | Event type. The value is fixed at **'windowSizeLayoutBreakpointChange'**, indicating window size layout breakpoint changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.WindowSizeLayoutBreakpointInfo](arkts-arkui-uiobserver-windowsizelayoutbreakpointinfo-c.md)&gt; | No | Target listener to unregister. If no parameter is provided, all window size layout breakpoint change listeners for the current [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) are removed. |

**Examples**

See the example for [on('windowSizeLayoutBreakpointChange')](#onwindowsizelayoutbreakpointchange).

## off('nodeRenderState')

```TypeScript
off(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback?: NodeRenderStateChangeCallback): void
```

Unregisters the callback for listening for node rendering state changes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'nodeRenderState' | Yes | Event type. The value is fixed at **'nodeRenderState'**. |
| nodeIdentity | [NodeIdentity](arkts-arkui-nodeidentity-t.md) | Yes | Node ID. |
| callback | [NodeRenderStateChangeCallback](arkts-arkui-noderenderstatechangecallback-t.md) | No | Target listener to unregister. If no parameter is provided, all node rendering state change listeners are unregistered. |

**Examples**

See the example for [on('nodeRenderState')](#onnoderenderstate).

## off('textChange')

```TypeScript
off(type: 'textChange', callback?: Callback<observer.TextChangeEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'textChange' | Yes | The type of event to remove the listener for. Must be 'textChange'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

For details, see [on('textChange')](#ontextchange).

## off('textChange')

```TypeScript
off(type: 'textChange', identity: observer.ObserverOptions, callback?: Callback<observer.TextChangeEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'textChange' | Yes | The type of event to remove the listener for. Must be 'textChange'. |
| identity | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | Identity options. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

For details, see [on('textChange')](#ontextchange).

## offNavDestinationSizeChange

```TypeScript
offNavDestinationSizeChange(callback?: Callback<observer.NavDestinationInfo>): void
```

Removes the listener callback registered using the **onNavDestinationSizeChange** API. This API uses an asynchronous callback to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | No | Callback to be removed. If no parameter is passed, all callbacks are removed. |

**Examples**

See the example for the [onNavDestinationSizeChange](#onnavdestinationsizechange) API.

## offNavDestinationSizeChangeByUniqueId

```TypeScript
offNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with 'onNavDestinationSizeChangeByUniqueId()'.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| navigationUniqueId | number | Yes | The uniqueId of the Navigation to which NavDestination belongs. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**Examples**

See the example for the [onNavDestinationSizeChangeByUniqueId](#onnavdestinationsizechangebyuniqueid) API.

## offRouterPageSizeChange

```TypeScript
offRouterPageSizeChange(callback?: Callback<observer.RouterPageInfo>): void
```

Removes the listener callback registered using the **onRouterPageSizeChange** API. This API uses an asynchronous callback to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.RouterPageInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | No | Callback to be removed. If no parameter is passed, all callbacks are removed. |

**Examples**

See the example for the [onRouterPageSizeChange](#onrouterpagesizechange) API.

## offSwiperContentUpdate

```TypeScript
offSwiperContentUpdate(callback?: Callback<SwiperContentInfo>): void
```

Unregister the listener for content switching events of the **Swiper** component.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | No | Target listener to unregister. If no parameter is provided, all listeners for the **Swiper** component are unregistered. |

**Examples**

See the example for the [onSwiperContentUpdate](#onswipercontentupdate) API.

<a id="offswipercontentupdate-1"></a>

## offSwiperContentUpdate

```TypeScript
offSwiperContentUpdate(config: observer.ObserverOptions, callback?: Callback<SwiperContentInfo>): void
```

Unregister the listener for content switching events of a specific **Swiper** component identified by its ID.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | Information about the target **Swiper** component. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | No | Target listener to unregister. If no parameter is provided, all listeners for the **Swiper** component are unregistered. |

**Examples**

See the example for the [onSwiperContentUpdate](#onswipercontentupdate) API.

## on('navDestinationUpdate')

```TypeScript
on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback<observer.NavDestinationInfo>): void
```

Subscribes to status changes of this **NavDestination** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | Yes | Event type. The value is fixed at **'navDestinationUpdate'**, which indicates the state change event<br>of the **NavDestination** component. |
| options | { navigationId: ResourceStr } | Yes | ID of the target **NavDestination** component. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | Yes | Callback used to return the current<br>state of the **NavDestination** component. |

**Examples**

```TypeScript
// Index.ets
// Example usage of uiObserver.on('navDestinationUpdate', options, callback)
// uiObserver.off('navDestinationUpdate', options, callback)

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text('pageOne')
    }.title('pageOne')
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  pageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    // Register a listener with the specified Navigation component ID.
    this.getUIContext().getUIObserver().on('navDestinationUpdate', { navigationId: 'testId' }, (info) => {
      console.info('NavDestination state update', JSON.stringify(info));
    });
  }

  aboutToDisappear() {
    // Unregister the listener. Omitting the callback parameter removes all registered listeners.
    this.getUIContext().getUIObserver().off('navDestinationUpdate', { navigationId: 'testId' });
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button('push').onClick(() => {
          // Push the PageOne NavDestination onto the navigation stack.
          this.stack.pushPath({ name: 'pageOne' });
        })
      }
      .id('testId')
      .title('Navigation')
      .navDestination(this.pageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('navDestinationUpdate')

```TypeScript
on(type: 'navDestinationUpdate', callback: Callback<observer.NavDestinationInfo>): void
```

Subscribes to status changes of this **NavDestination** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | Yes | Event type. The value is fixed at **'navDestinationUpdate'**,<br>which indicates the state change event of the **NavDestination** component. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | Yes | Callback used to return the current state of<br>the **NavDestination** component. |

**Examples**

```TypeScript
// Index.ets
// Example usage of uiObserver.on('navDestinationUpdate', callback)
// uiObserver.off('navDestinationUpdate', callback)

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text('pageOne')
    }.title('pageOne')
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  pageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    // Add event listeners.
    this.getUIContext().getUIObserver().on('navDestinationUpdate', (info) => {
      console.info('NavDestination state update', JSON.stringify(info));
    });
  }

  aboutToDisappear() {
    // Unregister the listener. Omitting the callback parameter removes all registered listeners.
    this.getUIContext().getUIObserver().off('navDestinationUpdate');
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button('push').onClick(() => {
          // Push the PageOne NavDestination onto the navigation stack.
          this.stack.pushPath({ name: 'pageOne' });
        })
      }
      .title('Navigation')
      .navDestination(this.pageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('navDestinationUpdateByUniqueId')

```TypeScript
on(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void
```

Registers a callback function to be called when the navigation destination is updated.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationUpdateByUniqueId' | Yes | The type of event to listen for. Must be 'navDestinationUpdateByUniqueId'. |
| navigationUniqueId | number | Yes | The uniqueId of the navigation. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | Yes | The callback function to be called when the navigation destination is updated. |

**Examples**

This example demonstrates how to listen for [NavDestination](../arkui-ts/ts-basic-components-navdestination.md) component state changes using the [Navigation](../arkui-ts/ts-basic-components-navigation.md) component's uniqueId.

```TypeScript
// Index.ets
// Example usage of on('navDestinationUpdateByUniqueId', navigationUniqueId, callback)
// off('navDestinationUpdateByUniqueId', navigationUniqueId, callback)

@Component
struct PageOne {
  private text = '';
  private uniqueId = -1;
  aboutToAppear() {
    // Obtain the uniqueId of the target Navigation component.
    let navigationUniqueId = this.queryNavigationInfo()?.uniqueId;
    if (navigationUniqueId) {
      this.uniqueId = navigationUniqueId.valueOf();
    }
    this.text = JSON.stringify(this.uniqueId);
    // Register a listener with the specified Navigation component uniqueId.
    this.getUIContext().getUIObserver().on('navDestinationUpdateByUniqueId', this.uniqueId, (info) => {
      console.info('NavDestination state update navigationId', JSON.stringify(info));
    });
  }
  aboutToDisappear() {
    // Unregister the listener. Omitting the callback parameter removes all registered listeners.
    this.getUIContext().getUIObserver().off('navDestinationUpdateByUniqueId', this.uniqueId);
  }
  build() {
    NavDestination() {
      Text('pageOne')
      Text('navigationUniqueId: ' + this.text)
        .width('80%')
        .height(50)
        .margin(50)
        .fontSize(20)
    }.title('pageOne')
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  pageBuilder(name: string) {
    PageOne()
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button('push').onClick(() => {
          // Push the PageOne NavDestination onto the navigation stack.
          this.stack.pushPath({ name: 'pageOne' });
        })
      }
      .id('testId')
      .title('Navigation')
      .navDestination(this.pageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('scrollEvent')

```TypeScript
on(type: 'scrollEvent', options: observer.ObserverOptions, callback: Callback<observer.ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'scrollEvent' | Yes | The type of event to listen for. Must be 'scrollEvent'. |
| options | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | Yes | The callback function to be called when the scroll event start or stop. |

**Examples**

See the example for [on('scrollEvent')](#onscrollevent).

## on('scrollEvent')

```TypeScript
on(type: 'scrollEvent', callback: Callback<observer.ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'scrollEvent' | Yes | The type of event to listen for. Must be 'scrollEvent'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | Yes | The callback function to be called when the scroll event start or stop. |

**Examples**

```TypeScript
// Index.ets
// Example usage of uiObserver.on('scrollEvent', callback)
// uiObserver.off('scrollEvent', callback)
// uiObserver.on('scrollEvent', options, callback)
// uiObserver.off('scrollEvent', options, callback)

import { UIObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  scroller: Scroller = new Scroller();
  observer: UIObserver = this.getUIContext().getUIObserver();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7];

  build() {
    Column() {
      Column() {
        Scroll(this.scroller) {
          Column() {
            ForEach(this.arr, (item: number) => {
              Text(item.toString())
                .width('90%')
                .height(150)
                .backgroundColor(0xFFFFFF)
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .margin({ top: 10 })
            }, (item: number) => item.toString())
          }.width('100%')
        }
        .id('testId')
        .height('80%')
      }
      .width('100%')

      Row() {
        Button('UIObserver on')
          .onClick(() => {
            // Add event listeners.
            this.observer.on('scrollEvent', (info) => {
              console.info('scrollEventInfo', JSON.stringify(info));
            });
          })
        Button('UIObserver off')
          .onClick(() => {
            // Unregister the listener. Omitting the callback parameter removes all registered listeners.
            this.observer.off('scrollEvent');
          })
      }

      Row() {
        Button('UIObserverWithId on')
          .onClick(() => {
            // Register a listener with the specified scrollable component ID.
            this.observer.on('scrollEvent', { id: 'testId' }, (info) => {
              console.info('scrollEventInfo', JSON.stringify(info));
            });
          })
        Button('UIObserverWithId off')
          .onClick(() => {
            // Unregister the listener. Omitting the callback parameter removes all registered listeners.
            this.observer.off('scrollEvent', { id: 'testId' });
          })
      }
    }
    .height('100%')
  }
}
```

## on('routerPageUpdate')

```TypeScript
on(type: 'routerPageUpdate', callback: Callback<observer.RouterPageInfo>): void
```

Unsubscribes to state changes of the page in the router.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | Yes | Event type.<br>The value is fixed at 'routerPageUpdate', which indicates the state change event of the page in the router. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.RouterPageInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | Yes | Callback to be unregistered. |

**Examples**

```TypeScript
// PageOne.ets

@Entry
@Component
struct PageOne {
  build() {
    Column() {
      Text('pageOne')
    }
  }
}
```

```TypeScript
// Index.ets
// Example usage of uiObserver.on('routerPageUpdate', callback)
// uiObserver.off('routerPageUpdate', callback)

@Entry
@Component
struct Index {
  aboutToAppear() {
    // Add event listeners.
    this.getUIContext().getUIObserver().on('routerPageUpdate', (info) => {
      console.info('router page update', JSON.stringify(info));
    });
  }

  aboutToDisappear() {
    // Unregister the listener. Omitting the callback parameter removes all registered listeners.
    this.getUIContext().getUIObserver().off('routerPageUpdate');
  }

  build() {
    Column() {
      Button('pushUrl').onClick(() => {
        // Navigate to PageOne.ets using router.
        this.getUIContext().getRouter().pushUrl({ url: 'pages/PageOne' });
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('densityUpdate')

```TypeScript
on(type: 'densityUpdate', callback: Callback<observer.DensityInfo>): void
```

Listens for screen pixel density changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'densityUpdate' | Yes | Event type. The value **'densityUpdate'** indicates the pixel density changes of the screen. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md)&gt; | Yes | Callback used to return the updated screen pixel density using a [DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md) object. |

**Examples**

```TypeScript
// Index.ets
// Example usage of uiObserver.on('densityUpdate', callback)
// uiObserver.off('densityUpdate', callback)

import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State density: number = 0;
  @State message: string = 'Listener not registered';

  // Define callbacks for event listeners.
  densityUpdateCallback = (info: uiObserver.DensityInfo) => {
    this.density = info.density;
    this.message = 'DPI after change:' + this.density.toString();
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(24)
        .fontWeight(FontWeight.Bold)
      Button ('Subscribe to Screen Pixel Density Changes')
        .margin({ bottom: 10 })
        .onClick(() => {
          this.message = 'Listener registered';
          // Add event listeners.
          this.getUIContext().getUIObserver().on('densityUpdate', this.densityUpdateCallback);
        })
      Button ('Unsubscribe from Screen Pixel Density Changes')
        .onClick(() => {
          this.message = 'Listener not registered';
          // Remove event listeners.
          this.getUIContext().getUIObserver().off('densityUpdate', this.densityUpdateCallback);
        })
    }
  }
}
```

## on('willDraw')

```TypeScript
on(type: 'willDraw', callback: Callback<void>): void
```

Listens for drawing instruction dispatch in each frame.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'willDraw' | Yes | Event event. The value **'willDraw'** indicates whether drawing is about to occur. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
// Index.ets
// Example usage of uiObserver.on('willDraw', callback)
// uiObserver.off('willDraw', callback)

@Entry
@Component
struct Index {
  // Define callbacks for event listeners.
  willDrawCallback = () => {
    console.info('willDraw instruction dispatched.');
  }

  build() {
    Column() {
      Button('Listen for Drawing Instruction Dispatch')
        .margin({ bottom: 10 })
        .onClick(() => {
          // Add event listeners.
          this.getUIContext().getUIObserver().on('willDraw', this.willDrawCallback);
        })
      Button('Unregister Drawing Instruction Dispatch Listener')
        .onClick(() => {
          // Remove event listeners.
          this.getUIContext().getUIObserver().off('willDraw', this.willDrawCallback);
        })
    }
  }
}
```

## on('didLayout')

```TypeScript
on(type: 'didLayout', callback: Callback<void>): void
```

Listens for layout completion status in each frame.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'didLayout' | Yes | Event type. The value **'didLayout'** indicates whether the layout has been completed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
// Index.ets
// Example usage of uiObserver.on('didLayout', callback)
// uiObserver.off('didLayout', callback)

@Entry
@Component
struct Index {
  // Define callbacks for event listeners.
  didLayoutCallback = () => {
    console.info('Layout completed.');
  }

  build() {
    Column() {
      Button('Listen for Layout Completion')
        .margin({ bottom: 10 })
        .onClick(() => {
          // Add event listeners.
          this.getUIContext().getUIObserver().on('didLayout', this.didLayoutCallback);
        })
      Button('Unregister Layout Completion Listener')
        .onClick(() => {
          // Remove event listeners.
          this.getUIContext().getUIObserver().off('didLayout', this.didLayoutCallback);
        })
    }
  }
}
```

## on('navDestinationSwitch')

```TypeScript
on(
    type: 'navDestinationSwitch',
    callback: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Registers a callback function to be called when the navigation switched to a new navDestination.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | Yes | The type of event to listen for. Must be 'navDestinationSwitch'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | Yes | The callback function to be called when the navigation switched to a new navDestination. |

**Examples**

```TypeScript
// Index.ets
// Example usage of UIObserver.on('navDestinationSwitch', callback)
// UIObserver.off('navDestinationSwitch', callback)

import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text('pageOne')
    }.title('pageOne')
  }
}

// Define callbacks for event listeners.
const callbackFunc = (info: uiObserver.NavDestinationSwitchInfo) => {
  console.info(`testTag navDestinationSwitch from: ${JSON.stringify(info.from)} to: ${JSON.stringify(info.to)}`);
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  pageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    let obs = this.getUIContext().getUIObserver();
    // Add event listeners.
    obs.on('navDestinationSwitch', callbackFunc);
  }

  aboutToDisappear() {
    let obs = this.getUIContext().getUIObserver();
    // Remove event listeners.
    obs.off('navDestinationSwitch', callbackFunc);
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button('push').onClick(() => {
          // Push the PageOne NavDestination onto the navigation stack.
          this.stack.pushPath({ name: 'pageOne' });
        })
      }
      .title("Navigation")
      .navDestination(this.pageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('navDestinationSwitch')

```TypeScript
on(
    type: 'navDestinationSwitch',
    observerOptions: observer.NavDestinationSwitchObserverOptions,
    callback: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Registers a callback function to be called when the navigation switched to a new navDestination.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | Yes | The type of event to listen for. Must be 'navDestinationSwitch'. |
| observerOptions | [observer.NavDestinationSwitchObserverOptions](arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | Yes | Options. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | Yes | The callback function to be called when the navigation switched to a new navDestination. |

**Examples**

```TypeScript
// Index.ets
// Example usage of UIObserver.on('navDestinationSwitch', observerOptions, callback)
// UIObserver.off('navDestinationSwitch', observerOptions, callback)

import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text('pageOne')
    }.title('pageOne')
  }
}

// Define callbacks for event listeners.
function callbackFunc(info: uiObserver.NavDestinationSwitchInfo) {
  console.info(`testTag navDestinationSwitch from: ${JSON.stringify(info.from)} to: ${JSON.stringify(info.to)}`);
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  pageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    let obs = this.getUIContext().getUIObserver();
    // Register a listener with the specified Navigation component ID.
    obs.on('navDestinationSwitch', { navigationId: 'myNavId' }, callbackFunc);
  }

  aboutToDisappear() {
    let obs = this.getUIContext().getUIObserver();
    // Remove event listeners.
    obs.off('navDestinationSwitch', { navigationId: 'myNavId' }, callbackFunc);
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button('push').onClick(() => {
          // Push the PageOne NavDestination onto the navigation stack.
          this.stack.pushPath({ name: 'pageOne' });
        })
      }
      .id("myNavId")
      .title("Navigation")
      .navDestination(this.pageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('willClick')

```TypeScript
on(type: 'willClick', callback: ClickEventListenerCallback): void
```

Registers a callback function to be called before clickEvent is called.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'willClick' | Yes | The type of event to listen for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | Yes | The callback function to be called when the clickEvent will be trigger or after. |

**Examples**

See the example for [on('willClick')](#onwillclick).

## on('didClick')

```TypeScript
on(type: 'didClick', callback: ClickEventListenerCallback): void
```

Registers a callback function to be called after clickEvent is called.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'didClick' | Yes | The type of event to listen for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | Yes | The callback function to be called when the clickEvent will be trigger or after. |

**Examples**

See the example for [on('willClick')](#onwillclick).

## on('willClick')

```TypeScript
on(type: 'willClick', callback: GestureEventListenerCallback): void
```

Registers a callback function to be called before tapGesture is called.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'willClick' | Yes | The type of event to listen for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | Yes | The callback function to be called when the clickEvent will be trigger or after. |

**Examples**

```TypeScript
// Index.ets
// Example usage of uiObserver.on('willClick', callback)
// uiObserver.off('willClick', callback)
// uiObserver.on('didClick', callback)
// uiObserver.off('didClick', callback)

// Define callbacks for event listeners.
const willClickGestureCallback = (event: GestureEvent, node?: FrameNode) => {
  console.info('Example willClickCallback GestureEvent is called');
}

const willClickCallback = (event: ClickEvent, node?: FrameNode) => {
  console.info('Example willClickCallback ClickEvent is called');
}

const didClickGestureCallback = (event: GestureEvent, node?: FrameNode) => {
  console.info('Example didClickCallback GestureEvent is called');
}

const didClickCallback = (event: ClickEvent, node?: FrameNode) => {
  console.info('Example didClickCallback ClickEvent is called');
}

@Entry
@Component
struct ClickExample {
  @State clickCount: number = 0;
  @State tapGestureCount: number = 0;

  aboutToAppear(): void {
    // Add event listeners.
    let observer = this.getUIContext().getUIObserver();
    observer.on('willClick', willClickGestureCallback);
    observer.on('willClick', willClickCallback);
    observer.on('didClick', didClickGestureCallback);
    observer.on('didClick', didClickCallback);
  }

  aboutToDisappear(): void {
    // Remove event listeners.
    let observer = this.getUIContext().getUIObserver();
    observer.off('willClick', willClickGestureCallback);
    observer.off('willClick', willClickCallback);
    // If no callback is specified, all callbacks for this event will be removed.
    observer.off('didClick');
  }

  build() {
    Column() {
      /**
       * onClick and TapGesture are handled in the same way in the backend.
       * Therefore, whether onClick or TapGesture is triggered,
       * both callback types (GestureEvent and ClickEvent) registered with on('willClick') will be triggered.
       * Similarly, both callback types registered with on('didClick') will be triggered.
       */
      Column() {
        Text('Click Count: ' + this.clickCount)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(50)
      .onClick((event: ClickEvent) => {
        this.clickCount++;
        console.info('Example Click event is called');
      })

      Column() {
        Text('TapGesture Count: ' + this.tapGestureCount)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(50)
      .gesture(TapGesture({ count: 2 }).onAction((event: TapGestureEvent) => {
        this.tapGestureCount++;
        console.info('Example Click event is called');
      }))
    }
  }
}
```

## on('didClick')

```TypeScript
on(type: 'didClick', callback: GestureEventListenerCallback): void
```

Registers a callback function to be called after tapGesture is called.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'didClick' | Yes | The type of event to listen for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | Yes | The callback function to be called when the clickEvent will be trigger or after. |

**Examples**

See the example for [on('willClick')](#onwillclick).

## on('beforePanStart')

```TypeScript
on(type: 'beforePanStart', callback: PanListenerCallback): void
```

Listens for pan gesture [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) pre-execution events, executing the callback before the actual [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) event. It works for finger swiping, mouse dragging, mouse wheel scrolling, and touchpad movements, but not for screen reader touch mode.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'beforePanStart' | Yes | Event type. The value is fixed at **'beforePanStart'**, indicating command dispatch before the execution of the pan gesture [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) event. The registered callback is triggered before **onActionStart** is executed. |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | Yes | Callback used to return the result. It provides [GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md), [GestureRecognizer](../arkts-components/arkts-arkui-tapgesture-comp-gesturerecognizer-c.md), and the target component's [FrameNode](arkts-arkui-framenode-c.md) information. |

**Examples**

```TypeScript
// Index.ets
// Example usage of uiObserver.on('beforePanStart', callback)
// uiObserver.off('beforePanStart', callback)
// uiObserver.on('afterPanStart', callback)
// uiObserver.off('afterPanStart', callback)
// uiObserver.on('beforePanEnd', callback)
// uiObserver.off('beforePanEnd', callback)
// uiObserver.on('afterPanEnd', callback)
// uiObserver.off('afterPanEnd', callback)

// Used in page components.
let TEST_TAG: string = 'node';

// Define callbacks for event listeners.
const callbackFunc = () => {
  console.info('on == beforePanStart');
}

const afterPanCallBack = () => {
  console.info('on == afterPanStart');
}

const beforeEndCallBack = () => {
  console.info('on == beforeEnd');
}

const afterEndCallBack = () => {
  console.info('on == afterEnd');
}

const beforeStartCallBack = () => {
  console.info('on == beforeStartCallBack');
}

const panGestureCallBack = (event: GestureEvent, current: GestureRecognizer, node?: FrameNode) => {
  TEST_TAG = 'panGestureEvent';
  console.info('===' + TEST_TAG + '=== event.repeat is ' + event.repeat);
  console.info('===' + TEST_TAG + '=== event target is ' + event.target.id);
  TEST_TAG = 'panGestureCurrent';
  console.info('===' + TEST_TAG + '=== current.getTag() is ' + current.getTag());
  TEST_TAG = 'panGestureNode';
  console.info('===' + TEST_TAG + '=== node?.getId() is ' + node?.getId());
}


@Entry
@Component
struct PanExample {
  @State offsetX: number = 0;
  @State offsetY: number = 0;
  @State positionX: number = 0;
  @State positionY: number = 0;
  private panOption: PanGestureOptions = new PanGestureOptions({direction: PanDirection.All });

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    // Add event listeners.
    observer.on('beforePanStart', callbackFunc);
    observer.on('beforePanStart', panGestureCallBack);
    observer.on('beforePanStart', beforeStartCallBack);
    observer.on('afterPanStart', afterPanCallBack);
    observer.on('beforePanEnd', beforeEndCallBack);
    observer.on('afterPanEnd', afterEndCallBack);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    // Remove event listeners.
    observer.off('beforePanStart', callbackFunc);
    observer.off('beforePanStart');
    observer.off('afterPanStart', afterPanCallBack);
    observer.off('beforePanEnd');
    observer.off('afterPanEnd');
  }

  build() {
    Column() {
      Column() {
        Text('PanGesture :\nX: ' + this.offsetX + '\n' + 'Y: ' + this.offsetY)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(50)
      .translate({ x: this.offsetX, y: this.offsetY, z: 0 })
      .id('columnOuter')
      .gesture(
        PanGesture(this.panOption)
          .onActionStart((event: GestureEvent) => {
            console.info('Pan start');
          })
          .onActionUpdate((event: GestureEvent) => {
            if (event) {
              this.offsetX = this.positionX + event.offsetX;
              this.offsetY = this.positionY + event.offsetY;
            }
          })
          .onActionEnd((event: GestureEvent) => {
            this.positionX = this.offsetX;
            this.positionY = this.offsetY;
            console.info('Pan end');
            }))
          }
  }
}
```

## on('beforePanEnd')

```TypeScript
on(type: 'beforePanEnd', callback: PanListenerCallback): void
```

Listens for pan gesture [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) pre-execution events, executing the callback before the actual [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) event. It works for finger swiping, mouse dragging, mouse wheel scrolling, and touchpad movements, but not for screen reader touch mode.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'beforePanEnd' | Yes | Event type. The value is fixed at **'beforePanEnd'**, indicating command dispatch before the execution of the pan gesture [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) event. The registered callback is triggered before **onActionEnd** is executed. |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | Yes | Callback used to return the result. It provides [GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md), [GestureRecognizer](../arkts-components/arkts-arkui-tapgesture-comp-gesturerecognizer-c.md), and the target component's [FrameNode](arkts-arkui-framenode-c.md) information. |

**Examples**

See the example for [on('beforePanStart')](#onbeforepanstart).

## on('afterPanStart')

```TypeScript
on(type: 'afterPanStart', callback: PanListenerCallback): void
```

Listens for pan gesture [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) post-execution events, executing the callback after the actual [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) event. It works for finger swiping, mouse dragging, mouse wheel scrolling, and touchpad movements, but not for screen reader touch mode.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'afterPanStart' | Yes | Event type. The value is fixed at **'afterPanStart'**, indicating command dispatch after the execution of the pan gesture [onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart) event. The registered callback is triggered after **onActionStart** is executed. |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | Yes | Callback used to return the result. It provides [GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md), [GestureRecognizer](../arkts-components/arkts-arkui-tapgesture-comp-gesturerecognizer-c.md), and the target component's [FrameNode](arkts-arkui-framenode-c.md) information. |

**Examples**

See the example for [on('beforePanStart')](#onbeforepanstart).

## on('afterPanEnd')

```TypeScript
on(type: 'afterPanEnd', callback: PanListenerCallback): void
```

Listens for pan gesture [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) post-execution events, executing the callback after the actual [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) event. It works for finger swiping, mouse dragging, mouse wheel scrolling, and touchpad movements, but not for screen reader touch mode.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'afterPanEnd' | Yes | Event type. The value is fixed at **'beforePanEnd'**, indicating command dispatch after the execution of the pan gesture [onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend) event. The registered callback is triggered after **onActionEnd** is executed. |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | Yes | Callback used to return the result. It provides [GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md), [GestureRecognizer](../arkts-components/arkts-arkui-tapgesture-comp-gesturerecognizer-c.md), and the target component's [FrameNode](arkts-arkui-framenode-c.md) information. |

**Examples**

See the example for [on('beforePanStart')](#onbeforepanstart).

## on('tabContentUpdate')

```TypeScript
on(type: 'tabContentUpdate', options: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void
```

Registers a callback function to be called when the tabContent is showed or hidden.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | Yes | The type of event to listen for. Must be 'tabContentUpdate'. |
| options | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | Yes | The callback function to be called when the tabContent show or hide. |

**Examples**

```TypeScript
// Index.ets
// Example usage of uiObserver.on('tabContentUpdate', options, callback)
// uiObserver.off('tabContentUpdate', options, callback)

import { uiObserver } from '@kit.ArkUI';

// Define callbacks for event listeners.
function callbackFunc(info: uiObserver.TabContentInfo) {
  console.info('tabContentUpdate', JSON.stringify(info));
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    // Register a listener with the specified Tabs component ID.
    observer.on('tabContentUpdate', { id: 'tabsId' }, callbackFunc);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    // Remove event listeners.
    observer.off('tabContentUpdate', { id: 'tabsId' }, callbackFunc);
  }

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId0')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId1')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId2')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId3')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId')
    }.width('100%')
  }
}
```

## on('tabContentUpdate')

```TypeScript
on(type: 'tabContentUpdate', callback: Callback<observer.TabContentInfo>): void
```

Registers a callback function to be called when the tabContent is showed or hidden.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | Yes | The type of event to listen for. Must be 'tabContentUpdate'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | Yes | The callback function to be called when the tabContent is showed or hidden. |

**Examples**

```TypeScript
// Index.ets
// Example usage of uiObserver.on('tabContentUpdate', callback)
// uiObserver.off('tabContentUpdate', callback)

import { uiObserver } from '@kit.ArkUI';

// Define callbacks for event listeners.
const callbackFunc = (info: uiObserver.TabContentInfo) => {
  console.info('tabContentUpdate', JSON.stringify(info));
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    // Add event listeners.
    observer.on('tabContentUpdate', callbackFunc);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    // Remove event listeners.
    observer.off('tabContentUpdate', callbackFunc);
  }

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId0')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId1')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId2')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId3')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId')
    }.width('100%')
  }
}
```

## on('tabChange')

```TypeScript
on(type: 'tabChange', config: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void
```

Registers a callback function to be called when the tabContent is showed or hidden. Include the cases when the first tab content shows and when the tab changes current index.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'tabChange' | Yes | The type of event to listen for. Must be 'tabChange'. |
| config | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | The options object. Includes the observed component id. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | Yes | The callback function to be called when when the tabContent is showed or hidden. |

**Examples**

```TypeScript
// Index.ets
// This example demonstrates how to subscribe to tab change events of the Tabs component with ID 'tabsId'.
// During initialization of the Tabs component, the display events for tab page 0 are listened for, with the corresponding tab ID 'tabContentId0'. After users swipe on the Tabs component, the system detects the hiding of tab page 0 and the display of tab page 1 with ID 'tabContentId1'.
import { uiObserver } from '@kit.ArkUI';

// Define callbacks for event listeners.
function callbackFunc(info: uiObserver.TabContentInfo) {
  console.info('tabChange', JSON.stringify(info));
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    // Register a listener with the specified Tabs component ID.
    observer.on('tabChange', { id: 'tabsId' }, callbackFunc);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    // Remove event listeners.
    observer.off('tabChange', { id: 'tabsId' }, callbackFunc);
  }

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId0')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId1')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId2')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId3')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId')

      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId5')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId6')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId7')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId8')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
    }.width('100%')
  }
}
```

## on('tabChange')

```TypeScript
on(type: 'tabChange', callback: Callback<observer.TabContentInfo>): void
```

Registers a callback function to be called when the tabContent is showed or hidden. Include the cases when the first tab content shows and when the tab changes current index.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'tabChange' | Yes | The type of event to listen for. Must be 'tabChange'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | Yes | The callback function to be called when the tabContent is showed or hidden. |

**Examples**

```TypeScript
// Index.ets
// This example demonstrates how to subscribe to tab switching events of Tabs components.
// It simultaneously subscribes to two Tabs components with IDs 'tabsId1' and 'tabsId2'.
// During initialization of both Tabs components, the display events for tab page 0 are listened for, with corresponding tab IDs 'tabContentId0' and 'tabContentId5'.
// After users swipe on the Tabs component with ID 'tabsId1', the system detects the hiding of tab page 0 and the display of tab page 1 with ID 'tabContentId1'.
import { uiObserver } from '@kit.ArkUI';

// Define callbacks for event listeners.
function callbackFunc(info: uiObserver.TabContentInfo) {
  console.info('tabChange', JSON.stringify(info));
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    // Add event listeners.
    observer.on('tabChange', callbackFunc);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    // Remove event listeners.
    observer.off('tabChange', callbackFunc);
  }

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId0')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId1')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId2')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId3')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId1')

      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId5')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId6')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId7')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId8')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId2')
    }.width('100%')
  }
}
```

## on('windowSizeLayoutBreakpointChange')

```TypeScript
on(type: 'windowSizeLayoutBreakpointChange', callback: Callback<observer.WindowSizeLayoutBreakpointInfo>): void
```

Registers a callback for window size layout breakpoint changes. This enables adaptive UI layout adjustments based on window size variations. This API uses an asynchronous callback to return the result.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'windowSizeLayoutBreakpointChange' | Yes | Event type. The value is fixed at **'windowSizeLayoutBreakpointChange'**, indicating window size layout breakpoint changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.WindowSizeLayoutBreakpointInfo](arkts-arkui-uiobserver-windowsizelayoutbreakpointinfo-c.md)&gt; | Yes | Callback used to return the result. It provides window width and height layout breakpoint enumerations using a **WindowSizeLayoutBreakpointinfo** object. |

**Examples**

This example demonstrates how to register and unregister window size layout breakpoint change listeners.

```TypeScript
import { uiObserver, window } from '@kit.ArkUI';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  private changeOrientation(isLandscape: boolean) {
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    window.getLastWindow(context).then((lastWindow) => {
      lastWindow.setPreferredOrientation(isLandscape ? window.Orientation.LANDSCAPE : window.Orientation.PORTRAIT);
    });
  }

  @State message: string = '';
  @State widthBreakpoint: WidthBreakpoint = WidthBreakpoint.WIDTH_SM;
  @State heightBreakpoint: HeightBreakpoint = HeightBreakpoint.HEIGHT_SM;
  winSizeLayoutBreakpointCallback = (info: uiObserver.WindowSizeLayoutBreakpointInfo) => {
    this.widthBreakpoint = info.widthBreakpoint;
    this.heightBreakpoint = info.heightBreakpoint;
    this.message = 'widthBpt:' + this.widthBreakpoint.toString() + 'heightBpt:' + this.heightBreakpoint.toString();
  }

  build() {
    Column() {
      Text(this.message)
      Button('Register Window Size Breakpoint Change Listener')
        .onClick(() => {
          this.getUIContext()
            .getUIObserver()
            .on('windowSizeLayoutBreakpointChange', this.winSizeLayoutBreakpointCallback);
        })
      Button('Unregister Window Size Breakpoint Change Listener')
        .onClick(() => {
          this.getUIContext()
            .getUIObserver()
            .off('windowSizeLayoutBreakpointChange', this.winSizeLayoutBreakpointCallback);
        })
      Button("Portrait").onClick(() => {
        this.changeOrientation(false);
      })
      Button("Landscape").onClick(() => {
        this.changeOrientation(true);
      })
    }
  }
}
```

## on('nodeRenderState')

```TypeScript
on(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback: NodeRenderStateChangeCallback): void
```

Registers a callback to be invoked when the rendering state of a specific node changes. This callback is executed immediately once upon successful registration.

Be mindful of node quantity limitations. For performance reasons, registering too many nodes within a single UI instance will throw an exception.

Typically, a **RENDER_OUT** notification is received when a component moves off-screen. However, in certain scenarios, a **RENDER_OUT** notification might not be triggered even if a component has moved off-screen. For example, components with caching capabilities like Swiper will not trigger **RENDER_OUT** notifications even when the **isShown** parameter in the [cachedCount](../arkts-components/arkts-arkui-swiper-comp-attribute.md#cachedcount-1) attribute is set to **true**.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'nodeRenderState' | Yes | Event type. The value is fixed at **'nodeRenderState'**, indicating rendering state changes. |
| nodeIdentity | [NodeIdentity](arkts-arkui-nodeidentity-t.md) | Yes | Node ID. |
| callback | [NodeRenderStateChangeCallback](arkts-arkui-noderenderstatechangecallback-t.md) | Yes | Callback used to return the result. It provides the [NodeRenderState](arkts-arkui-arkui-uicontext-noderenderstate-e.md) of the node rendering state change event and the component's [FrameNode](arkts-arkui-framenode-c.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [161001](../errorcode-node-render-monitor.md#161001-number-of-nodes-listening-for-render-state-exceeds-the-limit) | The count of nodes monitoring render state is over the limitation. |

**Examples**

This example demonstrates how to add and remove listeners for a target component. When the user swipes left, the target component disappears from the screen, triggering a RENDER_OUT notification. When the user swipes right, the component reappears on the screen, triggering a RENDER_IN notification.

```TypeScript
// Index.ets
// Example usage of uiObserver.on('nodeRenderState', nodeIdentity, callback)
// uiObserver.off('nodeRenderState', nodeIdentity, callback)

// Used in page components.
import { NodeRenderState } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State fontColor: string = '#182431';
  @State selectedFontColor: string = '#007DFF';
  @State currentIndex: number = 0;
  @State selectedIndex: number = 0;
  @State notice: string = "";
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
      Tabs({ barPosition: BarPosition.Start, index: this.currentIndex, controller: this.controller }) {
        TabContent() {
          Column() {
            Column() {
              Button("Listened Node").margin({ top: 5 }).id("button_1")
              Button("Add Listener").margin({ top: 5 }).onClick(() => {
                let node: FrameNode | null = this.getUIContext().getFrameNodeById("button_1");
                if (node) {
                  let observer = this.getUIContext().getUIObserver();
                  // Add event listeners.
                  observer.on("nodeRenderState", node?.getUniqueId(), (state: NodeRenderState, node?: FrameNode) => {
                    // Update notification content based on node state changes.
                    if (state === 0) {
                      this.notice = "RENDER_IN";
                    } else {
                      this.notice = "RENDER_OUT";
                    }
                    console.info("Node state changed. Current state: ", state);
                  });
                }
              })
              Button("Remove Listener").margin({ top: 5 }).onClick(() => {
                let node: FrameNode | null = this.getUIContext().getFrameNodeById("button_1");
                if (node) {
                  let observer = this.getUIContext().getUIObserver();
                  // Unregister the listener. Omitting the callback parameter removes all registered listeners.
                  observer.off("nodeRenderState", node?.getUniqueId());
                }
                this.notice = "";
              })
            }
          }.width('100%').height('100%').backgroundColor('#00CB87')
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
        this.currentIndex = index;
        this.selectedIndex = index;
      })
      .onAnimationStart((index: number, targetIndex: number, event: TabsAnimationEvent) => {
        if (index === targetIndex) {
          return;
        }
        this.selectedIndex = targetIndex;
      })
      .width(360)
      .height(296)
      .margin({ top: 52 })
      .backgroundColor('#F1F3F5')

      Text(`Notification received: ${this.notice}`)
        .fontSize(20)
        .margin(10)
    }.width('100%')
  }
}
```

## on('textChange')

```TypeScript
on(type: 'textChange', callback: Callback<observer.TextChangeEventInfo>): void
```

Registers a callback function to be called when text field's content is changed.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'textChange' | Yes | The type of event to listen for. Must be 'textChange'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md)&gt; | Yes | The callback function to be called when text field's content is changed. |

**Examples**

```TypeScript
import { UIObserver } from '@kit.ArkUI';

@Entry
@Component
struct TextUiObserver {
  observer: UIObserver = this.getUIContext().getUIObserver();
  build() {
    Column() {
      TextArea({ text: 'Hello World TextArea' })
        .width(336)
        .height(56)
        .margin({bottom:5})
        .backgroundColor('#FFFFFF')
        .id('TestId1')
      TextInput({ text: 'Hello World TextInput' })
        .width(336)
        .height(56)
        .margin({bottom:5})
        .backgroundColor('#FFFFFF')
        .id('TestId2')
      Search({ value: 'Hello World Search' })
        .width(336)
        .height(56)
        .margin({bottom:5})
        .backgroundColor('#FFFFFF')
        .id('TestId3')
      Row() {
        // Enable global listening.
        Button('UIObserver on')
          .onClick(() => {
            this.observer.on('textChange', (info) => {
              console.info('textChangeInfo', JSON.stringify(info));
            });
          })
        // Disable global listening.
        Button('UIObserver off')
          .onClick(() => {
            this.observer.off('textChange');
          })
      }.margin({bottom:5})
      // Enable and disable listening for a specific ID.
      Row() {
        Button('UIObserver TestId1 on')
          .onClick(() => {
            this.observer.on('textChange', { id: 'TestId1' }, (info) => {
              console.info('textChangeInfo', JSON.stringify(info));
            });
          })

        Button('UIObserver TestId1 off')
          .onClick(() => {
            this.observer.off('textChange', { id: 'TestId1' });
          })
      }.margin({bottom:5})
      Row() {
        Button('UIObserver TestId2 on')
          .onClick(() => {
            this.observer.on('textChange', { id: "TestId2" }, (info) => {
              console.info('textChangeInfo', JSON.stringify(info));
            });
          })

        Button('UIObserver TestId2 off')
          .onClick(() => {
            this.observer.off('textChange', { id: "TestId2" });
          })
      }.margin({bottom:5})
      Row() {
        Button('UIObserver TestId3 on')
          .onClick(() => {
            this.observer.on('textChange', { id: "TestId3" }, (info) => {
              console.info('textChangeInfo', JSON.stringify(info));
            });
          })

        Button('UIObserver TestId3 off')
          .onClick(() => {
            this.observer.off('textChange', { id: "TestId3" });
          })
      }.margin({bottom:5})
    }.width('100%').height('100%').backgroundColor('#F1F3F5')
  }
}
```

## on('textChange')

```TypeScript
on(type: 'textChange', identity: observer.ObserverOptions, callback: Callback<observer.TextChangeEventInfo>): void
```

Registers a callback function to be called when text field's content is changed.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'textChange' | Yes | The type of event to listen for. Must be 'textChange'. |
| identity | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | Identity options. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md)&gt; | Yes | The callback function to be called when the text field's content is changed. |

**Examples**

For details, see [on('textChange')](#ontextchange).

## onNavDestinationSizeChange

```TypeScript
onNavDestinationSizeChange(callback: Callback<observer.NavDestinationInfo>): void
```

Registers a callback that is triggered when the size of the visible navigation destination changes. This API uses an asynchronous callback to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | Yes | Callback used to return navigation destination information. |

**Examples**

```TypeScript
import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOneContent {
  destSizeCallback(info: uiObserver.NavDestinationInfo): void {
    console.info(`testTag destSize changeTo ${(info && info.size) ? JSON.stringify(info.size) : 'NA'}`);
  }

  aboutToAppear(): void {
    // You can obtain the size of the navigation destination page by registering a listener.
    this.getUIContext().getUIObserver().onNavDestinationSizeChange(this.destSizeCallback);
  }

  aboutToDisappear(): void {
    this.getUIContext().getUIObserver().offNavDestinationSizeChange(this.destSizeCallback);
  }

  build() {
    Column() {
      Button('queryDestSize').onClick(() => {
        // You can also proactively obtain the size of the navigation destination page.
        let info = this.queryNavDestinationInfo();
        console.info(`testTag destSize: ${(info && info.size) ? JSON.stringify(info.size) : 'NA'}`);
      })
    }
    .width('100%')
    .height('100%')
  }
}

@Component
struct PageOne {
  build() {
    NavDestination() {
      PageOneContent()
    }
    .title('pageOne')
  }
}

@Entry
@Component
struct QueryNavDestinationSize {
  private stack: NavPathStack = new NavPathStack();

  aboutToAppear(): void {
    this.stack.pushPath({name: 'one'});
  }

  @Builder
  myPageMap(name: string) {
    PageOne()
  }

  build() {
    Navigation(this.stack) {
    }
    .width('100%')
    .height('100%')
    .navDestination(this.myPageMap)
    .hideNavBar(true)
  }
}
```

## onNavDestinationSizeChangeByUniqueId

```TypeScript
onNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void
```

Removes the listener callback registered using the **onNavDestinationSizeChangeByUniqueId** API. This API uses an asynchronous callback to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| navigationUniqueId | number | Yes | Unique ID of the **Navigation** component to which the **NavDestination** component to be listened belongs, which can be obtained through [queryNavigationInfo](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md#querynavigationinfo). |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | Yes | Callback to be removed. If no parameter is passed, all callbacks with the same **navigationUniqueId** setting are removed. |

**Examples**

```TypeScript
import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOneContent {
  private navUniqueId: number = 0;

  destSizeCallback(info: uiObserver.NavDestinationInfo): void {
    console.info(`testTag destSize changeTo ${(info && info.size) ? JSON.stringify(info.size) : 'NA'}`);
  }

  aboutToAppear(): void {
    let navInfo = this.queryNavigationInfo();
    if (navInfo && navInfo.uniqueId) {
      this.navUniqueId = navInfo.uniqueId;
      // You can obtain the size of the navigation destination page by registering a listener.
      this.getUIContext().getUIObserver().onNavDestinationSizeChangeByUniqueId(this.navUniqueId, this.destSizeCallback);
    }
  }

  aboutToDisappear(): void {
    this.getUIContext().getUIObserver().offNavDestinationSizeChangeByUniqueId(this.navUniqueId, this.destSizeCallback);
  }

  build() {
    Column() {
      Button('queryDestSize').onClick(() => {
        // You can also proactively obtain the size of the navigation destination page.
        let info = this.queryNavDestinationInfo();
        console.info(`testTag destSize: ${(info && info.size) ? JSON.stringify(info.size) : 'NA'}`);
      })
    }
    .width('100%')
    .height('100%')
  }
}

@Component
struct PageOne {
  build() {
    NavDestination() {
      PageOneContent()
    }
    .title('pageOne')
  }
}

@Entry
@Component
struct QueryNavDestinationSize {
  private stack: NavPathStack = new NavPathStack();

  aboutToAppear(): void {
    this.stack.pushPath({name: 'one'});
  }

  @Builder
  myPageMap(name: string) {
    PageOne()
  }

  build() {
    Navigation(this.stack) {
    }
    .width('100%')
    .height('100%')
    .navDestination(this.myPageMap)
    .hideNavBar(true)
  }
}
```

## onRouterPageSizeChange

```TypeScript
onRouterPageSizeChange(callback: Callback<observer.RouterPageInfo>): void
```

Registers a callback that is triggered when the size of the visible router page changes. This API uses an asynchronous callback to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.RouterPageInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | Yes | Callback used to return the information about the router page. |

**Examples**

```TypeScript
import { uiObserver } from '@kit.ArkUI';

const myPageRouterPageSizeCallback = (info: uiObserver.RouterPageInfo): void => {
  console.info(`testTag pageSize changeTo ${(info && info.size) ? JSON.stringify(info.size) : 'NA'}`);
}

@Entry
@Component
struct QueryRouterPageSize {
  aboutToAppear(): void {
    // You can obtain the page size information by registering a listener.
    this.getUIContext().getUIObserver().onRouterPageSizeChange(myPageRouterPageSizeCallback);
  }

  aboutToDisappear(): void {
    this.getUIContext().getUIObserver().offRouterPageSizeChange(myPageRouterPageSizeCallback);
  }

  build() {
    Column() {
      Button('querySize').onClick(() => {
        // You can also proactively obtain the page size.
        let info = this.queryRouterPageInfo();
        console.info(`testTag pageSize: ${info && info.size ? JSON.stringify(info.size) : 'NA'}`);
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## onSwiperContentUpdate

```TypeScript
onSwiperContentUpdate(callback: Callback<SwiperContentInfo>): void
```

Listens for content switching events of the **Swiper** component. This API uses an asynchronous callback to return the result.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | Yes | Callback used to return the result. It provides the **Swiper** content switching information using a **SwiperContentInfo** object. |

**Examples**

```TypeScript
// Index.ets
import { SwiperContentInfo } from '@kit.ArkUI';

// Define callbacks for event listeners.
const callbackFunc = (info: SwiperContentInfo) => {
  console.info('swiperContentUpdate', JSON.stringify(info));
}

@Entry
@Component
struct SwiperExample {
  private swiperController: SwiperController = new SwiperController();

  aboutToAppear(): void {
    // Listen for 'swiperContentUpdate' events.
    this.getUIContext().getUIObserver().onSwiperContentUpdate(callbackFunc);
  }

  aboutToDisappear(): void {
    // Unregister the listener for 'swiperContentUpdate' events.
    this.getUIContext().getUIObserver().offSwiperContentUpdate(callbackFunc);
  }

  build() {
    Column({ space: 5 }) {
      Swiper(this.swiperController) {
        Column() {
          Text('SwiperItem1')
        }.width('100%').height('100%').backgroundColor('#00CB87')

        Column() {
          Text('SwiperItem2')
        }.width('100%').height('100%').backgroundColor('#007DFF')

        Column() {
          Text('SwiperItem3')
        }.width('100%').height('100%').backgroundColor('#FFBF00')

        Column() {
          Text('SwiperItem4')
        }.width('100%').height('100%').backgroundColor('#E67C92')
      }
      .width(360)
      .height(300)
    }.width('100%')
  }
}
```

<a id="onswipercontentupdate-1"></a>

## onSwiperContentUpdate

```TypeScript
onSwiperContentUpdate(config: observer.ObserverOptions, callback: Callback<SwiperContentInfo>): void
```

Listens for content switching events of a specific **Swiper** component identified by its ID. This API uses an asynchronous callback to return the result.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | Information about the target **Swiper** component. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | Yes | Callback used to return the result. It provides the **Swiper** content switching information using a **SwiperContentInfo** object. |

**Examples**

```TypeScript
// Index.ets
import { SwiperContentInfo } from '@kit.ArkUI';

// Define callbacks for event listeners.
function callbackFunc(info: SwiperContentInfo) {
  console.info('swiperContentUpdate', JSON.stringify(info));
}

@Entry
@Component
struct SwiperExample {
  private swiperController: SwiperController = new SwiperController();

  aboutToAppear(): void {
    // Listen for 'swiperContentUpdate' events for the component with the specified ID.
    this.getUIContext().getUIObserver().onSwiperContentUpdate({ id: 'swiperId' }, callbackFunc);
  }

  aboutToDisappear(): void {
    // Unregister the listener for 'swiperContentUpdate' events for the component with the specified ID.
    this.getUIContext().getUIObserver().offSwiperContentUpdate({ id: 'swiperId' }, callbackFunc);
  }

  build() {
    Column({ space: 5 }) {
      Swiper(this.swiperController) {
        Column() {
          Text('SwiperItem1')
        }.width('100%').height('100%').backgroundColor('#00CB87')

        Column() {
          Text('SwiperItem2')
        }.width('100%').height('100%').backgroundColor('#007DFF')

        Column() {
          Text('SwiperItem3')
        }.width('100%').height('100%').backgroundColor('#FFBF00')

        Column() {
          Text('SwiperItem4')
        }.width('100%').height('100%').backgroundColor('#E67C92')
      }
      .id('swiperId')
      .width(360)
      .height(300)
    }.width('100%')
  }
}
```

## removeGlobalGestureListener

```TypeScript
removeGlobalGestureListener(type: GestureListenerType, callback?: GestureListenerCallback): void
```

Unregisters the specified global gesture listener.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [GestureListenerType](arkts-arkui-arkui-uicontext-gesturelistenertype-e.md) | Yes | Event type. |
| callback | [GestureListenerCallback](arkts-arkui-gesturelistenercallback-t.md) | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for this gesture type. |

**Examples**

See the example for the [addGlobalGestureListener](#addglobalgesturelistener) API .
