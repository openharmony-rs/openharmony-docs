# CustomProperty（系统接口）

表示自定义策略。

**起始版本：** 21

<!--Device-dlpPermission-export interface CustomProperty--><!--Device-dlpPermission-export interface CustomProperty-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## enterprise

```TypeScript
enterprise: string
```

表示企业定制策略的JSON字符串。长度不超过2<sup>22</sup>字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

<!--Device-CustomProperty-enterprise: string--><!--Device-CustomProperty-enterprise: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

