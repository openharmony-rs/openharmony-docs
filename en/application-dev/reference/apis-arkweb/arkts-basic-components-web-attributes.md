# Attributes

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=4180bb2e440d5dee76207e80672383a5f25809b4 translatedAt=2026-08-07T04:34:58.488Z pushedAt=2026-08-07T14:01:57.110Z -->

The supported universal attributes include [aspectRatio](../apis-arkui/arkui-ts/ts-universal-attributes-layout-constraints.md#aspectratio), [backdropBlur](../apis-arkui/arkui-ts/ts-universal-attributes-background.md#backdropblur), [backgroundColor](../apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor), [bindContentCover](../apis-arkui/arkui-ts/ts-universal-attributes-modal-transition.md#bindcontentcover), [bindContextMenu](../apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindcontextmenu8), [bindMenu](../apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindmenu), [bindSheet](../apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#bindsheet), [borderColor](../apis-arkui/arkui-ts/ts-universal-attributes-border.md#bordercolor), [borderRadius](../apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderradius), [borderStyle](../apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderstyle), [borderWidth](../apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderwidth), [clip](../apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#clip12), [constraintSize](../apis-arkui/arkui-ts/ts-universal-attributes-size.md#constraintsize), [defaultFocus](../apis-arkui/arkui-ts/ts-universal-attributes-focus.md#defaultfocus9), [focusable](../apis-arkui/arkui-ts/ts-universal-attributes-focus.md#focusable), [tabIndex](../apis-arkui/arkui-ts/ts-universal-attributes-focus.md#tabindex9), [groupDefaultFocus](../apis-arkui/arkui-ts/ts-universal-attributes-focus.md#groupdefaultfocus9), [displayPriority](../apis-arkui/arkui-ts/ts-universal-attributes-layout-constraints.md#displaypriority), [enabled](../apis-arkui/arkui-ts/ts-universal-attributes-enable.md#enabled), [flexBasis](../apis-arkui/arkui-ts/ts-universal-attributes-flex-layout.md#flexbasis), [flexShrink](../apis-arkui/arkui-ts/ts-universal-attributes-flex-layout.md#flexshrink), [layoutWeight](../apis-arkui/arkui-ts/ts-universal-attributes-size.md#layoutweight), [id](../apis-arkui/arkui-ts/ts-universal-attributes-component-id.md#id), [gridOffset](../apis-arkui/arkui-ts/ts-universal-attributes-grid.md#attributes), [gridSpan](../apis-arkui/arkui-ts/ts-universal-attributes-grid.md#attributes), [useSizeType](../apis-arkui/arkui-ts/ts-universal-attributes-grid.md#attributes), [height](../apis-arkui/arkui-ts/ts-universal-attributes-size.md#height), [touchable](../apis-arkui/arkui-ts/ts-universal-attributes-click.md#touchabledeprecated), [margin](../apis-arkui/arkui-ts/ts-universal-attributes-size.md#margin), [markAnchor](../apis-arkui/arkui-ts/ts-universal-attributes-location.md#markanchor), [offset](../apis-arkui/arkui-ts/ts-universal-attributes-location.md#offset), [width](../apis-arkui/arkui-ts/ts-universal-attributes-size.md#width), [zIndex](../apis-arkui/arkui-ts/ts-universal-attributes-z-order.md#zindex), [visibility](../apis-arkui/arkui-ts/ts-universal-attributes-visibility.md#visibility), [scale](../apis-arkui/arkui-ts/ts-universal-attributes-transformation.md#scale), [translate](../apis-arkui/arkui-ts/ts-universal-attributes-transformation.md#translate), [responseRegion](../apis-arkui/arkui-ts/ts-universal-attributes-touch-target.md#responseregion), [size](../apis-arkui/arkui-ts/ts-universal-attributes-size.md#size), [opacity](../apis-arkui/arkui-ts/ts-universal-attributes-opacity.md#opacity), [shadow](../apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow), [sharedTransition](../apis-arkui/arkui-ts/ts-transition-animation-shared-elements.md), [transition](../apis-arkui/arkui-ts/ts-transition-animation-component.md), [position](../apis-arkui/arkui-ts/ts-universal-attributes-location.md#position), and [direction](../apis-arkui/arkui-ts/ts-universal-attributes-location.md#direction).

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The sample effect is subject to the actual device.

## Overview

Web component attributes are used to configure the web page loading behavior, security policies, runtime environment, and interaction capabilities of the **Web** component through chain calls in the ArkUI declarative syntax. They serve as the primary entry point for customizing **Web** component behavior. For general style and layout attributes (such as size, margin, background, and visibility), see [Size Settings](../apis-arkui/arkui-ts/ts-universal-attributes-size.md). This chapter describes only attributes specific to the **Web** component. For runtime dynamic control capabilities (such as loading URLs, navigating forward/backward, registering/unregistering JS objects, running JavaScript, and injecting CSS), use them together with [WebviewController](./arkts-apis-webview-WebviewController.md).

## domStorageAccess

domStorageAccess(domStorageAccess: boolean)

Sets whether to enable the DOM Storage API permission. If this attribute is not explicitly called, the DOM Storage API permission is disabled by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name             | Type   | Mandatory  | Description                                |
| ---------------- | ------- | ---- | ------------------------------------ |
| domStorageAccess | boolean | Yes    | Sets whether to enable the Document Object Model storage interface (DOM Storage API).<br>The value **true** enables it, and **false** disables it.<br>If **undefined** or **null** is passed, the default value **false** is used. |

> **NOTE**
>
> - A web page can be loaded only when its DOM Storage API is set to **true**.

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .domStorageAccess(true)
      }
    }
  }
  ```

## fileAccess

fileAccess(fileAccess: boolean)

Sets whether to enable access to the file system in the application. This setting does not affect the access to the files specified through [$rawfile(filepath/filename)](../../quick-start/resource-categories-and-access.md#accessing-resources). For API version 11 and earlier versions, access to the file system in the application is enabled by default if this attribute is not explicitly called. Since API version 12, access to the file system in the application is disabled by default if this attribute is not explicitly called.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name       | Type   | Mandatory  | Description                  |
| ---------- | ------- | ---- | ---------------------- |
| fileAccess | boolean | Yes | Whether to enable access to the file system in the app.<br>The value **true** means to enable, and **false** means to disable.<br>In addition, when fileAccess is **false**, resources in the read-only resource directory `/data/storage/el1/bundle/entry/resources/resfile` can still be accessed through the file protocol, which is not controlled by fileAccess.<br>In API version 11 and earlier, the value is **true** when undefined or null is passed. In API version 12 and later, the value is **false** when undefined or null is passed. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .fileAccess(true)
      }
    }
  }
  ```

## imageAccess

imageAccess(imageAccess: boolean)

Sets whether to allow automatic loading of image resources. If this attribute is not explicitly called, automatic loading is allowed by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name        | Type   | Mandatory  | Description           |
| ----------- | ------- | ---- | --------------- |
| imageAccess | boolean | Yes    | Whether to allow automatic loading of image resources.<br>The value **true** means allowed, and **false** means not allowed.<br>If **undefined** or **null** is passed, the value is **false**. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .imageAccess(true)
      }
    }
  }
  ```

## javaScriptProxy

javaScriptProxy(javaScriptProxy: JavaScriptProxy)

Registers the ArkTS object in **javaScriptProxy** with the **Web** component. The object will be registered in all frames of the web page, including all iframes, using the name specified in **JavaScriptProxy**. This enables JavaScript to call methods of the ArkTS object in **javaScriptProxy**.

> **NOTE**
>
> The **javaScriptProxy** API must be used together with [deleteJavaScriptRegister<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#deletejavascriptregister) to prevent memory leaks.
> All parameters of the **javaScriptProxy** object cannot be updated.
> When registering a **javaScriptProxy** object, at least one of the synchronous or asynchronous method lists must be non-empty. Both types of methods can be registered simultaneously.
> This API supports registering only one object. To register multiple objects, use [registerJavaScriptProxy<sup>9+</sup>](./arkts-apis-webview-WebviewController.md#registerjavascriptproxy).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name       | Type                                    | Mandatory  | Description                                    |
| ---------- | ---------------------------------------- | ---- |---------------------------------------- |
| javaScriptProxy     | [JavaScriptProxy](./arkts-basic-components-web-i.md#javascriptproxy12)                                   | Yes   |  Object to be registered. Methods can be declared, but attributes cannot.<br>When **undefined** or **null** is passed in, the ArkTS object in javaScriptProxy is not registered with the **Web** component.                 |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';

  class TestObj {
    constructor() {
    }

    test(data1: string, data2: string, data3: string): string {
      console.info("data1:" + data1);
      console.info("data2:" + data2);
      console.info("data3:" + data3);
      return "AceString";
    }

    asyncTest(data: string): void {
      console.info("async data:" + data);
    }

    toString(): void {
      console.info('toString' + "interface instead.");
    }
  }

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    testObj = new TestObj();
    build() {
      Column() {
        Button('deleteJavaScriptRegister')
          .onClick(() => {
            try {
              this.controller.deleteJavaScriptRegister("objName");
            } catch (error) {
              console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
            }
          })
        Web({ src: 'www.example.com', controller: this.controller })
          .javaScriptAccess(true)
          .javaScriptProxy({
            object: this.testObj,
            name: "objName",
            methodList: ["test", "toString"],
            asyncMethodList: ["asyncTest"],
            controller: this.controller,
        })
      }
    }
  }
  ```

## javaScriptAccess

javaScriptAccess(javaScriptAccess: boolean)

Sets whether to allow execution of JavaScript scripts. If this attribute is not explicitly called, execution is allowed by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name             | Type   | Mandatory  | Description               |
| ---------------- | ------- | ---- | ------------------- |
| javaScriptAccess | boolean | Yes | Whether to allow JavaScript script execution.<br>The value **true** means allowed, and **false** means not allowed.<br>The default value is **false** when undefined or null is passed. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .javaScriptAccess(true)
      }
    }
  }
  ```

## overScrollMode<sup>11+</sup>

overScrollMode(mode: OverScrollMode)

Sets the over-scroll mode of the **Web** component. When enabled, if the user scrolls to the edge of the root web page, the **Web** component bounces back with an elastic animation, and inner pages on the root page do not trigger the bounce effect. If this attribute is not explicitly called, the over-scroll mode is disabled by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type                                   | Mandatory  | Description              |
| ---- | --------------------------------------- | ---- | ------------------ |
| mode | [OverScrollMode](./arkts-basic-components-web-e.md#overscrollmode11) | Yes   | Whether to enable the overscroll mode.<br>When **undefined** or **null** is passed in, the value is **OverScrollMode.NEVER**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State mode: OverScrollMode = OverScrollMode.ALWAYS;
    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .overScrollMode(this.mode)
      }
    }
  }
  ```

## mixedMode

mixedMode(mixedMode: MixedMode)

Sets the behavior when a secure source attempts to load resources from an insecure source. When this attribute is not explicitly called, the default value is **MixedMode.None**, which means that secure sources are not allowed to load content from insecure sources.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name      | Type                       | Mandatory  | Description     |
| --------- | --------------------------- | ---- | --------- |
| mixedMode | [MixedMode](./arkts-basic-components-web-e.md#mixedmode) | Yes   | Mixed content mode to be set.<br>If **undefined** or **null** is passed in, the value **MixedMode.All** is used. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State mode: MixedMode = MixedMode.All;
    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .mixedMode(this.mode)
      }
    }
  }
  ```

## onlineImageAccess

onlineImageAccess(onlineImageAccess: boolean)

Sets whether to allow loading of image resources from the network (resources accessed via HTTP and HTTPS). If this attribute is not explicitly called, loading is allowed by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name              | Type   | Mandatory  | Description            |
| ----------------- | ------- | ---- | ---------------- |
| onlineImageAccess | boolean | Yes | Whether to allow loading image resources from the network.<br>The value **true** means that loading is allowed, and **false** means it is not allowed.<br>When **undefined** or **null** is passed in, the value is **false**. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .onlineImageAccess(true)
      }
    }
  }
  ```

## zoomAccess

zoomAccess(zoomAccess: boolean)

Sets whether to support zoom gestures. If this attribute is not explicitly called, zoom gestures are supported by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name       | Type   | Mandatory  | Description         |
| ---------- | ------- | ---- | ------------- |
| zoomAccess | boolean | Yes | Whether to support gesture-based zooming.<br>The value **true** indicates supported, and **false** indicates not supported.<br>When **undefined** or **null** is passed, the value is **false**. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .zoomAccess(true)
      }
    }
  }
  ```

## overviewModeAccess

overviewModeAccess(overviewModeAccess: boolean)

Sets whether to load web pages by using the overview mode. That is, zoom out the content to fit the screen width. When this attribute is not explicitly called, web pages can be loaded in overview mode by default.

**System capability**: SystemCapability.Web.Webview.Core

**Device behavior**: This API has no effect on the PCs/2-in-1 devices and works on other devices.

**Parameters**

| Name               | Type   | Mandatory  | Description           |
| ------------------ | ------- | ---- | --------------- |
| overviewModeAccess | boolean | Yes | Whether to load web pages in overview mode.<br>The value **true** means to use overview mode, and **false** means not to use it.<br>The default value is **false** when undefined or null is passed in. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .overviewModeAccess(true)
      }
    }
  }
  ```

## databaseAccess

databaseAccess(databaseAccess: boolean)

Sets whether to enable the Web SQL Database storage API permission. If this permission is not explicitly called, it is disabled by default.

> **NOTE**
>
> - After the ArkWeb kernel is upgraded to M132, the API's control over the Web SQL Database becomes invalid because the kernel discards Web SQL. For details about the ArkWeb kernel version, see [Constraints](../../web/web-component-overview.md#constraints).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name           | Type   | Mandatory  | Description             |
| -------------- | ------- | ---- | ----------------- |
| databaseAccess | boolean | Yes   | Whether to enable Web SQL Database storage API permission.<br>**true** means enabling the detection, and **false** means disabling it.<br>If **undefined** or **null** is passed in, the value is **false**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .databaseAccess(true)
      }
    }
  }
  ```

## geolocationAccess

geolocationAccess(geolocationAccess: boolean)

Sets whether to enable the geolocation permission. If this attribute is not explicitly called, the permission is enabled by default. For details about how to use this feature, see [Managing Location Permissions](../../web/web-geolocation-permission.md).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name              | Type   | Mandatory  | Description           |
| ----------------- | ------- | ---- | --------------- |
| geolocationAccess | boolean | Yes | Whether to enable the geolocation permission.<br>The value **true** means to enable the permission, and **false** means the opposite.<br>The value **false** is used when **undefined** or **null** is passed in. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .geolocationAccess(true)
      }
    }
  }
  ```

## mediaPlayGestureAccess<sup>9+</sup>

mediaPlayGestureAccess(access: boolean)

Sets whether autoplay of audible videos requires a user tap. Muted video playback is not affected by this API. If this attribute is not explicitly set, a user tap is required by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type   | Mandatory  | Description               |
| ------ | ------- | ---- | ------------------- |
| access | boolean | Yes | Whether the autoplay of videos with audio requires a user tap.<br>The value **true** indicates that a user tap is required, and **false** indicates that the video can be autoplayed.<br>If **undefined** or **null** is passed, the value is **false**. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State access: boolean = true;

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .mediaPlayGestureAccess(this.access)
      }
    }
  }
  ```

HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
      <title>Video Playback Page</title>
  </head>
  <body>
  <h1>Video Playback</h1>
  <video id="testVideo" controls autoplay>
      // Configure the autoplay attribute in the video tag to allow automatic video playback.
      // Save an MP4 media file in the rawfile directory of resources and name it example.mp4.
      <source src="example.mp4" type="video/mp4">
  </video>
  </body>
  </html>
  ```

