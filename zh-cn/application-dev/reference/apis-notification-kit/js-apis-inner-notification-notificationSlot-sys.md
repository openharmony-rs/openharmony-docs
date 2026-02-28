# NotificationSlot(系统接口)

描述通知渠道，不同通知渠道对应的通知提醒方式不同。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 当前界面仅包含本模块的系统接口，其他公开接口参见[NotificationSlot](./js-apis-inner-notification-notificationSlot.md)。

## NotificationSlot

**系统能力：** SystemCapability.Notification.Notification

| 名称                 | 类型                 | 只读 | 可选 | 说明                   |
| -------------------- | ------------------- | ---- |-----|------------------------|
| reminderMode<sup>11+</sup> | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是 | 是  | 通知提醒模式。<br>**系统接口**：此接口为系统接口。 <br>- bit0：铃声提示。0表示关闭，1表示开启。 <br>- bit1：锁屏。0表示关闭，1表示开启。 <br>- bit2：横幅。0表示关闭，1表示开启。 <br>- bit3：亮屏。0表示关闭，1表示开启。 <br>- bit4：振动。0表示关闭，1表示开启。 <br>- bit5：状态栏通知图标。0表示关闭，1表示开启。<br/> **ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本**：23    |
| authorizedStatus<sup>12+</sup> | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是 | 是  | 授权状态。<br>**系统接口**：此接口为系统接口。 <br>- 0：表示已授权。 <br>- 1：表示待授权。<br/> **ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：23    |
