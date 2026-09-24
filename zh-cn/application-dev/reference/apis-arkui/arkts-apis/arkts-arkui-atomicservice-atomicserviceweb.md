# @ohos.atomicservice.AtomicServiceWeb(Defines the atomicService web component)

## 需要权限

访问在线网页时需添加网络权限：ohos.permission.INTERNET，具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。

## 子组件

无

## 属性

不支持[通用属性](../arkts-components/arkts-arkui-common-comp.md#common)。

## 事件

不支持[通用事件](../arkts-components/arkts-arkui-common-comp.md#common)。

## 导入模块

```TypeScript
import { AtomicServiceWeb, OnMessageEvent, OnErrorReceiveEvent, OnHttpErrorReceiveEvent, OnPageBeginEvent, OnPageEndEvent, AtomicServiceWebController, OnLoadInterceptEvent, OnProgressChangeEvent, OnLoadInterceptCallback, WebHeader } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceWebController](arkts-arkui-atomicservice-atomicserviceweb-atomicservicewebcontroller-c.md) | 通过AtomicServiceWebController可以控制AtomicServiceWeb组件各种行为。一个AtomicServiceWebController对象只能控制一个AtomicServiceWeb组件，且必须在AtomicServiceWeb组件和AtomicServiceWebController绑定后，才能调用AtomicServiceWebController上的方法。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceWeb](arkts-arkui-atomicservice-atomicserviceweb-atomicserviceweb-s.md) | 为开发者提供满足定制化诉求的Web高阶组件，屏蔽原生Web组件中无需关注的接口，并提供JS扩展能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [OnErrorReceiveEvent](arkts-arkui-atomicservice-atomicserviceweb-onerrorreceiveevent-i.md) | 定义网页加载遇到错误时触发该回调。 |
| [OnHttpErrorReceiveEvent](arkts-arkui-atomicservice-atomicserviceweb-onhttperrorreceiveevent-i.md) | 定义网页加载资源遇到HTTP错误时触发该回调。 |
| [OnLoadInterceptEvent](arkts-arkui-atomicservice-atomicserviceweb-onloadinterceptevent-i.md) | 定义Web组件加载url之前触发的加载拦截事件。 |
| [OnMessageEvent](arkts-arkui-atomicservice-atomicserviceweb-onmessageevent-i.md) | 定义页面返回或销毁时触发该回调。 |
| [OnPageBeginEvent](arkts-arkui-atomicservice-atomicserviceweb-onpagebeginevent-i.md) | 定义网页加载开始时触发该回调。 |
| [OnPageEndEvent](arkts-arkui-atomicservice-atomicserviceweb-onpageendevent-i.md) | 定义网页加载结束时触发该回调。 |
| [OnProgressChangeEvent](arkts-arkui-atomicservice-atomicserviceweb-onprogresschangeevent-i.md) | 定义网页加载进度变化时触发该回调。 |
| [WebHeader](arkts-arkui-atomicservice-atomicserviceweb-webheader-i.md) | Web组件返回的请求/响应头对象。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnLoadInterceptCallback](arkts-arkui-onloadinterceptcallback-t.md) | 当Web组件加载url之前触发该回调，用于判断是否阻止此次访问。 |

## 示例

### 示例1

加载本地网页。

```TypeScript
// xxx.ets
import { AtomicServiceWeb, AtomicServiceWebController } from '@kit.ArkUI';

@Entry
@Component
struct WebComponent {
  @State controller: AtomicServiceWebController = new AtomicServiceWebController();
  
  build() {
    Column() {
      AtomicServiceWeb({ src: $rawfile('index.html'), controller: this.controller })
    }
  }
}
```

### 示例2

加载在线网页。

```TypeScript
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

```TypeScript
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
      AtomicServiceWeb({ src: $rawfile('index.html'), controller: this.controller, navPathStack: this.navPathStack })
    }
    .onReady((context: NavDestinationContext) => {
      this.navPathStack = context.pathStack;
    })
  }
}
```

### 示例4

设置onMessage()事件回调。

```TypeScript
// xxx.ets
import { AtomicServiceWeb, AtomicServiceWebController, OnMessageEvent } from '@kit.ArkUI';

@Entry
@Component
struct WebComponent {
  @State controller: AtomicServiceWebController = new AtomicServiceWebController();

  build() {
    Column() {
      AtomicServiceWeb({
        src: $rawfile('index.html'),
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

```TypeScript
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

```TypeScript
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

```TypeScript
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
  @State count: number = 1;

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
        this.controller.forward();
        console.info(`AtomicServiceWebLog forward`);
      })
      Button('backward').onClick(() => {
        this.controller.backward();
        console.info(`AtomicServiceWebLog backward`);
      })
      Button('refresh').onClick(() => {
        this.controller.refresh();
        console.info(`AtomicServiceWebLog refresh`);
      })
      Button('loadUrl').onClick(() => {
        this.controller.loadUrl('https://www.baidu.com/');
        console.info(`AtomicServiceWebLog loadUrl`);
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
        this.controller.setCustomUserAgent('test' + this.count++);

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
          console.info('AtomicServiceWebLog onControllerAttached call back success');
        },
        onLoadIntercept: (event: OnLoadInterceptEvent) => {
          console.info('AtomicServiceWebLog onLoadIntercept call back success ' + JSON.stringify({
            getRequestUrl: event.data.getRequestUrl(),
            getRequestMethod: event.data.getRequestMethod(),
            getRequestHeader: event.data.getRequestHeader(),
            isRequestGesture: event.data.isRequestGesture(),
            isMainFrame: event.data.isMainFrame(),
            isRedirect: event.data.isRedirect(),
          }));
          return false;
        },
        onProgressChange: (event: OnProgressChangeEvent) => {
          console.info('AtomicServiceWebLog onProgressChange call back success ' + JSON.stringify(event));
        },
        onMessage: (event: OnMessageEvent) => {
          console.info('AtomicServiceWebLog onMessage call back success ' + JSON.stringify(event));
        },
        onPageBegin: (event: OnPageBeginEvent) => {
          console.info('AtomicServiceWebLog onPageBegin call back success ' + JSON.stringify(event));
        },
        onPageEnd: (event: OnPageEndEvent) => {
          console.info('AtomicServiceWebLog onPageEnd call back success ' + JSON.stringify(event));
        },
        onHttpErrorReceive: (event: OnHttpErrorReceiveEvent) => {
          console.info('AtomicServiceWebLog onHttpErrorReceive call back success ' + JSON.stringify(event));
        },
        onErrorReceive: (event: OnErrorReceiveEvent) => {
          console.info('AtomicServiceWebLog onErrorReceive call back success ' + JSON.stringify(event));
        }
      })
    }
  }
}
```

### 示例7

设置嵌套滚动。

```TypeScript
// xxx.ets
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
        Text('嵌套AsWeb-头部')
          .height('15%')
          .width('100%')
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
        Text('嵌套AsWeb-尾部')
          .height('15%')
          .width('100%')
          .fontSize(30)
          .backgroundColor(Color.Yellow)
      }
    }
  }
}
```
