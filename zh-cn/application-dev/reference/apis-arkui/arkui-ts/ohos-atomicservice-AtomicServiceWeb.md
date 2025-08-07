# AtomicServiceWeb
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @txazo-->
<!--SE: @autojuan-->
<!--TSE: @sunfei2021; @youzhi92-->

为开发者提供满足定制化诉求的Web高阶组件，屏蔽原生Web组件中无需关注的接口，并提供JS扩展能力。

> **说明：**
>
> - 该组件从API Version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## 需要权限

访问在线网页时需添加网络权限：ohos.permission.INTERNET，具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。

## 导入模块

```
import { AtomicServiceWeb } from '@kit.ArkUI';
```

## 子组件

无

## 属性

不支持[通用属性](ts-component-general-attributes.md)

## AtomicServiceWeb

```
AtomicServiceWeb({
  src: ResourceStr,
  controller: AtomicServiceWebController,
  navPathStack?: NavPathStack,
  mixedMode?: MixedMode,
  darkMode?: WebDarkMode,
  forceDarkAccess?: boolean,
  nestedScroll?: NestedScrollOptions | NestedScrollOptionsExt,
  onMessage?: Callback<OnMessageEvent>,
  onErrorReceive?: Callback<OnErrorReceiveEvent>,
  onHttpErrorReceive?: Callback<OnHttpErrorReceiveEvent>,
  onPageBegin?: Callback<OnPageBeginEvent>,
  onPageEnd?: Callback<OnPageEndEvent>,
  onControllerAttached?: Callback<void>,
  onLoadIntercept?: Callback<OnLoadInterceptEvent, boolean>,
  onProgressChange?: Callback<OnProgressChangeEvent>
})
```

**装饰器类型：**@Component

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数**：

