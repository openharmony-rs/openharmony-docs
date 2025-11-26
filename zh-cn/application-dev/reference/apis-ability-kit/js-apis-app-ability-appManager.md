# @ohos.app.ability.appManager (应用管理)

appManager模块提供App管理的能力，包括查询当前是否处于稳定性测试场景、查询是否为ram受限设备、获取应用程序的内存大小、获取有关运行进程的信息等。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 9 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { appManager } from '@kit.AbilityKit';
```

## ProcessState<sup>10+</sup>

表示进程状态的枚举。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称                 | 值  | 说明                               |
| -------------------- | --- | --------------------------------- |
| STATE_CREATE    | 0   |    进程处于创建状态。       |
| STATE_FOREGROUND          | 1   |    进程处于前台状态。      |
| STATE_ACTIVE  | 2   |     进程处于获焦状态。   |
| STATE_BACKGROUND        | 3   |    进程处于后台不可见状态。           |
| STATE_DESTROY        | 4   |    进程处于销毁状态。         |

## appManager.isRunningInStabilityTest

isRunningInStabilityTest(callback: AsyncCallback&lt;boolean&gt;): void

查询当前是否处于稳定性测试场景。使用callback异步回调。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | 是 |以回调方式返回接口运行结果及当前是否处于稳定性测试场景，可进行错误处理或其他自定义处理。返回true表示处于稳定性测试场景，返回false表示处于非稳定性测试场景。  |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';

appManager.isRunningInStabilityTest((err, flag) => {
  if (err) {
    console.error(`isRunningInStabilityTest fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info(`The result of isRunningInStabilityTest is: ${JSON.stringify(flag)}`);
  }
});
```


## appManager.isRunningInStabilityTest

isRunningInStabilityTest(): Promise&lt;boolean&gt;

查询当前是否处于稳定性测试场景。使用Promise异步回调。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;boolean&gt; | 以Promise方式返回接口运行结果及当前是否处于稳定性测试场景，可进行错误处理或其他自定义处理。返回true表示处于稳定性测试场景，返回false表示处于非稳定性测试场景。 |

**错误码**：

以下错误码详细介绍请参考[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.isRunningInStabilityTest().then((flag) => {
  console.info(`The result of isRunningInStabilityTest is: ${flag}`);
}).catch((err: Error) => {
  let error=err as BusinessError;
  console.error(`error: code: ${error.code} message: ${error.message}`);
});
```

## appManager.isRamConstrainedDevice

isRamConstrainedDevice(): Promise\<boolean>

查询是否为ram受限设备。使用Promise异步回调。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;boolean&gt; | 以Promise方式返回接口运行结果及当前设备是否为ram受限设备，可进行错误处理或其他自定义处理。true：当前设备为ram受限设备，false：当前设备为非ram受限设备。 |

**错误码**：

以下错误码详细介绍请参考[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.isRamConstrainedDevice().then((data) => {
  console.info(`The result of isRamConstrainedDevice is: ${data}`);
}).catch((err: Error) => {
  let error = err as BusinessError;
  console.error(`error: ${error.code} ${error.message}`);
});
```

## appManager.isRamConstrainedDevice

isRamConstrainedDevice(callback: AsyncCallback\<boolean>): void

查询是否为ram受限设备。使用callback异步回调。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | 是 |以回调方式返回接口运行结果及当前设备是否为ram受限设备，可进行错误处理或其他自定义处理。true：当前设备为ram受限设备，false：当前设备为非ram受限设备。  |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';

appManager.isRamConstrainedDevice((err, data) => {
  if (err) {
    console.error(`isRamConstrainedDevice fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info(`The result of isRamConstrainedDevice is: ${JSON.stringify(data)}`);
  }
});
```

## appManager.getAppMemorySize

ArkTS-Dyn: getAppMemorySize(): Promise\<number>

ArkTS-Sta: getAppMemorySize(): Promise\<int>

获取当前应用程序可以使用的内存的值。使用Promise异步回调。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;int\> | 获取当前应用程序可以使用的内存的值，可根据此值进行错误处理或其他自定义处理，单位是M。使用Promise异步回调。|

**错误码**：

以下错误码详细介绍请参考[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.getAppMemorySize().then((data) => {
  console.info(`The size of app memory is: ${data}`);
}).catch((err: Error) => {
  let error = err as BusinessError;
  console.error(`error: code: ${error.code} message: ${error.message}`);
});
```

