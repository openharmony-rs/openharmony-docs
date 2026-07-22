# ProcessMode

UIAbility启动后的进程模式。ProcessMode作为[StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md)的一个属性，仅在[UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability)中生效，用来指定目标UIAbility的进程模式。该功能仅在2in1和Tablet设备上生效，在其他设备中返回801错误码。

**起始版本：** 12

<!--Device-contextConstant-export enum ProcessMode--><!--Device-contextConstant-export enum ProcessMode-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## NEW_PROCESS_ATTACH_TO_PARENT

```TypeScript
NEW_PROCESS_ATTACH_TO_PARENT = 1
```

创建一个新进程，并在该进程上启动UIAbility。该进程会跟随父进程退出。

**约束：**

使用此模式时，要求目标UIAbility跟调用方是在同一个应用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProcessMode-NEW_PROCESS_ATTACH_TO_PARENT = 1--><!--Device-ProcessMode-NEW_PROCESS_ATTACH_TO_PARENT = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM

```TypeScript
NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM = 2
```

创建一个新进程，在该进程上启动UIAbility，并绑定该进程到状态栏图标上。

**约束：**

使用此模式时，要求目标UIAbility跟调用方是在同一个应用，并且应用要在状态栏中有图标。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProcessMode-NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM = 2--><!--Device-ProcessMode-NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM = 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ATTACH_TO_STATUS_BAR_ITEM

```TypeScript
ATTACH_TO_STATUS_BAR_ITEM = 3
```

启动UIAbility，并绑定该UIAbility所在进程到状态栏图标上。

**约束：**

使用此模式时，要求目标UIAbility跟调用方是在同一个应用，并且应用要在状态栏中有图标。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProcessMode-ATTACH_TO_STATUS_BAR_ITEM = 3--><!--Device-ProcessMode-ATTACH_TO_STATUS_BAR_ITEM = 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

