# DistributedExtensionAbility

DistributedExtensionAbility模块提供分布式相关扩展能力，提供分布式创建、销毁、连接的生命周期回调。

**起始版本：** 20

<!--Device-unnamed-declare class DistributedExtensionAbility--><!--Device-unnamed-declare class DistributedExtensionAbility-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
```

<a id="oncollaborate"></a>
## onCollaborate

```TypeScript
onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult
```

多设备协作场景下返回协作结果的回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedExtensionAbility-onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult--><!--Device-DistributedExtensionAbility-onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wantParam | Record&lt;string, Object&gt; | 是 | want相关参数，仅支持key值取"ohos.extra.param.key.supportCollaborateIndex"。通过该key值可以获取到调用方传输的数据并进行相应的处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AbilityConstant.CollaborateResult | 协同方应用是否接受协同。 |

**示例：**

```TypeScript
import { abilityConnectionManager, DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { AbilityConstant } from '@kit.AbilityKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCollaborate(wantParam: Record<string, Object>) {
    console.info(`DistributedExtension onCollabRequest Accept to the result of Ability collaborate`);
    let sessionId = -1;
    const collaborationValues = wantParam["CollaborationValues"] as abilityConnectionManager.CollaborationValues;
    if (!collaborationValues) {
      console.error('Failed to get collaborationValues.');
      return sessionId;
    }
    console.info(`onCollab, collaborationValues: ${JSON.stringify(collaborationValues)}`);
    return AbilityConstant.CollaborateResult.ACCEPT;
  }
}

```

<a id="oncreate"></a>
## onCreate

```TypeScript
onCreate(want: Want): void
```

Extension生命周期回调，在创建时回调，执行初始化业务逻辑操作。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedExtensionAbility-onCreate(want: Want): void--><!--Device-DistributedExtensionAbility-onCreate(want: Want): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**示例：**

```TypeScript
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

<a id="ondestroy"></a>
## onDestroy

```TypeScript
onDestroy(): void
```

Extension生命周期回调，在销毁时回调，执行资源清理等操作。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedExtensionAbility-onDestroy(): void--><!--Device-DistributedExtensionAbility-onDestroy(): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**示例：**

```TypeScript
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onDestroy() {
    console.info('DistributedExtension onDestroy ok');
  }
}

```

## context

```TypeScript
context: DistributedExtensionContext
```

DistributedExtension的上下文环境，继承自ExtensionContext。

**类型：** DistributedExtensionContext

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedExtensionAbility-context: DistributedExtensionContext--><!--Device-DistributedExtensionAbility-context: DistributedExtensionContext-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

