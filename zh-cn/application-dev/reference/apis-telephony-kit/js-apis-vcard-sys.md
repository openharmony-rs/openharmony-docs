# @ohos.telephony.vcard (VCard模块)（系统接口）
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @Fanyl8-->
<!--Designer: @ghxbob-->
<!--Tester: @weitiantian-->
<!--Adviser: @zhang_yixin13-->

VCard是电子名片的文件格式标准,它可包含的信息有：姓名、地址资讯、电话号码、URL，logo，相片等。VCard模块提供了VCard能力，包括将VCard文件导入联系人数据库和将联系人数据导出为VCard文件等。

>**说明：**
>
>本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。<br />
>本模块为系统接口。

## 导入模块

## VCardBuilderOptions<sup>11+</sup>

VCard版本和编码信息。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService

| 名称         | 类型   | 必填 |    说明    |
| ------------ | ------ | ---- | ---------- |
| cardType     | [VCardType](#vcardtype11) |  否  | VCard版本类型 (默认值为VERSION_21)。     |
| charset       | string |  否  | VCard编码类型（默认值为'UTF-8'）。     |

## VCardType<sup>11+</sup>

VCard版本类型。

**系统接口：** 此接口为系统接口。

**系统能力**：SystemCapability.Telephony.CoreService

| 名称            | 值   | 说明       |
| --------------- | ---- | ---------- |
| VERSION_21 | 0 | VCard2.1版本。 |
| VERSION_30 | 1 | VCard3.0版本。 |
| VERSION_40 | 2 | VCard4.0版本。 |
