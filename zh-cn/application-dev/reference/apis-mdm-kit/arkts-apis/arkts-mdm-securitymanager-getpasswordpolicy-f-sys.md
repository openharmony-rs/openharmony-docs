# getPasswordPolicy（系统接口）

## getPasswordPolicy

```TypeScript
function getPasswordPolicy(): PasswordPolicy
```

��ȡ�豸����������ԡ�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PasswordPolicy | �豸����������ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
import { securityManager } from '@kit.MDMKit';

try {
  let result: securityManager.PasswordPolicy = securityManager.getPasswordPolicy();
  console.info(`Succeeded in getting password policy, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get password policy. Code: ${err.code}, message: ${err.message}`);
}

```

