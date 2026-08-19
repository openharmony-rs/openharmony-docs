# WebDataBase

Implements a WebDataBase object. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:<br> You must load the Web component before calling the APIs in WebDataBase. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-class WebDataBase--><!--Device-webview-class WebDataBase-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## deleteHttpAuthCredentials

```TypeScript
static deleteHttpAuthCredentials(): void
```

Deletes all HTTP authentication credentials saved in the cache. This API returns the result synchronously.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDataBase-static deleteHttpAuthCredentials(): void--><!--Device-WebDataBase-static deleteHttpAuthCredentials(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## existHttpAuthCredentials

```TypeScript
static existHttpAuthCredentials(): boolean
```

Get whether instances holds any http authentication credentials.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDataBase-static existHttpAuthCredentials(): boolean--><!--Device-WebDataBase-static existHttpAuthCredentials(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true if instances saved any http authentication credentials otherwise false. |

## getHttpAuthCredentials

```TypeScript
static getHttpAuthCredentials(host: string, realm: string): Array<string>
```

Get http authentication credentials.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDataBase-static getHttpAuthCredentials(host: string, realm: string): Array<string>--><!--Device-WebDataBase-static getHttpAuthCredentials(host: string, realm: string): Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | The host to which the credentials apply. |
| realm | string | 是 | The realm to which the credentials apply. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | Return an array containing username and password. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |

## saveHttpAuthCredentials

```TypeScript
static saveHttpAuthCredentials(host: string, realm: string, username: string, password: string): void
```

Saves HTTP authentication credentials for a given host and realm. This API returns the result synchronously.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebDataBase-static saveHttpAuthCredentials(host: string, realm: string, username: string, password: string): void--><!--Device-WebDataBase-static saveHttpAuthCredentials(host: string, realm: string, username: string, password: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | Host to which HTTP authentication credentials apply. |
| realm | string | 是 | Realm to which HTTP authentication credentials apply. |
| username | string | 是 | User name. |
| password | string | 是 | Password. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |

