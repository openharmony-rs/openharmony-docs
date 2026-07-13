# GeolocationPermissions

Provides a method for managing web geographic location permissions.

**起始版本：** 9

**系统能力：** SystemCapability.Web.Webview.Core

## allowGeolocation

```TypeScript
static allowGeolocation(origin: string, incognito?: boolean): void
```

Allow geolocation permissions for specifies source.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin. |
| incognito | boolean | 否 | Whether to allow the specified origin to use the geolocation information inincognito mode. The value **true** means to allow the specified origin to use the geolocation information inincognito mode, and **false** means the opposite.<br>Default value: **false**.<br>If **null** or**undefined** is passed in, the value is **false**.<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. The origin format must follow defined in RFC 6454. |

## deleteAllGeolocation

```TypeScript
static deleteAllGeolocation(incognito?: boolean): void
```

Delete all geolocation permissions.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | Whether to clear the geolocation permission status of all sources in incognitomode. The value **true** means to clear the geolocation permission status of all sources in incognito mode,and **false** means the opposite.<br>Default value: **false**.<br>If **null** or **undefined** is passed in,the value is **false**.<br>**起始版本：** 11 |

## deleteGeolocation

```TypeScript
static deleteGeolocation(origin: string, incognito?: boolean): void
```

Delete geolocation permissions for specifies source.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin. |
| incognito | boolean | 否 | Whether to clear the geolocation permission status of a specified origin inincognito mode. The value **true** means to clear the geolocation permission status of a specified origin inincognito mode, and **false** means the opposite.<br>Default value: **false**.<br>If **null** or**undefined** is passed in, the value is **false**.<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. The origin format must follow defined in RFC 6454. |

## getAccessibleGeolocation

```TypeScript
static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise<boolean>
```

Gets the geolocation permission status of the specified source.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin. |
| incognito | boolean | 否 | Whether to obtain the geolocation permission status of the specified origin inincognito mode. The value **true** means to obtain the geolocation permission status of the specified originin incognito mode, and **false** means the opposite.<br>Default value: **false**.<br>If **null** or**undefined** is passed, error code **401** is thrown.<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the geolocation permission status of the specified origin.<br>If the operation is successful, the value **true** means that the geolocation permission is granted, and**false** means the opposite.<br>If the operation fails, the geolocation permission status of the specified origin is not found. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. The origin format must follow defined in RFC 6454. |

## getAccessibleGeolocation

```TypeScript
static getAccessibleGeolocation(origin: string, callback: AsyncCallback<boolean>, incognito?: boolean): void
```

Gets the geolocation permission status of the specified source.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin. |
| callback | AsyncCallback&lt;boolean&gt; | 是 | Callback used to return the geolocation permission status of thespecified origin.<br>If the operation is successful, the value **true** means that the geolocation permissionis granted, and **false** means the opposite.<br>If the operation fails, the geolocation permission status ofthe specified origin is not found. |
| incognito | boolean | 否 | Whether to obtain the geolocation permission status of the specified origin inincognito mode. The value **true** means to obtain the geolocation permission status of the specified originin incognito mode, and **false** means the opposite.<br>Default value: **false**.<br>If **null** or**undefined** is passed, error code **401** is thrown.<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. The origin format must follow defined in RFC 6454. |

## getStoredGeolocation

```TypeScript
static getStoredGeolocation(incognito?: boolean): Promise<Array<string>>
```

Get all stored geolocation permission url source.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | Whether to obtain the geolocation permission status of all origins in incognitomode. The value **true** means to obtain the geolocation permission status of all origins in incognito mode,and **false** means the opposite.<br>Default value: **false**.<br>If **null** or **undefined** is passed,error code **401** is thrown.<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the geolocation permission status of all origins. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## getStoredGeolocation

```TypeScript
static getStoredGeolocation(callback: AsyncCallback<Array<string>>, incognito?: boolean): void
```

Get all stored geolocation permission url source.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | Callback used to return the geolocation permission status ofall origins. |
| incognito | boolean | 否 | Whether to obtain the geolocation permission status of all origins in incognitomode. The value **true** means to obtain the geolocation permission status of all origins in incognito mode,and **false** means the opposite.<br>Default value: **false**.<br>If **null** or **undefined** is passed,error code **401** is thrown.<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

