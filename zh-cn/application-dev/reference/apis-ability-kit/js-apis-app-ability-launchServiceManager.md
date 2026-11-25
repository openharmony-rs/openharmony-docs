# @ohos.app.ability.launchServiceManager (LaunchService管理)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

launchServiceManager模块提供LaunchService注册、注销、进程启动、停止及信息查询能力。

当应用需要将模块内的可执行程序作为启动服务运行时，可在module.json5配置文件的[launchServices标签](../../quick-start/module-configuration-file.md#launchservices标签)中声明服务，并通过本模块管理服务。例如，应用可注册自身声明的LaunchService，在服务已注册且启用后按需启动或停止其进程，并查询服务状态和进程信息；不再需要该服务时，可注销服务。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

## 导入模块

```ts
import { launchServiceManager } from '@kit.AbilityKit';
```

## LaunchServiceState

定义LaunchService状态的枚举类型，用于[LaunchServiceInformation](js-apis-app-ability-launchServiceInformation.md)。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| NOT_REGISTERED | 0 | LaunchService未注册。<br>**ArkTS-Dyn起始版本：** 26.1.0<br>**ArkTS-Sta起始版本：** 26.1.0 |
| ENABLED | 1 | LaunchService已注册并启用。<br>**ArkTS-Dyn起始版本：** 26.1.0<br>**ArkTS-Sta起始版本：** 26.1.0 |
| DISABLED | 2 | LaunchService已注册，但被禁用。<br>**ArkTS-Dyn起始版本：** 26.1.0<br>**ArkTS-Sta起始版本：** 26.1.0 |

## launchServiceManager.register

register(descriptor: LaunchServiceDescriptor): Promise&lt;void&gt;

注册LaunchService。使用Promise异步回调。

> **说明：**
>
> 在module.json5配置文件中将runAtLoad设置为true，且服务注册成功，状态为ENABLED，系统将自动启动LaunchService进程。
>
> 仅允许包含该LaunchService的应用自身进行注册，且需根据应用类型申请对应权限：
>
> - 普通应用（非MDM应用）：需申请ohos.permission.REGISTER_DAEMON_SERVICE权限。
> - MDM应用：需申请ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE权限。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**需要权限**：ohos.permission.REGISTER_DAEMON_SERVICE 或 ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| descriptor | [LaunchServiceDescriptor](js-apis-app-ability-launchServiceDescriptor.md) | 是 | 要注册的LaunchService的描述符。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 801 | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| 16000050 | System service connection failed. |
| 16000211 | The specified service is not found. |
| 16000212 | The specified service is already registered. |

**示例**：

以下示例中的包名、模块名、服务名及用户ID需替换为实际值，调用前需具备所需权限。

ArkTS-Dyn示例：

```ts
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 构造服务描述符，包名、模块名和服务名需替换为实际值
const descriptor: launchServiceManager.LaunchServiceDescriptor = {
  bundleName: 'com.example.launchservice',
  moduleName: 'entry',
  serviceName: 'ExampleService'
};
try {
  // 注册LaunchService
  launchServiceManager.register(descriptor).then((result) => {
    console.info(`Operation succeeded: ${JSON.stringify(result)}`);
  }).catch((error: BusinessError) => {
    console.error(`Operation failed: ${error.code}, ${error.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 构造服务描述符，包名、模块名和服务名需替换为实际值
const descriptor: launchServiceManager.LaunchServiceDescriptor = {
  bundleName: 'com.example.launchservice',
  moduleName: 'entry',
  serviceName: 'ExampleService'
};
try {
  // 注册LaunchService
  launchServiceManager.register(descriptor).then(() => {
    console.info('Operation succeeded.');
  }).catch((error: Error) => {
    const err = error as BusinessError;
    console.error(`Operation failed: ${err.code}, ${err.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

## launchServiceManager.unregister

unregister(descriptor: LaunchServiceDescriptor): Promise&lt;void&gt;

注销LaunchService。使用Promise异步回调。

> **说明：**
>
> 若LaunchService进程正在运行，注销时系统将停止该进程。
>
> 仅允许包含该LaunchService的应用自身进行注销，且需根据应用类型申请对应权限：
>
> - 普通应用（非MDM应用）：需申请ohos.permission.REGISTER_DAEMON_SERVICE权限。
> - MDM应用：需申请ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE权限。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**需要权限**：ohos.permission.REGISTER_DAEMON_SERVICE 或 ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| descriptor | [LaunchServiceDescriptor](js-apis-app-ability-launchServiceDescriptor.md) | 是 | 要注销的LaunchService的描述符。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 801 | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| 16000050 | System service connection failed. |
| 16000211 | The specified service is not found. |

**示例**：

以下示例中的包名、模块名、服务名及用户ID需替换为实际值，调用前需具备所需权限。

ArkTS-Dyn示例：

```ts
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 构造服务描述符，包名、模块名和服务名需替换为实际值
const descriptor: launchServiceManager.LaunchServiceDescriptor = {
  bundleName: 'com.example.launchservice',
  moduleName: 'entry',
  serviceName: 'ExampleService'
};
try {
  // 注销LaunchService，正在运行的服务进程将被停止
  launchServiceManager.unregister(descriptor).then((result) => {
    console.info(`Operation succeeded: ${JSON.stringify(result)}`);
  }).catch((error: BusinessError) => {
    console.error(`Operation failed: ${error.code}, ${error.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 构造服务描述符，包名、模块名和服务名需替换为实际值
const descriptor: launchServiceManager.LaunchServiceDescriptor = {
  bundleName: 'com.example.launchservice',
  moduleName: 'entry',
  serviceName: 'ExampleService'
};
try {
  // 注销LaunchService，正在运行的服务进程将被停止
  launchServiceManager.unregister(descriptor).then(() => {
    console.info('Operation succeeded.');
  }).catch((error: Error) => {
    const err = error as BusinessError;
    console.error(`Operation failed: ${err.code}, ${err.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

## launchServiceManager.start

start(descriptor: LaunchServiceDescriptor): Promise&lt;void&gt;

启动LaunchService进程。使用Promise异步回调。

> **说明：**
>
> 调用此接口前，必须确保LaunchService已完成注册且处于启动（ENABLED）状态。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**需要权限**：ohos.permission.USE_DAEMON_SERVICE

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| descriptor | [LaunchServiceDescriptor](js-apis-app-ability-launchServiceDescriptor.md) | 是 | 要启动的LaunchService的描述符。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 801 | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| 16000050 | System service connection failed. |
| 16000211 | The specified service is not found. |
| 16000213 | The specified service is disabled. |

**示例**：

以下示例中的包名、模块名、服务名及用户ID需替换为实际值，调用前需具备所需权限。

ArkTS-Dyn示例：

```ts
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 构造服务描述符，包名、模块名和服务名需替换为实际值
const descriptor: launchServiceManager.LaunchServiceDescriptor = {
  bundleName: 'com.example.launchservice',
  moduleName: 'entry',
  serviceName: 'ExampleService'
};
try {
  // 启动服务进程，调用前需确保LaunchService已注册并启用
  launchServiceManager.start(descriptor).then((result) => {
    console.info(`Operation succeeded: ${JSON.stringify(result)}`);
  }).catch((error: BusinessError) => {
    console.error(`Operation failed: ${error.code}, ${error.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 构造服务描述符，包名、模块名和服务名需替换为实际值
const descriptor: launchServiceManager.LaunchServiceDescriptor = {
  bundleName: 'com.example.launchservice',
  moduleName: 'entry',
  serviceName: 'ExampleService'
};
try {
  // 启动服务进程，调用前需确保LaunchService已注册并启用
  launchServiceManager.start(descriptor).then(() => {
    console.info('Operation succeeded.');
  }).catch((error: Error) => {
    const err = error as BusinessError;
    console.error(`Operation failed: ${err.code}, ${err.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

## launchServiceManager.stop

stop(descriptor: LaunchServiceDescriptor): Promise&lt;void&gt;

停止LaunchService进程。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**需要权限**：ohos.permission.USE_DAEMON_SERVICE

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| descriptor | [LaunchServiceDescriptor](js-apis-app-ability-launchServiceDescriptor.md) | 是 | 要停止的LaunchService的描述符。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 801 | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| 16000050 | System service connection failed. |
| 16000211 | The specified service is not found. |
| 16000214 | The specified service is not running. |

**示例**：

以下示例中的包名、模块名、服务名及用户ID需替换为实际值，调用前需具备所需权限。

ArkTS-Dyn示例：

```ts
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 构造服务描述符，包名、模块名和服务名需替换为实际值
const descriptor: launchServiceManager.LaunchServiceDescriptor = {
  bundleName: 'com.example.launchservice',
  moduleName: 'entry',
  serviceName: 'ExampleService'
};
try {
  // 停止LaunchService进程
  launchServiceManager.stop(descriptor).then((result) => {
    console.info(`Operation succeeded: ${JSON.stringify(result)}`);
  }).catch((error: BusinessError) => {
    console.error(`Operation failed: ${error.code}, ${error.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 构造服务描述符，包名、模块名和服务名需替换为实际值
const descriptor: launchServiceManager.LaunchServiceDescriptor = {
  bundleName: 'com.example.launchservice',
  moduleName: 'entry',
  serviceName: 'ExampleService'
};
try {
  // 停止LaunchService进程
  launchServiceManager.stop(descriptor).then(() => {
    console.info('Operation succeeded.');
  }).catch((error: Error) => {
    const err = error as BusinessError;
    console.error(`Operation failed: ${err.code}, ${err.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

## launchServiceManager.getInformation

getInformation(descriptor: LaunchServiceDescriptor): Promise&lt;LaunchServiceInformation&gt;

获取指定LaunchService的信息。使用Promise异步回调。

> **说明：**
>
> 如果应用程序已安装，但LaunchService未注册，返回的状态为NOT_REGISTERED，pid为0。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**需要权限**：ohos.permission.USE_DAEMON_SERVICE

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| descriptor | [LaunchServiceDescriptor](js-apis-app-ability-launchServiceDescriptor.md) | 是 | 要查询的LaunchService的描述符。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[LaunchServiceInformation](js-apis-app-ability-launchServiceInformation.md)&gt; | Promise对象，用于返回LaunchService信息。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 801 | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| 16000050 | System service connection failed. |
| 16000211 | The specified service is not found. |

**示例**：

以下示例中的包名、模块名、服务名及用户ID需替换为实际值，调用前需具备所需权限。

ArkTS-Dyn示例：

```ts
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 构造服务描述符，包名、模块名和服务名需替换为实际值
const descriptor: launchServiceManager.LaunchServiceDescriptor = {
  bundleName: 'com.example.launchservice',
  moduleName: 'entry',
  serviceName: 'ExampleService'
};
try {
  // 查询指定LaunchService的信息
  launchServiceManager.getInformation(descriptor).then((result) => {
    console.info(`Operation succeeded: ${JSON.stringify(result)}`);
  }).catch((error: BusinessError) => {
    console.error(`Operation failed: ${error.code}, ${error.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'
import { launchServiceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 构造服务描述符，包名、模块名和服务名需替换为实际值
const descriptor: launchServiceManager.LaunchServiceDescriptor = {
  bundleName: 'com.example.launchservice',
  moduleName: 'entry',
  serviceName: 'ExampleService'
};
try {
  // 查询指定LaunchService的信息
  launchServiceManager.getInformation(descriptor).then((result: launchServiceManager.LaunchServiceInformation) => {
    console.info(`Operation succeeded: ${JSON.stringify(result)}`);
  }).catch((error: Error) => {
    const err = error as BusinessError;
    console.error(`Operation failed: ${err.code}, ${err.message}`);
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Operation failed: ${err.code}, ${err.message}`);
}
```

## LaunchServiceInformation

type LaunchServiceInformation = _LaunchServiceInformation

描述LaunchService的信息，包含服务描述符、注册及启用状态和进程pid。作为[getInformation](js-apis-app-ability-launchServiceManager.md#launchservicemanagergetinformation)接口的返回结果，以及getAllRegisteredInformation接口返回数组中的元素。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

| 类型 | 说明 |
| --- | --- |
| [_LaunchServiceInformation](js-apis-app-ability-launchServiceInformation.md) | 定义LaunchService信息结构体。 |

## LaunchServiceDescriptor

type LaunchServiceDescriptor = _LaunchServiceDescriptor

描述LaunchService的所属应用、模块、服务名称，以及用户和应用分身信息。作为[register](js-apis-app-ability-launchServiceManager.md#launchservicemanagerregister)、[unregister](js-apis-app-ability-launchServiceManager.md#launchservicemanagerunregister)、[start](js-apis-app-ability-launchServiceManager.md#launchservicemanagerstart)、[stop](js-apis-app-ability-launchServiceManager.md#launchservicemanagerstop)、[getInformation](js-apis-app-ability-launchServiceManager.md#launchservicemanagergetinformation)接口的descriptor参数，用于指定要操作或查询的LaunchService。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

| 类型 | 说明 |
| --- | --- |
| [_LaunchServiceDescriptor](js-apis-app-ability-launchServiceDescriptor.md) | 定义LaunchService的描述符。 |
