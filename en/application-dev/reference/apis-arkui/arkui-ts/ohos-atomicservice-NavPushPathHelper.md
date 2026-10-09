# NavPushPathHelper

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @qq_36417014-->
<!--Designer: @autojuan-->
<!--Tester: @tinygreyy-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=4d3d2622ff7938ed6b9ee65665ad687e9a2cc6eb translatedAt=2026-08-28T01:37:14.622Z pushedAt=2026-08-28T07:50:19.280Z -->

When the target [NavDestination](ts-basic-components-navdestination.md) resides in a different hsp subpackage that is not depended on by the main package, the initial launch of the atomic service only downloads and installs the main package. In this case, you need to use **NavPushPathHelper** to first download and install the corresponding hsp subpackage, and then push the page information of the specified [NavDestination](ts-basic-components-navdestination.md) onto the stack or replace the current top-of-stack page, so that [Navigation](ts-basic-components-navigation.md) supports dynamically loading the hsp subpackage before navigation.

> **NOTE**
>
> This component is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { NavPushPathHelper } from '@kit.ArkUI';
```

## Child Components

Not supported

## Attributes

The [universal attributes](ts-component-general-attributes.md) are not supported.

## Events

The [universal events](ts-component-general-events.md) are not supported.

## NavPushPathHelper

Encapsulates all the routing APIs of the [NavPathStack](ts-basic-components-navigation.md#navpathstack10) of the Navigation route stack. **NavPushPathHelper** holds a **NavPathStack** object. In the encapsulated routing APIs, it checks whether the subpackage exists. If not, it dynamically downloads the subpackage. After the download is complete, it calls the corresponding API of **NavPathStack** to push the page information of the specified [NavDestination](ts-basic-components-navdestination.md) onto the stack or replace the current top-of-stack page. For details about how to use it, see [Example](#example).

### constructor

constructor(navPathStack: NavPathStack)

A constructor used to create a **NavPushPathHelper** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                           | Mandatory  |  Description        |
| ---- | ----------------------------- | ---- | -------------------- |
| navPathStack | [NavPathStack](ts-basic-components-navigation.md#navpathstack10) | Yes   | [Navigation](ts-basic-components-navigation.md) stack.|

### pushPath

pushPath(moduleName: string, info: NavPathInfo, animated?: boolean): Promise\<void\>

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the [NavDestination](ts-basic-components-navdestination.md) page specified by the **info** parameter onto the navigation stack. This API uses a promise to handle asynchronous operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                           | Mandatory  | Description                |
| ---- | ----------------------------- | ---- | -------------------- |
| moduleName | string | Yes   | Module name of the package where the [NavDestination](ts-basic-components-navdestination.md) page is located.|
| info | [NavPathInfo](ts-basic-components-navigation.md#navpathinfo10) | Yes   | Information about the [NavDestination](ts-basic-components-navdestination.md) page.|
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br>**true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Router Error Codes](../errorcode-router.md).

| ID  | Error Message|
| --------- | ------- |
| 300001    | hsp silent install fail.|

### pushPath

pushPath(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise\<void\>

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the [NavDestination](ts-basic-components-navdestination.md) page specified by the **info** parameter onto the navigation stack. This API uses a promise to handle asynchronous operations.

Depending on the [LaunchMode](ts-basic-components-navigation.md#launchmode12) specified in **options**, different navigation behaviors are triggered.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                           | Mandatory  | Description|
| ---- | ----------------------------- | ---- |----|
| moduleName | string | Yes   | Module name of the package where the [NavDestination](ts-basic-components-navdestination.md) page is located.|
| info | [NavPathInfo](ts-basic-components-navigation.md#navpathinfo10) | Yes   | Information about the [NavDestination](ts-basic-components-navdestination.md) page.|
| options | [NavigationOptions](ts-basic-components-navigation.md#navigationoptions12) | No   | Navigation options. The default value is **{ launchMode: LaunchMode.STANDARD, animated: true }**.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Router Error Codes](../errorcode-router.md).

| ID  | Error Message|
| --------- | ------- |
| 300001    | hsp silent install fail.|

### pushPathByName

pushPathByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise\<void\>

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the [NavDestination](ts-basic-components-navdestination.md) page specified by the **name** parameter onto the navigation stack, along with the data specified by **param**. This API uses a promise to handle asynchronous operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type     | Mandatory  | Description                   |
| ----- | ------- | ---- | --------------------- |
| moduleName | string | Yes   | Module name of the package where the [NavDestination](ts-basic-components-navdestination.md) page is located.|
| name  | string  | Yes   | Name of the [NavDestination](ts-basic-components-navdestination.md) page.  |
| param | Object | Yes   | Settings of the [NavDestination](ts-basic-components-navdestination.md) page.|
| animated | boolean | No    | Whether to support the transition animation.<br>Default value: **true**.<br>**true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Router Error Codes](../errorcode-router.md).

| ID  | Error Message|
| --------- | ------- |
| 300001    | hsp silent install fail.|

### pushPathByName

pushPathByName(moduleName: string, name: string, param: Object, onPop: Callback\<PopInfo>, animated?: boolean): Promise\<void\>

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the [NavDestination](ts-basic-components-navdestination.md) page specified by the **name** parameter onto the navigation stack, along with the data specified by **param**. The **onPop** callback handles the return results when the page is popped from the stack. This API uses a promise to handle asynchronous operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
|------|------|------|------|
| moduleName | string | Yes   | Module name of the package where the [NavDestination](ts-basic-components-navdestination.md) page is located.|
| name  | string  | Yes   | Name of the [NavDestination](ts-basic-components-navdestination.md) page.  |
| param | Object | Yes   | Settings of the [NavDestination](ts-basic-components-navdestination.md) page.|
| onPop | Callback\<[PopInfo](ts-basic-components-navigation.md#popinfo11)> | Yes | Callback invoked when the page is popped to process the return result. |
| animated | boolean | No    | Whether to support the transition animation.<br>Default value: **true**.<br>**true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Router Error Codes](../errorcode-router.md).

| ID  | Error Message|
| --------- | ------- |
| 300001    | hsp silent install fail.|

### pushDestination

pushDestination(moduleName: string, info: NavPathInfo, animated?: boolean): Promise\<void\>

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the [NavDestination](ts-basic-components-navdestination.md) page specified by the **info** parameter onto the navigation stack. This API uses a promise to handle asynchronous operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                           | Mandatory  | Description                  |
| ---- | ----------------------------- | ---- | -------------------- |
| moduleName | string | Yes   | Module name of the package where the [NavDestination](ts-basic-components-navdestination.md) page is located.|
| info | [NavPathInfo](ts-basic-components-navigation.md#navpathinfo10) | Yes   | Information about the [NavDestination](ts-basic-components-navdestination.md) page.|
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br>**true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md), [Router Error Codes](../errorcode-router.md), and [API Call Error Codes](../errorcode-internal.md).

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed.   |
| 100001    | Internal error.|
| 100005    | Builder function not registered. |
| 100006    | NavDestination not found.|
| 300001    | hsp silent install fail.|

### pushDestination

pushDestination(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise\<void\>

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the [NavDestination](ts-basic-components-navdestination.md) page specified by the **info** parameter onto the navigation stack. This API uses a promise to handle asynchronous operations.

Depending on the [LaunchMode](ts-basic-components-navigation.md#launchmode12) specified in the **options** parameter, different behaviors will be triggered.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                           | Mandatory  | Description|
| ---- | ----------------------------- | ---- |----|
| moduleName | string | Yes   | Module name of the package where the [NavDestination](ts-basic-components-navdestination.md) page is located.|
| info | [NavPathInfo](ts-basic-components-navigation.md#navpathinfo10) | Yes   | Information about the [NavDestination](ts-basic-components-navdestination.md) page.|
| options | [NavigationOptions](ts-basic-components-navigation.md#navigationoptions12) | No   | Navigation options. The default value is **{ launchMode: LaunchMode.STANDARD, animated: true }**.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md), [Router Error Codes](../errorcode-router.md), and [API Call Error Codes](../errorcode-internal.md).

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed.   |
| 100001    | Internal error.|
| 100005    | Builder function not registered. |
| 100006    | NavDestination not found.|
| 300001    | hsp silent install fail.|

### pushDestinationByName

pushDestinationByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise\<void\>

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the [NavDestination](ts-basic-components-navdestination.md) page specified by the **name** parameter onto the navigation stack, along with the data specified by **param**. This API uses a promise to handle asynchronous operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type     | Mandatory  | Description                   |
| ----- | ------- | ---- | --------------------- |
| moduleName | string | Yes   | Module name of the package where the [NavDestination](ts-basic-components-navdestination.md) page is located.|
| name  | string  | Yes   | Name of the [NavDestination](ts-basic-components-navdestination.md) page.  |
| param | Object | Yes   | Settings of the [NavDestination](ts-basic-components-navdestination.md) page.|
| animated | boolean | No    | Whether to support the transition animation.<br>Default value: **true**.<br>**true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md), [Router Error Codes](../errorcode-router.md), and [API Call Error Codes](../errorcode-internal.md).

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed.  |
| 100001    | Internal error.|
| 100005    | Builder function not registered. |
| 100006    | NavDestination not found.|
| 300001    | hsp silent install fail.|

### pushDestinationByName

pushDestinationByName(moduleName: string, name: string, param: Object, onPop: Callback\<PopInfo>, animated?: boolean): Promise\<void\>

First checks whether the subpackage exists. If not, downloads the subpackage through **moduleName**, and then pushes the page information of the [NavDestination](ts-basic-components-navdestination.md) specified by **name** onto the stack, with **param** as the data to pass and an **onPop** callback added to process the return result when the page is popped. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type     | Mandatory  | Description                 |
| ----- | ------- | ---- | --------------------- |
| moduleName | string | Yes   | Module name of the package where the [NavDestination](ts-basic-components-navdestination.md) page is located.|
| name  | string  | Yes   | Name of the [NavDestination](ts-basic-components-navdestination.md) page.  |
| param | Object | Yes | Parameter object of the [NavDestination](ts-basic-components-navdestination.md) page, used to pass data to the target page. |
| onPop | Callback\<[PopInfo](ts-basic-components-navigation.md#popinfo11)> | Yes   | Callback used to handle the result returned when the page is popped out of the stack.|
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br>**true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md), [Router Error Codes](../errorcode-router.md), and [API Call Error Codes](../errorcode-internal.md).

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed.  |
| 100001    | Internal error.|
| 100005    | Builder function not registered. |
| 100006    | NavDestination not found.|
| 300001    | hsp silent install fail.|

### replacePath

replacePath(moduleName: string, info: NavPathInfo, animated?: boolean): Promise\<void\>

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pops the top page from the current navigation stack and pushes the [NavDestination](ts-basic-components-navdestination.md) page specified by the **info** parameter onto the stack. This API uses a promise to handle asynchronous operations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                           | Mandatory  | Description                  |
| ---- | ----------------------------- | ---- | -------------------- |
| moduleName | string | Yes   | Module name of the package where the [NavDestination](ts-basic-components-navdestination.md) page is located.|
| info | [NavPathInfo](ts-basic-components-navigation.md#navpathinfo10) | Yes | Information about the parameters of the new page at the top of the stack. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**.<br>**true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Router Error Codes](../errorcode-router.md).

| ID  | Error Message|
| --------- | ------- |
| 300001    | hsp silent install fail.|

### replacePath

replacePath(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise\<void\>

First checks whether the subpackage exists. If not, downloads the subpackage through **moduleName**, then pops the current top of the page stack, and pushes the page information of the [NavDestination](ts-basic-components-navdestination.md) specified by **info** onto the stack. This API uses a promise to return the result.

Depending on the [LaunchMode](ts-basic-components-navigation.md#launchmode12) specified in the **options** parameter, different behaviors will be triggered.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                           | Mandatory  | Description                  |
| ---- | ----------------------------- | ---- | -------------------- |
| moduleName | string | Yes   | Module name of the package where the [NavDestination](ts-basic-components-navdestination.md) page is located.|
| info | [NavPathInfo](ts-basic-components-navigation.md#navpathinfo10) | Yes   | Parameters of the page to replace the top of the navigation stack.|
| options | [NavigationOptions](ts-basic-components-navigation.md#navigationoptions12) | No   | Navigation options. The default value is **{ launchMode: LaunchMode.STANDARD, animated: true }**.|

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Router Error Codes](../errorcode-router.md).

| ID  | Error Message|
| --------- | ------- |
| 300001    | hsp silent install fail.|

### replacePathByName

replacePathByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise\<void\>

First checks whether the subpackage exists. If not, downloads the subpackage through **moduleName**, then pops the current top of the page stack, and pushes the page information of the [NavDestination](ts-basic-components-navdestination.md) specified by **name** onto the stack, with **param** as the data to pass. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type     | Mandatory  | Description                  |
| ----- | ------- | ---- | --------------------- |
| moduleName | string | Yes   | Module name of the package where the [NavDestination](ts-basic-components-navdestination.md) page is located.|
| name  | string  | Yes   | Name of the [NavDestination](ts-basic-components-navdestination.md) page.  |
| param | Object | Yes   | Settings of the [NavDestination](ts-basic-components-navdestination.md) page.|
| animated | boolean | No    | Whether to support the transition animation.<br>Default value: **true**.<br>**true**: The transition animation is supported.<br>**false**: The transition animation is not supported. |

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Router Error Codes](../errorcode-router.md).

| ID  | Error Message|
| --------- | ------- |
| 300001    | hsp silent install fail.|

## Example

Main package:

```ts
// Index.ets
import { NavPushPathHelper } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
@Entry
@Component
struct NavigationExample {
  pageInfo: NavPathStack = new NavPathStack();
  helper: NavPushPathHelper = new NavPushPathHelper(this.pageInfo);

