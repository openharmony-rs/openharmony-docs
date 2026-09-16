# @InsightIntentForm

```TypeScript
export declare const InsightIntentForm: ((intentInfo: FormIntentDecoratorInfo) => ClassDecorator)
```

使用该装饰器装饰[FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md)并配置[FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md)绑定的卡片名称，便于AI入口通过意图添加卡片。该装饰器支持的参数参见[FormIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-formintentdecoratorinfo-i.md)。

> **说明：** 
> 
> 卡片名称定义的要求参见卡片配置。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
