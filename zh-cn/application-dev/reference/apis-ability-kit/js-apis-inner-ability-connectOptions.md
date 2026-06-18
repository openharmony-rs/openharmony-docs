# ConnectOptions
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yewei0794-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

在连接指定的后台服务时作为入参，用于接收连接过程中的状态变化，如作为[connectServiceExtensionAbility](js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability)的入参，连接指定的ServiceExtensionAbility。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  

## 导入模块

```ts
import { common } from '@kit.AbilityKit';
```

## ConnectOptions

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 名称         | 类型                                | 只读 | 可选 | 说明                                                         |
| ------------ | ----------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| onConnect    | [OnConnectFn](#onconnectfn23)       | 否   | 否   | 与指定的后台服务成功建立连接时，会触发该回调。<br/>**说明**：<br/>从API version 23开始，原来的onConnect()方法变更为当前属性，调用方式不变。 |
| onDisconnect | [OnDisconnectFn](#ondisconnectfn23) | 否   | 否   | 与指定的后台服务成功断开连接时，会触发该回调。<br/>**说明**：<br/>从API version 23开始，原来的onDisconnect()方法变更为当前属性，调用方式不变。 |
| onFailed     | [OnFailedFn](#onfailedfn23)         | 否   | 否   | 与指定的后台服务建立连接失败时，会触发该回调。<br/>**说明**：<br/>从API version 23开始，原来的onFailed()方法变更为当前属性，调用方式不变。 |

### onConnect

onConnect(elementName: ElementName, remote: rpc.IRemoteObject): void

建立连接时的回调函数。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 7

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明                                              |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------- |
| elementName | [ElementName](js-apis-bundleManager-elementName.md)          | 是   | 目标Ability的elementName。                        |
| remote      | [rpc.IRemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject) | 是   | 用于与目标Ability进行IPC通信的IRemoteObject实例。 |

**示例：**

```ts
import { UIAbility, common, Want, AbilityConstant } from '@kit.AbilityKit';
import { bundleManager } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

let connectWant: Want = {
  bundleName: 'com.example.myapp',
  abilityName: 'MyAbility'
};

let connectOptions: common.ConnectOptions = {
  onConnect(elementName: bundleManager.ElementName, remote: rpc.IRemoteObject) {
    console.info(`onConnect elementName: ${elementName}`);
  },
  onDisconnect(elementName: bundleManager.ElementName) {
    console.info(`onDisconnect elementName: ${elementName}`);
  },
  onFailed(code: number) {
    console.error(`onFailed code: ${code}`);
  }
};

class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let connection: number = this.context.connectServiceExtensionAbility(connectWant, connectOptions);
  }
}
```

### onDisconnect

onDisconnect(elementName: ElementName): void

断开连接时的回调函数。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 7

**参数：**

| 参数名      | 类型                                                | 必填 | 说明                       |
| ----------- | --------------------------------------------------- | ---- | -------------------------- |
| elementName | [ElementName](js-apis-bundleManager-elementName.md) | 是   | 目标Ability的elementName。 |

**示例：**

```ts
import { UIAbility, common, Want, AbilityConstant } from '@kit.AbilityKit';
import { bundleManager } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

let connectWant: Want = {
  bundleName: 'com.example.myapp',
  abilityName: 'MyAbility'
};

let connectOptions: common.ConnectOptions = {
  onConnect(elementName: bundleManager.ElementName, remote: rpc.IRemoteObject) {
    console.info(`onConnect elementName: ${elementName}`);
  },
  onDisconnect(elementName: bundleManager.ElementName) {
    console.info(`onDisconnect elementName: ${elementName}`);
  },
  onFailed(code: number) {
    console.error(`onFailed code: ${code}`);
  }
};

class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let connection: number = this.context.connectServiceExtensionAbility(connectWant, connectOptions);
  }
}
```

### onFailed

onFailed(code: number): void

连接失败时的回调函数。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 7

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| code   | number | 是   | 连接指定Ability失败返回的错误码。<br>错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。<br> 201 - The application does not have permission to call the interface.<br> 16000001 - The specified ability does not exist.<br> 16000002 - Incorrect ability type.<br> 16000004 - Cannot start an invisible component.<br> 16000005 - The specified process does not have the permission.<br> 16000006 - Cross-user operations are not allowed.<br> 16000008 - The crowdtesting application expires.<br> 16000053 - The ability is not on the top of the UI.<br> 16000055 - Installation-free timed out.<br> 16000050 - Internal error. |


**示例：**

```ts
import { UIAbility, common, Want, AbilityConstant } from '@kit.AbilityKit';
import { bundleManager } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

let connectWant: Want = {
  bundleName: 'com.example.myapp',
  abilityName: 'MyAbility'
};

let connectOptions: common.ConnectOptions = {
  onConnect(elementName: bundleManager.ElementName, remote: rpc.IRemoteObject) {
    console.info(`onConnect elementName: ${elementName}`);
  },
  onDisconnect(elementName: bundleManager.ElementName) {
    console.info(`onDisconnect elementName: ${elementName}`);
  },
  onFailed(code: number) {
    console.error(`onFailed code: ${code}`);
  }
};

class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let connection: number = this.context.connectServiceExtensionAbility(connectWant, connectOptions);
  }
}
```

## OnConnectFn<sup>23+</sup>

type OnConnectFn = (elementName: ElementName, remote: rpc.IRemoteObject) => void

与指定的后台服务成功建立连接时，会触发该回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明                                              |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------- |
| elementName | [ElementName](js-apis-bundleManager-elementName.md)          | 是   | 目标Ability的elementName。                        |
| remote      | [rpc.IRemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject) | 是   | 用于与目标Ability进行IPC通信的IRemoteObject实例。 |

**示例：**

ArkTS-Sta示例：

```ts
'use static'
import { UIAbility, common, Want, AbilityConstant } from '@kit.AbilityKit';
import { bundleManager } from '@kit.AbilityKit';
import rpc from '@ohos.rpc';

let connectWant: Want = {
  bundleName: 'com.example.myapp',
  abilityName: 'MyAbility'
};

let connectOptions: common.ConnectOptions = {
  onConnect: (elementName: bundleManager.ElementName, remote: rpc.IRemoteObject): void => {
    console.info(`onConnect elementName: ${JSON.stringify(elementName)}`);
  },
  onDisconnect: (elementName: bundleManager.ElementName): void => {
    console.info(`onDisconnect elementName: ${JSON.stringify(elementName)}`);
  },
  onFailed: (code: int): void => {
    console.error(`onFailed code: ${code}`);
  }
};

class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let connection = this.context.connectServiceExtensionAbility(connectWant, connectOptions);
  }
}
```

## OnDisconnectFn<sup>23+</sup>

type OnDisconnectFn = (elementName: ElementName) => void

与指定的后台服务成功断开连接时，会触发该回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型                                                | 必填 | 说明                       |
| ----------- | --------------------------------------------------- | ---- | -------------------------- |
| elementName | [ElementName](js-apis-bundleManager-elementName.md) | 是   | 目标Ability的elementName。 |

**示例：**

ArkTS-Sta示例：

```ts
'use static'
import { UIAbility, common, Want, AbilityConstant } from '@kit.AbilityKit';
import { bundleManager } from '@kit.AbilityKit';
import rpc from '@ohos.rpc';

let connectWant: Want = {
  bundleName: 'com.example.myapp',
  abilityName: 'MyAbility'
};

let connectOptions: common.ConnectOptions = {
  onConnect: (elementName: bundleManager.ElementName, remote: rpc.IRemoteObject): void => {
    console.info(`onConnect elementName: ${JSON.stringify(elementName)}`);
  },
  onDisconnect: (elementName: bundleManager.ElementName): void => {
    console.info(`onDisconnect elementName: ${JSON.stringify(elementName)}`);
  },
  onFailed: (code: int): void => {
    console.error(`onFailed code: ${code}`);
  }
};

class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let connection = this.context.connectServiceExtensionAbility(connectWant, connectOptions);
  }
}
```

## OnFailedFn<sup>23+</sup>

type OnFailedFn = (code: int) => void

与指定的后台服务建立连接失败时，会触发该回调，返回连接失败的错误码。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| code   | int | 是   | 连接指定Ability失败返回的错误码。<br>错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。<br> 201 - The application does not have permission to call the interface.<br> 16000001 - The specified ability does not exist.<br> 16000002 - Incorrect ability type.<br> 16000004 - Cannot start an invisible component.<br> 16000005 - The specified process does not have the permission.<br> 16000006 - Cross-user operations are not allowed.<br> 16000008 - The crowdtesting application expires.<br> 16000053 - The ability is not on the top of the UI.<br> 16000055 - Installation-free timed out.<br> 16000050 - Internal error. |

**示例：**

ArkTS-Sta示例：

```ts
'use static'
import { UIAbility, common, Want, AbilityConstant } from '@kit.AbilityKit';
import { bundleManager } from '@kit.AbilityKit';
import rpc from '@ohos.rpc';

let connectWant: Want = {
  bundleName: 'com.example.myapp',
  abilityName: 'MyAbility'
};

let connectOptions: common.ConnectOptions = {
  onConnect: (elementName: bundleManager.ElementName, remote: rpc.IRemoteObject): void => {
    console.info(`onConnect elementName: ${JSON.stringify(elementName)}`);
  },
  onDisconnect: (elementName: bundleManager.ElementName): void => {
    console.info(`onDisconnect elementName: ${JSON.stringify(elementName)}`);
  },
  onFailed: (code: int): void => {
    console.error(`onFailed code: ${code}`);
  }
};

class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let connection = this.context.connectServiceExtensionAbility(connectWant, connectOptions);
  }
}
```

