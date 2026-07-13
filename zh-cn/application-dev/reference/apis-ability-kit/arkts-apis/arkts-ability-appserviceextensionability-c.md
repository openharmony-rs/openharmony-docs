# AppServiceExtensionAbility

AppServiceExtensionAbility模块提供后台服务相关扩展能力，包括后台服务的创建、销毁、连接、断开等生命周期回调。

**继承/实现关系：** AppServiceExtensionAbility extends [ExtensionAbility](arkts-ability-extensionability-c.md)

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onConnect

```TypeScript
onConnect(want: Want): rpc.RemoteObject
```

调用方使用
[connectAppServiceExtensionAbility()](arkts-ability-uiabilitycontext-c.md#connectappserviceextensionability-1)
连接AppServiceExtensionAbility实例时，系统会触发该回调。

应用需要在该接口中返回一个RemoteObject对象，用于客户端和服务端进行通信。当AppServiceExtensionAbility实例处于连接状态时，如果调用方发起新的连接，系统会返回缓存的RemoteObject对象，
而不会重复回调onConnect()接口。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 调用方拉起当前AppServiceExtensionAbility实例时传递的Want类型信息，包括Ability名称、Bundle名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| rpc.RemoteObject | 一个RemoteObject对象，用于客户端和服务端进行通信。 |

**示例：**

```TypeScript
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtAbility]';

class StubTest extends rpc.RemoteObject {
  constructor(des: string) {
    super(des);
  }

  onConnect(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence, option: rpc.MessageOption) {
  }
}

export default class AppServiceExtAbility extends AppServiceExtensionAbility {
  onConnect(want: Want) {
    hilog.info(0x0000, TAG, `onConnect, want: ${want.abilityName}`);
    return new StubTest('test');
  }
}

```

## onCreate

```TypeScript
onCreate(want: Want): void
```

在AppServiceExtensionAbility实例创建时，系统会触发该回调。应用可以在该接口中执行自己的业务逻辑初始化操作，例如注册公共事件监听等。

> **说明：**
>
> 如果AppServiceExtensionAbility实例已创建，再次启动或连接该实例时不会触发onCreate()回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 调用方拉起当前AppServiceExtensionAbility实例时传递的Want类型信息，包括Ability名称、Bundle名称等。 |

**示例：**

```TypeScript
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtAbility]';

export default class AppServiceExtAbility extends AppServiceExtensionAbility {
  onCreate(want: Want) {
    hilog.info(0x0000, TAG, `onCreate, want: ${want.abilityName}`);
  }
}

```

## onDestroy

```TypeScript
onDestroy(): void
```

在AppServiceExtensionAbility实例销毁时，系统会触发该回调。应用可以在该接口中执行资源清理等操作，如注销监听等。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例：**

```TypeScript
import { AppServiceExtensionAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtAbility]';

export default class AppServiceExtAbility extends AppServiceExtensionAbility {
  onDestroy() {
    hilog.info(0x0000, TAG, `onDestroy`);
  }
}

```

## onDisconnect

```TypeScript
onDisconnect(want: Want): void
```

当所有连接方断开与AppServiceExtensionAbility实例的连接时，系统会触发该回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | AppServiceExtensionAbility实例最近一次被拉起或者连接时，调用方传递的Want类型信息，包括Ability名称、Bundle名称等。 |

**示例：**

```TypeScript
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtAbility]';

export default class AppServiceExtAbility extends AppServiceExtensionAbility {
  onDisconnect(want: Want) {
    hilog.info(0x0000, TAG, `onDisconnect, want: ${want.abilityName}`);
  }
}

```

## onRequest

```TypeScript
onRequest(want: Want, startId: number): void
```

调用方每次使用
[startAppServiceExtensionAbility()](arkts-ability-uiabilitycontext-c.md#startappserviceextensionability-1)
拉起AppServiceExtensionAbility实例时，系统都会触发该回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 调用方拉起当前AppServiceExtensionAbility实例时传递的Want类型信息，包括Ability名称、Bundle名称等。 |
| startId | number | 是 | 返回拉起次数。首次拉起初始值返回1，多次拉起时自动递增。 |

**示例：**

```TypeScript
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtAbility]';

export default class AppServiceExtAbility extends AppServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    hilog.info(0x0000, TAG, `onRequest, want: ${want.abilityName}, startId: ${startId}`);
  }
}

```

## context

```TypeScript
context: AppServiceExtensionContext
```

AppServiceExtensionAbility的上下文环境，继承自[ExtensionContext](arkts-ability-extensioncontext-c.md)。

**类型：** AppServiceExtensionContext

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

