# Class (WebSchemeHandlerResponse)

请求的响应，可以为被拦截的请求创建一个Response并填充自定义的内容返回给Web组件。

> **说明：**
>
> - 本模块首批接口从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 12开始支持。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## 导入模块

```ts
import { webview } from '@kit.ArkWeb';
```

## constructor<sup>12+</sup>

constructor()

Response的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**示例：**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';
import { WebNetErrorList } from '@ohos.web.netErrorList';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  schemeHandler: webview.WebSchemeHandler = new webview.WebSchemeHandler();

  build() {
    Column() {
      Button('response').onClick(() => {
        let response = new webview.WebSchemeHandlerResponse();
        try {
          response.setUrl("http://www.example.com")
          response.setStatus(200)
          response.setStatusText("OK")
          response.setMimeType("text/html")
          response.setEncoding("utf-8")
          response.setHeaderByName("header1", "value1", false)
          response.setNetErrorCode(WebNetErrorList.NET_OK)
          console.log("[schemeHandler] getUrl:" + response.getUrl())
          console.log("[schemeHandler] getStatus:" + response.getStatus())
          console.log("[schemeHandler] getStatusText:" + response.getStatusText())
          console.log("[schemeHandler] getMimeType:" + response.getMimeType())
          console.log("[schemeHandler] getEncoding:" + response.getEncoding())
          console.log("[schemeHandler] getHeaderByValue:" + response.getHeaderByName("header1"))
          console.log("[schemeHandler] getNetErrorCode:" + response.getNetErrorCode())

        } catch (error) {
          console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
        }
      })
      Web({ src: 'https://www.example.com', controller: this.controller })
    }
  }
}

