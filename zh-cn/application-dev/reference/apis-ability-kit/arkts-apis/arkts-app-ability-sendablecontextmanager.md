# @ohos.app.ability.sendableContextManager

sendableContextManager模块提供Context与[SendableContext](arkts-ability-sendablecontext-i.md)相互转换的能力。

**起始版本：** 12

<!--Device-unnamed-declare namespace sendableContextManager--><!--Device-unnamed-declare namespace sendableContextManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { sendableContextManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [convertFromContext](arkts-ability-sendablecontextmanager-convertfromcontext-f.md#convertfromcontext) | 将Context转换为SendableContext对象。 |
| [convertToAbilityStageContext](arkts-ability-sendablecontextmanager-converttoabilitystagecontext-f.md#converttoabilitystagecontext) | 将SendableContext对象转换为AbilityStageContext。 |
| [convertToApplicationContext](arkts-ability-sendablecontextmanager-converttoapplicationcontext-f.md#converttoapplicationcontext) | 将SendableContext对象转换为ApplicationContext。 |
| [convertToContext](arkts-ability-sendablecontextmanager-converttocontext-f.md#converttocontext) | 将SendableContext对象转换为Context。 |
| [convertToUIAbilityContext](arkts-ability-sendablecontextmanager-converttouiabilitycontext-f.md#converttouiabilitycontext) | 将SendableContext对象转换为UIAbilityContext。 |
| [setEventHubMultithreadingEnabled](arkts-ability-sendablecontextmanager-seteventhubmultithreadingenabled-f.md#seteventhubmultithreadingenabled) | 设置[Context](arkts-ability-context-t.md)中的[EventHub](arkts-ability-eventhub-c.md)是否启用跨线程通信能力。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SendableContext](arkts-ability-sendablecontextmanager-sendablecontext-t.md) | SendableContext二级模块 |