## multiWindowAccess<sup>9+</sup>

multiWindowAccess(multiWindow: boolean)

Sets whether to enable the multi-window permission. If this attribute is not explicitly called, the permission is disabled by default.

Enabling the multi-window permission requires implementation of the **onWindowNew** event. For the sample code, see [onWindowNew](./arkts-basic-components-web-events.md#onwindownew9).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name        | Type   | Mandatory  | Description        |
| ----------- | ------- | ---- | ------------ |
| multiWindow | boolean | Yes    | Whether to enable the multi-window permission.<br>The value **true** means to enable, and **false** means the opposite. |

## horizontalScrollBarAccess<sup>9+</sup>

horizontalScrollBarAccess(horizontalScrollBar: boolean)

Sets whether to display the horizontal scrollbar, including the system default scrollbar and user-defined scrollbars. If this attribute is not explicitly called, the scrollbar is displayed by default.

> **NOTE**
>
> - If an [@State](../../ui/state-management/arkts-state.md) decorated variable is used to control the visibility of the horizontal scrollbar, [controller.refresh()](./arkts-apis-webview-WebviewController.md#refresh) must be called for the settings to take effect.
> - When the [@State](../../ui/state-management/arkts-state.md) decorated variable changes frequently and dynamically, it is recommended to maintain a one-to-one correspondence between the toggle variable and the **Web** component.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name                | Type   | Mandatory  | Description        |
| ------------------- | ------- | ---- | ------------ |
| horizontalScrollBar | boolean | Yes | Sets whether to display the horizontal scrollbar.<br>The value **true** indicates to display it, and **false** indicates not to display it.<br>The default value is **false** when undefined or null is passed. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State isShow: boolean = true;
    @State btnMsg: string = 'Hide scrollbar';
  
    build() {
      Column() {
        // If an @State decorated variable is used to control the horizontal scrollbar visibility, controller.refresh() must be called for the settings to take effect.
        Button('refresh')
          .onClick(() => {
            if (this.isShow) {
              this.isShow = false;
              this.btnMsg = 'Show scrollbar';
            } else {
              this.isShow = true;
              this.btnMsg = 'Hide scrollbar';
            }
            try {
              this.controller.refresh();
            } catch (error) {
              console.error(`Failed to refresh Web. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
            }
          }).height('10%').width('40%')
        Web({ src: $rawfile('index.html'), controller: this.controller }).height('90%')
          .horizontalScrollBarAccess(this.isShow)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
      <meta name="viewport" id="viewport" content="width=device-width,initial-scale=1.0">
      <title>Demo</title>
      <style>
          body {
            width:3000px;
            height:6000px;
            padding-right:170px;
            padding-left:170px;
            border:5px solid blueviolet;
          }
      </style>
  </head>
  <body>
  Scroll Test
  </body>
  </html>
  ```

## verticalScrollBarAccess<sup>9+</sup>

verticalScrollBarAccess(verticalScrollBar: boolean)

Sets whether to display the vertical scrollbar, including the system default scrollbar and user-defined scrollbars. If this attribute is not explicitly called, the scrollbar is displayed by default.

> **NOTE**
>
> - If an @State decorated variable is used to control the vertical scrollbar visibility, **controller.refresh()** must be called for the settings to take effect.
> - If the vertical scrollbar visibility changes frequently through an @State decorated variable, it is recommended that the variable correspond to the **Web** component one by one.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name              | Type   | Mandatory  | Description        |
| ----------------- | ------- | ---- | ------------ |
| verticalScrollBar | boolean | Yes    | Whether to display the vertical scrollbar.<br>The value **true** means to display, and **false** means not to display.<br>The default value is **false** when undefined or null is passed in. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State isShow: boolean = true;
    @State btnMsg: string = 'Hide scrollbar';
  
    build() {
      Column() {
        // If an @State decorated variable is used to control the vertical scrollbar visibility, controller.refresh() must be called for the settings to take effect.
        Button(this.btnMsg)
          .onClick(() => {
            if (this.isShow) {
              this.isShow = false;
              this.btnMsg = 'Show scrollbar';
            } else {
              this.isShow = true;
              this.btnMsg = 'Hide scrollbar';
            }
            try {
              this.controller.refresh();
            } catch (error) {
              console.error(`Failed to refresh Web. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
            }
          }).height('10%').width('40%')
        Web({ src: $rawfile('index.html'), controller: this.controller }).height('90%')
          .verticalScrollBarAccess(this.isShow)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
      <meta name="viewport" id="viewport" content="width=device-width,initial-scale=1.0">
      <title>Demo</title>
      <style>
          body {
            width:3000px;
            height:6000px;
            padding-right:170px;
            padding-left:170px;
            border:5px solid blueviolet;
          }
      </style>
  </head>
  <body>
  Scroll Test
  </body>
  </html>
  ```

## cacheMode

cacheMode(cacheMode: CacheMode)

Sets the cache mode. When this attribute is not explicitly called, the default value **CacheMode.Default** is used.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name      | Type                       | Mandatory  | Description     |
| --------- | --------------------------- | ---- | --------- |
| cacheMode | [CacheMode](./arkts-basic-components-web-e.md#cachemode) | Yes   | Cache mode to set.<br>When **undefined** or **null** is passed in, the value is **CacheMode.Default**. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State mode: CacheMode = CacheMode.None;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .cacheMode(this.mode)
      }
    }
  }
  ```

## copyOptions<sup>11+</sup>

copyOptions(value: CopyOptions)

Sets the clipboard copy scope option. If this attribute is not explicitly called, pasting across all apps on the current device is supported by default after copying.

> **NOTE**
>
> When this attribute is set to **CopyOptions.None**, the **enablePreviewMenu** configuration item in [dataDetectorConfig](#datadetectorconfig20) does not take effect. When [enableDataDetector](#enabledatadetector20) is set to **true** and this attribute is set to **CopyOptions.LocalDevice**, the AI menu feature is activated.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name      | Type                       | Mandatory  | Description     |
| --------- | --------------------------- | ---- | --------- |
| value | [CopyOptions](../apis-arkui/arkui-ts/ts-appendix-enums.md#copyoptions9) | Yes   | Pasteboard copy options.<br>When **undefined** or **null** is passed in, the value is **CopyOptions.None**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .copyOptions(CopyOptions.None)
      }
    }
  }
  ```

## textZoomRatio<sup>9+</sup>

textZoomRatio(textZoomRatio: number)

Sets the text zoom ratio of the page. When this attribute is not explicitly called, the default zoom ratio is 100%.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name          | Type  | Mandatory  | Description                            |
| ------------- | ------ | ---- | -------------------------------- |
| textZoomRatio | number | Yes | Text zoom percentage for the page. The value **100** indicates the original size, a value greater than **100** indicates zoom in, and a value less than **100** indicates zoom out.<br>The value is an integer in the range (0, 2147483647]. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State ratio: number = 150;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .textZoomRatio(this.ratio)
      }
    }
  }
  ```

## initialScale<sup>9+</sup>

initialScale(percent: number)

Sets the zoom percentage of the entire page. If this attribute is not explicitly called, the default value is **100**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type  | Mandatory  | Description                         |
| ------- | ------ | ---- | ----------------------------- |
| percent | number | Yes   | Scale factor of the entire page.<br>Value range: (0, 1000]<br>When **undefined** or **null** is passed in, the attribute setting does not take effect.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State percent: number = 100;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .initialScale(this.percent)
      }
    }
  }
  ```

## blockNetwork<sup>9+</sup>

blockNetwork(block: boolean)

Sets whether to block online downloads. When this attribute is not explicitly called, online resources can be loaded by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type   | Mandatory  | Description               |
| ----- | ------- | ---- | ------------------- |
| block | boolean | Yes   | Whether to allow online downloads.<br>The value **true** means to block online downloads, and **false** means the opposite.<br>If **undefined** or **null** is passed in, the value is **false**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State block: boolean = true;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .blockNetwork(this.block)
      }
    }
  }
  ```

## defaultFixedFontSize<sup>9+</sup>

defaultFixedFontSize(size: number)

Sets the default fixed font size for the web page. For HTML elements that use the **monospace** font and do not specify **font-size**, the font size is rendered based on this value.

When this attribute is not explicitly called, the default fixed font size is **13**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type  | Mandatory  | Description                                    |
| ---- | ------ | ---- | ---------------------------------------- |
| size | number | Yes   | Default fixed font size to set, in px.<br>Value range: [-2^31, 2^31-1]. In actual rendering, values greater than 72 px are handled as 72 px, and values less than 1 px are handled as 1 px.<br><br>When **null** or **undefined** is passed in, the value is **13**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State fontSize: number = 16;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .defaultFixedFontSize(this.fontSize)
      }
    }
  }
  ```

## defaultFontSize<sup>9+</sup>

defaultFontSize(size: number)

Sets the default font size for the web page. For HTML elements that use non-monospace fonts and do not specify **font-size**, the font size is rendered based on this value.

When this attribute is not explicitly called, the default font size of the web page is **16**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type  | Mandatory  | Description                                    |
| ---- | ------ | ---- | ---------------------------------------- |
| size | number | Yes   | Default font size to set, in px.<br>Value range: [-2^31, 2^31-1]. In actual rendering, values greater than 72 px are handled as 72 px, and values less than 1 px are handled as 1 px.<br>When **null** or **undefined** is passed in, the value is **16**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State fontSize: number = 13;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .defaultFontSize(this.fontSize)
      }
    }
  }
  ```

## minFontSize<sup>9+</sup>

minFontSize(size: number)

Sets the minimum font size for the web page. If the font size of HTML elements is smaller than the value set by this API, the font size is rendered based on the value set by this API.

When no attribute is explicitly called, the default minimum font size of the web page is **8**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type  | Mandatory  | Description                                    |
| ---- | ------ | ---- | ---------------------------------------- |
| size | number | Yes   | Minimum font size to set, in px.<br>Value range: [-2^31, 2^31-1]. In actual rendering, values greater than 72 px are handled as 72 px, and values less than 1 px are handled as 1 px.<br>When **null** or **undefined** is passed in, the value is **8**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State fontSize: number = 13;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .minFontSize(this.fontSize)
      }
    }
  }
  ```

## minLogicalFontSize<sup>9+</sup>

minLogicalFontSize(size: number)

Sets the minimum logical font size for the web page.

For HTML elements whose font size is not specified:

1. If the font size of the element is smaller than the value set by this API, the font size is rendered based on the API value.

2. If **minLogicalFontSize** and **minFontSize** are both set, the larger value of the two will be used for elements whose font size is not specified.

When this attribute is not explicitly called, the default minimum logical font size of the web page is **8**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type  | Mandatory  | Description                                    |
| ---- | ------ | ---- | ---------------------------------------- |
| size | number | Yes | Sets the minimum logical font size for web pages, in px.<br>The value ranges from [-2^31, 2^31-1]. During actual rendering, values greater than 72 px are rendered as 72 px, and values less than 1 px are rendered as 1 px.<br>Defaults to 8 when null or undefined is passed in. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State fontSize: number = 13;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .minLogicalFontSize(this.fontSize)
      }
    }
  }
  ```

## webFixedFont<sup>9+</sup>

webFixedFont(family: string)

Sets the fixed font family of the web page to render HTML elements that use the **monospace** font.

When this attribute is not explicitly called, the default fixed font family of the web page is **monospace**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                    |
| ------ | ------ | ---- | ------------------------ |
| family | string | Yes | Fixed font family for web pages. The value is a font name string, for example, "monospace" or "Arial".<br>The value **monospace** is used when null or undefined is passed. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State family: string = "monospace";

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .webFixedFont(this.family)
      }
    }
  }
  ```

## webSansSerifFont<sup>9+</sup>

webSansSerifFont(family: string)

Sets the sans-serif font family of the web page to render HTML elements that use the **sans-serif** font.

When this attribute is not explicitly called, the sans-serif font family of the web page is **sans-serif** by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                    |
| ------ | ------ | ---- | ------------------------ |
| family | string | Yes   | Sans-serif font family to set.<br>When **null** or **undefined** is passed in, the sans-serif font family is **sans-serif**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State family: string = "sans-serif";

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .webSansSerifFont(this.family)
      }
    }
  }
  ```

## webSerifFont<sup>9+</sup>

webSerifFont(family: string)

Sets the serif font family of the web page to render HTML elements that use the **serif** font.

When this attribute is not explicitly called, the default serif font family of the web page is **serif**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                    |
| ------ | ------ | ---- | ------------------------ |
| family | string | Yes   | Serif font family to set.<br>When **null** or **undefined** is passed in, the sans-serif font family is **serif**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State family: string = "serif";

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .webSerifFont(this.family)
      }
    }
  }
  ```

## webStandardFont<sup>9+</sup>

webStandardFont(family: string)

Sets the standard font family of the web page to render HTML elements whose font style is not specified.

When this attribute is not explicitly called, the default standard font family of the web page is **sans-serif**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                  |
| ------ | ------ | ---- | ---------------------- |
| family | string | Yes   | Standard font family to set.<br>When **null** or **undefined** is passed in, the sans-serif font family is **sans-serif**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State family: string = "sans-serif";

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .webStandardFont(this.family)
      }
    }
  }
  ```

## webFantasyFont<sup>9+</sup>

webFantasyFont(family: string)

Sets the fantasy font family of the web page to render HTML elements that use the **fantasy** font.

When this attribute is not explicitly called, the default fantasy font family of the web page is **fantasy**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                    |
| ------ | ------ | ---- | ------------------------ |
| family | string | Yes   | Fantasy font family to set.<br>When **null** or **undefined** is passed in, the value is **fantasy**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';
  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State family: string = "fantasy";

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .webFantasyFont(this.family)
      }
    }
  }
  ```

## webCursiveFont<sup>9+</sup>

webCursiveFont(family: string)

Sets the cursive font family of the web page to render HTML elements that use the **cursive** font.

When this attribute is not explicitly called, the default cursive font family of the web page is **cursive**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                    |
| ------ | ------ | ---- | ------------------------ |
| family | string | Yes   | Cursive font family to set.<br>When **null** or **undefined** is passed in, the value is **cursive**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State family: string = "cursive";

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .webCursiveFont(this.family)
      }
    }
  }
  ```

## darkMode<sup>9+</sup>

darkMode(mode: WebDarkMode)

Sets the dark mode of the **Web** component. If this attribute is not explicitly called, dark mode is disabled by default.

When dark mode is enabled, the **Web** component enables the dark style defined in the media query **prefers-color-scheme** of the web page. If it is not defined, the web page remains unchanged. To enable forcible dark mode, use this API with [forceDarkAccess](#forcedarkaccess9). For details about how to use dark mode, see [Setting Dark Mode](../../web/web-set-dark-mode.md).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type                            | Mandatory  | Description                    |
| ---- | -------------------------------- | ---- | ------------------------ |
| mode | [WebDarkMode](./arkts-basic-components-web-e.md#webdarkmode9) | Yes   | Dark mode for the web page, which can be set to **Off**, **On**, or **Auto**.<br>When **null** or **undefined** is passed, the value is **WebDarkMode.Off**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State mode: WebDarkMode = WebDarkMode.On;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .darkMode(this.mode)
      }
    }
  }
  ```

## forceDarkAccess<sup>9+</sup>

forceDarkAccess(access: boolean)

