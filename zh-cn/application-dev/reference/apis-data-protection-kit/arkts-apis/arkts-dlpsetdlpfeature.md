# @ohos.dlpSetDlpFeature

本模块提供数据防泄漏（Data Loss Prevention，简称为DLP）特性开关的控制能力，包括开启和关闭DLP特性开关、返回特性开关设置结果等。

**使用场景**：

- 需要满足数据安全合规要求的场景。
- 对机密文件进行访问控制和加密保护。

> **说明：**
>
> - 本模块首批接口从API version 26.0.0开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口为系统接口。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [setDlpFeature](arkts-dataprotection-setdlpfeature-f-sys.md#setdlpfeature-1) | 设置DLP特性开关状态。使用Promise异步回调。调用成功后，DLP特性开关将设置为指定状态，系统将根据该状态启用或禁用DLP保护功能。当特性开关处于开启状态时，右键单击支持加密的文件，右键菜单中会显示“加密保护”选项。可加密类型包括：.txt，.pdf，.xls，.xlsx，.ppt，.pptx，.doc，.docx。企业策略开启或关闭数据防泄漏功能时使用此接口。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DLPFeatureInfo](arkts-dataprotection-dlpfeatureinfo-i-sys.md) | DLP特性开关的状态信息。 |
| [StatusInfoResult](arkts-dataprotection-statusinforesult-i-sys.md) | DLP特性开关状态设置的结果信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DlpFeatureStatus](arkts-dataprotection-dlpfeaturestatus-e-sys.md) | DLP特性开关状态的枚举。 |
<!--DelEnd-->

