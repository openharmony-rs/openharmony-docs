# UIAbilityContext (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @dsz2025-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7fe4eacae9c952d492316e40f501d71d3714186d translatedAt=2026-09-03T12:10:14.698Z pushedAt=2026-09-05T10:47:30.882Z -->

UIAbilityContext provides the context environment for a [UIAbility](js-apis-app-ability-uiAbility.md) that needs to store its status. It inherits from [Context](js-apis-inner-application-context.md) and provides UIAbility-related configuration and APIs for operating UIAbility and ServiceExtensionAbility components. For example, you can use the APIs to start a UIAbility, terminate a UIAbility to which the UIAbilityContext belongs, and start, terminate, connect to, or disconnect from a ServiceExtensionAbility.

> **NOTE**
>
>  - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs of this module can be used only in the stage model.
>  - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

> **NOTE**
>
> In the sample code provided in this topic, **this.context** is used to obtain UIAbilityContext, where **this** indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

## UIAbilityContext

### startAbilityForResultWithAccount

startAbilityForResultWithAccount(want: Want, accountId: number, callback: AsyncCallback\<AbilityResult>): void

Starts a UIAbility with the account ID specified and returns the result when the UIAbility is terminated. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> No permission verification is required when **accountId** specifies the current user.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target UIAbility.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| callback | AsyncCallback&lt;[AbilityResult](js-apis-inner-ability-abilityResult.md)&gt; | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0** and **data** is the result code and data when the UIAbility is terminated. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. <br>applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>applicable version: 10+ |
| 16000019 | No matching ability is found. <br>applicable version: 12+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>applicable version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>applicable version: 14+ |
| 16000073 | The app clone index is invalid. <br>applicable version: 12+ |
| 16000076 | The app instance key is invalid. <br>applicable version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>applicable version: 14+ |
| 16000078 | The multi-instance is not supported. <br>applicable version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>applicable version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>applicable version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let accountId = 100;

    try {
      this.context.startAbilityForResultWithAccount(want, accountId,
        (err: BusinessError, result: common.AbilityResult) => {
          if (err.code) {
            // Process service logic errors.
            console.error(`startAbilityForResultWithAccount failed, code is ${err.code}, message is ${err.message}`);
            return;
          }
          // Carry out normal service processing.
          console.info('startAbilityForResultWithAccount succeed');
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbilityForResultWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```


### startAbilityForResultWithAccount

startAbilityForResultWithAccount(want: Want, accountId: number, options: StartOptions, callback: AsyncCallback\<void\>): void

Starts a UIAbility with the account ID and start options specified and returns the result when the UIAbility is terminated. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> No permission verification is required when **accountId** specifies the current user.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target UIAbility.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| options | [StartOptions](js-apis-app-ability-startOptions.md) | Yes| Parameters used for starting the UIAbility.|
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. <br>applicable version: 9 |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. <br>applicable version: 9 |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. <br>applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>applicable version: 10+ |
| 16000019 | No matching ability is found. <br>applicable version: 12+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>applicable version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>applicable version: 14+ |
| 16000073 | The app clone index is invalid. <br>applicable version: 12+ |
| 16000076 | The app instance key is invalid. <br>applicable version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>applicable version: 14+ |
| 16000078 | The multi-instance is not supported. <br>applicable version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>applicable version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>applicable version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, StartOptions, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let accountId = 100;
    let options: StartOptions = {
      displayId: 0
    };

    try {
      this.context.startAbilityForResultWithAccount(want, accountId, options, (err: BusinessError) => {
        if (err.code) {
          // Process service logic errors.
          console.error(`startAbilityForResultWithAccount failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startAbilityForResultWithAccount succeed');
      });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbilityForResultWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```


### startAbilityForResultWithAccount

startAbilityForResultWithAccount(want: Want, accountId: number, options?: StartOptions): Promise\<AbilityResult\>

Starts a UIAbility with the account ID specified and returns the result when the UIAbility is terminated. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> No permission verification is required when **accountId** specifies the current user.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target UIAbility.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Parameters carried for starting the UIAbility, used to specify the options when the target UIAbility is started, such as the window mode. If this parameter is not passed, the default startup configuration of the system is used. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[AbilityResult](js-apis-inner-ability-abilityResult.md)&gt; | Promise that contains the **AbilityResult** parameter.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. <br>applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>applicable version: 10+ |
| 16000019 | No matching ability is found. <br>applicable version: 12+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>applicable version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>applicable version: 14+ |
| 16000073 | The app clone index is invalid. <br>applicable version: 12+ |
| 16000076 | The app instance key is invalid. <br>applicable version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>applicable version: 14+ |
| 16000078 | The multi-instance is not supported. <br>applicable version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>applicable version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>applicable version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, StartOptions, Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let accountId = 100;
    let options: StartOptions = {
      displayId: 0
    };

    try {
      this.context.startAbilityForResultWithAccount(want, accountId, options)
        .then((result: common.AbilityResult) => {
          // Carry out normal service processing.
          console.info('startAbilityForResultWithAccount succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`startAbilityForResultWithAccount failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbilityForResultWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```
### startServiceExtensionAbility

startServiceExtensionAbility(want: Want, callback: AsyncCallback\<void>): void

Starts a ServiceExtensionAbility. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API does not support app clones.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for starting the ServiceExtensionAbility.|
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>applicable version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. <br>applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>applicable version: 10+ |
| 16000019 | No matching ability is found. <br>applicable version: 12+ |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };

    try {
      this.context.startServiceExtensionAbility(want, (error: BusinessError) => {
        if (error.code) {
          // Process service logic errors.
          console.error(`startServiceExtensionAbility failed, code is ${error.code}, message is ${error.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startServiceExtensionAbility succeed');
      });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### startServiceExtensionAbility

