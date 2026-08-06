# LinkIntentParamMapping

LinkIntentParamMapping是 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 装饰器的意图参数和uri信息的映射。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-unnamed-declare interface LinkIntentParamMapping--><!--Device-unnamed-declare interface LinkIntentParamMapping-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## paramCategory

```TypeScript
paramCategory?: LinkParamCategory
```

表示意图参数类别。 若意图参数类别取值为\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_，系统获取paramName字段对应的意图参数映射名称，并将该意图参数映射名称拼接到uri链接的末尾(以键值对的形式key=value，key为意图参数映射名 称，value为意图参数值)。 若意图参数类别为\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_，系统获取paramName字段对应的意图参数映射名称，并将该意图参数映射名称及取值通过\_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ 的parameters字段进行传递。

**类型：** LinkParamCategory

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LinkIntentParamMapping-paramCategory?: LinkParamCategory--><!--Device-LinkIntentParamMapping-paramCategory?: LinkParamCategory-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## paramMappingName

```TypeScript
paramMappingName?: string
```

表示意图参数映射名称。

**类型：** string

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LinkIntentParamMapping-paramMappingName?: string--><!--Device-LinkIntentParamMapping-paramMappingName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## paramName

```TypeScript
paramName: string
```

表示意图参数的名称。

**类型：** string

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LinkIntentParamMapping-paramName: string--><!--Device-LinkIntentParamMapping-paramName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

