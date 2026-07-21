# NotificationSlot
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

描述通知渠道，不同通知渠道对应的通知提醒方式不同。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn和ArkTS-Sta。
> - 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## NotificationSlot

**系统能力：** SystemCapability.Notification.Notification

| 名称                 | 类型                 | 只读 | 可选 | 说明                   |
| -------------------- | ---------------------|---- | --- |----------------------|
| notificationType<sup>11+</sup>                 | [notificationManager.SlotType](js-apis-notificationManager.md#slottype) | 否 | 是  | 渠道类型。不同渠道类型的通知提醒方式不同。<br/> **ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本**：23 |
| enabled<sup>9+</sup> | boolean               | 是 | 是  | 是否允许发布此通知渠道类型的通知。<br> - true：允许发布通知。<br> - false：禁止发布通知。<br/> **ArkTS-Dyn起始版本**：9<br/>**ArkTS-Sta起始版本**：23   |
| notificationLevel<sup>20+</sup>                 | [notificationManager.SlotLevel](js-apis-notificationManager.md#slotlevel) | 否 | 是  | 通知级别，用于描述该渠道类型通知的显示优先级和提醒强度。<br/> **ArkTS-Dyn起始版本**：20<br/>**ArkTS-Sta起始版本**：23           |
| desc                 | string                | 否 | 是  | 通知渠道描述信息。大小不超过243字节，超出部分会被截断。<br/> **ArkTS-Dyn起始版本**：7<br/>**ArkTS-Sta起始版本**：23 |
| badgeFlag            | boolean               | 否 | 是  | 是否显示角标。默认值为true。<br> - true：显示角标。<br> - false：不显示角标。<br/> **ArkTS-Dyn起始版本**：7<br/>**ArkTS-Sta起始版本**：23              |
| bypassDnd            | boolean               | 否 | 是  | 是否在系统中绕过免打扰模式。默认值为false。<br> - true：绕过免打扰模式，免打扰模式下仍会提醒。<br> - false：不绕过免打扰模式，免打扰模式下不提醒。<br/> **ArkTS-Dyn起始版本**：7<br/>**ArkTS-Sta起始版本**：23      |
| vibrationEnabled     | boolean               | 否 | 是  | 是否可振动。默认值为false。<br> - true：可振动。<br> - false：不可振动。<br/> **ArkTS-Dyn起始版本**：7<br/>**ArkTS-Sta起始版本**：23                  |
| sound                | string                | 否 | 是  | 该渠道的通知的自定义铃声文件名。该文件放在resources/rawfile目录下，支持m4a、aac、mp3、ogg、wav、flac、amr等格式。大小不超过243字节，超出部分会被截断。<br/> **ArkTS-Dyn起始版本**：7<br/>**ArkTS-Sta起始版本**：23 |
| lightEnabled         | boolean               | 否 | 是  | 是否闪灯。默认值为false。<br> - true：闪灯。<br> - false：不闪灯。<br/> **ArkTS-Dyn起始版本**：7<br/>**ArkTS-Sta起始版本**：23                        |
| type<sup>(deprecated)</sup> | [notification.SlotType](js-apis-notification.md#slottype) | 否 | 是  | 渠道类型。<br>从API version 7开始支持，从API version 11开始废弃，建议使用notificationType替代。<br/>**ArkTS模式：** 该属性仅适用于ArkTS-Dyn。 <br/>**ArkTS-Dyn起始版本**：7        |
| level<sup>(deprecated)</sup> | ArkTS-Dyn: [notification.SlotLevel](js-apis-notificationManager.md#slotlevel) | 否 | 是  | 通知级别。<br>从API version 7开始支持，从API version 20开始废弃，建议使用notificationLevel替代。<br/>**ArkTS模式：** 该属性仅适用于ArkTS-Dyn。 <br/>**ArkTS-Dyn起始版本**：7 |
| lockscreenVisibility | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 否 | 是  | 在锁定屏幕上显示通知的模式。预留能力，暂不支持。<br/> **ArkTS-Dyn起始版本**：7<br/>**ArkTS-Sta起始版本**：23 |
| lightColor           | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 否 | 是  | 通知灯颜色。预留能力，暂不支持。<br/> **ArkTS-Dyn起始版本**：7<br/>**ArkTS-Sta起始版本**：23                |
| vibrationValues      | ArkTS-Dyn: Array\<number\> <br/>ArkTS-Sta: Array\<long\> | 否 | 是  | 通知振动样式。预留能力，暂不支持。              |
