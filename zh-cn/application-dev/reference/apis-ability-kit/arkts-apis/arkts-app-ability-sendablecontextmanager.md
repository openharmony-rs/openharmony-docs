# @ohos.app.ability.sendableContextManager

sendableContextManager模块提供Context与[SendableContext](arkts-ability-sendablecontext-i.md#SendableContext)相互转换的能力。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [convertFromContext](arkts-ability-sendablecontextmanager-convertfromcontext-f.md#convertFromContext-1) | 将Context转换为SendableContext对象。<br/> |
| [convertToAbilityStageContext](arkts-ability-sendablecontextmanager-converttoabilitystagecontext-f.md#convertToAbilityStageContext-1) | 将SendableContext对象转换为AbilityStageContext。<br/> |
| [convertToApplicationContext](arkts-ability-sendablecontextmanager-converttoapplicationcontext-f.md#convertToApplicationContext-1) | 将SendableContext对象转换为ApplicationContext。<br/> |
| [convertToContext](arkts-ability-sendablecontextmanager-converttocontext-f.md#convertToContext-1) | 将SendableContext对象转换为Context。<br/> |
| [convertToUIAbilityContext](arkts-ability-sendablecontextmanager-converttouiabilitycontext-f.md#convertToUIAbilityContext-1) | 将SendableContext对象转换为UIAbilityContext。<br/> |
| [setEventHubMultithreadingEnabled](arkts-ability-sendablecontextmanager-seteventhubmultithreadingenabled-f.md#setEventHubMultithreadingEnabled-1) | 设置[Context](arkts-ability-context-depr-i.md#Context)中的[EventHub](arkts-ability-eventhub-c.md#EventHub)是否启用跨线程通信能力。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 当多个Context进行通信时，需要调用该接口设置每个Context都支持EventHub跨线程数据传递功能。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SendableContext](arkts-ability-sendablecontextmanager-sendablecontext-t.md) | SendableContext二级模块<br/> |

