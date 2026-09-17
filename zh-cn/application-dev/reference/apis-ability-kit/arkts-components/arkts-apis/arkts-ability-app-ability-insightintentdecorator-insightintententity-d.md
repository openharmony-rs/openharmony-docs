# @InsightIntentEntity

```TypeScript
export declare const InsightIntentEntity: ((intentEntityInfo: IntentEntityDecoratorInfo) => ClassDecorator)
```

使用该装饰器装饰一个继承自[IntentEntity](arkts-ability-insightintent-intententity-i.md)的类，可将该类定义为意图实体，用于传递意图调用时所需的参数。该装饰器支持的参数参见[IntentEntityDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intententitydecoratorinfo-i.md)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
