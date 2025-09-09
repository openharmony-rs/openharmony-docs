# @ohos.app.ability.VpnExtensionAbility (三方VPN能力)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

VpnExtensionAbility模块提供三方VPN相关能力，提供三方VPN创建、销毁等生命周期回调。

>  **说明：**
>
>  - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>  - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { VpnExtensionAbility } from '@kit.NetworkKit';
```

## 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| context | [VpnExtensionContext](js-apis-inner-application-VpnExtensionContext.md) | 否 | 否 | VpnExtension的上下文环境，继承自ExtensionContext。 |

## VpnExtensionAbility.onCreate

onCreate(want: Want): void

在启动三方VPN进行初始化时回调。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数**：

| 参数名  | 类型                                       | 必填   | 说明             |
| ---- | ---------------------------------------- | ---- | -------------- |
| want   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 指示要启动的信息。 |

**示例：** 

  ```ts
import { VpnExtensionAbility } from '@kit.NetworkKit';
import { Want } from '@kit.AbilityKit';

class MyVpnExtAbility extends VpnExtensionAbility {
    onCreate(want: Want) {
       console.info('MyVpnExtAbility onCreate');
    }
}
  ```

## VpnExtensionAbility.onDestroy

onDestroy(): void

VpnExtensionAbility生命周期回调，在销毁时回调，执行资源清理等操作。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例：** 

  ```ts
import { VpnExtensionAbility } from '@kit.NetworkKit';

class MyVpnExtAbility extends VpnExtensionAbility {
    onDestroy() {
       console.info('MyVpnExtAbility onDestroy');
    }
}
  ```

