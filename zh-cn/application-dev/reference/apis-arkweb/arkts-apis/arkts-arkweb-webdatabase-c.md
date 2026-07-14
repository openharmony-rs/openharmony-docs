# WebDataBase

Web组件数据库管理对象。

> **说明：**
>
> - 本Class首批接口从API version 9开始支持。
>
> - 示例效果请以真机运行为准。
>
> - 目前调用WebDataBase下的方法，都需要先加载Web组件。

**起始版本：** 9

**系统能力：** SystemCapability.Web.Webview.Core

## deleteHttpAuthCredentials

```TypeScript
static deleteHttpAuthCredentials(): void
```

清除所有已保存的HTTP身份验证凭据，该方法为同步方法。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## existHttpAuthCredentials

```TypeScript
static existHttpAuthCredentials(): boolean
```

判断是否存在任何已保存的HTTP身份验证凭据，该方法为同步方法。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否存在任何已保存的HTTP身份验证凭据。<br>存在返回true，不存在返回false。 |

## getHttpAuthCredentials

```TypeScript
static getHttpAuthCredentials(host: string, realm: string): Array<string>
```

检索给定主机和域的HTTP身份验证凭据，该方法为同步方法。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | HTTP身份验证凭据应用的主机。 |
| realm | string | 是 | HTTP身份验证凭据应用的域。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 包含用户名和密码的数组，检索失败返回空数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## saveHttpAuthCredentials

```TypeScript
static saveHttpAuthCredentials(host: string, realm: string, username: string, password: string): void
```

保存给定主机和域的HTTP身份验证凭据，该方法为同步方法。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | HTTP身份验证凭据应用的主机。 |
| realm | string | 是 | HTTP身份验证凭据应用的域。 |
| username | string | 是 | 用户名。 |
| password | string | 是 | 密码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

