# WebOptions

Defines Web options through the [API](../../../reference/apis-arkweb/arkts-basic-components-web.md#api), including the web page resource URL, controller, rendering mode, and more.

**Since:** 8

**System capability:** SystemCapability.Web.Webview.Core

## controller

```TypeScript
controller: WebController | WebviewController
```

Controller used to control various behaviors of the Web component, including page navigation, lifecycle state, JavaScript interaction, etc. Since API version 9, WebController is no longer maintained. It is recommended to use [WebviewController](arkts-arkweb-webviewcontroller-t.md) instead.

**Type:** [WebController](arkts-arkweb-webcontroller-c.md) &#124; [WebviewController](arkts-arkweb-webviewcontroller-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## emulateTouchFromMouseEvent

```TypeScript
emulateTouchFromMouseEvent? : boolean
```

Whether to convert mouse events to touch events. The value **true** indicates that mouse events are converted to touch events, which is suitable for scenarios where touch and mouse interaction behaviors need to be unified; **false** indicates that mouse events are not converted to touch events.

Default value: **false**.

**Type:** boolean

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## incognitoMode

```TypeScript
incognitoMode? : boolean
```

Whether the current Webview is created in incognito mode. The value **true** indicates incognito mode, and **false** indicates normal mode.

Default value: **false**.

The value is **false** when undefined or null is passed in.&lt;!--RP1--&gt;&lt;!--RP1End--&gt;

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## renderMode

```TypeScript
renderMode? : RenderMode
```

Rendering mode of the current Web component. `RenderMode.ASYNC_RENDER` indicates asynchronous rendering, and `RenderMode.SYNC_RENDER` indicates synchronous rendering. Default value: `RenderMode.ASYNC_RENDER`. This mode does not support dynamic adjustment.

**Type:** [RenderMode](arkts-arkweb-rendermode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## sharedRenderProcessToken

```TypeScript
sharedRenderProcessToken? : string
```

Token that specifies the shared render process for the current Web component. In multi-render-process mode, Web components with the same token preferentially attempt to reuse the bound render process. The binding occurs during the initialization phase of the render process. When a render process has no associated Web component, its binding relationship is removed.

Default value: **""**.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## src

```TypeScript
src: string | Resource
```

Web page resource address. If a local resource file is accessed, use the resource protocol or &#36;rawfile resource reference. If a local resource file in the sandbox path outside the app package is loaded (HTML and TXT file types are supported), use file:// sandbox file path.

src cannot be dynamically changed through a state variable (for example, @State). To change the address, reload the page through [loadUrl()](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#loadurl).

**Type:** string &#124; Resource

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