Sets whether to enable forcible dark mode for the web page. This API is applicable only when [darkMode](#darkmode9) is enabled. When this attribute is not explicitly called, forcible dark mode is disabled for the web page by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type   | Mandatory  | Description           |
| ------ | ------- | ---- | --------------- |
| access | boolean | Yes | Whether to enable forced dark mode for web pages.<br>The value **true** means to enable it, and **false** means not to enable it.<br>If null or undefined is passed, the default value **false** is used. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State mode: WebDarkMode = WebDarkMode.On;
    @State access: boolean = true;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .darkMode(this.mode)
          .forceDarkAccess(this.access)
      }
    }
  }
  ```

## pinchSmooth<sup>9+</sup>

pinchSmooth(isEnabled: boolean)

Sets whether to enable pinch smooth mode for the web page. When this attribute is not explicitly called, pinch smooth mode is disabled by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name      | Type   | Mandatory  | Description         |
| --------- | ------- | ---- | ------------- |
| isEnabled | boolean | Yes   | Whether to enable pinch smooth mode for the web page.<br>The value **true** means to enable pinch smooth mode, and **false** means the opposite.<br>If **undefined** or **null** is passed in, the value is **false**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .pinchSmooth(true)
      }
    }
  }
  ```

## allowWindowOpenMethod<sup>10+</sup>

allowWindowOpenMethod(flag: boolean)

Sets whether to allow a new window to automatically open through JavaScript.

> **NOTE**
>
> - This API takes effect only when [javaScriptAccess](#javascriptaccess) is enabled.
> - This API opens a new window when [multiWindowAccess](#multiwindowaccess9) is enabled, and a local window when it is disabled.
> - The default value of **flag** is subject to the settings of the **persist.web.allowWindowOpenMethod.enabled** system attribute. If this attribute is not set, the default value of **flag** is **false**.
> - Run the **hdc shell param get persist.web.allowWindowOpenMethod.enabled** command to check whether the system attribute **persist.web.allowWindowOpenMethod.enabled** is enabled. If the attribute value is **1**, the system attribute is enabled. If the attribute value is **0** or does not exist, the system attribute is disabled. You can run the **hdc shell param set persist.web.allowWindowOpenMethod.enabled 1** command to enable the system attribute.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type   | Mandatory   | Description                     |
| ---- | ------- | ---- | ------------------------- |
| flag | boolean | Yes   | <br>Whether to allow a new window to automatically open through JavaScript. The value **true** means to allow a new window to automatically open through JavaScript, and **false** means only to allow a new window to automatically open through JavaScript using user behaviors.<br>The user behavior here refers to a user requests to open a new window (**window.open**) within 5 seconds after operating the **Web** component.<br>The default value of **flag** is subject to the settings of the **persist.web.allowWindowOpenMethod.enabled** system attribute. If this attribute is set to **true**, the default value of **flag** is **true**. If this attribute is not set, the default value of **flag** is **false**.|

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

// There are two Web components on the same page. When the WebComponent object opens a new window, the NewWebViewComp object is displayed.
@CustomDialog
struct NewWebViewComp {
    controller?: CustomDialogController;
    webviewController1: webview.WebviewController = new webview.WebviewController();

    build() {
        Column() {
            Web({ src: "", controller: this.webviewController1 })
                .javaScriptAccess(true)
                .multiWindowAccess(false)
                .onWindowExit(() => {
                    console.info("NewWebViewComp onWindowExit");
                    if (this.controller) {
                        this.controller.close();
                    }
                })
                .onActivateContent(() => {
                    // The Web component needs to be displayed in the foreground. The app is advised to perform tab or window switching here.
                    console.info("NewWebViewComp onActivateContent")
                })
        }
    }
}

@Entry
@Component
struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    dialogController: CustomDialogController | null = null;

    build() {
        Column() {
            Web({ src: $rawfile("index.html"), controller: this.controller })
                .javaScriptAccess(true)
                // MultiWindowAccess needs to be enabled.
                .multiWindowAccess(true)
                .allowWindowOpenMethod(true)
                .onWindowNew((event) => {
                    if (this.dialogController) {
                        this.dialogController.close()
                    }
                    let popController: webview.WebviewController = new webview.WebviewController();
                    this.dialogController = new CustomDialogController({
                        builder: NewWebViewComp({ webviewController1: popController }),
                        // Set isModal to false to prevent the new window from being destroyed, so that the onActivateContent callback can be triggered.
                        isModal: false
                    })
                    this.dialogController.open();
                    // Return the WebviewController object corresponding to the new window to the web kernel.
                    // If event.handler.setWebController is not called, the rendering process will be blocked.
                    // If no new window is created, set the value of event.handler.setWebController to null to notify the Web component that no new window is created.
                    event.handler.setWebController(popController);
                })
        }
    }
}
```

**Example of the HTML file**

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
<body>
<div>
    <button type="button" onclick="delayOpenwindow(5000)">delayOpenwindow_5s</button>
</div>

<script>
    function openwindowAll(){
        open("https://www.example.com","_blank","height=400,width=600,top=100,left=100,scrollbars=no")
    }
    function delayOpenwindow(t){
        setTimeout(openwindowAll, t);
    }
</script>
</body>
</html>
```

## mediaOptions<sup>10+</sup>

mediaOptions(options: WebMediaOptions)

Sets the web-based media playback policy, including the validity period for automatically resuming a paused web audio, and whether the audio of multiple **Web** instances in an application is exclusive. When this attribute is not explicitly set, the web audio cannot be automatically resumed after regaining the focus by default, and the audio of multiple **Web** instances in an application is exclusive.

> **NOTE**
>
> - Audios in the same **Web** instance are considered as the same audio.
> - The media playback policy controls videos with an audio track.
> - You are advised to set [audioExclusive](./arkts-basic-components-web-i.md#webmediaoptions10) to the same value for all **Web** components.
> - Audio and video interruption takes effect within an application and between applications, and playback resumption takes effect only between applications.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type                                 | Mandatory  | Description                                    |
| ------- | ------------------------------------- | ---- | ---------------------------------------- |
| options | [WebMediaOptions](./arkts-basic-components-web-i.md#webmediaoptions10) | Yes   | Web-based media playback policy.<br>After the parameter settings are updated, the playback must be started again for the settings to take effect.<br>When **undefined** or **null** is passed in, **{resumeInterval: 0, audioExclusive: true}** is used.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State options: WebMediaOptions = {resumeInterval: 10, audioExclusive: true};

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .mediaOptions(this.options)
      }
    }
  }
  ```

## javaScriptOnDocumentStart<sup>11+</sup>

javaScriptOnDocumentStart(scripts: Array\<ScriptItem>)

Injects a JavaScript script into the **Web** component. When the specified page or document starts to be loaded, the script is executed on any page whose source matches **scriptRules**. When this attribute is not explicitly called, JavaScript scripts are not injected into the **Web** component by default.

> **NOTE**
>
> - The script is injected after the root element (HTML Element) of the web document is created but before any other content is loaded.
>
> - The scripts are executed in lexicographic order, not in the order of the array. If the original array order is required, use the [runJavaScriptOnDocumentStart](#runjavascriptondocumentstart15) API instead.
>
> - When scripts with identical content are injected multiple times, they are silently deduplicated without display or notification, and the **scriptRules** from the first injection are used.
>
> - This API does not support [UrlRegexRule](./arkts-basic-components-web-i.md#urlregexrule23).
>
> - You are advised to use [runJavaScriptOnDocumentStart](#runjavascriptondocumentstart15) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type                               | Mandatory  | Description              |
| ------- | ----------------------------------- | ---- | ------------------ |
| scripts | Array\<[ScriptItem](./arkts-basic-components-web-i.md#scriptitem11)> | Yes   | Script item array to be injected.<br>When **undefined** or **null** is passed in, JavaScript scripts are not injected into **Web** components.|

**Example of the .ets file**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct Index {
      controller: webview.WebviewController = new webview.WebviewController();
      private localStorage: string =
          "if (typeof(Storage) !== 'undefined') {" +
          "   localStorage.setItem('color', 'Red');" +
          "}";
      @State scripts: Array<ScriptItem> = [
          { script: this.localStorage, scriptRules: ["*"] }
      ];

      build() {
          Column({ space: 20 }) {
              Web({ src: $rawfile('index.html'), controller: this.controller })
                  .javaScriptAccess(true)
                  .domStorageAccess(true)
                  .backgroundColor(Color.Grey)
                  .javaScriptOnDocumentStart(this.scripts)
                  .width('100%')
                  .height('100%')
          }
      }
  }
  ```

**Example of the HTML file**

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body style="font-size: 30px;" onload='bodyOnLoadLocalStorage()'>
      Hello world!
      <div id="result"></div>
  </body>
  <script type="text/javascript">
    function bodyOnLoadLocalStorage() {
      if (typeof(Storage) !== 'undefined') {
        document.getElementById('result').innerHTML = localStorage.getItem('color');
      } else {
        document.getElementById('result').innerHTML = 'Your browser does not support localStorage.';
      }
    }
  </script>
</html>
```

## javaScriptOnDocumentEnd<sup>11+</sup>

javaScriptOnDocumentEnd(scripts: Array\<ScriptItem>)

Injects a JavaScript script into the **Web** component. When the specified page or document has been loaded, the script is executed on any page whose source matches **scriptRules**. When this attribute is not explicitly called, JavaScript scripts are not injected into the **Web** component by default.

> **NOTE**
>
> - The script runs after any JavaScript code on the page, and the DOM tree has already been loaded and rendered at that point.
>
> - The scripts are executed in lexicographic order, not in the order of the array.
>
> - When scripts with identical content are injected multiple times, they are silently deduplicated without display or notification, and the **scriptRules** from the first injection are used.
>
> - This API does not support [UrlRegexRule](./arkts-basic-components-web-i.md#urlregexrule23).
>
> - You are advised to use [runJavaScriptOnDocumentEnd](#runjavascriptondocumentend15) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type                               | Mandatory  | Description              |
| ------- | ----------------------------------- | ---- | ------------------ |
| scripts | Array\<[ScriptItem](./arkts-basic-components-web-i.md#scriptitem11)> | Yes   | Script item array to be injected.<br>When **undefined** or **null** is passed in, JavaScript scripts are not injected into **Web** components.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct Index {
    controller: webview.WebviewController = new webview.WebviewController();
    private jsStr: string =
      "window.document.getElementById(\"result\").innerHTML = 'this is msg from javaScriptOnDocumentEnd'";
    @State scripts: Array<ScriptItem> = [
      { script: this.jsStr, scriptRules: ["*"] }
    ];

    build() {
      Column({ space: 20 }) {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .javaScriptAccess(true)
          .domStorageAccess(true)
          .backgroundColor(Color.Grey)
          .javaScriptOnDocumentEnd(this.scripts)
          .width('100%')
          .height('100%')
      }
    }
  }
  ```

```html
<!--index.html-->
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
</head>
<body style="font-size: 30px;">
Hello world!
<div id="result">test msg</div>
</body>
</html>
```

## runJavaScriptOnDocumentStart<sup>15+</sup>

runJavaScriptOnDocumentStart(scripts: Array\<ScriptItem>)

Injects a JavaScript script into the **Web** component. When the specified page or document starts to be loaded, the script is executed on any page whose source matches **scriptRules**. When this attribute is not explicitly called, JavaScript scripts are not injected into the **Web** component by default.

