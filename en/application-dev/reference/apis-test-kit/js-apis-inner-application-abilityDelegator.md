# AbilityDelegator

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=aee2f7468d1b3b04e493c7068f7ee7eaa8e0ca32 translatedAt=2026-08-07T09:48:03.937Z pushedAt=2026-08-07T11:31:02.470Z -->

**AbilityDelegator** is a proxy controller used to schedule and manage the UIAbility lifecycle. It listens for and manages the lifecycle changes of [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md) through **AbilityMonitor**. For example, you can obtain the current state of a UIAbility (for example, whether the UIAbility has been created or is in the foreground), obtain the UIAbility that currently has the focus, wait for the UIAbility to enter a lifecycle node (for example, the **onForeground** state), start a specified UIAbility, and set the timeout mechanism.

This module can be used to verify the correctness of lifecycle behaviors and simulate user operation sequences in UIAbility unit testing and integration testing scenarios. Note that the APIs of this module are for testing purposes only and should not be called in formal service code.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> The APIs of this module can be used only in <!--RP1-->[JsUnit](../../application-test/unittest-guidelines.md)<!--RP1End-->.

## Modules to Import

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## AbilityDelegator

### addAbilityMonitor<sup>9+</sup>

addAbilityMonitor(monitor: AbilityMonitor, callback: AsyncCallback\<void>): void

Adds an **AbilityMonitor** instance. This API uses an asynchronous callback to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| monitor  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) | Yes      | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) instance.|
| callback | AsyncCallback\<void>                                         | Yes      | Callback used to return the result. If the **AbilityMonitor** instance is added, **err** is **undefined**. Otherwise, **err** is an error object.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling AddAbilityMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Declare an AbilityDelegator object.
let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
// Create an AbilityMonitor instance and set the name of the ability to be monitored and the onAbilityCreate lifecycle callback.
let onAbilityCreateCallback = (data: UIAbility) => {
  console.info(`onAbilityCreateCallback, data: ${JSON.stringify(data)}`);
}

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityName',
  onAbilityCreate: onAbilityCreateCallback
};

// Obtain the AbilityDelegator instance.
abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
// Call the addAbilityMonitor method to add a monitor.
abilityDelegator.addAbilityMonitor(monitor, (error: BusinessError) => {
  if (error) {
    console.error(`addAbilityMonitor fail. Code: ${error.code}, message: ${error.message}`);
  }
});
```

### addAbilityMonitor<sup>9+</sup>

addAbilityMonitor(monitor: AbilityMonitor): Promise\<void>

Adds an **AbilityMonitor** instance. This API uses a promise to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) | Yes  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) instance.|

**Return value**

| Type          | Description               |
| -------------- | ------------------- |
| Promise\<void> |Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling AddAbilityMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';

let onAbilityCreateCallback = (data: UIAbility) => {
  console.info('onAbilityCreateCallback');
};

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityName',
  onAbilityCreate: onAbilityCreateCallback
};
let abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();

abilityDelegator.addAbilityMonitor(monitor).then(() => {
  console.info('addAbilityMonitor promise');
});
```

### addAbilityMonitorSync<sup>10+</sup>

addAbilityMonitorSync(monitor: AbilityMonitor): void

Adds an **AbilityMonitor** instance. This API returns the result synchronously. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) | Yes  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling AddAbilityMonitorSync failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

let onAbilityCreateCallback = (data: UIAbility) => {
  console.info('onAbilityCreateCallback');
};

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityName',
  onAbilityCreate: onAbilityCreateCallback
};

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.addAbilityMonitorSync(monitor);
```

### removeAbilityMonitor<sup>9+</sup>

removeAbilityMonitor(monitor: AbilityMonitor, callback: AsyncCallback\<void>): void

Removes an **AbilityMonitor** instance. This API uses an asynchronous callback to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) | Yes  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) instance.|
| callback | AsyncCallback\<void> | Yes | Callback used to return the result. If the **AbilityMonitor** instance is successfully deleted, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling RemoveAbilityMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

let onAbilityCreateCallback = (data: UIAbility) => {
  console.info('onAbilityCreateCallback');
};

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityName',
  onAbilityCreate: onAbilityCreateCallback
};

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.removeAbilityMonitor(monitor, (error: BusinessError) => {
  if (error) {
    console.error(`removeAbilityMonitor fail. Code: ${error.code}, message: ${error.message}`);
  }
});
```

