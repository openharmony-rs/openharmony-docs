# WebStorage

通过WebStorage可管理Web SQL数据库接口和HTML5 Web存储接口，每个应用中的所有Web组件共享一个WebStorage。
> **说明：**  
>  
> - 本Class首批接口从API version 9开始支持。  
>  
> - 示例效果请以真机运行为准。  
>  
> - 目前调用WebStorage下的方法，都需要先加载Web组件。  
>  
> - 本Class下的接口在ArkWeb内核升级到M132版本后因内核废弃Web SQL，对Web SQL数据库的管理失效。ArkWeb内核版本参考ArkWeb简介  
> [约束与限制](../../../web/web-component-overview.md#约束与限制)。

**起始版本：** 9

<!--Device-webview-class WebStorage--><!--Device-webview-class WebStorage-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## deleteAllData

```TypeScript
static deleteAllData(incognito?: boolean): void
```

清除被JavaScript存储API使用的所有存储数据，这包括Web SQL数据库和HTML5支持的Web存储API。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebStorage-static deleteAllData(incognito?: boolean): void--><!--Device-WebStorage-static deleteAllData(incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | true表示删除所有隐私模式下内存中的web数据，false表示删除正常非隐私模式下Web的SQL数据库当前使用的所有存储。<br>默认值：false。<br>传入undefined或null时为false。<br>**起始版本：** 11 |

## deleteOrigin

```TypeScript
static deleteOrigin(origin: string): void
```

清除指定源所使用的存储。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebStorage-static deleteOrigin(origin: string): void--><!--Device-WebStorage-static deleteOrigin(origin: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | 指定源的字符串索引，来自于[getOrigins](webview.WebStorage.static getOrigins(callback: AsyncCallback&lt;Array<WebStorageOrigin>&gt;))。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getOriginQuota

```TypeScript
static getOriginQuota(origin: string): Promise<number>
```

以Promise方式异步获取指定源的Web SQL数据库和HTML5支持的Web存储API的存储配额，配额以字节为单位。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebStorage-static getOriginQuota(origin: string): Promise<number>--><!--Device-WebStorage-static getOriginQuota(origin: string): Promise<number>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | 指定源的字符串索引 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise实例，用于获取指定源的存储配额。<br>单位：byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getOriginQuota

```TypeScript
static getOriginQuota(origin: string, callback: AsyncCallback<number>): void
```

使用callback回调异步获取指定源的Web SQL数据库和HTML5支持的Web存储API的存储配额，配额以字节为单位。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebStorage-static getOriginQuota(origin: string, callback: AsyncCallback<number>): void--><!--Device-WebStorage-static getOriginQuota(origin: string, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | 指定源的字符串索引。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 指定源的存储配额。<br>number是long型整数，范围为[-2147483648, 2147483647]。<br>单位：byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getOriginUsage

```TypeScript
static getOriginUsage(origin: string): Promise<number>
```

以Promise方式异步获取指定源的Web SQL数据库和HTML5支持的Web存储API的存储量，存储量以字节为单位。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebStorage-static getOriginUsage(origin: string): Promise<number>--><!--Device-WebStorage-static getOriginUsage(origin: string): Promise<number>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | 指定源的字符串索引 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise实例，用于获取指定源的存储量。<br>单位：byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getOriginUsage

```TypeScript
static getOriginUsage(origin: string, callback: AsyncCallback<number>): void
```

以回调方式异步获取指定源的Web SQL数据库和HTML5支持的Web存储API的存储量，存储量以字节为单位。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebStorage-static getOriginUsage(origin: string, callback: AsyncCallback<number>): void--><!--Device-WebStorage-static getOriginUsage(origin: string, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | 指定源的字符串索引 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 指定源的存储量。<br>单位：byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-输入参数origin错误) | Invalid origin. |

## getOrigins

```TypeScript
static getOrigins(): Promise<Array<WebStorageOrigin>>
```

以Promise方式异步获取当前使用Web SQL数据库和HTML5支持的Web存储API的所有源的信息。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebStorage-static getOrigins(): Promise<Array<WebStorageOrigin>>--><!--Device-WebStorage-static getOrigins(): Promise<Array<WebStorageOrigin>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;WebStorageOrigin&gt;&gt; | Promise used to return the information about the origins. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100012](../errorcode-webview.md#17100012-无可获取的webstorage源) | Invalid web storage origin. |

## getOrigins

```TypeScript
static getOrigins(callback: AsyncCallback<Array<WebStorageOrigin>>): void
```

以回调方式异步获取当前使用Web SQL数据库和HTML5支持的Web存储API的所有源的信息。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebStorage-static getOrigins(callback: AsyncCallback<Array<WebStorageOrigin>>): void--><!--Device-WebStorage-static getOrigins(callback: AsyncCallback<Array<WebStorageOrigin>>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;WebStorageOrigin&gt;&gt; | 是 | 以数组方式返回源的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100012](../errorcode-webview.md#17100012-无可获取的webstorage源) | Invalid web storage origin. |

