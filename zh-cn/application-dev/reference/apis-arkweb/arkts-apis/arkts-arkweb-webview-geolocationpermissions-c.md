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

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin. |
| incognito | boolean | 否 | Whether to allow the specified origin to use the geolocation information in<br/>incognito mode. The value **true** means to allow the specified origin to use the geolocation information in<br/>incognito mode, and **false** means the opposite.<br/>Default value: **false**.<br/>If **null** or<br/>**undefined** is passed in, the value is **false**. [since 11] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../errorcode-universal.md#17100011-Invalid) | Invalid origin. |

## deleteAllGeolocation

```TypeScript
static deleteAllGeolocation(incognito?: boolean): void
```

Delete all geolocation permissions.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | Whether to clear the geolocation permission status of all sources in incognito<br/>mode. The value **true** means to clear the geolocation permission status of all sources in incognito mode,<br/>and **false** means the opposite.<br/>Default value: **false**.<br/>If **null** or **undefined** is passed in,<br/>the value is **false**. [since 11] |

## deleteGeolocation

```TypeScript
static deleteGeolocation(origin: string, incognito?: boolean): void
```

Delete geolocation permissions for specifies source.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin. |
| incognito | boolean | 否 | Whether to clear the geolocation permission status of a specified origin in<br/>incognito mode. The value **true** means to clear the geolocation permission status of a specified origin in<br/>incognito mode, and **false** means the opposite.<br/>Default value: **false**.<br/>If **null** or<br/>**undefined** is passed in, the value is **false**. [since 11] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../errorcode-universal.md#17100011-Invalid) | Invalid origin. |

## getAccessibleGeolocation

```TypeScript
static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise<boolean>
```

Gets the geolocation permission status of the specified source.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin. |
| incognito | boolean | 否 | Whether to obtain the geolocation permission status of the specified origin in<br/>incognito mode. The value **true** means to obtain the geolocation permission status of the specified origin<br/>in incognito mode, and **false** means the opposite.<br/>Default value: **false**.<br/>If **null** or<br/>**undefined** is passed, error code **401** is thrown. [since 11] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the geolocation permission status of the specified origin.<br/><br/>If the operation is successful, the value **true** means that the geolocation permission is granted, and<br/>**false** means the opposite.<br/><br/>If the operation fails, the geolocation permission status of the specified origin is not found. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../errorcode-universal.md#17100011-Invalid) | Invalid origin. |

## getAccessibleGeolocation

```TypeScript
static getAccessibleGeolocation(origin: string, callback: AsyncCallback<boolean>, incognito?: boolean): void
```

Gets the geolocation permission status of the specified source.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin. |
| callback | AsyncCallback&lt;boolean&gt; | 是 | Callback used to return the geolocation permission status of the<br/>specified origin.<br/>If the operation is successful, the value **true** means that the geolocation permission<br/>is granted, and **false** means the opposite.<br/>If the operation fails, the geolocation permission status of<br/>the specified origin is not found. |
| incognito | boolean | 否 | Whether to obtain the geolocation permission status of the specified origin in<br/>incognito mode. The value **true** means to obtain the geolocation permission status of the specified origin<br/>in incognito mode, and **false** means the opposite.<br/>Default value: **false**.<br/>If **null** or<br/>**undefined** is passed, error code **401** is thrown. [since 11] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../../errorcode-universal.md#17100011-Invalid) | Invalid origin. |

## getStoredGeolocation

```TypeScript
static getStoredGeolocation(incognito?: boolean): Promise<Array<string>>
```

Get all stored geolocation permission url source.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | Whether to obtain the geolocation permission status of all origins in incognito<br/>mode. The value **true** means to obtain the geolocation permission status of all origins in incognito mode,<br/>and **false** means the opposite.<br/>Default value: **false**.<br/>If **null** or **undefined** is passed,<br/>error code **401** is thrown. [since 11] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the geolocation permission status of all origins. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. 3.Parameter verification failed. |

## getStoredGeolocation

```TypeScript
static getStoredGeolocation(callback: AsyncCallback<Array<string>>, incognito?: boolean): void
```

Get all stored geolocation permission url source.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | Callback used to return the geolocation permission status of<br/>all origins. |
| incognito | boolean | 否 | Whether to obtain the geolocation permission status of all origins in incognito<br/>mode. The value **true** means to obtain the geolocation permission status of all origins in incognito mode,<br/>and **false** means the opposite.<br/>Default value: **false**.<br/>If **null** or **undefined** is passed,<br/>error code **401** is thrown. [since 11] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. 3.Parameter verification failed. |

