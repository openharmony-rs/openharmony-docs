# MissionListener（系统接口）

定义系统任务状态监听，可以通过[on]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_注册。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface MissionListener--><!--Device-unnamed-export interface MissionListener-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## onMissionClosed

ArkTS-Dyn:
```TypeScript
onMissionClosed(mission: number): void
```

ArkTS-Sta:
```TypeScript
onMissionClosed(mission: int): void
```

当系统关闭任务时会触发该回调函数。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-MissionListener-onMissionClosed(mission: int): void--><!--Device-MissionListener-onMissionClosed(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示关闭的任务ID。 |

## onMissionCreated

ArkTS-Dyn:
```TypeScript
onMissionCreated(mission: number): void
```

ArkTS-Sta:
```TypeScript
onMissionCreated(mission: int): void
```

当系统创建任务时会触发该回调函数。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-MissionListener-onMissionCreated(mission: int): void--><!--Device-MissionListener-onMissionCreated(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示创建的任务ID。 |

## onMissionDestroyed

ArkTS-Dyn:
```TypeScript
onMissionDestroyed(mission: number): void
```

ArkTS-Sta:
```TypeScript
onMissionDestroyed(mission: int): void
```

当系统销毁任务时会触发该回调函数。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-MissionListener-onMissionDestroyed(mission: int): void--><!--Device-MissionListener-onMissionDestroyed(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示销毁的任务ID。 |

## onMissionIconUpdated

ArkTS-Dyn:
```TypeScript
onMissionIconUpdated(mission: number, icon: image.PixelMap): void
```

ArkTS-Sta:
```TypeScript
onMissionIconUpdated(mission: int, icon: image.PixelMap): void
```

当系统更新任务图标时会触发该回调函数。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-MissionListener-onMissionIconUpdated(mission: int, icon: image.PixelMap): void--><!--Device-MissionListener-onMissionIconUpdated(mission: int, icon: image.PixelMap): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示任务ID。 |
| icon | image.PixelMap | 是 | 表示更新的任务图标。 |

## onMissionLabelUpdated

ArkTS-Dyn:
```TypeScript
onMissionLabelUpdated(mission: number): void
```

ArkTS-Sta:
```TypeScript
onMissionLabelUpdated(mission: int): void
```

当系统更新任务标签时会触发该回调函数。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-MissionListener-onMissionLabelUpdated(mission: int): void--><!--Device-MissionListener-onMissionLabelUpdated(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示任务ID。 |

## onMissionMovedToFront

ArkTS-Dyn:
```TypeScript
onMissionMovedToFront(mission: number): void
```

ArkTS-Sta:
```TypeScript
onMissionMovedToFront(mission: int): void
```

当系统将任务移动到前台时会触发该回调函数。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-MissionListener-onMissionMovedToFront(mission: int): void--><!--Device-MissionListener-onMissionMovedToFront(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示任务ID。 |

## onMissionSnapshotChanged

ArkTS-Dyn:
```TypeScript
onMissionSnapshotChanged(mission: number): void
```

ArkTS-Sta:
```TypeScript
onMissionSnapshotChanged(mission: int): void
```

当系统更新任务缩略图时会触发该回调函数。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-MissionListener-onMissionSnapshotChanged(mission: int): void--><!--Device-MissionListener-onMissionSnapshotChanged(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示任务ID。 |

