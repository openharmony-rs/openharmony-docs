# @InsightIntentFunctionMethod

```TypeScript
export declare const InsightIntentFunctionMethod: ((intentInfo: FunctionIntentDecoratorInfo) => MethodDecorator)
```

该装饰器与[@InsightIntentFunction](arkts-ability-app-ability-insightintentdecorator-insightintentfunction-d.md#insightintentfunction)装饰器必须组合使用。使用该装饰器来装饰类中的静态函数，同时使用@InsightIntentFunction装饰器来装饰静态函数所属的类，可以将对应的静态函数定义为意图，便于AI入口能够快速执行此函数。

> **说明：** 
> 
> 静态方法所在的类需要通过export导出。
> 函数的参数名称、参数类型需要与意图定义的参数名称、参数类型保持一致。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
