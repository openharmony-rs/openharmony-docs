# Class (WebDataBase)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @yuzhouhang1-->
<!--Designer: @handyohos-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=cb3bcbeb60045c709f23a1022353e0111d4ac4f4 translatedAt=2026-08-07T04:36:49.828Z pushedAt=2026-08-07T08:11:31.512Z -->

Implements a **WebDataBase** object.

## Overview

WebDataBase is a database management class provided by the Web component, used to manage HTTP authentication credentials in the Web component, including saving, querying, checking, and deleting credentials. It is suitable for scenarios where automatic management of HTTP authentication credentials for web apps is required, helping to solve the problem of users frequently entering usernames and passwords, improving user experience and reducing repetitive operations.

### Basic Concepts

- **HTTP authentication credentials**: Authentication information containing a username and password, used to access protected HTTP resources.

- **Host and realm**: The target host and realm to which the credentials apply.

- **Synchronous method**: All methods provided by WebDataBase are synchronous methods, which return results immediately upon invocation.

### Key Design

WebDataBase adopts a static class design:

1. Provides static methods for managing HTTP authentication credentials.

2. Supports saving, querying, and deleting credentials.

3. All methods require a Web component to be loaded before use.

### Main Methods

| Method Name | Description |
|--------|------|
| [getHttpAuthCredentials](#gethttpauthcredentials) | Retrieves HTTP authentication credentials for a given host and realm. Used to obtain saved credential information when re-login or user identity verification is required, for example, automatically filling in login forms after an app restarts, or accessing protected web pages that require authentication. |
| [saveHttpAuthCredentials](#savehttpauthcredentials) | Saves HTTP authentication credentials for a given host and realm. Used to save credentials after a user successfully logs in for the first time, so that the next time the same website is accessed, automatic login can be performed or authentication information does not need to be re-entered, improving user experience. |
| [existHttpAuthCredentials](#existhttpauthcredentials) | Checks whether any saved HTTP authentication credentials exist. Used to check whether credentials have been saved when an app starts up to decide whether to display the login page, or to determine whether re-authentication is required before a user accesses protected resources. |
| [deleteHttpAuthCredentials](#deletehttpauthcredentials) | Clears all saved HTTP authentication credentials. Used to delete all credential information when a user logs out, switches accounts, or clears app data, protecting user privacy and account security. |

### Example

```ts
import { webview } from '@kit.ArkWeb';

// Save HTTP authentication credentials.
webview.WebDataBase.saveHttpAuthCredentials('www.example.com', 'protected', 'username', 'password');

// Retrieve credentials.
let credentials = webview.WebDataBase.getHttpAuthCredentials('www.example.com', 'protected');

// Check whether credentials exist.
let exists = webview.WebDataBase.existHttpAuthCredentials();

// Delete all credentials.
webview.WebDataBase.deleteHttpAuthCredentials();
```

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effect is subject to the actual device.
>
> - You must load the **Web** component before calling the APIs in **WebDataBase**.

## Modules to Import

```ts
import { webview } from '@kit.ArkWeb';
```

## getHttpAuthCredentials

static getHttpAuthCredentials(host: string, realm: string): Array\<string>

Retrieves HTTP authentication credentials for a given host and realm. This API returns the result synchronously.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                        |
| ------ | ------ | ---- | ---------------------------- |
| host | string | Yes | Host address of the HTTP authentication credential app, in the format of 'www.example.com' or '192.168.1.1', excluding the protocol and port number. |
| realm | string | Yes | Authentication realm of the HTTP authentication credential app, which indicates the scope or protection area for authentication under the same host. It is usually specified by the WWW-Authenticate header returned by the server. |

**Return value**

| Type | Description                                        |
| ----- | -------------------------------------------- |
| Array\<string> | Array of the matching user names and passwords is returned if the operation is successful; otherwise, an empty array is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                               |
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
  host: string = 'www.spincast.org';
  realm: string = 'protected example';
  usernamePassword: string[] = [];

  build() {
    Column() {
      Button('getHttpAuthCredentials')
        .onClick(() => {
          try {
            this.usernamePassword = webview.WebDataBase.getHttpAuthCredentials(this.host, this.realm);
            console.info('num: ' + this.usernamePassword.length);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## saveHttpAuthCredentials

static saveHttpAuthCredentials(host: string, realm: string, username: string, password: string): void

Saves HTTP authentication credentials for a given host and realm. This API returns the result synchronously.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type  | Mandatory| Description                        |
| -------- | ------ | ---- | ---------------------------- |
| host     | string | Yes  | Host of the HTTP authentication credential. Used to match the host corresponding to the credential. |
| realm    | string | Yes  | Realm of the HTTP authentication credential. Used to match the authentication realm corresponding to the credential. |
| username | string | Yes  | Username for HTTP authentication, which serves as the identity for accessing protected resources. |
| password | string | Yes  | Password for HTTP authentication. Used with the username to complete authentication. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                                               |
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
  host: string = 'www.spincast.org';
  realm: string = 'protected example';

  build() {
    Column() {
      Button('saveHttpAuthCredentials')
        .onClick(() => {
          try {
            webview.WebDataBase.saveHttpAuthCredentials(this.host, this.realm, 'Stromgol', 'Laroche');
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## existHttpAuthCredentials

static existHttpAuthCredentials(): boolean

Checks whether any saved HTTP authentication credentials exist. This API returns the result synchronously.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Whether any saved HTTP authentication credentials exist.<br>**true** is returned if any saved HTTP authentication credentials exist; otherwise, **false** is returned.|

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
      Button('existHttpAuthCredentials')
        .onClick(() => {
          try {
            if (webview.WebDataBase.existHttpAuthCredentials()) {
                console.info('HTTP auth credentials exist.');
              } else {
                console.info('No HTTP auth credentials found.');
              }
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## deleteHttpAuthCredentials

static deleteHttpAuthCredentials(): void

Deletes all HTTP authentication credentials saved in the cache. This API returns the result synchronously.

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
      Button('deleteHttpAuthCredentials')
        .onClick(() => {
          try {
            webview.WebDataBase.deleteHttpAuthCredentials();
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```