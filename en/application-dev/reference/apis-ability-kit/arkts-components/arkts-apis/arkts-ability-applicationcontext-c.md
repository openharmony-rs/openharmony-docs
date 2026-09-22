# ApplicationContext

```TypeScript
declare class ApplicationContext extends Context
```

ApplicationContext inherits from Context and provides application-level management capabilities, such as application lifecycle listening, process management, and application environment setting.

> **NOTE:** 
> 
> The APIs of this module can be used only in the stage model.

**Inheritance/Implementation:** ApplicationContext extends [Context](arkts-ability-context-c.md)

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## clearUpApplicationData

```TypeScript
clearUpApplicationData(): Promise<void>
```

Clears up all data in the application file path and revokes the permissions that the application has requested from users. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> For details about the application file path, see
> [Application File Directory and Application File Path](../../../file-management/app-sandbox-directory.md#application-file-directory-and-application-file-path)
> . The figure shows only the application file paths in the EL1 and EL2 directories. For the application file paths
> in other directories, refer to EL1.
> 
> This API stops the application process. After the application process is stopped, all subsequent callbacks will
> not be triggered.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Clear all data under the application file path of the current application.
    applicationContext.clearUpApplicationData();
  }
}
```

<a id="clearupapplicationdata-1"></a>

## clearUpApplicationData

```TypeScript
clearUpApplicationData(callback: AsyncCallback<void>): void
```

Clears up all data in the application file path and revokes the permissions that the application has requested from users. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> For details about the application file path, see
> [Application File Directory and Application File Path](../../../file-management/app-sandbox-directory.md#application-file-directory-and-application-file-path)
> . The figure shows only the application file paths in the EL1 and EL2 directories. For the application file paths
> in other directories, refer to EL1.
> 
> This API stops the application process. After the application process is stopped, all subsequent callbacks will
> not be triggered.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the application data is cleared up, &lt;code&gt;error&lt;/code&gt; is &lt;code&gt;undefined&lt;/code&gt;; otherwise, &lt;code&gt;error&lt;/code&gt; is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Clear all data under the application file path of the current application.
    applicationContext.clearUpApplicationData(error => {
      if (error) {
        console.error(`Failed to clear up application data. Code: ${error.code}, message: ${error.message}`);
      }
    });
  }
}
```

## disableDelayedProcessExit

```TypeScript
disableDelayedProcessExit(): Promise<void>
```

Disables delayed process exit for the current process.

<p>&lt;b&gt;NOTE&lt;/b&gt;: <br>This API can be called only by the main thread. <br>Calling this API cancels the effect of [enableDelayedProcessExit](#enabledelayedprocessexit).</p>

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: Fail to connect system service. |
| [16000150](../errorcode-ability.md#16000150-failed-to-send-request) | The current process has no UIAbility, and this API cannot be called. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Disable the delayed exit feature of the current process.
      this.context.getApplicationContext().disableDelayedProcessExit().then(() => {
        console.info('disableDelayedProcessExit succeed');
      }).catch((error: BusinessError) => {
        console.error(`disableDelayedProcessExit error, code: ${error.code}, error msg: ${error.message}`);
      });
    } catch(error) {
      console.error('disableDelayedProcessExit failed. Code=%{public}d, Message=%{public}s', error.code, error.message);
    }
  }
}
```

## enableDelayedProcessExit

```TypeScript
enableDelayedProcessExit(): Promise<void>
```

Enable delayed exit for the current process. <p>**NOTE:**  <br>It can be called only by the main thread. <br>Under normal circumstances, the process exits after the last UIAbility within the application process has exited. After calling this interface, the process will delay its exit for 10 seconds after the last UIAbility exits. If a new Ability is started within the 10 seconds in the current process, the process no longer exits.</p>

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: Fail to connect system service. |
| [16000150](../errorcode-ability.md#16000150-failed-to-send-request) | The current process has no UIAbility, and this API cannot be called. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Enable the delayed exit feature of the current process.
      this.context.getApplicationContext().enableDelayedProcessExit().then(() => {
        console.info('enableDelayedProcessExit succeed');
      }).catch((error: BusinessError) => {
        console.error(`enableDelayedProcessExit error, code: ${error.code}, error msg: ${error.message}`);
      });
    } catch(error) {
      console.error('enableDelayedProcessExit failed. Code=%{public}d, Message=%{public}s', error.code, error.message);
    }
  }
}
```

## getAllRunningInstanceKeys

```TypeScript
getAllRunningInstanceKeys(): Promise<Array<string>>
```

