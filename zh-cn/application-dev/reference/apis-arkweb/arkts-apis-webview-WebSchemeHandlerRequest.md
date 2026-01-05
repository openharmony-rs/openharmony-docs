# Class (WebSchemeHandlerRequest)

通过WebSchemeHandler拦截到的请求。

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

## getHeader<sup>12+</sup>

getHeader(): Array\<WebHeader\>

获取资源请求头信息。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                         | 说明         |
| -------------------------- | ---------- |
| Array\<[WebHeader](./arkts-apis-webview-i.md#webheader)\> | 返回资源请求头信息。 |

**示例：**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## getRequestUrl<sup>12+</sup>

getRequestUrl(): string

获取资源请求的URL信息。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明            |
| ------ | ------------- |
| string | 返回资源请求的URL信息。 |

**示例：**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## getRequestMethod<sup>12+</sup>

getRequestMethod(): string

获取请求方法。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明            |
| ------ | ------------- |
| string | 返回请求方法。 |

**示例：**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## getReferrer<sup>12+</sup>

getReferrer(): string

获取referrer。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明            |
| ------ | ------------- |
| string | 获取到的referrer。 |

**示例：**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## isMainFrame<sup>12+</sup>

isMainFrame(): boolean

判断资源请求是否为主frame。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明            |
| ------ | ------------- |
| boolean | 判断资源请求是否为主frame，如果资源请求是主frame则返回true，否则返回false。 |

**示例：**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## hasGesture<sup>12+</sup>

hasGesture(): boolean

获取资源请求是否与手势（如点击）相关联。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明            |
| ------ | ------------- |
| boolean | 返回资源请求是否与手势（如点击）相关联，如果返回资源请求与手势相关联则返回true，否则返回false。 |

**示例：**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## getHttpBodyStream<sup>12+</sup>

getHttpBodyStream(): WebHttpBodyStream | null

获取资源请求中的WebHttpBodyStream。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明            |
| ------ | ------------- |
| [WebHttpBodyStream](./arkts-apis-webview-WebHttpBodyStream.md) \| null | 返回资源请求中的WebHttpBodyStream，如果没有则返回null。 |

**示例：**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## getRequestResourceType<sup>12+</sup>

getRequestResourceType(): WebResourceType

获取资源请求的资源类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明            |
| ------ | ------------- |
| [WebResourceType](./arkts-apis-webview-e.md#webresourcetype12) | 返回资源请求的资源类型。 |

**示例：**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## getFrameUrl<sup>12+</sup>

getFrameUrl(): string

获取触发此请求的Frame的URL。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明            |
| ------ | ------------- |
| string | 返回触发此请求的Frame的URL。 |

**示例：**

完整示例代码参考[onRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12)。

## 使用@ohos.transfer进行WebSchemeHandlerRequest类型转换

ArkTS-Dyn中使用ArkTS-Sta的WebSchemeHandlerRequest对象。

- 在ArkTS-Sta模块中将ArkTS-Sta WebSchemeHandlerRequest转换成ArkTS-Dyn WebSchemeHandlerRequest，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { buffer } from '@kit.ArkTS';
  import { transfer } from '@kit.ArkTS';
  import { Web, Column, Component, Entry } from '@kit.ArkUI';
  import { WebNetErrorList } from '@ohos.web.netErrorList';
  import { webSchemeHandlerRequestStaticToDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController(undefined);
  schemeHandler: webview.WebSchemeHandler = new webview.WebSchemeHandler();
  htmlData: string = "<html><body bgcolor=\"white\">Source:<pre>source</pre></body></html>";

  build() {
      Column() {
      Web({ src: 'https://www.example.com', controller: this.controller })
          .onControllerAttached(() => {
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

              let dynamicHandler = transfer.transferDynamic(request, 'ArkWeb.WebSchemeHandlerRequest');  // transferDynamic
              webSchemeHandlerRequestStaticToDynamic(dynamicHandler);

              let response = new webview.WebSchemeHandlerResponse();
              try {
                  response.setNetErrorCode(WebNetErrorList.NET_OK);
                  response.setStatus(200);
                  response.setStatusText("OK");
                  response.setMimeType("text/html");
                  response.setEncoding("utf-8");
                  response.setHeaderByName("header1", "value1", false);
              } catch (error) {
                  console.error(`[schemeHandler] ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }

              // 调用 didFinish/didFail 前需要优先调用 didReceiveResponse 将构造的响应头传递给被拦截的请求。
              let buf = buffer.from(this.htmlData)
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
              } catch (error) {
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

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebSchemeHandlerRequest的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  import { webview } from '@kit.ArkWeb';
  export function webSchemeHandlerRequestStaticToDynamic(handler_: any) {
    try {
      let handler: webview.WebSchemeHandlerRequest = handler_ as webview.WebSchemeHandlerRequest;
      let result: string = handler.getRequestUrl();
      console.info('webSchemeHandlerRequestStaticToDynamic result=' + result);
    } catch (e) {
      console.error('webSchemeHandlerRequestStaticToDynamic catch Error: ' + e.toString());
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的WebSchemeHandlerRequest对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn WebSchemeHandlerRequest对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { buffer } from '@kit.ArkTS';
  import { WebNetErrorList } from '@ohos.web.netErrorList';
  import { webSchemeHandlerRequestDynamicToStatic } from 'library';

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

              webSchemeHandlerRequestDynamicToStatic(request); // transferStatic

              let response = new webview.WebSchemeHandlerResponse();
              try {
                  response.setNetErrorCode(WebNetErrorList.NET_OK);
                  response.setStatus(200);
                  response.setStatusText("OK");
                  response.setMimeType("text/html");
                  response.setEncoding("utf-8");
                  response.setHeaderByName("header1", "value1", false);
              } catch (error) {
                  console.error(`[schemeHandler] ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }

              // 调用 didFinish/didFail 前需要优先调用 didReceiveResponse 将构造的响应头传递给被拦截的请求。
              let buf = buffer.from(this.htmlData)
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
              } catch (error) {
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

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebSchemeHandlerRequest的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';

  export function webSchemeHandlerRequestDynamicToStatic(dynObject: Object | undefined | null) {
    try {
        let handler: webview.WebSchemeHandlerRequest = transfer.transferStatic(dynObject, 'ArkWeb.WebSchemeHandlerRequest') as webview.WebSchemeHandlerRequest;
        let result: string = handler.getRequestUrl();
        console.info('webSchemeHandlerRequestDynamicToStatic result=' + result);
    } catch (e: Error) {
        console.error('webSchemeHandlerRequestDynamicToStatic catch error：-----------' + e.message);
    }
  }
  ```