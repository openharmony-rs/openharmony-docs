# @InsightIntentPage

```TypeScript
export declare const InsightIntentPage: ((intentInfo: PageIntentDecoratorInfo) => ClassDecorator)
```

使用该装饰器装饰当前应用的页面，可以将页面定义为意图，便于AI入口通过意图快速跳转到指定页面。该装饰器支持的参数参见[PageIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-pageintentdecoratorinfo-i.md)。

> **说明：** 
> 
> 该装饰器仅支持装饰struct页面。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
