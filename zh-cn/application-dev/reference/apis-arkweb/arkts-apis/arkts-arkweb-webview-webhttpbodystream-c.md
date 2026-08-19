# WebHttpBodyStream

WebHttpBodyStream是HTTP请求体数据流对象，用于在自定义scheme拦截场景中读取POST、PUT等请求的请求体数据。该对象通过WebSchemeHandlerRequest的getHttpBodyStream方 法获取，支持BYTES、FILE、BLOB、CHUNKED类型的数据。开发者可以通过该接口在自定义协议拦截器中读取上行数据，实现对请求体的检视或转发。注意本类中的其他接口需要在 [initialize](#initialize)成功后才能调用。 WebHttpBodyStream与[WebSchemeHandlerRequest](arkts-arkweb-webview-webschemehandlerrequest-c.md)配合使用：WebSchemeHandlerRequest代表被拦截 的请求，WebHttpBodyStream代表该请求的HTTP body数据流。通过读取流中的数据，开发者可以获取完整的请求体内容。

**起始版本：** 12

<!--Device-webview-class WebHttpBodyStream--><!--Device-webview-class WebHttpBodyStream-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## getPosition

```TypeScript
getPosition(): number
```

读取WebHttpBodyStream中当前的读取位置。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebHttpBodyStream-getPosition(): number--><!--Device-WebHttpBodyStream-getPosition(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | WebHttpBodyStream中当前的读取位置。单位：字节。 |

## getSize

```TypeScript
getSize(): number
```

获取WebHttpBodyStream中的数据大小，分块传输时总是返回零。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebHttpBodyStream-getSize(): number--><!--Device-WebHttpBodyStream-getSize(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取WebHttpBodyStream数据大小。单位：字节。 |

## initialize

```TypeScript
initialize(): Promise<void>
```

初始化WebHttpBodyStream。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebHttpBodyStream-initialize(): Promise<void>--><!--Device-WebHttpBodyStream-initialize(): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise实例，用于获取WebHttpBodyStream是否初始化成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100022](../errorcode-webview.md#17100022-webhttpbodystream初始化失败) | Failed to initialize the HTTP body stream. |

## isChunked

```TypeScript
isChunked(): boolean
```

WebHttpBodyStream是否采用分块传输。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebHttpBodyStream-isChunked(): boolean--><!--Device-WebHttpBodyStream-isChunked(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | WebHttpBodyStream是否采用分块传输，如果采用分块传输则返回true，否则返回false。 |

## isEof

```TypeScript
isEof(): boolean
```

判断WebHttpBodyStream中的所有数据是否都已被读取。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebHttpBodyStream-isEof(): boolean--><!--Device-WebHttpBodyStream-isEof(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | WebHttpBodyStream中的所有数据是否都已被读取。 <br>如果所有数据都已被读取，则返回true。对于分块传输类型的WebHttpBodyStream，在第一次读取尝试之前返回false。 |

## isInMemory

```TypeScript
isInMemory(): boolean
```

判断WebHttpBodyStream中的上传数据是否在内存中。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebHttpBodyStream-isInMemory(): boolean--><!--Device-WebHttpBodyStream-isInMemory(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | WebHttpBodyStream中的上传数据是否在内存中。 <br>如果WebHttpBodyStream中的上传数据完全在内存中，并且所有读取请求都将同步成功，则返回true。对于分块传输类型的数据，预期返回false。 |

## read

```TypeScript
read(size: number): Promise<ArrayBuffer>
```

读取WebHttpBodyStream中的数据。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebHttpBodyStream-read(size: number): Promise<ArrayBuffer>--><!--Device-WebHttpBodyStream-read(size: number): Promise<ArrayBuffer>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 读取WebHttpBodyStream中的字节数。单位：字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise实例，用于获取WebHttpBodyStream中读取的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |

