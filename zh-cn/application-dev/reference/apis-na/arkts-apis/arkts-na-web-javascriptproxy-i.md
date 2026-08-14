# JavaScriptProxy

Defines the JavaScript object to be injected.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface JavaScriptProxy--><!--Device-unnamed-export declare interface JavaScriptProxy-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## asyncMethodList

```TypeScript
asyncMethodList?: Array<string>
```

The async method of the application side JavaScript object participating in the registration.

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-JavaScriptProxy-asyncMethodList?: Array<string>--><!--Device-JavaScriptProxy-asyncMethodList?: Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## controller

```TypeScript
controller: WebviewController
```

Controller.

**类型：** [WebviewController](arkts-na-webviewcontroller-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-JavaScriptProxy-controller: WebviewController--><!--Device-JavaScriptProxy-controller: WebviewController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## jsObject

```TypeScript
jsObject: object
```

Objects participating in registration.

**类型：** object

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-JavaScriptProxy-jsObject: object--><!--Device-JavaScriptProxy-jsObject: object-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## methodList

```TypeScript
methodList: Array<string>
```

The method of the application side JavaScript object participating in the registration.

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-JavaScriptProxy-methodList: Array<string>--><!--Device-JavaScriptProxy-methodList: Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## name

```TypeScript
name: string
```

The name of the registered object, which is consistent with the object name called in the window.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-JavaScriptProxy-name: string--><!--Device-JavaScriptProxy-name: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## permission

```TypeScript
permission?: string
```

permission configuration defining web page URLs that can access JavaScriptProxy methods. The configuration can be defined at two levels, object level and method level.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-JavaScriptProxy-permission?: string--><!--Device-JavaScriptProxy-permission?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

