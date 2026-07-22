# createAppAccountManager

## 导入模块

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## createAppAccountManager

```TypeScript
function createAppAccountManager(): AppAccountManager
```

创建应用账号管理器对象。

**起始版本：** 7

<!--Device-appAccount-function createAppAccountManager(): AppAccountManager--><!--Device-appAccount-function createAppAccountManager(): AppAccountManager-End-->

**系统能力：** SystemCapability.Account.AppAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AppAccountManager](arkts-basicservices-appaccount-appaccountmanager-i.md) | 应用账号管理器对象。 |

**示例：**

```TypeScript
let appAccountManager: appAccount.AppAccountManager = appAccount.createAppAccountManager();

```

