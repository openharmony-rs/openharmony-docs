# AtomicServiceWeb

为开发者提供满足定制化诉求的Web高阶组件，屏蔽原生Web组件中无需关注的接口，并提供JS扩展能力。

> **说明：**
> 
> - 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceWeb, OnMessageEvent, OnErrorReceiveEvent, OnHttpErrorReceiveEvent, OnPageBeginEvent, OnPageEndEvent, AtomicServiceWebController, OnLoadInterceptEvent, OnProgressChangeEvent, OnLoadInterceptCallback, WebHeader } from '@kit.ArkUI';
```

## onLoadIntercept

```TypeScript
onLoadIntercept?: OnLoadInterceptCallback
```

当Web组件加载url之前触发该回调，用于判断是否阻止此次访问。默认允许加载。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: AtomicServiceWebController
```

通过AtomicServiceWebController可以控制AtomicServiceWeb组件各种行为。

**类型：** [AtomicServiceWebController](arkts-arkui-atomicservice-atomicserviceweb-atomicservicewebcontroller-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## darkMode

```TypeScript
darkMode?: WebDarkMode
```

设置Web深色模式，默认关闭。

**类型：** [WebDarkMode](../../apis-arkweb/arkts-components/arkts-arkweb-webdarkmode-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## forceDarkAccess

```TypeScript
forceDarkAccess?: boolean
```

设置网页是否开启强制深色模式。true表示设置网页开启强制深色模式，false表示设置网页不开启强制深色模式。默认值：false。 该属性仅在darkMode开启深色模式时生效。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mixedMode

```TypeScript
mixedMode?: MixedMode
```

设置是否允许加载超文本传输协议（HTTP）和超文本传输安全协议（HTTPS）混合内容，默认不允许加载HTTP和HTTPS混合内容。

**类型：** [MixedMode](../../apis-arkweb/arkts-components/arkts-arkweb-mixedmode-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navPathStack

```TypeScript
navPathStack?: NavPathStack
```

路由栈信息。当使用NavDestination作为页面的根容器时，需传入NavDestination容器对应的NavPathStack处理页面路由。默认值为空。

**类型：** [NavPathStack](../arkts-components/arkts-arkui-navpathstack-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## nestedScroll

```TypeScript
nestedScroll?: NestedScrollOptions | NestedScrollOptionsExt
```

设置嵌套滚动选项。nestedScroll为NestedScrollOptions（向前、向后两个方向）类型时， scrollForward、scrollBackward默认滚动选项为NestedScrollMode.SELF_FIRST。 nestedScroll为NestedScrollOptionsExt（上下左右四个方向）类型时， scrollUp、scrollDown、scrollLeft、scrollRight默认滚动选项为NestedScrollMode.SELF_FIRST。

**类型：** [NestedScrollOptions](../arkts-components/arkts-arkui-nestedscrolloptions-i.md) \| [NestedScrollOptionsExt](../../apis-arkweb/arkts-components/arkts-arkweb-nestedscrolloptionsext-i.md)

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onControllerAttached

```TypeScript
onControllerAttached?: Callback<void>
```

当Controller成功绑定到Web组件时触发该回调，此回调中不能使用操作网页的相关接口。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onErrorReceive

```TypeScript
onErrorReceive?: Callback<OnErrorReceiveEvent>
```

网页加载遇到错误时触发该回调。出于性能考虑，建议此回调中尽量执行简单逻辑。在无网络的情况下，触发此回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnErrorReceiveEvent](arkts-arkui-atomicservice-atomicserviceweb-onerrorreceiveevent-i.md)&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHttpErrorReceive

```TypeScript
onHttpErrorReceive?: Callback<OnHttpErrorReceiveEvent>
```

网页加载资源时遇到HTTP错误（响应码&gt;=400）触发该回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnHttpErrorReceiveEvent](arkts-arkui-atomicservice-atomicserviceweb-onhttperrorreceiveevent-i.md)&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMessage

```TypeScript
onMessage?: Callback<OnMessageEvent>
```

H5页面通过JS SDK的postMessage()发送消息后，Web组件对应的页面返回或销毁时，触发该回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnMessageEvent](arkts-arkui-atomicservice-atomicserviceweb-onmessageevent-i.md)&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPageBegin

```TypeScript
onPageBegin?: Callback<OnPageBeginEvent>
```

网页开始加载时触发该回调，且只在主frame触发，iframe或者frameset的内容加载时不会触发此回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnPageBeginEvent](arkts-arkui-atomicservice-atomicserviceweb-onpagebeginevent-i.md)&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPageEnd

```TypeScript
onPageEnd?: Callback<OnPageEndEvent>
```

网页加载完成时触发该回调，且只在主frame触发。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnPageEndEvent](arkts-arkui-atomicservice-atomicserviceweb-onpageendevent-i.md)&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onProgressChange

```TypeScript
onProgressChange?: Callback<OnProgressChangeEvent>
```

网页加载进度变化时触发该回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OnProgressChangeEvent](arkts-arkui-atomicservice-atomicserviceweb-onprogresschangeevent-i.md)&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

网页资源地址，访问网络资源需要在AGC（AppGallery Connect）配置业务域名，访问本地资源仅支持包内文件（\$rawfile）。 不支持通过状态变量（例如@State）动态更新地址。加载的网页中支持通过JS SDK提供的接口调用系统能力，具体以JS SDK为准。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
