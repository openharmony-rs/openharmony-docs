# getAccountManager

## getAccountManager

```TypeScript
function getAccountManager(): AccountManager
```

获取系统账号管理对象。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-osAccount-function getAccountManager(): AccountManager--><!--Device-osAccount-function getAccountManager(): AccountManager-End-->

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 系统账号管理对象。 |

**示例：**

```TypeScript
let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
```

