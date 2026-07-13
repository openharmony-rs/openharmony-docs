# WebHttpBodyStream

The http body stream of the request.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## getPosition

```TypeScript
getPosition(): number
```

读取WebHttpBodyStream中当前的读取位置。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

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

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取WebHttpBodyStream中的数据大小。单位：字节。 |

## initialize

```TypeScript
initialize(): Promise<void>
```

初始化WebHttpBodyStream。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

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

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

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

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | WebHttpBodyStream中的所有数据是否都已被读取。<br>如果所有数据都已被读取，则返回true。对于分块传输类型的WebHttpBodyStream，在第一次读取尝试之前返回false。 |

## isInMemory

```TypeScript
isInMemory(): boolean
```

判断WebHttpBodyStream中的上传数据是否在内存中。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | WebHttpBodyStream中的上传数据是否在内存中。<br>如果WebHttpBodyStream中的上传数据完全在内存中，并且所有读取请求都将同步成功，则返回true。对于分块传输类型的数据，预期返回false。 |

## read

```TypeScript
read(size: number): Promise<ArrayBuffer>
```

读取WebHttpBodyStream中的数据。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

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
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

