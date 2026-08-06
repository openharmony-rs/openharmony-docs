# WebStorage

Implements a WebStorage object to manage the Web SQL database and HTML5 Web Storage APIs. All Web components in an application share a WebStorage object. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_API Note\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_:\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_ You must load the Web component before calling the APIs in WebStorage. \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-webview-class WebStorage--><!--Device-webview-class WebStorage-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## deleteAllData

```TypeScript
static deleteAllData(incognito?: boolean): void
```

Deletes all data in the Web SQL Database.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static deleteAllData(incognito?: boolean): void--><!--Device-WebStorage-static deleteAllData(incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | Whether to delete all data in the Web SQL Database in incognito mode.{@code true} means to delete all data in the Web SQL Database in incognito mode;{@code false} means to delete all data in the Web SQL Database in normal non-incognito mode. |

## deleteOrigin

```TypeScript
static deleteOrigin(origin: string): void
```

Deletes all data in the specified origin.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static deleteOrigin(origin: string): void--><!--Device-WebStorage-static deleteOrigin(origin: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin, which is obtained through \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getOriginQuota

```TypeScript
static getOriginQuota(origin: string): Promise<double>
```

Get the web storage quota with the origin.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOriginQuota(origin: string): Promise<double>--><!--Device-WebStorage-static getOriginQuota(origin: string): Promise<double>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | The origin which to be inquired. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;double&gt; | - the promise returned by the function. Unit: byte. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin.@static |

## getOriginQuota

```TypeScript
static getOriginQuota(origin: string, callback: AsyncCallback<double>): void
```

Get the web storage quota with the origin.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOriginQuota(origin: string, callback: AsyncCallback<double>): void--><!--Device-WebStorage-static getOriginQuota(origin: string, callback: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | The origin which to be inquired. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;double&gt; | 是 | the callback of getOriginQuota. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin.@static |

## getOriginUsage

```TypeScript
static getOriginUsage(origin: string): Promise<double>
```

Get the web amount of storage with the origin.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOriginUsage(origin: string): Promise<double>--><!--Device-WebStorage-static getOriginUsage(origin: string): Promise<double>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | The origin which to be inquired. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;double&gt; | - the promise returned by the function. Unit: byte. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin.@static |

## getOriginUsage

```TypeScript
static getOriginUsage(origin: string, callback: AsyncCallback<double>): void
```

Get the web amount of storage with the origin.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOriginUsage(origin: string, callback: AsyncCallback<double>): void--><!--Device-WebStorage-static getOriginUsage(origin: string, callback: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | The origin which to be inquired. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;double&gt; | 是 | the callback of getOriginUsage. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin.@static |

## getOrigins

```TypeScript
static getOrigins(): Promise<Array<WebStorageOrigin>>
```

Obtains information about all origins that are currently using the Web SQL Database. This API uses a promise to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOrigins(): Promise<Array<WebStorageOrigin>>--><!--Device-WebStorage-static getOrigins(): Promise<Array<WebStorageOrigin>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;WebStorageOrigin&gt;&gt; | - Promise used to return the information about the origins. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100012](../../apis-arkweb/errorcode-webview.md#17100012-无可获取的webstorage源) | Invalid web storage origin. |

## getOrigins

```TypeScript
static getOrigins(callback: AsyncCallback<Array<WebStorageOrigin>>): void
```

Obtains information about all origins that are currently using the Web SQL Database. This API uses an asynchronous callback to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebStorage-static getOrigins(callback: AsyncCallback<Array<WebStorageOrigin>>): void--><!--Device-WebStorage-static getOrigins(callback: AsyncCallback<Array<WebStorageOrigin>>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;WebStorageOrigin&gt;&gt; | 是 | Callback used to return the information about the origins. For details, see \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100012](../../apis-arkweb/errorcode-webview.md#17100012-无可获取的webstorage源) | Invalid web storage origin. |