### removeAbilityMonitor<sup>9+</sup>

removeAbilityMonitor(monitor: AbilityMonitor): Promise\<void>

Removes an **AbilityMonitor** instance. This API uses a promise to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name   | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) | Yes  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) instance.|

**Return value**

| Type          | Description               |
| -------------- | ------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling RemoveAbilityMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

let onAbilityCreateCallback = (data: UIAbility) => {
  console.info('onAbilityCreateCallback');
};

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityName',
  onAbilityCreate: onAbilityCreateCallback
};

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.removeAbilityMonitor(monitor).then(() => {
  console.info('removeAbilityMonitor promise');
});
```

### removeAbilityMonitorSync<sup>10+</sup>

removeAbilityMonitorSync(monitor: AbilityMonitor): void

Removes an **AbilityMonitor** instance. This API returns the result synchronously. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) | Yes  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling RemoveAbilityMonitorSync failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

let onAbilityCreateCallback = (data: UIAbility) => {
  console.info('onAbilityCreateCallback');
};

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityName',
  onAbilityCreate: onAbilityCreateCallback
};

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.removeAbilityMonitorSync(monitor);
```

### waitAbilityMonitor<sup>9+</sup>

waitAbilityMonitor(monitor: AbilityMonitor, callback: AsyncCallback\<UIAbility>): void

Waits for the **Ability** instance that matches the **AbilityMonitor** instance to reach the **onCreate** lifecycle state and returns the **Ability** instance. This API uses an asynchronous callback to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) | Yes  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) instance.|
| callback | AsyncCallback\<[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md)> | Yes | Callback used to return the result. If waiting for the **Ability** instance that matches the **AbilityMonitor** instance to reach the **onCreate** lifecycle state is successful, **err** is **undefined** and **data** is the **Ability** instance obtained. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling WaitAbilityMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

let onAbilityCreateCallback = (data: UIAbility) => {
  console.info(`onAbilityCreateCallback, data: ${JSON.stringify(data)}`);
}

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityName',
  onAbilityCreate: onAbilityCreateCallback
};

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.waitAbilityMonitor(monitor, (error: BusinessError, data: UIAbility) => {
  if (error) {
    console.error(`waitAbilityMonitor fail. Code: ${error.code}, message: ${error.message}`);
  } else {
    console.info('waitAbilityMonitor success.');
  }
});
```

### waitAbilityMonitor<sup>9+</sup>

waitAbilityMonitor(monitor: AbilityMonitor, timeout: number, callback: AsyncCallback\<UIAbility>): void

Waits a period of time for the **Ability** instance that matches the **AbilityMonitor** instance to reach the **onCreate** lifecycle state and returns the **Ability** instance. This API uses an asynchronous callback to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) | Yes  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) instance.|
| timeout  | number                                                       | Yes  | Maximum waiting time, in milliseconds. The default value is 5000 ms.                                |
| callback | AsyncCallback\<[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md)> | Yes | Callback used to return the result. If waiting for the **Ability** instance that matches the **AbilityMonitor** instance to reach the **onCreate** lifecycle state is successful, **err** is **undefined** and **data** is the **Ability** instance obtained. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling WaitAbilityMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Declare an AbilityDelegator object.
let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
// Set the maximum waiting time, in milliseconds.
let timeout = 100;
// Create an AbilityMonitor instance and set the name of the ability to be monitored.
let onAbilityCreateCallback = (data: UIAbility) => {
  console.info(`onAbilityCreateCallback, data: ${JSON.stringify(data)}.`);
};

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityName',
  onAbilityCreate: onAbilityCreateCallback
};

// Obtain the AbilityDelegator instance.
abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
// Call waitAbilityMonitor and pass the timeout parameter to wait for the matched ability instance.
abilityDelegator.waitAbilityMonitor(monitor, timeout, (error: BusinessError, data: UIAbility) => {
  if (error) {
    console.error(`waitAbilityMonitor fail. Code: ${error.code}, message: ${error.message}`);
  } else {
    console.info('waitAbilityMonitor success.');
  }
});
```

### waitAbilityMonitor<sup>9+</sup>

waitAbilityMonitor(monitor: AbilityMonitor, timeout?: number): Promise\<UIAbility>

