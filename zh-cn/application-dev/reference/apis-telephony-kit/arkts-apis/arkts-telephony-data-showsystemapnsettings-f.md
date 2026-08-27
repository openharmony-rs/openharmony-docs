# showSystemApnSettings

## 导入模块

```TypeScript
```

## showSystemApnSettings

```TypeScript
function showSystemApnSettings(context: Context): Promise<void>
```

打开当前默认移动数据卡对应的APN配置界面。使用Promise异步回调。

> **说明：**
> 
> - 该接口仅支持查看和选择当前已添加的通用APN，不支持新建或修改。
> 
> - 若未插入SIM卡或设备不支持APN配置，将无法打开该配置界面。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Telephony.CellularData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | Stage模型的应用上下文（仅支持UIAbilityContext和ExtensionContext）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { data } from '@kit.TelephonyKit';
import { common } from '@kit.AbilityKit';

let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
data.showSystemApnSettings(context).then(() => {
  console.info("showSystemApnSettings success");
}).catch(() => {
  console.error("showSystemApnSettings failed");
});
```
