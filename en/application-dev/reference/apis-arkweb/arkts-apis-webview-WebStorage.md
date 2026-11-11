# Class (WebStorage)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @yuzhouhang1-->
<!--Designer: @handyohos-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=bc20c4f6d6ff5465b72098b36f6b50a02fe75bae translatedAt=2026-11-06T11:08:00.792Z pushedAt=2026-11-10T02:27:25.605Z nl=1 -->

Implements a **WebStorage** object to manage the Web SQL database and HTML5 Web Storage APIs. All **Web** components in an application share a **WebStorage** object.

## Overview

WebStorage provides the capability to manage Web storage data, including Web SQL databases and the HTML5 Web storage API. It mainly addresses the following issues:
- Cross-Web-component data storage management.
- Querying storage space quota and usage.
- Clearing storage data.

### Basic Concepts

- **Origin**: The data isolation unit of Web storage. Pages under the same origin can share storage data.
- **Quota**: The maximum storage space allowed for each origin, in bytes.
- **Usage**: The storage space currently used by each origin, in bytes.

### Key Design

WebStorage adopts a unified management design pattern:
1. All Web components in each application share one WebStorage instance.
2. The origin is used as the index to distinguish and manage storage data of different origins.
3. Supports both synchronous and asynchronous access to storage data.
4. Supports separate data management in privacy mode and non-privacy mode.

### Usage Examples

````ts
import { webview } from '@kit.ArkWeb';

// Obtain the information about all origins.
webview.WebStorage.getOrigins((error, origins) => {
  if (!error) {
    origins.forEach(origin => {
      console.info(`Origin: ${origin.origin}, Usage: ${origin.usage}, Quota: ${origin.quota}`);
    });
  }
});

