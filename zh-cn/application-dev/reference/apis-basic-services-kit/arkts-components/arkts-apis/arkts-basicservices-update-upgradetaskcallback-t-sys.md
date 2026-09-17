# UpgradeTaskCallback（系统接口）

```TypeScript
export type UpgradeTaskCallback = (eventInfo: EventInfo) => void
```

事件回调。

**版本说明**： 从API version 23开始支持。

@typedef UpgradeTaskCallback [since 9 - 22] @typedef { function } UpgradeTaskCallback [since 23]

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventInfo | [EventInfo](arkts-basicservices-update-eventinfo-i-sys.md) | 是 | Event information. |
