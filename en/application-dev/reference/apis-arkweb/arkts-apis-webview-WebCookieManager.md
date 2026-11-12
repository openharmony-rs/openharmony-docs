# Class (WebCookieManager)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=31d045953794e03aa2b9b22d12ee8034b9ab7518 translatedAt=2026-11-06T11:07:24.022Z pushedAt=2026-11-10T02:22:33.374Z nl=1 -->

WebCookieManager is the cookie manager for Web components, providing global management capabilities for cookies in Web components. With this class, developers can obtain, set, save, and clear cookies, as well as control cookie permissions. All methods of this class are static, and all Web components in an app share a single WebCookieManager instance. The cookie format complies with the [RFC6265](https://www.rfc-editor.org/info/rfc6265/) standard.

When browsing web pages in Privacy Mode, data such as cookies and caches are not written to local persistent storage. After the Web component in Privacy Mode is destroyed, this data is cleared and not retained.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effects are subject to the actual running on a real device.
>
> - By default, static methods must be used on the user interface (UI) thread. Since API version 26.0.1, after [setLazyInitializeWebEngine](#setlazyinitializewebengine22) is set to true, static methods are supported for use on non-user interface (UI) threads.

## Modules to Import

```ts
import { webview } from '@kit.ArkWeb';
```

## fetchCookieSync<sup>11+</sup>

static fetchCookieSync(url: string, incognito?: boolean): string

Obtains the cookies corresponding to the specified URL.

> **NOTE**
>
> - The system automatically deletes expired cookies. For data with the same key name, the new data overwrites the previous data.
> 
> - To obtain usable cookies, you are advised to pass a complete URL to fetchCookieSync.
> 
> - fetchCookieSync is used to obtain all cookies. Each cookie value is separated by "; ", but a specific cookie value cannot be obtained individually.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                     |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL to which the cookies to get belong. A complete URL is recommended. |
| incognito    | boolean | No  | Whether to obtain the cookie in incognito mode. The value **true** means to obtain the cookie in incognito mode, and **false** means the opposite.<br>The default value is **false**.<br>If **undefined** or **null** is passed, error code **401** will be thrown.|

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| string | Cookies corresponding to the specified URL. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100002 | URL error. No valid cookie found for the specified URL. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('fetchCookieSync')
        .onClick(() => {
          try {
            let value = webview.WebCookieManager.fetchCookieSync('https://www.example.com');
            console.info("fetchCookieSync cookie = " + value);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## fetchCookieSync

static fetchCookieSync(url: string, incognito?: boolean, includePartitionedCookies?: boolean): string

Obtains the cookies corresponding to a specified URL. The optional parameter incognito specifies whether to obtain cookies in Privacy Mode, and the optional parameter includePartitionedCookies specifies whether to obtain first-party partitioned cookies.

> **NOTE**
>
> - The system automatically deletes expired cookies. For data with the same key name, the new data overwrites the previous data.
>
> - To obtain usable cookies, a complete URL must be passed to fetchCookieSync.
>
> - fetchCookieSync is used to obtain all cookies. Each cookie value is separated by "; ", but a specific cookie value cannot be obtained individually.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL of the cookies to get. A complete URL is recommended. |
| incognito | boolean | No | Whether to obtain the in-memory cookies of the Web component in Privacy Mode. The value **true** indicates Privacy Mode, and **false** indicates Non-Privacy Mode.<br>Default value: **false**.<br>Passing **undefined** or **null** throws error code 401. |
| includePartitionedCookies | boolean | No | Whether to allow getting first-party partitioned cookies. true indicates allowed, false indicates not allowed.<br>Default value: false.<br>Passing undefined or null throws an exception error code 401. |

**Return value**

| Type | Description |
| ------ | ------------------------- |
| string | The cookies corresponding to the specified URL. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| ID | Error Message |
| -------- | ------------------------------------------------------ |
| 17100002 | URL error. No valid cookie found for the specified URL. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('fetchCookieSync')
        .onClick(() => {
          try {
            let value = webview.WebCookieManager.fetchCookieSync('https://www.example.com', false, true);
            console.info("fetchCookieSync cookie = " + value);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## fetchCookie<sup>11+</sup>

static fetchCookie(url: string, callback: AsyncCallback\<string>): void

Obtains the cookies corresponding to a specified URL. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                     |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL to which the cookies to get belong. A complete URL is recommended. |
| callback | AsyncCallback\<string> | Yes | Callback function used to get the cookies. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 17100002 | URL error. No valid cookie found for the specified URL.   |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('fetchCookie')
        .onClick(() => {
          try {
            webview.WebCookieManager.fetchCookie('https://www.example.com', (error, cookie) => {
              if (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
                return;
              }
              if (cookie) {
                console.info('fetchCookie cookie = ' + cookie);
              }
            })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## fetchCookie<sup>11+</sup>

static fetchCookie(url: string): Promise\<string>

Obtains the cookies corresponding to a specified URL. This API uses a promise to return the result.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                     |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL to which the cookies to get belong. A complete URL is recommended. |

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| Promise\<string> | Promise instance, used to get the cookies corresponding to the specified URL. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 17100002 | URL error. No valid cookie found for the specified URL.  |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('fetchCookie')
        .onClick(() => {
          try {
            webview.WebCookieManager.fetchCookie('https://www.example.com')
              .then(cookie => {
                console.info("fetchCookie cookie = " + cookie);
              })
              .catch((error: BusinessError) => {
                console.error(`ErrorCode: ${error.code},  Message: ${error.message}`);
              })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## fetchCookie<sup>14+</sup>

static fetchCookie(url: string, incognito: boolean): Promise\<string>

Obtains the cookies corresponding to a specified URL. This API uses a promise to return the result.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                     |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL to which the cookies belong. It is recommended to use the complete URL. |
| incognito    | boolean | Yes  | Whether to obtain the cookie in incognito mode. The value **true** means to obtain the cookie in incognito mode, and **false** means the opposite.|

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| Promise\<string> | Promise instance, used to get the specified cookies corresponding to the URL. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 17100002 | URL error. No valid cookie found for the specified URL. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('fetchCookie')
        .onClick(() => {
          try {
            webview.WebCookieManager.fetchCookie('https://www.example.com', false)
              .then(cookie => {
                console.info("fetchCookie cookie = " + cookie);
              })
              .catch((error: BusinessError) => {
                console.error(`ErrorCode: ${error.code},  Message: ${error.message}`);
              })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## fetchCookie

static fetchCookie(url: string, incognito: boolean, includePartitionedCookies: boolean): Promise\<string>

Obtains the cookies corresponding to a specified URL. The parameter incognito specifies whether to obtain cookies in Privacy Mode, and the parameter includePartitionedCookies specifies whether to obtain first-party partitioned cookies. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL of the cookies to get. A complete URL is recommended. |
| incognito | boolean | Yes | Whether to obtain the in-memory cookies of the Web component in Privacy Mode. The value **true** indicates Privacy Mode, and **false** indicates Non-Privacy Mode.<br>Passing **undefined** or **null** throws error code 401. |
| includePartitionedCookies | boolean | Yes | Whether to allow getting first-party partitioned cookies. true indicates allowed, false indicates not allowed. <br>Passing undefined or null throws an exception error code 401. |

**Return value**

| Type | Description |
| ------ | ------------------------- |
| Promise\<string> | Promise object, used to get the cookies corresponding to the specified URL. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| ID | Error Message |
| -------- | ------------------------------------------------------ |
| 17100002 | URL error. No valid cookie found for the specified URL. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('fetchCookie')
        .onClick(() => {
          try {
            webview.WebCookieManager.fetchCookie('https://www.example.com', false, true)
              .then(cookie => {
                console.info("fetchCookie cookie = " + cookie);
              })
              .catch((error: BusinessError) => {
                console.error(`ErrorCode: ${error.code},  Message: ${error.message}`);
              })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## fetchAllCookies<sup>23+</sup>

static fetchAllCookies(incognito: boolean): Promise\<Array\<WebHttpCookie\>\>

Obtains all cookies. This API uses a promise to return the result.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --------- | ------- | -- | -------------------------------------- |
| incognito | boolean | Yes | true indicates getting all cookies of the webview in privacy mode, and false indicates all cookies in normal non-privacy mode. |

**Return value**

| Type | Description |
| ------ | ------------------------- |
| Promise\<Array\<[WebHttpCookie](./arkts-apis-webview-i.md#webhttpcookie23)\>\> | Promise object, used to get all cookies and their corresponding field values. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController()

  build() {
    Row() {
      Column() {
        Button('Config Cookie')
        .onClick(() => {
          try {
            webview.WebCookieManager.configCookieSync('https://www.example.com', 'a=b');
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })

        Button('Get All Cookies')
        .onClick(() => {
          webview.WebCookieManager.fetchAllCookies(false).then((cookies) => {
            for (let i = 0; i < cookies.length; i++) {
              console.info('fetchAllCookies cookie[' + i + '].name = ' + cookies[i].name);
              console.info('fetchAllCookies cookie[' + i + '].value = ' + cookies[i].value);
            }
          })
        })

        Web({ src: 'https://www.example.com', controller: this.controller})
      }
    }
  }
}
```

## configCookieSync<sup>11+</sup>

static configCookieSync(url: string, value: string, incognito?: boolean): void

Sets a single cookie value for a specified URL.

> **NOTE**
>
> - The URL in configCookieSync can specify a method for domain to make requests within the page also carry cookies.
>
> - Cookies are periodically saved to disk every 30s. You can also use the [saveCookieAsync](#savecookieasync) API to force the save.
>
> - The value parameter must follow the format of the Set-Cookie HTTP response header. It is a key-value pair in the form of "key=value", which can be followed by a cookie attribute list separated by "; " (for example, "key=value; Max-Age=100").
> 
> - If there is a cookie with the same host, path, and name, it will be replaced by the new cookie. If the set cookie has expired, it will not be stored. If you need to set multiple cookies, you should call this method multiple times.
>
> - If cookies are set twice or multiple times through configCookieSync, the cookies set each time are separated by "; ".
>
> - If the specified value contains the "Secure" attribute, the URL must use the "https://" protocol.
>
> - If you need to overwrite an HttpOnly cookie, you need to specify the HttpOnly attribute in value.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                     |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL of the cookie to set. A complete URL is recommended. |
| value  | string | Yes  | Cookie value to set.     |
| incognito    | boolean | No   | Whether to set the cookies in incognito mode. The value **true** means to set the cookies in incognito mode, and **false** means the opposite.<br>The default value is **false**.<br>If **undefined** or **null** is passed, error code **401** will be thrown.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100002 | URL error. No valid cookie found for the specified URL.  |
| 17100005 | The provided cookie value is invalid. It must follow the format specified in RFC 6265. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('configCookieSync')
        .onClick(() => {
          try {
            // Only one cookie value can be set in configCookieSync at a time.
            webview.WebCookieManager.configCookieSync('https://www.example.com', 'a=b');
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## configCookieSync<sup>14+</sup>

static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void

Sets a single cookie value for a specified URL.

> **NOTE**
>
> - The URL in configCookieSync can specify a method for domain to make requests within the page also carry cookies.
>
> - Cookies are periodically saved to disk every 30s. You can also use the [saveCookieAsync](#savecookieasync) API to force the save.
>
> - The value parameter must follow the format of the Set-Cookie HTTP response header. It is a key-value pair in the form of "key=value", which can be followed by a cookie attribute list separated by "; " (for example, "key=value; Max-Age=100").
> 
> - If there is a cookie with the same host, path, and name, it will be replaced by the new cookie. If the set cookie has expired, it will not be stored. If you need to set multiple cookies, you should call this method multiple times.
>
> - If cookies are set twice or multiple times through configCookieSync, the cookies set each time are separated by "; ".
>
> - If the specified value contains the "Secure" attribute, the URL must use the "https://" protocol.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                     |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL to which the cookie to be set belongs. A complete URL is recommended. |
| value  | string | Yes  | Cookie value to set.     |
| incognito    | boolean | Yes   | true indicates setting the cookie for the corresponding URL in privacy mode, and false indicates setting the cookie for the corresponding URL in normal non-privacy mode. |
| includeHttpOnly    | boolean | Yes   | true indicates allowing overwriting of cookies containing http-only, and false indicates not allowing overwriting of cookies containing http-only. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100002 | URL error. No valid cookie found for the specified URL.  |
| 17100005 | The provided cookie value is invalid. It must follow the format specified in RFC 6265. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('configCookieSync')
        .onClick(() => {
          try {
            // Only a single cookie value can be set.
            webview.WebCookieManager.configCookieSync('https://www.example.com', 'a=b', false, false);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## configCookie<sup>11+</sup>

static configCookie(url: string, value: string, callback: AsyncCallback\<void>): void

Sets a single cookie value for a specified URL. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - The URL in configCookie can specify a method for domain to make requests within the page also carry cookies.
>
> - Cookies are periodically saved to disk every 30s. You can also use the [saveCookieAsync](#savecookieasync) API to force the save.
>
> - The value parameter must follow the format of the Set-Cookie HTTP response header. It is a key-value pair in the form of "key=value", which can be followed by a cookie attribute list separated by "; " (for example, "key=value; Max-Age=100").
> 
> - If there is a cookie with the same host, path, and name, it will be replaced by the new cookie. If the set cookie has expired, it will not be stored. If you need to set multiple cookies, you should call this method multiple times.
>
> - If cookies are set twice or multiple times through configCookie, the cookies set each time are separated by "; ".
>
> - If the specified value contains the "Secure" attribute, the URL must use the "https://" protocol.
>
> - If you need to overwrite an HttpOnly cookie, you need to specify the HttpOnly attribute in value.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                     |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL to which the cookie to be set belongs. Recommended to use the complete URL. |
| value  | string | Yes  | Cookie value to set.     |
| callback | AsyncCallback\<void> | Yes | Callback used to return the result of setting the cookie. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 17100002 | URL error. No valid cookie found for the specified URL.  |
| 17100005 | The provided cookie value is invalid. It must follow the format specified in RFC 6265. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('configCookie')
        .onClick(() => {
          try {
            webview.WebCookieManager.configCookie('https://www.example.com', "a=b", (error) => {
              if (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }
            })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## configCookie<sup>11+</sup>

static configCookie(url: string, value: string): Promise\<void>

Sets a single cookie value for a specified URL. This API uses a promise to return the result.

> **NOTE**
>
> - The URL in configCookie can specify a method for domain to make requests within the page also carry cookies.
>
> - Cookies are periodically saved to disk every 30s. You can also use the [saveCookieAsync](#savecookieasync) API to force the save.
>
> - The value parameter must follow the format of the Set-Cookie HTTP response header. It is a key-value pair in the form of "key=value", which can be followed by a cookie attribute list separated by "; " (for example, "key=value; Max-Age=100").
> 
> - If there is a cookie with the same host, path, and name, it will be replaced by the new cookie. If the set cookie has expired, it will not be stored. If you need to set multiple cookies, you should call this method multiple times.
>
> - If cookies are set twice or multiple times through configCookie, the cookies set each time are separated by "; ".
>
> - If the specified value contains the "Secure" attribute, the URL must use the "https://" protocol.
>
> - If you need to overwrite an HttpOnly cookie, you need to specify the HttpOnly attribute in value.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                     |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL to which the cookie to be set belongs. Recommended to use a complete URL. |
| value  | string | Yes  | Cookie value to set.     |

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| Promise\<void> | Promise instance, used to get whether setting a single cookie value for the specified URL is successful. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 17100002 | URL error. No valid cookie found for the specified URL. |
| 17100005 | The provided cookie value is invalid. It must follow the format specified in RFC 6265. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('configCookie')
        .onClick(() => {
          try {
            webview.WebCookieManager.configCookie('https://www.example.com', 'a=b')
              .then(() => {
                console.info('configCookie success!');
              })
              .catch((error: BusinessError) => {
                console.error('error: ' + JSON.stringify(error));
              })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## configCookie<sup>14+</sup>

static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise\<void>

Sets a single cookie value for a specified URL. This API uses a promise to return the result.

> **NOTE**
>
> - The URL in configCookie can specify a method for domain to make requests within the page also carry cookies.
>
> - Cookies are periodically saved to disk every 30s. You can also use the [saveCookieAsync](#savecookieasync) API to force the save.
>
> - The value parameter must follow the format of the Set-Cookie HTTP response header. It is a key-value pair in the form of "key=value", which can be followed by a cookie attribute list separated by "; " (for example, "key=value; Max-Age=100").
> 
> - If there is a cookie with the same host, path, and name, it will be replaced by the new cookie. If the set cookie has expired, it will not be stored. If you need to set multiple cookies, you should call this method multiple times.
>
> - If cookies are set twice or multiple times through configCookie, the cookies set each time are separated by "; ".
>
> - If the specified value contains the "Secure" attribute, the URL must use the "https://" protocol.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                     |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL to which the cookie to be set belongs. A complete URL is recommended. |
| value  | string | Yes  | Cookie value to set.     |
| incognito    | boolean | Yes   | true indicates setting the cookie for the corresponding URL in privacy mode, and false indicates setting the cookie for the corresponding URL in normal non-privacy mode. |
| includeHttpOnly    | boolean | Yes   | true indicates allowing overwriting of cookies containing http-only, and false indicates not allowing overwriting of cookies containing http-only. |

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| Promise\<void> | Promise instance, used to get whether setting a single cookie value for the specified URL is successful. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 17100002 | URL error. No valid cookie found for the specified URL. |
| 17100005 | The provided cookie value is invalid. It must follow the format specified in RFC 6265. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('configCookie')
        .onClick(() => {
          try {
            webview.WebCookieManager.configCookie('https://www.example.com', 'a=b', false, false)
              .then(() => {
                console.info('configCookie success!');
              })
              .catch((error: BusinessError) => {
                console.error('error: ' + JSON.stringify(error));
              })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## saveCookieSync<sup>15+</sup>

static saveCookieSync(): void

Synchronously saves all cookies (that can be obtained through **fetchCookie** and need to be persisted) to the disk.

> **NOTE**
>
> - saveCookieSync is used to forcibly write cookies that need to be persisted to the disk. Session cookies are not persisted on PC/2-in-1 and tablet devices. Even if saveCookieSync is called, session cookies are not written to the disk.
>
> - saveCookieSync blocks the caller until the operation is complete, during which I/O operations may be performed.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('saveCookieSync')
        .onClick(() => {
          try {
            webview.WebCookieManager.saveCookieSync();
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## saveCookieAsync

static saveCookieAsync(callback: AsyncCallback\<void>): void

Asynchronously saves all cookies (that can be obtained through **fetchCookie** and need to be persisted) to the disk.

> **NOTE**
>
> - saveCookieAsync is used to forcibly write cookies that need to be persisted to the disk. Session cookies are not persisted on PC/2-in-1 and tablet devices. Even if saveCookieAsync is called, session cookies are not written to the disk.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                              |
| -------- | ---------------------- | ---- | :------------------------------------------------- |
| callback | AsyncCallback\<void> | Yes | Callback function, used to get whether the cookies are saved successfully. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('saveCookieAsync')
        .onClick(() => {
          try {
            webview.WebCookieManager.saveCookieAsync((error) => {
              if (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }
            })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## saveCookieAsync

static saveCookieAsync(): Promise\<void>

Saves all cookies (that can be obtained through **fetchCookie** and need to be persisted) to the disk. This API uses a promise to return the result.

> **NOTE**
>
> - saveCookieAsync is used to forcibly write cookies that need to be persisted to the disk. Session cookies are not persisted on PC/2-in-1 and tablet devices. Even if saveCookieAsync is called, session cookies are not written to the disk.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type            | Description                                     |
| ---------------- | ----------------------------------------- |
| Promise\<void> | Promise instance, used to get whether the cookies are saved successfully. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('saveCookieAsync')
        .onClick(() => {
          try {
            webview.WebCookieManager.saveCookieAsync()
              .then(() => {
                console.info("saveCookieAsync success!");
              })
              .catch((error: BusinessError) => {
                console.error("error: " + error);
              });
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## putAcceptCookieEnabled

static putAcceptCookieEnabled(accept: boolean): void

Sets whether the **WebCookieManager** instance has the permission to send and receive cookies.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type   | Mandatory| Description                                |
| ------ | ------- | ---- | :----------------------------------- |
| accept | boolean | Yes | Whether to have the permission to send and receive cookies. The default value is **true**, indicating that the app has the permission to send and receive cookies. The value **false** indicates that the app does not have the permission to send and receive cookies. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('putAcceptCookieEnabled')
        .onClick(() => {
          try {
            webview.WebCookieManager.putAcceptCookieEnabled(false);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## isCookieAllowed

static isCookieAllowed(): boolean

Checks whether the **WebCookieManager** instance has the permission to send and receive cookies.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type   | Description                            |
| ------- | -------------------------------- |
| boolean | Whether the **WebCookieManager** instance has the permission to send and receive cookies.<br>The value **true** indicates that the **WebCookieManager** instance has the permission to send and receive cookies, and **false** indicates the opposite.<br>Default value: **true**. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('isCookieAllowed')
        .onClick(() => {
          let result = webview.WebCookieManager.isCookieAllowed();
          console.info("result: " + result);
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## putAcceptThirdPartyCookieEnabled

static putAcceptThirdPartyCookieEnabled(accept: boolean): void

Sets whether the **WebCookieManager** instance has the permission to send and receive third-party cookies.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type   | Mandatory| Description                                      |
| ------ | ------- | ---- | :----------------------------------------- |
| accept | boolean | Yes | Whether to allow sending and receiving third-party cookies.<br>true indicates allowed, false indicates not allowed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('putAcceptThirdPartyCookieEnabled')
        .onClick(() => {
          try {
            webview.WebCookieManager.putAcceptThirdPartyCookieEnabled(false);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## isThirdPartyCookieAllowed

static isThirdPartyCookieAllowed(): boolean

Checks whether the **WebCookieManager** instance has the permission to send and receive third-party cookies.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type   | Description                                  |
| ------- | -------------------------------------- |
| boolean | Whether the **WebCookieManager** instance has the permission to send and receive third-party cookies.<br>The value **true** indicates that the **WebCookieManager** instance has the permission to send and receive third-party cookies, and **false** indicates the opposite.<br>The default value is **false**. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('isThirdPartyCookieAllowed')
        .onClick(() => {
          let result = webview.WebCookieManager.isThirdPartyCookieAllowed();
          console.info("result: " + result);
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## existCookie

static existCookie(incognito?: boolean): boolean

Checks whether cookies exist.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type   | Mandatory| Description                                      |
| ------ | ------- | ---- | :----------------------------------------- |
| incognito<sup>11+</sup>    | boolean | No  | Whether to check for cookies in incognito mode. The value **true** means to check for cookies in incognito mode, and **false** means the opposite.<br>The default value is **false**.<br>If **undefined** or **null** is passed, **undefined** is returned.|

**Return value**

| Type   | Description                                  |
| ------- | -------------------------------------- |
| boolean | The value **true** means that cookies exist, and **false** means the opposite. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('existCookie')
        .onClick(() => {
          let result = webview.WebCookieManager.existCookie();
          console.info("result: " + result);
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## clearAllCookiesSync<sup>11+</sup>

static clearAllCookiesSync(incognito?: boolean): void

Clears all cookies, including session cookies and persistent cookies. To clear only session cookies, use [clearSessionCookieSync](#clearsessioncookiesync11).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type   | Mandatory| Description                                      |
| ------ | ------- | ---- | :----------------------------------------- |
| incognito    | boolean | No  | Whether to clear all cookies in incognito mode. The value **true** means to clear all cookies in incognito mode, and **false** means the opposite.<br>The default value is **false**.<br>If **undefined** or **null** is passed, cookies are not cleared.|

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('clearAllCookiesSync')
        .onClick(() => {
          webview.WebCookieManager.clearAllCookiesSync();
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## clearAllCookies<sup>11+</sup>

static clearAllCookies(callback: AsyncCallback\<void>): void

Clears all cookies, including session cookies and persistent cookies. This API uses an asynchronous callback to return the result. To clear only session cookies, use [clearSessionCookie](#clearsessioncookie11).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                              |
| -------- | ---------------------- | ---- | :------------------------------------------------- |
| callback | AsyncCallback\<void> | Yes | Callback function, used to get whether all cookies are cleared successfully. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('clearAllCookies')
        .onClick(() => {
          try {
            webview.WebCookieManager.clearAllCookies((error) => {
              if (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }
            })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## clearAllCookies<sup>11+</sup>

static clearAllCookies(): Promise\<void>

Clears all cookies, including session cookies and persistent cookies. This API uses a promise to return the result. To clear only session cookies, use [clearSessionCookie](#clearsessioncookie11-1).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type            | Description                                     |
| ---------------- | ----------------------------------------- |
| Promise\<void> | Promise instance, used to get whether clearing all cookies is successful. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('clearAllCookies')
        .onClick(() => {
          webview.WebCookieManager.clearAllCookies()
            .then(() => {
              console.info("clearAllCookies success!");
            })
            .catch((error: BusinessError) => {
              console.error("error: " + error);
            });
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## clearSessionCookieSync<sup>11+</sup>

static clearSessionCookieSync(): void

Deletes all session cookies.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('clearSessionCookieSync')
        .onClick(() => {
          webview.WebCookieManager.clearSessionCookieSync();
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## clearSessionCookie<sup>11+</sup>

static clearSessionCookie(callback: AsyncCallback\<void>): void

Clears all session cookies. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                              |
| -------- | ---------------------- | ---- | :------------------------------------------------- |
| callback | AsyncCallback\<void> | Yes | Callback function, used to get whether clearing all session cookies is successful. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('clearSessionCookie')
        .onClick(() => {
          try {
            webview.WebCookieManager.clearSessionCookie((error) => {
              if (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }
            })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## clearSessionCookie<sup>11+</sup>

static clearSessionCookie(): Promise\<void>

Clears all session cookies. This API uses a promise to return the result.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type            | Description                                     |
| ---------------- | ----------------------------------------- |
| Promise\<void> | Promise instance, used to get whether clearing all session cookies is successful. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('clearSessionCookie')
        .onClick(() => {
          try {
            webview.WebCookieManager.clearSessionCookie()
              .then(() => {
                console.info("clearSessionCookie success!");
              })
              .catch((error: BusinessError) => {
                console.error("error: " + error);
              });
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## setLazyInitializeWebEngine<sup>22+</sup>

static setLazyInitializeWebEngine(lazy: boolean): void

Sets whether to delay the initialization of the ArkWeb kernel. If this method is not called, the ArkWeb kernel is not delayed by default.

> **NOTE**
>
> - This interface is a global static method and must be called before using the ArkWeb component and initializing the ArkWeb kernel. Otherwise, the setting does not take effect.
> 
> - This interface applies only to interfaces that initialize CookieManager after being called, such as other interfaces of the WebCookieManager class. After calling this interface and setting it to true, when you call an applicable interface, the initialization of the ArkWeb kernel is skipped during CookieManager initialization. You need to initialize the ArkWeb kernel yourself later.
>
> - Since API version 26.0.1, after calling this interface and setting it to true, the WebCookieManager interfaces support being used on non-UI threads.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                    |
| ---- | ------- | -- | ------------------------- |
| lazy | boolean | Yes| Whether to delay the initialization of the ArkWeb kernel. The value **true** means to delay the initialization, and **false** means the opposite.|

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

webview.WebCookieManager.setLazyInitializeWebEngine(true);

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  aboutToAppear(): void {
    webview.WebCookieManager.configCookieSync('https://www.example.com', 'a=b');
    webview.WebCookieManager.fetchCookieSync('https://www.example.com');
  }

  build() {
    Column() {
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## getCookie<sup>(deprecated)</sup>

static getCookie(url: string): string

Obtains the cookies corresponding to the specified URL.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 11. You are advised to use [fetchCookieSync](#fetchcookiesync11) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                     |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL to which the cookies to get belong. A complete URL is recommended. |

**Return value**

| Type  | Description                     |
| ------ | ------------------------- |
| string | The cookies corresponding to the specified URL. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100002 | URL error. No valid cookie found for the specified URL.  |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('getCookie')
        .onClick(() => {
          try {
            let value = webview.WebCookieManager.getCookie('https://www.example.com');
            console.info("value: " + value);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## setCookie<sup>(deprecated)</sup>

static setCookie(url: string, value: string): void

Sets a single cookie value for a specified URL.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 11. You are advised to use [configCookieSync<sup>11+</sup>](#configcookiesync11) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                     |
| ------ | ------ | ---- | :------------------------ |
| url    | string | Yes   | URL to which the cookie to be set belongs. A complete URL is recommended. |
| value  | string | Yes  | Cookie value to set.     |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100002 | URL error. No valid cookie found for the specified URL.  |
| 17100005 | The provided cookie value is invalid. It must follow the format specified in RFC 6265. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('setCookie')
        .onClick(() => {
          try {
            webview.WebCookieManager.setCookie('https://www.example.com', 'a=b');
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## deleteEntireCookie<sup>(deprecated)</sup>

static deleteEntireCookie(): void

Deletes all cookies.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 11. You are advised to use [clearAllCookiesSync](#clearallcookiessync11) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('deleteEntireCookie')
        .onClick(() => {
          webview.WebCookieManager.deleteEntireCookie();
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## deleteSessionCookie<sup>(deprecated)</sup>

static deleteSessionCookie(): void

Deletes all session cookies.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 11. You are advised to use [clearSessionCookieSync](#clearsessioncookiesync11) instead.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('deleteSessionCookie')
        .onClick(() => {
          webview.WebCookieManager.deleteSessionCookie();
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```