Waits a period of time for the **Ability** instance that matches the **AbilityMonitor** instance to reach the **onCreate** lifecycle state and returns the **Ability** instance. This API uses a promise to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) | Yes  | [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) instance.|
| timeout | number                                                       | No  | Maximum waiting time, in milliseconds. The default value is 5000 ms.                                |

**Return value**

| Type                                                       | Description                      |
| ----------------------------------------------------------- | -------------------------- |
| Promise\<[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md)> | Promise used to return the **Ability** instance obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling WaitAbilityMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

let onAbilityCreateCallback = (data: UIAbility) => {
  console.info('onAbilityCreateCallback');
};

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityName',
  onAbilityCreate: onAbilityCreateCallback
};

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.waitAbilityMonitor(monitor).then((data: UIAbility) => {
  console.info('waitAbilityMonitor promise');
});
```

### getAppContext<sup>9+</sup>

getAppContext(): Context

Obtains the application context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type                                 | Description                                       |
| ------------------------------------- | ------------------------------------------- |
| [Context](../apis-ability-kit/js-apis-inner-application-context.md) | [Context](../apis-ability-kit/js-apis-inner-application-context.md).|

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();

let context = abilityDelegator.getAppContext();
```

### getAbilityState<sup>9+</sup>

getAbilityState(ability: UIAbility): number

Obtains the lifecycle state of an Ability.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type                                             | Mandatory| Description           |
| ------- | ------------------------------------------------- | ---- | --------------- |
| ability | [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md) | Yes  | Target ability.|