> **NOTE**
>
> - The script is injected after the root element (HTML Element) of the web document is created but before any other content is loaded.
>
> - The scripts are executed in the order of the array.
>
> - When scripts with identical content are injected multiple times, they are silently deduplicated without display or notification, and the **scriptRules** from the first injection are used.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type                               | Mandatory  | Description              |
| ------- | ----------------------------------- | ---- | ------------------ |
| scripts | Array\<[ScriptItem](./arkts-basic-components-web-i.md#scriptitem11)> | Yes   | Script item array to be injected.<br>When **undefined** or **null** is passed in, JavaScript scripts are not injected into **Web** components.|

**Example of the .ets file**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct Index {
      controller: webview.WebviewController = new webview.WebviewController();
      private localStorage: string =
          "if (typeof(Storage) !== 'undefined') {" +
          "   localStorage.setItem('color', 'Red');" +
          "}";
      private localStorage2: string =
          "console.info('runJavaScriptOnDocumentStart urlRegexRules Matching succeeded.')";
      @State scripts: Array<ScriptItem> = [
          { script: this.localStorage, scriptRules: ["*"] },
          { script: this.localStorage2, scriptRules: [], urlRegexRules: [{secondLevelDomain: "", rule: ".*index.html"}] }
      ];

      build() {
          Column({ space: 20 }) {
              Web({ src: $rawfile('index.html'), controller: this.controller })
                  .javaScriptAccess(true)
                  .domStorageAccess(true)
                  .backgroundColor(Color.Grey)
                  .runJavaScriptOnDocumentStart(this.scripts)
                  .width('100%')
                  .height('100%')
          }
      }
  }
  ```

**Example of the HTML file**

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body style="font-size: 30px;" onload='bodyOnLoadLocalStorage()'>
      Hello world!
      <div id="result"></div>
  </body>
  <script type="text/javascript">
    function bodyOnLoadLocalStorage() {
      if (typeof(Storage) !== 'undefined') {
        document.getElementById('result').innerHTML = localStorage.getItem('color');
      } else {
        document.getElementById('result').innerHTML = 'Your browser does not support localStorage.';
      }
    }
  </script>
</html>
```

## runJavaScriptOnDocumentEnd<sup>15+</sup>

runJavaScriptOnDocumentEnd(scripts: Array\<ScriptItem>)

Injects a JavaScript script into the **Web** component. When the specified page or document has been loaded, the script is executed on any page whose source matches **scriptRules**. When this attribute is not explicitly called, JavaScript scripts are not injected into the **Web** component by default.

> **NOTE**
>
> - The script runs after any JavaScript code on the page, and the DOM tree has already been loaded and rendered at that point.
>
> - The scripts are executed in the order of the array.
>
> - When scripts with identical content are injected multiple times, they are silently deduplicated without display or notification, and the **scriptRules** from the first injection are used.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type                               | Mandatory  | Description              |
| ------- | ----------------------------------- | ---- | ------------------ |
| scripts | Array\<[ScriptItem](./arkts-basic-components-web-i.md#scriptitem11)> | Yes   | Script item array to be injected.<br>When **undefined** or **null** is passed in, JavaScript scripts are not injected into **Web** components.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct Index {
    controller: webview.WebviewController = new webview.WebviewController();
    private jsStr: string =
      "window.document.getElementById(\"result\").innerHTML = 'this is msg from runJavaScriptOnDocumentEnd'";
    private jsStr2: string = "console.info('runJavaScriptOnDocumentEnd urlRegexRules Matching succeeded.')";
    @State scripts: Array<ScriptItem> = [
      { script: this.jsStr, scriptRules: ["*"] },
      { script: this.jsStr2, scriptRules: [], urlRegexRules: [{secondLevelDomain: "", rule: ".*index.html"}] }
    ];

    build() {
      Column({ space: 20 }) {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .javaScriptAccess(true)
          .domStorageAccess(true)
          .backgroundColor(Color.Grey)
          .runJavaScriptOnDocumentEnd(this.scripts)
          .width('100%')
          .height('100%')
      }
    }
  }
  ```

```html
<!--index.html-->
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
</head>
<body style="font-size: 30px;">
Hello world!
<div id="result">test msg</div>
</body>
</html>
```

## runJavaScriptOnHeadEnd<sup>15+</sup>

runJavaScriptOnHeadEnd(scripts: Array\<ScriptItem>)

Injects a JavaScript script into the **Web** component. When the **head** tag of the DOM tree is parsed, the script is executed on any page whose source matches **scriptRules**. When this attribute is not explicitly called, JavaScript scripts are not injected into the **Web** component by default.

> **NOTE**
>
> - This script is executed in the array order.
>
> - If a script with the same content is injected for multiple times, the script is silently deduplicated, not displayed, and no notification is displayed. The **scriptRules** of the first injection is used.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type                               | Mandatory  | Description              |
| ------- | ----------------------------------- | ---- | ------------------ |
| scripts | Array\<[ScriptItem](./arkts-basic-components-web-i.md#scriptitem11)> | Yes   | Script item array to be injected.<br>When **undefined** or **null** is passed in, JavaScript scripts are not injected into **Web** components.|

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  controller: webview.WebviewController = new webview.WebviewController();
  private jsStr: string =
    "window.document.getElementById(\"result\").innerHTML = 'this is msg from runJavaScriptOnHeadEnd'";
  private jsStr2: string = "console.info('runJavaScriptOnHeadEnd urlRegexRules Matching succeeded.')";
  @State scripts: Array<ScriptItem> = [
    { script: this.jsStr, scriptRules: ["*"] },
    { script: this.jsStr2, scriptRules: [], urlRegexRules: [{secondLevelDomain: "", rule: ".*index.html"}] }
  ];

  build() {
    Column({ space: 20 }) {
      Web({ src: $rawfile('index.html'), controller: this.controller })
        .javaScriptAccess(true)
        .domStorageAccess(true)
        .backgroundColor(Color.Grey)
        .runJavaScriptOnHeadEnd(this.scripts)
        .width('100%')
        .height('100%')
    }
  }
}
```

```html
<!--index.html-->
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
</head>
<body style="font-size: 30px;">
Hello world!
<div id="result">test msg</div>
</body>
</html>
```

## layoutMode<sup>11+</sup>

layoutMode(mode: WebLayoutMode)

Sets the layout mode of the **Web** component. If this attribute is not explicitly called, the **Web** layout follows the system mode (**WebLayoutMode.NONE**) by default. For common issues, see [Web Component Size Adapting to Page Content Layout](../../web/web-fit-content.md).
> **NOTE**
>
> Currently, only two **Web** layout modes are supported:
> - The **Web** layout follows the system mode (**WebLayoutMode.NONE**).
> - The **Web** component height adapts to the frontend page height (**WebLayoutMode.FIT_CONTENT**).
>
> The adaptive layout of the **Web** component height based on the frontend page has the following limitations:
> - When **layoutMode** is set to **WebLayoutMode.FIT_CONTENT**:
>    - [forceDisplayScrollBar](#forcedisplayscrollbar14) does not support persistent display.
>    - [blankScreenDetectionConfig](#blankscreendetectionconfig22) does not take effect.
> - If the width or height of the **Web** component exceeds 7680 px, specify the **RenderMode.SYNC_RENDER** mode when creating the **Web** component. Otherwise, the entire screen will be blank.
> - Dynamic switching of the **layoutMode** mode is not supported after the **Web** component is created.
> - **Web** component size specifications: When **RenderMode.ASYNC_RENDER** is specified, the width and height must not exceed 7680 px respectively.
> - Frequent changes to the page width and height will trigger re-layout of the **Web** component, affecting the user experience.
> - Waterfall layout web pages (loading more content when scrolling to the bottom) are not supported.
> - Width adaptation is not supported; only height adaptation is supported.
> - Because the height adapts to the web page height, you cannot modify the component height by changing the component height attribute.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type                                 | Mandatory  | Description                 |
| ---- | ------------------------------------- | ---- | --------------------- |
| mode | [WebLayoutMode](./arkts-basic-components-web-e.md#weblayoutmode11) | Yes | Specifies the Web layout mode, which can follow the system or adaptive layout.<br>When null or undefined is passed, `WebLayoutMode.NONE` is used. |

**Example**

  1. After specifying the **layoutMode** to **WebLayoutMode.FIT_CONTENT**, you need to explicitly specify the **renderMode** to **RenderMode.SYNC_RENDER**. Otherwise, rendering errors may occur when the viewport height exceeds 7680 px in the default **RenderMode.ASYNC_RENDER**.

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    mode: WebLayoutMode = WebLayoutMode.FIT_CONTENT;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller, renderMode: RenderMode.SYNC_RENDER })
          .layoutMode(this.mode)
      }
    }
  }
  ```

  2. After specifying the layoutMode to **WebLayoutMode.FIT_CONTENT**, you are advised to specify [overScrollMode](#overscrollmode11) to **OverScrollMode.NEVER**. Otherwise, when the web page scrolls to the edge in the nested scrolling scenario, the rebounding effect is triggered first, which affects user experience.

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    layoutMode: WebLayoutMode = WebLayoutMode.FIT_CONTENT;
    @State overScrollMode: OverScrollMode = OverScrollMode.NEVER;

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller, renderMode: RenderMode.SYNC_RENDER })
          .layoutMode(this.layoutMode)
          .overScrollMode(this.overScrollMode)
      }
    }
  }
  ```

## nestedScroll<sup>11+</sup>

nestedScroll(value: NestedScrollOptions | NestedScrollOptionsExt)

Sets nested scrolling options.

> **NOTE**
>
> - You can set the up, down, left, and right directions, or set the forward and backward nested scrolling modes to implement scrolling linkage with the parent component.
> - Containers that support nested scrolling: [Grid](../apis-arkui/arkui-ts/ts-container-grid.md), [List](../apis-arkui/arkui-ts/ts-container-list.md), [Scroll](../apis-arkui/arkui-ts/ts-container-scroll.md), [Swiper](../apis-arkui/arkui-ts/ts-container-swiper.md), [Tabs](../apis-arkui/arkui-ts/ts-container-tabs.md), [WaterFlow](../apis-arkui/arkui-ts/ts-container-waterflow.md), [Refresh](../apis-arkui/arkui-ts/ts-container-refresh.md) and [bindSheet](../apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#bindsheet).
> - Input sources that support nested scrolling: gestures, mouse device, and touchpad.
> - In nested scrolling scenarios, since the **Web** component's over-scrolling to the edge will trigger the over-scroll bounce effect first, it is recommended that you set [overScrollMode](#overscrollmode11) to **OverScrollMode.NEVER** to avoid undermining user experience.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                                    | Mandatory  | Description            |
| ----- | ---------------------------------------- | ---- | ---------------- |
| value | [NestedScrollOptions](../apis-arkui/arkui-ts/ts-container-scrollable-common.md#nestedscrolloptions10)\| [NestedScrollOptionsExt](./arkts-basic-components-web-i.md#nestedscrolloptionsext14)<sup>14+</sup> | Yes   | Nested scrolling options.<br> When the value is of the **NestedScrollOptions** type (forward and backward), the default nested scrolling mode of the **scrollForward** and **scrollBackward** options is [NestedScrollMode.SELF_FIRST](../apis-arkui/arkui-ts/ts-appendix-enums.md#nestedscrollmode10).<br> When the value is of the **NestedScrollOptionsExt** type (up, down, left, and right), the default nested scrolling mode of the **scrollUp**, **scrollDown**, **scrollLeft**, and **scrollRight** options is **NestedScrollMode.SELF_FIRST**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';
  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .nestedScroll({
            scrollForward: NestedScrollMode.SELF_FIRST,
            scrollBackward: NestedScrollMode.SELF_FIRST,
          })
      }
    }
  }
  ```

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';
  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController()
    build() {
      Scroll(){
        Column() {
          Text("Nested Web")
            .height("25%")
            .width("100%")
            .fontSize(30)
            .backgroundColor(Color.Yellow)
          Web({ src: $rawfile('index.html'),
                controller: this.controller })
            .nestedScroll({
              scrollUp: NestedScrollMode.SELF_FIRST,
              scrollDown: NestedScrollMode.PARENT_FIRST,
              scrollLeft: NestedScrollMode.SELF_FIRST,
              scrollRight: NestedScrollMode.SELF_FIRST,
            })
        }
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
  <head>
      <meta name="viewport" id="viewport" content="width=device-width, initial-scale=1.0">
      <style>
          .blue {
            background-color: lightblue;
          }
          .green {
            background-color: lightgreen;
          }
          .blue, .green {
          font-size:16px;
          height:200px;
          text-align: center;       /* Horizontally centered */
          line-height: 200px;       /* Vertically centered (the height matches the container height) */
          }
      </style>
  </head>
  <body>
  <div class="blue" >webArea</div>
  <div class="green">webArea</div>
  <div class="blue">webArea</div>
  <div class="green">webArea</div>
  <div class="blue">webArea</div>
  <div class="green">webArea</div>
  <div class="blue">webArea</div>
  </body>
  </html>
  ```

## enableScrollDirectionalLock

enableScrollDirectionalLock(value: boolean, type: ScrollDirectionalLockType) 

Sets the scroll direction lock for the **Web** component to prevent simultaneous horizontal and vertical scrolling when the user swipes diagonally, thereby improving the scrolling experience. If this method is not explicitly called, scroll direction lock is supported by default in nested scrolling scenarios. The **ALL** mode applies to all scenarios where scroll locking is needed, while the **NESTED_SCROLL** mode applies only to nested scrolling scenarios.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type     | Mandatory | Description |
| ------ | ---------------- | ---- | -------- |
| value  | boolean                   | Yes   | Whether to enable scroll direction lock. The value **true** means the scroll direction is locked, and the scroll view locks the scroll axis based on the user's initial swipe direction. The value **false** means no locking.        |
| type   | [ScrollDirectionalLockType](./arkts-basic-components-web-e.md#scrolldirectionallocktype) | Yes   | Specifies the scenarios in which the **Web** component applies scroll direction lock. **ALL** means scroll lock is supported in all scenarios, and **NESTED_SCROLL** means scroll lock is supported in nested scrolling scenarios. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Web({ src: 'www.example.com', controller: this.controller })
        .width('100%')
        .height('100%')
        // Supports locking of the scroll direction in all scenarios.
        .enableScrollDirectionalLock(true, ScrollDirectionalLockType.ALL)
    }
  }
}
```

## bypassVsyncCondition<sup>20+</sup>

bypassVsyncCondition(condition: WebBypassVsyncCondition)

Sets the rendering process to bypass vsync (vertical synchronization) scheduling and directly trigger drawing when the **scrollBy** API is called to scroll the page. When this attribute is not explicitly called, vsync scheduling is not skipped by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type                                 | Mandatory  | Description                 |
| ---- | ------------------------------------- | ---- | --------------------- |
| condition | [WebBypassVsyncCondition](./arkts-basic-components-web-e.md#webbypassvsynccondition20) | Yes   | Condition for triggering the rendering process to bypass vsync scheduling.<br> When **undefined** or **null** is passed in, the value is **NONE**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    condition: WebBypassVsyncCondition = WebBypassVsyncCondition.SCROLLBY_FROM_ZERO_OFFSET;

    build() {
      Column() {
        Button('scrollBy')
          .onClick(() => {
            this.controller.scrollBy(0, 5);
          })
        Web({ src: 'www.example.com', controller: this.controller })
          .bypassVsyncCondition(this.condition)
      }
    }
  }
  ```

## enableNativeEmbedMode<sup>11+</sup>

enableNativeEmbedMode(enabled: boolean)

Sets whether to enable the same-layer rendering feature. When this method is not explicitly called, the same-layer rendering feature is disabled by default.

> **NOTE**
>
> APIs such as [registerNativeEmbedRule](#registernativeembedrule12) and [nativeEmbedOptions](#nativeembedoptions16) take effect only when this attribute is enabled.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                     | Mandatory  | Description            |
| ----- | ---------------------------------------- | ---- | ---------------- |
| enabled |  boolean | Yes   | Whether to enable the same-layer rendering feature.<br>The value **true** means to enable the same-layer rendering feature, and **false** means the opposite.<br>When **undefined** or **null** is passed in, the value is **false**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';
  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .enableNativeEmbedMode(true)
      }
    }
  }
  ```

## forceDisplayScrollBar<sup>14+</sup>

forceDisplayScrollBar(enabled: boolean)

Sets whether the scroll bar is always visible. Under the always-visible settings, when the page size exceeds one page, the scroll bar appears and remains visible. When this attribute is not explicitly called, the scroll bar is not always visible by default.

When **layoutMode** is set to **WebLayoutMode.FIT_CONTENT**, the **enabled** parameter is set to **false**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type| Mandatory| Description          |
| ------- | -------- | ---- | ------------------ |
| enabled | boolean | Yes | Whether the scroll bar is always displayed.<br>The value **true** indicates that the scroll bar is always displayed, and **false** indicates the opposite.<br>When layoutMode is set to WebLayoutMode.FIT_CONTENT, the enabled parameter is forcibly set to **false**, and setting it to **true** does not take effect.<br>If **undefined** or **null** is passed in, the attribute setting does not take effect. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .forceDisplayScrollBar(true)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Demo</title>
      <style>
        body {
          width:2560px;
          height:2560px;
          padding-right:170px;
          padding-left:170px;
          border:5px solid blueviolet;
        }
      </style>
  </head>
  <body>
  Scroll Test
  </body>
  </html>
  ```

## registerNativeEmbedRule<sup>12+</sup>

registerNativeEmbedRule(tag: string, type: string)

Registers the HTML tag name and type for same-layer rendering. The tag name only supports <object\> and <embed\>. The tag type only supports visible ASCII characters.

If the specified type is the same as the W3C standard <object\> or <embed\> type, the ArkWeb kernel identifies the type as a non-same-layer tag.

This API is also controlled by **enableNativeEmbedMode** and does not take effect when same-layer rendering is disabled. When this API is not used, the ArkWeb kernel recognizes the <embed\> tags with the "native/" prefix as same-layer tags.

