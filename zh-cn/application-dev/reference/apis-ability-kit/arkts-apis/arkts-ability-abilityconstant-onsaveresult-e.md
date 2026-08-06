# OnSaveResult

保存应用数据的结果，该类型为枚举。配合UIAbility的 [onSaveState()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 方法使用，可以实现\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AbilityConstant-export enum OnSaveResult--><!--Device-AbilityConstant-export enum OnSaveResult-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ALL_AGREE

```TypeScript
ALL_AGREE = 0
```

总是同意保存状态。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OnSaveResult-ALL_AGREE = 0--><!--Device-OnSaveResult-ALL_AGREE = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CONTINUATION_REJECT

```TypeScript
CONTINUATION_REJECT = 1
```

拒绝迁移保存状态。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OnSaveResult-CONTINUATION_REJECT = 1--><!--Device-OnSaveResult-CONTINUATION_REJECT = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CONTINUATION_MISMATCH

```TypeScript
CONTINUATION_MISMATCH = 2
```

迁移不匹配。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OnSaveResult-CONTINUATION_MISMATCH = 2--><!--Device-OnSaveResult-CONTINUATION_MISMATCH = 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## RECOVERY_AGREE

```TypeScript
RECOVERY_AGREE = 3
```

同意恢复保存状态。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OnSaveResult-RECOVERY_AGREE = 3--><!--Device-OnSaveResult-RECOVERY_AGREE = 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## RECOVERY_REJECT

```TypeScript
RECOVERY_REJECT = 4
```

拒绝恢复保存状态。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OnSaveResult-RECOVERY_REJECT = 4--><!--Device-OnSaveResult-RECOVERY_REJECT = 4-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ALL_REJECT

```TypeScript
ALL_REJECT = 5
```

Always rejected to save the status.

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OnSaveResult-ALL_REJECT = 5--><!--Device-OnSaveResult-ALL_REJECT = 5-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

