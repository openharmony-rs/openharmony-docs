# NotifyMissionsChangedCallback（系统接口）

```TypeScript
type NotifyMissionsChangedCallback = (deviceId: string) => void
```

任务回调函数已更改。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type NotifyMissionsChangedCallback = (deviceId: string) => void--><!--Device-unnamed-type NotifyMissionsChangedCallback = (deviceId: string) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | Indicates the deviceId mission changed.  |

