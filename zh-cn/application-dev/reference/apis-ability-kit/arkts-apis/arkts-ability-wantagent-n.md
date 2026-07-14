# wantAgent

WantAgent模块封装了[Want](arkts-ability-want-c.md)对象，允许应用程序在未来的某个时间点触发WantAgent实例执行指定操作（如启动Ability、发送公共事件等）。

该模块提供了创建WantAgent实例、获取WantAgent实例所属应用的包名、获取WantAgent实例所属应用的UID、主动触发WantAgent实例、判断两个WantAgent实例是否相等等功能。WantAgent的一个典型应
用场景是通知处理。例如，当用户点击通知时，会触发WantAgent的[trigger](arkts-ability-trigger-f.md#trigger-1)接口，并拉起目标应用。具体使用请参考[Notification](../../../../notification/notification-with-wantagent.md)。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getBundleName](arkts-ability-getbundlename-f.md#getbundlename-1) | 获取WantAgent实例所属应用的包名，使用callback异步回调。 |
| [getBundleName](arkts-ability-getbundlename-f.md#getbundlename-2) | 获取WantAgent实例所属应用的包名。使用Promise异步回调。 |
| [getUid](arkts-ability-getuid-f.md#getuid-1) | 获取WantAgent实例所属应用的UID，使用callback异步回调。 |
| [getUid](arkts-ability-getuid-f.md#getuid-2) | 获取WantAgent实例所属应用的UID。使用Promise异步回调。 |
| [cancel](arkts-ability-cancel-f.md#cancel-1) | 取消WantAgent实例，使用callback异步回调。 |
| [cancel](arkts-ability-cancel-f.md#cancel-2) | 取消WantAgent实例。使用Promise异步回调。 |
| [trigger](arkts-ability-trigger-f.md#trigger-1) | 触发WantAgent实例，执行指定的操作（启动Ability、发送公共事件等）。使用callback异步回调。 |
| [equal](arkts-ability-equal-f.md#equal-1) | 判断两个WantAgent实例是否相等，使用callback异步回调，以此来确定是否是来自同一应用的相同操作。当两个WantAgent实例由当前用户下的同一应用使用相同的WantAgentInfo信息创建，并且实例未被cancel取消，这两个实例相等。在通知（携带WantAgent实例）场景，通知更新时会比较2个通知中的WantAgent实例，不相等时会把旧通知的WantAgent实例删除。 |
| [equal](arkts-ability-equal-f.md#equal-2) | 判断两个WantAgent实例是否相等，使用Promise异步回调，以此来确定是否是来自同一应用的相同操作。当两个WantAgent实例由当前用户下的同一应用使用相同的WantAgentInfo信息创建，并且实例未被cancel取消，这两个实例相等。在通知（携带WantAgent实例）场景，通知更新时会比较2个通知中的WantAgent实例，不相等时会把旧通知的WantAgent实例删除。 |
| [getWantAgent](arkts-ability-getwantagent-f.md#getwantagent-1) | 创建WantAgent，使用callback异步回调。创建成功返回WantAgent对象，创建失败返回空值。 |
| [getWantAgent](arkts-ability-getwantagent-f.md#getwantagent-2) | 创建WantAgent。使用Promise异步回调。创建成功返回WantAgent对象，创建失败返回空值。 |
| [getOperationType](arkts-ability-getoperationtype-f.md#getoperationtype-1) | 获取一个WantAgent实例的OperationType信息，使用callback异步回调。 |
| [getOperationType](arkts-ability-getoperationtype-f.md#getoperationtype-2) | 获取一个WantAgent实例的OperationType信息。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getWant](arkts-ability-getwant-f-sys.md#getwant-1) | 获取WantAgent对象的want。使用callback异步回调。 |
| [getWant](arkts-ability-getwant-f-sys.md#getwant-2) | 获取WantAgent对象的want。使用Promise异步回调。 |
| [triggerAsync](arkts-ability-triggerasync-f-sys.md#triggerasync-1) | 主动触发WantAgent实例，即按照WantAgent实例中已封装的指定操作和参数等信息执行。使用Promise异步回调。仅当入参agent为本地WantAgent实例时需要申请: ohos.permission.TRIGGER_LOCAL_WANTAGENT permission. |
| [setWantAgentMultithreading](arkts-ability-setwantagentmultithreading-f-sys.md#setwantagentmultithreading-1) | 开启或者关闭WantAgent多线程传递功能。 |
| [createLocalWantAgent](arkts-ability-createlocalwantagent-f-sys.md#createlocalwantagent-1) | 创建本地WantAgent实例。@link triggerAsync}接口说明。 |
| [isLocalWantAgent](arkts-ability-islocalwantagent-f-sys.md#islocalwantagent-1) | 判断WantAgent实例是否为本地实例。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CompleteData](arkts-ability-completedata-i.md) | 表示主动触发WantAgent返回的数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [WantAgentFlags](arkts-ability-wantagentflags-e.md) | 表示WantAgent行为控制标志，用于配置WantAgent的创建和触发行为。 |
| [OperationType](arkts-ability-operationtype-e.md) | 表示WantAgent支持的操作类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [OperationType](arkts-ability-operationtype-e-sys.md) | 表示WantAgent支持的操作类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [TriggerInfo](arkts-ability-triggerinfo-t.md) | TriggerInfo对象。 |
| [WantAgentInfo](arkts-ability-wantagentinfo-t.md) | WantAgentInfo对象。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [LocalWantAgentInfo](arkts-ability-localwantagentinfo-t-sys.md) | LocalWantAgentInfo对象。 |
<!--DelEnd-->

