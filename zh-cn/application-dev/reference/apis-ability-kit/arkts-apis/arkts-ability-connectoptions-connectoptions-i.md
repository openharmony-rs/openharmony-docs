# ConnectOptions

在连接指定的后台服务时作为入参，用于接收连接过程中的状态变化，如作为 [connectServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#connectserviceextensionability) 的入参，连接指定的ServiceExtensionAbility。

**起始版本：** 7

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onConnect

```TypeScript
onConnect(elementName: ElementName, remote: rpc.IRemoteObject): void
```

建立连接时的回调函数。

**起始版本：** 7

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-elementname-i.md) | 是 | 目标Ability的elementName。 |
| remote | rpc.IRemoteObject | 是 | 用于与目标Ability进行IPC通信的IRemoteObject实例。 |

**示例**

```TypeScript
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

## onDisconnect

```TypeScript
onDisconnect(elementName: ElementName): void
```

断开连接时的回调函数。

**起始版本：** 7

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | [ElementName](arkts-ability-elementname-i.md) | 是 | 目标Ability的elementName。 |

**示例**

```TypeScript
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

## onFailed

```TypeScript
onFailed(code: number): void
```

连接失败时的回调函数。

**起始版本：** 7

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 连接指定Ability失败返回的错误码。错误码详细介绍请参考[通用错误码](../../errorcode-universal.md)和[元能力子系统错误码](../errorcode-ability.md)。201 - The application does not have permission to call the interface.16000001 - The specified ability does not exist.16000002 - Incorrect ability type.16000004 - Cannot start an invisible component.16000005 - The specified process does not have the permission.16000006 - Cross-user operations are not allowed.16000008 - The crowdtesting application expires.16000053 - The ability is not on the top of the UI.16000055 - Installation-free timed out.16000050 - Internal error. |

**示例**

```TypeScript
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
