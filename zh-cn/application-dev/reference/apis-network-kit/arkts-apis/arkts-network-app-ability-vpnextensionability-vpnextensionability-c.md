# VpnExtensionAbility

VpnExtensionContext是VpnExtensionAbility的上下文环境，继承自 [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。 VpnExtensionContext可直接作为VpnExtension的上下文环境，提供允许访问特定于VpnExtensionAbility的资源的能力。

**起始版本：** 11

<!--Device-unnamed-export default class VpnExtensionAbility--><!--Device-unnamed-export default class VpnExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { VpnExtensionAbility, VpnExtensionContext } from '@kit.NetworkKit';
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

拓展VPN启动初始化的时候进行回调。 > **说明：** > > 建议配对调用[onDestroy](#ondestroy)监听拓展VPN的销毁，及时执行资源清理等操作。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VpnExtensionAbility-onCreate(want: Want): void--><!--Device-VpnExtensionAbility-onCreate(want: Want): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 指示要启动的信息。 |

**示例**

```TypeScript
import { VpnExtensionAbility } from '@kit.NetworkKit';
import { Want } from '@kit.AbilityKit';

class MyVpnExtAbility extends VpnExtensionAbility {
    onCreate(want: Want) {
       console.info('MyVpnExtAbility onCreate');
    }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

拓展VPN销毁之前进行回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VpnExtensionAbility-onDestroy(): void--><!--Device-VpnExtensionAbility-onDestroy(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

```TypeScript
import { VpnExtensionAbility } from '@kit.NetworkKit';

class MyVpnExtAbility extends VpnExtensionAbility {
    onDestroy() {
       console.info('MyVpnExtAbility onDestroy');
    }
}
```

## context

```TypeScript
context: VpnExtensionContext
```

指定context。

**类型：** VpnExtensionContext

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VpnExtensionAbility-context: VpnExtensionContext--><!--Device-VpnExtensionAbility-context: VpnExtensionContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

