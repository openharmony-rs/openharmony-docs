# @ohos.app.ability.launchServiceManager (LaunchService管理)(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

launchServiceManager模块的系统接口提供已注册LaunchService信息查询、应用LaunchService启用状态管理及状态监听能力。

当系统应用需要集中管理启动服务时，可通过[getAllRegisteredInformation](#launchservicemanagergetallregisteredinformation)查询指定用户或所有用户下已注册的LaunchService，并通过[setLaunchServicesEnabled](#launchservicemanagersetlaunchservicesenabled)设置目标应用LaunchService的启用状态。例如，在启动服务管理界面中，可展示已注册的服务信息，结合[onLaunchServiceObserver](#launchservicemanageronlaunchserviceobserver)监听服务注册、注销及进程启动、停止事件，及时更新界面；不再需要监听时，可通过[offLaunchServiceObserver](#launchservicemanagerofflaunchserviceobserver)注销观察者。

> **说明：**
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[LaunchService管理](js-apis-app-ability-launchServiceManager.md)。

**起始版本**：26.1.0

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

## 导入模块

```ts
import { launchServiceManager } from '@kit.AbilityKit';
```

## LaunchServiceProcessState

定义LaunchService进程状态的枚举类型，用于[LaunchServiceProcessStateData](js-apis-app-ability-launchServiceProcessStateData-sys.md)。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| CREATED | 0 | LaunchService进程已创建。 |
| TERMINATED | 1 | LaunchService进程已终止。 |

## launchServiceManager.getAllRegisteredInformation

getAllRegisteredInformation(userId?: number): Promise&lt;Array&lt;LaunchServiceInformation&gt;&gt;

获取所有已注册的LaunchService信息。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MANAGE_DAEMON_SERVICE

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| userId | number | 否 | 指定userId时，查询该userId下已注册的LaunchService；未指定userId时，查询所有用户下已注册的LaunchService。<br>取值限定为非负整数。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;Array&lt;[LaunchServiceInformation](js-apis-app-ability-launchServiceInformation.md)&gt;&gt; | Promise对象，返回一个LaunchService的数组信息。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| 16000050 | System service connection failed. |

**示例**：

以下示例中的包名、模块名、服务名及用户ID需替换为实际值，调用前需具备所需权限。

```ts
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 不传入userId，查询所有用户下已注册的LaunchService信息
  launchServiceManager.getAllRegisteredInformation().then((result) => {
    console.info(`Operation succeeded: ${JSON.stringify(result)}`);
  }).catch((error: BusinessError) => {
    console.error(`Operation failed: ${error.code}, ${error.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

## launchServiceManager.setLaunchServicesEnabled

setLaunchServicesEnabled(bundleName: string, userId: number, appIndex: number, enabled: boolean, token?: Uint8Array): Promise&lt;void&gt;

设置应用LaunchService的启用状态。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MANAGE_DAEMON_SERVICE

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| bundleName | string | 是 | 目标应用包名。 |
| userId | number | 是 | 目标应用用户ID。<br>取值限定为非负整数。 |
| appIndex | number | 是 | 目标应用分身索引。<br>取值限定为非负整数。 |
| enabled | boolean | 是 | 设置的启用状态。true表示启用，false表示禁用。 |
| token | Uint8Array | 否 | 用于批准该操作的身份验证令牌。若传递了该令牌，直接使用该令牌进行鉴权；未传递时将拉起用户授权界面。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| 16000050 | System service connection failed. |
| 16000215 | The approval request was rejected. |
| 16300005 | The target bundle does not exist. |

**示例**：

以下示例中的包名、模块名、服务名及用户ID需替换为实际值，调用前需具备所需权限。

```ts
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 启用用户ID为100的指定应用（appIndex为0，表示主应用）的LaunchService。
  // 本示例未传入token，调用时将拉起用户授权界面。
  launchServiceManager.setLaunchServicesEnabled('com.example.launchservice', 100, 0, true).then((result) => {
    console.info(`Operation succeeded: ${JSON.stringify(result)}`);
  }).catch((error: BusinessError) => {
    console.error(`Operation failed: ${error.code}, ${error.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

## launchServiceManager.onLaunchServiceObserver

onLaunchServiceObserver(observer: LaunchServiceObserver): number

注册一个观察者来监听LaunchService状态和进程状态的变化。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MANAGE_DAEMON_SERVICE

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| observer | [LaunchServiceObserver](js-apis-app-ability-launchServiceObserver-sys.md) | 是 | 用于监听LaunchService状态和进程状态变化的观察者。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| number | 注册的观察者ID。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| 16000050 | System service connection failed. |
| 16000165 | The number of registered observers for the current application has reached the upper limit. |

**示例**：

以下示例中的包名、模块名、服务名及用户ID需替换为实际值，调用前需具备所需权限。

```ts
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 定义LaunchService状态变化观察者
const observer: launchServiceManager.LaunchServiceObserver = {
  // 服务注册或注销时接收状态变化通知
  onLaunchServiceRegisteredChanged: (data: Array<launchServiceManager.LaunchServiceStateData>) => {
    console.info(JSON.stringify(data));
  },
  // 服务进程启动或停止时接收状态变化通知
  onLaunchServiceProcessStateChanged: (data: launchServiceManager.LaunchServiceProcessStateData) => {
    console.info(JSON.stringify(data));
  }
};
try {
  // 注册观察者，返回的ID用于后续注销监听
  const observerId = launchServiceManager.onLaunchServiceObserver(observer);
  console.info(`Observer ID: ${observerId}`);
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

## launchServiceManager.offLaunchServiceObserver

offLaunchServiceObserver(observerId: number): Promise&lt;void&gt;

注销用于监听LaunchService状态和进程状态更改的观察者。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MANAGE_DAEMON_SERVICE

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| observerId | number | 是 | 注册的观察者ID。<br>取值限定为正整数。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| 16000050 | System service connection failed. |
| 16000216 | The specified id is invalid. |

**示例**：

以下示例中的包名、模块名、服务名及用户ID需替换为实际值，调用前需具备所需权限。

```ts
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 定义LaunchService状态变化观察者
const observer: launchServiceManager.LaunchServiceObserver = {
  // 服务注册或注销时接收状态变化通知
  onLaunchServiceRegisteredChanged: (data: Array<launchServiceManager.LaunchServiceStateData>) => {
    console.info(JSON.stringify(data));
  },
  // 服务进程启动或停止时接收状态变化通知
  onLaunchServiceProcessStateChanged: (data: launchServiceManager.LaunchServiceProcessStateData) => {
    console.info(JSON.stringify(data));
  }
};
// 注册观察者，返回的ID用于后续注销监听
const observerId = launchServiceManager.onLaunchServiceObserver(observer);
try {
  // 使用注册时返回的观察者ID注销监听
  launchServiceManager.offLaunchServiceObserver(observerId).then((result) => {
    console.info(`Operation succeeded: ${JSON.stringify(result)}`);
  }).catch((error: BusinessError) => {
    console.error(`Operation failed: ${error.code}, ${error.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

## LaunchServiceProcessStateData

type LaunchServiceProcessStateData = _LaunchServiceProcessStateData

描述LaunchService进程状态变化数据，包含服务描述符、进程pid和进程状态。作为[onLaunchServiceProcessStateChanged](js-apis-app-ability-launchServiceObserver-sys.md#onlaunchserviceprocessstatechanged)回调的processStateData参数，在服务进程启动或停止时传递。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| [_LaunchServiceProcessStateData](js-apis-app-ability-launchServiceProcessStateData-sys.md) | 定义LaunchService进程状态变化数据结构体。 |

## LaunchServiceObserver

type LaunchServiceObserver = _LaunchServiceObserver

定义LaunchService状态和进程状态变化的观察者。作为[onLaunchServiceObserver](js-apis-app-ability-launchServiceManager-sys.md#launchservicemanageronlaunchserviceobserver)接口的observer参数，用于接收服务注册、注销及进程启动、停止的通知。通过[offLaunchServiceObserver](js-apis-app-ability-launchServiceManager-sys.md#launchservicemanagerofflaunchserviceobserver)接口传入注册时返回的观察者ID，可注销监听。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| [_LaunchServiceObserver](js-apis-app-ability-launchServiceObserver-sys.md) | 定义LaunchService状态和进程状态变化的观察者。 |

## LaunchServiceStateData

type LaunchServiceStateData = _LaunchServiceStateData

描述LaunchService注册状态变化数据，包含服务描述符和变化后的注册状态。作为[onLaunchServiceRegisteredChanged](js-apis-app-ability-launchServiceObserver-sys.md#onlaunchserviceregisteredchanged)回调的stateDataList数组中的元素，在服务注册或注销时传递。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| [_LaunchServiceStateData](js-apis-app-ability-launchServiceStateData-sys.md) | 定义LaunchService状态变化数据结构体。 |