```

## setUrl<sup>12+</sup>

setUrl(url: string): void

给当前的Response设置重定向或因HSTS而更改后的URL，设置了url后会触发请求的跳转。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名   | 类型    |  必填  | 说明                       |
| --------| ------- | ---- | ---------------------------|
|  url | string | 是   | 即将要跳转的URL。 |

**示例：**

完整示例代码参考[constructor](#constructor12)。

**错误码：**

以下错误码的详细介绍请参见[webview错误码](errorcode-webview.md)。

| 错误码ID | 错误信息                  |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Incorrect parameter types.    |

## setNetErrorCode<sup>12+</sup>

setNetErrorCode(code: WebNetErrorList): void

给当前的Response设置网络错误码。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名   | 类型    |  必填  | 说明                       |
| --------| ------- | ---- | ---------------------------|
|  code | [WebNetErrorList](arkts-apis-netErrorList.md#webneterrorlist) | 是   | 网络错误码。 |

**错误码：**

以下错误码的详细介绍请参见[webview错误码](errorcode-webview.md)。

| 错误码ID | 错误信息                  |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.    |

**示例：**

完整示例代码参考[constructor](#constructor12)。

## setStatus<sup>12+</sup>

setStatus(code: number): void

给当前的Response设置HTTP状态码。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名   | 类型    |  必填  | 说明                       |
| --------| ------- | ---- | ---------------------------|
|  code | number | 是   | Http状态码。 |

**错误码：**

以下错误码的详细介绍请参见[webview错误码](errorcode-webview.md)。

| 错误码ID | 错误信息                  |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Incorrect parameter types. |

**示例：**

完整示例代码参考[constructor](#constructor12)。

## setStatusText<sup>12+</sup>

setStatusText(text: string): void

给当前的Response设置状态文本。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名   | 类型    |  必填  | 说明                       |
| --------| ------- | ---- | ---------------------------|
|  text | string | 是   | 状态文本。 |

**错误码：**

以下错误码的详细介绍请参见[webview错误码](errorcode-webview.md)。

| 错误码ID | 错误信息                  |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Incorrect parameter types.    |

**示例：**

完整示例代码参考[constructor](#constructor12)。

## setMimeType<sup>12+</sup>

setMimeType(type: string): void

给当前的Response设置媒体类型。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名   | 类型    |  必填  | 说明                       |
| --------| ------- | ---- | ---------------------------|
|  type | string | 是   | 媒体类型。 |

**错误码：**

以下错误码的详细介绍请参见[webview错误码](errorcode-webview.md)。

| 错误码ID | 错误信息                  |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Incorrect parameter types.    |

**示例：**

完整示例代码参考[constructor](#constructor12)。

## setEncoding<sup>12+</sup>

setEncoding(encoding: string): void

给当前的Response设置字符集。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名   | 类型    |  必填  | 说明                       |
| --------| ------- | ---- | ---------------------------|
|  encoding | string | 是   | 字符集。 |

**错误码：**

以下错误码的详细介绍请参见[webview错误码](errorcode-webview.md)。

| 错误码ID | 错误信息                  |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Incorrect parameter types.    |

**示例：**

完整示例代码参考[constructor](#constructor12)。

## setHeaderByName<sup>12+</sup>

setHeaderByName(name: string, value: string, overwrite: boolean): void

给当前的Response设置头信息。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名   | 类型    |  必填  | 说明                       |
| --------| ------- | ---- | ---------------------------|
|  name | string | 是   | 头部（header）的名称。 |
|  value | string | 是   | 头部（header）的值。 |
|  overwrite | boolean | 是   | 如果为true，将覆盖现有的头部，否则不覆盖。 |

**错误码：**

以下错误码的详细介绍请参见[webview错误码](errorcode-webview.md)。

| 错误码ID | 错误信息                  |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.    |

**示例：**

完整示例代码参考[constructor](#constructor12)。

## getUrl<sup>12+</sup>

getUrl(): string

获取重定向或由于HSTS而更改后的URL。
风险提示：如果想获取url来做JavascriptProxy通信接口认证，请使用[getLastJavascriptProxyCallingFrameUrl<sup>12+</sup>](./arkts-apis-webview-WebviewController.md#getlastjavascriptproxycallingframeurl12)

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型    | 说明                                     |
| ------- | --------------------------------------- |
| string | 获取经过重定向或由于HSTS而更改后的URL。|

**示例：**

完整示例代码参考[constructor](#constructor12)。

## getNetErrorCode<sup>12+</sup>

getNetErrorCode(): WebNetErrorList

获取Response的网络错误码。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型    | 说明                                     |
| ------- | --------------------------------------- |
| [WebNetErrorList](arkts-apis-netErrorList.md#webneterrorlist) | 获取Response的网络错误码。|

**示例：**

完整示例代码参考[constructor](#constructor12)。

## getStatus<sup>12+</sup>

getStatus(): number

获取Response的Http状态码。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型    | 说明                                     |
| ------- | --------------------------------------- |
| number | 获取Response的Http状态码。|

**示例：**

完整示例代码参考[constructor](#constructor12)。

## getStatusText<sup>12+</sup>

getStatusText(): string

获取Response的状态文本。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型    | 说明                                     |
| ------- | --------------------------------------- |
| string | 状态文本。|

**示例：**

完整示例代码参考[constructor](#constructor12)。

## getMimeType<sup>12+</sup>

getMimeType(): string

获取Response的媒体类型。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型    | 说明                                     |
| ------- | --------------------------------------- |
| string | 媒体类型。|

**示例：**

完整示例代码参考[constructor](#constructor12)。

## getEncoding<sup>12+</sup>

getEncoding(): string

获取Response的字符集。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型    | 说明                                     |
| ------- | --------------------------------------- |
| string | 字符集。|

**示例：**

完整示例代码参考[constructor](#constructor12)。

## getHeaderByName<sup>12+</sup>

getHeaderByName(name: string): string

获取Response的字符集。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名  | 类型             | 必填 | 说明                  |
| ------- | ---------------- | ---- | -------------------- |
| name     | string | 是   | 头部（header）的名称。      |


**返回值：**

| 类型    | 说明                                     |
| ------- | --------------------------------------- |
| string | 头部（header）的值。|

**示例：**

完整示例代码参考[constructor](#constructor12)。