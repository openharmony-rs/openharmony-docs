# getAccountManager

## getAccountManager

```TypeScript
function getAccountManager(): AccountManager
```

获取系统账号管理对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-osAccount-function getAccountManager(): AccountManager--><!--Device-osAccount-function getAccountManager(): AccountManager-End-->

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AccountManager](arkts-basicservices-osaccount-accountmanager-i.md) | 系统账号管理对象。 |

## 示例

```TypeScript
let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
```