Obtains the unique instance IDs of all multi-instances of this application. This API uses a promise to return the result. It can be called only on the main thread.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the unique instance IDs of all multi-instances of the application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported. |

**Examples**

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Obtain the unique instance identifiers of all multi-instance instances of the application.
      applicationContext.getAllRunningInstanceKeys();
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`getAllRunningInstanceKeys fail, code: ${code}, msg: ${message}`);
    }
  }
}
```

## getAllWindowStages

```TypeScript
getAllWindowStages(): Promise<Array<window.WindowStage>>
```

Obtains all WindowStage objects in the current application process. This API uses a promise to return the result. It can be called only on the main thread.

This API is used to manage multiple windows in an application that contains several UIAbility components, for example, managing the states of different WindowStage objects, or synchronizing state or data between multiple windows within the same application.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md)&gt;&gt; | Promise used to return all WindowStage objects in the current application process. |

**Examples**

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Obtain all WindowStage objects in the current process of the application.
      applicationContext.getAllWindowStages().then((data: window.WindowStage[]) => {
        let windowStage: window.WindowStage[] = data;
        console.info(`WindowStages size ${windowStage.length}`);
      }).catch((error: BusinessError) => {
        console.error(`getAllWindowStages error, code: ${error.code}, error msg: ${error.message}`);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`getAllWindowStages fail, code: ${code}, msg: ${message}`);
    }
  }
}
```

## getCurrentAppCloneIndex

```TypeScript
getCurrentAppCloneIndex(): number
```

Obtains the index of the current application clone.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the current application clone. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | The MultiAppMode is not App_CLONE. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Obtain the clone index of the current application.
      let appCloneIndex = applicationContext.getCurrentAppCloneIndex();
    } catch (error) {
      console.error(`Failed to get current app clone index. Code: ${error.code}, message: ${error.message}`);
    }
  }
}
```

## getCurrentInstanceKey

```TypeScript
getCurrentInstanceKey(): string
```

Obtains the unique instance ID of this application. This API can be called only on the main thread.

This API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 16000078 is returned.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Unique instance ID of the application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported. |

**Examples**

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    let currentInstanceKey = '';
    try {
      // Obtain the unique instance identifier of the current application's multiple instances.
      currentInstanceKey = applicationContext.getCurrentInstanceKey();
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`getCurrentInstanceKey fail, code: ${code}, msg: ${message}`);
    }
    console.info(`currentInstanceKey: ${currentInstanceKey}`);
  }
}
```

## getRunningProcessInformation

```TypeScript
getRunningProcessInformation(): Promise<Array<ProcessInformation>>
```

