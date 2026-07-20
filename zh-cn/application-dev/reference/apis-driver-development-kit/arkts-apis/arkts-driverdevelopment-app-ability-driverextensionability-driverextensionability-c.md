# DriverExtensionAbility

DriverExtensionAbility模块提供驱动相关扩展能力，提供驱动创建、销毁、连接、断开等生命周期回调。

**起始版本：** 10

<!--Device-unnamed-declare class DriverExtensionAbility--><!--Device-unnamed-declare class DriverExtensionAbility-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

## 导入模块

```TypeScript
import { DriverExtensionContext } from '@kit.DriverDevelopmentKit';
```

<a id="onconnect"></a>
## onConnect

```TypeScript
onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>
```

Extension生命周期回调，会在[onCreate](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-abilitystage-abilitystage-c.md#oncreate-1)之后回调。返回一个[RemoteObject](@ohos.rpc:rpc.RemoteObject)对象，用于客户端和服务端进行通信。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>--><!--Device-DriverExtensionAbility-onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| rpc.RemoteObject | 一个RemoteObject对象，用于客户端和服务端进行通信；或一个Promise对象，返回用于通信的RemoteObject对象。 |

**示例：**

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class StubTest extends rpc.RemoteObject{
    constructor(des : string) {
        super(des);
    }
    onRemoteMessageRequest(code : number, data : rpc.MessageSequence, reply : rpc.MessageSequence, option : rpc.MessageOption) {
      // 必须重写此接口
      return true;
    }
}
class DriverExt extends DriverExtensionAbility {
  onConnect(want : Want) {
    console.info(`onConnect , want: ${want.abilityName}`);
    return new StubTest('test');
  }
}

```

如果生成返回值[RemoteObject](../apis-ipc-kit/js-apis-rpc.md#remoteobject)依赖一个异步接口，可以使用异步生命周期：

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class StubTest extends rpc.RemoteObject{
    constructor(des : string) {
        super(des);
    }
    onRemoteMessageRequest(code : number, data : rpc.MessageSequence, reply : rpc.MessageSequence, option : rpc.MessageOption) {
      // 必须重写此接口
      return true;
    }
}
async function getDescriptor() {
    // 调用异步函数...
    return "asyncTest";
}
class DriverExt extends DriverExtensionAbility {
  async onConnect(want : Want) {
    console.info(`onConnect , want: ${want.abilityName}`);
    let descriptor = await getDescriptor();
    return new StubTest(descriptor);
  }
}

```

<a id="ondisconnect"></a>
## onDisconnect

```TypeScript
onDisconnect(want: Want): void | Promise<void>
```

Extension的生命周期回调，客户端执行断开连接服务时回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-onDisconnect(want: Want): void | Promise<void>--><!--Device-DriverExtensionAbility-onDisconnect(want: Want): void | Promise<void>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**示例：**

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { Want } from '@kit.AbilityKit';

class DriverExt extends DriverExtensionAbility {
  onDisconnect(want : Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
  }
}

```

在执行完onDisconnect生命周期回调后，应用可能会退出，从而可能导致onDisconnect中的异步函数未能正确执行，比如异步写入数据库。可以使用异步生命周期，以确保异步onDisconnect完成后再继续后续的生命周期。

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { Want } from '@kit.AbilityKit';

class DriverExt extends DriverExtensionAbility {
  async onDisconnect(want : Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
    // 调用异步函数...
  }
}

```

<a id="ondump"></a>
## onDump

```TypeScript
onDump(params: Array<string>): Array<string>
```

转储客户端信息时调用，建议不要转储敏感信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-onDump(params: Array<string>): Array<string>--><!--Device-DriverExtensionAbility-onDump(params: Array<string>): Array<string>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | Array&lt;string&gt; | 是 | 表示命令形式的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 一个string类型的数组，用于转存客户端信息。 |

**示例：**

```TypeScript
class DriverExt extends DriverExtensionAbility {
    onDump(params : Array<string>) {
        console.info(`dump, params: ${JSON.stringify(params)}`);
        return ['params'];
    }
}

```

<a id="oninit"></a>
## onInit

```TypeScript
onInit(want: Want): void
```

Extension生命周期回调，在创建时回调，执行初始化业务逻辑操作。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-onInit(want: Want): void--><!--Device-DriverExtensionAbility-onInit(want: Want): void-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**示例：**

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { Want } from '@kit.AbilityKit';

class DriverExt extends DriverExtensionAbility {
  onInit(want : Want) {
    console.info(`onInit, want: ${want.abilityName}`);
  }
}

```

<a id="onrelease"></a>
## onRelease

```TypeScript
onRelease(): void
```

Extension生命周期回调，在销毁时回调，执行资源清理等操作。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-onRelease(): void--><!--Device-DriverExtensionAbility-onRelease(): void-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**示例：**

```TypeScript
class DriverExt extends DriverExtensionAbility {
  onRelease() {
    console.info('onRelease');
  }
}

```

## context

```TypeScript
context: DriverExtensionContext
```

DriverExtension的上下文环境，继承自ExtensionContext。

**类型：** DriverExtensionContext

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-context: DriverExtensionContext--><!--Device-DriverExtensionAbility-context: DriverExtensionContext-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

