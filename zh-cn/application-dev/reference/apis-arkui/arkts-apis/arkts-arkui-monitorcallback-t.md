# MonitorCallback

```TypeScript
export declare type MonitorCallback = (monitorValue: IMonitor) => void
```

参数为[IMonitor](../arkts-components/arkts-arkui-imonitor-i.md)类型的监听回调函数。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monitorValue | IMonitor | 是 | 回调函数传入的变化信息。 |