Obtains the information about running processes. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ProcessInformation](arkts-ability-processinformation-i.md)&gt;&gt; | Promise used to return the API call result and the process running information. You can perform error handling or custom processing in this callback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbility extends UIAbility {
  onForeground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Obtain the information about running processes.
    applicationContext.getRunningProcessInformation().then((data) => {
      console.info(`The process running information is: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
      console.error(`error code: ${error.code}, error msg: ${error.message}`);
    });
  }
}
```

<a id="getrunningprocessinformation-1"></a>

## getRunningProcessInformation

```TypeScript
getRunningProcessInformation(callback: AsyncCallback<Array<ProcessInformation>>): void
```

Obtains the information about running processes. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ProcessInformation](arkts-ability-processinformation-i.md)&gt;&gt; | Yes | Callback used to return the information about the running processes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onForeground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Obtain the running process information.
    applicationContext.getRunningProcessInformation((err, data) => {
      if (err) {
        console.error(`Failed to get running process information. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.info(`The process running information is: ${JSON.stringify(data)}`);
      }
    });
  }
}
```

## getUIAbilityByInstanceId

```TypeScript
getUIAbilityByInstanceId(instanceId: string): UIAbility
```

Get the UIAbility instance by the instance Id.

<p>**NOTE:**  <br>It can be called only by the main thread. </p>

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instanceId | string | Yes | The instanceId of the UIAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | The UIAbility instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000003](../errorcode-ability.md#16000003-id-does-not-exist) | The id does not exist. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. System service failed to communicate with dependency module. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      let instanceId = 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx';
      // Obtain the UIAbility instance based on the instance ID.
      let uiAbility = applicationContext.getUIAbilityByInstanceId(instanceId);
      console.info(`getUIAbilityByInstanceId succeed, ability: ${uiAbility}`);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`getUIAbilityByInstanceId fail, code: ${code}, message: ${message}`);
    }
  }
}
```

## getUIAbilityChildProcessInfos

```TypeScript
getUIAbilityChildProcessInfos(): Promise<Array<ChildProcessInformation>>
```

Obtains the information about the UIAbility child processes of the current application. This API uses a promise to return the result. The returned child processes are created via startAbility with ProcessMode.NEW_PROCESS_ATTACH_TO_PARENT.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ChildProcessInformation](arkts-ability-childprocessinformation-i.md)&gt;&gt; | Promise used to return the information about the UIAbility child processes of the current application. If no child processes exist, an empty array is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Connect to system service failed. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Obtain the UIAbility child process information.
    applicationContext.getUIAbilityChildProcessInfos().then((data) => {
      console.info(`getUIAbilityChildProcessInfos success, count: ${data.length}`);
      for (let info of data) {
        console.info(`pid: ${info.pid}, parentPid: ${info.parentPid}, processName: ${info.processName}`);
      }
    }).catch((err: BusinessError) => {
      console.error(`getUIAbilityChildProcessInfos failed, code: ${err.code}, msg: ${err.message}`);
    });
  }
}
```

## killAllProcesses

```TypeScript
killAllProcesses(): Promise<void>
```

Kills all processes of this application. The application will not execute the normal lifecycle when exiting. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> This API is used to forcibly exit an application in abnormal scenarios. To exit an application properly, call
> [terminateSelf()](arkts-ability-uiabilitycontext-c.md#terminateself).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Terminate all processes of the application.
    applicationContext.killAllProcesses();
  }
}
```

<a id="killallprocesses-1"></a>

## killAllProcesses

```TypeScript
killAllProcesses(clearPageStack: boolean): Promise<void>
```

Kills all processes of this application. The application will not execute the normal lifecycle when exiting. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> This API is used to forcibly exit an application in abnormal scenarios. To exit an application properly, call
> [terminateSelf()](arkts-ability-uiabilitycontext-c.md#terminateself).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clearPageStack | boolean | Yes | Whether to clear the page stack. **true** to clear, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | If the input parameter is not valid parameter. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

let isClearPageStack = false;

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Terminate all processes of the application and clear the page stack.
    applicationContext.killAllProcesses(isClearPageStack);
  }
}
```

<a id="killallprocesses-2"></a>

## killAllProcesses

```TypeScript
killAllProcesses(callback: AsyncCallback<void>): void
```

Kills all processes of this application. The application will not execute the normal lifecycle when exiting. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> This API is used to forcibly exit an application in abnormal scenarios. To exit an application properly, call
> [terminateSelf()](arkts-ability-uiabilitycontext-c.md#terminateself).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If all the processes are killed, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Terminate all processes of the application.
    applicationContext.killAllProcesses(error => {
      if (error) {
        console.error(`Failed to kill all processes. Code: ${error.code}, message: ${error.message}`);
      }
    });
  }
}
```

## off('abilityLifecycle')

```TypeScript
off(type: 'abilityLifecycle', callbackId: number, callback: AsyncCallback<void>): void
```

Unregisters a listener for the lifecycle of a UIAbility within the application. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'abilityLifecycle' | Yes | Lifecycle of the UIAbility within the application. The value is fixed at **'abilityLifecycle'**. |
| callbackId | number | Yes | ID returned when the [ApplicationContext.on('abilityLifecycle')](#onabilitylifecycle) API is called to register a listener for the lifecycle of a UIAbility within the application. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the deregistration is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class EntryAbility extends UIAbility {
  onDestroy() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    console.info(`stage applicationContext: ${applicationContext}`);
    try {
      // Unregister the listener for the in-application UIAbility lifecycle.
      applicationContext.off('abilityLifecycle', lifecycleId, (error, data) => {
        if (error) {
          console.error(`Failed to unregister abilityLifecycle callback. Code: ${error.code}, message: ${error.message}`);
        } else {
          console.info(`unregisterAbilityLifecycleCallback success, data: ${JSON.stringify(data)}`);
        }
      });
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## off('abilityLifecycle')

```TypeScript
off(type: 'abilityLifecycle', callbackId: number): Promise<void>
```

Unregisters a listener for the lifecycle of a UIAbility within the application. This API uses a promise to return the result. It can be called only on the main thread.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'abilityLifecycle' | Yes | Lifecycle of the UIAbility within the application. The value is fixed at **'abilityLifecycle'**. |
| callbackId | number | Yes | ID returned when the [ApplicationContext.on('abilityLifecycle')](#onabilitylifecycle) API is called to register a listener for the lifecycle of a UIAbility within the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class MyAbility extends UIAbility {
  onDestroy() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    console.info(`stage applicationContext: ${applicationContext}`);
    try {
      // Unregister the listener for the in-application UIAbility lifecycle.
      applicationContext.off('abilityLifecycle', lifecycleId);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## off('environment')

```TypeScript
off(type: 'environment', callbackId: number, callback: AsyncCallback<void>): void
```

Unregisters the listener for system environment changes. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'environment' | Yes | System environment change, for example, system dark/light color mode change. The value is fixed at **'environment'**. |
| callbackId | number | Yes | ID returned when the [ApplicationContext.on('environment')](#onenvironment) API is called to register a listener for system environment changes. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the deregistration is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class EntryAbility extends UIAbility {
  onDestroy() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Unregister the listener for system environment changes.
      applicationContext.off('environment', callbackId, (error, data) => {
        if (error) {
          console.error(`Failed to unregister environment callback. Code: ${error.code}, message: ${error.message}`);
        } else {
          console.info(`unregisterEnvironmentCallback success, data: ${JSON.stringify(data)}`);
        }
      });
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## off('environment')

```TypeScript
off(type: 'environment', callbackId: number): Promise<void>
```

Unregisters the listener for system environment changes. This API uses a promise to return the result. It can be called only on the main thread.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'environment' | Yes | System environment change, for example, system dark/light color mode change. The value is fixed at **'environment'**. |
| callbackId | number | Yes | ID returned when the [ApplicationContext.on('environment')](#onenvironment) API is called to register a listener for system environment changes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class MyAbility extends UIAbility {
  onDestroy() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Unregister the listener for system environment changes.
      applicationContext.off('environment', callbackId);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## off('applicationStateChange')

```TypeScript
off(type: 'applicationStateChange', callback?: ApplicationStateChangeCallback): void
```

Unregisters the listener for application process state changes. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'applicationStateChange' | Yes | Application process state change. The value is fixed at **'applicationStateChange'**. |
| callback | [ApplicationStateChangeCallback](arkts-ability-app-ability-applicationstatechangecallback-applicationstatechangecallback-c.md) | No | Callback used to return the result. The value can be a callback defined by [ApplicationContext.on('applicationStateChange')](#onapplicationstatechange) or empty.<br>- If a defined callback is passed in, the listener for that callback is unregistered.<br>- If no value is passed in, all the listeners for the corresponding event are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

Assume that [ApplicationContext.on('applicationStateChange')](#onapplicationstatechange) is used to register a callback named applicationStateChangeCallback. The following example shows how to unregister the corresponding listener.

```TypeScript
import { UIAbility, ApplicationStateChangeCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let applicationStateChangeCallback: ApplicationStateChangeCallback = {
  onApplicationForeground() {
    console.info('applicationStateChangeCallback onApplicationForeground');
  },
  onApplicationBackground() {
    console.info('applicationStateChangeCallback onApplicationBackground');
  }
};

export default class MyAbility extends UIAbility {
  onDestroy() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // In this example, the callback parameter is ApplicationStateChangeCallback. Replace it with the actual value.
      // If no value is passed in, all the listeners for the corresponding event are unregistered.
      applicationContext.off('applicationStateChange', applicationStateChangeCallback);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## offSystemConfigurationUpdated

```TypeScript
offSystemConfigurationUpdated(callback?: systemConfiguration.UpdatedCallback): void
```

unregisters a listener for system configuration updated.

<p>**NOTE:**  <br>It can be called only by the main thread. </p>

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [systemConfiguration.UpdatedCallback](arkts-ability-systemconfiguration-updatedcallback-i.md) | No | The system configuration updated callback. If a defined callback is passed in, the listener for that callback is unregistered. If no value is passed in, all the listeners for the corresponding event are unregistered. |

**Examples**

```TypeScript
import { UIAbility, systemConfiguration, ConfigurationConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let callBack: systemConfiguration.UpdatedCallback = {
      onColorModeUpdated(colorMode: ConfigurationConstant.ColorMode) {
        console.info(`system configuration updated colormode:` + colorMode);
      },
      onFontSizeScaleUpdated(fontSizeScale: number) {
        console.info(`system configuration updated ability:` + fontSizeScale);
      },
      onFontWeightScaleUpdated(fontWeightScale: number) {
        console.info(`system configuration updated ability:` + fontWeightScale);
      },
      onMCCUpdated(mcc: string) {
        console.info(`system configuration updated ability:` + mcc);
      },
      onMNCUpdated(mnc: string) {
        console.info(`system configuration updated ability:` + mnc);
      },
      onLanguageUpdated(language: string) {
        console.info(`system configuration updated ability:` + language);
      },
      onFontIdUpdated(fontId: string) {
        console.info(`system configuration updated ability:` + fontId);
      },
      onHasPointerDeviceUpdated(hasPointerDevice: boolean) {
        console.info(`system configuration updated ability:` + hasPointerDevice);
      },
      onLocaleUpdated(locale: string) {
        console.info(`system configuration updated ability:` + locale);
      }
    }
    // 1. Obtain the applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2. Unregister the listener through applicationContext.
      applicationContext.offSystemConfigurationUpdated(callBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`offSystemConfigurationUpdated finish`);
  }
}
```

## on('abilityLifecycle')

```TypeScript
on(type: 'abilityLifecycle', callback: AbilityLifecycleCallback): number
```

Registers a listener for the lifecycle of a UIAbility within the application. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'abilityLifecycle' | Yes | Lifecycle of the UIAbility within the application. The value is fixed at **'abilityLifecycle'**. |
| callback | [AbilityLifecycleCallback](arkts-ability-app-ability-abilitylifecyclecallback-abilitylifecyclecallback-c.md) | Yes | Callback triggered when the UIAbility lifecycle changes. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the callback registered. This ID is used to unregister the corresponding callback in [ApplicationContext.off('abilityLifecycle')](#offabilitylifecycle). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { UIAbility, AbilityLifecycleCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let abilityLifecycleCallback: AbilityLifecycleCallback = {
      onAbilityCreate(ability) {
        console.info(`AbilityLifecycleCallback onAbilityCreate ability: ${ability}`);
      },
      onWindowStageCreate(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageCreate ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageCreate windowStage: ${windowStage}`);
      },
      onWindowStageActive(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageActive ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageActive windowStage: ${windowStage}`);
      },
      onWindowStageInactive(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageInactive ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageInactive windowStage: ${windowStage}`);
      },
      onWindowStageDestroy(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageDestroy ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageDestroy windowStage: ${windowStage}`);
      },
      onAbilityDestroy(ability) {
        console.info(`AbilityLifecycleCallback onAbilityDestroy ability: ${ability}`);
      },
      onAbilityForeground(ability) {
        console.info(`AbilityLifecycleCallback onAbilityForeground ability: ${ability}`);
      },
      onAbilityBackground(ability) {
        console.info(`AbilityLifecycleCallback onAbilityBackground ability: ${ability}`);
      },
      onAbilityContinue(ability) {
        console.info(`AbilityLifecycleCallback onAbilityContinue ability: ${ability}`);
      }
    }

    // Obtain applicationContext through the context property.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Register a listener for the in-application lifecycle through applicationContext.
      lifecycleId = applicationContext.on('abilityLifecycle', abilityLifecycleCallback);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info(`registerAbilityLifecycleCallback lifecycleId: ${lifecycleId}`);
  }

  // Unregister the listener for the in-application UIAbility lifecycle when it is no longer needed or when the application exits.
  onDestroy() {
    // Obtain applicationContext through the context property.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      applicationContext.off('abilityLifecycle', lifecycleId, (error, data) => {
        if (error) {
          console.error(`Failed to unregister abilityLifecycle callback. Code: ${error.code}, message: ${error.message}`);
        } else {
          console.info(`unregisterAbilityLifecycleCallback success, data: ${JSON.stringify(data)}`);
        }
      });
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## on('environment')

