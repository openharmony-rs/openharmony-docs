# WebStorage

Implements a WebStorage object to manage the Web SQL database and HTML5 Web Storage APIs. All Web components in an application share a WebStorage object. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:<br> You must load the Web component before calling the APIs in WebStorage. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-class WebStorage--><!--Device-webview-class WebStorage-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## deleteAllData

```TypeScript
static deleteAllData(incognito?: boolean): void
```

Deletes all data in the Web SQL Database.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static deleteAllData(incognito?: boolean): void--><!--Device-WebStorage-static deleteAllData(incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | Whether to delete all data in the Web SQL Database in incognito mode. {@code true} means to delete all data in the Web SQL Database in incognito mode; {@code false} means to delete all data in the Web SQL Database in normal non-incognito mode. |

## deleteOrigin

```TypeScript
static deleteOrigin(origin: string): void
```

Deletes all data in the specified origin.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static deleteOrigin(origin: string): void--><!--Device-WebStorage-static deleteOrigin(origin: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin, which is obtained through [getOrigins](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webstorage-c.md#getorigins). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getOriginQuota

```TypeScript
static getOriginQuota(origin: string): Promise<double>
```

Get the web storage quota with the origin.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOriginQuota(origin: string): Promise<double>--><!--Device-WebStorage-static getOriginQuota(origin: string): Promise<double>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | The origin which to be inquired. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;double&gt; | the promise returned by the function. Unit: byte. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. @static |

## getOriginQuota

```TypeScript
static getOriginQuota(origin: string, callback: AsyncCallback<double>): void
```

Get the web storage quota with the origin.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOriginQuota(origin: string, callback: AsyncCallback<double>): void--><!--Device-WebStorage-static getOriginQuota(origin: string, callback: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | The origin which to be inquired. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;double&gt; | 是 | the callback of getOriginQuota. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. @static |

## getOriginUsage

```TypeScript
static getOriginUsage(origin: string): Promise<double>
```

Get the web amount of storage with the origin.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOriginUsage(origin: string): Promise<double>--><!--Device-WebStorage-static getOriginUsage(origin: string): Promise<double>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | The origin which to be inquired. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;double&gt; | the promise returned by the function. Unit: byte. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. @static |

## getOriginUsage

```TypeScript
static getOriginUsage(origin: string, callback: AsyncCallback<double>): void
```

Get the web amount of storage with the origin.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOriginUsage(origin: string, callback: AsyncCallback<double>): void--><!--Device-WebStorage-static getOriginUsage(origin: string, callback: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | The origin which to be inquired. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;double&gt; | 是 | the callback of getOriginUsage. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. @static |

## getOrigins

```TypeScript
static getOrigins(): Promise<Array<WebStorageOrigin>>
```

Obtains information about all origins that are currently using the Web SQL Database. This API uses a promise to return the result.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOrigins(): Promise<Array<WebStorageOrigin>>--><!--Device-WebStorage-static getOrigins(): Promise<Array<WebStorageOrigin>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[WebStorageOrigin](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webstorageorigin-i.md)&gt;&gt; | Promise used to return the information about the origins. For details, see { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100012](../../apis-arkweb/errorcode-webview.md#17100012-无可获取的webstorage源) | Invalid web storage origin. |

## getOrigins

```TypeScript
static getOrigins(callback: AsyncCallback<Array<WebStorageOrigin>>): void
```

Obtains information about all origins that are currently using the Web SQL Database. This API uses an asynchronous callback to return the result.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOrigins(callback: AsyncCallback<Array<WebStorageOrigin>>): void--><!--Device-WebStorage-static getOrigins(callback: AsyncCallback<Array<WebStorageOrigin>>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[WebStorageOrigin](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webstorageorigin-i.md)&gt;&gt; | 是 | Callback used to return the information about the origins. For details, see [WebStorageOrigin](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webstorageorigin-i.md). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100012](../../apis-arkweb/errorcode-webview.md#17100012-无可获取的webstorage源) | Invalid web storage origin. |

