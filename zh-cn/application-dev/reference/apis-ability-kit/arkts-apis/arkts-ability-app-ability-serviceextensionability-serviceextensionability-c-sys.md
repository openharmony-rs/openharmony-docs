# ServiceExtensionAbility（系统接口）

ServiceExtensionAbility模块提供后台服务相关扩展能力，提供后台服务创建、销毁、连接、断开等生命周期回调。

**起始版本：** 9

<!--Device-unnamed-declare class ServiceExtensionAbility--><!--Device-unnamed-declare class ServiceExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { ServiceExtensionAbility } from '@kit.AbilityKit';
```

## onConfigurationUpdate

```TypeScript
onConfigurationUpdate(newConfig: Configuration): void
```

当Extension更新配置信息时调用。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ServiceExtensionAbility-onConfigurationUpdate(newConfig: Configuration): void--><!--Device-ServiceExtensionAbility-onConfigurationUpdate(newConfig: Configuration): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newConfig | [Configuration](../../apis-arkui/arkts-components/arkts-arkui-common-configuration-i.md) | 是 | 表示需要更新的配置信息。 |

**示例：**

```TypeScript
import { ServiceExtensionAbility, Configuration } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onConfigurationUpdate(newConfig: Configuration) {
    console.info(`onConfigurationUpdate, config: ${JSON.stringify(newConfig)}`);
  }
}

```

## onConnect

```TypeScript
onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>
```

Extension生命周期回调，如果是connectAbility拉起的服务，会在onCreate之后回调。返回一个RemoteObject对象，用于客户端和服务端进行通信。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ServiceExtensionAbility-onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>--><!--Device-ServiceExtensionAbility-onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| rpc.RemoteObject | RemoteObject or Promise used to return a RemoteObject,which is used for communication between the client and server. |

**示例：**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

class StubTest extends rpc.RemoteObject{
  constructor(des: string) {
    super(des);
  }
  onConnect(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence, option: rpc.MessageOption) {
  }
}
class ServiceExt extends ServiceExtensionAbility {
  onConnect(want: Want) {
    console.info('onConnect , want: ${want.abilityName}');
    return new StubTest('test');
  }
}

```

如果生成返回值RemoteObject依赖一个异步接口，可以使用异步生命周期：

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

class StubTest extends rpc.RemoteObject{
  constructor(des: string) {
    super(des);
  }
  onConnect(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence, option: rpc.MessageOption) {
  }
}
async function getDescriptor() {
  // 调用异步函数...
  return "asyncTest"
}
class ServiceExt extends ServiceExtensionAbility {
  async onConnect(want: Want) {
    console.info(`onConnect , want: ${want.abilityName}`);
    let descriptor = await getDescriptor();
    return new StubTest(descriptor);
  }
}

```

## onCreate

```TypeScript
onCreate(want: Want): void
```

Extension生命周期回调，在创建时回调，执行初始化业务逻辑操作。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ServiceExtensionAbility-onCreate(want: Want): void--><!--Device-ServiceExtensionAbility-onCreate(want: Want): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**示例：**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onCreate(want: Want) {
    console.info(`onCreate, want: ${want.abilityName}`);
  }
}

```

## onDestroy

```TypeScript
onDestroy(): void
```

Extension生命周期回调，在销毁时回调，执行资源清理等操作。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ServiceExtensionAbility-onDestroy(): void--><!--Device-ServiceExtensionAbility-onDestroy(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
import { ServiceExtensionAbility } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onDestroy() {
    console.info('onDestroy');
  }
}

```

## onDisconnect

```TypeScript
onDisconnect(want: Want): void | Promise<void>
```

Extension的生命周期回调，客户端执行断开连接服务时回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ServiceExtensionAbility-onDisconnect(want: Want): void | Promise<void>--><!--Device-ServiceExtensionAbility-onDisconnect(want: Want): void | Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**示例：**

同步回调示例如下：

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onDisconnect(want: Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
  }
}

```

Promise异步回调示例如下：

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  async onDisconnect(want: Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
    // 调用异步函数...
  }
}

```

## onDump

```TypeScript
onDump(params: Array<string>): Array<string>
```

转储客户端信息时调用。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ServiceExtensionAbility-onDump(params: Array<string>): Array<string>--><!--Device-ServiceExtensionAbility-onDump(params: Array<string>): Array<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 表示命令形式的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 表示转存客户端信息数组。 |

**示例：**

```TypeScript
import { ServiceExtensionAbility } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onDump(params: Array<string>) {
    console.info(`dump, params: ${JSON.stringify(params)}`);
    return ['params'];
  }
}

```

## onReconnect

```TypeScript
onReconnect(want: Want): void
```

Extension的生命周期回调，当所有以前的客户端都断开连接之后，新客户端尝试连接到服务时调用。预留能力，当前暂未支持。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ServiceExtensionAbility-onReconnect(want: Want): void--><!--Device-ServiceExtensionAbility-onReconnect(want: Want): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**示例：**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onReconnect(want: Want) {
    console.info('onReconnect, want: ${want.abilityName}');
  }
}

```

## onRequest

```TypeScript
onRequest(want: Want, startId: number): void
```

Extension生命周期回调，如果是startAbility或者startServiceExtensionAbility拉起的服务，会在onCreate之后回调。每次拉起服务都会回调，startId会递增。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ServiceExtensionAbility-onRequest(want: Want, startId: int): void--><!--Device-ServiceExtensionAbility-onRequest(want: Want, startId: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |
| startId | number | 是 | 返回拉起次数。首次拉起初始值返回1，多次之后自动递增。 |

**示例：**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class ServiceExt extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info('onRequest, want: ${want.abilityName}');
  }
}

```

## context

```TypeScript
context: ServiceExtensionContext
```

ServiceExtension的上下文环境，继承自ExtensionContext。

**类型：** ServiceExtensionContext

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ServiceExtensionAbility-context: ServiceExtensionContext--><!--Device-ServiceExtensionAbility-context: ServiceExtensionContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