```TypeScript
on(type: 'environment', callback: EnvironmentCallback): number
```

Registers a listener for system environment changes. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE:** 
> 
> - You can also use [onConfigurationUpdate](arkts-ability-app-ability-ability-ability-c.md#onconfigurationupdate) to listen for system environment changes. Unlike [onConfigurationUpdate](arkts-ability-app-ability-ability-ability-c.md#onconfigurationupdate) of **Ability**, this API offers greater flexibility. It can be used both within application components and pages. However, the environment variables that can be subscribed to are different from those of [onConfigurationUpdate](arkts-ability-app-ability-ability-ability-c.md#onconfigurationupdate). For example, this API cannot be used to subscribe to direction, screen density, and display ID changes. For details, see the description of each environment variable in [Configuration](arkts-ability-app-ability-configuration-configuration-i.md).
> 
> - There are certain restrictions when this API is triggered. For example, if you set the application language by calling [setLanguage](#setlanguage), the system does not trigger the callback for the current API even if the system language changes. For details, see [When to Use](../../../application-models/subscribe-system-environment-variable-changes.md#when-to-use).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'environment' | Yes | System environment change, for example, system dark/light color mode change. The value is fixed at **'environment'**. |
| callback | [EnvironmentCallback](arkts-ability-app-ability-environmentcallback-environmentcallback-c.md) | Yes | Callback triggered when the system environment changes. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the callback registered. This ID is used to unregister the corresponding callback in [ApplicationContext.off('environment')](#offenvironment). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { UIAbility, EnvironmentCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let environmentCallback: EnvironmentCallback = {
      onConfigurationUpdated(config) {
        console.info(`onConfigurationUpdated config: ${JSON.stringify(config)}`);
      },
      onMemoryLevel(level) {
        console.info(`onMemoryLevel level: ${level}`);
      }
    };
    // Obtain the applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Register a listener for system environment changes through applicationContext.
      callbackId = applicationContext.on('environment', environmentCallback);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info(`registerEnvironmentCallback callbackId: ${callbackId}`);
  }

  // Unregister the listener for system environment changes when it is no longer needed or when the application exits.
  onDestroy() {
    // Obtain the applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      applicationContext.off('environment', callbackId, (error, data) => {
        if (error) {
          console.error(`Failed to unregister environment callback. Code: ${error.code}, message: ${error.message}`);
        } else {
          console.info(`unregisterEnvironmentCallback success, data: ${JSON.stringify(data)}`);
        }
      });
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## on('applicationStateChange')

