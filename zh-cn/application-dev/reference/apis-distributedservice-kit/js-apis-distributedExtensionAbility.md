# @ohos.application.DistributedExtensionAbility (协同Extension)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->

DistributedExtensionAbility（分布式扩展能力）模块提供分布式相关扩展能力，提供分布式创建、销毁、连接的生命周期回调。该模块适用于多设备协同场景下的应用，通过统一的生命周期管理接口，降低了多设备应用的开发难度。

> **说明：**
>
> 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
```

## DistributedExtensionAbility

### 属性

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**设备行为差异：** 该接口在不支持分布式业务的Wearable设备不生效。

| 名称    | 类型                          | 只读 | 可选 | 说明                                                       |
| ------- | ----------------------------- | ---- | ---- | ---------------------------------------------------------- |
| context | [DistributedExtensionContext](js-apis-distributedExtensionContext.md) | 否   | 否   | DistributedExtension（协同Extension）的上下文环境，继承自ExtensionContext。DistributedExtensionContext的设计说明请参见[DistributedExtensionContext接口](js-apis-distributedExtensionContext.md)。 |

### onCreate

onCreate(want: Want): void

Extension生命周期回调，在创建时回调，执行初始化业务逻辑操作。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**设备行为差异：** 该接口在不支持分布式业务的Wearable设备不生效。

**参数：**

| 参数名     | 类型 | 必填                                                             | 说明 |
| ----------| ---- | ---------------------------------------------------------------- | ---- |
| want      | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 当前Extension相关的Want信息，包含ability（应用组件）名称、bundle名称等，用于携带创建Extension所需的初始化配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| void | 无返回值，用于执行初始化业务逻辑操作。 |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCreate(want: Want) {
    console.info(`DistributedExtension Create ok`);
    console.info(`DistributedExtension on Create want: ${JSON.stringify(want)}`);
    console.info(`DistributedExtension Create end`);
  }
}
```

### onCollaborate

onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult

Extension生命周期回调，在多设备协同场景下，协同方应用被拉起过程中返回是否接受协同的结果，返回结果决定协同流程是否继续。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**设备行为差异：** 该接口在不支持分布式业务的Wearable设备不生效。

**参数：**

| 参数名    | 类型   | 必填 | 说明                                                                                                                                   |
| --------- | ------ | ---- | -------------------------------------------------------------------------------------------------------------------------------------- |
| wantParam | Record<string, Object> | 是   | 协同回调参数，键值对对象，携带调用方传输的协同相关数据。开发者可通过"ohos.extra.param.key.supportCollaborateIndex"和"CollaborationValues"等key值获取这些数据，以决定是否接受协同请求及处理协同逻辑，影响协同流程是否继续。 |

**返回值：**

| 类型 | 说明 |
| ---------- | ---- |
| [AbilityConstant.CollaborateResult](../apis-ability-kit/js-apis-app-ability-abilityConstant.md#collaborateresult18) | 表示协同方应用是否接受协同的结果。取值包括：**ACCEPT**表示接受协同，协同流程继续；**REJECT**表示拒绝协同，协同流程终止。 |

**示例**

```ts
import { abilityConnectionManager, DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { AbilityConstant } from '@kit.AbilityKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCollaborate(wantParam: Record<string, Object>) {
    console.info(`DistributedExtension onCollaborate 接受协同请求的结果`);
    // 获取调用方传输的协同相关参数
    const collaborationValues = wantParam["CollaborationValues"] as abilityConnectionManager.CollaborationValues;
    if (collaborationValues == undefined) { // 协同参数为空时拒绝协同
      return AbilityConstant.CollaborateResult.REJECT;
    }
    console.info(`onCollab, collaborationValues: ${JSON.stringify(collaborationValues)}`);
    return AbilityConstant.CollaborateResult.ACCEPT; // 接受协同请求
  }
}
```

### onDestroy

onDestroy(): void

Extension生命周期回调，在销毁时回调，执行资源清理等操作。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**设备行为差异：** 该接口在不支持分布式业务的Wearable设备不生效。

**示例：**

```ts
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onDestroy() {
    console.info('DistributedExtension onDestroy ok');
  }
}
```
