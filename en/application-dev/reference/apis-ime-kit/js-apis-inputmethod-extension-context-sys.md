# @ohos.InputMethodExtensionContext (InputMethodExtensionContext) (System API)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4c244f2ed12456a4c6059eccff764e442d7872b9 translatedAt=2026-09-02T11:45:08.752Z pushedAt=2026-09-08T08:44:02.104Z -->

The **InputMethodExtensionContext** module is the context of **InputMethodExtensionAbility**. It inherits from **ExtensionContext** and provides the capabilities and APIs (system APIs) of **InputMethodExtensionAbility**.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with the superscript to indicate their earliest API version.
> The APIs of this module can be used only in the stage model.
> The APIs of this module are system APIs.

## Modules to Import

```ts
import { InputMethodExtensionContext } from '@kit.IMEKit';
```

## Usage Instructions

Before using the features of **InputMethodExtensionContext**, obtain an instance through an **InputMethodExtensionAbility** child class.

```ts
import { InputMethodExtensionAbility, InputMethodExtensionContext } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';

class InputMethodExtAbility extends InputMethodExtensionAbility {
  onCreate(want: Want): void {
    console.info('onCreate, want:' + want.abilityName);
  }
}
```

## InputMethodExtensionContext

**InputMethodExtensionContext** is the context of **InputMethodExtensionAbility**. It inherits from **ExtensionContext** and is used to operate the lifecycle and state related to input method extension.

### terminateSelf<sup>(deprecated)</sup>

terminateSelf(callback: AsyncCallback&lt;void&gt;): void