```TypeScript
on(type: 'applicationStateChange', callback: ApplicationStateChangeCallback): void
```

Registers a listener for application process state changes. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'applicationStateChange' | Yes | Application process state change. The value is fixed at **'applicationStateChange'**. |
| callback | [ApplicationStateChangeCallback](arkts-ability-app-ability-applicationstatechangecallback-applicationstatechangecallback-c.md) | Yes | Callback triggered when the application process state is changed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { UIAbility, ApplicationStateChangeCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let applicationStateChangeCallback: ApplicationStateChangeCallback = {
  onApplicationForeground() {
    console.info('applicationStateChangeCallback onApplicationForeground');
  },
  onApplicationBackground() {
    console.info('applicationStateChangeCallback onApplicationBackground');
  }
}

export default class MyAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    // Obtain the applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Register the current application process state listener through applicationContext.
      applicationContext.on('applicationStateChange', applicationStateChangeCallback);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info('Register applicationStateChangeCallback');
  }

  // Unregister all registered listeners of this event type when they are no longer needed or when the application exits.
  onDestroy() {
    // Obtain the applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      applicationContext.off('applicationStateChange', applicationStateChangeCallback);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## onSystemConfigurationUpdated

```TypeScript
onSystemConfigurationUpdated(callback: systemConfiguration.UpdatedCallback): void
```

Registers a listener for system configuration updated.

<p>**NOTE:**  <br>It can be called only by the main thread. </p>

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [systemConfiguration.UpdatedCallback](arkts-ability-systemconfiguration-updatedcallback-i.md) | Yes | The system configuration updated callback. |

**Examples**

```TypeScript
import { UIAbility, systemConfiguration, ConfigurationConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callBack: systemConfiguration.UpdatedCallback = {
  onColorModeUpdated(colorMode: ConfigurationConstant.ColorMode) {
    console.info(`system configuration updated colormode:` + colorMode);
  },
  onFontSizeScaleUpdated(fontSizeScale: number) {
    console.info(`system configuration updated ability:` + fontSizeScale);
  },
  onFontWeightScaleUpdated(fontWeightScale: number) {
    console.info(`system configuration updated ability:` + fontWeightScale);
  },
  onLanguageUpdated(language: string) {
    console.info(`system configuration updated ability:` + language);
  },
  onFontIdUpdated(fontId: string) {
    console.info(`system configuration updated ability:` + fontId);
  },
  onMCCUpdated(mcc: string) {
    console.info(`system configuration updated ability:` + mcc);
  },
  onMNCUpdated(mnc: string) {
    console.info(`system configuration updated ability:` + mnc);
  },
  onHasPointerDeviceUpdated(hasPointerDevice: boolean) {
    console.info(`system configuration updated ability:` + hasPointerDevice);
  },
  onLocaleUpdated(locale: string) {
    console.info(`system configuration updated ability:` + locale);
  }
}

export default class EntryAbility extends UIAbility {
  onForeground() {
    // Obtain the applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Register the listener through applicationContext.
      applicationContext.onSystemConfigurationUpdated(callBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }

  // Unregister the listener when it is no longer needed or when the application exits.
  onDestroy() {
    // Obtain the applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Unregister the listener through applicationContext.
      applicationContext.offSystemConfigurationUpdated(callBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## restartApp

```TypeScript
restartApp(want: Want): void
```

Restarts the application and starts the specified UIAbility. This API can be called only by the main thread, and the application to restart must be active.

> **NOTE:** 
> 
> When this API is called to restart the application, the **onDestroy** lifecycle callback of the ability in the
> application is not triggered.
> 
> If an atomic service calls this API,
> [restartSelfAtomicService()](arkts-ability-abilitymanager-restartselfatomicservice-f.md)
> , or [UIAbilityContext.restartApp()](arkts-ability-uiabilitycontext-c.md#restartapp) within 3 seconds after a
> successful call to this API, the system returns error code 16000064.
> 
> If an application calls this API or
> [UIAbilityContext.restartApp()](arkts-ability-uiabilitycontext-c.md#restartapp) within 3 seconds after a
> successful call to this API, the system returns error code 16000064.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the UIAbility to start. No verification is performed on the bundle name passed in. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000063](../errorcode-ability.md#16000063-invalid-ability-during-application-restart) | The target to restart does not belong to the current application or is not a UIAbility. |
| [16000064](../errorcode-ability.md#16000064-frequent-application-restart) | Restart too frequently. Try again at least 3s later. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { common, Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'restartApp';
  private context = this.getUIContext().getHostContext()?.getApplicationContext() as common.ApplicationContext;

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let want: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EntryAbility'
          };
          if (this.context) {
            try {
              // Restart the application and start the specified UIAbility.
              this.context.restartApp(want);
            } catch (err) {
              hilog.error(0x0000, 'testTag', `restart failed: ${err.code}, ${err.message}`);
            }
          } else {
            hilog.error(0x0000, 'testTag', '%{public}s', 'AppContext is null');
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## setColorMode

```TypeScript
setColorMode(colorMode: ConfigurationConstant.ColorMode): void
```

Sets the dark/light color mode for the application. This API can be called only on the main thread.

> **NOTE:** 
> 
> Before calling this API, ensure that the window has been created and the page corresponding to the UIAbility has
> been loaded (using the
> loadContent() API in the
> [onWindowStageCreate()](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagecreate) lifecycle).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorMode | [ConfigurationConstant.ColorMode](arkts-ability-configurationconstant-colormode-e.md) | Yes | Dark/light color mode, which can be dark mode, light mode, or follow-system mode (default). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |

**Examples**

```TypeScript
import { UIAbility, ConfigurationConstant } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info("Ability onWindowStageCreate");
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
      // Obtain the application context.
      let applicationContext = this.context.getApplicationContext();
      // Set the application to dark mode.
      applicationContext.setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_DARK);
    });
  }
}
```

## setFont

```TypeScript
setFont(font: string): void
```

Sets the font for this application. This API can be called only on the main thread.

> **NOTE:** 
> 
> Before calling this API, ensure that the window has been created and the page corresponding to the UIAbility has
> been loaded (using the
> loadContent() API in the
> [onWindowStageCreate()](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagecreate) lifecycle).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| font | string | Yes | Font, which can be registered by calling [UIContext.registerFont](../../../reference/apis-arkui/arkts-apis-uicontext-font.md#registerfont). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  aboutToAppear() {
    this.getUIContext().getFont().registerFont({
      familyName: 'fontName',
      familySrc: $rawfile('font/medium.ttf')  // 'font/medium.ttf' is used only as an example. Replace it with the actual font resource file.
    });

    // Set the application to use the registered custom font.
    this.context.getApplicationContext().setFont('fontName');
  }

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(50)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## setFontSizeScale

```TypeScript
setFontSizeScale(fontSizeScale: number): void
```

Sets the scale ratio for the font size of this application. This API can be called only on the main thread.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontSizeScale | number | Yes | Font scale ratio. The value is a non-negative number. When the application's [fontSizeScale](../../../quick-start/app-configuration-file.md#configuration) is set to **followSystem** and the value set here exceeds the value of [fontSizeMaxScale](../../../quick-start/app-configuration-file.md#configuration), the value of [fontSizeMaxScale](../../../quick-start/app-configuration-file.md#configuration) takes effect. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        return;
      }
      // Obtain the application context.
      let applicationContext = this.context.getApplicationContext();
      // Set the font size scale of the application.
      applicationContext.setFontSizeScale(2);
    });
  }
}
```