For details, see [Using Same-Layer Rendering](../../web/web-same-layer.md#rendering-text-boxes-at-the-same-layer-on-web-pages).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type  | Mandatory  | Description            |
|------|--------| ---- |------------------|
| tag  | string | Yes   | Tag name.            |
| type | string | Yes  | Tag type. The ArkWeb kernel uses a prefix to match this parameter.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';
  import { NodeController, BuilderNode, NodeRenderType, FrameNode, UIContext } from '@kit.ArkUI';

  declare class Params {
    text: string;
    width: number;
    height: number;
  }

  declare class NodeControllerParams {
    surfaceId: string;
    renderType: NodeRenderType;
    width: number;
    height: number;
  }

  class MyNodeController extends NodeController {
    private rootNode: BuilderNode<[Params]> | undefined | null;
    private surfaceId_: string = "";
    private renderType_: NodeRenderType = NodeRenderType.RENDER_TYPE_DISPLAY;
    private width_: number = 0;
    private height_: number = 0;

    setRenderOption(params: NodeControllerParams) {
      this.surfaceId_ = params.surfaceId;
      this.renderType_ = params.renderType;
      this.width_ = params.width;
      this.height_ = params.height;
    }

    makeNode(uiContext: UIContext): FrameNode | null {
      this.rootNode = new BuilderNode(uiContext, { surfaceId: this.surfaceId_, type: this.renderType_ });
      this.rootNode.build(wrapBuilder(ButtonBuilder), { text: "myButton", width: this.width_, height: this.height_ });
      return this.rootNode.getFrameNode();
    }

    postInputEvent(event: TouchEvent | MouseEvent | undefined): boolean {
      return this.rootNode?.postInputEvent(event) as boolean;
    }
  }

  @Component
  struct ButtonComponent {
    @Prop params: Params;
    @State bkColor: Color = Color.Red;

    build() {
      Column() {
        Button(this.params.text)
          .height(50)
          .width(200)
          .border({ width: 2, color: Color.Red })
          .backgroundColor(this.bkColor)
      }
      .width(this.params.width)
      .height(this.params.height)
    }
  }

  @Builder
  function ButtonBuilder(params: Params) {
    ButtonComponent({ params: params })
      .backgroundColor(Color.Green)
  }

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    private nodeController: MyNodeController = new MyNodeController();
    uiContext: UIContext = this.getUIContext();

    build() {
      Column() {
        Stack() {
          NodeContainer(this.nodeController)
          Web({ src: $rawfile('index.html'), controller: this.controller })
             // Enable same-layer rendering.
            .enableNativeEmbedMode(true)
             // Register the same-layer tag of <object> and type of "native."
            .registerNativeEmbedRule("object", "native")
             // Obtain the lifecycle change data of the <object> tag.
            .onNativeEmbedLifecycleChange((object) => {
              if (object.status == NativeEmbedStatus.CREATE) {
                this.nodeController.setRenderOption({
                  surfaceId: object.surfaceId as string,
                  renderType: NodeRenderType.RENDER_TYPE_TEXTURE,
                  width: this.uiContext!.px2vp(object.info?.width),
                  height: this.uiContext!.px2vp(object.info?.height)
                });
                this.nodeController.rebuild();
              }
            })
        }
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
      <title>Same-Layer Rendering Test</title>
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
  </head>
  <body>
  <div>
      <div id="bodyId">
          <object id="nativeButton" type ="native/button" width="300" height="300" style="background-color:red">
          </object>
      </div>
  </div>
  </body>
  </html>
  ```

## defaultTextEncodingFormat<sup>12+</sup>

defaultTextEncodingFormat(textEncodingFormat: string)

Sets the default text encoding format for the web page. When this attribute is not explicitly called, the default text encoding format of the web page is UTF-8.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type  | Mandatory  | Description                                    |
| ---- | ------ | ---- | ---------------------------------------- |
| textEncodingFormat | string | Yes   | Default text encoding format.<br>When **null** or **undefined** is passed in, the value is **UTF-8**.  |

  **Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          // Set the height.
          .height(500)
          .defaultTextEncodingFormat("UTF-8")
          .javaScriptAccess(true)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
      <meta name="viewport" content="width=device-width" />
      <title>My test html5 page</title>
  </head>
  <body>
      <p>Hello world!</p>
  </body>
  </html>
  ```

## metaViewport<sup>12+</sup>

metaViewport(enabled: boolean)

Sets whether the **viewport** attribute of the **meta** tag is enabled. When this attribute is not explicitly called, the **viewport** attribute of the **meta** tag is supported by default.

> **NOTE**
>
> - Whether the **viewport** attribute of the **\<meta>** tag in the frontend HTML page is enabled is determined by checking whether the User-Agent contains the "Mobile" field. When the User-Agent does not contain the "Mobile" field, the **viewport** attribute in the **\<meta>** tag is disabled by default. In this case, you can explicitly set the **metaViewport** attribute to **true** to override the disabled state.

**System capability**: SystemCapability.Web.Webview.Core

**Device behavior difference:** This API can be called on phones, wearables, and TVs, but does not work on PCs or 2in1 devices. For tablets, the **viewport-fit** attribute in the **meta** tag will be parsed no matter whether this parameter is set to **true** or **false**. When **viewport-fit** is set to **cover**, the size of the safe area can be obtained through the CSS attribute.

**Parameters**

| Name| Type| Mandatory| Description                        |
| ------ | -------- | ---- | -------------------------------- |
| enabled | boolean  | Yes  | Whether the **viewport** attribute of the **meta** tag is enabled.<br>The value **true** indicates that the **viewport** attribute of the **meta** tag is enabled and parsed, and the layout is performed based on the **viewport** attribute.<br>The value **false** indicates the **viewport** attribute of the **meta** tag is disabled and not parsed, and the default layout is used.<br>When **null** or **undefined** is passed in, the value is **true**.|

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Web({ src: $rawfile('index.html'), controller: this.controller })
        .metaViewport(true)
    }
  }
}
```

HTML file to be loaded:

```html
<!--index.html-->
<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
    <p>Hello world!</p>
</body>
</html>
```

## textAutosizing<sup>12+</sup>

textAutosizing(textAutosizing: boolean)

Sets whether to enable automatic font sizing for the **Web** component. When no attribute is explicitly called, automatic font sizing is enabled for the **Web** component by default.

After automatic font sizing takes effect, any text smaller than 16 px is enlarged to fall between 16 px and 32 px. This eliminates readability issues on narrow screens (viewport < 980 px) where mobile-specific layouts are absent.

> **NOTE**
>
> - The preconditions for automatic font sizing to take effect are as follows:
>   - The device type should be phone, tablet, wearable, or TV.
>   - The viewport width of the **Web** component is less than 980 px.
>   - The page is text-heavy: font size (px) × character count ≥ 3920.
>   - **metaViewport** is not set on the frontend, or the **metaViewport** does not contain the **width** and **initial-scale** attributes.

**System capability**: SystemCapability.Web.Webview.Core

**Device behavior**: This API has no effect on the PCs/2-in-1 devices and works on other devices.

**Parameters**

| Name | Type  | Mandatory  | Description                                    |
| ---- | ------ | ---- | ---------------------------------------- |
| textAutosizing | boolean | Yes   | Whether to enable automatic text resizing.<br>The value **true** means to enable automatic text resizing, and **false** means the opposite.<br>When **undefined** or **null** is passed in, the value is **true**.|

  **Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .textAutosizing(false)
      }
    }
  }
  ```

## enableNativeMediaPlayer<sup>12+</sup>

enableNativeMediaPlayer(config: NativeMediaPlayerConfig)

Sets whether to enable the [application to take over web page media playback](../../web/app-takeovers-web-media.md). When this attribute is not explicitly called, the web page media playback takeover feature is disabled by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type  | Mandatory  | Description|
| ---- | ------ | ---- | ---------------------|
| config | [NativeMediaPlayerConfig](./arkts-basic-components-web-i.md#nativemediaplayerconfig12) | Yes | Configuration object for the app to take over web media playback. It contains the following attributes: enable (boolean type, whether to enable this feature, default value: false), shouldOverlay (boolean type, whether the player view of the app taking over web video playback overlays the web content after the feature is enabled, default value: false).<br>If undefined or null is passed, it is equivalent to `{enable: false, shouldOverlay: false}`.|

  **Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .enableNativeMediaPlayer({enable: true, shouldOverlay: false})
      }
    }
  }
  ```

## onAdsBlocked<sup>12+</sup>

onAdsBlocked(callback: OnAdsBlockedCallback)

Called after an ad is blocked on the web page to notify the user of detailed information about the blocked ad. To reduce the frequency of notifications and minimize the impact on the page loading process, only the first notification is made when the page is fully loaded. Subsequent blocking events are reported at intervals of 1 second, and no notifications are sent if there is no ad blocked.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description                 |
| ------ | ------ | ---- | --------------------- |
| callback       | [OnAdsBlockedCallback](./arkts-basic-components-web-t.md#onadsblockedcallback12) | Yes| Callback of **onAdsBlocked**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    @State totalAdsBlockCounts: number = 0;
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'https://www.example.com', controller: this.controller })
        .onAdsBlocked((details: AdsBlockedDetails) => {
          if (details) {
            console.info(' Blocked ' + details.adsBlocked.length + ' in ' + details.url);
            let adList: Array<string> = Array.from(new Set(details.adsBlocked));
            this.totalAdsBlockCounts += adList.length;
            console.info('Total blocked counts :' + this.totalAdsBlockCounts);
          }
        })
      }
    }
  }
  ```

## keyboardAvoidMode<sup>12+</sup>

keyboardAvoidMode(mode: WebKeyboardAvoidMode)

Sets the custom soft keyboard avoidance mode.

If the keyboard avoidance mode set in **UIContext** is [KeyboardAvoidMode.RESIZE](../apis-arkui/arkts-apis-uicontext-e.md#keyboardavoidmode11), this API does not take effect.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name             | Type                             | Mandatory  | Description         |
| ------------------- | ------------------------------   | ------ | ------------- |
| mode | [WebKeyboardAvoidMode](./arkts-basic-components-web-e.md#webkeyboardavoidmode12) | Yes    | Web soft keyboard avoidance mode.<br>In the nested scrolling scenario, the soft keyboard avoidance mode of the **Web** component is not recommended, including **RESIZE_VISUAL** and **RESIZE_CONTENT**.<br>Default value: **WebKeyboardAvoidMode.RESIZE_CONTENT**|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State avoidMode: WebKeyboardAvoidMode = WebKeyboardAvoidMode.RESIZE_VISUAL;

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
        .keyboardAvoidMode(this.avoidMode)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
    <title>Test Web Page</title>
  </head>
  <body>
    <input type="text" placeholder="Text">
  </body>
  </html>
  ```

## editMenuOptions<sup>12+</sup>

editMenuOptions(editMenu: EditMenuOptions)

Sets a custom text selection menu for the **Web** component.

> **NOTE**
> This API is similar to **bindSelectionMenu**, with the following differences:
> - **editMenuOptions**: Adds extension items based on the system default menu style, with the trigger conditions unchanged.
> - [bindSelectionMenu](#bindselectionmenu13): Fully customizes the menu style and trigger conditions, as defined by the developer.
> It is not recommended to use both at the same time. Choose based on the degree of customization required.

You can use this attribute to customize a text menu.

You can use [onCreateMenu](../apis-arkui/arkui-ts/ts-text-common.md#oncreatemenu12) to modify, add, and delete menu options. If you do not want to display the text menu, return an empty array.

You can use [onMenuItemClick](../apis-arkui/arkui-ts/ts-text-common.md#onmenuitemclick12) to customize the callback for menu options. This function is triggered after a menu option is clicked and determines whether to execute the default callback based on the return value. If **true** is returned, the system callback is not executed. If **false** is returned, the system callback is executed.

In [onPrepareMenu<sup>20+</sup>](../apis-arkui/arkui-ts/ts-text-common.md#properties-1), this callback is triggered after the text selection area changes and before the menu is displayed. You can modify, add, or delete menu options in the callback to dynamically update the menu.

If this method is used together with [selectionMenuOptions<sup>(deprecated)</sup>](#selectionmenuoptionsdeprecated), the **selectionMenuOptions<sup> (deprecated) </sup>** method does not take effect.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name             | Type                             | Mandatory  | Description         |
| ------------------- | ------------------------------   | ------ | ------------- |
| editMenu | [EditMenuOptions](../apis-arkui/arkui-ts/ts-text-common.md#editmenuoptions) | Yes | Custom text menu options for the Web component.<br>The number of menu items, the content size, and the icon size are consistent with those of the ArkUI [Menu](../apis-arkui/arkui-ts/ts-basic-components-menu.md) component.<br>Among the system-provided ID enum values ([TextMenuItemId](../apis-arkui/arkui-ts/ts-text-common.md#textmenuitemid12)) in the menu, only CUT, COPY, PASTE, SELECT_ALL, TRANSLATE, SEARCH, and AI_WRITER are supported in the Web component.<br>In the onMenuItemClick function, the textRange parameter is meaningless in the Web component, and the value passed in is -1.|

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

let selectText:string = '';
class TestClass {
  setSelectText(param: String) {
    selectText = param.toString();
  }
}

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  @State testObj: TestClass = new TestClass();

  onCreateMenu(menuItems: Array<TextMenuItem>): Array<TextMenuItem> {
    let items = menuItems.filter((menuItem) => {
      // Filter the menu items as required.
      return (
        menuItem.id.equals(TextMenuItemId.CUT) ||
        menuItem.id.equals(TextMenuItemId.COPY) ||
        menuItem.id.equals((TextMenuItemId.PASTE)) ||
        menuItem.id.equals((TextMenuItemId.TRANSLATE)) ||
        menuItem.id.equals((TextMenuItemId.SEARCH)) ||
        menuItem.id.equals((TextMenuItemId.AI_WRITER))
      )
    });
    let customItem1: TextMenuItem = {
      content: 'customItem1',
      id: TextMenuItemId.of('customItem1'),
      icon: $r('app.media.icon')
    };
    let customItem2: TextMenuItem = {
      content: $r('app.string.customItem2'),
      id: TextMenuItemId.of('customItem2'),
      icon: $r('app.media.icon')
    };
    items.push(customItem1);// Add an item to the end of the item list.
    items.unshift(customItem2);// Add an item to the beginning of the item list.

    return items;
  }

  onMenuItemClick(menuItem: TextMenuItem, textRange: TextRange): boolean {
    if (menuItem.id.equals(TextMenuItemId.CUT)) {
      // Custom behavior
      console.info("Intercept ID: CUT")
      // The value **true** means intercepting this menu item and skipping the default system cut operation.
      return true;
    } else if (menuItem.id.equals(TextMenuItemId.COPY)) {
      // Custom behavior
      console.info("Not intercept ID: COPY")
      // The value **false** means not intercepting this menu item and performing the default system copy operation.
      return false;
    } else if (menuItem.id.equals(TextMenuItemId.of('customItem1'))) {
      // Custom behavior
      console.info("Intercept ID: customItem1")
      return true;// Custom menu item. If true is returned, the menu is not closed after being clicked. If false is returned, the menu is closed.
    } else if (menuItem.id.equals((TextMenuItemId.of($r('app.string.customItem2'))))){
      // Custom behavior
      console.info("Intercept ID: app.string.customItem2")
      return true;
    }
    return false;// Return the default value false.
  }

   onPrepareMenu = (menuItems: Array<TextMenuItem>) => {
    let item1: TextMenuItem = {
      content: 'prepare1',
      id: TextMenuItemId.of('prepareMenu1'),
    };
    let item2: TextMenuItem = {
      content: 'prepare2' + selectText,
      id: TextMenuItemId.of('prepareMenu2'),
    };
    menuItems.push(item1);// Add an item to the end of the item list.
    menuItems.unshift(item2);// Add an item to the beginning of the item list.

    return menuItems;
  }

  @State EditMenuOptions: EditMenuOptions =
    { onCreateMenu: this.onCreateMenu, onMenuItemClick: this.onMenuItemClick, onPrepareMenu:this.onPrepareMenu }

  build() {
    Column() {
      Web({ src: $rawfile("index.html"), controller: this.controller })
        .editMenuOptions(this.EditMenuOptions)
        .javaScriptProxy({
          object: this.testObj,
          name: "testObjName",
          methodList: ["setSelectText"],
          controller: this.controller,
        })
    }
  }
}
```

 HTML file to be loaded:

```html
<!--index.html-->
<!DOCTYPE html>
<html>
  <head>
      <title>Test Web Page</title>
  </head>
  <body>
    <h1>editMenuOptions Demo</h1>
    <span>edit menu options</span>
    <script>
      document.addEventListener('selectionchange', () => {
        var selection = window.getSelection();
        if (selection.rangeCount > 0) {
          var selectedText = selection.toString();
          testObjName.setSelectText(selectedText);
        }
      });
  </script>
  </body>
</html>
```

## enableHapticFeedback<sup>13+</sup>

enableHapticFeedback(enabled: boolean)

Sets whether to enable haptic feedback for long-pressed text in the **Web** component. The **ohos.permission.VIBRATE** permission must be declared. When this attribute is not explicitly called, haptic feedback is enabled by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type       | Mandatory  | Description|
| --------- | ---------   | ------ | ------------- |
| enabled   | boolean | Yes  | Whether to enable vibration.<br>The value **true** indicates that vibration is enabled, and **false** indicates the opposite.<br>If **undefined** or **null** is passed, the default value is used, which means vibration is enabled. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Web({ src: $rawfile("index.html"), controller: this.controller })
      .enableHapticFeedback(true)
    }
  }
}
```

 HTML file to be loaded:

```html
<!--index.html-->
<!DOCTYPE html>
<html>
  <head>
      <title>Test Web Page</title>
  </head>
  <body>
    <h1>enableHapticFeedback Demo</h1>
    <span>enable haptic feedback</span>
  </body>
