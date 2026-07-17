# NotifySnapshotCallback（系统接口）

```TypeScript
type NotifySnapshotCallback = (deviceId: string, mission: number) => void
```

快照更改时的回调函数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type NotifySnapshotCallback = (deviceId: string, mission: int) => void--><!--Device-unnamed-type NotifySnapshotCallback = (deviceId: string, mission: int) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | Indicates the deviceId snapshot changed. |
| mission | int | 是 | Indicates the id of mission. |

