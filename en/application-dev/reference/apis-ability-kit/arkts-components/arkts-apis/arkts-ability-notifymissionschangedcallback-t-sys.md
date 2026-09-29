# NotifyMissionsChangedCallback (System API)

```TypeScript
type NotifyMissionsChangedCallback = (deviceId: string) => void
```

Callback function on mission changed.

@typedef { function } NotifyMissionsChangedCallback

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-type NotifyMissionsChangedCallback = (deviceId: string) => void--><!--Device-unnamed-type NotifyMissionsChangedCallback = (deviceId: string) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates the deviceId mission changed. |
