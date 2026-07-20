# @ohos.file.securityLabel

该模块提供文件数据安全等级的相关功能：向应用程序提供查询、设置文件数据安全等级的JS接口。

**起始版本：** 9

<!--Device-unnamed-declare namespace securityLabel--><!--Device-unnamed-declare namespace securityLabel-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { securityLabel } from '@kit.CoreFileKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getSecurityLabel](arkts-corefile-securitylabel-getsecuritylabel-f.md#getsecuritylabel) | 获取文件或目录的数据安全等级。若未设置过数据安全等级则默认返回“s3”。使用Promise异步回调。 |
| [getSecurityLabel](arkts-corefile-securitylabel-getsecuritylabel-f.md#getsecuritylabel-1) | 获取文件或目录的数据安全等级。若未设置过数据安全等级则默认返回“s3”。使用callback异步回调。 |
| [getSecurityLabelSync](arkts-corefile-securitylabel-getsecuritylabelsync-f.md#getsecuritylabelsync) | 以同步方法获取文件或目录的数据安全等级。若未设置过数据安全等级则默认返回“s3”。 |
| [setSecurityLabel](arkts-corefile-securitylabel-setsecuritylabel-f.md#setsecuritylabel) | 设置文件或目录的数据安全等级。数据安全等级仅可由低向高或平级设置。使用Promise异步回调。 |
| [setSecurityLabel](arkts-corefile-securitylabel-setsecuritylabel-f.md#setsecuritylabel-1) | 设置文件或目录的数据安全等级。数据安全等级仅可由低向高或平级设置。使用callback异步回调。 |
| [setSecurityLabelSync](arkts-corefile-securitylabel-setsecuritylabelsync-f.md#setsecuritylabelsync) | 以同步方法设置文件或目录的数据安全等级。数据安全等级仅可由低向高或平级设置。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DataLevel](arkts-corefile-securitylabel-datalevel-t.md) | 数据安全等级。 |

