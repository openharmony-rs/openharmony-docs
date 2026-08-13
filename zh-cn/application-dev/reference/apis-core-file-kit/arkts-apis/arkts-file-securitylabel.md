# @ohos.file.securityLabel

该模块提供文件数据安全等级的相关功能：向应用程序提供查询、设置文件数据安全等级的JS接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace securityLabel--><!--Device-unnamed-declare namespace securityLabel-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getSecurityLabel](arkts-corefile-securitylabel-getsecuritylabel-f.md#getSecurityLabel) | 获取文件或目录的数据安全等级。若未设置过数据安全等级则默认返回“s3”。使用Promise异步回调。 |
| [getSecurityLabel](arkts-corefile-securitylabel-getsecuritylabel-f.md#getSecurityLabel) | 获取文件或目录的数据安全等级。若未设置过数据安全等级则默认返回“s3”。使用callback异步回调。 |
| [getSecurityLabelSync](arkts-corefile-securitylabel-getsecuritylabelsync-f.md#getSecurityLabelSync) | 以同步方法获取文件或目录的数据安全等级。若未设置过数据安全等级则默认返回“s3”。 |
| [setSecurityLabel](arkts-corefile-securitylabel-setsecuritylabel-f.md#setSecurityLabel) | 设置文件或目录的数据安全等级。数据安全等级仅可由低向高或平级设置。使用Promise异步回调。 |
| [setSecurityLabel](arkts-corefile-securitylabel-setsecuritylabel-f.md#setSecurityLabel) | 设置文件或目录的数据安全等级。数据安全等级仅可由低向高或平级设置。使用callback异步回调。 |
| [setSecurityLabelSync](arkts-corefile-securitylabel-setsecuritylabelsync-f.md#setSecurityLabelSync) | 以同步方法设置文件或目录的数据安全等级。数据安全等级仅可由低向高或平级设置。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DataLevel](arkts-corefile-securitylabel-datalevel-t.md) | 数据安全等级。 |