  build() {
    Navigation(this.pageInfo) {
      Column() {
        Button('StartTest', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.helper.pushPath('hsptest1', { name: 'pageOne' }, false).then(() => {
              console.info(`[pushPath]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushPath]failed, error code = ${error.code}, error.message = ${error.message}.`);
            }); // Push the NavDestination page specified by name to the navigation stack.
          })
      }
    }.title('NavIndex')
  }
}
```

Subpackage **hsptest1**:

```ts
// PageOne.ets
import { NavPushPathHelper } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class NavParam {
  count: number = 10;
}

class ParamWithOp {
  operation: number = 1;
  count: number = 10;
}

@Builder
export function PageOneBuilder(name: string, param: Object) {
  PageOne();
}

@Component
export struct PageOne {
  pageInfo: NavPathStack = new NavPathStack();
  helper: NavPushPathHelper = new NavPushPathHelper(this.pageInfo);
  @State message: string = 'Hello World';

  build() {
    NavDestination() {
      Column() {
        Text(this.message)
          .width('80%')
          .height(50)
          .margin(10)

        Button('pushPath', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.pushPath('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[pushPath]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}).then(() => {
              console.info(`[pushPath]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushPath]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushPath with NavigationOptions', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.pushPath('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[pushPath with NavigationOptions]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}, {launchMode:0, animated:true}).then(() => {
              console.info(`[pushPath with NavigationOptions]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushPath with NavigationOptions]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushPathByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            let navParam = new NavParam();
            this.helper.pushPathByName('hsptest2', 'pageTwo', navParam, (popInfo) => {
              this.message = '[pushPathByName]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }).then(() => {
              console.info(`[pushPathByName]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushPathByName]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushPathByNameWithoutOnPop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            let navParam = new NavParam();
            this.helper.pushPathByName('hsptest2', 'pageTwo', navParam, true).then(() => {
              console.info(`[pushPathByNameWithoutOnPop]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushPathByNameWithoutOnPop]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushDestination', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.pushDestination('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[pushDestination]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}).then(() => {
              console.info(`[pushDestination]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushDestination]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushDestination with NavigationOptions', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.pushDestination('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[pushDestination with NavigationOptions]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}, {launchMode:0, animated:true}).then(() => {
              console.info(`[pushDestination with NavigationOptions]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushDestination with NavigationOptions]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushDestinationByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            let navParam = new NavParam();
            this.helper.pushDestinationByName('hsptest2', 'pageTwo', navParam, (popInfo) => {
              this.message = '[pushDestinationByName]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }).then(() => {
              console.info(`[pushDestinationByName]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushDestinationByName]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushDestinationByNameWithoutOnPop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            let navParam = new NavParam();
            this.helper.pushDestinationByName('hsptest2', 'pageTwo', navParam, true).then(() => {
              console.info(`[pushDestinationByNameWithoutOnPop]success.`);
            }).catch((error: BusinessError) => {
                console.error(`[pushDestinationByNameWithoutOnPop]failed, error code = ${error.code}, error.message = ${error.message}.`);
              });
          })

        Button('replacePath', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.replacePath('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[replacePath]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}).then(() => {
              console.info(`[replacePath]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[replacePath]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('replacePath with NavigationOptions', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.replacePath('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[replacePath with NavigationOptions]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}, {launchMode:0, animated:true}).then(() => {
              console.info(`[replacePath with NavigationOptions]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[replacePath with NavigationOptions]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('replacePathByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            let navParam = new NavParam();
            this.helper.replacePathByName('hsptest2', 'pageTwo', navParam).then(() => {
              console.info(`[replacePathByName]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[replacePathByName]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

      }.width('100%').height('100%')
    }.title('pageOne')
    .onBackPressed(() => {
      this.pageInfo.pop({ number: 1 }) // Pop the top element out of the navigation stack.
      return true;
    }).onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
      this.helper = new NavPushPathHelper(this.pageInfo);
    })
  }
}
```

Configure **{"routerMap": "$profile:route_map"}** in the project configuration file **module.json5**. The configuration in the **route_map.json** file is as follows:

```json
{
  "routerMap": [
    {
      "name": "pageOne",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "PageOneBuilder",
      "data": {
        "description": "this is pageOne"
      }
    }
  ]
}
```

Subpackage **hsptest2**:

```ts
// PageTwo.ets

class ResultClass {
  constructor(count: number) {
    this.count = count;
  }
  count: number = 10;
}

@Builder
export function PageTwoBuilder() {
  PageTwo();
}

@Component
export struct PageTwo {
  pathStack: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Button('pop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.pop(new ResultClass(1)); // Return to the previous page and pass the processing result to the onPop callback of push.
          })
      }.width('100%').height('100%')
    }.title('pageTwo')
    .onBackPressed(() => {
      this.pathStack.pop(new ResultClass(0)); // Return to the previous page and pass the processing result to the onPop callback of push.
      return true;
    }).onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
    })
  }
}
```

Configure **{"routerMap": "$profile:route_map"}** in the project configuration file **module.json5**. The configuration in the **route_map.json** file is as follows:

```json
{
  "routerMap": [
    {
      "name": "pageTwo",
      "pageSourceFile": "src/main/ets/pages/PageTwo.ets",
      "buildFunction": "PageTwoBuilder",
      "data": {
        "description": "this is pageTwo"
      }
    }
  ]
}
```

![NavPushPathHelperDemo.gif](figures/NavPushPathHelperDemo.gif)