# LinkParamCategory

@InsightIntentLink装饰器的意图参数类别，用于定义意图参数的传递形式。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare enum LinkParamCategory--><!--Device-unnamed-export declare enum LinkParamCategory-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## LINK

```TypeScript
LINK = 'link'
```

表示意图参数类别为'link'。系统获取paramName字段对应的意图参数映射名称，并将该意图参数映射名称拼接到URI链接的末尾。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinkParamCategory-LINK = 'link'--><!--Device-LinkParamCategory-LINK = 'link'-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## WANT

```TypeScript
WANT = 'want'
```

表示意图参数类别为'want'。系统获取paramName字段对应的意图参数映射名称，并将该意图参数映射名称及取值通过 [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md#Want)的parameters字段进行传递。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinkParamCategory-WANT = 'want'--><!--Device-LinkParamCategory-WANT = 'want'-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