**Return value**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| number | Lifecycle state of the ability, For details about the state values, see [AbilityLifecycleState](js-apis-app-ability-abilityDelegatorRegistry.md#abilitylifecyclestate).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let ability: UIAbility;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.getCurrentTopAbility((err: BusinessError, data: UIAbility) => {
  if (err) {
    console.error(`getCurrentTopAbility fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('getCurrentTopAbility callback');
    ability = data;
    let state = abilityDelegator.getAbilityState(ability);
    console.info(`getAbilityState ${state}`);
  }
});
```

### getCurrentTopAbility<sup>9+</sup>

getCurrentTopAbility(callback: AsyncCallback\<UIAbility>): void

Obtains the top ability of this app. This API uses an asynchronous callback to return the result. It cannot be called in the worker thread. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description              |
| -------- | ------------------------------------------------------------ | ---- | ------------------ |
| callback | AsyncCallback\<[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md)> | Yes  | Callback used to return the result. If the top ability is obtained, **err** is **undefined** and **data** is the **Ability** instance obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling GetCurrentTopAbility failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let ability: UIAbility;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.getCurrentTopAbility((err: BusinessError, data: UIAbility) => {
  if (err) {
    console.error(`getCurrentTopAbility fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('getCurrentTopAbility callback');
    ability = data;
  }
});
```

### getCurrentTopAbility<sup>9+</sup>

getCurrentTopAbility(): Promise\<UIAbility>

Obtains the top ability of this app. This API uses a promise to return the result. It cannot be called in the worker thread. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type                                                       | Description                                  |
| ----------------------------------------------------------- | -------------------------------------- |
| Promise\<[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md)> | Promise used to return the top ability. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000100 | Calling GetCurrentTopAbility failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let ability: UIAbility;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.getCurrentTopAbility().then((data: UIAbility) => {
  console.info('getCurrentTopAbility promise');
  ability = data;
});
```

### startAbility<sup>9+</sup>

startAbility(want: Want, callback: AsyncCallback\<void>): void

Starts an ability. This API uses an asynchronous callback to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                  | Mandatory| Description              |
| -------- | -------------------------------------- | ---- | ------------------ |
| want     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | **Want** parameter for starting the ability.   |
| callback | AsyncCallback\<void>                   | Yes  | Callback used to return the result. If the ability is started, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
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
| 16000012 | The app is controlled. <br>Applicable versions: 10+ |
| 16000013 | The app is controlled by EDM. <br>Applicable versions: 10+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Declare an AbilityDelegator object.
let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
// Construct a Want object to specify the bundleName and abilityName of the target ability.
let want: Want = {
  bundleName: 'bundleName',
  abilityName: 'abilityName'
};

// Obtain the AbilityDelegator instance.
abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
// Call startAbility to start the specified ability.
abilityDelegator.startAbility(want, (err: BusinessError, data: void) => {
  if (err) {
    console.error(`startAbility fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('startAbility callback');
  }
});
```

### startAbility<sup>9+</sup>

startAbility(want: Want): Promise\<void>

Starts an ability. This API uses a promise to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type                                  | Mandatory| Description           |
| ------ | -------------------------------------- | ---- | --------------- |
| want   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | **Want** parameter for starting the ability.|

**Return value**

| Type          | Description               |
| -------------- | ------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
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
| 16000012 | The app is controlled. <br>Applicable versions: 10+ |
| 16000013 | The app is controlled by EDM. <br>Applicable versions: 10+ |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { Want } from '@kit.AbilityKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let want: Want = {
  bundleName: 'bundleName',
  abilityName: 'abilityName'
};

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.startAbility(want).then((data: void) => {
  console.info('startAbility promise');
});
```

### doAbilityForeground<sup>9+</sup>

doAbilityForeground(ability: UIAbility, callback: AsyncCallback\<void>): void

Schedules the lifecycle state of an ability to **Foreground**. This API uses an asynchronous callback to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                   |
| -------- | ----------------------- | ---- | ------------------------------------------------------- |
| ability  | [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md)  | Yes  | Target ability.                                        |
| callback | AsyncCallback\<void>    | Yes  | Callback used to return the result. If the ability lifecycle state is changed to **Foreground**, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling DoAbilityForeground failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let ability: UIAbility;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.getCurrentTopAbility((err: BusinessError, data: UIAbility) => {
  if (err) {
    console.error(`getCurrentTopAbility fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('getCurrentTopAbility callback');
    ability = data;
    abilityDelegator.doAbilityForeground(ability, (err: BusinessError) => {
      if (err) {
        console.error(`doAbilityForeground fail. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.info('doAbilityForeground callback');
      }
    });
  }
});
```

### doAbilityForeground<sup>9+</sup>

doAbilityForeground(ability: UIAbility): Promise\<void>

Schedules the lifecycle state of an ability to **Foreground**. This API uses a promise to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type   | Mandatory| Description           |
| ------- | ------- | ---- | --------------- |
| ability | [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md) | Yes  | Target ability.|

**Return value**

| Type             | Description                                                        |
| ----------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.        |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling DoAbilityForeground failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let ability: UIAbility;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.getCurrentTopAbility((err: BusinessError, data: UIAbility) => {
  if (err) {
    console.error(`getCurrentTopAbility fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('getCurrentTopAbility callback');
    ability = data;
    abilityDelegator.doAbilityForeground(ability).then(() => {
      console.info('doAbilityForeground promise');
    });
  }
});
```

### doAbilityBackground<sup>9+</sup>

doAbilityBackground(ability: UIAbility, callback: AsyncCallback\<void>): void

Schedules the lifecycle state of a specified ability to **Background**. This API uses an asynchronous callback to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                   |
| -------- | ----------------------- | ---- | ------------------------------------------------------- |
| ability  | [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md)  | Yes  | Target ability.                                        |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the ability lifecycle state is changed to **Background**, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling DoAbilityBackground failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let ability: UIAbility;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.getCurrentTopAbility((err: BusinessError, data: UIAbility) => {
  if (err) {
    console.error(`getCurrentTopAbility fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('getCurrentTopAbility callback');
    ability = data;
    abilityDelegator.doAbilityBackground(ability, (err: BusinessError) => {
      if (err) {
        console.error(`doAbilityBackground fail. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.info('doAbilityBackground callback');
      }
    });
  }
});
```

### doAbilityBackground<sup>9+</sup>

doAbilityBackground(ability: UIAbility): Promise\<void>

Schedules the lifecycle state of a specified ability to **Background**. This API uses a promise to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type   | Mandatory| Description           |
| ------- | ------- | ---- | --------------- |
| ability | [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md) | Yes  | Target ability.|

**Return value**

| Type             | Description                                                        |
| ----------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.                           |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling DoAbilityBackground failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let ability: UIAbility;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.getCurrentTopAbility((err: BusinessError, data: UIAbility) => {
  if (err) {
    console.error(`getCurrentTopAbility fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('getCurrentTopAbility callback');
    ability = data;
    abilityDelegator.doAbilityBackground(ability).then(() => {
      console.info('doAbilityBackground promise');
    });
  }
});
```

### printSync<sup>9+</sup>

printSync(msg: string): void

Prints log information to the unit test console.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| msg    | string | Yes  | Log string. The value contains a maximum of 10,000 characters.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let msg = 'msg';

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.printSync(msg);
```

### print

print(msg: string, callback: AsyncCallback\<void>): void

Prints log information to the unit test console. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                | Mandatory| Description              |
| -------- | -------------------- | ---- | ------------------ |
| msg      | string               | Yes  | Log string. The value contains a maximum of 10,000 characters.        |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the log information is printed to the unit test console, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let msg = 'msg';

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.print(msg, (err: BusinessError) => {
  if (err) {
    console.error(`print fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('print callback');
  }
});
```

### print

print(msg: string): Promise\<void>

Prints log information to the unit test console. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| msg    | string | Yes  | Log string. The value contains a maximum of 10,000 characters.|

**Return value**

| Type          | Description               |
| -------------- | ------------------- |
| Promise\<void> |Promise that returns no value.|

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let msg = 'msg';

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.print(msg).then(() => {
  console.info('print promise');
});
```

### executeShellCommand

executeShellCommand(cmd: string, callback: AsyncCallback\<ShellCmdResult>): void

Executes a shell command. This API uses an asynchronous callback to return the result. Multi-thread concurrent calls are not supported.

Only the following shell commands are supported: aa, bm, cp, mkdir, rm, uinput, hilog, ppwd, echo, uitest, acm, hidumper, wukong, pkill, ps, pidof.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description              |
| -------- | ------------------------------------------------------------ | ---- | ------------------ |
| cmd      | string                                                       | Yes  | Shell command string.   |
| callback | AsyncCallback\<[ShellCmdResult](js-apis-inner-application-shellCmdResult.md#shellcmdresult-1)> | Yes  | Callback used to return the result. If the shell command is executed, **err** is **undefined** and **data** is the execution result obtained. Otherwise, **err** is an error object.|

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Declare an AbilityDelegator object.
let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
// Set the shell command string to be executed.
let shellCommand = 'cmd';

// Obtain the AbilityDelegator instance and execute the shell command.
abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.executeShellCommand(shellCommand, (err: BusinessError, data: abilityDelegatorRegistry.ShellCmdResult) => {
  if (err) {
    console.error(`executeShellCommand fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('executeShellCommand callback');
  }
});
```

### executeShellCommand

executeShellCommand(cmd: string, timeoutSecs: number, callback: AsyncCallback\<ShellCmdResult>): void

Executes a shell command with the timeout period specified. This API uses an asynchronous callback to return the result. Multi-thread concurrent calls are not supported.

Only the following shell commands are supported: aa, bm, cp, mkdir, rm, uinput, hilog, ppwd, echo, uitest, acm, hidumper, wukong, pkill, ps, pidof.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name     | Type                                                        | Mandatory| Description                         |
| ----------- | ------------------------------------------------------------ | ---- | ----------------------------- |
| cmd         | string                                                       | Yes  | Shell command string.              |
| timeoutSecs | number                                                       | Yes  | Command timeout period, in seconds.|
| callback    | AsyncCallback\<[ShellCmdResult](js-apis-inner-application-shellCmdResult.md#shellcmdresult-1)> | Yes  | Callback used to return the result. If the shell command is executed, **err** is **undefined** and **data** is the execution result obtained. Otherwise, **err** is an error object.  |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let shellCommand = 'cmd';
let timeout = 100;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.executeShellCommand(shellCommand, timeout, (err: BusinessError, data: abilityDelegatorRegistry.ShellCmdResult) => {
  if (err) {
    console.error(`executeShellCommand fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('executeShellCommand callback');
  }
});
```

### executeShellCommand

executeShellCommand(cmd: string, timeoutSecs?: number): Promise\<ShellCmdResult>

Executes a shell command with the timeout period specified. This API uses a promise to return the result. Multi-thread concurrent calls are not supported.

Only the following shell commands are supported: aa, bm, cp, mkdir, rm, uinput, hilog, ppwd, echo, uitest, acm, hidumper, wukong, pkill, ps, pidof.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name     | Type  | Mandatory| Description                         |
| ----------- | ------ | ---- | ----------------------------- |
| cmd         | string | Yes  | Shell command string.              |
| timeoutSecs | number | No  | Command timeout period, in seconds. The default value is **0**, indicating that the timeout period is not set.|

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<[ShellCmdResult](js-apis-inner-application-shellCmdResult.md#shellcmdresult-1)> | Promise used to return a [ShellCmdResult](js-apis-inner-application-shellCmdResult.md#shellcmdresult-1) object.|

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let shellCommand = 'cmd';
let timeout = 100;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.executeShellCommand(shellCommand, timeout).then((data) => {
  console.info('executeShellCommand promise');
});
```

### finishTest<sup>9+</sup>

finishTest(msg: string, code: number, callback: AsyncCallback\<void>): void

Finishes the test and prints log information to the unit test console. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                | Mandatory| Description              |
| -------- | -------------------- | ---- | ------------------ |
| msg      | string               | Yes  | Log string.        |
| code     | number               | Yes  | Log code.            |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the test finishes and the log information is printed to the unit test console, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling FinishTest failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let msg = 'msg';

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.finishTest(msg, 0, (err: BusinessError) => {
  if (err) {
    console.error(`finishTest fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('finishTest callback');
  }
});
```

### finishTest<sup>9+</sup>

finishTest(msg: string, code: number): Promise\<void>

Finishes the test and prints log information to the unit test console. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| msg    | string | Yes  | Log string.|
| code   | number | Yes  | Log code.    |

**Return value**

| Type          | Description               |
| -------------- | ------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling FinishTest failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let msg = 'msg';

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.finishTest(msg, 0).then(() => {
  console.info('finishTest promise');
});
```

### addAbilityStageMonitor<sup>9+</sup>

addAbilityStageMonitor(monitor: AbilityStageMonitor, callback: AsyncCallback\<void>): void

Adds an **AbilityStageMonitor** instance to monitor the lifecycle state changes of a specified ability stage. This API uses an asynchronous callback to return the result. Multi-thread concurrent calls are not supported.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| monitor  | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) | Yes      | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) instance.|
| callback | AsyncCallback\<void>                                         | Yes      | Callback used to return the result. If the **AbilityStageMonitor** instance is added, **err** is undefined. Otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling AddAbilityStageMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.addAbilityStageMonitor({
  moduleName: 'moduleName',
  srcEntrance: 'srcEntrance',
}, (err: BusinessError) => {
  if (err) {
    console.error(`addAbilityStageMonitor fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('addAbilityStageMonitor callback');
  }
});
```

### addAbilityStageMonitor<sup>9+</sup>

addAbilityStageMonitor(monitor: AbilityStageMonitor): Promise\<void>

Adds an **AbilityStageMonitor** instance to monitor the lifecycle state changes of an ability stage. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) | Yes  | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) instance.|

**Return value**

| Type          | Description               |
| -------------- | ------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling AddAbilityStageMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.addAbilityStageMonitor({
  moduleName: 'moduleName',
  srcEntrance: 'srcEntrance',
}).then(() => {
  console.info('addAbilityStageMonitor promise');
});
```

### addAbilityStageMonitorSync<sup>10+</sup>

addAbilityStageMonitorSync(monitor: AbilityStageMonitor): void

Adds an **AbilityStageMonitor** instance to monitor the lifecycle state changes of an ability stage. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| monitor  | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) | Yes      | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling AddAbilityStageMonitorSync failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.addAbilityStageMonitorSync({
  moduleName: 'moduleName',
  srcEntrance: 'srcEntrance',
});
```

### removeAbilityStageMonitor<sup>9+</sup>

removeAbilityStageMonitor(monitor: AbilityStageMonitor, callback: AsyncCallback\<void>): void

Removes an **AbilityStageMonitor** instance from the application memory. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| monitor  | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) | Yes      | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) instance.|
| callback | AsyncCallback\<void>                                         | Yes      | Callback used to return the result. If the **AbilityStageMonitor** instance is removed, **err** is undefined. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling RemoveAbilityStageMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.removeAbilityStageMonitor({
  moduleName: 'moduleName',
  srcEntrance: 'srcEntrance',
}, (err: BusinessError) => {
  if (err) {
    console.error(`removeAbilityStageMonitor fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('removeAbilityStageMonitor callback');
  }
});
```

### removeAbilityStageMonitor<sup>9+</sup>

removeAbilityStageMonitor(monitor: AbilityStageMonitor): Promise\<void>

Removes an **AbilityStageMonitor** instance from the application memory. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) | Yes  | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) instance.|

**Return value**

| Type          | Description               |
| -------------- | ------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling RemoveAbilityStageMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.removeAbilityStageMonitor({
  moduleName: 'moduleName',
  srcEntrance: 'srcEntrance',
}).then(() => {
  console.info('removeAbilityStageMonitor promise');
});
```

### removeAbilityStageMonitorSync<sup>10+</sup>

removeAbilityStageMonitorSync(monitor: AbilityStageMonitor): void

Removes an **AbilityStageMonitor** instance from the application memory. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| monitor  | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) | Yes      | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling RemoveAbilityStageMonitorSync failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.removeAbilityStageMonitorSync({
  moduleName: 'moduleName',
  srcEntrance: 'srcEntrance',
});
```

### waitAbilityStageMonitor<sup>9+</sup>

waitAbilityStageMonitor(monitor: AbilityStageMonitor, callback: AsyncCallback\<AbilityStage>): void

Returns an **AbilityStage** instance that matches the conditions set in an **AbilityStageMonitor** instance. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| monitor  | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) | Yes      | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) instance.|
| callback | AsyncCallback\<AbilityStage>                                         | Yes      | Callback used to return the result. If the operation is successful, **err** is undefined and data is the [AbilityStage](../apis-ability-kit/js-apis-app-ability-abilityStage.md) instance obtained. Otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling WaitAbilityStageMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { AbilityStage } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.waitAbilityStageMonitor({
  moduleName: 'moduleName',
  srcEntrance: 'srcEntrance',
}, (err: BusinessError, data: AbilityStage) => {
  if (err) {
    console.error(`waitAbilityStageMonitor fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('waitAbilityStageMonitor callback');
  }
});
```

### waitAbilityStageMonitor<sup>9+</sup>

waitAbilityStageMonitor(monitor: AbilityStageMonitor, timeout?: number): Promise\<AbilityStage>

Returns an **AbilityStage** instance that matches the conditions set in an **AbilityStageMonitor** instance. You can specify the timeout period. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) | Yes  | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) instance.|
| timeout | number | No  | Maximum waiting time, in milliseconds. The default value is 5000 ms.|

**Return value**

| Type          | Description               |
| -------------- | ------------------- |
| Promise\<AbilityStage> | Promise used to return the [AbilityStage](../apis-ability-kit/js-apis-app-ability-abilityStage.md) instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling WaitAbilityStageMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { AbilityStage } from '@kit.AbilityKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.waitAbilityStageMonitor({
  moduleName: 'moduleName',
  srcEntrance: 'srcEntrance',
}).then((data: AbilityStage) => {
  console.info('waitAbilityStageMonitor promise');
});
```

### waitAbilityStageMonitor<sup>9+</sup>

waitAbilityStageMonitor(monitor: AbilityStageMonitor, timeout: number, callback: AsyncCallback\<AbilityStage>): void

Returns an **AbilityStage** instance that matches the conditions set in an **AbilityStageMonitor** instance within the specified timeout period. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| monitor | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) | Yes  | [AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) instance.|
| timeout | number | Yes  | Maximum waiting time, in milliseconds. The default value is 5000 ms.|
| callback | AsyncCallback\<AbilityStage>                                         | Yes      | Callback used to return the result. If the operation is successful, **err** is undefined and data is the [AbilityStage](../apis-ability-kit/js-apis-app-ability-abilityStage.md) instance obtained. Otherwise, **err** is an error object.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000100 | Calling WaitAbilityStageMonitor failed. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { AbilityStage } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let timeout = 100;

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.waitAbilityStageMonitor({
  moduleName: 'moduleName',
  srcEntrance: 'srcEntrance',
}, timeout, (err: BusinessError, data: AbilityStage) => {
  if (err) {
    console.error(`waitAbilityStageMonitor fail. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('waitAbilityStageMonitor callback');
  }
});
```

### setMockList<sup>11+</sup>

setMockList(mockList: Record\<string, string>): void

Sets a list of mock data.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| mockList | Record\<string, string> | Yes  | Key-value object of the mock, where **key** is the target path to be replaced and **value** is the path of the mock implementation to be used for the replacement.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message       |
| -------- | --------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000050 | Internal error. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

// Create a key-value object of the mock, where key is the target path to be replaced, and value is the path of the mock implementation file.
let mockList: Record<string, string> = {
  '@ohos.router': 'src/main/mock/ohos/router.mock',
  'common.time': 'src/main/mock/common/time.mock',
};
let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;

// Obtain the AbilityDelegator instance.
abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
// Call setMockList to set the mock replacement relationship.
abilityDelegator.setMockList(mockList);
```