</html>
```

## bindSelectionMenu<sup>13+</sup>

bindSelectionMenu(elementType: WebElementType, content: CustomBuilder, responseType: WebResponseType, options?: SelectionMenuOptionsExt)

Sets the custom selection menu.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name      | Type                            | Mandatory| Description                               |
| ------------ | ------------------------------- | ---- | ----------------------------------- |
| elementType     | [WebElementType](./arkts-basic-components-web-e.md#webelementtype13)             | Yes  | Menu type.  |
| content      | [CustomBuilder](../apis-arkui/arkui-ts/ts-types.md#custombuilder8)     | Yes  | Menu content.  |
| responseType | [WebResponseType](./arkts-basic-components-web-e.md#webresponsetype13)           | Yes  | Response type of the menu.|
| options      | [SelectionMenuOptionsExt](./arkts-basic-components-web-i.md#selectionmenuoptionsext13)   | No   | Menu options. The default configuration is used when undefined or null is passed in.|

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { pasteboard } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface PreviewBuilderParam {
  width: number;
  height: number;
  url:Resource | string | undefined;
}

interface PreviewBuilderParamForImage {
  previewImage: Resource | string | undefined;
  width: number;
  height: number;
}


@Builder function PreviewBuilderGlobalForImage($$: PreviewBuilderParamForImage) {
  Column() {
    Image($$.previewImage)
      .objectFit(ImageFit.Fill)
      .autoResize(true)
  }.width($$.width).height($$.height)
}

@Entry
@Component
struct SelectionMenuLongPress {
  controller: webview.WebviewController = new webview.WebviewController();
  previewController: webview.WebviewController = new webview.WebviewController();
  @Builder PreviewBuilder($$: PreviewBuilderParam){
    Column() {
      Stack(){
        Text("") // Select whether to display the URL.
          .padding(5)
          .width('100%')
          .textAlign(TextAlign.Start)
          .backgroundColor(Color.White)
          .copyOption(CopyOptions.LocalDevice)
          .maxLines(1)
          .textOverflow({overflow:TextOverflow.Ellipsis})
        Progress({ value: this.progressValue, total: 100, type: ProgressType.Linear }) // Display the progress bar.
          .style({ strokeWidth: 3, enableSmoothEffect: true })
          .backgroundColor(Color.White)
          .opacity(this.progressVisible?1:0)
          .backgroundColor(Color.White)
      }.alignContent(Alignment.Bottom)
      Web({src:$$.url,controller: new webview.WebviewController()})
        .javaScriptAccess(true)
        .fileAccess(true)
        .onlineImageAccess(true)
        .imageAccess(true)
        .domStorageAccess(true)
        .onPageBegin(()=>{
          this.progressValue = 0;
          this.progressVisible = true;
        })
        .onProgressChange((event)=>{
          this.progressValue = event.newProgress;
        })
        .onPageEnd(()=>{
          this.progressVisible = false;
        })
        .hitTestBehavior(HitTestMode.None) // Disable the gesture response during web page preview.
    }.width($$.width).height($$.height) // Set the preview width and height.
  }

  private result: WebContextMenuResult | undefined = undefined;
  @State previewImage: Resource | string | undefined = undefined;
  @State previewWidth: number = 1;
  @State previewHeight: number = 1;
  @State previewWidthImage: number = 1;
  @State previewHeightImage: number = 1;
  @State linkURL:string = "";
  @State progressValue:number = 0;
  @State progressVisible:boolean = true;
  uiContext: UIContext = this.getUIContext();
  enablePaste = false;

  clearSelection() {
    try {
      this.controller.runJavaScript(
        'clearSelection()',
        (error, result) => {
          if (error) {
            console.error(`run clearSelection JavaScript error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
            return;
          }
          if (result) {
            console.info(`The clearSelection() return value is: ${result}`);
          }
        });
    } catch (error) {
      console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
    }
  }


  @Builder
  LinkMenuBuilder() {
    Menu() {
      MenuItem({ content: 'Copy Link', })
        .onClick(() => {
          const pasteboardData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, this.linkURL);
          const systemPasteboard = pasteboard.getSystemPasteboard();
          systemPasteboard.setData(pasteboardData);
        })
      MenuItem({content:'Open Link'})
        .onClick(()=>{
          this.controller.loadUrl(this.linkURL);
        })
    }
  }
  @Builder
  ImageMenuBuilder() {
    Menu() {
      MenuItem({ content: 'Copy Image', })
        .onClick(() => {
          this.result?.copyImage();
          this.result?.closeContextMenu();
        })
    }
  }
  @Builder
  TextMenuBuilder() {
    Menu() {
      MenuItem({ content: 'Copy', })
        .onClick(() => {
          try {
            this.controller.runJavaScript(
              'copySelectedText()',
              (error, result) => {
                if (error) {
                  console.error(`run copySelectedText JavaScript error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
                  return;
                }
                if (result) {
                  console.info(`The copySelectedText() return value is: ${result}`);
                }
              });
          } catch (error) {
            console.error(`Failed to clear selection. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
          }
          this.clearSelection()
        }).backgroundColor(Color.Pink)
    }
  }
  build() {
    Column() {
      Web({ src: $rawfile("index.html"), controller: this.controller })
        .javaScriptAccess(true)
        .fileAccess(true)
        .onlineImageAccess(true)
        .imageAccess(true)
        .domStorageAccess(true)
        .bindSelectionMenu(WebElementType.TEXT, this.TextMenuBuilder, WebResponseType.LONG_PRESS,
          {
            onAppear: () => {},
            onDisappear: () => {},
            menuType: MenuType.SELECTION_MENU,
          })
        .bindSelectionMenu(WebElementType.LINK, this.LinkMenuBuilder, WebResponseType.LONG_PRESS,
          {
            onAppear: () => {},
            onDisappear: () => {
              this.result?.closeContextMenu();
            },
            preview: this.PreviewBuilder({
              width: 500,
              height: 400,
              url:this.linkURL
            }),
            menuType: MenuType.PREVIEW_MENU
          })
        .bindSelectionMenu(WebElementType.IMAGE, this.ImageMenuBuilder, WebResponseType.LONG_PRESS,
          {
            onAppear: () => {},
            onDisappear: () => {
              this.result?.closeContextMenu();
            },
            preview: PreviewBuilderGlobalForImage({
              previewImage: this.previewImage,
              width: this.previewWidthImage,
              height: this.previewHeightImage,
            }),
            menuType: MenuType.PREVIEW_MENU,
          })
        .zoomAccess(true)
        .onContextMenuShow((event) => {
          if (event) {
            this.result = event.result;
            this.previewWidthImage = this.uiContext!.px2vp(event.param.getPreviewWidth());
            this.previewHeightImage = this.uiContext!.px2vp(event.param.getPreviewHeight());
            if (event.param.getSourceUrl().indexOf("resource://rawfile/") == 0) {
              this.previewImage = $rawfile(event.param.getSourceUrl().substring(19));
            } else {
              this.previewImage = event.param.getSourceUrl();
            }
            this.linkURL = event.param.getLinkUrl()
            // The value **true** indicates that the system default context menu is intercepted and a custom menu is used.
            return true;
          }
          return false;
        })
    }

  }
  // Swipe back
  onBackPress(): boolean | void {
    if (this.controller.accessStep(-1)) {
      this.controller.backward();
      return true;
    } else {
      return false;
    }
  }
}
```

 HTML file to be loaded:

```html
<!--index.html-->
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Touch and hold to copy text</title>
    <style>
        .container {
            background-color: white;
            padding: 30px;
            margin: 20px 0;
        }

        .context {
            line-height: 1.8;
            font-size: 18px;
        }

        .context span {
            border-radius: 8px;
            background-color: #f8f9fa;
        }

        .context a {
            color: #3498db;
            text-decoration: none;
            font-size: 18px;
            font-weight: 600;
            padding: 12px 24px;
            border: 2px solid #3498db;
            border-radius: 30px;
            display: inline-block;
            position: relative;
            overflow: hidden;
            margin-bottom: 20px;
        }

        .context img {
            max-width: 100%;
            height: auto;
            display: block;
            margin-bottom: 20px;
        }

        .context:hover img {
            transform: scale(1.05);
        }
    </style>
</head>
<body>
<div class="container">

    <div class="context">
        <!--img.png is in the same directory as the html file-->
        <img src="img.png">
    </div>

    <div class="context">
        <a  href="https://www.example.com">Touch and hold the link to display the menu</a>
    </div>

    <div class="context">
        <span>In this digital age, the text copying functionality has grown increasingly important. Whether quoting famous remarks, saving key information, or sharing interesting content, copying text is an integral part of our daily operations.</span>
    </div>

</div>
<br>

<script>
    function copySelectedText() {
        const selectedText = window.getSelection().toString();
        if (selectedText.length > 0) {
            // Use the Clipboard API to copy text.
            navigator.clipboard.writeText(selectedText)
                .then(() => {
                    showNotification();
                })
                .catch(err => {
                    console.error('Copy failed:', err);
                });
        }
    }
     function clearSelection() {
        if (window.getSelection) {
            window.getSelection().removeAllRanges();
        }
    }
</script>
</body>
</html>
```

## blurOnKeyboardHideMode<sup>14+</sup>

blurOnKeyboardHideMode(mode: BlurOnKeyboardHideMode)

Sets the blur mode for **Web** elements when the soft keyboard is dismissed. If this attribute is not explicitly called, the [BlurOnKeyboardHideMode.SILENT](./arkts-basic-components-web-e.md#bluronkeyboardhidemode14) mode is used by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type                                   | Mandatory  | Description              |
| ---- | --------------------------------------- | ---- | ------------------ |
| mode | [BlurOnKeyboardHideMode](./arkts-basic-components-web-e.md#bluronkeyboardhidemode14) | Yes   | Whether to enable blur mode of the web element when soft keyboard is hidden. The default value is **BlurOnKeyboardHideMode.SILENT**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State blurMode: BlurOnKeyboardHideMode = BlurOnKeyboardHideMode.BLUR;
    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .blurOnKeyboardHideMode(this.blurMode)
      }
    }
  }
  ```

 HTML file to be loaded:

```html
<!--index.html-->
<!DOCTYPE html>
<html>
  <head>
      <title>Test Web Page</title>
  </head>
  <body>
    <h1>blurOnKeyboardHideMode Demo</h1>
    <input type="text" id="input_a">
    <script>
      const inputElement = document.getElementById('input_a');
      inputElement.addEventListener('blur', function() {
        console.info('Input has lost focus');
      });
    </script>
  </body>
</html>
```

## enableFollowSystemFontWeight<sup>18+</sup>

enableFollowSystemFontWeight(follow: boolean)

Sets whether the **Web** component can change the font weight according to the system settings. When this attribute is not explicitly called, the **Web** component can change the font weight according to the system settings by default.

> **NOTE**
>
> Currently, only front-end text elements support this capability. The **canvas** element and embedded .docx and .pdf texts do not support this capability.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name      | Type                            | Mandatory| Description                               |
| ------------ | ------------------------------- | ---- | ----------------------------------- |
| follow | boolean | Yes   | Whether the **Web** component can change the font weight according to the system settings.<br>The value **true** means that the **Web** component can change the font weight according to the system settings, and **false** means the opposite.<br>When **undefined** or **null** is passed in, the value is **true**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    build() {
      Column() {
        Web({ src: "www.example.com", controller: this.controller })
          .enableFollowSystemFontWeight(true)
      }
    }
  }
  ```

## optimizeParserBudget<sup>15+</sup>

optimizeParserBudget(optimizeParserBudget: boolean)

Sets whether to enable segment-based HTML parsing optimization. If no attribute is explicitly called, the parsing time is used as the segment point by default.

To avoid occupying too many main thread resources and enable progressive loading of web pages, the ArkWeb kernel uses the segment-based parsing policy when parsing the HTML files. By default, the ArkWeb kernel uses the parsing time as the segment point. When the parsing time exceeds the threshold, the parsing is interrupted and then the layout and rendering operations are performed.

After optimization is enabled, the ArkWeb kernel not only checks whether the parsing time exceeds the limit, but also additionally determines whether the number of parsed tokens (the smallest parsing units of an HTML document, such as `<div>`, `attr="xxx"`, etc.) exceeds the threshold specified by the kernel, and lowers this threshold. When the FCP (First Contentful Paint) of the page is triggered, the default interrupt judgment logic is restored. This makes the parsing operations before FCP more frequent, thereby increasing the possibility that the first-frame content is parsed and enters the rendering phase earlier, while effectively reducing the rendering workload of the first frame, ultimately advancing the FCP time.

When the FCP of a page is triggered, the default segment parsing logic is restored. Therefore, the segment-based HTML parsing optimization takes effect only for the first page loaded by each **Web** component.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name       | Type   | Mandatory  | Description                  |
| ---------- | ------- | ---- | ---------------------- |
| optimizeParserBudget | boolean | Yes   | Whether to enable segment-based HTML parsing optimization.<br>The value **true** means to use the number of parsed records instead of the parsing time as the segment point for HTML segment parsing, and reduce the upper limit of the number of parsed records in each segment. The value **false** means to use the parsing time as the segment point for HTML segment parsing.<br>If **undefined** or **null** is passed in, the value is **false**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController()
    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .optimizeParserBudget(true)
      }
    }
  }
  ```

## enableWebAVSession<sup>18+</sup>

enableWebAVSession(enabled: boolean)

Sets whether to support an application to connect to media controller. If this attribute is not explicitly set, the application can connect to media controller by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type| Mandatory| Description          |
| ------- | -------- | ---- | ------------------ |
| enabled | boolean  | Yes  | Whether to support an application to connect to media controller.<br>The value **true** means to support an application to connect to media controller, and **false** means the opposite.<br>When **undefined** or **null** is passed in, the value is **true**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .enableWebAVSession(true)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
      <title>Video Playback Page</title>
  </head>
  <body>
      <h1>Video Playback</h1>
      <video id="testVideo" controls>
          <!--Save an MP4 media file in the rawfile directory of resources and name it example.mp4.-->
          <source src="example.mp4" type="video/mp4">
      </video>
  </body>
  </html>
  ```

## nativeEmbedOptions<sup>16+</sup>

nativeEmbedOptions(options?: EmbedOptions)

Sets the same-layer rendering configuration. This attribute takes effect only when [enableNativeEmbedMode](#enablenativeembedmode11) is enabled and cannot be dynamically modified. If this attribute is not explicitly called, the default value **{supportDefaultIntrinsicSize: false}** is used.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name      | Type                            | Mandatory| Description                               |
| ------------ | ------------------------------- | ---- | ----------------------------------- |
| options | [EmbedOptions](./arkts-basic-components-web-i.md#embedoptions16) | No   | Configuration options of the same-layer rendering.<br>If **undefined** or **null** is passed in, the value **{supportDefaultIntrinsicSize: false}** is used.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    options: EmbedOptions = {supportDefaultIntrinsicSize: true};

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .enableNativeEmbedMode(true)
          .nativeEmbedOptions(this.options)
      }
    }
  }
  ```

HTML file to be loaded:

  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
  <head>
      <title>Same-Layer Rendered Fixed-Size HTML Test</title>
  </head>
  <body>
  <div>
      <embed id="input" type = "native/view" style = "background-color:red"/>
  </div>
  </body>
  </html>
  ```

## enableDataDetector<sup>20+</sup>

enableDataDetector(enable: boolean)

Sets whether to recognize special entities of web texts, such as emails, phone numbers, and URLs. This API depends on the text recognition capability at the bottom layer of the device. Otherwise, the setting is invalid. When this attribute is not explicitly called, the detector is disabled by default.

> **NOTE**
>
> Attributes such as [dataDetectorConfig](#datadetectorconfig20) and [enableSelectedDataDetector](#enableselecteddatadetector22) take effect only when this attribute is enabled.

If **enableDataDetector** is set to **true** and [dataDetectorConfig](#datadetectorconfig20) is not set, all types of entities will be recognized, and the **color** and **decoration** attributes of the recognized entities will be changed to the following styles:

<!--code_no_check-->

```ts
color: '#ff0a59f7',
decoration:{
  type: TextDecorationType.Underline,
  color: '#ff0a59f7',
  style: TextDecorationStyle.SOLID
}
```

When **enableDataDetector** is set to **true** and [copyOptions](#copyoptions11) is set to **CopyOptions.LocalDevice**, the AI menu feature is activated. In this case, after text is selected on the web page, the text selection menu can display the corresponding AI menu items, including **url** (open link), **email** (create new email), **phoneNumber** (call), **address** (navigate to the location), and **dateTime** (create new schedule reminder) from [TextMenuItemId](../apis-arkui/arkui-ts/ts-text-common.md#textmenuitemid12).

When the AI menu takes effect, the corresponding option can be displayed only when the selection contains a complete AI entity. This menu item and the askAI menu item in [TextMenuItemId](../apis-arkui/arkui-ts/ts-text-common.md#textmenuitemid12) do not appear at the same time.

For details about the application scenario, see [Using Smart Text Data Detector](../../web/web-data-detector.md).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type   | Mandatory| Description                             |
| ------ | ------- | ---- | --------------------------------- |
| enable  | boolean | Yes  | Whether to enable web text recognition. The value **true** means to enable web text recognition, and **false** means the opposite.<br>When **undefined** or **null** is passed in, the attribute setting does not take effect.|

> **NOTE**
> 
> Dynamically updating the **enableDataDetector** status does not affect the current page immediately. You need to refresh the page for the new configuration to take effect.

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .enableDataDetector(true)
      }
    }
  }
  ```

HTML file to be loaded:

  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
  <head>
      <title>Example enableDataDetector</title>;
  </head>
  <body>
      <p> Telephone: 400-123-4567 </p>
      <p>Email: example@example.com </p>
  </body>
  </html>
  ```

## dataDetectorConfig<sup>20+</sup>

dataDetectorConfig(config: TextDataDetectorConfig)

Configures text recognition settings.

This API must be used together with [enableDataDetector](#enabledatadetector20). It takes effect only when **enableDataDetector** is set to **true**.

When entities A and B overlap, the following rules are followed:

1. If A is a subset of B (A ⊂ B), then B is retained; otherwise, A is retained.

2. If A is not a subset of B (A ⊄ B) and B is not a subset of A (B ⊄ A), and if the starting point of A is earlier than that of B (A.start < B.start), then A is retained; otherwise, B is retained.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type                                                       | Mandatory| Description                                                        |
| ------ | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| config | [TextDataDetectorConfig](../apis-arkui/arkui-ts/ts-text-common.md#textdatadetectorconfig11)| Yes  | Text recognition configuration.|

> **NOTE**
> 
> The **onDetectResultUpdate** method in **TextDataDetectorConfig** is not supported in the **Web** component. The configured callback will not be called.
>
> When [copyOptions](#copyoptions11) is set to **CopyOptions.None**, the **enablePreviewMenu** item in **TextDataDetectorConfig** is invalid.
> 
> Dynamically updating the **TextDataDetectorConfig** configuration does not affect the current page immediately. You need to refresh the page for the new configuration to take effect.

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .enableDataDetector(true)
          .dataDetectorConfig({
            types: [
              TextDataDetectorType.PHONE_NUMBER,
              TextDataDetectorType.EMAIL
            ],
            color: Color.Red,
            decoration: {
              type: TextDecorationType.LineThrough,
              color: Color.Green,
              style: TextDecorationStyle.WAVY
            }
          })
      }
    }
  }
  ```

HTML file to be loaded:

  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
  <head>
      <title>Example dataDetectorConfig</title>;
  </head>
  <body>
      <p> Telephone: 400-123-4567 </p>
      <p> Email: 12345678901@example.com </p>
      <p> Website: www.example.com (cannot be identified) </p>
  </body>
  </html>
  ```

## enableSelectedDataDetector<sup>22+</sup>

enableSelectedDataDetector(enable: boolean)

Sets whether to enable the AI menu feature for text selection menu. After the AI menu feature is enabled, the email, phone number, website, date, and address in the selection can be identified, and the corresponding AI menu items are displayed in the text selection menu. By default, the AI menu feature is enabled.

When the AI menu feature is enabled, after text is selected on the web page, the text selection menu can display the corresponding AI menu items, including **url** (open link), **email** (create new email), **phoneNumber** (call), **address** (navigate to the location), and **dateTime** (create new schedule) from [TextMenuItemId](../apis-arkui/arkui-ts/ts-text-common.md#textmenuitemid12).

When the AI menu takes effect, the corresponding option can be displayed only when the selection contains a complete AI entity. This menu item and the askAI menu item in [TextMenuItemId](../apis-arkui/arkui-ts/ts-text-common.md#textmenuitemid12) do not appear at the same time.

For details about the application scenario, see [Using Smart Text Data Detector](../../web/web-data-detector.md).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type   | Mandatory| Description                             |
| ------ | ------- | ---- | --------------------------------- |
| enable  | boolean | Yes  | Whether to enable web text recognition. The value **true** means to enable web text recognition, and **false** means the opposite.<br>If **undefined** or **null** is passed in, the attribute is reset to the default value.|

> **NOTE**
>
> If **enableSelectedDataDetector** is not set or is set to **true**, the **types** in [dataDetectorConfig](#datadetectorconfig20) are used. If **dataDetectorConfig** is not set, all types are recognized by default.
> 
> If **enableSelectedDataDetector** is set to false, the AI menu for text selection is not activated.

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .enableSelectedDataDetector(true)
      }
    }
  }
  ```

HTML file to be loaded:

  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
  <head>
      <title>enableSelectedDataDetector Example</title>
  </head>
  <body>
      <p> Telephone: 400-123-4567 </p>
      <p>Email: example@example.com </p>
  </body>
  </html>
  ```

## gestureFocusMode<sup>20+</sup>

gestureFocusMode(mode: GestureFocusMode)

Sets the gesture focus mode of the **Web** component, which controls the focus response behavior of the **Web** component. If this attribute is not explicitly called, the default behavior is that any gesture causes the **Web** component to gain focus when the gesture is pressed.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name             | Type                             | Mandatory  | Description         |
| ------------------- | ------------------------------   | ------ | ------------- |
| mode | [GestureFocusMode](./arkts-basic-components-web-e.md#gesturefocusmode20) | Yes    | Gesture focus mode of the **Web** component. If **undefined** or **null** is passed in, the value **GestureFocusMode.DEFAULT** is used.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State mode: GestureFocusMode = GestureFocusMode.DEFAULT;
    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .gestureFocusMode(this.mode)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
    <title>Test Web Page</title>
  </head>
  <body>
    <input type="text" placeholder="Text">
  </body>
  </html>
  ```

## rotateRenderEffect<sup>22+</sup>

rotateRenderEffect(effect: WebRotateEffect)

Sets how the final state of the **Web** component's content is rendered during its width and height animation process when the component rotates. If this attribute is not explicitly called, by default, the component's content stays at the final size and always aligned with the upper left corner of the component.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name             | Type                             | Mandatory  | Description         |
| ------------------- | ------------------------------   | ------ | ------------- |
| effect | [WebRotateEffect](./arkts-basic-components-web-e.md#webrotateeffect22) | Yes    | How the final state of the **Web** component's content is rendered during its width and height animation process when the component rotates.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State effect: WebRotateEffect = WebRotateEffect.TOPLEFT_EFFECT;
    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .rotateRenderEffect(this.effect)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
    <title>Test Web Page</title>
  </head>
  <body>
    <p>Test Web Page</p>
  </body>
  </html>
  ```

## forceEnableZoom<sup>21+</sup>

forceEnableZoom(enable: boolean)

Sets whether to enable the forcible zoom functionality for the **Web** component.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name       | Type   | Mandatory  | Description         |
| ---------- | ------- | ---- | ------------- |
| enable | boolean | Yes   | Whether to comply with the zoom restriction specified by the **\<meta name="viewport">** tag on the web page.<br>The value **true** means to not comply with the web page zoom restriction, and **false** means the opposite.<br>When **undefined** or **null** is passed in, the attribute setting does not take effect.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .forceEnableZoom(true)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no">
    <title>Test Web Page</title>
  </head>
  <body>
    <h1>forceEnableZoom Demo</h1>
    <span>You can scale page when forceEnableZoom is true.</span>
  </body>
  </html>
  ```

## backToTop<sup>22+</sup>

backToTop(backToTop: boolean)

Sets whether to enable the back-to-top feature for the **Web** component when the status bar is touched. When this attribute is not explicitly called, the back-to-top feature for the status bar is enabled by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type   | Mandatory| Description                             |
| ------ | ------- | ---- | --------------------------------- |
| backToTop  | boolean | Yes  | Whether to enable the back-to-top feature. The value **true** means to enable the feature, and **false** means the opposite.<br>When **undefined** or **null** is passed in, the value is **true**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .backToTop(true)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
  <head>
      <meta name="viewport" id="viewport" content="width=device-width, initial-scale=1.0">
      <style>
          .blue {
            background-color: lightblue;
          }
          .green {
            background-color: lightgreen;
          }
          .blue, .green {
           font-size:16px;
           height:200px;
           text-align: center;       /* Horizontally centered */
           line-height: 200px;       /* Vertically centered (the height matches the container height) */
          }
      </style>
  </head>
  <body>
  <div class="blue" >webArea</div>
  <div class="green">webArea</div>
  <div class="blue">webArea</div>
  <div class="green">webArea</div>
  <div class="blue">webArea</div>
  <div class="green">webArea</div>
  <div class="blue">webArea</div>
  <div class="green">webArea</div>
  <div class="blue">webArea</div>
  </body>
  </html>
  ```

## blankScreenDetectionConfig<sup>22+</sup>

blankScreenDetectionConfig(detectConfig: BlankScreenDetectionConfig)

Sets the blank screen detection configuration, such as whether to enable the detection, detection time, and detection policy. When this attribute is not explicitly called, blank screen detection is disabled by default.

> **NOTE**
>
> - Based on the configuration of **detectConfig**, [onDetectedBlankScreen](./arkts-basic-components-web-events.md#ondetectedblankscreen22) may be triggered when a blank screen or near-blank screen is detected after a web page is loaded.
> - The setting takes effect in the next navigation.
> - After the user interacts with the web page, the system does not check whether a blank screen occurs.
> - This feature is not supported when **layoutMode** is set to **WebLayoutMode.FIT_CONTENT**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name       | Type   | Mandatory  | Description         |
| ---------- | ------- | ---- | ------------- |
| detectConfig | [BlankScreenDetectionConfig](./arkts-basic-components-web-i.md#blankscreendetectionconfig22) | Yes   | Blank screen detection policy.|

**Example**

  ```ts
  // blankScreenDetectionConfig.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .blankScreenDetectionConfig({
            enable: true,
            detectionTiming: [2, 4, 6, 8],
            contentfulNodesCountThreshold: 4,
            detectionMethods:[BlankScreenDetectionMethod.DETECTION_CONTENTFUL_NODES_SEVENTEEN]
          })
          .onDetectedBlankScreen((event: BlankScreenDetectionEventInfo)=>{
            console.info(`Found blank screen on ${event.url}.`);
            console.info(`The blank screen reason is ${event.blankScreenReason}.`);
            console.info(`The blank screen detail is ${event.blankScreenDetails?.detectedContentfulNodesCount}.`);
          })
      }
    }
  }
  ```

## enableImageAnalyzer<sup>23+</sup>

enableImageAnalyzer(enable: boolean)

Sets whether to enable AI analysis of web page images. Currently, the image text recognition feature is supported. If this attribute is not explicitly called, this feature is enabled by default.

> **NOTE**
>
> When you long-press or hover the mouse over the image text, AI analyzer is triggered and the text in the image can be selected. The specifications of images that can trigger analyzer are as follows:
>
> - The original width and height of the image are greater than or equal to 100 pixels.
>
> - For [devices](../../quick-start/module-configuration-file.md#devicetypes) other than 2-in-1 devices, the image rendering width must exceed 80% of the web page width.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type   | Mandatory| Description                             |
| ------ | ------- | ---- | --------------------------------- |
| enable  | boolean | Yes  | Whether to enable AI analyzer for web page images. The value **true** means to enable AI analyzer, and **false** means the opposite.<br>If **undefined** or **null** is passed in, the value is reset to **true**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .enableImageAnalyzer(true) // To disable the image analyzer, set this parameter to false.
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" id="viewport" content="width=device-width, initial-scale=1.0">
    <style>
      .image-container {
        width: 90%;
      }
      .image-container img {
        width: 100%;
        height: auto;
      }
    </style>
  </head>
  <body>
    <div class="image-container">
      <!--example.jpg is in the same directory as the HTML file-->
      <img src="example.jpg" alt="Image to be analyzed by AI">
    </div>
  </body>
  </html>
  ```

