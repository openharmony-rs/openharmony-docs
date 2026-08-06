# AbilityStateData

AbilityStateData是Ability状态信息的数据结构。使用 [on]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 注册生命周期变化监听后，可以通过[ApplicationStateObserver]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的onAbilityStateChanged回调的入参获取该数据结构。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare class AbilityStateData--><!--Device-unnamed-declare class AbilityStateData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## abilityName

```TypeScript
abilityName: string
```

Ability名称。

**类型：** string

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-AbilityStateData-abilityName: string--><!--Device-AbilityStateData-abilityName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## abilityType

```TypeScript
abilityType: int
```

\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_： [UIAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_或 [ExtensionAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_等。

**类型：** int

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-AbilityStateData-abilityType: int--><!--Device-AbilityStateData-abilityType: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## appCloneIndex

```TypeScript
appCloneIndex?: int
```

应用包的\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_索引标识。

**类型：** int

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-AbilityStateData-appCloneIndex?: int--><!--Device-AbilityStateData-appCloneIndex?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

应用Bundle名称。

**类型：** string

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-AbilityStateData-bundleName: string--><!--Device-AbilityStateData-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## callerBundleName

```TypeScript
callerBundleName?: string
```

Ability创建时的拉起方Bundle名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AbilityStateData-callerBundleName?: string--><!--Device-AbilityStateData-callerBundleName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## isAtomicService

```TypeScript
isAtomicService: boolean
```

判断Ability所属应用是否为原子化服务。 true: 是原子化服务。 false: 不是原子化服务。

**类型：** boolean

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-AbilityStateData-isAtomicService: boolean--><!--Device-AbilityStateData-isAtomicService: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## moduleName

```TypeScript
moduleName: string
```

Ability所属的模块名称。

**类型：** string

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-AbilityStateData-moduleName: string--><!--Device-AbilityStateData-moduleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: int
```

进程ID。

**类型：** int

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-AbilityStateData-pid: int--><!--Device-AbilityStateData-pid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: int
```

Ability状态。 - \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_： [UIAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_的状态参见 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_； [ExtensionAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_的状态参见 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ ；[UIExtensionAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_的状态参见 \_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_ 。 - \_\_\_MD\_LINK\_DESC\_USD\_4\_\_\_：参见 \_\_\_MD\_LINK\_DESC\_USD\_5\_\_\_。

**类型：** int

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-AbilityStateData-state: int--><!--Device-AbilityStateData-state: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: int
```

所属应用程序的UID。

**类型：** int

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-AbilityStateData-uid: int--><!--Device-AbilityStateData-uid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

