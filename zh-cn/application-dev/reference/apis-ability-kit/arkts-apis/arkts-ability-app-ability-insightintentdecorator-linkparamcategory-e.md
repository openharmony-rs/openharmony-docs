# LinkParamCategory

\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 装饰器的意图参数类别，用于定义意图参数的传递形式。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-unnamed-declare enum LinkParamCategory--><!--Device-unnamed-declare enum LinkParamCategory-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## LINK

```TypeScript
LINK = 'link'
```

表示意图参数类别为'link'。意图参数将被拼接到uri链接的末尾，以uri链接的形式传给应用。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LinkParamCategory-LINK = 'link'--><!--Device-LinkParamCategory-LINK = 'link'-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## WANT

```TypeScript
WANT = 'want'
```

表示意图参数类别为'want'。意图参数将通过[Want]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的parameters字段传给应用。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LinkParamCategory-WANT = 'want'--><!--Device-LinkParamCategory-WANT = 'want'-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