## appManager.getAppMemorySize

ArkTS-Dyn: getAppMemorySize(callback: AsyncCallback\<number>): void

ArkTS-Sta: getAppMemorySize(callback: AsyncCallback\<int>): void

获取当前应用程序可以使用的内存的值。使用callback异步回调。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: : AsyncCallback&lt;int\> | 是 |获取当前应用程序可以使用的内存的值，可根据此值进行错误处理或其他自定义处理，单位是M。使用callback异步回调。|

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';

appManager.getAppMemorySize((err, data) => {
  if (err) {
    console.error(`getAppMemorySize fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info(`The size of app memory is: ${JSON.stringify(data)}`);
  }
})
```

## appManager.getRunningProcessInformation

getRunningProcessInformation(): Promise\<Array\<ProcessInformation>>

获取当前应用运行进程的相关信息。使用Promise异步回调。

> **说明：**
>
> - 对于API version 11之前的版本，该接口需要申请权限ohos.permission.GET_RUNNING_INFO（该权限仅系统应用可申请）。
> - 从API version 11开始，该接口仅用于获取调用方自身的进程信息，不再需要申请权限。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | 以Promise方式返回接口运行结果及有关运行进程的信息，可进行错误处理或其他自定义处理。 |

**错误码**：

以下错误码详细介绍请参考[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.getRunningProcessInformation().then((data) => {
  console.info(`The running process information is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${error.code} ${error.message}`);
});
```

## appManager.getRunningProcessInformation

getRunningProcessInformation(callback: AsyncCallback\<Array\<ProcessInformation>>): void

获取当前应用运行进程的相关信息。使用callback异步回调。

> **说明：**
>
> - 对于API version 11之前的版本，该接口需要申请权限ohos.permission.GET_RUNNING_INFO（该权限仅系统应用可申请）。
> - 从API version 11开始，该接口仅用于获取调用方自身的进程信息，不再需要申请权限。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | 是 |以callback方式返回接口运行结果及有关运行进程的信息，可进行错误处理或其他自定义处理。|

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.getRunningProcessInformation().then((data) => {
  console.info(`getRunningProcessInformation data length  ${data.length} `);
}).catch((err: Error) => {
  let error = err as BusinessError;
  console.error(`error: ${error.code} ${error.message}`);
});
```

## appManager.on('applicationState')<sup>14+</sup>

on(type: 'applicationState', observer: ApplicationStateObserver): number

注册全部应用程序的状态观测器。

**需要权限**：ohos.permission.RUNNING_STATE_OBSERVER

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 调用接口类型，固定填'applicationState'字符串。 |
| observer | [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) | 是 | 应用状态观测器，用于观测应用的生命周期变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 已注册观测器的数字代码，可用于off接口取消注册观测器。|

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let applicationStateObserver: appManager.ApplicationStateObserver = {
  onForegroundApplicationChanged(appStateData) {
    console.info(`[appManager] onForegroundApplicationChanged: ${JSON.stringify(appStateData)}`);
  },
  onAbilityStateChanged(abilityStateData) {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  },
  onProcessCreated(processData) {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  },
  onProcessDied(processData) {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  },
  onProcessStateChanged(processData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  },
  onAppStarted(appStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  },
  onAppStopped(appStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
};

try {
  const observerId = appManager.on('applicationState', applicationStateObserver);
  console.info(`[appManager] observerCode: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.onApplicationStateChange<sup>23+</sup>

onApplicationStateChange(observer: ApplicationStateObserver): int

注册全部应用程序的状态观测器。

**需要权限**：ohos.permission.RUNNING_STATE_OBSERVER

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                           |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------- |
| observer | [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) | 是   | 应用状态观测器，用于观测应用的生命周期变化。   |

**返回值：**

| 类型 | 说明                                                  |
| ---- | ----------------------------------------------------- |
| int  | 已注册观测器的数字代码，可用于off接口取消注册观测器。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 16000050 | Internal error.                                              |

**示例：**

```ts
// ArkTS-Sta示例
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class CustomApplicationStateObserver implements appManager.ApplicationStateObserver {
  public appStateData?: appManager.AppStateData;
  public abilityStateData?: appManager.AbilityStateData;
  public processData?: appManager.ProcessData;

  onForegroundApplicationChanged(appStateData: appManager.AppStateData): void {
    console.info(`[appManager] onForegroundApplicationChanged: ${JSON.stringify(appStateData)}`);
  }

  onAbilityStateChanged(abilityStateData: appManager.AbilityStateData): void {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  }

  onProcessCreated(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  }

  onProcessDied(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  }

  onProcessStateChanged(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  }

  onAppStarted(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  }

  onAppStopped(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
}

try {
  let applicationStateObserver = new CustomApplicationStateObserver();
  const observerId = appManager.onApplicationStateChange(applicationStateObserver);
  console.info(`[appManager] observerCode: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.on('applicationState')<sup>14+</sup>

on(type: 'applicationState', observer: ApplicationStateObserver, bundleNameList: Array\<string>): number

注册指定应用程序的状态观测器。

**需要权限**：ohos.permission.RUNNING_STATE_OBSERVER

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 调用接口类型，固定填'applicationState'字符串。 |
| observer | [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) | 是 | 应用状态观测器，用于观测应用的生命周期变化。 |
| bundleNameList | Array\<string> | 是 | 表示需要注册监听的bundleName数组。最大值128。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 已注册观测器的数字代码，可用于off接口注销观测器。|

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let applicationStateObserver: appManager.ApplicationStateObserver = {
  onForegroundApplicationChanged(appStateData) {
    console.info(`[appManager] onForegroundApplicationChanged: ${JSON.stringify(appStateData)}`);
  },
  onAbilityStateChanged(abilityStateData) {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  },
  onProcessCreated(processData) {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(abilityStateData)}`);
  },
  onProcessDied(processData) {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(abilityStateData)}`);
  },
  onProcessStateChanged(processData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(abilityStateData)}`);
  },
  onAppStarted(appStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  },
  onAppStopped(appStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
};

let bundleNameList = ['bundleName1', 'bundleName2'];

try {
  const observerId = appManager.on('applicationState', applicationStateObserver, bundleNameList);
  console.info(`[appManager] observerCode: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.onApplicationStateChange<sup>23+</sup>

 onApplicationStateChange(observer: ApplicationStateObserver, bundleNameList: Array\<string>): int

注册指定应用程序的状态观测器。

**需要权限**：ohos.permission.RUNNING_STATE_OBSERVER

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名         | 类型                                                         | 必填 | 说明                                          |
| -------------- | ------------------------------------------------------------ | ---- | --------------------------------------------- |
| observer       | [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) | 是   | 应用状态观测器，用于观测应用的生命周期变化。  |
| bundleNameList | Array\<string>                                               | 是   | 表示需要注册监听的bundleName数组。最大值128。 |

**返回值：**

| 类型 | 说明                                              |
| ---- | ------------------------------------------------- |
| int  | 已注册观测器的数字代码，可用于off接口注销观测器。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 16000050 | Internal error.                                              |

**示例：**

```ts
// ArkTS-Sta示例
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class CustomApplicationStateObserver implements appManager.ApplicationStateObserver {
  public appStateData?: appManager.AppStateData;
  public abilityStateData?: appManager.AbilityStateData;
  public processData?: appManager.ProcessData;

  onForegroundApplicationChanged(appStateData: appManager.AppStateData): void {
    console.info(`[appManager] onForegroundApplicationChanged: ${JSON.stringify(appStateData)}`);
  }

  onAbilityStateChanged(abilityStateData: appManager.AbilityStateData): void {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  }

  onProcessCreated(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  }

  onProcessDied(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  }

  onProcessStateChanged(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  }

  onAppStarted(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  }

  onAppStopped(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStopped:  ${JSON.stringify(appStateData)}`);
  }
}

try {
  let bundleNameList = ['bundleName1', 'bundleName2'];
  let applicationStateObserver = new CustomApplicationStateObserver();
  const observerId = appManager.onApplicationStateChange(applicationStateObserver, bundleNameList);
  console.info(`[appManager] observerCode: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.off('applicationState')<sup>14+</sup>

off(type: 'applicationState', observerId: number): Promise\<void>

取消注册应用程序状态观测器。使用Promise异步回调。

**需要权限**：ohos.permission.RUNNING_STATE_OBSERVER

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 调用接口类型，固定填'applicationState'字符串。 |
| observerId | number | 是 | 表示观测器的编号代码。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<void> | 以Promise方式返回接口运行结果，可进行错误处理或其他自定义处理。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 0;

// 1.注册应用状态监听器
let applicationStateObserver: appManager.ApplicationStateObserver = {
  onForegroundApplicationChanged(appStateData) {
    console.info(`[appManager] onForegroundApplicationChanged:  ${JSON.stringify(appStateData)}`);
  },
  onAbilityStateChanged(abilityStateData) {
    console.info(`[appManager] onAbilityStateChanged:  ${JSON.stringify(abilityStateData)}`);
  },
  onProcessCreated(processData) {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  },
  onProcessDied(processData) {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  },
  onProcessStateChanged(processData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  },
  onAppStarted(appStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  },
  onAppStopped(appStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
};
let bundleNameList = ['bundleName1', 'bundleName2'];

try {
  observerId = appManager.on('applicationState', applicationStateObserver, bundleNameList);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

// 2.注销应用状态监听器
try {
  appManager.off('applicationState', observerId).then((data) => {
    console.info(`unregisterApplicationStateObserver success, data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`unregisterApplicationStateObserver fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.offApplicationStateChange<sup>23+</sup>

offApplicationStateChange(observerId: int): Promise\<void>

取消注册应用程序状态观测器。使用Promise异步回调。

**需要权限**：ohos.permission.RUNNING_STATE_OBSERVER

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型   | 必填 | 说明                                           |
| ---------- | ------ | ---- | ---------------------------------------------- |
| observerId | int    | 是   | 表示观测器的编号代码。                         |

**返回值：**

| 类型           | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| Promise\<void> | 以Promise方式返回接口运行结果，可进行错误处理或其他自定义处理。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 16000050 | Internal error.                                              |

**示例：**

```ts
// ArkTS-Sta示例
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 0;

// 1.注册应用状态监听器
class CustomApplicationStateObserver implements appManager.ApplicationStateObserver {
  public appStateData?: appManager.AppStateData;
  public abilityStateData?: appManager.AbilityStateData;
  public processData?: appManager.ProcessData;

  onForegroundApplicationChanged(appStateData: appManager.AppStateData): void {
    console.info(`[appManager] onForegroundApplicationChanged: ${JSON.stringify(appStateData)}`);
  }

  onAbilityStateChanged(abilityStateData: appManager.AbilityStateData): void {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  }

  onProcessCreated(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  }

  onProcessDied(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  }

  onProcessStateChanged(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  }

  onAppStarted(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  }

  onAppStopped(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
}

let bundleNameList = ['bundleName1', 'bundleName2'];

try {
  let applicationStateObserver = new CustomApplicationStateObserver();
  observerId = appManager.onApplicationStateChange(applicationStateObserver, bundleNameList);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

// 2.注销应用状态监听器
try {
  appManager.offApplicationStateChange(observerId).then(() => {
    console.info(`unregisterApplicationStateObserver success`);
  }).catch((err: Error) => {
    console.error(`unregisterApplicationStateObserver fail, err: ${err.message}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.off('applicationState')<sup>15+</sup>

off(type: 'applicationState', observerId: number, callback: AsyncCallback\<void>): void

取消注册应用程序状态观测器。使用callback异步回调。

**需要权限**：ohos.permission.RUNNING_STATE_OBSERVER

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 15

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 调用接口类型，固定填'applicationState'字符串。 |
| observerId | number | 是 | 表示观测器的编号代码。 |
| callback | AsyncCallback\<void> | 是 | 回调函数。当取消注册应用程序状态观测器成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 0;

// 1.注册应用状态监听器
let applicationStateObserver: appManager.ApplicationStateObserver = {
  onForegroundApplicationChanged(appStateData) {
    console.info(`[appManager] onForegroundApplicationChanged: ${JSON.stringify(appStateData)}`);
  },
  onAbilityStateChanged(abilityStateData) {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  },
  onProcessCreated(processData) {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  },
  onProcessDied(processData) {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  },
  onProcessStateChanged(processData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  },
  onAppStarted(appStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  },
  onAppStopped(appStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
};
let bundleNameList = ['bundleName1', 'bundleName2'];

try {
  observerId = appManager.on('applicationState', applicationStateObserver, bundleNameList);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

function offCallback(err: BusinessError) {
  if (err) {
    console.error(`appmanager.off failed, code: ${err.code}, msg: ${err.message}`);
  } else {
    console.info(`appmanager.off success.`);
  }
}

// 2.注销应用状态监听器
try {
  appManager.off('applicationState', observerId, offCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.offApplicationStateChange<sup>23+</sup>

offApplicationStateChange(observerId: int, callback: AsyncCallback\<void>): void

取消注册应用程序状态观测器。使用callback异步回调。

**需要权限**：ohos.permission.RUNNING_STATE_OBSERVER

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                 | 必填 | 说明                                                         |
| ---------- | -------------------- | ---- | ------------------------------------------------------------ |
| observerId | int                  | 是   | 表示观测器的编号代码。                                       |
| callback   | AsyncCallback\<void> | 是   | 回调函数。当取消注册应用程序状态观测器成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 16000050 | Internal error.                                              |

**示例：**

```ts
// ArkTS-Sta示例
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 0;

// 1.注册应用状态监听器
class CustomApplicationStateObserver implements appManager.ApplicationStateObserver {
  public appStateData?: appManager.AppStateData;
  public abilityStateData?: appManager.AbilityStateData;
  public processData?: appManager.ProcessData;

  onForegroundApplicationChanged(appStateData: appManager.AppStateData): void {
    console.info(`[appManager] onForegroundApplicationChanged: ${JSON.stringify(appStateData)}`);
  }

  onAbilityStateChanged(abilityStateData: appManager.AbilityStateData): void {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  }

  onProcessCreated(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  }

  onProcessDied(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  }

  onProcessStateChanged(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  }

  onAppStarted(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  }

  onAppStopped(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
}

let bundleNameList = ['bundleName1', 'bundleName2'];

try {
  let applicationStateObserver = new CustomApplicationStateObserver();
  observerId = appManager.onApplicationStateChange(applicationStateObserver, bundleNameList);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

function offCallback(err: BusinessError<void> | null) {
  if (err) {
    console.error(`appmanager.off failed, code: ${err.code}, msg: ${err.message}`);
  } else {
    console.info(`appmanager.off success.`);
  }
}

// 2.注销应用状态监听器
try {
  appManager.offApplicationStateChange(observerId, offCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.killProcessesByBundleName<sup>14+</sup>

ArkTS-Dyn: killProcessesByBundleName(bundleName: string, clearPageStack: boolean, appIndex?: number): Promise\<void>

ArkTS-Sta: killProcessesByBundleName(bundleName: string, clearPageStack: boolean, appIndex?: int): Promise\<void>

通过Bundle名称终止进程。使用Promise异步回调。

**需要权限**：ohos.permission.KILL_APP_PROCESSES 或 ohos.permission.CLEAN_BACKGROUND_PROCESSES

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| bundleName | string | 是 | 表示Bundle名称。 |
| clearPageStack | boolean | 是 | 表示是否清除页面堆栈。true表示清除，false表示不清除。 |
| appIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 应用分身Id，默认值为0。取值为0时，表示终止主应用的所有进程。取值大于0时，表示终止指定分身应用的所有进程。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 401 | If the input parameter is not valid parameter. |
| 16000050 | Internal error. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let isClearPageStack = false;
let appIndex = 1;

try {
  appManager.killProcessesByBundleName(bundleName, isClearPageStack, appIndex).then((data) => {
    console.info('killProcessesByBundleName success.');
  }).catch((error: Error) => {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error(`killProcessesByBundleName fail, err: ${code}, ${message}}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.isAppRunning<sup>14+</sup>

ArkTS-Dyn: isAppRunning(bundleName: string, appCloneIndex?: number): Promise\<boolean>

ArkTS-Sta: isAppRunning(bundleName: string, appCloneIndex?: int): Promise\<boolean>

判断应用是否在运行。使用Promise异步回调。

**需要权限**：ohos.permission.GET_RUNNING_INFO

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| bundleName | string | 是 | 查询的应用包名。 |
| appCloneIndex | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 分身应用索引。 |

**返回值：**

| 类型           | 说明              |
| -------------- | ---------------- |
| Promise\<boolean> | Promise对象。返回true表示应用正在运行，返回false表示应用未运行。 |

**错误码**：

  以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16000050 | Internal error. |
| 16000073 | The app clone index is invalid. |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = "ohos.samples.etsclock";
  appManager.isAppRunning(bundleName).then((data: boolean) => {
    hilog.info(0x0000, 'testTag', `data: ${data}`);
  }).catch((error: Error) => {
    let err = error as BusinessError;
    hilog.error(0x0000, 'testTag', `isAppRunning error, code: ${err.code}, msg:${err.message}`);
  })
} catch (error) {
  let err = error as BusinessError;
  hilog.error(0x0000, 'testTag', `isAppRunning error, code: ${err.code}, msg:${err.message}`);
}
```

## AbilityStateData<sup>14+</sup>

type AbilityStateData = _AbilityStateData.default

Ability状态信息。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅支持ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 14

| 类型 | 说明 |
| --- | --- |
| [_AbilityStateData.default](js-apis-inner-application-abilityStateData.md) | Ability状态信息。 |

## AbilityStateData<sup>23+</sup>

type AbilityStateData = _AbilityStateData

Ability状态信息。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅支持ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明              |
| ------------------------------------------------------------ | ----------------- |
| [_AbilityStateData](js-apis-inner-application-abilityStateData.md) | Ability状态信息。 |

## AppStateData<sup>14+</sup>

type AppStateData = _AppStateData.default

应用状态信息。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅支持ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 14

| 类型 | 说明 |
| --- | --- |
| [_AppStateData.default](js-apis-inner-application-appStateData.md) | 应用状态信息。 |

## AppStateData<sup>23+</sup>

type AppStateData = _AppStateData

应用状态信息。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅支持ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                       | 说明           |
| ---------------------------------------------------------- | -------------- |
| [_AppStateData](js-apis-inner-application-appStateData.md) | 应用状态信息。 |

## ApplicationStateObserver<sup>14+</sup>

type ApplicationStateObserver = _ApplicationStateObserver.default

ApplicationStateObserver模块。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅支持ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 14

| 类型 | 说明 |
| --- | --- |
| [_ApplicationStateObserver.default](js-apis-inner-application-applicationStateObserver.md) | ApplicationStateObserver模块。 |

## ApplicationStateObserver<sup>23+</sup>

type ApplicationStateObserver = _ApplicationStateObserver

ApplicationStateObserver模块。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅支持ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                           |
| ------------------------------------------------------------ | ------------------------------ |
| [_ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) | ApplicationStateObserver模块。 |

## ProcessInformation

type ProcessInformation = _ProcessInformation

ProcessInformation模块。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 类型 | 说明 |
| --- | --- |
| [_ProcessInformation](js-apis-inner-application-processInformation.md) | ProcessInformation模块。 |

## ProcessData<sup>14+</sup>

type ProcessData = _ProcessData.default

进程数据。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅支持ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 14

| 类型 | 说明 |
| --- | --- |
| [_ProcessData.default](js-apis-inner-application-processData.md) | 进程数据。 |

## ProcessData<sup>23+</sup>

type ProcessData = _ProcessData

进程数据。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 该接口仅支持ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                     | 说明       |
| -------------------------------------------------------- | ---------- |
| [_ProcessData](js-apis-inner-application-processData.md) | 进程数据。 |