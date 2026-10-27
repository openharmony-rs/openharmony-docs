# isSelfSuperAdmin

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## isSelfSuperAdmin

```TypeScript
function isSelfSuperAdmin(): boolean
```

查询自身是否是超级管理员应用

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function isSelfSuperAdmin(): boolean--><!--Device-adminManager-function isSelfSuperAdmin(): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果self是超级设备管理员，则返回true；如果self是不是超级管理员设备，则返回false。 |

**示例**

```TypeScript
import { adminManager } from '@kit.MDMKit';

try {
  let result: boolean = adminManager.isSelfSuperAdmin();
  console.info(`Succeeded in querying admin is super admin or not : ${result}`);
} catch (err) {
  console.error(`Failed to query admin is super admin or not. Code: ${err.code}, message: ${err.message}`);
}
```