Destroys the input method ExtensionAbility. Uses an asynchronous callback.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [destroy](./js-apis-inputmethod-extension-context.md#destroy) instead.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This API is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. When the input method application is destroyed successfully, **err** is **undefined**; otherwise, it is an error object. |

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    this.context.terminateSelf((error: BusinessError) => {
      if (error.code) {
        console.error(`terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
        return;
      }
      console.info('terminateSelf succeed');
    });
  }
}
```

### terminateSelf<sup>(deprecated)</sup>

terminateSelf(): Promise&lt;void&gt;

Destroys the input method ExtensionAbility. Uses a promise for asynchronous callback.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [destroy](./js-apis-inputmethod-extension-context.md#destroy) instead.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This API is a system API.

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    this.context.terminateSelf().then(() => {
      console.info('terminateSelf succeed');
    }).catch((error: BusinessError) => {
      console.error(`terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```

### startAbilityWithAccount<sup>(deprecated)</sup>

startAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback&lt;void&gt;): void

Starts the target application with the specified account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. No alternative API is available.

**Model restriction:** This API can be used only in the stage model.

**Required Permission:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This API is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Used to specify the Want type information of the target application. |
| accountId | number | Yes | ID of the target system account. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. If the target application is started successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes**

For details about the following error codes, refer to [Input Method Framework Error Codes](errorcode-inputmethod-framework.md), [Ability Error Codes](../apis-ability-kit/errorcode-ability.md), and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | not system application. |
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
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let accountId = 100;
    this.context.startAbilityWithAccount(want, accountId, (error: BusinessError) => {
      if (error.code) {
        console.error(`startAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
        return;
      }
      console.info('startAbilityWithAccount succeed');
    });
  }
}
```

### startAbilityWithAccount<sup>(deprecated)</sup>

startAbilityWithAccount(want: Want, accountId: number): Promise&lt;void&gt;

Starts the target application with the specified account. Uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. No alternative API is available.

**Model restriction:** This API can be used only in the stage model.

**Required Permission:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This API is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Used to specify the Want type information of the target application. |
| accountId | number | Yes | ID of the target system account. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, refer to [Input Method Framework Error Codes](errorcode-inputmethod-framework.md), [Ability Error Codes](../apis-ability-kit/errorcode-ability.md), and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | not system application. |
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
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let accountId = 100;
    this.context.startAbilityWithAccount(want, accountId).then(() => {
      console.info('startAbilityWithAccount succeed');
    }).catch((error: BusinessError) => {
      console.error(`startAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```

### connectAbility<sup>(deprecated)</sup>

connectAbility(want: Want, options: ConnectOptions): number

Connects the current ability to a **ServiceExtensionAbility**.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. No alternative API is available. Input method applications are not advised to actively connect to a **ServiceExtensionAbility**. To communicate with system components, use the [sendPrivateCommand](js-apis-inputmethodengine.md#sendprivatecommand12) or [on('privateCommand')](js-apis-inputmethodengine.md#onprivatecommand12) private command channel.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This API is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Used to specify the Want type information of the target **ServiceExtensionAbility**. |
| options | [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) | Yes | Connection callback, used to return the information about successful connection, interruption, or failure. |

**Return value**

| Type | Description |
| -------- | -------- |
| number | Numeric identifier of the connection, which the caller passes in when performing a disconnection later. |

**Error codes**

For details about the following error codes, refer to [Input Method Framework Error Codes](errorcode-inputmethod-framework.md), [Ability Error Codes](../apis-ability-kit/errorcode-ability.md), and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                |
| -------- | ------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist.                   |
| 16000002 | Incorrect ability type.<br>Applicable Version: 10+                                 |
| 16000004 | Cannot start an invisible component.<br>Applicable Version: 10+                    |
| 16000005 | The specified process does not have the permission.     |
| 16000006 | Cross-user operations are not allowed.<br>Applicable Version: 10+                  |
| 16000008 | The crowdtesting application expires.<br>Applicable Version: 10+                   |
| 16000011 | The context does not exist.                             |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.                                         |
| 16000053 | The ability is not on the top of the UI.<br>Applicable Version: 10+                |
| 16000055 | Installation-free timed out.<br>Applicable Version: 10+                           |

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
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
      connection = this.context.connectAbility(want, options);
    } catch (paramError) {
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

### connectAbilityWithAccount<sup>(deprecated)</sup>

connectAbilityWithAccount(want: Want, accountId: number): number

Connects to a **ServiceExtensionAbility** with the specified account.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. No alternative API is available.

**Model restriction:** This API can be used only in the stage model.

**Required Permission:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This API is a system API.

**Parameters**

| Parameter Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Used to specify the Want type information of the target **ServiceExtensionAbility**. |
| accountId | number | Yes | ID of the target system account. |

**Return value**

| Type | Description |
| -------- | -------- |
| number | Numeric identifier of the connection, which the caller passes in when performing a disconnection later. |

**Error codes**

For details about the following error codes, refer to [Input Method Framework Error Code](errorcode-inputmethod-framework.md), [Ability Error Codes](../apis-ability-kit/errorcode-ability.md), and [Universal Error Codes](../errorcode-universal.md).

| Error Code ID | Error Message                                                |
| -------- | ------------------------------------------------------- |
| 201      | The application does not have permission to call the interface. |
| 202      | not system application. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist.                   |
| 16000002 | Incorrect ability type.<br>Applicable Version: 10+                                 |
| 16000004 | Cannot start an invisible component.<br>Applicable Version: 10+                    |
| 16000005 | The specified process does not have the permission.     |
| 16000006 | Cross-user operations are not allowed.<br>Applicable Version: 10+                  |
| 16000008 | The crowdtesting application expires.<br>Applicable Version: 10+                   |
| 16000011 | The context does not exist.                             |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.                                         |
| 16000053 | The ability is not on the top of the UI. <br>Applicable Version: 10+               |
| 16000055 | Installation-free timed out.<br>Applicable Version: 10+                            |

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let accountId = 100;
    let connection: number;

    try {
      connection = this.context.connectAbilityWithAccount(want, accountId);
    } catch (paramError) {
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

### connectServiceExtensionAbility<sup>(deprecated)</sup>

connectServiceExtensionAbility(want: Want, options: ConnectOptions): number

Connects the current ability to a **ServiceExtensionAbility**.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. No alternative API is available. Input method applications are not advised to actively connect to a **ServiceExtensionAbility**. To communicate with system components, use the [sendPrivateCommand](js-apis-inputmethodengine.md#sendprivatecommand12) or [on('privateCommand')](js-apis-inputmethodengine.md#onprivatecommand12) private command channel.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This API is a system API.

**Parameters**

| Parameter Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Used to specify the Want type information of the target **ServiceExtensionAbility**. |
| options | [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) | Yes | Connection callback, used to return the information about successful connection, interruption, or failure. |

**Return value**

| Type | Description |
| -------- | -------- |
| number | Numeric identifier of the connection, which the caller passes in when performing a disconnection later. |

**Error codes**

For details about the following error codes, refer to [Input Method Framework Error Codes](errorcode-inputmethod-framework.md), [Ability Error Codes](../apis-ability-kit/errorcode-ability.md), and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                |
| -------- | ------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist.                   |
| 16000002 | Incorrect ability type.<br>Applicable version: 10+                                 |
| 16000004 | Cannot start an invisible component.<br>Applicable version: 10+                    |
| 16000005 | The specified process does not have the permission.     |
| 16000006 | Cross-user operations are not allowed.<br>Applicable version: 10+                  |
| 16000008 | The crowdtesting application expires.<br>Applicable version: 10+                   |
| 16000011 | The context does not exist.                             |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.                                         |
| 16000053 | The ability is not on the top of the UI.<br>Applicable version: 10+                |
| 16000055 | Installation-free timed out.<br>Applicable version: 10+                           |

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
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
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

### disconnectAbility<sup>(deprecated)</sup>

disconnectAbility(connection: number, callback: AsyncCallback&lt;void&gt;): void

Disconnects from the **ServiceExtensionAbility**. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| connection | number | Yes | Numeric identifier of the connection, returned by **connectAbility**/**connectServiceExtensionAbility**. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. If the disconnection is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the following error codes, refer to [Input Method Framework Error Codes](errorcode-inputmethod-framework.md), [Ability Error Codes](../apis-ability-kit/errorcode-ability.md), and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject | null;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let connection = 1;
    try {
      this.context.disconnectAbility(connection, (error: BusinessError) => {
        commRemote = null;
        if (error.code) {
          console.error(`disconnectAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        console.info('disconnectAbility succeed');
      });
    } catch (paramError) {
      commRemote = null;
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

### disconnectAbility<sup>(deprecated)</sup>

disconnectAbility(connection: number): Promise&lt;void&gt;

Disconnects from the **ServiceExtensionAbility**. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This API is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| connection | number | Yes | Numeric identifier of the connection, returned by **connectAbility**/**connectServiceExtensionAbility**. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, refer to [Input Method Framework Error Codes](errorcode-inputmethod-framework.md), [Ability Error Codes](../apis-ability-kit/errorcode-ability.md), and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject | null;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let connection = 1;
    this.context.disconnectAbility(connection).then(() => {
      commRemote = null;
      console.info('disconnectAbility succeed');
    }).catch((error: BusinessError) => {
      commRemote = null;
      console.error(`disconnectAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```

### disconnectServiceExtensionAbility<sup>(deprecated)</sup>

disconnectServiceExtensionAbility(connection: number, callback: AsyncCallback&lt;void&gt;): void

Disconnects from the **ServiceExtensionAbility**. This API uses an asynchronous callback.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. No alternative API is available. It is used together with **connectServiceExtensionAbility**, both of which are deprecated. The pattern of connecting to or disconnecting from a **ServiceExtensionAbility** is not recommended.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This API is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| connection | number | Yes | Numeric identifier of the connection, returned by **connectServiceExtensionAbility**. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. If the disconnection is successful, **err** is **undefined**; otherwise, it is an error object. |

**Error codes**

For details about the following error codes, refer to [Input Method Framework Error Codes](errorcode-inputmethod-framework.md), [Ability Error Codes](../apis-ability-kit/errorcode-ability.md), and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject | null;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let connection = 1;
    try {
      this.context.disconnectServiceExtensionAbility(connection, (error: BusinessError) => {
        commRemote = null;
        if (error.code) {
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        console.info('disconnectServiceExtensionAbility succeed');
      });
    } catch (paramError) {
      commRemote = null;
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

### disconnectServiceExtensionAbility<sup>(deprecated)</sup>

disconnectServiceExtensionAbility(connection: number): Promise&lt;void&gt;

Disconnects from the **ServiceExtensionAbility**. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. No alternative API is available. It is used together with **connectServiceExtensionAbility**, both of which are deprecated. The pattern of connecting to or disconnecting from a **ServiceExtensionAbility** is not recommended.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This API is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| connection | number | Yes | Numeric identifier of the connection, returned by **connectServiceExtensionAbility**. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, refer to [Input Method Framework Error Codes](errorcode-inputmethod-framework.md), [Ability Error Codes](../apis-ability-kit/errorcode-ability.md), and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |

**Example**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject | null;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let connection = 1;
    this.context.disconnectServiceExtensionAbility(connection).then(() => {
      commRemote = null;
      console.info('disconnectServiceExtensionAbility succeed');
    }).catch((error: BusinessError) => {
      commRemote = null;
      console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```