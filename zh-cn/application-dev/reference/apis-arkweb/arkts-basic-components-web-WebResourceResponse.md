# Class (WebResourceResponse)

Web组件资源响应对象。示例代码参考[onHttpErrorReceive事件](./arkts-basic-components-web-events.md#onhttperrorreceive)。

支持使用[@ohos.transfer](../apis-arkts/js-apis-transfer.md)系统对象转换工具进行动静态类型转换。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件首批接口从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 8开始支持。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## constructor

constructor()

WebResourceResponse的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

## getReasonMessage

getReasonMessage(): string

获取资源响应的状态码描述。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明            |
| ------ | ------------- |
| string | 返回资源响应的状态码描述。 |

## getResponseCode

ArkTS-Dyn: getResponseCode(): number

ArkTS-Sta: getResponseCode(): int

获取资源响应的状态码。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明          |
| ------ | ----------- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 返回资源响应的状态码。 |

## getResponseData

getResponseData(): string

获取资源响应数据。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明        |
| ------ | --------- |
| string | 返回资源响应数据。 |

## getResponseEncoding

getResponseEncoding(): string

获取资源响应的编码。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明         |
| ------ | ---------- |
| string | 返回资源响应的编码。 |

## getResponseHeader

getResponseHeader() : Array\<Header\>

获取资源响应头。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                         | 说明       |
| -------------------------- | -------- |
| Array\<[Header](./arkts-basic-components-web-i.md#header)\> | 返回资源响应头。 |

## getResponseMimeType

getResponseMimeType(): string

获取资源响应的媒体（MIME）类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明                 |
| ------ | ------------------ |
| string | 返回资源响应的媒体（MIME）类型。 |

## getResponseDataEx<sup>13+</sup>

ArkTS-Dyn: getResponseDataEx(): string | number | ArrayBuffer | Resource | undefined

ArkTS-Sta: getResponseDataEx(): string | int | ArrayBuffer | Resource | undefined

获取资源响应数据，支持多种数据类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**返回值：**

|类型|说明|
|---|---|
|string|返回HTML格式的字符串。|
|ArkTS-Dyn: number<br>ArkTS-Sta: int|返回文件句柄。|
|ArrayBuffer|返回二进制数据。|
|[Resource](../apis-arkui/arkui-ts/ts-types.md#resource)|返回`$rawfile`资源。|
|undefined|如果没有可用数据，返回`undefined`。|

## getResponseIsReady<sup>13+</sup>

getResponseIsReady(): boolean

获取响应数据是否已准备就绪。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**返回值：**

|类型|说明|
|---|---|
|boolean|`true`表示响应数据已准备好，`false`表示未准备好。|

## setResponseData<sup>9+</sup>

ArkTS-Dyn: setResponseData(data: string \| number \| Resource \| ArrayBuffer): void

ArkTS-Sta: setResponseData(data: string \| int \| Resource \| ArrayBuffer): void

设置资源响应数据。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                     | 必填   | 说明                                     |
| ---- | ---------------------------------------- | ---- | ---------------------------------------- |
| data | ArkTS-Dyn: string \| number \| [Resource](../apis-arkui/arkui-ts/ts-types.md#resource)<sup>10+</sup> \| ArrayBuffer<sup>11+</sup><br>ArkTS-Sta: string \| int \| [Resource](../apis-arkui/arkui-ts/ts-types.md#resource)<sup>10+</sup> \| ArrayBuffer<sup>11+</sup> | 是    | 要设置的资源响应数据。string表示HTML格式的字符串。number表示文件句柄，此句柄由系统的Web组件负责关闭。Resource表示应用rawfile目录下文件资源。ArrayBuffer表示资源的原始二进制数据。 |

## setResponseEncoding<sup>9+</sup>

setResponseEncoding(encoding: string): void

设置资源响应的编码。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型   | 必填   | 说明         |
| -------- | ------ | ---- | ------------ |
| encoding | string | 是    | 要设置的资源响应的编码。 |

## setResponseMimeType<sup>9+</sup>

setResponseMimeType(mimeType: string): void

设置资源响应的媒体（MIME）类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型   | 必填   | 说明                 |
| -------- | ------ | ---- | -------------------- |
| mimeType | string | 是   | 要设置的资源响应的媒体（MIME）类型。 |

## setReasonMessage<sup>9+</sup>

setReasonMessage(reason: string): void

设置资源响应的状态码描述。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型   | 必填   | 说明            |
| ------ | ------ | ---- | --------------- |
| reason | string | 是   | 要设置的资源响应的状态码描述。 |

## setResponseHeader<sup>9+</sup>

setResponseHeader(header: Array\<Header\>): void

设置资源响应头。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                       | 必填   | 说明       |
| ------ | -------------------------- | ---- | ---------- |
| header | Array\<[Header](./arkts-basic-components-web-i.md#header)\> | 是   | 要设置的资源响应头。 |

## setResponseCode<sup>9+</sup>

ArkTS-Dyn: setResponseCode(code: number): void

ArkTS-Sta: setResponseCode(code: int): void

设置资源响应的状态码。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型   | 必填   | 说明          |
| ---- | ------ | ---- | ------------- |
| code | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 要设置的资源响应的状态码。如果该资源以错误结束，请参考[@ohos.web.netErrorList](arkts-apis-netErrorList.md)设置相应错误码，避免设置错误码为 ERR_IO_PENDING，设置为该错误码可能会导致XMLHttpRequest同步请求阻塞。 |

## setResponseIsReady<sup>9+</sup>

setResponseIsReady(IsReady: boolean): void

设置资源响应数据是否已经就绪。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型    | 必填  | 说明          |
| ------- | ------- | ---- | ------------- |
| IsReady | boolean | 是   | 资源响应数据是否已经就绪。<br>true表示资源响应数据已经就绪，false表示资源响应数据未就绪。<br>如果数据是异步提供，需要显式设置为false。设置为非法值如null，undefined或者不设置都会被认为数据已经准备好。 |

## 使用@ohos.transfer进行WebResourceResponse类型转换

ArkTS-Dyn中使用ArkTS-Sta的WebResourceResponse对象。

- 在ArkTS-Sta模块中将ArkTS-Sta WebResourceResponse转换成ArkTS-Dyn WebResourceResponse，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, Button, OnHttpErrorReceiveEvent } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { webResourceResponseStaticToDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Button("Trigger onHttpErrorReceive")
          .onClick(() => {
            try {
              this.controller.loadUrl('http://httpbin.org/post');
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onHttpErrorReceive((parameter: OnHttpErrorReceiveEvent): void => {
            console.info('onHttpErrorReceive invoked');
            try {
              let dynamicHandler = transfer.transferDynamic(parameter.response, 'ArkWeb.WebResourceResponse');
              webResourceResponseStaticToDynamic(dynamicHandler);
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
      }
    }
  }
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebResourceResponse的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function webResourceResponseStaticToDynamic(handler_: any) {
    try {
      let response: WebResourceResponse = handler_ as WebResourceResponse;
      let result: string = response.getResponseMimeType();
      console.info('webResourceResponseStaticToDynamic result=' + result);
    } catch (e) {
      console.error('webResourceResponseStaticToDynamic catch Error: ' + e.toString());
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的WebResourceResponse对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn WebResourceResponse对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { webResourceResponseDynamicToStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Button("Trigger onHttpErrorReceive")
          .onClick(() => {
            try {
              this.controller.loadUrl('http://httpbin.org/post');
            } catch (error) {
              console.error(`ErrorCode: ${error.code},  Message: ${error.message}`);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
          .onHttpErrorReceive((parameter: OnHttpErrorReceiveEvent): void => {
            if (parameter) {
              console.info("onHttpErrorReceive start");
              webResourceResponseDynamicToStatic(parameter.response);
            }
          })
      }
    }
  }
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebResourceResponse的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { WebResourceResponse } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function webResourceResponseDynamicToStatic(dynObject: Object | undefined | null) {
    try {
        let response: WebResourceResponse = transfer.transferStatic(dynObject, 'ArkWeb.WebResourceResponse') as WebResourceResponse;
        let result: string = response.getResponseMimeType();
        console.info('webResourceResponseDynamicToStatic result=' + result);
    } catch (e: Error) {
        console.error('webResourceResponseDynamicToStatic catch error：-----------' + e.message);
    }
  }
  ```