## setLanguage

```TypeScript
setLanguage(language: string): void
```

Sets the language for the application. This API can be called only on the main thread.

> **NOTE:** 
> 
> Before calling this API, ensure that the window has been created and the page corresponding to the UIAbility has
> been loaded (using the
> loadContent()
> API in the
> [onWindowStageCreate()](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagecreate) lifecycle).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| language | string | Yes | Target language. The list of supported languages can be obtained by calling [getSystemLanguages()](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-system-c.md#getsystemlanguages). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info("Ability onWindowStageCreate");
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Set the application language to Chinese.
    applicationContext.setLanguage('zh-cn');
  }
}
```

## setSupportedProcessCache

```TypeScript
setSupportedProcessCache(isSupported : boolean): void
```

Sets whether the current application's process supports resource caching, so that the cached process resources can be reused when the application is started again. This API can be called only on the main thread.

This setting applies only to the current process instance and does not affect others. If the application process instance is terminated, the previously set state will not be preserved and must be reset.

This API can be properly called only on phones and 2-in-1 devices. If it is called on other device types, error code 801 is returned.

> **NOTE:** 
> 
> - This API only sets the application to be ready for quick startup after caching. It does not mean that quick startup will be triggered. Other conditions must be considered to determine whether to trigger quick startup.
> 
> - To ensure that this API is effective before the process exits, it should be called as soon as possible. You are advised to call this API within the **onCreate()** callback of the [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md).
> 
> - If this API is called multiple times within the same process, the outcome of the final call is used. In cases where there are multiple AbilityStage instances, to achieve the desired result, this API must be called and configured with the same value in each AbilityStage.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isSupported | boolean | Yes | Whether process cache is supported. The value &lt;code&gt;true&lt;/code&gt; means that process cache is supported, and &lt;code&gt;false&lt;/code&gt; means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { AbilityStage, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Set the current application process to support caching of process resources.
      applicationContext.setSupportedProcessCache(true);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`setSupportedProcessCache fail, code: ${code}, msg: ${message}`);
    }
  }
}
```

