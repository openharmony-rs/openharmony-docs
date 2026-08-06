# ReturnMode

意图执行结果返回给意图拉起方的返回形式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-insightIntent-enum ReturnMode--><!--Device-insightIntent-enum ReturnMode-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CALLBACK

```TypeScript
CALLBACK = 0
```

表示意图执行结果将由[意图执行基类]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中的 [onExecuteInUIAbilityForegroundMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 接口或 [onExecuteInUIExtensionAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_ 接口返回。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ReturnMode-CALLBACK = 0--><!--Device-ReturnMode-CALLBACK = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## FUNCTION

```TypeScript
FUNCTION = 1
```

表示意图执行结果会延迟返回，直到开发者主动调用[意图提供方管理能力]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中的 [sendExecuteResult]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口或 [sendIntentResult]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口返回意图执行结 果。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ReturnMode-FUNCTION = 1--><!--Device-ReturnMode-FUNCTION = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

