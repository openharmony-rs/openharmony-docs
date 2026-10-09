# ServiceExtensionContext (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7fe4eacae9c952d492316e40f501d71d3714186d translatedAt=2026-09-03T12:11:52.721Z pushedAt=2026-09-05T10:47:30.890Z -->

The ServiceExtensionContext module provides the context environment for the ServiceExtensionAbility. It inherits from ExtensionContext.

The ServiceExtensionContext module provides the capabilities of the ServiceExtensionAbility, including starting, terminating, connecting, and disconnecting an ability (application component).

> **NOTE**
> 
>  - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs of this module can be used only in the stage model.
>  - The APIs of this module must be used on the main thread, but not in child threads such as Worker and TaskPool.
>  - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## Usage

Before using the ServiceExtensionContext functions, obtain a ServiceExtensionContext instance through a ServiceExtensionAbility subclass instance.

**Example**

```ts
import { ServiceExtensionAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject | null; // Release the instance when the connection is disconnected.

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let context = this.context; // Obtain a ServiceExtensionContext instance.
  }
}
```

## ServiceExtensionContext.startAbility

startAbility(want: Want, callback: AsyncCallback&lt;void&gt;): void

Starts an ability. This API can be called only on the main thread. It uses an asynchronous callback to return the result.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes | Want type parameter. Pass required information about the Ability to start, such as the Ability name and bundle name. |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the ability is started, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. <br>Applicable Version: 10+ |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden.        |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. <br>Applicable Version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable Version: 10+ |
| 16000019 | No matching ability is found. <br>Applicable Version: 12+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable Version: 12+ |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };

    try {
      this.context.startAbility(want, (error: BusinessError) => {
        if (error.code) {
          // Process service logic errors.
          console.error(`startAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startAbility succeed');
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## ServiceExtensionContext.startAbility

startAbility(want: Want, options?: StartOptions): Promise\<void>

Starts an ability. This API can be called only on the main thread. It uses a promise to return the result asynchronously.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes | Want type parameter, carrying the information of the Ability to start, such as the Ability name and bundle name. |
| options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Parameters carried when starting the Ability. Pass this parameter when you need to specify startup parameters such as the window mode and display device. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. <br>Applicable Version: 10+ |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden.        |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. <br>Applicable Version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable Version: 10+ |
| 16000019 | No matching ability is found. <br>Applicable Version: 12+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable Version: 12+ |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let options: StartOptions = {
      windowMode: 0,
    };

    try {
      this.context.startAbility(want, options)
        .then((data: void) => {
          // Carry out normal service processing.
          console.info('startAbility succeed');
        })
        .catch((error: BusinessError) => {
          // Process service logic errors.
          console.error(`startAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## ServiceExtensionContext.startAbility

startAbility(want: Want, options: StartOptions, callback: AsyncCallback&lt;void&gt;): void

Starts an ability. This API can be called only on the main thread. It uses an asynchronous callback to return the result.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes| Want information about the target ability.|
| options | [StartOptions](js-apis-app-ability-startOptions.md) | Yes| Parameters used for starting the ability.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the ability is started, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. <br>Applicable Version: 10+ |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. <br>Applicable Version: 9-11 |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. <br>Applicable Version: 9-11 |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. <br>Applicable Version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable Version: 10+ |
| 16000019 | No matching ability is found. <br>Applicable Version: 12+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable Version: 12+ |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      windowMode: 0
    };

    try {
      this.context.startAbility(want, options, (error: BusinessError) => {
        if (error.code) {
          // Process service logic errors.
          console.error(`startAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startAbility succeed');
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## ServiceExtensionContext.startAbilityWithAccount

startAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback\<void>): void

Starts an ability with the account ID specified. This API can be called only on the main thread. It uses an asynchronous callback to return the result.

> **NOTE**
>
> - For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> - When accountId is the current user, no permission verification is required.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the ability is started, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden.        |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000019 | No matching ability is found. <br>Applicable Version: 12+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable Version: 12+ |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let accountId = 100;

    try {
      this.context.startAbilityWithAccount(want, accountId, (error: BusinessError) => {
        if (error.code) {
          // Process service logic errors.
          console.error(`startAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startAbilityWithAccount succeed');
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## ServiceExtensionContext.startAbilityWithAccount

startAbilityWithAccount(want: Want, accountId: number, options: StartOptions, callback: AsyncCallback\<void\>): void

Starts an ability with the account ID and start options specified. This API can be called only on the main thread. It uses an asynchronous callback to return the result.

> **NOTE**
>
> - For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> - When accountId is the current user, no permission verification is required.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| options | [StartOptions](js-apis-app-ability-startOptions.md) | Yes| Parameters used for starting the ability.|
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the ability is started, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. <br>Applicable Version: 9 |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. <br>Applicable Version: 9 |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. <br>Applicable Version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable Version: 10+ |
| 16000019 | No matching ability is found. <br>Applicable Version: 12+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable Version: 12+ |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId is the system account ID, which can be obtained via the getOsAccountLocalId API. Here 100 is used as an example.
    let accountId = 100;
    let options: StartOptions = {
      windowMode: 0
    };

    try {
      this.context.startAbilityWithAccount(want, accountId, options, (error: BusinessError) => {
        if (error.code) {
          // Process service logic errors.
          console.error(`startAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startAbilityWithAccount succeed');
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```


## ServiceExtensionContext.startAbilityWithAccount

startAbilityWithAccount(want: Want, accountId: number, options?: StartOptions): Promise\<void>

Starts an ability with the account ID specified. This API can be called only on the main thread. It uses a promise to return the result asynchronously.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> When accountId is the current user, no permission verification is required.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Parameters carried when starting an Ability. Pass this parameter when you need to specify startup parameters such as the window mode and display device. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden.        |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000019 | No matching ability is found. <br>Applicable Version: 12+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable Version: 12+ |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId is the system account ID, which can be obtained through the getOsAccountLocalId API. 100 is used as an example here.
    let accountId = 100;
    let options: StartOptions = {
      windowMode: 0
    };

    try {
      this.context.startAbilityWithAccount(want, accountId, options)
        .then((data: void) => {
          // Carry out normal service processing.
          console.info('startAbilityWithAccount succeed');
        })
        .catch((error: BusinessError) => {
          // Process service logic errors.
          console.error(`startAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.startServiceExtensionAbility

startServiceExtensionAbility(want: Want, callback: AsyncCallback\<void>): void

Starts a new ServiceExtensionAbility. This API can be called only on the main thread. It uses an asynchronous callback to return the result.

> **NOTE**
>
> - For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> - This API does not support starting the ServiceExtensionAbility of a clone application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the ServiceExtensionAbility is started, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. <br>Applicable Version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable Version: 10+ |
| 16000019 | No matching ability is found. <br>Applicable Version: 12+ |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      this.context.startServiceExtensionAbility(want, (error: BusinessError) => {
        if (error.code) {
          // Process service logic errors.
          console.error(`startServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startServiceExtensionAbility succeed');
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.startServiceExtensionAbility

startServiceExtensionAbility(want: Want): Promise\<void>

Starts a new ServiceExtensionAbility. This API can be called only in the main thread. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> - For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> - This API does not support starting the ServiceExtensionAbility of a clone application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. <br>Applicable Version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable Version: 10+ |
| 16000019 | No matching ability is found. <br>Applicable Version: 12+ |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      this.context.startServiceExtensionAbility(want)
        .then((data) => {
          // Carry out normal service processing.
          console.info('startServiceExtensionAbility succeed');
        })
        .catch((error: BusinessError) => {
          // Process service logic errors.
          console.error(`startServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.startServiceExtensionAbilityWithAccount

startServiceExtensionAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback\<void>): void

Starts a new ServiceExtensionAbility. This API can be called only in the main thread. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> - When accountId is the current user, no permission verification is required.
> - This API does not support starting the ServiceExtensionAbility of a clone application.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the ServiceExtensionAbility is started, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. <br>Applicable Version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable Version: 10+ |
| 16000019 | No matching ability is found. <br>Applicable Version: 12+ |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId is the system account ID, which can be obtained through the getOsAccountLocalId API. Here 100 is used as an example.
    let accountId = 100;

    try {
      this.context.startServiceExtensionAbilityWithAccount(want, accountId, (error: BusinessError) => {
        if (error.code) {
          // Process service logic errors.
          console.error(`startServiceExtensionAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startServiceExtensionAbilityWithAccount succeed');
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.startServiceExtensionAbilityWithAccount

startServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise\<void>

Starts a new ServiceExtensionAbility. This API can be called only in the main thread. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> - For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> - When accountId is the current user, no permission verification is required.
> - This API does not support starting the ServiceExtensionAbility of a clone application.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. <br>Applicable Version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable Version: 10+ |
| 16000019 | No matching ability is found. <br>Applicable Version: 12+ |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId is the system account ID, which can be obtained through the getOsAccountLocalId API. Here 100 is used as an example.
    let accountId = 100;

    try {
      this.context.startServiceExtensionAbilityWithAccount(want, accountId)
        .then((data: void) => {
          // Carry out normal service processing.
          console.info('startServiceExtensionAbilityWithAccount succeed');
        })
        .catch((error: BusinessError) => {
          // Process service logic errors.
          console.error(`startServiceExtensionAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.startAbilityAsCaller<sup>10+</sup>

startAbilityAsCaller(want: Want, callback: AsyncCallback\<void>): void

Starts an ability with the caller information specified. The caller information is carried in **Want** and identified at the system service layer. The ability can obtain the caller information from the **Want** parameter in the **onCreate** lifecycle callback. When this API is used to start an ability, the caller information carried in **Want** is not overwritten by the current application information. The system service layer can obtain the initial caller information. This API can be called only on the main thread. It uses an asynchronous callback to return the result.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Application Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Application Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes| Want information about the target ability.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the ability is started, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden.        |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable version: 12+ |
| 16000076 | The app instance key is invalid. <br>Applicable version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate(want: Want) {
    // want contains the information about the caller who starts the application.
    let localWant: Want = want;
    localWant.bundleName = 'com.example.demo';
    localWant.moduleName = 'entry';
    localWant.abilityName = 'TestAbility';

    // Start a new ability using the caller information.
    this.context.startAbilityAsCaller(localWant, (err) => {
      if (err && err.code != 0) {
        console.error(`startAbilityAsCaller failed, err: ${JSON.stringify(err)}`);
      } else {
        console.info('startAbilityAsCaller success.');
      }
    })
  }
}
```

## ServiceExtensionContext.startAbilityAsCaller<sup>10+</sup>

startAbilityAsCaller(want: Want, options: StartOptions, callback: AsyncCallback\<void>): void

Starts an ability with the caller information and start options specified. The caller information is carried in **Want** and identified at the system service layer. The ability can obtain the caller information from the **Want** parameter in the **onCreate** lifecycle callback. When this API is used to start an ability, the caller information carried in **Want** is not overwritten by the current application information. The system service layer can obtain the initial caller information. This API can be called only on the main thread. It uses an asynchronous callback to return the result.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes| Want information about the target ability.|
| options | [StartOptions](js-apis-app-ability-startOptions.md) | Yes| Parameters used for starting the ability.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the ability is started, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable Version: 12+ |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate(want: Want) {
    // want contains the information about the caller who starts the application.
    let localWant: Want = want;
    localWant.bundleName = 'com.example.demo';
    localWant.moduleName = 'entry';
    localWant.abilityName = 'TestAbility';

    let option: StartOptions = {
      displayId: 0
    }

    // Start a new ability using the caller information.
    this.context.startAbilityAsCaller(localWant, option, (err) => {
      if (err && err.code != 0) {
        console.error(`startAbilityAsCaller failed, err: ${JSON.stringify(err)}`);
      } else {
        console.info('startAbilityAsCaller success.');
      }
    })
  }
}
```

## ServiceExtensionContext.startAbilityAsCaller<sup>10+</sup>

startAbilityAsCaller(want: Want, options?: StartOptions): Promise\<void>

Starts an ability with the start options specified. The caller information is carried in **Want** and identified at the system service layer. The ability can obtain the caller information from the **Want** parameter in the **onCreate** lifecycle callback. When this API is used to start an ability, the caller information carried in **Want** is not overwritten by the current application information. The system service layer can obtain the initial caller information. This API can be called only on the main thread. It uses a promise to return the result asynchronously.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes| Want information about the target ability.|
| options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Parameters carried when starting an Ability. Need to specify startup parameters such as window mode and display device when passing. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden.        |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable Version: 12+ |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate(want: Want) {
    // want contains the information about the caller who starts the application.
    let localWant: Want = want;
    localWant.bundleName = 'com.example.demo';
    localWant.moduleName = 'entry';
    localWant.abilityName = 'TestAbility';

    let option: StartOptions = {
      displayId: 0
    };

    // Start a new ability using the caller information.
    this.context.startAbilityAsCaller(localWant, option)
      .then(() => {
        console.info('startAbilityAsCaller success.');
      })
      .catch((err: BusinessError) => {
        console.error(`startAbilityAsCaller failed, err: ${JSON.stringify(err)}`);
      })
  }
}
```

## ServiceExtensionContext.stopServiceExtensionAbility

stopServiceExtensionAbility(want: Want, callback: AsyncCallback\<void>): void

Stops the specified ServiceExtensionAbility background service. This API can be called only in the main thread and uses an asynchronous callback.

> **NOTE**
>
> This API does not support stopping the ServiceExtensionAbility of a clone application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the ServiceExtensionAbility is stopped, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. <br>Applicable Version: 10+ |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      this.context.stopServiceExtensionAbility(want, (error: BusinessError) => {
        if (error.code) {
          // Process service logic errors.
          console.error(`stopServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('stopServiceExtensionAbility succeed');
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.stopServiceExtensionAbility

stopServiceExtensionAbility(want: Want): Promise\<void>

Stops the specified ServiceExtensionAbility background service. This API can be called only in the main thread and uses a promise to return the result.

> **NOTE**
>
> This API does not support stopping the ServiceExtensionAbility of a clone application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. <br>Applicable Version: 10+ |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      this.context.stopServiceExtensionAbility(want)
        .then(() => {
          // Carry out normal service processing.
          console.info('stopServiceExtensionAbility succeed');
        })
        .catch((error: BusinessError) => {
          // Process service logic errors.
          console.error(`stopServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.stopServiceExtensionAbilityWithAccount

stopServiceExtensionAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback\<void>): void

Stops the specified ServiceExtensionAbility background service of the specified account. This API can be called only in the main thread and uses an asynchronous callback.

> **NOTE**
> 
> - When accountId is the current user, no permission verification is required.
> - This API does not support stopping the ServiceExtensionAbility of a clone application.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| accountId | number | Yes | Account ID of the system account to stop, which can be obtained by the [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9) API. |
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the ServiceExtensionAbility is stopped, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId is the system account ID, which can be obtained through the getOsAccountLocalId API. 100 is used as an example here.
    let accountId = 100;

    try {
      this.context.stopServiceExtensionAbilityWithAccount(want, accountId, (error: BusinessError) => {
        if (error.code) {
          // Process service logic errors.
          console.error(`stopServiceExtensionAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('stopServiceExtensionAbilityWithAccount succeed');
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.stopServiceExtensionAbilityWithAccount

stopServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise\<void>

Stops the specified ServiceExtensionAbility background service of the specified account. This API can be called only in the main thread and uses a promise to return the result.

> **NOTE**
> 
> - When accountId is the current user, no permission verification is required.
> - This API does not support stopping the ServiceExtensionAbility of a clone application.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| accountId | number | Yes | Account ID of the system account to stop, which can be obtained by the [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9) API. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId is the system account ID, which can be obtained through the getOsAccountLocalId API. 100 is used as an example here.
    let accountId = 100;

    try {
      this.context.stopServiceExtensionAbilityWithAccount(want, accountId)
        .then(() => {
          // Carry out normal service processing.
          console.info('stopServiceExtensionAbilityWithAccount succeed');
        })
        .catch((error: BusinessError) => {
          // Process service logic errors.
          console.error(`stopServiceExtensionAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.terminateSelf

terminateSelf(callback: AsyncCallback&lt;void&gt;): void

Terminates this ability. This API can be called only on the main thread. It uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the ability is terminated, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. <br>Applicable Version: 9 |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 9 |
| 16000005 | The specified process does not have the permission. <br>Applicable Version: 9 |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |

**Example**

```ts
import { ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    this.context.terminateSelf((error: BusinessError) => {
      if (error.code) {
        // Process service logic errors.
        console.error(`terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
        return;
      }
      // Carry out normal service processing.
      console.info('terminateSelf succeed');
    });
  }
}
```

## ServiceExtensionContext.terminateSelf

terminateSelf(): Promise&lt;void&gt;

Terminates this ability. This API can be called only on the main thread. It uses a promise to return the result asynchronously.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 16000001 | The specified ability does not exist. <br>Applicable Version: 9 |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 9 |
| 16000005 | The specified process does not have the permission. <br>Applicable Version: 9 |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |

**Example**

```ts
import { ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    this.context.terminateSelf().then(() => {
      // Carry out normal service processing.
      console.info('terminateSelf succeed');
    }).catch((error: BusinessError) => {
      // Process service logic errors.
      console.error(`terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```

## ServiceExtensionContext.connectServiceExtensionAbility

connectServiceExtensionAbility(want: Want, options: ConnectOptions): number

Connects this ability to a ServiceExtensionAbility. This API can be called only on the main thread.

> **NOTE**
>
> - For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> - This API does not support connecting to the ServiceExtensionAbility of a clone application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes | Want type parameter, which carries the information about the Ability to connect, such as the Ability name and bundle name. |
| options | [ConnectOptions](js-apis-inner-ability-connectOptions.md) | Yes | Connection options object, which contains the callback functions invoked when the service is connected, disconnected, or fails to connect. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Connection identifier used to disconnect the connection later. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. <br>Applicable Version: 10+ |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. <br>Applicable Version: 10+ |
| 16000008 | The crowdtesting application expires. <br>Applicable Version: 10+ |
| 16000053 | The ability is not on the top of the UI. <br>Applicable Version: 10+ |
| 16000055 | Installation-free timed out. <br>Applicable Version: 10+ |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. <br>Applicable Version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable Version: 10+ |
| 16000050 | Internal error. |

**Example**

```ts
import { ServiceExtensionAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

let commRemote: rpc.IRemoteObject | null; // Release when disconnecting.

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('----------- onConnect -----------');
      },
      onDisconnect(elementName) {
        console.info('----------- onDisconnect -----------');
      },
      onFailed(code) {
        console.error('----------- onFailed -----------');
      }
    };
    let connection: number;

    try {
      connection = this.context.connectServiceExtensionAbility(want, options);
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.connectServiceExtensionAbilityWithAccount

connectServiceExtensionAbilityWithAccount(want: Want, accountId: number, options: ConnectOptions): number

Connects this ability to a ServiceExtensionAbility of a given account. This API can be called only on the main thread.

> **NOTE**
>
> - For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> - When accountId is the current user, no permission verification is required.
> - This API does not support connecting to the ServiceExtensionAbility of a clone application.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called on phones and tablets. If it is called on other devices, error code 16000006 is returned.

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes | Want information for connecting to the Ability. |
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| options | [ConnectOptions](js-apis-inner-ability-connectOptions.md) | Yes | Connection options object, which contains the callback functions invoked when the service is connected, disconnected, or fails to connect. |

**Return value**

| Type| Description|
| -------- | -------- |
| number | Connection identifier used to disconnect the connection later. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. <br>Applicable Version: 10+ |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. <br>Applicable Version: 10+ |
| 16000008 | The crowdtesting application expires. <br>Applicable Version: 10+ |
| 16000053 | The ability is not on the top of the UI. <br>Applicable Version: 10+ |
| 16000055 | Installation-free timed out. <br>Applicable Version: 10+ |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. <br>Applicable Version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable Version: 10+ |
| 16000050 | Internal error. |

**Example**

```ts
import { ServiceExtensionAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

let commRemote: rpc.IRemoteObject | null; // Release it when disconnecting.

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId is the system account ID, which can be obtained through the getOsAccountLocalId API. Here 100 is used as an example.
    let accountId = 100;
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('----------- onConnect -----------');
      },
      onDisconnect(elementName) {
        console.info('----------- onDisconnect -----------');
      },
      onFailed(code) {
        console.info('----------- onFailed -----------');
      }
    };
    let connection: number;

    try {
      connection = this.context.connectServiceExtensionAbilityWithAccount(want, accountId, options);
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.disconnectServiceExtensionAbility

disconnectServiceExtensionAbility(connection: number, callback: AsyncCallback&lt;void&gt;): void

Disconnects an ability from a connected service-type ability. After the disconnection, set the remote object returned upon successful connection to null. This API can be called only on the main thread. It uses an asynchronous callback.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| connection | number | Yes| Number returned after **connectServiceExtensionAbility** is called.|
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. If the Ability is successfully disconnected from the connected service-type Ability, err is undefined; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |

**Example**

```ts
import { ServiceExtensionAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

let commRemote: rpc.IRemoteObject | null; // Release the instance when the connection is disconnected.

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    // connection is the return value of connectServiceExtensionAbility.
    let connection = 1;
    try {
      this.context.disconnectServiceExtensionAbility(connection, (error: BusinessError) => {
        commRemote = null;
        if (error.code) {
          // Process service logic errors.
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('disconnectServiceExtensionAbility succeed');
      });
    } catch (paramError) {
      commRemote = null;
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.disconnectServiceExtensionAbility

disconnectServiceExtensionAbility(connection: number): Promise&lt;void&gt;

Disconnects an ability from a connected service-type ability. After the disconnection, set the remote object returned upon successful connection to null. This API can be called only on the main thread. It uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| connection | number | Yes| Number returned after **connectServiceExtensionAbility** is called.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |

**Example**

```ts
import { ServiceExtensionAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

let commRemote: rpc.IRemoteObject | null; // Release the instance when the connection is disconnected.

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    // connection is the return value of connectServiceExtensionAbility.
    let connection = 1;
    try {
      this.context.disconnectServiceExtensionAbility(connection)
        .then(() => {
          commRemote = null;
          // Carry out normal service processing.
          console.info('disconnectServiceExtensionAbility succeed');
        })
        .catch((error: BusinessError) => {
          commRemote = null;
          // Process service logic errors.
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      commRemote = null;
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.startAbilityByCall

startAbilityByCall(want: Want): Promise&lt;Caller&gt;

Starts an ability in the foreground or background and obtains the caller object for communicating with the ability. This API can be called only on the main thread. It uses a promise to return the result asynchronously.

This API cannot be used to start the UIAbility with the launch type set to [specified](../../application-models/uiability-launch-type.md#specified).

Observe the following when using this API:
 - If an application running in the background needs to call this API to start an ability, it must have the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission.
 - If **exported** of the target ability is **false** in cross-application scenarios, the caller must have the ohos.permission.START_INVISIBLE_ABILITY permission.
 - The usage rules of this API differ between the intra-device and cross-device scenarios. For details, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**Required permissions**: ohos.permission.ABILITY_BACKGROUND_COMMUNICATION

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Information about the ability to start, including **abilityName**, **moduleName**, **bundleName**, **deviceId**, and **parameters** (optional). If **parameters** is left blank or null, the ability is started in the background.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Caller&gt; | Promise used to return the caller object to communicate with.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. <br>Applicable Version: 9 |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. <br>Applicable Version: 9 |

**Example**

Start an ability in the background.

```ts
import { ServiceExtensionAbility, Caller, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let caller: Caller;
    // Start an ability in the background by not passing parameters.
    let wantBackground: Want = {
      bundleName: 'com.example.myservice',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      deviceId: ''
    };

    try {
      this.context.startAbilityByCall(wantBackground)
        .then((obj: Caller) => {
          // Carry out normal service processing.
          caller = obj;
          console.info('startAbilityByCall succeed');
        }).catch((error: BusinessError) => {
        // Process service logic errors.
        console.error(`startAbilityByCall failed, error.code: ${error.code}, error.message: ${error.message}`);
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

Start an ability in the foreground.

```ts
import { ServiceExtensionAbility, Caller, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let caller: Caller;
    // Start an ability in the foreground with ohos.aafwk.param.callAbilityToForeground in parameters set to true.
    let wantForeground: Want = {
      bundleName: 'com.example.myservice',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      deviceId: '',
      parameters: {
        'ohos.aafwk.param.callAbilityToForeground': true
      }
    };

    try {
      this.context.startAbilityByCall(wantForeground)
        .then((obj: Caller) => {
          // Carry out normal service processing.
          caller = obj;
          console.info('startAbilityByCall succeed');
        }).catch((error: BusinessError) => {
        // Process service logic errors.
        console.error(`startAbilityByCall failed, error.code: ${error.code}, error.message: ${error.message}`);
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```
## ServiceExtensionContext.startRecentAbility

startRecentAbility(want: Want, callback: AsyncCallback\<void>): void

Starts an ability. If the ability has multiple instances, the latest instance is started. This API can be called only on the main thread. It uses an asynchronous callback to return the result.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| callback | AsyncCallback\<void> | Yes| Callback used to return the result. If the ability is started, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. <br>Applicable Version: 10+ |
| 202 | The application is not system-app, can not use system-api. <br>Applicable Version: 14+ |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable Version: 14+ |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      this.context.startRecentAbility(want, (err: BusinessError) => {
        if (err.code) {
          // Process service logic errors.
          console.error(`startRecentAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startRecentAbility succeed');
      });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startRecentAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```
## ServiceExtensionContext.startRecentAbility

startRecentAbility(want: Want, options: StartOptions, callback: AsyncCallback\<void>): void

Starts an ability. If the ability has multiple instances, the latest instance is started. This API can be called only on the main thread. It uses an asynchronous callback to return the result.

You can use this API to carry start options.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| options | [StartOptions](js-apis-app-ability-startOptions.md) | Yes| Parameters used for starting the ability.|
| callback | AsyncCallback\<void> | Yes| Callback used to return the result. If the ability is started, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. <br>Applicable Version: 10+ |
| 202 | The application is not system-app, can not use system-api. <br>Applicable Version: 14+ |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. <br>Applicable Version: 9 |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable Version: 14+ |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      windowMode: 0
    };

    try {
      this.context.startRecentAbility(want, options, (err: BusinessError) => {
        if (err.code) {
          // Process service logic errors.
          console.error(`startRecentAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startRecentAbility succeed');
      });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startRecentAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```
## ServiceExtensionContext.startRecentAbility

startRecentAbility(want: Want, options?: StartOptions): Promise\<void>

Starts an ability. If the ability has multiple instances, the latest instance is started. This API uses a promise to return the result asynchronously. It can be called only on the main thread.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Parameters carried when starting an Ability. Pass when you need to specify startup parameters such as window mode and display device. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. <br>Applicable Version: 10+ |
| 202 | The application is not system-app, can not use system-api. <br>Applicable Version: 14+ |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>Applicable Version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000073 | The app clone index is invalid. <br>Applicable Version: 14+ |
| 16000076 | The app instance key is invalid. <br>Applicable Version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>Applicable Version: 14+ |
| 16000078 | The multi-instance is not supported. <br>Applicable Version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>Applicable Version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>Applicable Version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      windowMode: 0,
    };

    try {
      this.context.startRecentAbility(want, options)
        .then(() => {
          // Carry out normal service processing.
          console.info('startRecentAbility succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`startRecentAbility failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startRecentAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## ServiceExtensionContext.startAbilityByCallWithAccount<sup>10+</sup>

startAbilityByCallWithAccount(want: Want, accountId: number): Promise&lt;Caller&gt;

Starts an ability with the account ID specified and obtains the caller object for communicating with the ability. This API can be called only on the main thread. It uses a promise to return the result asynchronously.

This API cannot be used to start the UIAbility with the launch type set to [specified](../../application-models/uiability-launch-type.md#specified).

Observe the following when using this API:
 - If an application needs to call this API to start an ability that belongs to another user, it must have the ohos.permission.ABILITY_BACKGROUND_COMMUNICATION and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permissions.
 - If an application running in the background needs to call this API to start an ability, it must have the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission.
 - If **exported** of the target ability is **false** in cross-application scenarios, the caller must have the ohos.permission.START_INVISIBLE_ABILITY permission.
 - The usage rules of this API differ between the intra-device and cross-device scenarios. For details, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**Required permissions**: ohos.permission.ABILITY_BACKGROUND_COMMUNICATION and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Information about the ability to start, including **abilityName**, **moduleName**, **bundleName**, **deviceId** (optional), and **parameters** (optional). If **deviceId** is left blank or null, the local ability is started. If **parameters** is left blank or null, the ability is started in the background.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Caller&gt; | Promise used to return the caller object to communicate with.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { ServiceExtensionAbility, Want, Caller } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let caller: Caller;
    // ID of a system account. The value -1 indicates the current user.
    let accountId = -1;
    // Specify the ability to start.
    let want: Want = {
      bundleName: 'com.acts.actscalleeabilityrely',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      deviceId: '',
      parameters: {
        // If ohos.aafwk.param.callAbilityToForeground is set to true, the ability is launched in the foreground; if it is set to false or not set, the ability is launched in the background.
        'ohos.aafwk.param.callAbilityToForeground': true
      }
    };

    try {
      this.context.startAbilityByCallWithAccount(want, accountId)
        .then((obj: Caller) => {
          // Carry out normal service processing.
          caller = obj;
          console.info('startAbilityByCallWithAccount succeed');
        }).catch((error: BusinessError) => {
        // Process service logic errors.
        console.error(`startAbilityByCallWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ServiceExtensionContext.requestModalUIExtension<sup>11+</sup>

requestModalUIExtension(pickerWant: Want): Promise\<void>

Requests the specified focused application to start the UIExtensionAbility of the corresponding type. The focused application is specified by **bundleName** in **want.parameters**. If **bundleName** is left unspecified, or if the specified application does not gain focus, the UIExtensionAbility is directly started on the system UI. The UIExtensionAbility to start is determined by the combination of the **bundleName**, **abilityName**, and **moduleName** fields in **Want**, and its type is determined by the **ability.want.params.uiExtensionType** field in **want.parameters**. This API can be called only on the main thread. It uses a promise to return the result asynchronously.

Before starting the UIExtensionAbility, ensure that the focused application has finished page initialization. Otherwise, the UIExtensionAbility fails to start. The application can determine the time to start the UIExtensionAbility by listening for the page loading status.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| pickerWant | [Want](js-apis-app-ability-want.md)  | Yes | Want information for starting the UIExtension. Ensure that the target application has completed page initialization before calling this API. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object with no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. <br>Applicable Version: 11 |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. <br>Applicable Version: 11 |
| 16000002 | Incorrect ability type. <br>Applicable Version: 11 |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 11 |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. <br>Applicable Version: 11 |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class ServiceExtension extends ServiceExtensionAbility {
  onCreate() {
    let pickerWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'UIExtAbility',
      moduleName: 'entry_test',
      parameters: {
        'bundleName': 'com.example.myapplication',
        // The value is the same as the value of type configured for com.example.myapplication.UIExtAbility.
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };

    try {
      this.context.requestModalUIExtension(pickerWant)
        .then(() => {
          // Carry out normal service processing.
          console.info('requestModalUIExtension succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`requestModalUIExtension failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`requestModalUIExtension failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## ServiceExtensionContext.requestModalUIExtension<sup>11+</sup>

requestModalUIExtension(pickerWant: Want, callback: AsyncCallback\<void>): void

Requests the specified focused application to start the UIExtensionAbility of the corresponding type. The focused application is specified by **bundleName** in **want.parameters**. If **bundleName** is left unspecified, or if the specified application does not gain focus, the UIExtensionAbility is directly started on the system UI. The UIExtensionAbility to start is determined by the combination of the **bundleName**, **abilityName**, and **moduleName** fields in **Want**, and its type is determined by the **ability.want.params.uiExtensionType** field in **want.parameters**. This API can be called only on the main thread. It uses an asynchronous callback to return the result.

Before starting the UIExtensionAbility, ensure that the focused application has finished page initialization. Otherwise, the UIExtensionAbility fails to start. The application can determine the time to start the UIExtensionAbility by listening for the page loading status.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| pickerWant | [Want](js-apis-app-ability-want.md)  | Yes| Want information used to start the UIExtensionAbility.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the UIExtensionAbility is started, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. <br>Applicable Version: 11 |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. <br>Applicable Version: 11 |
| 16000002 | Incorrect ability type. <br>Applicable Version: 11 |
| 16000004 | Cannot start an invisible component. <br>Applicable Version: 11 |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. <br>Applicable Version: 11 |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class ServiceExtension extends ServiceExtensionAbility {
  onCreate() {
    let pickerWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'com.example.myapplication.UIExtAbility',
      moduleName: 'entry_test',
      parameters: {
        'bundleName': 'com.example.myapplication',
        // The value is the same as the value of type configured for com.example.myapplication.UIExtAbility.
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };

    try {
      this.context.requestModalUIExtension(pickerWant, (err: BusinessError) => {
        if (err.code) {
          // Process service logic errors.
          console.error(`requestModalUIExtension failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('requestModalUIExtension succeed');
      });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`requestModalUIExtension failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## ServiceExtensionContext.openLink<sup>12+</sup>

openLink(link: string, options?: OpenLinkOptions): Promise&lt;void&gt;

Starts a UIAbility through App Linking. This API can be called only on the main thread. It uses a promise to return the result asynchronously.

A URL in the standard format is passed in to the **link** field to start the target UIAbility based on the implicit Want matching rules. The target UIAbility must have the following filter characteristics to process links of App Linking:
- The **actions** field must contain **ohos.want.action.viewData**.
- The **entities** field must contain **entity.system.browsable**.
- The **uris** field must contain elements whose **scheme** is **https** and **domainVerify** is **true**.

If an input parameter is invalid, for example, a mandatory parameter is not set or the URL set in **link** is not in the standard format, an exception is thrown. If the parameter verification is successful but an error occurs when starting the target UIAbility, the error information is returned through promise.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| link | string | Yes| URL to open, which must be in the standard format.|
| options | [OpenLinkOptions](js-apis-app-ability-openLinkOptions.md) | No | Option parameters for opening the URL, which can be used to set whether to enable only App Linking. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Failed to start the invisible ability. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation flag is forbidden. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000019 | No matching ability is found. |
| 16200001 | The caller has been released. |
| 16000136 | The UIAbility is prohibited from launching itself via App Linking. <br>Applicable Version: 23+ |

**Example**

```ts
import { ServiceExtensionAbility, Want, OpenLinkOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function log(info: string) {
  console.error(`[ServiceExtApp]:: ${JSON.stringify(info)}`);
}

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onCreate(want: Want) {
    log(`ServiceExtAbility OnCreate`);
  }

  onRequest(want: Want, startId: number) {
    log(`ServiceExtAbility onRequest`);
    let link: string = 'https://www.example.com';
    let openLinkOptions: OpenLinkOptions = {
      appLinkingOnly: false
    };
    try {
      this.context.openLink(
        link,
        openLinkOptions
      ).then(() => {
        log(`open link success.`);
      }).catch((err: BusinessError) => {
        log(`open link failed, errCode ${JSON.stringify(err.code)}`);
      });
    }
    catch (e) {
      log(`exception occurred, errCode ${JSON.stringify(e.code)}`);
    }
  }

  onDestroy() {
    log(`ServiceExtAbility onDestroy`);
  }
}
```

## ServiceExtensionContext.preStartMission<sup>12+</sup>

preStartMission(bundleName: string, moduleName: string, abilityName: string, startTime: string): Promise&lt;void&gt;

Starts an atomic service and pre-opens the window, with the loading box skipped. This API uses a promise to return the result.

If parameter verification is successful but the atomic service fails to start, you need to implement an exception mechanism to capture the error.

**Required permissions**: ohos.permission.PRE_START_ATOMIC_SERVICE

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name of the atomic service.|
| moduleName | string | Yes| Module name of the atomic service.|
| abilityName | string | Yes| Ability name of the atomic service.|
| startTime | string | Yes| Start time to open the atomic service, in milliseconds.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300007 | The target free-installation task does not exist. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error.                    |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function log(info: string) {
  console.error(`[ServiceExtApp]:: ${JSON.stringify(info)}`);
}

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onCreate(want: Want) {
    log(`ServiceExtAbility OnCreate, want: ${JSON.stringify(want)}.`);
  }

  onRequest(want: Want, startId: number) {
    log(`ServiceExtAbility onRequest`);
    try {
      if (want.parameters && want.parameters["ohos.aafwk.param.startTime"]) {
        this.context.preStartMission(
          want.bundleName,
          want.moduleName,
          want.abilityName,
          want.parameters["ohos.aafwk.param.startTime"] as string
        ).then(() => {
          log(`pre-start mission success.`);
        }).catch((err: BusinessError) => {
          log(`pre-start mission failed, errCode: ${err.code}, errMsg: ${err.message}.`);
        });
      }
    } catch (e) {
      let code = (e as BusinessError).code;
      let msg = (e as BusinessError).message;
      log(`exception occurred, errCode: ${code}, errMsg: ${msg}.`);
    }
  }

  onDestroy() {
    log(`ServiceExtAbility onDestroy`);
  }
}
```

## ServiceExtensionContext.startUIServiceExtensionAbility<sup>14+</sup>

startUIServiceExtensionAbility(want: Want): Promise&lt;void&gt;

Starts a new [UIServiceExtensionAbility](js-apis-app-ability-uiServiceExtensionAbility-sys.md). This API can be called only in the main thread. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> - For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> - This API does not support starting the UIServiceExtensionAbility of a clone application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**
| Name| Type| Mandatory| Description                |
| ------ | ---- | ---- | -------------------- |
| want   | [Want](js-apis-app-ability-want.md) | Yes | Want type parameter, carrying the information about the Ability to start, such as the Ability name and bundle name. |

**Return value**

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).
| ID| Error Message                                                             |
| -------- | ---------------------------------------------------------------------|
| 201      | The application does not have permission to call the interface.      |
| 202      | The application is not system-app, can not use system-api.           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801      | Capability not supported.                       |
| 16000001 | The specified ability does not exist.               |
| 16000002 | Incorrect ability type.                             |
| 16000004 | Cannot start an invisible component.              |
| 16000005 | The specified process does not have the permission. |
| 16000008 | The crowdtesting application expires.               |
| 16000011 | The context does not exist.                         |
| 16000012 | The application is controlled.                      |
| 16000013 | The application is controlled by EDM.               |
| 16000019 | No matching ability is found.                       |
| 16000050 | Internal error.                                     |
| 16200001 | The caller has been released.                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

export default class MyServiceExtensionAbility extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    const startWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'UIServiceExtensionAbility'
    }
    // Start a UIServiceExtensionAbility.
    this.context.startUIServiceExtensionAbility(startWant).then(() => {
      console.info('succeeded');
    }).catch((error: BusinessError) => {
      console.error(`error code: ${error.code}, error message : ${error.message}`);
    })
  }
}
```

## ServiceExtensionContext.openAtomicService<sup>18+</sup>
openAtomicService(appId: string, options?: AtomicServiceOptions): Promise&lt;void&gt;

Starts an atomic service by application ID. This API can be called only in the main thread. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| appId | string | Yes| Unique ID of the application, which is allocated by the cloud.|
| options | [AtomicServiceOptions](js-apis-app-ability-atomicServiceOptions.md) | No| Parameter carried in the request for starting the atomic service in jump-out mode.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | The application does not have permission to call the interface. |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000002 | Incorrect ability type.                                      |
| 16000004 | Cannot start an invisible component.                       |
| 16000011 | The context does not exist.                                  |
| 16000012 | The application is controlled.                               |
| 16000050 | Internal error.                                              |
| 16200001 | The caller has been released.                                |

**Example**

```ts
import { ServiceExtensionAbility, Want, AtomicServiceOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ServiceExtension extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    let appId: string = '6918661953712445909';
    let options: AtomicServiceOptions = {
      displayId: 0,
    };
    try {
      this.context.openAtomicService(appId, options)
        .then(() => {
          console.info('openAtomicService succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`openAtomicService failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`openAtomicService failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## ServiceExtensionContext.startUIAbilities<sup>20+</sup>

startUIAbilities(wantList: Array\<Want>): Promise\<void>

Starts multiple UIAbility components simultaneously. This API uses a promise to return the result asynchronously.

You can pass the Want information of multiple UIAbility instances, which can point to one or more applications. If all the UIAbility instances can be started successfully, the system displays these UIAbility instances in multiple windows simultaneously. Depending on the window handling, different devices may have varying display effects (including window shape, quantity, and layout).

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called on phones and tablets. If it is called on other devices, error code 801 is returned.

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------ |
| wantList | Array\<[Want](js-apis-app-ability-want.md)> | Yes | List of startup parameters for multiple UIAbility instances that need to be started simultaneously. A maximum of 4 Want objects can be passed in. The Want startup parameters do not support implicit startup, cross-user startup, distributed startup, installation-free startup, or on-demand loading. If no clone is specified, the main application is started by default. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------ | ------ |
| 201 | The application does not have permission to call the interface. |
| 202 | Not system application. |
| 801 | Capability not supported. |
| 16000001 | The specified ability does not exist. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |
| 16000073 | The app clone index is invalid. |
| 16000076 | The app instance key is invalid. |
| 16000080 | Creating a new instance is not supported. |
| 16000120 | A maximum of four UIAbility instances can be started simultaneously. The current parameter exceeds the maximum number or is less than 1.|
| 16000121 | The target component type is not a UIAbility. |
| 16000122 | The target component is blocked by the system module and does not support startup. |
| 16000123 | Implicit startup is not supported. |
| 16000124 | Starting a remote UIAbility is not supported. |
| 16000125 | Starting a plugin UIAbility is not supported. |
| 16000126 | Starting DLP files is not supported. |

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryServiceExtAbility extends ServiceExtensionAbility {
  onRequest() {
    let want1: Want = {
      bundleName: 'com.example.myapplication1',
      abilityName: 'EntryAbility'
    };
    let want2: Want = {
      bundleName: 'com.example.myapplication2',
      abilityName: 'EntryAbility'
    };
    let wantList: Array<Want> = [want1, want2];
    try {
      this.context.startUIAbilities(wantList).then(() => {
        console.info(`TestTag:: start succeeded.`);
      }).catch((error: BusinessError) => {
        console.info(`TestTag:: startUIAbilities failed: ${JSON.stringify(error)}`);
      });
    } catch (paramError) {
      // Process input parameter errors.
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```
## ServiceExtensionContext.requestModalUIExtensionWithAccount

requestModalUIExtensionWithAccount(pickerWant: Want, accountId: number): Promise\<void>

Requests to start a UIExtensionAbility of the corresponding type on the specified focused application for the specified user. The focused application is specified by bundleName in want.parameters. If no focused application is specified or the specified application is not focused, the UIExtensionAbility is started directly on the system UI. The UIExtensionAbility to be started is determined by the bundleName, abilityName, and moduleName fields in Want, and its type must be configured through the ability.want.params.uiExtensionType field in want.parameters. This operation can be called only on the main thread and provides an asynchronous callback in Promise form.

Before the focused application starts the UIExtensionAbility, ensure that the application has completed page initialization; otherwise, the startup will fail. The application can determine the timing for starting the UIExtensionAbility by listening to the page loading status.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**Required Permission**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Since:** 26.0.0

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| pickerWant | [Want](js-apis-app-ability-want.md)  | Yes | Want information for starting the UIExtension. The focused application is specified by bundleName in want.parameters. The UIExtensionAbility to be started is determined by the bundleName, abilityName, and moduleName fields in Want, and its type must be configured through the ability.want.params.uiExtensionType field in want.parameters. Ensure that the focused application has completed page initialization before calling this API. |
| accountId | number | Yes | Account ID of the system account, which can be obtained through [getForegroundOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount-sys.md#getforegroundosaccountlocalid23). |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise object that returns no result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed;2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. 4.The logical screen corresponding to the specified accountId is not in the foreground.|

**Example**

```ts
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ServiceExtension extends ServiceExtensionAbility {
  onCreate(want: Want) {
    let pullUIExtWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'UIExtAbility',
      moduleName: 'entry_test',
      parameters: {
        'bundleName': 'com.example.myapplication',
        // Same as the type configured for com.example.myapplication.UIExtAbility.
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };
    // Account ID description:
    // 1. Fixed value 100 in the example.
    // 2. You can call the system account management API getForegroundOsAccountLocalId(displayId: number) to obtain the ID of the foreground system account running on the specified logical display.
    let accountId = 100;

    try {
      this.context.requestModalUIExtensionWithAccount(pullUIExtWant, accountId)
        .then(() => {
          // Execute normal service logic.
          console.info('requestModalUIExtensionWithAccount succeed');
        })
        .catch((err: BusinessError) => {
          // Handle service logic errors.
          console.error(`requestModalUIExtensionWithAccount failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Handle input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`requestModalUIExtensionWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```
<!--no_check-->