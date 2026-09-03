# Class (GeolocationPermissions)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhang-yinglie-->
<!--Designer: @handyohos-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=fb8a23f8059c1122b20bab74c5aca3cfcd08dbd6 translatedAt=2026-08-07T04:57:47.686Z pushedAt=2026-08-07T07:55:06.486Z -->

GeolocationPermissions is the geolocation permission management object for the Web component. It provides management capabilities such as querying, authorizing, and deleting saved geolocation permission statuses in the Web component. With GeolocationPermissions, an app can pre-authorize access for a specific origin before a web page initiates a geolocation request, and can also proactively query or clear saved permission records without relying on the pop-up authorization flow when a web page requests permission.

GeolocationPermissions is suitable for scenarios where proactive management of Web component geolocation permissions is required. For example, an app may want to pre-authorize trusted websites to access geolocation, avoiding authorization prompts on each visit; or an app may need to clear geolocation permission records that are no longer needed by the user. The following permissions are required for accessing geolocation: ohos.permission.LOCATION, ohos.permission.APPROXIMATELY_LOCATION, and ohos.permission.LOCATION_IN_BACKGROUND. For details about the permissions, see [Development Guide for Location Permission Application](../../device/location/location-permission-guidelines.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effect is subject to the actual device.
>
> - You must load the **Web** component before calling the APIs in **GeolocationPermissions**.

## Modules to Import

```ts
import { webview } from '@kit.ArkWeb';
```

## allowGeolocation

static allowGeolocation(origin: string, incognito?: boolean): void

Allows the specified origin to use the geolocation APIs. It is used to pre-authorize geolocation permission for trusted websites to avoid repeated pop-ups, or to allow an app to proactively manage the geolocation authorization of a specific origin.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| origin | string | Yes | String of the specified origin.<br>The origin format must comply with the format defined in RFC 6454. An exception is thrown when a string that does not comply with the RFC 6454 format is input, with error code 17100011. |
| incognito<sup>11+</sup> | boolean | No | The value **true** indicates that the specified origin is allowed to use geolocation in privacy mode, and **false** indicates that the specified origin is allowed to use geolocation in normal (non-privacy) mode.<br>Default value: **false**.<br>The value is **false** when null or undefined is input. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100011 | Invalid origin. The origin format must comply with the format defined in RFC 6454. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  origin: string = 'file:///';

  build() {
    Column() {
      Button('allowGeolocation')
        .onClick(() => {
          try {
            // Allow the specified origin to use the geolocation API.
            webview.GeolocationPermissions.allowGeolocation(this.origin);
          } catch (error) {
            console.error(`Failed to allow geolocation. Code: ${(error as BusinessError).code}, Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## deleteGeolocation

static deleteGeolocation(origin: string, incognito?: boolean): void

Clears the geolocation permission status of the specified origin. It is used to revoke the geolocation authorization of a specified website, or to provide an app with the ability to manage permissions by origin.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| origin | string | Yes | String of the specified origin.<br>The origin format must comply with the format defined in RFC 6454. Throws an exception when a string that does not comply with the RFC 6454 format is input. Error code: 17100011. |
| incognito<sup>11+</sup> | boolean | No | Whether to clear the geolocation permission status of the specified origin in privacy mode. The value **true** indicates clearing in privacy mode, and **false** indicates clearing in normal non-privacy mode.<br>Default value: **false**.<br>The value is **false** when null or undefined is input. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100011 | Invalid origin. The origin format must comply with the format defined in RFC 6454. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  origin: string = 'file:///';

  build() {
    Column() {
      Button('deleteGeolocation')
        .onClick(() => {
          try {
            // ` preserved
</analysis>

<translation>
<seg id="0">Delete the geolocation permission status of the specified origin.
            webview.GeolocationPermissions.deleteGeolocation(this.origin);
          } catch (error) {
            console.error(`Failed to delete geolocation. Code: ${(error as BusinessError).code}, Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## getAccessibleGeolocation

static getAccessibleGeolocation(origin: string, callback: AsyncCallback\<boolean>, incognito?: boolean): void

Obtains the geolocation permission status of the specified origin. This API uses an asynchronous callback to return the result. It is used to query the geolocation authorization result of a specified website, such as displaying the permission status on a settings page or verifying authorization before access.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| origin   | string                 | Yes   | String of the specified origin.<br>The origin format must comply with the format defined in RFC 6454. An exception is thrown when a non-conforming input string is input. Error code: 17100011. |
| callback | AsyncCallback\<boolean> | Yes  | Callback used to return the geolocation permission status of the specified origin.<br>If the operation is successful, the value **true** means that the geolocation permission is granted, and **false** means the opposite.<br>If the operation fails, the geolocation permission status of the specified origin is not found.|
| incognito<sup>11+</sup>    | boolean | No   | The value **true** indicates to get the geolocation permission status of the specified origin in privacy mode, and **false** indicates to get it in normal mode.<br>Default value: **false**.<br>Throws an exception error with error code 401 when null or undefined is input. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100011 | Invalid origin. The origin format must follow the format defined in RFC 6454. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  origin: string = 'file:///';

  build() {
    Column() {
      Button('getAccessibleGeolocation')
        .onClick(() => {
          try {
            // Obtain the geolocation permission status of the specified origin asynchronously using a callback.
            webview.GeolocationPermissions.getAccessibleGeolocation(this.origin, (error, result) => {
              if (error) {
                console.error(`Failed to get accessible geolocation. Code: ${(error as BusinessError).code}, Message: ${(error as BusinessError).message}`);
                return;
              }
              console.info('getAccessibleGeolocationAsync result: ' + result);
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

## getAccessibleGeolocation

static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise\<boolean>

Obtains the geolocation permission status of the specified origin. This API uses a promise to return the result. It is used to query the geolocation authorization result of a specified website, such as displaying the permission status on a settings page or verifying authorization before access.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description            |
| ------ | -------- | ---- | -------------------- |
| origin | string | Yes | String of the specified origin.<br>The origin format must comply with the format defined in RFC 6454. An exception is thrown when a string that does not comply with the RFC 6454 format is input, with error code 17100011. |
| incognito<sup>11+</sup> | boolean | No | Whether to obtain the geolocation permission status of the specified origin in privacy mode. The value **true** indicates obtaining in privacy mode, and **false** indicates obtaining in normal mode.<br>Default value: **false**.<br>An exception with error code 401 is thrown when null or undefined is input. |

**Return value**

| Type            | Description                                                        |
| ---------------- | ------------------------------------------------------------ |
| Promise\<boolean> | Promise used to return the geolocation permission status of the specified origin.<br>If the operation is successful, the value **true** means that the geolocation permission is granted, and **false** means the opposite.<br>If the operation fails, the geolocation permission status of the specified origin is not found.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100011 | Invalid origin. The origin format must comply with the format defined in RFC 6454. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  origin: string = 'file:///';

  build() {
    Column() {
      Button('getAccessibleGeolocation')
        .onClick(() => {
          try {
            // Obtain the geolocation permission status of the specified origin asynchronously. This API uses a promise to return the result.
            webview.GeolocationPermissions.getAccessibleGeolocation(this.origin)
              .then(result => {
                console.info('getAccessibleGeolocationPromise result: ' + result);
              }).catch((error: BusinessError) => {
                console.error(`Failed to get accessible geolocation. Code: ${error.code}, Message: ${error.message}`);
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

## getStoredGeolocation

static getStoredGeolocation(callback: AsyncCallback\<Array\<string>>, incognito?: boolean): void

Obtains the geolocation permission status of all origins. This API uses an asynchronous callback to return the result. It is used to obtain a list of websites that have been granted geolocation permission, such as displaying on a privacy settings page or batch management on a permission management page.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                        | Mandatory| Description                                    |
| -------- | ---------------------------- | ---- | ---------------------------------------- |
| callback | AsyncCallback\<Array\<string>> | Yes | Callback invoked to return all origin information of stored geolocation permission statuses. The callback parameters include: error (error object, which is null when retrieval is successful) and origins (array of origin strings with stored geolocation permissions, where each element is an origin string that complies with the format defined in RFC 6454). When retrieval fails, error is the error object. |
| incognito<sup>11+</sup> | boolean | No | Whether to obtain all origin information of stored geolocation permission statuses in privacy mode. The value **true** indicates privacy mode, and **false** indicates normal mode.<br>Default value: **false**.<br>Throws an exception error code 401 when null or undefined is passed in. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
      Button('getStoredGeolocation')
        .onClick(() => {
          try {
            // Obtain all origin information of stored geolocation permission statuses asynchronously using a callback.
            webview.GeolocationPermissions.getStoredGeolocation((error, origins) => {
              if (error) {
                console.error(`Failed to get stored geolocation. Code: ${(error as BusinessError).code}, Message: ${(error as BusinessError).message}`);
                return;
              }
              let originsStr: string = origins.join();
              console.info('getStoredGeolocationAsync origins: ' + originsStr);
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

## getStoredGeolocation

static getStoredGeolocation(incognito?: boolean): Promise\<Array\<string>>

Obtains the geolocation permission status of all origins. This API uses a promise to return the result. It is used to obtain a list of websites that have been granted geolocation permission, such as displaying on a privacy settings page or batch management on a permission management page.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                        | Mandatory| Description                                    |
| -------- | ---------------------------- | ---- | ---------------------------------------- |
| incognito<sup>11+</sup>   | boolean | No   | The value **true** indicates that all origin information of stored geolocation permission status is obtained in private mode, and **false** indicates that it is obtained in normal mode.<br>Default value: **false**.<br>Throws an exception error code 401 when null or undefined is passed in. |

**Return value**

| Type                  | Description                                                     |
| ---------------------- | --------------------------------------------------------- |
| Promise\<Array\<string>> | Promise used to return the geolocation permission status of all origins.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
      Button('getStoredGeolocation')
        .onClick(() => {
          try {
            // Asynchronously obtain all origin information of stored geolocation permission statuses using a promise.
            webview.GeolocationPermissions.getStoredGeolocation()
              .then(origins => {
                let originsStr: string = origins.join();
                console.info('getStoredGeolocationPromise origins: ' + originsStr);
              }).catch((error: BusinessError) => {
                console.error(`Failed to get stored geolocation. Code: ${error.code}, Message: ${error.message}`);
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

## deleteAllGeolocation

static deleteAllGeolocation(incognito?: boolean): void

Clears the geolocation permission status of all origins. It is used to revoke geolocation authorization in batches in scenarios such as user logout or one-click clearing.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                        | Mandatory| Description                                    |
| -------- | ---------------------------- | ---- | ---------------------------------------- |
| incognito<sup>11+</sup>    | boolean | No   | The value **true** indicates clearing the geolocation permission status of all origins in Privacy Mode, and **false** indicates clearing the geolocation permission status of all origins in Normal Mode.<br>Default value: **false**.<br>The value **false** is used when null or undefined is input. |

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
      Button('deleteAllGeolocation')
        .onClick(() => {
          try {
            // Clear the geolocation permission status of all origins.
            webview.GeolocationPermissions.deleteAllGeolocation();
          } catch (error) {
            console.error(`Failed to delete all geolocation. Code: ${(error as BusinessError).code}, Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```