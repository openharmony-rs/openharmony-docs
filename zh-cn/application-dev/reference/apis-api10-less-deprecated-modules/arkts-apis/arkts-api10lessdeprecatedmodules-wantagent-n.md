# wantAgent

WantAgent模块提供了创建WantAgent实例、获取实例的用户ID、获取want信息、比较WantAgent实例和获取bundle名称等能力。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wantAgent/wantAgent

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getBundleName](arkts-api10lessdeprecatedmodules-wantagent-getbundlename-f.md#getBundleName-1) | 获取WantAgent实例的Bundle名称。使用callback异步回调。<br/> |
| [getBundleName](arkts-api10lessdeprecatedmodules-wantagent-getbundlename-f.md#getBundleName-2) | 获取WantAgent实例的Bundle名称。使用Promise异步回调。<br/> |
| [getUid](arkts-api10lessdeprecatedmodules-wantagent-getuid-f.md#getUid-1) | 获取WantAgent实例的用户ID。使用callback异步回调。<br/> |
| [getUid](arkts-api10lessdeprecatedmodules-wantagent-getuid-f.md#getUid-2) | 获取WantAgent实例的用户ID。使用Promise异步回调。<br/> |
| <!--DelRow-->[getWant](arkts-api10lessdeprecatedmodules-wantagent-getwant-f-sys.md#getWant-1) | 获取WantAgent中的Want(callback形式)。<br/> |
| <!--DelRow-->[getWant](arkts-api10lessdeprecatedmodules-wantagent-getwant-f-sys.md#getWant-2) | 获取WantAgent中的Want(Promise形式)。<br/> |
| [cancel](arkts-api10lessdeprecatedmodules-wantagent-cancel-f.md#cancel-1) | 取消WantAgent实例。使用callback异步回调。<br/> |
| [cancel](arkts-api10lessdeprecatedmodules-wantagent-cancel-f.md#cancel-2) | 取消WantAgent实例。使用Promise异步回调。<br/> |
| [trigger](arkts-api10lessdeprecatedmodules-wantagent-trigger-f.md#trigger-1) | 主动激发WantAgent实例。使用callback异步回调。<br/> |
| [equal](arkts-api10lessdeprecatedmodules-wantagent-equal-f.md#equal-1) | 判断两个WantAgent实例是否相等，以此来判断是否是来自同一应用的相同操作。使用callback异步回调。<br/> |
| [equal](arkts-api10lessdeprecatedmodules-wantagent-equal-f.md#equal-2) | 判断两个WantAgent实例是否相等，以此来判断是否是来自同一应用的相同操作。使用Promise异步回调。<br/> |
| [getWantAgent](arkts-api10lessdeprecatedmodules-wantagent-getwantagent-f.md#getWantAgent-1) | 创建WantAgent。创建失败返回的WantAgent为空值。使用callback异步回调。<br/> |
| [getWantAgent](arkts-api10lessdeprecatedmodules-wantagent-getwantagent-f.md#getWantAgent-2) | 创建WantAgent。创建失败返回的WantAgent为空值。使用Promise异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CompleteData](arkts-api10lessdeprecatedmodules-wantagent-completedata-i.md) | 表示主动触发WantAgent返回的数据。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [WantAgentFlags](arkts-api10lessdeprecatedmodules-wantagent-wantagentflags-e.md) | 表示WantAgent行为控制标志，用于配置WantAgent的创建和触发行为。<br/> |
| [OperationType](arkts-api10lessdeprecatedmodules-wantagent-operationtype-e.md) | 表示WantAgent支持的操作类型。<br/> |