// Clear the storage of the specified origin.
webview.WebStorage.deleteOrigin('https://example.com');
````

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effect is subject to the actual device.
>
> - You must load the **Web** component before calling the APIs in **WebStorage**.
>
> - After the ArkWeb kernel is upgraded to M132, the Web SQL database management becomes invalid because the kernel discards Web SQL. For details about the ArkWeb kernel version, see [Constraints](../../web/web-component-overview.md#constraints).

## Modules to Import

```ts
import { webview } from '@kit.ArkWeb';
```

## deleteOrigin

static deleteOrigin(origin: string): void

Deletes all data in the specified origin.

**Method call relationship:**
- The origin parameter should be obtained from the getOrigins() method.
- It is recommended to call getOrigins() to obtain the origin list first, and then call deleteOrigin() to clear the storage of the specified origin.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description                    |
| ------ | ------ | ---- | ------------------------ |
| origin | string | Yes  | Index of the origin, which is obtained through [getOrigins](#getorigins).|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100011 | Invalid origin.                             |
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
  origin: string = "resource://rawfile/";

  build() {
    Column() {
      Button('deleteOrigin')
        .onClick(() => {
          try {
            webview.WebStorage.deleteOrigin(this.origin);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }

        })
      Web({ src: $rawfile('index.html'), controller: this.controller })
    }
  }
}
```

HTML file to be loaded:
 ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
  <head>
    <meta charset="UTF-8">
    <title>test</title>
    <script type="text/javascript">

        // Open or create a database.
        var request = indexedDB.open('myDatabase', 1);

        // Triggered when the database version changes or the database is created for the first time.
        request.onupgradeneeded = function(event) {
            var db = event.target.result;

            // Create an object store (table) and set the primary key to id.
            var objectStore = db.createObjectStore('customers', { keyPath: 'id' });

            // Create an index for name.
            objectStore.createIndex('name', 'name', { unique: false });
        };

        // Called when the database is successfully opened.
        request.onsuccess = function(event) {
            var db = event.target.result;

            const customerData = [
                {id: 1, name: 'John Doe', email: 'john@example.com'},
                {id: 2, name: 'John Doe', email: 'john@example.com'},
            ]

            // Insert data.
            var transaction = db.transaction('customers', 'readwrite');
            var objectStore = transaction.objectStore('customers');

            customerData.forEach((customer) => {
                objectStore.add(customer);
            });

            transaction.oncomplete = function () {
                console.info('Transaction completed: data added');
            }
            
            transaction.onerror = function (event) {
                console.error("Transaction failed", event);
            }
            
            // Query data.
            var queryTransaction = db.transaction(['customers']);
            var queryObjectStore = queryTransaction.objectStore('customers');
            var query = queryObjectStore.get(2);
            
            query.onsuccess = function (event) {
                console.info('query succ');
                console.info('Customer:', event.target.result);
                console.info('Customer id:', event.target.result.id);
                console.info('Customer name:', event.target.result.name);
                console.info('Customer email:', event.target.result.email);
            };
            
            queryObjectStore.openCursor().onsuccess = (event) => {
                const cursor = event.target.result;
                if (cursor) {
                    var msg = "<p>Query record: " + cursor.key + "</p>";
                    document.querySelector("#status").innerHTML += msg;
                    var msg = "<p><b>" + cursor.value.name + "</b></p>";
                    document.querySelector("#status").innerHTML += msg;
                    console.info(`SSN ${cursor.key} corresponds to ${cursor.value.name}`);
                    cursor.continue();
                } else {
                    console.info("No more records")
                }
            }
        };

        // Error handling.
        request.onerror = function(event) {
            console.error('Database error:', event.target.error);
        };

      </script>
  </head>
  <body>
  <div id="status" name="status">Status</div>
  </body>
  </html>
 ```

## getOrigins

static getOrigins(callback: AsyncCallback\<Array\<WebStorageOrigin>>): void

Obtains information about origins that are currently using the Web SQL Database and HTML5-supported Web Storage APIs. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                  |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------ |
| callback | AsyncCallback\<Array\<[WebStorageOrigin](./arkts-apis-webview-i.md#webstorageorigin)>> | Yes  | Callback used to return the information about the origins.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100012 | Invalid web storage origin.                             |
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
      Button('getOrigins')
        .onClick(() => {
          try {
            webview.WebStorage.getOrigins((error, origins) => {
              if (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
                return;
              }
              for (let i = 0; i < origins.length; i++) {
                console.info('origin: ' + origins[i].origin);
                console.info('usage: ' + origins[i].usage);
                console.info('quota: ' + origins[i].quota);
              }
            })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }

        })
      Web({ src: $rawfile('index.html'), controller: this.controller })
    }
  }
}
```

For details about the HTML file loaded, see the HTML file loaded using the [deleteOrigin](#deleteorigin) API.

## getOrigins

static getOrigins(): Promise\<Array\<WebStorageOrigin>>

Obtains information about origins that are currently using the Web SQL Database and HTML5-supported Web Storage APIs. This API uses a promise to return the result.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type                            | Description                                                        |
| -------------------------------- | ------------------------------------------------------------ |
| Promise\<Array\<[WebStorageOrigin](./arkts-apis-webview-i.md#webstorageorigin)>> | Target Promise used to return the information about the origins.|

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100012 | Invalid web storage origin.                             |
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
      Button('getOrigins')
        .onClick(() => {
          try {
            webview.WebStorage.getOrigins()
              .then(origins => {
                for (let i = 0; i < origins.length; i++) {
                  console.info('origin: ' + origins[i].origin);
                  console.info('usage: ' + origins[i].usage);
                  console.info('quota: ' + origins[i].quota);
                }
              })
              .catch((e: BusinessError) => {
                console.error('error: ' + JSON.stringify(e));
              })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }

        })
      Web({ src: $rawfile('index.html'), controller: this.controller })
    }
  }
}
```

For details about the HTML file loaded, see the HTML file loaded using the [deleteOrigin](#deleteorigin) API.

## getOriginQuota

static getOriginQuota(origin: string, callback: AsyncCallback\<number>): void

Obtains the storage quota of an origin in Web SQL Database and HTML5-supported Web Storage APIs, in bytes. This API uses an asynchronous callback to return the result.

**Method call relationship:**
- The origin parameter should be obtained from the getOrigins() method.
- It is recommended to call getOrigins() to obtain the origin list first, and then call getOriginQuota() to obtain the quota of the specified origin.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                 | Mandatory| Description              |
| -------- | --------------------- | ---- | ------------------ |
| origin   | string                | Yes  | Index of the origin.|
| callback | AsyncCallback\<number> | Yes | Storage quota of the specified origin.<br>number is a long integer in the range [-2147483648, 2147483647].<br>Unit: byte. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100011 | Invalid origin.                             |
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
  origin: string = "resource://rawfile/";

  build() {
    Column() {
      Button('getOriginQuota')
        .onClick(() => {
          try {
            webview.WebStorage.getOriginQuota(this.origin, (error, quota) => {
              if (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
                return;
              }
              console.info('quota: ' + quota);
            })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }

        })
      Web({ src: $rawfile('index.html'), controller: this.controller })
    }
  }
}
```

For details about the HTML file loaded, see the HTML file loaded using the [deleteOrigin](#deleteorigin) API.

## getOriginQuota

static getOriginQuota(origin: string): Promise\<number>

Obtains the storage quota of an origin in the Web SQL Database and HTML5-supported Web Storage APIs, in bytes. This API uses a promise to return the result.

**Method call relationship:**
- The origin parameter should be obtained from the getOrigins() method.
- It is recommended to call getOrigins() to obtain the origin list first, and then call getOriginQuota() to obtain the quota of a specified origin.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| origin | string | Yes  | Index of the origin.|

**Return value**

| Type           | Description                                   |
| --------------- | --------------------------------------- |
| Promise\<number> | Promise instance, used to obtain the storage quota of a specified origin.<br>Unit: byte. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100011 | Invalid origin.                             |
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
  origin: string = "resource://rawfile/";

  build() {
    Column() {
      Button('getOriginQuota')
        .onClick(() => {
          try {
            webview.WebStorage.getOriginQuota(this.origin)
              .then(quota => {
                console.info('quota: ' + quota);
              })
              .catch((e: BusinessError) => {
                console.error('error: ' + JSON.stringify(e));
              })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }

        })
      Web({ src: $rawfile('index.html'), controller: this.controller })
    }
  }
}
```

