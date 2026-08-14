# getDistributedAccountAbility

## getDistributedAccountAbility

```TypeScript
function getDistributedAccountAbility(): DistributedAccountAbility
```

获取分布式账号单实例对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-distributedAccount-function getDistributedAccountAbility(): DistributedAccountAbility--><!--Device-distributedAccount-function getDistributedAccountAbility(): DistributedAccountAbility-End-->

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DistributedAccountAbility](arkts-basicservices-distributedaccount-distributedaccountability-i.md) | 返回一个实例，实例提供查询和更新分布式账号登录状态方法。 |

## 示例

```TypeScript
// 获取分布式账号的单实例对象
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
```

