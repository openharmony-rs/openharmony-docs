# NotifyMissionsChangedCallback（系统接口）

```TypeScript
type NotifyMissionsChangedCallback = (deviceId: string) => void
```

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID，表示发生任务变化的远程设备。 |
