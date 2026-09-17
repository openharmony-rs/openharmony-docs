# NotifySnapshotCallback (System API)

```TypeScript
type NotifySnapshotCallback = (deviceId: string, mission: number) => void
```

Callback function on snapshot changed.

@typedef { function } NotifySnapshotCallback

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates the deviceId snapshot changed. |
| mission | number | Yes | Indicates the id of mission. |
