# NotifyNetDisconnectCallback (System API)

```TypeScript
type NotifyNetDisconnectCallback = (deviceId: string, state: number) => void
```

Callback function on network disconnect.

@typedef { function } NotifyNetDisconnectCallback

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates the deviceId network disconnect. |
| state | number | Yes | Indicates the state of network. |
