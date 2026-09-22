# @ohos.atomicservice.AtomicServiceWeb(Defines the atomicService web component)

## Required Permissions

**ohos.permission.INTERNET**, required for accessing online web pages. For details about how to apply for a permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).

## Child Components

Not supported

## Attributes

The [universal attributes](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Events

The [universal events](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Modules to Import

```TypeScript
import { AtomicServiceWeb, OnMessageEvent, OnErrorReceiveEvent, OnHttpErrorReceiveEvent, OnPageBeginEvent, OnPageEndEvent, AtomicServiceWebController, OnLoadInterceptEvent, OnProgressChangeEvent, OnLoadInterceptCallback, WebHeader } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AtomicServiceWebController](arkts-arkui-atomicservice-atomicserviceweb-atomicservicewebcontroller-c.md) | Implements an **AtomicServiceWebController** object for controlling the behavior of the **AtomicServiceWeb** component. An **AtomicServiceWebController** can control only one **AtomicServiceWeb** component, and the APIs on the **AtomicServiceWebController** can be called only after it has been bound to the target **AtomicServiceWeb** component. |

### Structs

| Name | Description |
| --- | --- |
| [AtomicServiceWeb](arkts-arkui-atomicservice-atomicserviceweb-atomicserviceweb-s.md) | **AtomicServiceWeb** is an advanced web component offering customization to meet specific demands. It shields irrelevant APIs from the native **Web** component and extends functionality through JavaScript capabilities. |

### Interfaces

| Name | Description |
| --- | --- |
| [OnErrorReceiveEvent](arkts-arkui-atomicservice-atomicserviceweb-onerrorreceiveevent-i.md) | Represents the callback invoked when an error occurs during web page loading. |
| [OnHttpErrorReceiveEvent](arkts-arkui-atomicservice-atomicserviceweb-onhttperrorreceiveevent-i.md) | Represents the callback invoked when an HTTP error occurs during web page resource loading. |
| [OnLoadInterceptEvent](arkts-arkui-atomicservice-atomicserviceweb-onloadinterceptevent-i.md) | Represents the event triggered when resource loading is intercepted. |
| [OnMessageEvent](arkts-arkui-atomicservice-atomicserviceweb-onmessageevent-i.md) | Represents the callback invoked when the page is navigated back or destroyed. |
| [OnPageBeginEvent](arkts-arkui-atomicservice-atomicserviceweb-onpagebeginevent-i.md) | Represents the callback invoked when the web page loading begins. |
| [OnPageEndEvent](arkts-arkui-atomicservice-atomicserviceweb-onpageendevent-i.md) | Represents the callback invoked when the web page loading ends. |
| [OnProgressChangeEvent](arkts-arkui-atomicservice-atomicserviceweb-onprogresschangeevent-i.md) | Represents the callback invoked when the web page loading progress changes. |
| [WebHeader](arkts-arkui-atomicservice-atomicserviceweb-webheader-i.md) | Describes the request/response header returned by the **AtomicServiceWeb** component. |

### Types

| Name | Description |
| --- | --- |
| [OnLoadInterceptCallback](arkts-arkui-onloadinterceptcallback-t.md) | Represents the callback invoked when resource loading is intercepted. |

## Examples

### Example 1

This example loads a local web page:

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

### Example 2

This example loads an online web page:

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

### Example 3

This example demonstrates how to load a web page within a NavDestination container.

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

### Example 4

This example sets the onMessage() event callback.

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
        // Called when the user clicks Send Message and then Back on an HTML5 page.
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
<!-- Import the JS SDK file. -->
<script src="../js/atomicservice-sdk.js" type="text/javascript"></script>
<body>
<h1>JS SDK - postMessage()</h1>
<br/>
<button type="button" onclick="postMessage({ name: 'Jerry', age: 18 });">Send Message</button>
<br/>
<button type="button" onclick="back();">Back</button>
</body>
<script type="text/javascript">
    function postMessage(data) {
        // API provided by the JS SDK for sending messages.
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
        // Router API provided by the JS SDK for navigation back.
        has.router.back({
            delta: 1
        });
    }
</script>
</html>
```

### Example 5

This example sets the web page loading event callbacks.

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
        // Invoked when an error occurs during web page loading.
        onErrorReceive: (event: OnErrorReceiveEvent) => {
          console.info(`AtomicServiceWebLog onErrorReceive event = ${JSON.stringify({
            requestUrl: event.request?.getRequestUrl(),
            requestMethod: event.request?.getRequestMethod(),
            errorCode: event.error?.getErrorCode(),
            errorInfo: event.error?.getErrorInfo()
          })}`);
        },
        // Invoked when an HTTP error occurs during web page resource loading.
        onHttpErrorReceive: (event: OnHttpErrorReceiveEvent) => {
          console.info(`AtomicServiceWebLog onHttpErrorReceive event = ${JSON.stringify({
            requestUrl: event.request?.getRequestUrl(),
            requestMethod: event.request?.getRequestMethod(),
            responseCode: event.response?.getResponseCode(),
            responseData: event.response?.getResponseData(),
          })}`);
        },
        // Invoked when the web page starts to be loaded.
        onPageBegin: (event: OnPageBeginEvent) => {
          console.info(`AtomicServiceWebLog onPageBegin event = ${JSON.stringify({
            url: event.url
          })}`);
        },
        // Invoked when loading of the web page is complete.
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

### Example 6

This example demonstrates how to use AtomicServiceWeb and AtomicServiceWebController.

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
      Button('Dark Mode').onClick(() => {
        this.forceDarkAccess = !this.forceDarkAccess;
      })
      Button('mixedMode').onClick(() => {
        this.mixedMode = this.mixedMode == MixedMode.None ? MixedMode.All : MixedMode.None;
      })
      Button('Click').onClick(() => {
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

### Example 7

This example shows how to set nested scrolling.

```TypeScript
// xxx.ets
import { AtomicServiceWeb, AtomicServiceWebController } from '@kit.ArkUI';

@Entry
@Component
struct AtomicServiceNestedScroll {
  @State controller: AtomicServiceWebController = new AtomicServiceWebController();
  @State mode: string = 'PARALLEL mode (click to switch)';
  @State nestedScroll: NestedScrollOptions | NestedScrollOptionsExt = {
    scrollForward: NestedScrollMode.PARALLEL,
    scrollBackward: NestedScrollMode.PARALLEL
  };

  build() {
    Scroll() {
      Column() {
        Text('Nested AsWeb - Header')
          .height('15%')
          .width('100%')
          .fontSize(30)
          .backgroundColor(Color.Yellow)
        Button(this.mode)
          .margin({ top: 10, bottom: 10 })
          .onClick(() => {
            if (!(this.nestedScroll as NestedScrollOptions).scrollForward) {
              this.mode = 'SELF_FIRST mode (click to switch)';
              this.nestedScroll = {
                scrollForward: NestedScrollMode.SELF_FIRST,
                scrollBackward: NestedScrollMode.SELF_FIRST
              }
            } else {
              this.mode = 'PARENT_FIRST mode (click to switch)';
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
        Text('Nested AsWeb - Footer')
          .height('15%')
          .width('100%')
          .fontSize(30)
          .backgroundColor(Color.Yellow)
      }
    }
  }
}
```
