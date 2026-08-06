# AtomicServiceWeb

为开发者提供满足定制化诉求的Web高阶组件，屏蔽原生Web组件中无需关注的接口，并提供JS扩展能力。 > **说明：** > > - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct AtomicServiceWeb--><!--Device-unnamed-export declare struct AtomicServiceWeb-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: AtomicServiceWebController
```

Sets the controller of the AtomicServiceWeb.

**类型：** AtomicServiceWebController

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @ObjectLink

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-controller: AtomicServiceWebController--><!--Device-AtomicServiceWeb-controller: AtomicServiceWebController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## darkMode

```TypeScript
darkMode?: WebDarkMode
```

Sets the dark mode of Web.

**类型：** WebDarkMode

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-darkMode?: WebDarkMode--><!--Device-AtomicServiceWeb-darkMode?: WebDarkMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## forceDarkAccess

```TypeScript
forceDarkAccess?: boolean
```

Sets whether to enable forced dark algorithm when the web is in dark mode.

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-forceDarkAccess?: boolean--><!--Device-AtomicServiceWeb-forceDarkAccess?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mixedMode

```TypeScript
mixedMode?: MixedMode
```

Sets how to load HTTP and HTTPS content.

**类型：** MixedMode

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-mixedMode?: MixedMode--><!--Device-AtomicServiceWeb-mixedMode?: MixedMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navPathStack

```TypeScript
navPathStack?: NavPathStack
```

The navPathStack to control page route in Navigation and NavDestination.

**类型：** NavPathStack

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-navPathStack?: NavPathStack--><!--Device-AtomicServiceWeb-navPathStack?: NavPathStack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## nestedScroll

```TypeScript
nestedScroll?: NestedScrollOptions | NestedScrollOptionsExt
```

设置嵌套滚动选项。

**类型：** NestedScrollOptions \| NestedScrollOptionsExt

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-nestedScroll?: NestedScrollOptions | NestedScrollOptionsExt--><!--Device-AtomicServiceWeb-nestedScroll?: NestedScrollOptions | NestedScrollOptionsExt-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onControllerAttached

```TypeScript
onControllerAttached?: Callback<void>
```

Triggered when The controller is bound to the web component, this controller must be a WebviewController. This callback can not use the interface about manipulating web pages.

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-onControllerAttached?: Callback<void>--><!--Device-AtomicServiceWeb-onControllerAttached?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onErrorReceive

```TypeScript
onErrorReceive?: Callback<OnErrorReceiveEvent>
```

Triggered when the web page receives a web resource loading error.

**类型：** Callback&lt;OnErrorReceiveEvent&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-onErrorReceive?: Callback<OnErrorReceiveEvent>--><!--Device-AtomicServiceWeb-onErrorReceive?: Callback<OnErrorReceiveEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHttpErrorReceive

```TypeScript
onHttpErrorReceive?: Callback<OnHttpErrorReceiveEvent>
```

Triggered when the web page receives a web resource loading HTTP error.

**类型：** Callback&lt;OnHttpErrorReceiveEvent&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-onHttpErrorReceive?: Callback<OnHttpErrorReceiveEvent>--><!--Device-AtomicServiceWeb-onHttpErrorReceive?: Callback<OnHttpErrorReceiveEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onLoadIntercept

```TypeScript
onLoadIntercept?: OnLoadInterceptCallback
```

Triggered when the resources loading is intercepted.

**类型：** OnLoadInterceptCallback

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-onLoadIntercept?: OnLoadInterceptCallback--><!--Device-AtomicServiceWeb-onLoadIntercept?: OnLoadInterceptCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMessage

```TypeScript
onMessage?: Callback<OnMessageEvent>
```

The callback method to invoke after page is back or destroyed if postMessage() is called in H5 page.

**类型：** Callback&lt;OnMessageEvent&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-onMessage?: Callback<OnMessageEvent>--><!--Device-AtomicServiceWeb-onMessage?: Callback<OnMessageEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPageBegin

```TypeScript
onPageBegin?: Callback<OnPageBeginEvent>
```

Triggered at the begin of web page loading.

**类型：** Callback&lt;OnPageBeginEvent&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-onPageBegin?: Callback<OnPageBeginEvent>--><!--Device-AtomicServiceWeb-onPageBegin?: Callback<OnPageBeginEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPageEnd

```TypeScript
onPageEnd?: Callback<OnPageEndEvent>
```

Triggered at the end of web page loading.

**类型：** Callback&lt;OnPageEndEvent&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-onPageEnd?: Callback<OnPageEndEvent>--><!--Device-AtomicServiceWeb-onPageEnd?: Callback<OnPageEndEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onProgressChange

```TypeScript
onProgressChange?: Callback<OnProgressChangeEvent>
```

Triggered when the page loading progress changes.

**类型：** Callback&lt;OnProgressChangeEvent&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-onProgressChange?: Callback<OnProgressChangeEvent>--><!--Device-AtomicServiceWeb-onProgressChange?: Callback<OnProgressChangeEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

The address of the web page to be displayed.

**类型：** ResourceStr

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceWeb-src: ResourceStr--><!--Device-AtomicServiceWeb-src: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

