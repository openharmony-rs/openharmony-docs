# NotificationFlags
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @michael_woo888-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

描述通知标志的实例。

> **说明：**
>
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**系统能力**：SystemCapability.Notification.Notification

## 属性

| 名称             | 类型                    | 只读 | 可选 | 说明                                         |
| ---------------- | ---------------------- | ---- | -----|-------------------------------------------- |
| soundEnabled     | [NotificationFlagStatus](#notificationflagstatus11) | 是  | 是 | 是否启用声音提示。    |
| vibrationEnabled | [NotificationFlagStatus](#notificationflagstatus11) | 是  | 是 | 是否启用振动提醒功能。 |


## NotificationFlagStatus<sup>11+</sup>

描述通知标志状态。

**系统能力**：SystemCapability.Notification.Notification

| 名称           | 值  | 说明                               |
| -------------- | --- | --------------------------------- |
| TYPE_NONE      | 0   | 默认标志，效果等同于打开。          |
| TYPE_OPEN      | 1   | 通知标志打开。                     |
| TYPE_CLOSE     | 2   | 通知标志关闭。                     |
