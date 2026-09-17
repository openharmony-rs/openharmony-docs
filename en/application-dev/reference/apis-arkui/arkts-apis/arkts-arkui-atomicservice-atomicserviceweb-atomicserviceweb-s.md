# AtomicServiceWeb

**AtomicServiceWeb** is an advanced web component offering customization to meet specific demands. It shields irrelevant APIs from the native **Web** component and extends functionality through JavaScript capabilities.

> **NOTE:** 
> 
> - You can preview how this component looks on a real device, but not in DevEco Studio Previewer.

**Since:** 12

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceWeb, OnMessageEvent, OnErrorReceiveEvent, OnHttpErrorReceiveEvent, OnPageBeginEvent, OnPageEndEvent, AtomicServiceWebController, OnLoadInterceptEvent, OnProgressChangeEvent, OnLoadInterceptCallback, WebHeader } from '@kit.ArkUI';
```

## onLoadIntercept

```TypeScript
onLoadIntercept?: OnLoadInterceptCallback
```

Triggered when the resources loading is intercepted.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: AtomicServiceWebController
```

Sets the controller of the AtomicServiceWeb.

**Type:** [AtomicServiceWebController](arkts-arkui-atomicservice-atomicserviceweb-atomicservicewebcontroller-c.md)

**Since:** 12

**Decorator:** @ObjectLink

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## darkMode

```TypeScript
darkMode?: WebDarkMode
```

Sets the dark mode of Web.

**Type:** [WebDarkMode](../../apis-arkweb/arkts-components/arkts-arkweb-webdarkmode-e.md)

**Since:** 12

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## forceDarkAccess

```TypeScript
forceDarkAccess?: boolean
```

Sets whether to enable forced dark algorithm when the web is in dark mode.

**Type:** boolean

**Since:** 12

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mixedMode

```TypeScript
mixedMode?: MixedMode
```

Sets how to load HTTP and HTTPS content.

**Type:** [MixedMode](../../apis-arkweb/arkts-components/arkts-arkweb-mixedmode-e.md)

**Since:** 12

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## navPathStack

```TypeScript
navPathStack?: NavPathStack
```

The navPathStack to control page route in Navigation and NavDestination.

**Type:** [NavPathStack](../arkts-components/arkts-arkui-navpathstack-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## nestedScroll

```TypeScript
nestedScroll?: NestedScrollOptions | NestedScrollOptionsExt
```

Sets the nested scroll options.

**Type:** [NestedScrollOptions](../arkts-components/arkts-arkui-nestedscrolloptions-i.md) &#124; [NestedScrollOptionsExt](../../apis-arkweb/arkts-components/arkts-arkweb-nestedscrolloptionsext-i.md)

**Since:** 15

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onControllerAttached

```TypeScript
onControllerAttached?: Callback<void>
```

Triggered when The controller is bound to the web component, this controller must be a WebviewController. This callback can not use the interface about manipulating web pages.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onErrorReceive

```TypeScript
onErrorReceive?: Callback<OnErrorReceiveEvent>
```

Triggered when the web page receives a web resource loading error.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnErrorReceiveEvent](arkts-arkui-atomicservice-atomicserviceweb-onerrorreceiveevent-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onHttpErrorReceive

```TypeScript
onHttpErrorReceive?: Callback<OnHttpErrorReceiveEvent>
```

Triggered when the web page receives a web resource loading HTTP error.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnHttpErrorReceiveEvent](arkts-arkui-atomicservice-atomicserviceweb-onhttperrorreceiveevent-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onMessage

```TypeScript
onMessage?: Callback<OnMessageEvent>
```

The callback method to invoke after page is back or destroyed if postMessage() is called in H5 page.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnMessageEvent](arkts-arkui-atomicservice-atomicserviceweb-onmessageevent-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onPageBegin

```TypeScript
onPageBegin?: Callback<OnPageBeginEvent>
```

Triggered at the begin of web page loading.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnPageBeginEvent](arkts-arkui-atomicservice-atomicserviceweb-onpagebeginevent-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onPageEnd

```TypeScript
onPageEnd?: Callback<OnPageEndEvent>
```

Triggered at the end of web page loading.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnPageEndEvent](arkts-arkui-atomicservice-atomicserviceweb-onpageendevent-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onProgressChange

```TypeScript
onProgressChange?: Callback<OnProgressChangeEvent>
```

Triggered when the page loading progress changes.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnProgressChangeEvent](arkts-arkui-atomicservice-atomicserviceweb-onprogresschangeevent-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

The address of the web page to be displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
