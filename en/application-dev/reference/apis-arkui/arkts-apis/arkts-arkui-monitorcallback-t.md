# MonitorCallback

```TypeScript
export declare type MonitorCallback = (monitorValue: IMonitor) => void
```

A listener callback function of the [IMonitor](../arkts-components/arkts-arkui-common-comp-imonitor-i.md) type.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-unnamed-export declare type MonitorCallback = (monitorValue: IMonitor) => void--><!--Device-unnamed-export declare type MonitorCallback = (monitorValue: IMonitor) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| monitorValue | [IMonitor](../arkts-components/arkts-arkui-common-comp-imonitor-i.md) | Yes | Change information passed in by the callback, including the path of the state variable change (**dirty**), values before and after the change (obtained through the **value** API), and other details. For details about specific attributes and APIs, see **IMonitor**. |
