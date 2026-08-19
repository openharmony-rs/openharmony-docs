# GeolocationPermissions

GeolocationPermissions是Web组件的地理位置权限管理对象，提供对Web组件中已保存的地理位置权限状态的查询、授权、删除等管理能力。通过GeolocationPermissions，应用可以在网页发起地理位置请 求之前预先授权特定源的访问权限，也可以主动查询或清除已保存的权限记录，而无需依赖网页请求时的弹窗授权流程。 GeolocationPermissions适用于需要主动管理Web组件地理位置权限的场景，例如：应用希望预先授权信任的网站访问地理位置，避免每次访问都弹出授权提示；或应用需要清除用户不再需要的地理位置权限记录。访问地理位置时需添 加权限：ohos.permission.LOCATION、ohos.permission.APPROXIMATELY_LOCATION、ohos.permission.LOCATION_IN_BACKGROUND，具体权限说明请参 考[申请位置权限开发指导](../../../device/location/location-permission-guidelines.md)。

**起始版本：** 9

<!--Device-webview-class GeolocationPermissions--><!--Device-webview-class GeolocationPermissions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## allowGeolocation

```TypeScript
static allowGeolocation(origin: string, incognito?: boolean): void
```

允许指定源使用地理位置接口。用于预先授权信任网站的地理位置权限，避免重复弹窗，或由应用主动管理特定源的地理位置授权。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GeolocationPermissions-static allowGeolocation(origin: string, incognito?: boolean): void--><!--Device-GeolocationPermissions-static allowGeolocation(origin: string, incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | 指定源的字符串。 <br>origin格式必须遵循RFC 6454中定义的格式。传入不符合RFC 6454格式的字符串时抛出异常，错误码17100011。 |
| incognito | boolean | 否 | true表示隐私模式下允许指定源使用地理位置，false表示正常非隐私模式下允许指定源使用地理位置。 <br>默认值：false。 <br>传入null或undefined时为false。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## deleteAllGeolocation

```TypeScript
static deleteAllGeolocation(incognito?: boolean): void
```

清除所有源的地理位置权限状态。用于用户退出登录或一键清除等场景下批量撤销地理位置授权。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GeolocationPermissions-static deleteAllGeolocation(incognito?: boolean): void--><!--Device-GeolocationPermissions-static deleteAllGeolocation(incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | true表示隐私模式下清除所有源的地理位置权限状态，false表示正常非隐私模式下清除所有源的地理位置权限状态。 <br>默认值：false。 <br>传入null或undefined时为false。<br>**起始版本：** 11 |

## deleteGeolocation

```TypeScript
static deleteGeolocation(origin: string, incognito?: boolean): void
```

清除指定源的地理位置权限状态。用于撤销指定网站的地理位置授权，或为应用提供按源管理权限的能力。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GeolocationPermissions-static deleteGeolocation(origin: string, incognito?: boolean): void--><!--Device-GeolocationPermissions-static deleteGeolocation(origin: string, incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | 指定源的字符串。 <br>origin格式必须遵循RFC 6454中定义的格式。传入不符合RFC 6454格式的字符串时抛出异常，错误码17100011。 |
| incognito | boolean | 否 | true表示隐私模式下清除指定源的地理位置权限状态，false表示正常非隐私模式下清除指定源的地理位置权限状态。 <br>默认值：false。 <br>传入null或undefined时为false。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getAccessibleGeolocation

```TypeScript
static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise<boolean>
```

以Promise方式异步获取指定源的地理位置权限状态。用于查询指定网站的地理位置授权结果，如设置界面展示权限状态或访问前校验授权。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GeolocationPermissions-static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise<boolean>--><!--Device-GeolocationPermissions-static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise<boolean>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | 指定源的字符串。 <br>origin格式必须遵循RFC 6454中定义的格式。传入不符合RFC 6454格式的字符串时抛出异常，错误码17100011。 |
| incognito | boolean | 否 | true表示在隐私模式下获取指定源的地理位置权限状态，false表示在正常模式下获取。 <br>默认值：false。 <br>传入null或undefined时会抛出异常错误码401。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise实例，用于获取指定源的权限状态。 <br>获取成功，true表示已授权，false表示拒绝访问。 <br>获取失败，表示不存在指定源的权限状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getAccessibleGeolocation

```TypeScript
static getAccessibleGeolocation(origin: string, callback: AsyncCallback<boolean>, incognito?: boolean): void
```

以回调方式异步获取指定源的地理位置权限状态。用于查询指定网站的地理位置授权结果，如设置界面展示权限状态或访问前校验授权。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GeolocationPermissions-static getAccessibleGeolocation(origin: string, callback: AsyncCallback<boolean>, incognito?: boolean): void--><!--Device-GeolocationPermissions-static getAccessibleGeolocation(origin: string, callback: AsyncCallback<boolean>, incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | 指定源的字符串。 <br>origin格式必须遵循RFC 6454中定义的格式。传入不符合RFC 6454格式的字符串时抛出异常，错误码17100011。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 返回指定源的地理位置权限状态。 <br>获取成功，true表示已授权，false表示拒绝访问。 <br>获取失败，表示不存在指定源的权限状态。 |
| incognito | boolean | 否 | true表示在隐私模式下获取指定源的地理位置权限状态，false表示在正常模式下获取。 <br>默认值：false。 <br>传入null或undefined时会抛出异常错误码401。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getStoredGeolocation

```TypeScript
static getStoredGeolocation(incognito?: boolean): Promise<Array<string>>
```

以Promise方式异步获取已存储地理位置权限状态的所有源信息。用于获取已授权地理位置权限的网站列表，如隐私设置页展示或权限管理界面的批量管理。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GeolocationPermissions-static getStoredGeolocation(incognito?: boolean): Promise<Array<string>>--><!--Device-GeolocationPermissions-static getStoredGeolocation(incognito?: boolean): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | true表示在隐私模式下获取已存储地理位置权限状态的所有源信息，false表示在正常模式下获取。 <br>默认值：false。 <br>传入null或undefined时会抛出异常错误码401。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise实例，用于获取已存储地理位置权限状态的所有源信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |

## getStoredGeolocation

```TypeScript
static getStoredGeolocation(callback: AsyncCallback<Array<string>>, incognito?: boolean): void
```

以回调方式异步获取已存储地理位置权限状态的所有源信息。用于获取已授权地理位置权限的网站列表，如隐私设置页展示或权限管理界面的批量管理。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GeolocationPermissions-static getStoredGeolocation(callback: AsyncCallback<Array<string>>, incognito?: boolean): void--><!--Device-GeolocationPermissions-static getStoredGeolocation(callback: AsyncCallback<Array<string>>, incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | 返回已存储地理位置权限状态的所有源信息。回调参数包括：error（错误对象，获取成功时为null）和origins（已存储地 理位置权限的源字符串数组，每个元素为遵循RFC 6454中定义格式的源字符串）。获取失败时，error为错误对象。 |
| incognito | boolean | 否 | true表示在隐私模式下获取已存储地理位置权限状态的所有源信息，false表示在正常模式下获取。 <br>默认值：false。 <br>传入null或undefined时会抛出异常错误码401。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |

