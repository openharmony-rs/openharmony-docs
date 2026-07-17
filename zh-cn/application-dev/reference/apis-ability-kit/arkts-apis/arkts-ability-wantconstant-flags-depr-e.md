# Flags

Flags说明。用于表示处理Want的方式。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** Flags

<!--Device-wantConstant-export enum Flags--><!--Device-wantConstant-export enum Flags-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_AUTH_READ_URI_PERMISSION

```TypeScript
FLAG_AUTH_READ_URI_PERMISSION = 0x00000001
```

指示对URI执行读取操作的授权。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** FLAG_AUTH_READ_URI_PERMISSION

<!--Device-Flags-FLAG_AUTH_READ_URI_PERMISSION = 0x00000001--><!--Device-Flags-FLAG_AUTH_READ_URI_PERMISSION = 0x00000001-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_AUTH_WRITE_URI_PERMISSION

```TypeScript
FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002
```

指示对URI执行写入操作的授权。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** FLAG_AUTH_WRITE_URI_PERMISSION

<!--Device-Flags-FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002--><!--Device-Flags-FLAG_AUTH_WRITE_URI_PERMISSION = 0x00000002-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_FORWARD_RESULT

```TypeScript
FLAG_ABILITY_FORWARD_RESULT = 0x00000004
```

将结果返回给元能力。

**起始版本：** 6

**废弃版本：** 9

<!--Device-Flags-FLAG_ABILITY_FORWARD_RESULT = 0x00000004--><!--Device-Flags-FLAG_ABILITY_FORWARD_RESULT = 0x00000004-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_CONTINUATION

```TypeScript
FLAG_ABILITY_CONTINUATION = 0x00000008
```

确定是否可以将本地设备上的功能迁移到远程设备。

**起始版本：** 6

**废弃版本：** 9

<!--Device-Flags-FLAG_ABILITY_CONTINUATION = 0x00000008--><!--Device-Flags-FLAG_ABILITY_CONTINUATION = 0x00000008-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_NOT_OHOS_COMPONENT

```TypeScript
FLAG_NOT_OHOS_COMPONENT = 0x00000010
```

指定组件是否属于OHOS。

**起始版本：** 6

**废弃版本：** 9

<!--Device-Flags-FLAG_NOT_OHOS_COMPONENT = 0x00000010--><!--Device-Flags-FLAG_NOT_OHOS_COMPONENT = 0x00000010-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_FORM_ENABLED

```TypeScript
FLAG_ABILITY_FORM_ENABLED = 0x00000020
```

指定是否启动某个能力。

**起始版本：** 6

**废弃版本：** 9

<!--Device-Flags-FLAG_ABILITY_FORM_ENABLED = 0x00000020--><!--Device-Flags-FLAG_ABILITY_FORM_ENABLED = 0x00000020-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_ABILITYSLICE_MULTI_DEVICE

```TypeScript
FLAG_ABILITYSLICE_MULTI_DEVICE = 0x00000100
```

支持分布式调度系统中的多设备启动。

**起始版本：** 6

**废弃版本：** 9

<!--Device-Flags-FLAG_ABILITYSLICE_MULTI_DEVICE = 0x00000100--><!--Device-Flags-FLAG_ABILITYSLICE_MULTI_DEVICE = 0x00000100-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_START_FOREGROUND_ABILITY

```TypeScript
FLAG_START_FOREGROUND_ABILITY = 0x00000200
```

指示无论主机应用程序是否已启动，都将启动使用服务模板的功能。

**起始版本：** 6

**废弃版本：** 9

<!--Device-Flags-FLAG_START_FOREGROUND_ABILITY = 0x00000200--><!--Device-Flags-FLAG_START_FOREGROUND_ABILITY = 0x00000200-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_INSTALL_ON_DEMAND

```TypeScript
FLAG_INSTALL_ON_DEMAND = 0x00000800
```

如果未安装指定的功能，请安装该功能。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** FLAG_INSTALL_ON_DEMAND

<!--Device-Flags-FLAG_INSTALL_ON_DEMAND = 0x00000800--><!--Device-Flags-FLAG_INSTALL_ON_DEMAND = 0x00000800-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_INSTALL_WITH_BACKGROUND_MODE

```TypeScript
FLAG_INSTALL_WITH_BACKGROUND_MODE = 0x80000000
```

如果未安装，使用后台模式安装该功能。

**起始版本：** 6

**废弃版本：** 9

<!--Device-Flags-FLAG_INSTALL_WITH_BACKGROUND_MODE = 0x80000000--><!--Device-Flags-FLAG_INSTALL_WITH_BACKGROUND_MODE = 0x80000000-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_CLEAR_MISSION

```TypeScript
FLAG_ABILITY_CLEAR_MISSION = 0x00008000
```

指示清除其他任务的操作。可以为传递给 **FeatureAbility** 中[startAbility](arkts-ability-featureability-startability-f.md#startability-1)方法的**Want**设置此标志，并且必须与**FLAG_ABILITY_NEW_MISSION**一起使用。

**起始版本：** 6

**废弃版本：** 9

<!--Device-Flags-FLAG_ABILITY_CLEAR_MISSION = 0x00008000--><!--Device-Flags-FLAG_ABILITY_CLEAR_MISSION = 0x00008000-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_NEW_MISSION

```TypeScript
FLAG_ABILITY_NEW_MISSION = 0x10000000
```

指示在历史任务堆栈上创建任务的操作。

**起始版本：** 6

**废弃版本：** 9

<!--Device-Flags-FLAG_ABILITY_NEW_MISSION = 0x10000000--><!--Device-Flags-FLAG_ABILITY_NEW_MISSION = 0x10000000-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## FLAG_ABILITY_MISSION_TOP

```TypeScript
FLAG_ABILITY_MISSION_TOP = 0x20000000
```

指示如果启动能力的现有实例已位于任务堆栈的顶部，则将重用该实例。否则，将创建一个新的能力实例。

**起始版本：** 6

**废弃版本：** 9

<!--Device-Flags-FLAG_ABILITY_MISSION_TOP = 0x20000000--><!--Device-Flags-FLAG_ABILITY_MISSION_TOP = 0x20000000-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

