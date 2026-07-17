# EnterprisePolicy

表示企业定制策略。

**起始版本：** 21

<!--Device-dlpPermission-export interface EnterprisePolicy--><!--Device-dlpPermission-export interface EnterprisePolicy-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## policyString

```TypeScript
policyString: string
```

表示企业定制策略的JSON字符串。长度不超过2<sup>22</sup>字节，超出此范围输出错误日志。

**类型：** string

**起始版本：** 21

<!--Device-EnterprisePolicy-policyString: string--><!--Device-EnterprisePolicy-policyString: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

