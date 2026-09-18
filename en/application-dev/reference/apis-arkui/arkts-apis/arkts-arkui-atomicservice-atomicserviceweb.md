# @ohos.atomicservice.AtomicServiceWeb(Defines the atomicService web component)

## Required Permissions

**ohos.permission.INTERNET**, required for accessing online web pages. For details about how to apply for a permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).

## Child Components

Not supported

## Attributes

The universal attributes are not supported.

## Events

The universal events are not supported.

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

```TypeScript
### Example 1

This example loads a local web page:
```

```TypeScript
### Example 2

This example loads an online web page:
```

```TypeScript
### Example 3

This example demonstrates how to load a web page within a NavDestination container.
```

```TypeScript
### Example 4

This example sets the onMessage() event callback.
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

```TypeScript
### Example 5

This example sets the web page loading event callbacks.
```

```TypeScript
### Example 6

This example demonstrates how to use AtomicServiceWeb and AtomicServiceWebController.
```

```TypeScript
### Example 7

This example shows how to set nested scrolling.
```
