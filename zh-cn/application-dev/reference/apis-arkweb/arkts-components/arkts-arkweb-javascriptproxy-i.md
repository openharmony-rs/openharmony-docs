# JavaScriptProxy

定义要注入的JavaScript对象，包括对象名、方法列表和权限配置。适用于需要实现JavaScript与原生交互的场景，提升跨语言调用的灵活性和安全性。

**起始版本：** 12

<!--Device-unnamed-declare interface JavaScriptProxy--><!--Device-unnamed-declare interface JavaScriptProxy-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## asyncMethodList

```TypeScript
asyncMethodList?: Array<string>
```

参与注册的应用侧JavaScript对象的异步方法。异步方法无法获取返回值。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-JavaScriptProxy-asyncMethodList?: Array<string>--><!--Device-JavaScriptProxy-asyncMethodList?: Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## controller

```TypeScript
controller: WebController | WebviewController
```

控制器。从API version 9开始，WebController不再维护，建议使用WebviewController替代。

**类型：** [WebController](arkts-arkweb-webcontroller-c.md) \| [WebviewController](arkts-arkweb-webviewcontroller-t.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-JavaScriptProxy-controller: WebController | WebviewController--><!--Device-JavaScriptProxy-controller: WebController | WebviewController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## methodList

```TypeScript
methodList: Array<string>
```

参与注册的应用侧JavaScript对象的同步方法。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-JavaScriptProxy-methodList: Array<string>--><!--Device-JavaScriptProxy-methodList: Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## name

```TypeScript
name: string
```

注册对象的名称，与window中调用的对象名一致。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-JavaScriptProxy-name: string--><!--Device-JavaScriptProxy-name: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## object

```TypeScript
object: object
```

参与注册的对象。只能声明方法，不能声明属性。方法必须是函数类型。

**类型：** object

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-JavaScriptProxy-object: object--><!--Device-JavaScriptProxy-object: object-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## permission

```TypeScript
permission?: string
```

json字符串，默认为空，通过该字符串配置JSBridge的权限管控，可以定义object、method一级的url白名单。 JavaScriptProxy的permission参数支持resource/http/https协议，不支持file协议。 示例请参考[前端页面调用应用侧函数](../../../web/web-in-page-app-function-invoking.md)。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-JavaScriptProxy-permission?: string--><!--Device-JavaScriptProxy-permission?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

