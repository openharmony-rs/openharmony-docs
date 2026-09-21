# off

## Modules to Import

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## off('navDestinationUpdate')

```TypeScript
export function off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<NavDestinationInfo>): void
```

Unsubscribes from status changes of the **NavDestination** component. Compared with [uiObserver.off](#offnavdestinationupdate), this API supports the **options** parameter, which enables you to specify the ID of the target **Navigation** component to observe.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | Yes | Event type. Set to **'navDestinationUpdate'** for **NavDestination** component status change events. |
| options | { navigationId: ResourceStr } | Yes | ID of the target **Navigation** component. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md)&gt; | No | Callback used to return the result. It provides the current state of the **NavDestination** component. |


## off('navDestinationUpdate')

```TypeScript
export function off(type: 'navDestinationUpdate', callback?: Callback<NavDestinationInfo>): void
```

Unsubscribes from status changes of the **NavDestination** component.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | Yes | Event type. Set to **'navDestinationUpdate'** for **NavDestination** component status change events. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md)&gt; | No | Callback used to return the result. It provides the current state of the **NavDestination** component. |


## off('scrollEvent')

```TypeScript
export function off(type: 'scrollEvent', options: ObserverOptions, callback?: Callback<ScrollEventInfo>): void
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
| options | [ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type and scroll ID will be removed. |

**Examples**

```TypeScript
import { uiObserver } from '@kit.ArkUI'

@Entry
@Component
struct Index {
  scroller: Scroller = new Scroller();
  options: uiObserver.ObserverOptions = { id: 'testId' };
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7]

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
            // Register a listener.
            uiObserver.on('scrollEvent', (info) => {
              console.info(`scrollEventInfo ${JSON.stringify(info)}`);
            });
          })
        Button('UIObserver off')
          .onClick(() => {
            // Unregister the listener.
            uiObserver.off('scrollEvent');
          })
      }

      Row() {
        Button('UIObserverWithId on')
          .onClick(() => {
            // Register a listener with the specified component ID.
            uiObserver.on('scrollEvent', this.options, (info) => {
              console.info(`scrollEventInfo ${JSON.stringify(info)}`);
            });
          })
        Button('UIObserverWithId off')
          .onClick(() => {
            // Unregister the listener.
            uiObserver.off('scrollEvent',this.options);
          })
      }
    }
    .height('100%')
  }
}
```


## off('scrollEvent')

```TypeScript
export function off(type: 'scrollEvent', callback?: Callback<ScrollEventInfo>): void
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
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | No | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |


## off('routerPageUpdate')

```TypeScript
export function off(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback?: Callback<RouterPageInfo>): void
```

Unsubscribes from state changes of the page during routing.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | Yes | Event type. The value is fixed at **'routerPageUpdate'**, which indicates the state change event of the page during routing. |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) &#124; UIContext | Yes | Context information, which is used to specify the target page scope. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RouterPageInfo](arkts-arkui-uiobserver-routerpageinfo-c.md)&gt; | No | Target listener to unregister. |

**Examples**

```TypeScript
// used in UIAbility
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { uiObserver, UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // Before actual use, uiContext must be assigned a value. For details, see the example for uiObserver.on('routerPageUpdate').
  private uiContext: UIContext | null = null;

  onDestroy(): void {
    // Unregister all callbacks for the routerPageUpdate event under the current ability context.
    uiObserver.off('routerPageUpdate', this.context)
  }

  onWindowStageDestroy(): void {
    // Unregister all callbacks for the routerPageUpdate event under the UI context.
    if (this.uiContext) {
      uiObserver.off('routerPageUpdate', this.uiContext);
    }
  }

  // ... other function in EntryAbility
}
```


## off('densityUpdate')

```TypeScript
export function off(type: 'densityUpdate', context: UIContext, callback?: Callback<DensityInfo>): void
```

Unregisters the listener for screen pixel density changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'densityUpdate' | Yes | Event type. Set to **'densityUpdate'** for screen pixel density change events. |
| context | UIContext | Yes | Context information, which is used to specify the target page scope. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md)&gt; | No | Target listener to unregister. If no parameter is provided, all listeners for the **densityUpdate** event under the current UI context are unregistered. |


## off('willDraw')

```TypeScript
export function off(type: 'willDraw', context: UIContext, callback?: Callback<void>): void
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
| context | UIContext | Yes | Context information, which is used to specify the target page scope. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Target listener to unregister. |


## off('didLayout')

```TypeScript
export function off(type: 'didLayout', context: UIContext, callback?: Callback<void>): void
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
| context | UIContext | Yes | Context information, which is used to specify the target page scope. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Target listener to unregister. |


## off('tabContentUpdate')

```TypeScript
export function off(type: 'tabContentUpdate', options: ObserverOptions, callback?: Callback<TabContentInfo>): void
```

Unsubscribes from **TabContent** page switching events for the specified **Tabs** component identified by its ID.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | Yes | Event type. Set to **'tabContentUpdate'** for **TabContent** page switching events. |
| options | [ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | Yes | ID of the target **Tabs** component. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | No | Target listener to unregister. |


## off('tabContentUpdate')

```TypeScript
export function off(type: 'tabContentUpdate', callback?: Callback<TabContentInfo>): void
```

Unsubscribes from the **TabContent** switching event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | Yes | Event type. Set to **'tabContentUpdate'** for **TabContent** page switching events. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | No | Target listener to unregister. |


## off('navDestinationSwitch')

```TypeScript
export function off(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    callback?: Callback<NavDestinationSwitchInfo>
  ): void
```

Unsubscribes from **Navigation** component page switching events.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | Yes | Event type. Set to **'navDestinationSwitch'** for **Navigation** component page switching events. |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) &#124; UIContext | Yes | Context information, which is used to specify the target scope for page switching events. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | No | Target listener to unregister. |


## off('navDestinationSwitch')

```TypeScript
export function off(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    observerOptions: NavDestinationSwitchObserverOptions,
    callback?: Callback<NavDestinationSwitchInfo>
  ): void
```

Unsubscribes from **Navigation** component page switching events. Compared with [uiObserver.off](#offnavdestinationswitch), this API supports the **observerOptions** parameter, which enables you to configure observation options.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | Yes | Event type. Set to **'navDestinationSwitch'** for **Navigation** component page switching events. |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) &#124; UIContext | Yes | Context information, which is used to specify the target scope for page switching events. |
| observerOptions | [NavDestinationSwitchObserverOptions](arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | Yes | Observer configuration options. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | No | Target listener to unregister. |
