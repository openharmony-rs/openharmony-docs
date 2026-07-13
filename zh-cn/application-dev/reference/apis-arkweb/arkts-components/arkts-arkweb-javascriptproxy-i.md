# JavaScriptProxy

定义要注入的JavaScript对象。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## asyncMethodList

```TypeScript
asyncMethodList?: Array<string>
```

参与注册的应用侧JavaScript对象的异步方法。异步方法无法获取返回值。

**类型：** Array<string>

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## controller

```TypeScript
controller: WebController | WebviewController
```

Controller.

**类型：** WebController | WebviewController

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## methodList

```TypeScript
methodList: Array<string>
```

参与注册的应用侧JavaScript对象的同步方法。

**类型：** Array<string>

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## name

```TypeScript
name: string
```

注册对象的名称，与window中调用的对象名一致。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## object

```TypeScript
object: object
```

参与注册的对象。

**类型：** object

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## permission

```TypeScript
permission?: string
```

permission configuration defining web page URLs that can access JavaScriptProxy methods.
The configuration can be defined at two levels, object level and method level.

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