## startSelfUIAbility

```TypeScript
startSelfUIAbility(want: Want): Promise<void>
```

Starts a UIAbility of the current application during the delayed-exit window.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Indicates the UIAbility to start. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: Fail to connect system service. |
| [16000122](../errorcode-ability.md#16000122-target-component-is-intercepted-by-the-system-control-module) | The target component is blocked by the system module and does not support startup. |
| [16000123](../errorcode-ability.md#16000123-implicit-startup-is-not-supported) | Implicit startup is not supported. |
| [16000124](../errorcode-ability.md#16000124-starting-a-distributed-uiability-is-not-supported) | Starting a remote UIAbility is not supported. |
| [16000125](../errorcode-ability.md#16000125-starting-a-plugin-uiability-is-not-supported) | Starting a plugin UIAbility is not supported. |
| [16000130](../errorcode-ability.md#16000130-uiability-does-not-belong-to-the-caller) | The UIAbility does not belong to the caller. |
| [16000161](../errorcode-ability.md#16000161-delayed-process-exit-is-not-pending-in-the-current-process-and-this-api-cannot-be-called) | Delayed process exit is not pending in the current process, and this API cannot be called. |
| [16000162](../errorcode-ability.md#16000162-the-current-process-still-has-another-uiability-and-this-api-cannot-be-called) | The current process still has another UIAbility, and this API cannot be called. |

**Examples**

```TypeScript
import { common, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State message: string = 'Delayed startup';
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Button(this.message)
      .fontSize(50)
      .align(Alignment.Center)
      .onClick(() => {
        try {
          const newWant: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EntryAbility',
            parameters: {
              'pageName': 'IndexNew'  // Mark the main page to be started.
            }
          };
          // Obtain the application context.
          let applicationContext = this.context.getApplicationContext();
          // Start the main UI during delayed exit.
          this.context.terminateSelf().then(() => {
            // Set a delay of 2000 ms to ensure that the main application exits completely before calling the startSelfUIAbility API.
            setTimeout(() => {
              applicationContext.getApplicationContext().startSelfUIAbility(newWant).then(() => {
                hilog.info(0x0000, 'testTag', 'Main UI started successfully.');
              }).catch((error: BusinessError) => {
                hilog.error(0x0000, 'testTag', `Failed to start the main UI, code: ${error.code}, error msg: ${error.message}`);
              });
            }, 2000);
          });
        } catch (error) {
          hilog.error(0x0000, 'testTag', `Failed to start the main UI, code: ${error.code}, error msg: ${error.message}`);
        }
      });
  }
}
```
