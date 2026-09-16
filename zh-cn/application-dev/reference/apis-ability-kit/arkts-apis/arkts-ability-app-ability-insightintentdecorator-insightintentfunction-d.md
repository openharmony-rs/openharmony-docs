# @InsightIntentFunction

```TypeScript
export declare const InsightIntentFunction: (() => ClassDecorator)
```

该装饰器与[@InsightIntentFunctionMethod](arkts-ability-app-ability-insightintentdecorator-insightintentfunctionmethod-d.md#insightintentfunctionmethod)装饰器必须组合使用。使用该装饰器来装饰类，同时使用[@InsightIntentFunctionMethod](arkts-ability-app-ability-insightintentdecorator-insightintentfunctionmethod-d.md#insightintentfunctionmethod)装饰器来装饰类中的静态函数，可以将对应的静态函数定义为意图，便于AI入口能够快速执行此函数。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