For details about the HTML file loaded, see the HTML file loaded using the [deleteOrigin](#deleteorigin) API.

## getOriginUsage

static getOriginUsage(origin: string, callback: AsyncCallback\<number>): void

Obtains the storage usage of an origin in the Web SQL Database and HTML5-supported Web Storage APIs, in bytes. This API uses an asynchronous callback to return the result.

**Method call relationship:**
- The origin parameter should be obtained from the getOrigins() method.
- It is recommended to call getOrigins() to obtain the origin list first, and then call getOriginUsage() to obtain the usage of the specified origin.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                 | Mandatory| Description              |
| -------- | --------------------- | ---- | ------------------ |
| origin   | string                | Yes  | Index of the origin.|
| callback | AsyncCallback\<number> | Yes | Storage usage of the specified origin.<br>Unit: byte. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 17100011 | Invalid origin.                             |
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
  origin: string = "resource://rawfile/";

  build() {
    Column() {
      Button('getOriginUsage')
        .onClick(() => {
          try {
            webview.WebStorage.getOriginUsage(this.origin, (error, usage) => {
              if (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
                return;
              }
              console.info('usage: ' + usage);
            })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }

        })
      Web({ src: $rawfile('index.html'), controller: this.controller })
    }
  }
}
```

For details about the HTML file loaded, see the HTML file loaded using the [deleteOrigin](#deleteorigin) API.

## getOriginUsage

static getOriginUsage(origin: string): Promise\<number>

Obtains the storage usage of an origin in the Web SQL Database and HTML5-supported Web Storage APIs, in bytes. This API uses a promise to return the result.

**Method call relationship:**
- The origin parameter should be obtained from the getOrigins() method.
- It is recommended to call getOrigins() first to obtain the origin list, and then call getOriginUsage() to obtain the usage of a specified origin.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| origin | string | Yes  | Index of the origin.|

**Return value**

| Type           | Description                                 |
| --------------- | ------------------------------------- |
| Promise\<number> | Promise instance, used to obtain the storage usage of a specified origin.<br>Unit: byte. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                             |
| -------- | ----------------------------------------------------- |
| 17100011 | Invalid origin.                            |
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
  origin: string = "resource://rawfile/";

  build() {
    Column() {
      Button('getOriginUsage')
        .onClick(() => {
          try {
            webview.WebStorage.getOriginUsage(this.origin)
              .then(usage => {
                console.info('usage: ' + usage);
              }).catch((e: BusinessError) => {
              console.error('error: ' + JSON.stringify(e));
            })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: $rawfile('index.html'), controller: this.controller })
    }
  }
}
```

For details about the HTML file loaded, see the HTML file loaded using the [deleteOrigin](#deleteorigin) API.

## deleteAllData

static deleteAllData(incognito?: boolean): void

Deletes all storage data used by JavaScript storage APIs, including the Web SQL Database and HTML5-supported Web storage APIs.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| incognito<sup>11+</sup>    | boolean | No   | true indicates deleting all web data in memory in incognito mode, and false indicates deleting all storage data used by the JavaScript storage API in normal non-incognito mode, including Web SQL databases and the Web storage API supported by HTML5.<br>Default value: false.<br>When undefined or null is passed in, the value is false. |

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
      Button('deleteAllData')
        .onClick(() => {
          try {
            webview.WebStorage.deleteAllData();
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: $rawfile('index.html'), controller: this.controller })
    }
  }
}
```

For details about the HTML file loaded, see the HTML file loaded using the [deleteOrigin](#deleteorigin) API.