## enableAutoFill<sup>23+</sup>

enableAutoFill(value: boolean)

Sets whether to enable web page autofill. By default, this feature is enabled.

<!--RP1-->

> **NOTE**
>
> The autofill feature of this API depends on SmartFill service and Password Autofill Service.

<!--RP1End-->

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type   | Mandatory| Description                             |
| ------ | ------- | ---- | --------------------------------- |
| value  | boolean | Yes  | Whether to enable autofill for web pages. The value **true** means to enable autofill, and **false** means the opposite.<br>When **undefined** or **null** is passed in, the value is **true**.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .enableAutoFill(true)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
    <head>
      <meta content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0;" name="viewport"/>
      <title>Autofill test</title>
    </head>
    <body>
      <h4 align="center">Autofill test</h4>
      <form method="post" action="">
        <div align="center">
          <label for="name" style="width: 120px; display: inline-block; text-align: end;">Name:</label>
          <input type="text" id="name" autocomplete="name"/><br/><br/>
          <label for="tel-national" style="width: 120px; display: inline-block; text-align: end;">Mobile number:</label>
          <input type="text" id="tel-national" autocomplete="tel-national"/><br/><br/>
        </div>
        <div align="center">
          <button type="submit" style="width: 80px">Submit</button>
        </div>
      </form>
    </body>
  </html>
  ```

## enableDefaultContextMenu<sup>24+</sup>

enableDefaultContextMenu(enable: boolean)

Sets whether to enable the default right-click context menu. If this method is not explicitly called, the menu is disabled by default. The default menu supports only the **CUT**, **COPY**, **PASTE**, and **SELECT_ALL** menu items.

> **NOTE**
>
> - When the [onContextMenuShow](./arkts-basic-components-web-events.md#oncontextmenushow9) callback is set and returns **true** in the callback, the setting of this API does not take effect.
> - The default menu items are controlled by [editMenuOptions](#editmenuoptions12), through which you can customize the menu options.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type    | Mandatory | Description                                    |
| ------- | ------- | ---- | --------------------------------------- |
| enable  | boolean | Yes   | Whether to enable the default right-click context menu. The value **true** means enabled, and **false** means disabled.<br>When **undefined** or **null** is passed, the value is **false**. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .enableDefaultContextMenu(true)
      }
    }
  }
  ```

