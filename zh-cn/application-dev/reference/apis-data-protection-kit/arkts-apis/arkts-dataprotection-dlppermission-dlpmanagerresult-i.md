# DLPManagerResult

表示打开DLP权限管理应用的结果。

**起始版本：** 11

<!--Device-dlpPermission-export interface DLPManagerResult--><!--Device-dlpPermission-export interface DLPManagerResult-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## resultCode

```TypeScript
resultCode: number
```

表示打开DLP权限管理应用并退出后返回的结果码。取值范围为0到3。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DLPManagerResult-resultCode: number--><!--Device-DLPManagerResult-resultCode: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## want

```TypeScript
want: Want
```

表示打开DLP权限管理应用并退出后返回的数据。

**类型：** Want

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DLPManagerResult-want: Want--><!--Device-DLPManagerResult-want: Want-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

