# @ohos.dlpSetDlpFeature

本模块提供数据防泄漏（Data Loss Prevention，简称为DLP）特性开关的控制能力，包括开启和关闭DLP特性开关、返回特性开关设置结果等。

**使用场景**：

- 需要满足数据安全合规要求的场景。
- 对机密文件进行访问控制和加密保护。

**起始版本**：26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[setDlpFeature](arkts-dataprotection-dlpsetdlpfeature-setdlpfeature-f-sys.md#setDlpFeature-1) | 设置DLP特性开关状态。使用Promise异步回调。调用成功后，DLP特性开关将设置为指定状态，系统将根据该状态启用或禁用DLP保护功能。<br/><br/>当特性开关处于开启状态时，右键单击支持加密的文件，右键菜单中会显示“加密保护”选项。可加密类型包括：.txt，.pdf，.xls，.xlsx，.ppt，.pptx，.doc，.docx。<br/><br/>企业策略开启或关闭数据防泄漏功能时使用此接口。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[DLPFeatureInfo](arkts-dataprotection-dlpsetdlpfeature-dlpfeatureinfo-i-sys.md) | DLP特性开关的状态信息。<br/> |
| <!--DelRow-->[StatusInfoResult](arkts-dataprotection-dlpsetdlpfeature-statusinforesult-i-sys.md) | DLP特性开关状态设置的结果信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[DlpFeatureStatus](arkts-dataprotection-dlpsetdlpfeature-dlpfeaturestatus-e-sys.md) | DLP特性开关状态的枚举。<br/> |

