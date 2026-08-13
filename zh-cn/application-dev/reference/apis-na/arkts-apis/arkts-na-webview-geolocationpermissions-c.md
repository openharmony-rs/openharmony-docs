# GeolocationPermissions

Implements a GeolocationPermissions object. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; You must load the Web component before calling the APIs in GeolocationPermissions. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-class GeolocationPermissions--><!--Device-webview-class GeolocationPermissions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## allowGeolocation

```TypeScript
static allowGeolocation(origin: string, incognito?: boolean): void
```

Allows the specified origin to use the geolocation information.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-GeolocationPermissions-static allowGeolocation(origin: string, incognito?: boolean): void--><!--Device-GeolocationPermissions-static allowGeolocation(origin: string, incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin. |
| incognito | boolean | 否 | Whether to allow the specified origin to use the geolocation information in incognito mode. {@code true} means to allow the specified origin to use the geolocation information in incognito mode; {@code false} means to allow the specified origin to use the geolocation information in normal non-incognito mode. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## deleteAllGeolocation

```TypeScript
static deleteAllGeolocation(incognito?: boolean): void
```

Clears the geolocation permission status of all sources.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-GeolocationPermissions-static deleteAllGeolocation(incognito?: boolean): void--><!--Device-GeolocationPermissions-static deleteAllGeolocation(incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | Whether to clear the geolocation permission status of all sources in incognito mode. {@code true} means to clear the geolocation permission status of all sources in incognito mode; {@code false} means to clear the geolocation permission status of all sources in normal non-incognito mode. |

## deleteGeolocation

```TypeScript
static deleteGeolocation(origin: string, incognito?: boolean): void
```

Delete geolocation permissions for specifies source.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-GeolocationPermissions-static deleteGeolocation(origin: string, incognito?: boolean): void--><!--Device-GeolocationPermissions-static deleteGeolocation(origin: string, incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Url source. |
| incognito | boolean | 否 | {@code true} delete geolocation permissions for specifies source in incognito mode; {@code false} otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getAccessibleGeolocation

```TypeScript
static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise<boolean>
```

Gets the geolocation permission status of the specified source.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-GeolocationPermissions-static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise<boolean>--><!--Device-GeolocationPermissions-static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise<boolean>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Url source. |
| incognito | boolean | 否 | {@code true} gets the geolocation permission status of the specified source in incognito mode; {@code false} otherwise. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | A Promise instance that obtains the permission status of the specified source and obtains successfully, true for authorization, false for access denial. Failed to get, indicating that the permission status of the specified source does not exist. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getAccessibleGeolocation

```TypeScript
static getAccessibleGeolocation(origin: string, callback: AsyncCallback<boolean>, incognito?: boolean): void
```

Gets the geolocation permission status of the specified source.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-GeolocationPermissions-static getAccessibleGeolocation(origin: string, callback: AsyncCallback<boolean>, incognito?: boolean): void--><!--Device-GeolocationPermissions-static getAccessibleGeolocation(origin: string, callback: AsyncCallback<boolean>, incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Url source. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | Returns the geolocation permission status for the specified source. Successful acquisition, true means authorized, false means access is denied. Failed to get, indicating that the permission status of the specified source does not exist. |
| incognito | boolean | 否 | {@code true} gets the geolocation permission status of the specified source in incognito mode; {@code false} otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../apis-arkweb/errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getStoredGeolocation

```TypeScript
static getStoredGeolocation(incognito?: boolean): Promise<Array<string>>
```

Get all stored geolocation permission url source.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-GeolocationPermissions-static getStoredGeolocation(incognito?: boolean): Promise<Array<string>>--><!--Device-GeolocationPermissions-static getStoredGeolocation(incognito?: boolean): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | {@code true} get all stored geolocation permission url source in incognito mode; {@code false} otherwise. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | A Promise instance that gets all source information about the stored geolocation permission state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |

## getStoredGeolocation

```TypeScript
static getStoredGeolocation(callback: AsyncCallback<Array<string>>, incognito?: boolean): void
```

Get all stored geolocation permission url source.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-GeolocationPermissions-static getStoredGeolocation(callback: AsyncCallback<Array<string>>, incognito?: boolean): void--><!--Device-GeolocationPermissions-static getStoredGeolocation(callback: AsyncCallback<Array<string>>, incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | Returns all source information for stored geolocation permission states. |
| incognito | boolean | 否 | {@code true} gets all stored geolocation permission url source in incognito mode; {@code false} otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |

