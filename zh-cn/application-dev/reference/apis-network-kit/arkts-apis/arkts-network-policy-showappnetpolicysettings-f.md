# showAppNetPolicySettings

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## showAppNetPolicySettings

```TypeScript
function showAppNetPolicySettings(context: Context): Promise<void>
```

当需要设置当前应用能否使用Wi-Fi/蜂窝联网时，调用该接口可以打开当前应用的联网设置界面，以设置应用的联网权限。使用Promise异步回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-policy-function showAppNetPolicySettings(context: Context): Promise<void>--><!--Device-policy-function showAppNetPolicySettings(context: Context): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | Stage模型的应用上下文（仅支持UIAbilityContext和ExtensionContext）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { policy } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
policy.showAppNetPolicySettings(context).then(() => {
    console.info("showAppNetPolicySettings success");
}).catch(() => {
    console.error("showAppNetPolicySettings failed");
    }
)
```

