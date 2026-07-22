# getAuthorizationManager（系统接口）

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## getAuthorizationManager

```TypeScript
function getAuthorizationManager(): AuthorizationManager
```

获取系统账号授权管理器。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-osAccount-function getAuthorizationManager(): AuthorizationManager--><!--Device-osAccount-function getAuthorizationManager(): AuthorizationManager-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AuthorizationManager](arkts-basicservices-osaccount-authorizationmanager-i-sys.md) | 返回系统账号授权管理的实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例：**

```TypeScript
let authorizationManager: osAccount.AuthorizationManager = osAccount.getAuthorizationManager();

```

