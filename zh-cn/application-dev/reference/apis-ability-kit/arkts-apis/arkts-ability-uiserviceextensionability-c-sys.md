# UIServiceExtensionAbility（系统接口）

UIServiceExtensionAbility提供浮窗组件相关扩展能力，继承自[ExtensionAbility](arkts-ability-extensionability-c.md).
主要用于向三方应用提供带界面的服务。

**继承/实现关系：** UIServiceExtensionAbility extends [ExtensionAbility](arkts-ability-extensionability-c.md)

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onConnect

```TypeScript
onConnect(want: Want, proxy: UIServiceHostProxy): void
```

UIServiceExtension生命周期回调。如果是
[connectUIServiceExtensionAbility()](arkts-ability-uiextensioncontext-c.md#connectuiserviceextensionability-1)
拉起的服务，会在[onCreate()](arkts-ability-uiserviceextensionability-c-sys.md#oncreate-1)之后回调。接收一个
[UIServiceHostProxy](arkts-ability-uiservicehostproxy-i-sys.md)对象，用于客户端和服务端进行通信。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 当前[UIServiceExtensionAbility](arkts-ability-uiserviceextensionability-c-sys.md)相关的[Want](arkts-ability-want-c.md)类型信息，包括Ability名称、Bundle名称等。 |
| proxy | UIServiceHostProxy | 是 | 一个[UIServiceHostProxy](arkts-ability-uiservicehostproxy-i-sys.md)对象，用于客户端和服务端进行通信。 |

**示例：**

```TypeScript
import { UIServiceExtensionAbility, Want, common} from '@kit.AbilityKit';

class UIServiceExt extends UIServiceExtensionAbility {
  onConnect(want: Want, proxy: common.UIServiceHostProxy){
    console.info('onConnect, want:' + want.abilityName + '');
  }
}

```

## onCreate

```TypeScript
onCreate(want: Want): void
```

[UIServiceExtensionContext](../../apis-na/arkts-apis/arkts-na-uiserviceextensioncontext-c-sys.md)生命周期创建接口，执行初始化
业务逻辑操作。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 当前[UIServiceExtensionAbility](arkts-ability-uiserviceextensionability-c-sys.md)相关的[Want](arkts-ability-want-c.md)类型信息，包括Ability名称、Bundle名称等。 |

**示例：**

```TypeScript
import { UIServiceExtensionAbility, Want } from '@kit.AbilityKit';

class UIServiceExt extends UIServiceExtensionAbility {
  // 创建UIServiceExtensionAbility
  onCreate(want: Want) {
    console.info(`onCreate, want: ${want.abilityName}`);
  }
}

```

## onData

```TypeScript
onData(proxy: UIServiceHostProxy, data: Record<string, Object>): void
```

接收到数据的回调。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| proxy | UIServiceHostProxy | 是 | 往客户端发送数据的Proxy。 |
| data | Record&lt;string, Object&gt; | 是 | 表示接收到的数据。 |

**示例：**

```TypeScript
import { UIServiceExtensionAbility, common} from '@kit.AbilityKit';

class ServiceExt extends UIServiceExtensionAbility {
  onData(proxy : common.UIServiceHostProxy, data : Record<string, Object> ){
    console.info('onData');
  }
}

```

## onDestroy

```TypeScript
onDestroy(): void
```

UIServiceExtension销毁时回调，执行资源清理等操作。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
import { UIServiceExtensionAbility } from '@kit.AbilityKit';

class ServiceExt extends UIServiceExtensionAbility {
  onDestroy() {
    console.info('onDestroy');
  }
}

```

## onDisconnect

```TypeScript
onDisconnect(want: Want, proxy: UIServiceHostProxy): void
```

断开与UIServiceExtension的连接。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 当前[UIServiceExtensionAbility](arkts-ability-uiserviceextensionability-c-sys.md)相关的[Want](arkts-ability-want-c.md)类型信息，包括Ability名称、Bundle名称等。 |
| proxy | UIServiceHostProxy | 是 | 往发起方发送数据的Proxy。 |

**示例：**

```TypeScript
import { UIServiceExtensionAbility, Want, common } from '@kit.AbilityKit';

class UIServiceExt extends UIServiceExtensionAbility {
  onDisconnect(want: Want, proxy: common.UIServiceHostProxy) {
    console.info('onDisconnect, want: ${want.abilityName}');
  }
}

```

## onRequest

```TypeScript
onRequest(want: Want, startId: number): void
```

请求拉起UIServiceExtension服务处理。如果是
[startAbility](arkts-ability-uiabilitycontext-c.md#startability-1)
或者
[startUIServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#startuiserviceextensionability-1)
拉起的服务，会在[onCreate](arkts-ability-uiserviceextensionability-c-sys.md#oncreate-1)之后回调。每次拉起服务都会回调，startId会递增。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 当前[UIServiceExtensionAbility](arkts-ability-uiserviceextensionability-c-sys.md)相关的[Want](arkts-ability-want-c.md)类型信息，包括Ability名称、Bundle名称等。 |
| startId | number | 是 | 返回浮窗拉起次数。首次拉起初始值返回1，多次之后自动递增。 |

**示例：**

```TypeScript
import { UIServiceExtensionAbility, Want} from '@kit.AbilityKit';

class UIServiceExt extends UIServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    console.info('onRequest, want:' + want.abilityName + ', startId:' + startId);
  }
}

```

## onWindowDidCreate

```TypeScript
onWindowDidCreate(window: window.Window): void
```

UIServiceExtension创建后回调。UIServiceExtension服务创建窗口成功后，通过onWindowDidCreate接口把创建的窗口对象传递给前台应用。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| window | window.Window | 是 | 表示已创建的Window。 |

**示例：**

```TypeScript
import { UIServiceExtensionAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

class ServiceExt extends UIServiceExtensionAbility {
  onWindowDidCreate(window : window.Window){
    console.info('onWindowDidCreate');
  }
}

```

## onWindowWillCreate

```TypeScript
onWindowWillCreate(config: window.ExtensionWindowConfig): void
```

UIServiceExtension窗体创建前的回调。前台应用把要创建windows的参数通过window.ExtensionWindowConfig传回给UIServiceExtension服务。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | window.ExtensionWindowConfig | 是 | UIServiceExtension窗体配置信息。 |

**示例：**

```TypeScript
import { UIServiceExtensionAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

class UIServiceExt extends UIServiceExtensionAbility {
  onWindowWillCreate(config : window.ExtensionWindowConfig){
    console.info('onWindowWillCreate');
  }
}

```

## context

```TypeScript
context: UIServiceExtensionContext
```

UIServiceExtension的上下文环境，继承自[ExtensionContext](arkts-ability-extensionability-c.md)。

**类型：** UIServiceExtensionContext

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

