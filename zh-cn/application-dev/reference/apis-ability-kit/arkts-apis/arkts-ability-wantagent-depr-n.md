# wantAgent

WantAgent模块提供了创建WantAgent实例、获取实例的用户ID、获取want信息、比较WantAgent实例和获取bundle名称等能力。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wantAgent/wantAgent

<!--Device-unnamed-declare namespace wantAgent--><!--Device-unnamed-declare namespace wantAgent-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getBundleName](arkts-ability-wantagent-getbundlename-depr-f.md#getbundlename-1) | 获取WantAgent实例的Bundle名称。使用callback异步回调。 |
| [getBundleName](arkts-ability-wantagent-getbundlename-depr-f.md#getbundlename-2) | 获取WantAgent实例的Bundle名称。使用Promise异步回调。 |
| [getUid](arkts-ability-wantagent-getuid-depr-f.md#getuid-1) | 获取WantAgent实例的用户ID。使用callback异步回调。 |
| [getUid](arkts-ability-wantagent-getuid-depr-f.md#getuid-2) | 获取WantAgent实例的用户ID。使用Promise异步回调。 |
| [cancel](arkts-ability-wantagent-cancel-depr-f.md#cancel-1) | 取消WantAgent实例。使用callback异步回调。 |
| [cancel](arkts-ability-wantagent-cancel-depr-f.md#cancel-2) | 取消WantAgent实例。使用Promise异步回调。 |
| [trigger](arkts-ability-wantagent-trigger-depr-f.md#trigger-1) | 主动激发WantAgent实例。使用callback异步回调。 |
| [equal](arkts-ability-wantagent-equal-depr-f.md#equal-1) | 判断两个WantAgent实例是否相等，以此来判断是否是来自同一应用的相同操作。使用callback异步回调。 |
| [equal](arkts-ability-wantagent-equal-depr-f.md#equal-2) | 判断两个WantAgent实例是否相等，以此来判断是否是来自同一应用的相同操作。使用Promise异步回调。 |
| [getWantAgent](arkts-ability-wantagent-getwantagent-depr-f.md#getwantagent-1) | 创建WantAgent。创建失败返回的WantAgent为空值。使用callback异步回调。 |
| [getWantAgent](arkts-ability-wantagent-getwantagent-depr-f.md#getwantagent-2) | 创建WantAgent。创建失败返回的WantAgent为空值。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getWant](arkts-ability-wantagent-getwant-depr-f-sys.md#getwant-1) | 获取WantAgent中的Want(callback形式)。 |
| [getWant](arkts-ability-wantagent-getwant-depr-f-sys.md#getwant-2) | 获取WantAgent中的Want(Promise形式)。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CompleteData](arkts-ability-wantagent-completedata-depr-i.md) | 表示主动触发WantAgent返回的数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [WantAgentFlags](arkts-ability-wantagent-wantagentflags-depr-e.md) | 表示WantAgent行为控制标志，用于配置WantAgent的创建和触发行为。 |
| [OperationType](arkts-ability-wantagent-operationtype-depr-e.md) | 表示WantAgent支持的操作类型。 |

