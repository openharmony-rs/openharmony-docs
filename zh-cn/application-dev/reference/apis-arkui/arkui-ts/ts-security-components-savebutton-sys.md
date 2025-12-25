# SaveButton (系统接口)

<!--Kit: ArkUI-->
<!--Subsystem: Security-->
<!--Owner: @harylee-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

安全控件的保存控件。应用集成保存控件后，用户首次使用保存控件展示弹窗，在点击允许后自动授权，应用会在短时间内获取访问媒体库特权接口的授权。后续使用无需弹窗授权。在API version 19及之前的版本中，授权持续时间为10秒；在API version 20及之后的版本中，授权持续时间为1分钟。


> **说明：**
>
> 该组件从API version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[SaveButton](ts-security-components-savebutton.md)。


## 接口

## SaveIconStyle枚举说明

保存控件的图标风格。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| PICTURE | 2 | 保存控件展示图片图标。|


