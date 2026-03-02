# NotificationFlags

描述通知标志的实例。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**系统能力**：SystemCapability.Notification.Notification

**ArkTS-Dyn起始版本**：8

**ArkTS-Sta起始版本**：23

## 属性

| 名称             | 类型                    | 只读 | 可选 | 说明                                         |
| ---------------- | ---------------------- | ---- | -----|-------------------------------------------- |
| soundEnabled     | [NotificationFlagStatus](#notificationflagstatus11) | 否  | 是 | 是否启用声音提示功能。从API version 23开始成为可写参数，设置时仅[TYPE_CLOSE](#notificationflagstatus11)会生效。<br/>**ArkTS-Dyn起始版本**：8 <br/>**ArkTS-Sta起始版本**：23    |
| vibrationEnabled | [NotificationFlagStatus](#notificationflagstatus11) | 否  | 是 | 是否启用振动提醒功能。从API version 23开始成为可写参数，设置时仅[TYPE_CLOSE](#notificationflagstatus11)会生效。<br/>**ArkTS-Dyn起始版本**：8 <br/>**ArkTS-Sta起始版本**：23 |
| bannerEnabled<sup>23+</sup> | [NotificationFlagStatus](#notificationflagstatus11) | 否  | 是 | 是否启用横幅功能。设置时仅[TYPE_CLOSE](#notificationflagstatus11)会生效。<br/>**ArkTS-Dyn起始版本**：23<br/>**ArkTS-Sta起始版本**：23 |
| lockScreenEnabled<sup>23+</sup> | [NotificationFlagStatus](#notificationflagstatus11) | 否  | 是 | 是否启用锁屏功能。设置时仅[TYPE_CLOSE](#notificationflagstatus11)会生效。<br/>**ArkTS-Dyn起始版本**：23<br/>**ArkTS-Sta起始版本**：23 |


## NotificationFlagStatus<sup>11+</sup>

描述通知标志状态。

**系统能力**：SystemCapability.Notification.Notification

**ArkTS-Dyn起始版本**：11

**ArkTS-Sta起始版本**：23

| 名称           | 值  | 说明                               |
| -------------- | --- | --------------------------------- |
| TYPE_NONE      | 0   | 默认标志，效果等同于打开。          |
| TYPE_OPEN      | 1   | 通知标志打开。                     |
| TYPE_CLOSE     | 2   | 通知标志关闭。                     |
