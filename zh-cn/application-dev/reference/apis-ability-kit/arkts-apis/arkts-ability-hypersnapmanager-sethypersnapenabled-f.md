# setHyperSnapEnabled

## 导入模块

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## setHyperSnapEnabled

```TypeScript
function setHyperSnapEnabled(enableFlag: boolean): void
```

启用或禁用应用的快启功能。 > **说明：** > > - 当通过本接口启用应用快启功能时，系统最终会根据应用兼容性、资源可用性和系统策略来决定是否创建或使用快启。当通过本接口禁用快启功能时，可以保证系统不会创建快启。 > > - 设置的值会在重启后保持。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-hyperSnapManager-function setHyperSnapEnabled(enableFlag: boolean): void--><!--Device-hyperSnapManager-function setHyperSnapEnabled(enableFlag: boolean): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enableFlag | boolean | 是 | 表示快启功能开关标志。 <br>- `true`：表示启用快启功能（系统将最终决策是否创建快启）。 <br>- `false`：禁用应用快启功能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000150](../errorcode-ability.md#16000150-发送请求失败) | Failed to send request to system service. |

