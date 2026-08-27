# NotifySnapshotCallback（系统接口）

```TypeScript
type NotifySnapshotCallback = (deviceId: string, mission: number) => void
```

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID，表示快照发生变化的远程设备。 |
| mission | number | 是 | 任务ID，表示快照发生变化的任务。 |
