# MissionListener（系统接口）

定义系统任务状态监听，可以通过[on](arkts-ability-missionmanager-on-f-sys.md#on-1)注册。

**起始版本：** 8

<!--Device-unnamed-export interface MissionListener--><!--Device-unnamed-export interface MissionListener-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

<a id="onmissionclosed"></a>
## onMissionClosed

```TypeScript
onMissionClosed(mission: number): void
```

当系统关闭任务时会触发该回调函数。

**起始版本：** 9

<!--Device-MissionListener-onMissionClosed(mission: int): void--><!--Device-MissionListener-onMissionClosed(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示关闭的任务ID。 |

<a id="onmissioncreated"></a>
## onMissionCreated

```TypeScript
onMissionCreated(mission: number): void
```

当系统创建任务时会触发该回调函数。

**起始版本：** 8

<!--Device-MissionListener-onMissionCreated(mission: int): void--><!--Device-MissionListener-onMissionCreated(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示创建的任务ID。 |

<a id="onmissiondestroyed"></a>
## onMissionDestroyed

```TypeScript
onMissionDestroyed(mission: number): void
```

当系统销毁任务时会触发该回调函数。

**起始版本：** 8

<!--Device-MissionListener-onMissionDestroyed(mission: int): void--><!--Device-MissionListener-onMissionDestroyed(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示销毁的任务ID。 |

<a id="onmissioniconupdated"></a>
## onMissionIconUpdated

```TypeScript
onMissionIconUpdated(mission: number, icon: image.PixelMap): void
```

当系统更新任务图标时会触发该回调函数。

**起始版本：** 9

<!--Device-MissionListener-onMissionIconUpdated(mission: int, icon: image.PixelMap): void--><!--Device-MissionListener-onMissionIconUpdated(mission: int, icon: image.PixelMap): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示任务ID。 |
| icon | image.PixelMap | 是 | 表示更新的任务图标。 |

<a id="onmissionlabelupdated"></a>
## onMissionLabelUpdated

```TypeScript
onMissionLabelUpdated(mission: number): void
```

当系统更新任务标签时会触发该回调函数。

**起始版本：** 9

<!--Device-MissionListener-onMissionLabelUpdated(mission: int): void--><!--Device-MissionListener-onMissionLabelUpdated(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示任务ID。 |

<a id="onmissionmovedtofront"></a>
## onMissionMovedToFront

```TypeScript
onMissionMovedToFront(mission: number): void
```

当系统将任务移动到前台时会触发该回调函数。

**起始版本：** 8

<!--Device-MissionListener-onMissionMovedToFront(mission: int): void--><!--Device-MissionListener-onMissionMovedToFront(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示任务ID。 |

<a id="onmissionsnapshotchanged"></a>
## onMissionSnapshotChanged

```TypeScript
onMissionSnapshotChanged(mission: number): void
```

当系统更新任务缩略图时会触发该回调函数。

**起始版本：** 8

<!--Device-MissionListener-onMissionSnapshotChanged(mission: int): void--><!--Device-MissionListener-onMissionSnapshotChanged(mission: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mission | number | 是 | 表示任务ID。 |

