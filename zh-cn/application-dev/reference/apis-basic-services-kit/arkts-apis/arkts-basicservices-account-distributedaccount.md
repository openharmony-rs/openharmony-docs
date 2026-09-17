# @ohos.account.distributedAccount(分布式账号管理)

本模块提供管理分布式账号的一些基础功能，主要包括查询和更新账号登录状态。适用于多设备协同场景，提升跨设备账号管理的一致性和用户体验。典型使用场景包括多设备协同、分布式数据同步、跨设备能力调用等。

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { distributedAccount } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getDistributedAccountAbility](arkts-basicservices-distributedaccount-getdistributedaccountability-f.md) | 获取分布式账号的单实例对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DistributedAccountAbility](arkts-basicservices-distributedaccount-distributedaccountability-i.md) | 提供查询和更新分布式账号登录状态方法（使用前需要先获取分布式账号的单实例对象）。 |
| [DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md) | 提供操作系统账号的分布式账号信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DistributedAccountAbility](arkts-basicservices-distributedaccount-distributedaccountability-i-sys.md) | 提供查询和更新分布式账号登录状态方法（使用前需要先获取分布式账号的单实例对象）。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DistributedAccountStatus](arkts-basicservices-distributedaccount-distributedaccountstatus-e.md) | 表示分布式账号状态枚举。 |