## enableDrag

enableDrag(value: boolean)

Sets whether to enable the drag function. If this attribute is not explicitly called, the web page drag function is enabled by default.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters** 

| Name | Type    | Mandatory | Description                              |
| ------ | ------- | ---- | --------------------------------- |
| value  | boolean | Yes   | Whether to enable the web page drag function. The value **true** means enabled, and **false** means disabled. When **undefined** or **null** is passed, the value is **true**. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct Index {
    private controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile('test.html'), controller: this.controller })
          .enableDrag(false)
      }
    }
  }
  ```

 HTML file to be loaded.

```html
<!--test.html-->
<!DOCTYPE html>
<html>
  <head><meta charset="UTF-8"><title>drag test</title></head>
  <body>
    <div id="drag" draggable="true" style="width:100px;height:100px;background:red;margin:20px;"></div>
    <div id="drop" style="width:200px;height:200px;background:gray;margin:20px;"></div>
    <script>
      drag.ondragstart=e=>e.dataTransfer.setData('text/plain','');
      drop.ondragover=e=>e.preventDefault();
      drop.ondrop=e=>{e.preventDefault(); drop.style.background='green';};
      drag.ondragend=()=>{drop.style.background='gray';};
    </script>
  </body>
</html>
```

## password<sup>(deprecated)</sup>

password(password: boolean)

Sets whether to save the password. This API is an empty API.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 10. You are advised to use [enableAutoFill<sup>23+</sup>](#enableautofill23) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type  | Mandatory | Description                            |
| ------------ | ------ | ---- | -------------------------------- |
| password | boolean | Yes | Whether to allow the web component to save passwords. The value **true** means the web component is allowed to save passwords, and **false** means the opposite. If **undefined** or **null** is passed, the default value **false** is used. |

## textZoomAtio<sup>(deprecated)</sup>

textZoomAtio(textZoomAtio: number)

Sets the text zoom ratio of the page.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [textZoomRatio<sup>9+</sup>](#textzoomratio9) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type  | Mandatory | Description                            |
| ------------ | ------ | ---- | -------------------------------- |
| textZoomAtio | number | Yes | Text zoom percentage of the page to set. The value 100 indicates the original size, a value greater than 100 indicates zoom-in, and a value less than 100 indicates zoom-out.<br>The value range is (0, 2147483647]. |

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct WebComponent {
    controller: WebController = new WebController()
    @State ratio: number = 150
    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .textZoomAtio(this.ratio)
      }
    }
  }
  ```

## userAgent<sup>(deprecated)</sup>

userAgent(userAgent: string)

Sets the user agent.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 10. You are advised to use [setCustomUserAgent](./arkts-apis-webview-WebviewController.md#setcustomuseragent10)<sup>10+</sup> instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name      | Type  | Mandatory  | Description     |
| --------- | ------ | ---- | --------- |
| userAgent | string | Yes   | User agent to set.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State userAgent:string = 'Mozilla/5.0 (Phone; OpenHarmony 5.0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36 ArkWeb/4.1.6.1 Mobile DemoApp';

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
          .userAgent(this.userAgent)
      }
    }
  }
  ```

## tableData<sup>(deprecated)</sup>

tableData(tableData: boolean)

Sets whether to save form data. When this attribute is not explicitly called, the **Web** component is allowed to save form data by default. This API is an empty API.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 10. You are advised to use [enableAutoFill<sup>23+</sup>](#enableautofill23) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type  | Mandatory | Description                            |
| ------------ | ------ | ---- | -------------------------------- |
| tableData | boolean | Yes | Whether to allow the Web component to save form data. The value **true** means the Web component is allowed to save form data, and **false** means the opposite. If **undefined** or **null** is passed, the value is **true**. |

## wideViewModeAccess<sup>(deprecated)</sup>

wideViewModeAccess(wideViewModeAccess: boolean)

Sets whether to support the **viewport** attribute of the HTML **\<meta>** tag. This API is an empty API.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 10. You are advised to use [metaViewport<sup>12+</sup>](#metaviewport12) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name             | Type                                                        | Mandatory  | Description         |
| ------------------- | ----------------------------------------------------------    | ---- | ------------- |
| wideViewModeAccess | boolean | Yes   | Whether to support the **viewport** attribute of the HTML **\<meta>** tag.<br>The value **true** means to support the **viewport** attribute of the HTML **\<meta>** tag, and **false** means the opposite.|

## selectionMenuOptions<sup>(deprecated)</sup>

selectionMenuOptions(expandedMenuOptions: Array\<ExpandedMenuItemOptions>)

Sets the extended options of the custom context menu on selection, including the text content, icon, and callback.

The API only supports the selection of plain text; if the selected content contains images or other non-text elements, the **action** information may display garbled content.

> **NOTE**
>
> When used together with [editMenuOptions](#editmenuoptions12), this API does not take effect.
>
> This API is supported since API version 12 and deprecated since API version 20. You are advised to use [editMenuOptions<sup>12+</sup>](#editmenuoptions12) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name             | Type                                                        | Mandatory  | Description         |
| ------------------- | ----------------------------------------------------------    | ---- | ------------- |
| expandedMenuOptions | Array<[ExpandedMenuItemOptions](./arkts-basic-components-web-i.md#expandedmenuitemoptionsdeprecated)> | Yes   | Extended options of the custom context menu on selection.<br>The number of menu options, menu content size, and start icon size must be the same as those of the ArkUI [Menu](../apis-arkui/arkui-ts/ts-basic-components-menu.md) component.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State menuOptionArray: Array<ExpandedMenuItemOptions> = [
      {content: 'Apple', startIcon: $r('app.media.icon'), action: (selectedText) => {
        console.info('select info ' + selectedText.toString());
      }},
      {content: 'Banana', startIcon: $r('app.media.icon'), action: (selectedText) => {
        console.info('select info ' + selectedText.toString());
      }}
    ];

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
        .selectionMenuOptions(this.menuOptionArray)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
    <title>Test Web Page</title>
  </head>
  <body>
    <h1>selectionMenuOptions Demo</h1>
    <span>selection menu options</span>
  </body>
  </html>
  ```

## zoomControlAccess<sup>22+</sup>

zoomControlAccess(zoomControlAccess: boolean)

Sets whether to allow zooming by pressing **Ctrl + '-/+'** or **Ctrl** + mouse wheel/touchpad.

If this attribute is not explicitly called, zooming by pressing **Ctrl + '-/+'** or **Ctrl** + mouse wheel/touchpad is allowed by default.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name       | Type   | Mandatory  | Description         |
| ---------- | ------- | ---- | ------------- |
| zoomControlAccess | boolean | Yes | Whether to allow zooming through key combinations. The value **true** means the zooming is supported, and **false** means the opposite. If null or undefined is passed, the default value **false** is used.|

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .zoomControlAccess(true)
      }
    }
  }
  ```

  HTML file to be loaded:

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Test Web Page</title>
  </head>
  <body>
    <h1>zoomControlAccess Demo</h1>
    <span>You can zoom in/out page when zoomControlAccess is true.</span>
  </body>
  </html>
  ```

## aiSessionOptions

aiSessionOptions(aiSessions: Array&lt;AISessionEvent&gt;)

Configures custom frontend AI sessions for the **Web** component, used to register multiple custom AI sessions.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| aiSessions | Array&lt;[AISessionEvent](./arkts-basic-components-web-i.md#aisessionevent)&gt; | Yes   | Array of frontend AI session configuration objects. Each object contains an AI session type and the corresponding lifecycle callback methods. Currently, only models included in [AISessionType](./arkts-basic-components-web-e.md#aisessiontype) are supported. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct DemoPage {
  private webController: webview.WebviewController = new webview.WebviewController();
  sessions: Map<string, string> = new Map<string, string>();

  onCreateAISession = (id: string, params: string, result: OnAISessionCallback): boolean => {
    this.sessions.set(id, params); // Simulate creating an AI session.
    console.info(`[AISession]onCreateAISession params: ${params}`);
    // Notify the caller that the AI session is created successfully.
    result(AISessionResultType.SUCCESS, "AISession created");
    return true;
  }

  onExecuteAIAction = (id: string, params: string, result: OnAISessionCallback): void => {
    this.sessions.get(id); // Simulate retrieving the session and executing an action.
    console.info(`[AISession]onExecuteAIAction params: ${params}`);
    // Simulate streaming the AI execution result: multiple RUNNING calls indicate the task is in progress and return data chunks, and a final SUCCESS call indicates task completion.
    result(AISessionResultType.RUNNING, "AISession chunk 1\n");
    result(AISessionResultType.RUNNING, "AISession chunk 2\n");
    result(AISessionResultType.SUCCESS, "AISession chunk end\n");
  }

  onDestroyAISession = (id: string): void => {
    this.sessions.delete(id); // Simulate destroying the session and releasing resources.
  }

  @State options: AISessionEvent = {
    aiSessionType: AISessionType.SUMMARIZER,
    onCreateAISession: this.onCreateAISession,
    onExecuteAIAction: this.onExecuteAIAction,
    onDestroyAISession: this.onDestroyAISession
  }

  build() {
    Column() {
      Web({ src: $rawfile('index.html'), controller: this.webController })
        .aiSessionOptions([this.options])
    }
    .width('100%')
    .height('100%')
  }
}

```

HTML file to be loaded

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <title>Summarizer API Test</title>
</head>
<body style="max-width:600px;margin:20px auto;padding:0 16px;">
  <p id="status">checking...</p>
  <button id="initBtn" onclick="init()">Create Session</button>
  <br><br>
  <textarea id="input" rows="6" style="width:100%;font:inherit" placeholder="paste text to summarize"></textarea>
  <br><br>
  <button id="btn" onclick="run()" disabled>Summarize</button>
  <pre id="result"></pre>
  <script>
    let s;
    (async () => {
      const d = document.getElementById('status');
      if (!('Summarizer' in self)) { d.textContent = 'API not supported'; return; }
      const a = await Summarizer.availability();
      d.textContent = 'Summarizer: ' + a;
      if (a === 'unavailable') document.getElementById('initBtn').disabled = true;
    })();

    async function init() {
      const d = document.getElementById('status'), ib = document.getElementById('initBtn');
      ib.disabled = true;
      d.textContent = 'creating...';
      try {
        s = await Summarizer.create({
          type: 'tldr', length: 'medium', format: 'plain-text',
          monitor(m) { m.addEventListener('downloadprogress', e => { d.textContent = 'downloading ' + (e.loaded * 100 | 0) + '%' }); }
        });
        d.textContent = 'ready';
        document.getElementById('btn').disabled = false;
      } catch (e) { d.textContent = 'Error: ' + e.message; ib.disabled = false; }
    }

    async function run() {
      const t = document.getElementById('input').value.trim();
      if (!t || !s) return;
      const btn = document.getElementById('btn'), r = document.getElementById('result');
      btn.disabled = true;
      r.textContent = '...';
      try { r.textContent = await s.summarize(t); }
      catch (e) { r.textContent = 'Error: ' + e.message; }
      btn.disabled = false;
    }
  </script>
</body>
</html>
```

## scrollbarLayoutPolicy

scrollbarLayoutPolicy(policy: ScrollbarLayoutPolicy)

Selects the layout mode of the vertical scrollbar within the **Web** component, used to adapt to the writing direction of different languages. The **CONTENT** mode is suitable for scenarios where the web page CSS **direction** attribute needs to be followed, while the **SYSTEM** mode is suitable for scenarios in multilingual apps where the system language direction needs to be followed, such as for right-to-left languages like Arabic and Hebrew.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Since**: 26.0.0

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | -------------- | ---- | -------------- |
| policy | [ScrollbarLayoutPolicy](./arkts-basic-components-web-e.md#scrollbarlayoutpolicy) | Yes   | Sets the layout mode of the vertical scrollbar within the **Web** component. Options: **CONTENT** (follows the web page CSS **direction** attribute), **SYSTEM** (lays out according to the left-to-right or right-to-left writing direction of the system language. For right-to-left languages, the scrollbar is laid out on the left side. This applies to all nested scrollbars within the web page). |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Web({ src: 'www.example.com', controller: this.controller })
        .width('100%')
        .height('100%')
        // Set to SYSTEM to follow the system language direction layout. Set to CONTENT to use the Web style layout.
        .scrollbarLayoutPolicy(ScrollbarLayoutPolicy.SYSTEM)
    }
  }
}
```

## keyboardAppearance

keyboardAppearance(mode: WebKeyboardAppearanceMode)

Sets the keyboard appearance mode, which controls the appearance style of the keyboard that pops up for input boxes in the **Web** component, including immersive and non-immersive modes. If this method is not explicitly called, the system immersive mode is followed by default.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Since**: 26.0.0

**Parameters** 

| Name | Type | Mandatory | Description |
| ------ | --------- | ---- | ---- |
| mode | [WebKeyboardAppearanceMode](./arkts-basic-components-web-e.md#webkeyboardappearancemode) | Yes   | Keyboard appearance. When **undefined** or **null** is passed, the system immersive mode is followed. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    @State appearanceMode: WebKeyboardAppearanceMode = WebKeyboardAppearanceMode.DARK_IMMERSIVE;

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
        .keyboardAppearance(this.appearanceMode)
      }
    }
  }
  ```

  HTML file to be loaded.

  ```html
  <!--index.html-->
  <!DOCTYPE html>
  <html>
  <head>
    <title>test page</title>
  </head>
  <body>
    <input type="text" placeholder="Text">
  </body>
  </html>
  ```

## enableFullscreenVideoOverlay

enableFullscreenVideoOverlay(enabled: boolean)

Sets whether to enable the overlay fullscreen playback feature for the **Web** component. If this attribute is not explicitly called, this feature is disabled by default.

> **NOTE**
>
> - Currently, only videos in H.264 and H.265 decoding formats are supported.
> - Only fullscreen requests initiated by video elements are responded to.

**Since**: 26.0.0

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

Device behavior differences: This API does not respond on 2-in-1 devices, but is supported on other device types.

**Parameters**

| Name | Type | Mandatory | Description                         |
| ------ | -------- | ---- | -------------------------------- |
| enabled | boolean  | Yes   | Whether to enable the overlay fullscreen playback feature for the **Web** component.<br>**true** means the feature is enabled.<br>**false** means the feature is disabled.<br>When **undefined** or **null** is passed, the value is **false**. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
        .enableFullscreenVideoOverlay(true)
      }
    }
  }
  ```

## enableMediaNetworkProxy

enableMediaNetworkProxy(enabled: boolean)

Sets whether to enable the media resource network request proxy feature for the **Web** component. If this attribute is not explicitly called, this feature is disabled by default.

> **NOTE**
>
> - Currently, only HLS streaming media videos are supported.

**Since**: 26.0.0

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description                         |
| ------ | -------- | ---- | -------------------------------- |
| enabled | boolean  | Yes   | Whether to enable the media resource network request proxy feature for the **Web** component.<br>**true** means the feature is enabled.<br>**false** means the feature is disabled. |

**Example**

  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: 'www.example.com', controller: this.controller })
        .enableMediaNetworkProxy(true)
      }
    }
  }
  ```