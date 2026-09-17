# convertToUIAbilityContext

## 导入模块

```TypeScript
import { sendableContextManager } from '@kit.AbilityKit';
```

## convertToUIAbilityContext

```TypeScript
function convertToUIAbilityContext(sendableContext: SendableContext): common.UIAbilityContext
```

将SendableContext对象转换为UIAbilityContext。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sendableContext | [SendableContext](arkts-ability-sendablecontextmanager-sendablecontext-t.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [common.UIAbilityContext](arkts-ability-common-uiabilitycontext-t.md) | [UIAbilityContext](arkts-ability-uiabilitycontext-c.md) object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |

**示例**

```TypeScript
主线程传递Context：
```

```TypeScript
Worker线程接收Context：
```