startServiceExtensionAbility(want: Want): Promise\<void>

Starts a ServiceExtensionAbility. This API uses a promise to return the result.

> **NOTE**
>
> This API does not support app clones.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for starting the ServiceExtensionAbility.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>applicable version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. <br>applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>applicable version: 10+ |
| 16000019 | No matching ability is found. <br>applicable version: 12+ |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };

    try {
      this.context.startServiceExtensionAbility(want)
        .then(() => {
          // Carry out normal service processing.
          console.info('startServiceExtensionAbility succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`startServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### startServiceExtensionAbilityWithAccount

startServiceExtensionAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback\<void>): void

Starts a ServiceExtensionAbility with the account ID specified. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-inner-device-sys.md).
>
> No permission verification is required when **accountId** specifies the current user.
>
> This API does not support app clones.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for starting the ServiceExtensionAbility.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>applicable version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. <br>applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>applicable version: 10+ |
| 16000019 | No matching ability is found. <br>applicable version: 12+ |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let accountId = 100;

    try {
      this.context.startServiceExtensionAbilityWithAccount(want, accountId, (err: BusinessError) => {
        if (err.code) {
          // Process service logic errors.
          console.error(`startServiceExtensionAbilityWithAccount failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startServiceExtensionAbilityWithAccount succeed');
      });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startServiceExtensionAbilityWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### startServiceExtensionAbilityWithAccount

startServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise\<void>

Starts a ServiceExtensionAbility with the account ID specified. This API uses a promise to return the result.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-inner-device-sys.md).
>
> No permission verification is required when **accountId** specifies the current user.
>
> This API does not support app clones.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for starting the ServiceExtensionAbility.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>Applicable version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. <br>Applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable version: 10+ |
| 16000019 | No matching ability is found. <br>Applicable version: 12+ |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let accountId = 100;

    try {
      this.context.startServiceExtensionAbilityWithAccount(want, accountId)
        .then(() => {
          // Carry out normal service processing.
          console.info('startServiceExtensionAbilityWithAccount succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`startServiceExtensionAbilityWithAccount failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startServiceExtensionAbilityWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```
### stopServiceExtensionAbility

stopServiceExtensionAbility(want: Want, callback: AsyncCallback\<void>): void

Stops a ServiceExtensionAbility. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API does not support stopping the ServiceExtensionAbility of an app clone.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for stopping the ServiceExtensionAbility.|
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. <br>applicable version: 10+ |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>applicable version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. <br>applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>applicable version: 10+ |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };

    try {
      this.context.stopServiceExtensionAbility(want, (err: BusinessError) => {
        if (err.code) {
          // Process service logic errors.
          console.error(`stopServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('stopServiceExtensionAbility succeed');
      });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`stopServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### stopServiceExtensionAbility

stopServiceExtensionAbility(want: Want): Promise\<void>

Stops the specified ServiceExtensionAbility. This API uses a promise to return the result.

> **NOTE**
>
> This API does not support stopping the ServiceExtensionAbility of an app clone.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for stopping the ServiceExtensionAbility.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. <br>applicable version: 10+ |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>applicable version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };

    try {
      this.context.stopServiceExtensionAbility(want)
        .then(() => {
          // Carry out normal service processing.
          console.info('stopServiceExtensionAbility succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`stopServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`stopServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### stopServiceExtensionAbilityWithAccount

stopServiceExtensionAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback\<void>): void

Stops the ServiceExtensionAbility service of the specified account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - When accountId is the current user, no permission verification is required.
> - This API does not support stopping the ServiceExtensionAbility of an app clone.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for stopping the ServiceExtensionAbility.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>Applicable version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let accountId = 100;

    try {
      this.context.stopServiceExtensionAbilityWithAccount(want, accountId, (err: BusinessError) => {
        if (err.code) {
          // Process service logic errors.
          console.error(`stopServiceExtensionAbilityWithAccount failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('stopServiceExtensionAbilityWithAccount succeed');
      });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`stopServiceExtensionAbilityWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### stopServiceExtensionAbilityWithAccount

stopServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise\<void>

Stops the ServiceExtensionAbility service of the specified account. This API uses a promise to return the result.

> **NOTE**
>
> - When accountId is the current user, no permission verification is required.
> - This API does not support stopping the ServiceExtensionAbility of an app clone.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information for stopping the ServiceExtensionAbility.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. <br>Applicable version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let accountId = 100;

    try {
      this.context.stopServiceExtensionAbilityWithAccount(want, accountId)
        .then(() => {
          // Carry out normal service processing.
          console.info('stopServiceExtensionAbilityWithAccount succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`stopServiceExtensionAbilityWithAccount failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`stopServiceExtensionAbilityWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### connectServiceExtensionAbilityWithAccount

connectServiceExtensionAbilityWithAccount(want: Want, accountId: number, options: ConnectOptions): number

Connects this UIAbility to a ServiceExtensionAbility, with the account ID specified. This API can be called only on the main thread.

> **NOTE**
>
> - For details about the component startup rules, see [Intra-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).
> - When accountId is the current user, no permission verification is required.
> - This API does not support connecting to the ServiceExtensionAbility of an app clone.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Device behavior differences**: This API can be properly called on phones and tablets. If it is called on other devices, error code 16000006 is returned.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes | Want information for connecting to the ServiceExtensionAbility. |
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| options | [ConnectOptions](js-apis-inner-ability-connectOptions.md) | Yes| Instance of the callback function after the connection to the ServiceExtensionAbility is set up.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Result code of the connection.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. <br>applicable version: 10+ |
| 16000004 | Cannot start an invisible component. <br>applicable version: 10+ |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. <br>applicable version: 10+ |
| 16000008 | The crowdtesting application expires. <br>applicable version: 10+ |
| 16000053 | The ability is not on the top of the UI. <br>applicable version: 10+ |
| 16000055 | Installation-free timed out. <br>applicable version: 10+ |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled. <br>applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>applicable version: 10+ |
| 16000050 | Internal error. |

**Example**

```ts
import { UIAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let accountId = 100;
    let commRemote: rpc.IRemoteObject;
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('onConnect...');
      },
      onDisconnect(elementName) {
        console.info('onDisconnect...');
      },
      onFailed(code) {
        console.info('onFailed...');
      }
    };
    let connection: number;

    try {
      connection = this.context.connectServiceExtensionAbilityWithAccount(want, accountId, options);
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### startAbilityWithAccount

startAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback\<void\>): void

Starts a UIAbility with want and the account ID specified. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

Unlike [startAbilityForResultWithAccount](#startabilityforresultwithaccount), this API does not return the result information when the started ability exits. It applies to scenarios where the result code is not required.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> When accountId is the current user, no permission verification is required.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target UIAbility.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000019 | No matching ability is found. <br>applicable version: 12+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>applicable version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>applicable version: 14+ |
| 16000073 | The app clone index is invalid. <br>applicable version: 12+ |
| 16000076 | The app instance key is invalid. <br>applicable version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>applicable version: 14+ |
| 16000078 | The multi-instance is not supported. <br>applicable version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>applicable version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>applicable version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let accountId = 100;

    try {
      this.context.startAbilityWithAccount(want, accountId, (err: BusinessError) => {
        if (err.code) {
          // Process service logic errors.
          console.error(`startAbilityWithAccount failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startAbilityWithAccount succeed');
      });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbilityWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```


### startAbilityWithAccount

startAbilityWithAccount(want: Want, accountId: number, options: StartOptions, callback: AsyncCallback\<void\>): void

Starts a UIAbility with want, the account ID, and start options specified. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> When accountId is the current user, no permission verification is required.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target UIAbility.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| options | [StartOptions](js-apis-app-ability-startOptions.md) | Yes | Parameters carried for starting the UIAbility, used to specify the options when the target UIAbility is started, such as the window mode. |
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. <br>Applicable version: 9 |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. <br>Applicable version: 9 |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. <br>Applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable version: 10+ |
| 16000019 | No matching ability is found. <br>Applicable version: 12+ |
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
import { UIAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let accountId = 100;
    let options: StartOptions = {
      displayId: 0
    };

    try {
      this.context.startAbilityWithAccount(want, accountId, options, (err: BusinessError) => {
        if (err.code) {
          // Process service logic errors.
          console.error(`startAbilityWithAccount failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startAbilityWithAccount succeed');
      });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbilityWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```


### startAbilityWithAccount

startAbilityWithAccount(want: Want, accountId: number, options?: StartOptions): Promise\<void\>

Starts a UIAbility with want, the account ID, and start options specified. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> When accountId is the current user, no permission verification is required.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target UIAbility.|
| accountId | number | Yes | Account ID of the system account, which can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Parameters carried for starting the UIAbility, used to specify the options when the target UIAbility is started, such as the window mode. If this parameter is not passed, the default startup configuration of the system is used. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000019 | No matching ability is found. <br>applicable version: 12+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>applicable version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>applicable version: 14+ |
| 16000073 | The app clone index is invalid. <br>applicable version: 12+ |
| 16000076 | The app instance key is invalid. <br>applicable version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>applicable version: 14+ |
| 16000078 | The multi-instance is not supported. <br>applicable version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>applicable version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>applicable version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let accountId = 100;
    let options: StartOptions = {
      displayId: 0
    };

    try {
      this.context.startAbilityWithAccount(want, accountId, options)
        .then(() => {
          // Carry out normal service processing.
          console.info('startAbilityWithAccount succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`startAbilityWithAccount failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbilityWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### setMissionIcon

setMissionIcon(icon: image.PixelMap, callback: AsyncCallback\<void>): void

Sets an icon for this UIAbility in the mission. The maximum size of the icon is 600 MB. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| icon | image.PixelMap | Yes| Icon of the UIAbility to set.|
| callback | AsyncCallback\<void> | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202 | The application is not system-app, can not use system-api. <br>Applicable version: 10+ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let imagePixelMap: image.PixelMap;
    let color = new ArrayBuffer(4 * 6 * 4); // Create an ArrayBuffer object to store image pixels. The size of the object is (height * width * 4) bytes.
    let bufferArr = new Uint8Array(color);
    for (let i = 0; i < bufferArr.length; i += 4) {
      bufferArr[i] = 255;
      bufferArr[i+1] = 0;
      bufferArr[i+2] = 122;
      bufferArr[i+3] = 255;
    }
    image.createPixelMap(color, {
      editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 }
    }).then((data) => {
      imagePixelMap = data;
      this.context.setMissionIcon(imagePixelMap, (err: BusinessError) => {
        if (err.code) {
          console.error(`setMissionIcon failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        console.info('setMissionIcon succeed');
      });
    }).catch((err: BusinessError) => {
      console.error(`createPixelMap failed, code is ${err.code}, message is ${err.message}`);
    });
  }
}
```


### setMissionIcon

setMissionIcon(icon: image.PixelMap): Promise\<void>

Sets the icon displayed for the current UIAbility in the task. The maximum icon size is 600 MB. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| icon | image.PixelMap | Yes| Icon of the UIAbility to set.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202 | The application is not system-app, can not use system-api. <br>Applicable version: 10+ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let imagePixelMap: image.PixelMap;
    let color = new ArrayBuffer(4 * 6 * 4); // Create an ArrayBuffer object to store image pixels. The size of the object is (height * width * 4) bytes.
    let bufferArr = new Uint8Array(color);
    for (let i = 0; i < bufferArr.length; i += 4) {
      bufferArr[i] = 255;
      bufferArr[i+1] = 0;
      bufferArr[i+2] = 122;
      bufferArr[i+3] = 255;
    }
    image.createPixelMap(color, {
      editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 }
    }).then((data) => {
      imagePixelMap = data;
      this.context.setMissionIcon(imagePixelMap)
        .then(() => {
          console.info('setMissionIcon succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`setMissionIcon failed, code is ${err.code}, message is ${err.message}`);
        });
    }).catch((err: BusinessError) => {
      console.error(`createPixelMap failed, code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

### startRecentAbility

startRecentAbility(want: Want, callback: AsyncCallback&lt;void&gt;): void

Starts a UIAbility. If the UIAbility has multiple instances, the latest instance is started. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE**
>
> - For a successful launch in cross-device scenarios, the caller and target must be the same application and the application must have the ohos.permission.DISTRIBUTED_DATASYNC permission.
>
> - If **visible** of the target UIAbility is **false** in cross-application scenarios, the caller must have the ohos.permission.START_INVISIBLE_ABILITY permission.
>
> - If the specified UIAbility has multiple instances, the caller must have the ohos.permission.START_RECENT_ABILITY permission (available only for system applications) to start the latest instance.
>
> - If the caller is running in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is required (available only for system applications).

For more component startup rules, see [intra-device component startup rules (available only to system applications)](../../application-models/component-startup-rules-inner-device-sys.md) and [cross-device component startup rules (available only to system applications)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target UIAbility.|
| callback | AsyncCallback\<void> | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. <br>applicable version: 10+ |
| 202 | The application is not system-app, can not use system-api. <br>applicable version: 14+ |
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
| 16000012 | The application is controlled. <br>applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>applicable version: 10+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>applicable version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>applicable version: 14+ |
| 16000073 | The app clone index is invalid. <br>applicable version: 12+ |
| 16000076 | The app instance key is invalid. <br>applicable version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>applicable version: 14+ |
| 16000078 | The multi-instance is not supported. <br>applicable version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>applicable version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>applicable version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
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
### startRecentAbility

startRecentAbility(want: Want, options: StartOptions, callback: AsyncCallback&lt;void&gt;): void

Starts a UIAbility with the start options specified. If the UIAbility has multiple instances, the latest instance is started.  This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE**
>
> - For a successful launch in cross-device scenarios, the caller and target must be the same application and the application must have the ohos.permission.DISTRIBUTED_DATASYNC permission.
>
> - If **visible** of the target UIAbility is **false** in cross-application scenarios, the caller must have the ohos.permission.START_INVISIBLE_ABILITY permission.
>
> - If the specified UIAbility has multiple instances, the caller must have the ohos.permission.START_RECENT_ABILITY permission (available only for system applications) to start the latest instance.
>
> - If the caller is running in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is required (available only for system applications).

For more component startup rules, see [intra-device component startup rules (available only to system applications)](../../application-models/component-startup-rules-inner-device-sys.md) and [cross-device component startup rules (available only to system applications)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target UIAbility.|
| options | [StartOptions](js-apis-app-ability-startOptions.md) | Yes| Parameters used for starting the UIAbility.|
| callback | AsyncCallback\<void> | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. <br>Applicable version: 10+ |
| 202 | The application is not system-app, can not use system-api. <br>Applicable version: 14+ |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. <br>Applicable version: 9 |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. <br>Applicable version: 9 |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. <br>Applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>Applicable version: 10+ |
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
import { UIAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0
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
### startRecentAbility

startRecentAbility(want: Want, options?: StartOptions): Promise&lt;void&gt;

Starts a UIAbility. If the UIAbility has multiple instances, the latest instance is started. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE**
>
> - For a successful launch in cross-device scenarios, the caller and target must be the same application and the application must have the ohos.permission.DISTRIBUTED_DATASYNC permission.
>
> - If **visible** of the target UIAbility is **false** in cross-application scenarios, the caller must have the ohos.permission.START_INVISIBLE_ABILITY permission.
>
> - If the specified UIAbility has multiple instances, the caller must have the ohos.permission.START_RECENT_ABILITY permission (available only for system applications) to start the latest instance.
>
> - If the caller is running in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is required (available only for system applications).

For more component startup rules, see [intra-device component startup rules (available only to system applications)](../../application-models/component-startup-rules-inner-device-sys.md) and [cross-device component startup rules (available only to system applications)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target UIAbility.|
| options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Parameters carried for starting the UIAbility, used to specify the options when the target UIAbility is started, such as the window mode. If this parameter is not passed, the default startup configuration of the system is used. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. <br>applicable version: 10+ |
| 202 | The application is not system-app, can not use system-api. <br>applicable version: 14+ |
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
| 16000012 | The application is controlled. <br>applicable version: 10+ |
| 16000013 | The application is controlled by EDM. <br>applicable version: 10+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. <br>applicable version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>applicable version: 14+ |
| 16000073 | The app clone index is invalid. <br>applicable version: 12+ |
| 16000076 | The app instance key is invalid. <br>applicable version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>applicable version: 14+ |
| 16000078 | The multi-instance is not supported. <br>applicable version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>applicable version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>applicable version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0,
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

### startAbilityByCallWithAccount<sup>10+</sup>

startAbilityByCallWithAccount(want: Want, accountId: number): Promise&lt;Caller&gt;

Starts a UIAbility with the account ID specified and obtains the caller object for communicating with the UIAbility. This API can be called only on the main thread. This API uses a promise to return the result.

This API cannot be used to start the UIAbility with the launch type set to [specified](../../application-models/uiability-launch-type.md#specified).

Observe the following when using this API:
 - If an application needs to call this API to start a UIAbility that belongs to another user, it must have the ohos.permission.ABILITY_BACKGROUND_COMMUNICATION and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permissions.
 - If an application running in the background needs to call this API to start a UIAbility, it must have the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission.
 - If **exported** of the target UIAbility is **false** in cross-application scenarios, the caller must have the ohos.permission.START_INVISIBLE_ABILITY permission.
 - The usage rules of this API differ between the same-device and cross-device scenarios. For details, see [intra-device component startup rules (available only to system applications)](../../application-models/component-startup-rules-inner-device-sys.md) and [cross-device component startup rules (available only to system applications)](../../application-models/component-startup-rules-cross-device-sys.md).

**Required permissions**: ohos.permission.ABILITY_BACKGROUND_COMMUNICATION and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Information about the UIAbility to start, including **abilityName**, **moduleName**, **bundleName**, **deviceId** (optional), and **parameters** (optional). If **deviceId** is left blank or null, the local UIAbility is started. If **parameters** is left blank or null, the UIAbility is started in the background.|
| accountId | number | Yes | Account ID of the system account. The value -1 indicates the current active user. It can be obtained by [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[Caller](js-apis-app-ability-uiAbility.md#caller)&gt; | Promise object used to return the caller object for communication. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000050 | Internal error. |
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
import { UIAbility, Want, Caller } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
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
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

### startAbilityAsCaller<sup>10+</sup>

startAbilityAsCaller(want: Want, callback: AsyncCallback\<void>): void

Starts a UIAbility with the caller information specified. The caller information is carried in **want** and identified at the system service layer. The UIAbility can obtain the caller information from the **want** parameter in the **onCreate** lifecycle callback. When this API is used to start a UIAbility, the caller information carried in **want** is not overwritten by the current application information. The system service layer can obtain the initial caller information. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (Available Only to System Applications)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes| Want information about the target UIAbility.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
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
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    // want contains the information about the caller who starts the application.
    let localWant: Want = want;
    localWant.bundleName = 'com.example.demo';
    localWant.moduleName = 'entry';
    localWant.abilityName = 'TestAbility';

    // Start a new ability using the caller information.
    this.context.startAbilityAsCaller(localWant, (err) => {
      if (err.code) {
        console.error(`startAbilityAsCaller failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('startAbilityAsCaller success.');
      }
    });
  }
}
```

### startAbilityAsCaller<sup>10+</sup>

startAbilityAsCaller(want: Want, options: StartOptions, callback: AsyncCallback\<void>): void

Starts a UIAbility with the caller information and start options specified. The caller information is carried in **want** and identified at the system service layer. The UIAbility can obtain the caller information from the **want** parameter in the **onCreate** lifecycle callback. When this API is used to start a UIAbility, the caller information carried in **want** is not overwritten by the current application information. The system service layer can obtain the initial caller information. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes| Want information about the target UIAbility.|
| options | [StartOptions](js-apis-app-ability-startOptions.md) | Yes| Parameters used for starting the UIAbility.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|
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
| 16000071 | App clone is not supported. <br>applicable version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>applicable version: 14+ |
| 16000073 | The app clone index is invalid. <br>applicable version: 12+ |
| 16000076 | The app instance key is invalid. <br>applicable version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>applicable version: 14+ |
| 16000078 | The multi-instance is not supported. <br>applicable version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>applicable version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>applicable version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want, AbilityConstant, StartOptions } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    // want contains the information about the caller who starts the application.
    let localWant: Want = want;
    localWant.bundleName = 'com.example.demo';
    localWant.moduleName = 'entry';
    localWant.abilityName = 'TestAbility';
    let option: StartOptions = {
      displayId: 0
    };

    // Start a new ability using the caller information.
    this.context.startAbilityAsCaller(localWant, option, (err) => {
      if (err.code) {
        console.error(`startAbilityAsCaller failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('startAbilityAsCaller success.');
      }
    });
  }
}
```

### startAbilityAsCaller<sup>10+</sup>

startAbilityAsCaller(want: Want, options?: StartOptions): Promise\<void>

Starts a UIAbility with the caller information specified. The caller information is carried in **want** and identified at the system service layer. The UIAbility can obtain the caller information from the **want** parameter in the **onCreate** lifecycle callback. When this API is used to start a UIAbility, the caller information carried in **want** is not overwritten by the current application information. The system service layer can obtain the initial caller information. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes| Want information about the target UIAbility.|
| options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Parameters carried for starting the UIAbility, used to specify the options when the target UIAbility is started, such as the window mode. If this parameter is not passed, the default startup configuration of the system is used. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
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
| 16000071 | App clone is not supported. <br>applicable version: 14+ |
| 16000072 | App clone or multi-instance is not supported. <br>applicable version: 14+ |
| 16000073 | The app clone index is invalid. <br>applicable version: 12+ |
| 16000076 | The app instance key is invalid. <br>applicable version: 14+ |
| 16000077 | The number of app instances reaches the limit. <br>applicable version: 14+ |
| 16000078 | The multi-instance is not supported. <br>applicable version: 14+ |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. <br>applicable version: 14+ |
| 16000080 | Creating a new instance is not supported. <br>applicable version: 14+ |
| 16200001 | The caller has been released. |

**Example**

```ts
import { UIAbility, Want, AbilityConstant, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
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
        console.error(`startAbilityAsCaller failed, code is ${err.code}, message is ${err.message}`);
      });
  }
}
```

### requestModalUIExtension<sup>11+</sup>

requestModalUIExtension(pickerWant: Want): Promise\<void>

Requests the specified foreground application to start the UIExtensionAbility of the corresponding type. This API uses a promise to return the result. It can be called only on the main thread.

The foreground application is specified by **bundleName** in **want.parameters**. If **bundleName** is left unspecified, or if the application specified by **bundleName** is not running in the foreground or does not exist, the UIExtensionAbility is directly started on the system UI. The UIExtensionAbility to start is determined by the combination of the **bundleName**, **abilityName**, and **moduleName** fields in **want**, and its type is determined by the **ability.want.params.uiExtensionType** field in **want.parameters**.

Before starting the UIExtensionAbility, ensure that the foreground application has finished page initialization. Otherwise, the UIExtensionAbility fails to start and the error message "uiContent is nullptr" is displayed. The application can determine the time to start the UIExtensionAbility by listening for the page loading status. After the page initialization is successful, the key log information "UIContentImpl: focus again" is recorded.

> **NOTE**
>
> For details about the component startup rules, see [intra-device component startup rules (available only to system applications)](../../application-models/component-startup-rules-inner-device-sys.md) and [cross-device component startup rules (available only to system applications)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> This API does not support app clones.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| pickerWant | [Want](js-apis-app-ability-want.md)  | Yes| Want information used to start the UIExtensionAbility.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. <br>applicable version: 11 |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. <br>applicable version: 11 |
| 16000002 | Incorrect ability type. <br>applicable version: 11 |
| 16000004 | Cannot start an invisible component. <br>applicable version: 11 |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. <br>applicable version: 11 |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'com.example.myapplication.UIExtAbility',
      moduleName: 'entry_test',
      parameters: {
        'bundleName': 'com.example.myapplication',
        // Same as the type configured for com.example.myapplication.UIExtAbility
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };

    try {
      this.context.requestModalUIExtension(want)
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

### requestModalUIExtension<sup>11+</sup>
requestModalUIExtension(pickerWant: Want, callback: AsyncCallback\<void>): void

Requests the specified foreground application to start the UIExtensionAbility of the corresponding type. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

The foreground application is specified by **bundleName** in **want.parameters**. If **bundleName** is left unspecified, or if the application specified by **bundleName** is not running in the foreground or does not exist, the UIExtensionAbility is directly started on the system UI. The UIExtensionAbility to start is determined by the combination of the **bundleName**, **abilityName**, and **moduleName** fields in **want**, and its type is determined by the **ability.want.params.uiExtensionType** field in **want.parameters**.

Before starting the UIExtensionAbility, ensure that the foreground application has finished page initialization. Otherwise, the UIExtensionAbility fails to start and the error message "uiContent is nullptr" is displayed. The application can determine the time to start the UIExtensionAbility by listening for the page loading status. After the page initialization is successful, the key log information "UIContentImpl: focus again" is recorded.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> This API does not support app clones.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| pickerWant | [Want](js-apis-app-ability-want.md)  | Yes| Want information used to start the UIExtensionAbility.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| error code ID | error message |
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. <br>applicable version: 11 |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. <br>applicable version: 11 |
| 16000002 | Incorrect ability type. <br>applicable version: 11 |
| 16000004 | Cannot start an invisible component. <br>applicable version: 11 |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. <br>applicable version: 11 |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'UIExtAbility',
      moduleName: 'entry_test',
      parameters: {
        'bundleName': 'com.example.myapplication',
        // Same as the type configured for com.example.myapplication.UIExtAbility.
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };

    try {
      this.context.requestModalUIExtension(want, (err: BusinessError) => {
        if (err.code) {
          // Handle the service logic error.
          console.error(`requestModalUIExtension failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // Execute the normal service.
        console.info('requestModalUIExtension succeed');
      });
    } catch (err) {
      // Handle the input parameter error.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`requestModalUIExtension failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### requestModalUIExtensionWithAccount

requestModalUIExtensionWithAccount(pickerWant: Want, accountId: number): Promise\<void>

Requests to start a UIExtensionAbility of the corresponding type for a specified user on a specified foreground application. The foreground application is specified by bundleName in want.parameters. If no foreground application is specified, the application specified by bundleName is not in the foreground, or the bundleName of the specified foreground application is incorrect, the UIExtensionAbility is started directly on the system UI. The UIExtensionAbility to start is determined by the bundleName, abilityName, and moduleName fields in want, and its type must be configured through the ability.want.params.uiExtensionType field in want.parameters. This operation can be called only on the main thread and provides an asynchronous callback in Promise form.

Before the foreground application starts the UIExtensionAbility, ensure that the application has completed page initialization. Otherwise, the startup fails and the error message "uiContent is nullptr" is displayed. The application can determine the timing for starting the UIExtensionAbility by listening to the page loading status. After page initialization succeeds, the key log "UIContentImpl: focus again" is displayed.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> This API does not support app clones.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Since**: 26.0.0

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| pickerWant | [Want](js-apis-app-ability-want.md)  | Yes | Want information for starting the UIExtension. |
| accountId | number | Yes | ID of the system account, which can be obtained through [getForegroundOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount-sys.md#getforegroundosaccountlocalid23). |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void> | Promise object that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed;2.Send restart message to system service failed; 3.System service failed to communicate with dependency module.4.The logical screen corresponding to the specified accountId is not in the foreground.|

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'com.example.myapplication.UIExtAbility',
      moduleName: 'entry_test',
      parameters: {
        'bundleName': 'com.example.myapplication',
        // Same as the type configured for com.example.myapplication.UIExtAbility.
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };
    // Account ID description:
    // 1. Fixed value 100 in the example.
    // 2. Obtain the ID of the foreground system account running on the specified logical display through the system account management API getForegroundOsAccountLocalId(displayId: number).
    let accountId = 100;

    try {
      this.context.requestModalUIExtensionWithAccount(want, accountId)
        .then(() => {
          // Execute normal services.
          console.info('requestModalUIExtensionWithAccount succeed');
        })
        .catch((err: BusinessError) => {
          // Process service logic errors.
          console.error(`requestModalUIExtensionWithAccount failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`requestModalUIExtensionWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### connectAbilityWithAccount<sup>(deprecated)</sup>

connectAbilityWithAccount(want: Want, accountId: number, options: ConnectOptions): number

Connects the current UIAbility to a ServiceExtensionAbility of a specified account. This API can be called only in the main thread.

> **NOTE**
>
> For details about the component startup rules, see [Intra-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-inner-device-sys.md) and [Cross-device Component Startup Rules (for System Applications Only)](../../application-models/component-startup-rules-cross-device-sys.md).
>
> When accountId is the current user, no permission verification is required.
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [connectServiceExtensionAbilityWithAccount](#connectserviceextensionabilitywithaccount) instead.
>
> This API does not support app clones.

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Device behavior differences** This API can be called normally on phones and tablets, and returns error code 16000006 on other device types.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes | Want information for connecting to the ServiceExtensionAbility. |
| accountId | number | Yes | ID of the system account, which can be obtained through [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |
| options | [ConnectOptions](js-apis-inner-ability-connectOptions.md) | Yes | Instance of the callback function invoked after the connection to the ServiceExtensionAbility is established. |

**Return value**

| Type | Description |
| -------- | -------- |
| number | Result code of the Ability connection. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | The application does not have permission to call the interface. |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |

**Example**

```ts
import { UIAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let accountId = 100;
    let commRemote: rpc.IRemoteObject;
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('onConnect...');
      },
      onDisconnect(elementName) {
        console.info('onDisconnect...');
      },
      onFailed(code) {
        console.info('onFailed...');
      }
    };
    let connection: number;

    try {
      connection = this.context.connectAbilityWithAccount(want, accountId, options);
    } catch (err) {
      // Handle the input parameter error.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectAbilityWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### disconnectAbility<sup>(deprecated)</sup>

disconnectAbility(connection: number): Promise\<void>

Disconnects from the [ServiceExtensionAbility](../../application-models/extensionability-overview.md). After the disconnection, the developer needs to set the remote object returned upon successful connection to null. This API uses a promise to return the result asynchronously. It can be called only on the main thread.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [disconnectServiceExtensionAbility](js-apis-inner-application-uiAbilityContext.md#disconnectserviceextensionability) instead.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| connection | number | Yes | ID of the connected ServiceExtensionAbility, that is, the connectionId returned by [connectAbilityWithAccount](#connectabilitywithaccountdeprecated). |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // connection is the return value of connectAbilityWithAccount.
    let connection = 1;
    let commRemote: rpc.IRemoteObject | null;

    try {
      this.context.disconnectAbility(connection).then(() => {
        commRemote = null;
        // Execute the normal service.
        console.info('disconnectAbility succeed');
      }).catch((err: BusinessError) => {
        // Handle the service logic error.
        console.error(`disconnectAbility failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      commRemote = null;
      // Handle the input parameter error.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### disconnectAbility<sup>(deprecated)</sup>

disconnectAbility(connection: number, callback: AsyncCallback\<void>): void

Disconnects from the [ServiceExtensionAbility](../../application-models/extensionability-overview.md). After the disconnection, the developer needs to set the remote object returned upon a successful connection to null. This API uses an asynchronous callback. It can be called only on the main thread.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [disconnectServiceExtensionAbility](js-apis-inner-application-uiAbilityContext.md#disconnectserviceextensionability) instead.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| connection | number | Yes | ID of the connected ServiceExtensionAbility, that is, the connectionId returned by [connectAbilityWithAccount](#connectabilitywithaccountdeprecated). |
| callback | AsyncCallback\<void> | Yes | Callback function. If the disconnection from the ServiceExtensionAbility is successful, err is undefined; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // connection is the return value of connectAbilityWithAccount.
    let connection = 1;
    let commRemote: rpc.IRemoteObject | null;

    try {
      this.context.disconnectAbility(connection, (err: BusinessError) => {
        commRemote = null;
        if (err.code) {
          // Handle the service logic error.
          console.error(`disconnectAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // Execute the normal service.
        console.info('disconnectAbility succeed');
      });
    } catch (err) {
      commRemote = null;
      // Handle the input parameter error.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```
