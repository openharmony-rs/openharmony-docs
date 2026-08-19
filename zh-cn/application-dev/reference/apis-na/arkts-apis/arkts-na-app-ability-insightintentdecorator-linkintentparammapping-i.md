# LinkIntentParamMapping

LinkIntentParamMapping是@InsightIntentLink装饰器的意图参数和URI信息的映射。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface LinkIntentParamMapping--><!--Device-unnamed-export declare interface LinkIntentParamMapping-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
```

## paramCategory

```TypeScript
paramCategory?: LinkParamCategory
```

若取值为[LINK](arkts-na-app-ability-insightintentdecorator-linkparamcategory-e.md)，系统获取paramName对应的映射名称，并以键值对形式拼接到URI末尾。若取值为[WANT](arkts-na-app-ability-insightintentdecorator-linkparamcategory-e.md)， 系统获取paramName对应的映射名称及其取值，通过[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)的parameters字段传递。

**类型：** [LinkParamCategory](arkts-na-app-ability-insightintentdecorator-linkparamcategory-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinkIntentParamMapping-paramCategory?: LinkParamCategory--><!--Device-LinkIntentParamMapping-paramCategory?: LinkParamCategory-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## paramMappingName

```TypeScript
paramMappingName?: string
```

表示意图参数映射名称。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinkIntentParamMapping-paramMappingName?: string--><!--Device-LinkIntentParamMapping-paramMappingName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## paramName

```TypeScript
paramName: string
```

表示意图参数的名称。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinkIntentParamMapping-paramName: string--><!--Device-LinkIntentParamMapping-paramName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

