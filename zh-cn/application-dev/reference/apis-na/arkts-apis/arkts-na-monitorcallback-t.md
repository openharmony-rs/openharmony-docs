# MonitorCallback

```TypeScript
export type MonitorCallback = (iMonitor: IMonitor) => void
```

触发监听时被调用的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type MonitorCallback = (iMonitor: IMonitor) => void--><!--Device-unnamed-export type MonitorCallback = (iMonitor: IMonitor) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iMonitor | [IMonitor](arkts-na-decorator-imonitor-i.md) | 是 | 保存触发监听前后的值以及路径。 |

