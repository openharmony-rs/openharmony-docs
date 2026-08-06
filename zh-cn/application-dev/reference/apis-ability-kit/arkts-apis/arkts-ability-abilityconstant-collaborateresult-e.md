# CollaborateResult

应用协同状态，该类型为枚举。用于多设备场景下，调用方应用拉起协同方应用时，协同方应用是否接受协同。需要配合UIAbility的 [onCollaborate()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法进行 设置。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-AbilityConstant-export enum CollaborateResult--><!--Device-AbilityConstant-export enum CollaborateResult-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ACCEPT

```TypeScript
ACCEPT = 0
```

接受协同。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollaborateResult-ACCEPT = 0--><!--Device-CollaborateResult-ACCEPT = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REJECT

```TypeScript
REJECT = 1
```

拒绝协同。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollaborateResult-REJECT = 1--><!--Device-CollaborateResult-REJECT = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

