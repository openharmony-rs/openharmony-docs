# getOsAccountSubProfileManager（系统接口）

## getOsAccountSubProfileManager

```TypeScript
function getOsAccountSubProfileManager(): OsAccountSubProfileManager
```

获取系统账号子身份资料管理器。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-osAccount-function getOsAccountSubProfileManager(): OsAccountSubProfileManager--><!--Device-osAccount-function getOsAccountSubProfileManager(): OsAccountSubProfileManager-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 系统账号子身份资料管理器的实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';

let subProfileManager: osAccount.OsAccountSubProfileManager = osAccount.getOsAccountSubProfileManager();
```

ArkTS-Sta示例：

```TypeScript
import osAccount from '@ohos.account.osAccount';

let subProfileManager: osAccount.OsAccountSubProfileManager = osAccount.getOsAccountSubProfileManager();
```

