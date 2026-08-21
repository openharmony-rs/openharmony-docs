# SaveButton (系统接口)

<!--Kit: ArkUI-->
<!--Subsystem: Security-->
<!--Owner: @harylee-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

## 模块简介

安全控件的保存控件系统接口，适用于应用需要临时获取媒体库访问权限以保存图片或视频的场景，例如图片保存到相册、媒体内容导出等。

应用集成保存控件后，用户首次使用该控件时，保存控件会展示弹窗供用户确认。用户点击允许后，应用获取访问媒体库接口的临时授权，相关接口请参见[Interface (PhotoAccessHelper)](../../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md)；用户拒绝或关闭弹窗时，本次不授权，应用不会获得媒体库接口访问权限。后续使用无需弹窗授权。

在API version 19及之前的版本中，授权持续时间为10秒；在API version 20及之后的版本中，授权持续时间为1分钟。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 该组件从API version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[SaveButton](ts-security-components-savebutton.md)。

## 关键Class/Interface介绍

### 核心枚举类型

- **[SaveIconStyle](#saveiconstyle)：** 保存控件图标风格枚举，用于系统接口扩展保存控件图标样式。

## SaveIconStyle

保存控件的图标风格。

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| PICTURE | 2 | 保存控件展示图片图标。|
