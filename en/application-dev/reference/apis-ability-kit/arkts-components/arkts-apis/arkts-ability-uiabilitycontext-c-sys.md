# UIAbilityContext

```TypeScript
declare class UIAbilityContext extends Context
```

UIAbilityContext provides the context environment for a [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) that needs to store its status. It inherits from Context and provides UIAbility-related configuration and APIs for operating UIAbility and ServiceExtensionAbility components. For example, you can use the APIs to start a UIAbility, terminate a UIAbility to which the UIAbilityContext belongs, and start, terminate, connect to, or disconnect from a ServiceExtensionAbility.

**Inheritance/Implementation:** UIAbilityContext extends [Context](arkts-ability-context-c.md)

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## connectAbilityWithAccount

```TypeScript
connectAbilityWithAccount(want: Want, accountId: number, options: ConnectOptions): number
```

Connects this UIAbility to a ServiceExtensionAbility, with the account ID specified. This API can be called only on the main thread. This API can be properly called on phones and tablets. If it is called on other devices, error code 16000006 is returned.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [connectServiceExtensionAbilityWithAccount](#connectserviceextensionabilitywithaccount)(want: Want, accountId: number, options: ConnectOptions)

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |
| options | [ConnectOptions](arkts-ability-connectoptions-connectoptions-i.md) | Yes | Instance of the callback function after the connection to the ServiceExtensionAbility is set up. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Result code of the connection. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type.<br>**Applicable version:** 10 and later |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed.<br>**Applicable version:** 10 and later |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires.<br>**Applicable version:** 10 and later |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI.<br>**Applicable version:** 10 and later |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out.<br>**Applicable version:** 10 and later |

**Examples**

```TypeScript
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

## connectServiceExtensionAbilityWithAccount

```TypeScript
connectServiceExtensionAbilityWithAccount(want: Want, accountId: number, options: ConnectOptions): number
```

Connects this UIAbility to a ServiceExtensionAbility, with the account ID specified. This API can be called only on the main thread. This API can be properly called on phones and tablets. If it is called on other devices, error code 16000006 is returned.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |
| options | [ConnectOptions](arkts-ability-connectoptions-connectoptions-i.md) | Yes | Instance of the callback function after the connection to the ServiceExtensionAbility is set up. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Result code of the connection. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type.<br>**Applicable version:** 10 and later |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed.<br>**Applicable version:** 10 and later |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires.<br>**Applicable version:** 10 and later |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI.<br>**Applicable version:** 10 and later |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out.<br>**Applicable version:** 10 and later |

**Examples**

```TypeScript
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

## disconnectAbility

```TypeScript
disconnectAbility(connection: number, callback: AsyncCallback<void>): void
```

Disconnects from a [ServiceExtensionAbility](../../../application-models/extensionability-overview.md). Once the connection is terminated, set the remote object, which is returned when the connection is established, to null. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [disconnectServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#disconnectserviceextensionability)(connection: number, callback: AsyncCallback&lt;void&gt;)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connection | number | Yes | ID of the connected ServiceExtensionAbility, that is, **connectionId** returned by [connectServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#connectserviceextensionability). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed. 2.System service failed to communicate with dependency module. |

**Examples**

```TypeScript
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

<a id="disconnectability-1"></a>

## disconnectAbility

```TypeScript
disconnectAbility(connection: number): Promise<void>
```

Disconnects from a [ServiceExtensionAbility](../../../application-models/extensionability-overview.md). Once the connection is terminated, set the remote object, which is returned when the connection is established, to null. This API uses a promise to return the result. It can be called only on the main thread.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [disconnectServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#disconnectserviceextensionability)(connection: number)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connection | number | Yes | ID of the connected ServiceExtensionAbility, that is, **connectionId** returned by [connectServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#connectserviceextensionability). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed. 2.System service failed to communicate with dependency module. |

**Examples**

```TypeScript
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

## requestModalUIExtension

```TypeScript
requestModalUIExtension(pickerWant: Want, callback: AsyncCallback<void>): void
```

Requests the specified foreground application to start the UIExtensionAbility of the corresponding type. This API uses an asynchronous callback to return the result. It can be called only on the main thread. The foreground application is specified by **bundleName** in **want.parameters**. If **bundleName** is left unspecified, or if the application specified by **bundleName** is not running in the foreground or does not exist, the UIExtensionAbility is directly started on the system UI. The UIExtensionAbility to start is determined by the combination of the **bundleName**, **abilityName**, and **moduleName** fields in **want**, and its type is determined by the **ability.want.params.uiExtensionType** field in **want.parameters**. Before starting the UIExtensionAbility, ensure that the foreground application has finished page initialization. Otherwise, the UIExtensionAbility fails to start and the error message "uiContent is nullptr" is displayed. The application can determine the time to start the UIExtensionAbility by listening for the page loading status. After the page initialization is successful, the key log information "UIContentImpl: focus again" is recorded.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pickerWant | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information used to start the UIExtensionAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface.<br>**Applicable version:** 11 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist.<br>**Applicable version:** 11 |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type.<br>**Applicable version:** 11 |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 11 |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released.<br>**Applicable version:** 11 |

**Examples**

```TypeScript
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

<a id="requestmodaluiextension-1"></a>

## requestModalUIExtension

```TypeScript
requestModalUIExtension(pickerWant: Want): Promise<void>
```

Requests the specified foreground application to start the UIExtensionAbility of the corresponding type. This API uses a promise to return the result. It can be called only on the main thread. The foreground application is specified by **bundleName** in **want.parameters**. If **bundleName** is left unspecified, or if the application specified by **bundleName** is not running in the foreground or does not exist, the UIExtensionAbility is directly started on the system UI. The UIExtensionAbility to start is determined by the combination of the **bundleName**, **abilityName**, and **moduleName** fields in **want**, and its type is determined by the **ability.want.params.uiExtensionType** field in **want.parameters**. Before starting the UIExtensionAbility, ensure that the foreground application has finished page initialization. Otherwise, the UIExtensionAbility fails to start and the error message "uiContent is nullptr" is displayed. The application can determine the time to start the UIExtensionAbility by listening for the page loading status. After the page initialization is successful, the key log information "UIContentImpl: focus again" is recorded.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pickerWant | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information used to start the UIExtensionAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface.<br>**Applicable version:** 11 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist.<br>**Applicable version:** 11 |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type.<br>**Applicable version:** 11 |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 11 |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released.<br>**Applicable version:** 11 |

**Examples**

```TypeScript
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

## requestModalUIExtensionWithAccount

```TypeScript
requestModalUIExtensionWithAccount(pickerWant: Want, accountId: number): Promise<void>
```

Requests the specified foreground application to start the UIExtensionAbility of the corresponding type for the specified user. This API uses a promise to return the result. It can be called only on the main thread. The foreground application is specified by **bundleName** in **want.parameters**. If **bundleName** is left unspecified, or if the application specified by **bundleName** is not running in the foreground or does not exist, the UIExtensionAbility is directly started on the system UI. The UIExtensionAbility to start is determined by the combination of the **bundleName**, **abilityName**, and **moduleName** fields in **want**, and its type is determined by the **ability.want.params.uiExtensionType** field in **want.parameters**.

Before starting the UIExtensionAbility, ensure that the foreground application has finished page initialization. Otherwise, the UIExtensionAbility fails to start and the error message "uiContent is nullptr" is displayed. The application can determine the time to start the UIExtensionAbility by listening for the page loading status. After the page initialization is successful, the key log information "UIContentImpl: focus again" is recorded.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 26.0.0

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pickerWant | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information used to start the UIExtensionAbility. |
| accountId | number | Yes | The account to request. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1.Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. 4.The logical screen corresponding to the specified accountId is not in the foreground. |

**Examples**

```TypeScript
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

## setMissionIcon

```TypeScript
setMissionIcon(icon: image.PixelMap, callback: AsyncCallback<void>): void
```

Sets an icon for this UIAbility in the mission. The maximum size of the icon is 600 MB. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| icon | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | Icon of the UIAbility to set. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api.<br>**Applicable version:** 10 and later |

**Examples**

```TypeScript
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

<a id="setmissionicon-1"></a>

## setMissionIcon

```TypeScript
setMissionIcon(icon: image.PixelMap): Promise<void>
```

Sets an icon for this UIAbility in the mission. The maximum size of the icon is 600 MB. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| icon | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | Icon of the UIAbility to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api.<br>**Applicable version:** 10 and later |

**Examples**

```TypeScript
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

## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, callback: AsyncCallback<void>): void
```

Starts a UIAbility with the caller information specified. The caller information is carried in **want** and identified at the system service layer. The UIAbility can obtain the caller information from the **want** parameter in the **onCreate** lifecycle callback. When this API is used to start a UIAbility, the caller information carried in **want** is not overwritten by the current application information. The system service layer can obtain the initial caller information. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

<a id="startabilityascaller-1"></a>

## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

Starts a UIAbility with the caller information and start options specified. The caller information is carried in **want** and identified at the system service layer. The UIAbility can obtain the caller information from the **want** parameter in the **onCreate** lifecycle callback. When this API is used to start a UIAbility, the caller information carried in **want** is not overwritten by the current application information. The system service layer can obtain the initial caller information. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | Yes | Parameters used for starting the UIAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

<a id="startabilityascaller-2"></a>

## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, options?: StartOptions): Promise<void>
```

Starts a UIAbility with the caller information specified. The caller information is carried in **want** and identified at the system service layer. The UIAbility can obtain the caller information from the **want** parameter in the **onCreate** lifecycle callback. When this API is used to start a UIAbility, the caller information carried in **want** is not overwritten by the current application information. The system service layer can obtain the initial caller information. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Parameters used for starting the UIAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

## startAbilityByCallWithAccount

```TypeScript
startAbilityByCallWithAccount(want: Want, accountId: number): Promise<Caller>
```

Starts a UIAbility with the account ID specified and obtains the caller object for communicating with the UIAbility. This API can be called only on the main thread. This API uses a promise to return the result. This API cannot be used to start the UIAbility with the launch type set to [specified](../../../application-models/uiability-launch-type.md#specified). Observe the following when using this API:

- If an application needs to call this API to start a UIAbility that belongs to another user, it must have the  
ohos.permission.ABILITY_BACKGROUND_COMMUNICATION and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permissions.  
- If an application running in the background needs to call this API to start a UIAbility, it must have the  
ohos.permission.START_ABILITIES_FROM_BACKGROUND permission.  
- If **exported** of the target UIAbility is **false** in cross-application scenarios, the caller must have the  
ohos.permission.START_INVISIBLE_ABILITY permission.  
- The rules for using this API in the same-device and cross-device scenarios are different. For details, see [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 10

**Required permissions:** ohos.permission.ABILITY_BACKGROUND_COMMUNICATION and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Information about the UIAbility to start, including **abilityName**, **moduleName**, **bundleName**, **deviceId** (optional), and **parameters** (optional). If **deviceId** is left blank or null, the local UIAbility is started. If **parameters** is left blank or null, the UIAbility is started in the background. |
| accountId | number | Yes | ID of a system account. The value **-1** indicates the current user. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Caller](arkts-ability-app-ability-uiability-caller-i.md)&gt; | Promise used to return the caller object to communicate with. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

## startAbilityForResultWithAccount

```TypeScript
startAbilityForResultWithAccount(want: Want, accountId: number, callback: AsyncCallback<AbilityResult>): void
```

Starts a UIAbility with the account ID specified and returns the result when the UIAbility is terminated. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0** and **data** is the result code and data when the UIAbility is terminated. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

<a id="startabilityforresultwithaccount-1"></a>

## startAbilityForResultWithAccount

```TypeScript
startAbilityForResultWithAccount(
    want: Want,
    accountId: number,
    options: StartOptions,
    callback: AsyncCallback<void>
  ): void
```

Starts a UIAbility with the account ID and start options specified and returns the result when the UIAbility is terminated. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | Yes | Parameters used for starting the UIAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type.<br>**Applicable version:** 9 |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden.<br>**Applicable version:** 9 |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

<a id="startabilityforresultwithaccount-2"></a>

## startAbilityForResultWithAccount

```TypeScript
startAbilityForResultWithAccount(want: Want, accountId: number, options?: StartOptions): Promise<AbilityResult>
```

Starts a UIAbility with the account ID specified and returns the result when the UIAbility is terminated. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Parameters used for starting the UIAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Promise that contains the **AbilityResult** parameter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

## startAbilityWithAccount

```TypeScript
startAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void
```

Starts a UIAbility with want and the account ID specified. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

<a id="startabilitywithaccount-1"></a>

## startAbilityWithAccount

```TypeScript
startAbilityWithAccount(want: Want, accountId: number, options: StartOptions, callback: AsyncCallback<void>): void
```

Starts a UIAbility with want, the account ID, and start options specified. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | Yes | Parameters used for starting the UIAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type.<br>**Applicable version:** 9 |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden.<br>**Applicable version:** 9 |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

<a id="startabilitywithaccount-2"></a>

## startAbilityWithAccount

```TypeScript
startAbilityWithAccount(want: Want, accountId: number, options?: StartOptions): Promise<void>
```

Starts a UIAbility with want, the account ID, and start options specified. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Parameters used for starting the UIAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

## startRecentAbility

```TypeScript
startRecentAbility(want: Want, callback: AsyncCallback<void>): void
```

Starts a UIAbility. If the UIAbility has multiple instances, the latest instance is started. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> - For a successful launch in cross-device scenarios, the caller and target must be the same application and the application must have the ohos.permission.DISTRIBUTED_DATASYNC permission.
> 
> - If **visible** of the target UIAbility is **false** in cross-application scenarios, the caller must have the ohos.permission.START_INVISIBLE_ABILITY permission.
> 
> - If the specified UIAbility has multiple instances, the caller must have the ohos.permission.START_RECENT_ABILITY permission (available only for system applications) to start the latest instance.
> 
> - If the caller is running in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is required (available only for system applications).For details about the startup rules for the components in the stage model, see [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface.<br>**Applicable version:** 10 and later |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api.<br>**Applicable version:** 14 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

<a id="startrecentability-1"></a>

## startRecentAbility

```TypeScript
startRecentAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

Starts a UIAbility with the start options specified. If the UIAbility has multiple instances, the latest instance is started. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> - For a successful launch in cross-device scenarios, the caller and target must be the same application and the application must have the ohos.permission.DISTRIBUTED_DATASYNC permission.
> 
> - If **visible** of the target UIAbility is **false** in cross-application scenarios, the caller must have the ohos.permission.START_INVISIBLE_ABILITY permission.
> 
> - If the specified UIAbility has multiple instances, the caller must have the ohos.permission.START_RECENT_ABILITY permission (available only for system applications) to start the latest instance.
> 
> - If the caller is running in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is required (available only for system applications).For details about the startup rules for the components in the stage model, see [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | Yes | Parameters used for starting the UIAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type.<br>**Applicable version:** 9 |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden.<br>**Applicable version:** 9 |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface.<br>**Applicable version:** 10 and later |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api.<br>**Applicable version:** 14 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

<a id="startrecentability-2"></a>

## startRecentAbility

```TypeScript
startRecentAbility(want: Want, options?: StartOptions): Promise<void>
```

Starts a UIAbility. If the UIAbility has multiple instances, the latest instance is started. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> - For a successful launch in cross-device scenarios, the caller and target must be the same application and the application must have the ohos.permission.DISTRIBUTED_DATASYNC permission.
> 
> - If **visible** of the target UIAbility is **false** in cross-application scenarios, the caller must have the ohos.permission.START_INVISIBLE_ABILITY permission.
> 
> - If the specified UIAbility has multiple instances, the caller must have the ohos.permission.START_RECENT_ABILITY permission (available only for system applications) to start the latest instance.
> 
> - If the caller is running in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is required (available only for system applications).For details about the startup rules for the components in the stage model, see [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Parameters used for starting the UIAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface.<br>**Applicable version:** 10 and later |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api.<br>**Applicable version:** 14 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
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

## startServiceExtensionAbility

```TypeScript
startServiceExtensionAbility(want: Want, callback: AsyncCallback<void>): void
```

Starts a ServiceExtensionAbility. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for starting the ServiceExtensionAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
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

<a id="startserviceextensionability-1"></a>

## startServiceExtensionAbility

```TypeScript
startServiceExtensionAbility(want: Want): Promise<void>
```

Starts a ServiceExtensionAbility. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for starting the ServiceExtensionAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
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

## startServiceExtensionAbilityWithAccount

```TypeScript
startServiceExtensionAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void
```

Starts a ServiceExtensionAbility with the account ID specified. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for starting the ServiceExtensionAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
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

<a id="startserviceextensionabilitywithaccount-1"></a>

## startServiceExtensionAbilityWithAccount

```TypeScript
startServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise<void>
```

Starts a ServiceExtensionAbility with the account ID specified. This API uses a promise to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for starting the ServiceExtensionAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
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

## stopServiceExtensionAbility

```TypeScript
stopServiceExtensionAbility(want: Want, callback: AsyncCallback<void>): void
```

Stops a ServiceExtensionAbility. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for stopping the ServiceExtensionAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface.<br>**Applicable version:** 10 and later |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled.<br>**Applicable version:** 10 and later |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM.<br>**Applicable version:** 10 and later |

**Examples**

```TypeScript
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

<a id="stopserviceextensionability-1"></a>

## stopServiceExtensionAbility

```TypeScript
stopServiceExtensionAbility(want: Want): Promise<void>
```

Stops a ServiceExtensionAbility in the same application. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for stopping the ServiceExtensionAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface.<br>**Applicable version:** 10 and later |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |

**Examples**

```TypeScript
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

## stopServiceExtensionAbilityWithAccount

```TypeScript
stopServiceExtensionAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void
```

Stops a ServiceExtensionAbility with the account ID specified in the same application. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for stopping the ServiceExtensionAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **code** in **err** is **0**. Otherwise, **err** contains the corresponding error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |

**Examples**

```TypeScript
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

<a id="stopserviceextensionabilitywithaccount-1"></a>

## stopServiceExtensionAbilityWithAccount

```TypeScript
stopServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise<void>
```

Stops a ServiceExtensionAbility with the account ID specified in the same application. This API uses a promise to return the result.

> **NOTE:** 
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 9

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for stopping the ServiceExtensionAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |

**Examples**

```TypeScript
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