| 名称                   | 类型                                                                                                               | 必填 | 装饰器类型       | 说明                                                                                                                  |
|----------------------|------------------------------------------------------------------------------------------------------------------|----|-------------|----------------------------------------------------------------------------------------------------------------------|
| src                  | [ResourceStr](ts-types.md#resourcestr)                                                                           | 是  | -           | 网页资源地址，访问网络资源需要在AGC配置业务域名，访问本地资源仅支持包内文件（$rawfile）。不支持通过状态变量（例如@State）动态更新地址。加载的网页中支持通过JS SDK提供的接口调用系统能力，具体以JS SDK为准。 |
| controller           | [AtomicServiceWebController](#atomicservicewebcontroller)                                                        | 是  | @ObjectLink | 通过AtomicServiceWebController可以控制AtomicServiceWeb组件各种行为。                                                              |
| navPathStack         | [NavPathStack](ts-basic-components-navigation.md#navpathstack10)                                                 | 否  | -           | 路由栈信息。当使用NavDestination作为页面的根容器时，需传入NavDestination容器对应的NavPathStack处理页面路由。                                           |
| mixedMode            | [MixedMode](../../apis-arkweb/arkts-basic-components-web-e.md#mixedmode)                                          | 否  | @Prop       | 设置是否允许加载超文本传输协议（HTTP）和超文本传输安全协议（HTTPS）混合内容，默认不允许加载HTTP和HTTPS混合内容。                                                    |
| darkMode             | [WebDarkMode](../../apis-arkweb/arkts-basic-components-web-e.md#webdarkmode9)                                     | 否  | @Prop       | 设置Web深色模式，默认关闭。                                                                                                      |
| forceDarkAccess      | boolean                                                                                                          | 否  | @Prop       | 设置网页是否开启强制深色模式。true表示设置网页开启强制深色模式，false表示设置网页不开启强制深色模式。默认值：false。该属性仅在darkMode开启深色模式时生效。                                                                          |
| nestedScroll<sup>15+</sup>      | [NestedScrollOptions](../../apis-arkui/arkui-ts/ts-container-scrollable-common.md#nestedscrolloptions10对象说明) \| [NestedScrollOptionsExt](../../apis-arkweb/arkts-basic-components-web-i.md#nestedscrolloptionsext14) | 否  | @Prop       | 设置嵌套滚动选项。<br>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。                                                                              |
| onMessage            | Callback\<[OnMessageEvent](#onmessageevent)\>                                                                    | 否  | -           | H5页面通过JS SDK的postMessage()发送消息后，Web组件对应的页面返回或销毁时，触发该回调。                                                              |
| onErrorReceive       | Callback\<[OnErrorReceiveEvent](#onerrorreceiveevent)\>                                                          | 否  | -           | 网页加载遇到错误时触发该回调。出于性能考虑，建议此回调中尽量执行简单逻辑。在无网络的情况下，触发此回调。                                                                 |
| onHttpErrorReceive   | Callback\<[OnHttpErrorReceiveEvent](#onhttperrorreceiveevent)\>                                                  | 否  | -           | 网页加载资源遇到的HTTP错误（响应码>=400)时触发该回调。                                                                                     |
| onPageBegin          | Callback\<[OnPageBeginEvent](#onpagebeginevent)\>                                                                | 否  | -           | 网页开始加载时触发该回调，且只在主frame触发，iframe或者frameset的内容加载时不会触发此回调。                                                              |
| onPageEnd            | Callback\<[OnPageEndEvent](#onpageendevent)\>                                                                    | 否  | -           | 网页加载完成时触发该回调，且只在主frame触发。                                                                                            |
| onControllerAttached | Callback\<void\>                                                                                                 | 否  | -           | 当Controller成功绑定到Web组件时触发该回调。                                                                                         |
| onLoadIntercept      | [OnLoadInterceptCallback](#onloadinterceptcallback) | 否  | -  | 当Web组件加载url之前触发该回调，用于判断是否阻止此次访问。默认允许加载。                                                                              |
| onProgressChange     | Callback\<[OnProgressChangeEvent](../../apis-arkweb/arkts-basic-components-web-i.md#onprogresschangeevent12)\>        | 否  | -           | 网页加载进度变化时触发该回调。                                                                                                      |

## AtomicServiceWebController

通过AtomicServiceWebController可以控制AtomicServiceWeb组件各种行为。一个AtomicServiceWebController对象只能控制一个AtomicServiceWeb组件，且必须在AtomicServiceWeb组件和AtomicServiceWebController绑定后，才能调用AtomicServiceWebController上的方法。

**装饰器类型：** @Observed

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### getUserAgent

getUserAgent(): string

获取当前默认用户代理。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型     | 说明      |
|--------|---------|
| string | 默认用户代理。默认User-Agent定义与使用场景请参考[User-Agent开发指导](../../../web/web-default-userAgent.md)。 |

**错误码：**

以下错误码的详细介绍请参见[错误码](../../apis-arkweb/errorcode-webview.md)。

| 错误码ID    | 错误信息                                                                                             |
|----------|--------------------------------------------------------------------------------------------------|
| 17100001 | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

### getCustomUserAgent

getCustomUserAgent(): string

获取自定义用户代理。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型     | 说明         |
|--------|------------|
| string | 用户自定义代理信息。默认User-Agent定义与使用场景请参考[User-Agent开发指导](../../../web/web-default-userAgent.md)。 |

**错误码：**

以下错误码的详细介绍请参见[错误码](../../apis-arkweb/errorcode-webview.md).

| 错误码ID    | 错误信息                                                                                             |
|----------|--------------------------------------------------------------------------------------------------|
| 17100001 | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

### setCustomUserAgent

setCustomUserAgent(userAgent: string): void

设置自定义用户代理，会覆盖系统的用户代理。

建议在onControllerAttached回调事件中设置User-Agent，设置方式请参考示例。不建议将User-Agent设置在onLoadIntercept回调事件中，会概率性出现设置失败。

> **说明：**
>
>当Web组件src设置了url，且未在onControllerAttached回调事件中设置User-Agent。再调用setCustomUserAgent方法时，可能会出现加载的页面与实际设置User-Agent不符的异常现象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名       | 类型     | 必填 | 说明                                                                       |
|-----------|--------|----|--------------------------------------------------------------------------|
| userAgent | string | 是  | 用户自定义代理信息。建议先使用[getUserAgent](#getuseragent)获取当前默认用户代理，在此基础上追加自定义用户代理信息。 |

**错误码：**

以下错误码的详细介绍请参见[错误码](../../apis-arkweb/errorcode-webview.md).

| 错误码ID    | 错误信息                                                                                             |
|----------|--------------------------------------------------------------------------------------------------|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 17100001 | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

### refresh

refresh(): void

调用此接口通知AtomicServiceWeb组件刷新网页。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

以下错误码的详细介绍请参见[错误码](../../apis-arkweb/errorcode-webview.md).

| 错误码ID    | 错误信息                                                                                             |
|----------|--------------------------------------------------------------------------------------------------|
| 17100001 | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

### forward

forward(): void

按照历史栈，前进一个页面。一般结合[accessForward](#accessforward)一起使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

以下错误码的详细介绍请参见[错误码](../../apis-arkweb/errorcode-webview.md).

| 错误码ID    | 错误信息                                                                                             |
|----------|--------------------------------------------------------------------------------------------------|
| 17100001 | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

### backward

backward(): void

按照历史栈，后退一个页面。一般结合[accessBackward](#accessbackward)一起使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

以下错误码的详细介绍请参见[错误码](../../apis-arkweb/errorcode-webview.md).

| 错误码ID    | 错误信息                                                                                             |
|----------|--------------------------------------------------------------------------------------------------|
| 17100001 | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

### accessForward

accessForward(): boolean

当前页面是否可前进，即当前页面是否有前进历史记录。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型      | 说明                    |
|---------|-----------------------|
| boolean | 可以前进返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[错误码](../../apis-arkweb/errorcode-webview.md).

| 错误码ID    | 错误信息                                                                                             |
|----------|--------------------------------------------------------------------------------------------------|
| 17100001 | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

### accessBackward

accessBackward(): boolean

当前页面是否可后退，即当前页面是否有返回历史记录。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型      | 说明                    |
|---------|-----------------------|
| boolean | 可以后退返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[错误码](../../apis-arkweb/errorcode-webview.md).

| 错误码ID    | 错误信息                                                                                             |
|----------|--------------------------------------------------------------------------------------------------|
| 17100001 | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

### accessStep

accessStep(step: number): boolean

当前页面是否可前进或者后退给定的step步。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填 | 说明                    |
|------|--------|----|-----------------------|
| step | number | 是  | 要跳转的步数，正数代表前进，负数代表后退。 |

**返回值：**

| 类型      | 说明        |
|---------|-----------|
| boolean | 页面是否可前进或者后退给定的step步。返回true表示可以前进或者后退，返回false表示不可以前进或后退。 |

**错误码：**

以下错误码的详细介绍请参见[错误码](../../apis-arkweb/errorcode-webview.md).

| 错误码ID    | 错误信息                                                                                             |
|----------|--------------------------------------------------------------------------------------------------|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 17100001 | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

### loadUrl

loadUrl(url: string | Resource, headers?: Array\<WebHeader>): void

加载指定的URL。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                              | 必填 | 说明             |
|---------|---------------------------------|----|:---------------|
| url     | string \| [Resource](../../apis-arkui/arkui-ts/ts-types.md#resource)               | 是  | 需要加载的 URL。     |
| headers | Array\<[WebHeader](#webheader)> | 否  | URL的附加HTTP请求头。 |

**错误码：**

以下错误码的详细介绍请参见[错误码](../../apis-arkweb/errorcode-webview.md).

| 错误码ID    | 错误信息                                                                                             |
|----------|--------------------------------------------------------------------------------------------------|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 17100001 | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |
| 17100002 | Invalid url.                                                                                     |
| 17100003 | Invalid resource path or file type.                                                              |

## WebHeader

Web组件返回的请求/响应头对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称          | 类型     | 只读 | 可选 | 说明            |
|-------------|--------|----|----|---------------|
| headerKey   | string | 否  | 否  | 请求/响应头的key。   |
| headerValue | string | 否  | 否  | 请求/响应头的value。 |

## OnMessageEvent

定义页面回退或销毁时触发该回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型       | 必填 | 说明    |
|------|----------|----|-------|
| data | object[] | 是  | 消息列表。 |

## OnErrorReceiveEvent

定义网页加载遇到错误时触发该回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 类型                                                                                    | 必填 | 说明              |
|---------|---------------------------------------------------------------------------------------|----|-----------------|
| request | [WebResourceRequest](../../apis-arkweb/arkts-basic-components-web-WebResourceRequest.md) | 是  | 网页请求的封装信息。      |
| error   | [WebResourceError](../../apis-arkweb/arkts-basic-components-web-WebResourceError.md)     | 是  | 网页加载资源错误的封装信息 。 |

## OnHttpErrorReceiveEvent

定义网页收到加载资源加载HTTP错误时触发。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称       | 类型                                                                                      | 必填 | 说明         |
|----------|-----------------------------------------------------------------------------------------|----|------------|
| request  | [WebResourceRequest](../../apis-arkweb/arkts-basic-components-web-WebResourceRequest.md)   | 是  | 网页请求的封装信息。 |
| response | [WebResourceResponse](../../apis-arkweb/arkts-basic-components-web-WebResourceResponse.md) | 是  | 资源响应的封装信息。 |

## OnPageBeginEvent

定义网页加载开始时触发的函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称  | 类型     | 必填 | 说明        |
|-----|--------|----|-----------|
| url | string | 是  | 页面的URL地址。 |

## OnPageEndEvent

定义网页加载结束时触发的函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称  | 类型     | 必填 | 说明        |
|-----|--------|----|-----------|
| url | string | 是  | 页面的URL地址。 |

## OnLoadInterceptEvent

当资源加载被拦截时，加载拦截事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称             | 类型      | 必填   | 说明                                       |
| -------------- | ---- | ---- | ---------------------------------------- |
| data | [WebResourceRequest](../../apis-arkweb/arkts-basic-components-web-WebResourceRequest.md) | 是 | 网页请求的封装信息。 |

## OnProgressChangeEvent

定义网页加载进度变化时触发该回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称             | 类型      | 必填   | 说明                                       |
| -------------- | ---- | ---- | ---------------------------------------- |
| newProgress | number | 是 | 新的加载进度，取值范围为0到100的整数。                       |

## OnLoadInterceptCallback

type OnLoadInterceptCallback = (event: OnLoadInterceptEvent) => boolean

资源加载被拦截时触发该回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填 | 说明                    |
|------|--------|----|-----------------------|
| event | OnLoadInterceptEvent | 是  | 当资源加载被拦截时，加载拦截事件。 |

**返回值：**

| 类型      | 说明        |
|---------|-----------|
| boolean | 返回资源是否被拦截 |

## 事件

不支持[通用事件](ts-component-general-events.md)

## 示例

### 示例1

加载本地网页。

```ts
// xxx.ets
import { AtomicServiceWeb, AtomicServiceWebController } from '@kit.ArkUI';

@Entry
@Component
struct WebComponent {
  @State controller: AtomicServiceWebController = new AtomicServiceWebController();
  
  build() {
    Column() {
      AtomicServiceWeb({ src: $rawfile("index.html"), controller: this.controller })
    }
  }
}
```

### 示例2

加载在线网页。

```ts
// xxx.ets
import { AtomicServiceWeb, AtomicServiceWebController } from '@kit.ArkUI';

@Entry
@Component
struct WebComponent {
    @State controller: AtomicServiceWebController = new AtomicServiceWebController();

    build() {
        Column() {
            AtomicServiceWeb({ src: 'https://www.example.com', controller: this.controller })
        }
    }
}
```

### 示例3

NavDestination容器中加载网页。

```ts
// xxx.ets
import { AtomicServiceWeb, AtomicServiceWebController } from '@kit.ArkUI';

@Builder
export function WebComponentBuilder(name: string, param: Object) {
  WebComponent()
}

@Component
struct WebComponent {
  navPathStack: NavPathStack = new NavPathStack();
  @State controller: AtomicServiceWebController = new AtomicServiceWebController();

  build() {
    NavDestination() {
      AtomicServiceWeb({ src: $rawfile("index.html"), controller: this.controller, navPathStack: this.navPathStack })
    }
    .onReady((context: NavDestinationContext) => {
      this.navPathStack = context.pathStack;
    })
  }
}
```

### 示例4

设置onMessage()事件回调。

```ts
// xxx.ets
import { AtomicServiceWeb, AtomicServiceWebController, OnMessageEvent } from '@kit.ArkUI';

@Entry
@Component
struct WebComponent {
  @State controller: AtomicServiceWebController = new AtomicServiceWebController();

  build() {
    Column() {
      AtomicServiceWeb({
        src: $rawfile("index.html"),
        controller: this.controller,
        // H5页面点击“发送消息”后，再点击“返回上一页”，触发该回调
        onMessage: (event: OnMessageEvent) => {
          console.info(`[AtomicServiceWebLog] onMessage data = ${JSON.stringify(event.data)}`);
        }
      })
    }
  }
}
```

```html
// index.html
<!DOCTYPE html>
<html>
<meta charset="utf-8">
<!-- 引入JS SDK文件 -->
<script src="../js/atomicservice-sdk.js" type="text/javascript"></script>
<body>
<h1>JS SDK - postMessage()</h1>
<br/>
<button type="button" onclick="postMessage({ name: 'Jerry', age: 18 });">发送消息</button>
<br/>
<button type="button" onclick="back();">返回上一页</button>
</body>
<script type="text/javascript">
    function postMessage(data) {
        // JS SDK提供的发送消息接口
        has.asWeb.postMessage({
            data: data,
            callback: (err, res) => {
                if (err) {
                    console.error(`[AtomicServiceWebLog H5] postMessage error err. Code: ${err.code}, message: ${err.message}`);
                } else {
                    console.info(`[AtomicServiceWebLog H5] postMessage success res = ${JSON.stringify(res)}`);
                }
            }
        });
    }

    function back() {
        // JS SDK提供的Router路由回退接口
        has.router.back({
            delta: 1
        });
    }
</script>
</html>
```

### 示例5

设置网页加载事件回调。

```ts
// xxx.ets
import {
  AtomicServiceWeb,
  AtomicServiceWebController,
  OnErrorReceiveEvent,
  OnHttpErrorReceiveEvent,
  OnPageBeginEvent,
  OnPageEndEvent
} from '@kit.ArkUI';

@Entry
@Component
struct WebComponent {
  @State controller: AtomicServiceWebController = new AtomicServiceWebController();

  build() {
    Column() {
      AtomicServiceWeb({
        src: $rawfile('index.html'),
        controller: this.controller,
        // 网页加载遇到错误时触发该回调
        onErrorReceive: (event: OnErrorReceiveEvent) => {
          console.info(`AtomicServiceWebLog onErrorReceive event = ${JSON.stringify({
            requestUrl: event.request?.getRequestUrl(),
            requestMethod: event.request?.getRequestMethod(),
            errorCode: event.error?.getErrorCode(),
            errorInfo: event.error?.getErrorInfo()
          })}`);
        },
        // 网页加载遇到HTTP资源加载错误时触发该回调
        onHttpErrorReceive: (event: OnHttpErrorReceiveEvent) => {
          console.info(`AtomicServiceWebLog onHttpErrorReceive event = ${JSON.stringify({
            requestUrl: event.request?.getRequestUrl(),
            requestMethod: event.request?.getRequestMethod(),
            responseCode: event.response?.getResponseCode(),
            responseData: event.response?.getResponseData(),
          })}`);
        },
        // 页面开始加载，触发该回调
        onPageBegin: (event: OnPageBeginEvent) => {
          console.info(`AtomicServiceWebLog onPageBegin event = ${JSON.stringify({
            url: event.url
          })}`);
        },
        // 页面加载完成，触发该回调
        onPageEnd: (event: OnPageEndEvent) => {
          console.info(`AtomicServiceWebLog onPageEnd event = ${JSON.stringify({
            url: event.url
          })}`);
        }
      })
    }
  }
}
```

### 示例6

AtomicServiceWeb跟AtomicServiceWebController的使用示例。

```ts
// xxx.ets
import {
  AtomicServiceWeb,
  AtomicServiceWebController,
  OnErrorReceiveEvent,
  OnHttpErrorReceiveEvent,
  OnPageBeginEvent,
  OnPageEndEvent,
  OnMessageEvent,
  OnLoadInterceptEvent,
  OnProgressChangeEvent
} from '@kit.ArkUI';

@Entry
@Component
struct WebComponent {
  @State darkMode: WebDarkMode = WebDarkMode.On;
  @State forceDarkAccess: boolean = true;
  @State mixedMode: MixedMode = MixedMode.None;
  @State controller: AtomicServiceWebController = new AtomicServiceWebController();
  @State num: number = 1;

  build() {
    Column() {
      Button('accessForward').onClick(() => {
        console.info(`AtomicServiceWebLog accessForward = ${this.controller.accessForward()}`);
      })
      Button('accessBackward').onClick(() => {
        console.info(`AtomicServiceWebLog accessBackward = ${this.controller.accessBackward()}`);
      })
      Button('accessStep').onClick(() => {
        console.info(`AtomicServiceWebLog accessStep = ${this.controller.accessStep(1)}`);
      })
      Button('forward').onClick(() => {
        console.info(`AtomicServiceWebLog forward = ${this.controller.forward()}`);
      })
      Button('backward').onClick(() => {
        console.info(`AtomicServiceWebLog backward = ${this.controller.backward()}`);
      })
      Button('refresh').onClick(() => {
        console.info(`AtomicServiceWebLog refresh = ${this.controller.refresh()}`);
      })
      Button('loadUrl').onClick(() => {
        console.info(`AtomicServiceWebLog loadUrl = ${this.controller.loadUrl('https://www.baidu.com/')}`);
      })
      Button('深色模式').onClick(() => {
        this.forceDarkAccess = !this.forceDarkAccess;
      })
      Button('mixedMode').onClick(() => {
        this.mixedMode = this.mixedMode == MixedMode.None ? MixedMode.All : MixedMode.None;
      })
      Button('点击').onClick(() => {
        console.info(`AtomicServiceWebLog getUserAgent = ${this.controller.getUserAgent()}`);
        console.info(`AtomicServiceWebLog getCustomUserAgent = ${this.controller.getCustomUserAgent()}`);
        this.controller.setCustomUserAgent('test' + this.num++);

        console.info(`AtomicServiceWebLog getUserAgent after set = ${this.controller.getUserAgent()}`);
        console.info(`AtomicServiceWebLog getCustomUserAgent after set = ${this.controller.getCustomUserAgent()}`);
      })
      AtomicServiceWeb({
        src: 'https://www.example.com',
        mixedMode: this.mixedMode,
        darkMode: this.darkMode,
        forceDarkAccess: this.forceDarkAccess,
        controller: this.controller,
        onControllerAttached: () => {
          console.info("AtomicServiceWebLog onControllerAttached call back success");
        },
        onLoadIntercept: (event: OnLoadInterceptEvent) => {
          console.info("AtomicServiceWebLog onLoadIntercept call back success " + JSON.stringify({
            getRequestUrl: event.data.getRequestUrl(),
            getRequestMethod: event.data.getRequestMethod(),
            getRequestHeader: event.data.getRequestHeader(),
            isRequestGesture: event.data.isRequestGesture(),
            isMainFrame: event.data.isMainFrame(),
            isRedirect: event.data.isRedirect(),
          }))
          return false;
        },
        onProgressChange: (event: OnProgressChangeEvent) => {
          console.info("AtomicServiceWebLog onProgressChange call back success " + JSON.stringify(event));
        },
        onMessage: (event: OnMessageEvent) => {
          console.info("onMessage call back success " + JSON.stringify(event));
        },
        onPageBegin: (event: OnPageBeginEvent) => {
          console.info("onPageBegin call back success " + JSON.stringify(event));
        },
        onPageEnd: (event: OnPageEndEvent) => {
          console.info("onPageEnd call back success " + JSON.stringify(event));
        },
        onHttpErrorReceive: (event: OnHttpErrorReceiveEvent) => {
          console.info("onHttpErrorReceive call back success " + JSON.stringify(event));
        },
        onErrorReceive: (event: OnErrorReceiveEvent) => {
          console.info("onErrorReceive call back success " + JSON.stringify(event));
        }
      })
    }
  }
}
```

### 示例7

设置嵌套滚动。

```ts
import { AtomicServiceWeb, AtomicServiceWebController } from '@kit.ArkUI';

@Entry
@Component
struct AtomicServiceNestedScroll {
  @State controller: AtomicServiceWebController = new AtomicServiceWebController();
  @State mode: string = 'PARALLEL模式（点击切换）';
  @State nestedScroll: NestedScrollOptions | NestedScrollOptionsExt = {
    scrollForward: NestedScrollMode.PARALLEL,
    scrollBackward: NestedScrollMode.PARALLEL
  };

  build() {
    Scroll() {
      Column() {
        Text("嵌套AsWeb-头部")
          .height("15%")
          .width("100%")
          .fontSize(30)
          .backgroundColor(Color.Yellow)
        Button(this.mode)
          .margin({ top: 10, bottom: 10 })
          .onClick(() => {
            if (!(this.nestedScroll as NestedScrollOptions).scrollForward) {
              this.mode = 'SELF_FIRST模式（点击切换）';
              this.nestedScroll = {
                scrollForward: NestedScrollMode.SELF_FIRST,
                scrollBackward: NestedScrollMode.SELF_FIRST
              }
            } else {
              this.mode = 'PARENT_FIRST模式（点击切换）';
              this.nestedScroll = {
                scrollUp: NestedScrollMode.PARENT_FIRST,
                scrollDown: NestedScrollMode.PARENT_FIRST
              }
            }
          })
        AtomicServiceWeb({
          src: 'https://www.example.com',
          controller: this.controller,
          nestedScroll: this.nestedScroll
        })
        Text("嵌套AsWeb-尾部")
          .height("15%")
          .width("100%")
          .fontSize(30)
          .backgroundColor(Color.Yellow)
      }
    }
  }
}
```
