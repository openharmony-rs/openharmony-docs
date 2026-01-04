# Class (WebResourceHandler)

通过WebResourceHandler，可以提供自定义的返回头以及返回体给Web组件。

支持使用[@ohos.transfer](../apis-arkts/js-apis-transfer.md)系统对象转换工具进行动静态类型转换。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 12开始支持。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## didReceiveResponse<sup>12+</sup>

didReceiveResponse(response: WebSchemeHandlerResponse): void

将构造的响应头传递给被拦截的请求。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名          | 类型    |  必填  | 说明                                            |
| ---------------| ------- | ---- | ------------- |
| response      | [WebSchemeHandlerResponse](./arkts-apis-webview-WebSchemeHandlerResponse.md)  | 是   | 该拦截请求的响应。 |

**错误码：**

以下错误码的详细介绍请参见[Webview错误码](errorcode-webview.md)、[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                              |
| -------- | ------------------------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.    |
| 17100021 | The resource handler is invalid. |

**示例：**

示例请参考[OnRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## didReceiveResponseBody<sup>12+</sup>

didReceiveResponseBody(data: ArrayBuffer): void

将构造的响应体传递给被拦截的请求。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名          | 类型    |  必填  | 说明                                            |
| ---------------| ------- | ---- | ------------- |
| data      | ArrayBuffer  | 是   | 响应体数据。 |

**错误码：**

以下错误码的详细介绍请参见[Webview错误码](errorcode-webview.md)、[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                              |
| -------- | ------------------------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.    |
| 17100021 | The resource handler is invalid. |

**示例：**

示例请参考[OnRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## didFinish<sup>12+</sup>

didFinish(): void

通知Web组件被拦截的请求已经完成，并且没有更多的数据可用，调用前需要优先调用[didReceiveResponse](#didreceiveresponse12)将构造的响应头传递给被拦截的请求。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**错误码：**

以下错误码的详细介绍请参见[Webview错误码](errorcode-webview.md)。

| 错误码ID | 错误信息                              |
| -------- | ------------------------------------- |
| 17100021 | The resource handler is invalid. |

**示例：**

示例请参考[OnRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## didFail<sup>12+</sup>

didFail(code: WebNetErrorList): void

通知ArkWeb内核被拦截请求应该返回失败，调用前需要优先调用[didReceiveResponse](#didreceiveresponse12)将构造的响应头传递给被拦截的请求。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型    |  必填  | 说明                       |
| --------| ------- | ---- | ---------------------------|
|  code | [WebNetErrorList](arkts-apis-netErrorList.md#webneterrorlist) | 是   | 网络错误码。 |

**错误码：**

以下错误码的详细介绍请参见[Webview错误码](errorcode-webview.md)、[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                              |
| -------- | ------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 17100021 | The resource handler is invalid. |

**系统能力：** SystemCapability.Web.Webview.Core

**示例：**

示例请参考[OnRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## didFail<sup>20+</sup>

didFail(code: WebNetErrorList, completeIfNoResponse: boolean): void

通知ArkWeb内核，被拦截请求应返回失败。若completeIfNoResponse为false，调用前需优先调用[didReceiveResponse](#didreceiveresponse12)，将构造的响应头传递给被拦截的请求。若completeIfNoResponse为true，且调用前未调用[didReceiveResponse](#didreceiveresponse12)，则自动生成一个响应头，网络错误码为-104，详情参见[WebNetErrorList](arkts-apis-netErrorList.md#webneterrorlist)。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型    |  必填  | 说明                       |
| --------| ------- | ---- | ---------------------------|
|  code | [WebNetErrorList](arkts-apis-netErrorList.md#webneterrorlist) | 是   | 网络错误码。 |
|  completeIfNoResponse | boolean | 是   | 调用当前接口时，若之前未调用过[didReceiveResponse](#didreceiveresponse12)，是否完成此次网络请求；值为true时，若之前未调用过[didReceiveResponse](#didreceiveresponse12)，则会自动生成一个response以完成此次网络请求，网络错误码为-104；值为false时，将等待应用调用[didReceiveResponse](#didreceiveresponse12)并传入response，不会直接完成此次网络请求。 |

**错误码：**

以下错误码的详细介绍请参见[Webview错误码](errorcode-webview.md)。

| 错误码ID | 错误信息                              |
| -------- | ------------------------------------- |
| 17100101 | The errorCode is either ARKWEB_NET_OK or outside the range of error codes in WebNetErrorList. |
| 17100021 | The resource handler is invalid. |

**示例：**

ArkTS-Dyn示例：
```ts
// xxx.ets
import { webview, WebNetErrorList } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  schemeHandler: webview.WebSchemeHandler = new webview.WebSchemeHandler();

  build() {
    Column() {
      Web({ src: 'https://www.example.com', controller: this.controller })
        .onControllerAttached(() => {
          try {
            this.schemeHandler.onRequestStart((request: webview.WebSchemeHandlerRequest, resourceHandler: webview.WebResourceHandler) => {
              console.info("[schemeHandler] onRequestStart");
              try {
                console.info("[schemeHandler] onRequestStart url:" + request.getRequestUrl());
                console.info("[schemeHandler] onRequestStart method:" + request.getRequestMethod());
                console.info("[schemeHandler] onRequestStart referrer:" + request.getReferrer());
                console.info("[schemeHandler] onRequestStart isMainFrame:" + request.isMainFrame());
                console.info("[schemeHandler] onRequestStart hasGesture:" + request.hasGesture());
                console.info("[schemeHandler] onRequestStart header size:" + request.getHeader().length);
                console.info("[schemeHandler] onRequestStart resource type:" + request.getRequestResourceType());
                console.info("[schemeHandler] onRequestStart frame url:" + request.getFrameUrl());
                let header = request.getHeader();
                for (let i = 0; i < header.length; i++) {
                  console.info("[schemeHandler] onRequestStart header:" + header[i].headerKey + " " + header[i].headerValue);
                }
                let stream = request.getHttpBodyStream();
                if (stream) {
                  console.info("[schemeHandler] onRequestStart has http body stream");
                } else {
                  console.info("[schemeHandler] onRequestStart has no http body stream");
                }
              } catch (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }

              if (request.getRequestUrl().endsWith("example.com")) {
                return false;
              }

              try {
                // 直接调用didFail(WebNetErrorList.ERR_FAILED, true)，自动构造一个网络请求错误ERR_CONNECTION_FAILED。
                resourceHandler.didFail(WebNetErrorList.ERR_FAILED, true);
              } catch (error) {
              	// 当error.code为17100101时，若没有处理该错误，didFail方法也会调用成功。
                console.error(`[schemeHandler] ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }
              return true;
            })

            this.schemeHandler.onRequestStop((request: webview.WebSchemeHandlerRequest) => {
              console.info("[schemeHandler] onRequestStop");
            });

            this.controller.setWebSchemeHandler('https', this.schemeHandler);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
        .javaScriptAccess(true)
        .domStorageAccess(true)
    }
  }
}
```

ArkTS-Sta示例：
```ts
import { Entry, Column, Component, Web } from '@ohos.arkui.component';
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@ohos.base';
import { WebNetErrorList } from '@ohos.web.netErrorList';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController(undefined);
  schemeHandler: webview.WebSchemeHandler = new webview.WebSchemeHandler();

  build() {
    Column() {
      Web({ src: 'https://www.example.com', controller: this.controller })
        .onControllerAttached(() => {
          try {
            this.schemeHandler.onRequestStart((request: webview.WebSchemeHandlerRequest, resourceHandler: webview.WebResourceHandler) => {
              console.info("[schemeHandler] onRequestStart");
              try {
                console.info("[schemeHandler] onRequestStart url:" + request.getRequestUrl());
                console.info("[schemeHandler] onRequestStart method:" + request.getRequestMethod());
                console.info("[schemeHandler] onRequestStart referrer:" + request.getReferrer());
                console.info("[schemeHandler] onRequestStart isMainFrame:" + request.isMainFrame());
                console.info("[schemeHandler] onRequestStart hasGesture:" + request.hasGesture());
                console.info("[schemeHandler] onRequestStart header size:" + request.getHeader().length);
                console.info("[schemeHandler] onRequestStart resource type:" + request.getRequestResourceType());
                console.info("[schemeHandler] onRequestStart frame url:" + request.getFrameUrl());
                let header = request.getHeader();
                for (let i = 0; i < header.length; i++) {
                  console.info("[schemeHandler] onRequestStart header:" + header[i].headerKey + " " + header[i].headerValue);
                }
                let stream = request.getHttpBodyStream();
                if (stream) {
                  console.info("[schemeHandler] onRequestStart has http body stream");
                } else {
                  console.info("[schemeHandler] onRequestStart has no http body stream");
                }
              } catch (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }

              if (request.getRequestUrl().endsWith("example.com")) {
                return false;
              }

              try {
                // 直接调用didFail(WebNetErrorList.ERR_FAILED, true)，自动构造一个网络请求错误ERR_CONNECTION_FAILED
                resourceHandler.didFail(WebNetErrorList.ERR_FAILED, true);
              } catch (error) {
                // 当error.code为17100101(The errorCode is either ARKWEB_NET_OK or outside the range of error codes in WebNetErrorList)。
                // 且didFail(code: WebNetErrorList, completeIfNoResponse: boolean)的code值不为null时，接口会继续调用不会中断。
                console.error(`[schemeHandler] ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }
              return true;
            })

            this.schemeHandler.onRequestStop((request: webview.WebSchemeHandlerRequest) => {
              console.info("[schemeHandler] onRequestStop");
            });

            this.controller.setWebSchemeHandler('https', this.schemeHandler);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
        .javaScriptAccess(true)
        .domStorageAccess(true)
    }
  }
}
```

## 使用@ohos.transfer进行WebResourceHandler类型转换

ArkTS-Dyn中使用ArkTS-Sta的WebResourceHandler对象。

- 在ArkTS-Sta模块中将ArkTS-Sta WebResourceHandler转换成ArkTS-Dyn WebResourceHandler，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { buffer } from '@kit.ArkTS';
  import { transfer } from '@kit.ArkTS';
  import { Web, Column, Component, Entry } from '@kit.ArkUI';
  import { WebNetErrorList } from '@ohos.web.netErrorList';
  import { webResourceHandlerStaticToDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController(undefined);
  schemeHandler: webview.WebSchemeHandler = new webview.WebSchemeHandler();
  htmlData: string = "<html><body bgcolor=\"white\">Source:<pre>source</pre></body></html>";

  build() {
      Column() {
      Web({ src: 'https://www.example.com', controller: this.controller })
          .onControllerAttached((): void => {
          try {
              this.schemeHandler.onRequestStart((request: webview.WebSchemeHandlerRequest,
              resourceHandler: webview.WebResourceHandler) : boolean => {
              console.info("[schemeHandler] onRequestStart");
              try {
                  console.info("[schemeHandler] onRequestStart url:" + request.getRequestUrl());
                  console.info("[schemeHandler] onRequestStart method:" + request.getRequestMethod());
                  console.info("[schemeHandler] onRequestStart referrer:" + request.getReferrer());
                  console.info("[schemeHandler] onRequestStart isMainFrame:" + request.isMainFrame());
                  console.info("[schemeHandler] onRequestStart hasGesture:" + request.hasGesture());
                  console.info("[schemeHandler] onRequestStart header size:" + request.getHeader().length);
                  console.info("[schemeHandler] onRequestStart resource type:" + request.getRequestResourceType());
                  console.info("[schemeHandler] onRequestStart frame url:" + request.getFrameUrl());
                  let header = request.getHeader();
                  for (let i = 0; i < header.length; i++) {
                  console.info("[schemeHandler] onRequestStart header:" + header[i].headerKey + " " +
                  header[i].headerValue);
                  }
                  let stream = request.getHttpBodyStream();
                  if (stream) {
                  console.info("[schemeHandler] onRequestStart has http body stream");
                  } else {
                  console.info("[schemeHandler] onRequestStart has no http body stream");
                  }
              } catch (error) {
                  console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }

              if (request.getRequestUrl().endsWith("example.com")) {
                  return false;
              }

              let dynamicHandler = transfer.transferDynamic(resourceHandler, 'ArkWeb.WebResourceHandler');
              webResourceHandlerStaticToDynamic(dynamicHandler);
              return true;
              })

              this.schemeHandler.onRequestStop((request: webview.WebSchemeHandlerRequest) => {
              console.info("[schemeHandler] onRequestStop");
              });

              this.controller.setWebSchemeHandler('https', this.schemeHandler);
          } catch (error) {
              console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
          })
          .javaScriptAccess(true)
          .domStorageAccess(true)
      }
  }
  }
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebResourceHandler的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  import webview from '@ohos.web.webview'
  import { buffer } from '@kit.ArkTS';
  import { WebNetErrorList } from '@ohos.web.netErrorList';
  export function webResourceHandlerStaticToDynamic(handler_: any) {
    try {
      let resourceHandler: webview.WebResourceHandler = handler_ as webview.WebResourceHandler;

      let response = new webview.WebSchemeHandlerResponse();
      try {
        response.setNetErrorCode(WebNetErrorList.NET_OK);
        response.setStatus(200);
        response.setStatusText("OK");
        response.setMimeType("text/html");
        response.setEncoding("utf-8");
        response.setHeaderByName("header1", "value1", false);
      } catch (e) {
        console.error('webResourceHandlerStaticToDynamic catch Error: ' + e.toString());
      }

      // 调用 didFinish/didFail 前需要优先调用 didReceiveResponse 将构造的响应头传递给被拦截的请求。
      let htmlData: string = "<html><body bgcolor=\"white\">Source:<pre>source TESTTEST</pre></body></html>";
      let buf = buffer.from(htmlData)
      try {
        if (buf.length == 0) {
          console.info("[schemeHandler] length 0");
          resourceHandler.didReceiveResponse(response);
          // 如果认为buf.length为0是正常情况，则调用resourceHandler.didFinish，否则调用resourceHandler.didFail
          resourceHandler.didFail(WebNetErrorList.ERR_FAILED);
        } else {
          console.info("[schemeHandler] length 1");
          resourceHandler.didReceiveResponse(response);
          resourceHandler.didReceiveResponseBody(buf.buffer);
          resourceHandler.didFinish();
        }
      } catch (e) {
        console.error('webResourceHandlerStaticToDynamic catch Error: ' + e.toString());
      }
      console.info('webResourceHandlerStaticToDynamic done');
    } catch (e) {
      console.error('webResourceHandlerStaticToDynamic catch Error: ' + e.toString());
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的WebResourceHandler对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn WebResourceHandler对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { buffer } from '@kit.ArkTS';
  import { WebNetErrorList } from '@ohos.web.netErrorList';
  import { webResourceHandlerDynamicToStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  schemeHandler: webview.WebSchemeHandler = new webview.WebSchemeHandler();
  htmlData: string = "<html><body bgcolor=\"white\">Source:<pre>source</pre></body></html>";

  build() {
      Column() {
      Web({ src: 'https://www.example.com', controller: this.controller })
          .onControllerAttached(() => {
          try {
              this.schemeHandler.onRequestStart((request: webview.WebSchemeHandlerRequest, resourceHandler: webview.WebResourceHandler) => {
              console.info("[schemeHandler] onRequestStart");
              try {
                  console.info("[schemeHandler] onRequestStart url:" + request.getRequestUrl());
                  console.info("[schemeHandler] onRequestStart method:" + request.getRequestMethod());
                  console.info("[schemeHandler] onRequestStart referrer:" + request.getReferrer());
                  console.info("[schemeHandler] onRequestStart isMainFrame:" + request.isMainFrame());
                  console.info("[schemeHandler] onRequestStart hasGesture:" + request.hasGesture());
                  console.info("[schemeHandler] onRequestStart header size:" + request.getHeader().length);
                  console.info("[schemeHandler] onRequestStart resource type:" + request.getRequestResourceType());
                  console.info("[schemeHandler] onRequestStart frame url:" + request.getFrameUrl());
                  let header = request.getHeader();
                  for (let i = 0; i < header.length; i++) {
                  console.info("[schemeHandler] onRequestStart header:" + header[i].headerKey + " " + header[i].headerValue);
                  }
                  let stream = request.getHttpBodyStream();
                  if (stream) {
                  console.info("[schemeHandler] onRequestStart has http body stream");
                  } else {
                  console.info("[schemeHandler] onRequestStart has no http body stream");
                  }
              } catch (error) {
                  console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }

              if (request.getRequestUrl().endsWith("example.com")) {
                  return false;
              }

              webResourceHandlerDynamicToStatic(resourceHandler);
              return true;
              })

              this.schemeHandler.onRequestStop((request: webview.WebSchemeHandlerRequest) => {
              console.info("[schemeHandler] onRequestStop");
              });

              this.controller.setWebSchemeHandler('https', this.schemeHandler);
          } catch (error) {
              console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
          })
          .javaScriptAccess(true)
          .domStorageAccess(true)
      }
  }
  }
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebResourceHandler的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { buffer } from '@kit.ArkTS';
  import { WebNetErrorList } from '@ohos.web.netErrorList';

  export function webResourceHandlerDynamicToStatic(dynObject: Object | undefined | null) {
    try {
    let resourceHandler: webview.WebResourceHandler = transfer.transferStatic(dynObject, 'ArkWeb.WebResourceHandler') as webview.WebResourceHandler;

    let response = new webview.WebSchemeHandlerResponse();
    try {
      response.setNetErrorCode(WebNetErrorList.NET_OK);
      response.setStatus(200);
      response.setStatusText("OK");
      response.setMimeType("text/html");
      response.setEncoding("utf-8");
      response.setHeaderByName("header1", "value1", false);
    } catch (e) {
      console.error('webResourceHandlerDynamicToStatic catch Error: ' + e.toString());
    }

    // 调用 didFinish/didFail 前需要优先调用 didReceiveResponse 将构造的响应头传递给被拦截的请求。
    let htmlData: string = "<html><body bgcolor=\"white\">Source:<pre>source</pre></body></html>";
    let buf = buffer.from(htmlData)
    try {
      if (buf.length == 0) {
        console.info("[schemeHandler] length 0");
        resourceHandler.didReceiveResponse(response);
        // 如果认为buf.length为0是正常情况，则调用resourceHandler.didFinish，否则调用resourceHandler.didFail
        resourceHandler.didFail(WebNetErrorList.ERR_FAILED);
      } else {
        console.info("[schemeHandler] length 1");
        resourceHandler.didReceiveResponse(response);
        resourceHandler.didReceiveResponseBody(buf.buffer);
        resourceHandler.didFinish();
      }
    } catch (e) {
      console.error('webResourceHandlerDynamicToStatic catch Error: ' + e.toString());
    }
    console.info('webResourceHandlerDynamicToStatic done');
  } catch (e) {
    console.error('webResourceHandlerDynamicToStatic catch Error: ' + e.toString());
  }
  }
  ```