# wantAgent

WantAgent模块封装了[Want](arkts-ability-want-c.md#Want)对象，允许应用程序在未来的某个时间点触发WantAgent实例执行指定操作（如启动Ability、发送公共事件等）。

该模块提供了创建WantAgent实例、获取WantAgent实例所属应用的包名、获取WantAgent实例所属应用的UID、主动触发WantAgent实例、判断两个WantAgent实例是否相等等功能。WantAgent的一个典型应
用场景是通知处理。例如，当用户点击通知时，会触发WantAgent的[trigger](arkts-ability-wantagent-trigger-f.md#trigger-1)接口，并拉起目标应用。具体使用请参考[Notification](../../../../notification/notification-with-wantagent.md)。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getBundleName](arkts-ability-wantagent-getbundlename-f.md#getBundleName-1) | 获取WantAgent实例所属应用的包名，使用callback异步回调。<br/> |
| [getBundleName](arkts-ability-wantagent-getbundlename-f.md#getBundleName-2) | 获取WantAgent实例所属应用的包名。使用Promise异步回调。<br/> |
| [getUid](arkts-ability-wantagent-getuid-f.md#getUid-1) | 获取WantAgent实例所属应用的UID，使用callback异步回调。<br/> |
| [getUid](arkts-ability-wantagent-getuid-f.md#getUid-2) | 获取WantAgent实例所属应用的UID。使用Promise异步回调。<br/> |
| <!--DelRow-->[getWant](arkts-ability-wantagent-getwant-f-sys.md#getWant-1) | 获取WantAgent对象的want。使用callback异步回调。<br/> |
| <!--DelRow-->[getWant](arkts-ability-wantagent-getwant-f-sys.md#getWant-2) | 获取WantAgent对象的want。使用Promise异步回调。<br/> |
| [cancel](arkts-ability-wantagent-cancel-f.md#cancel-1) | 取消WantAgent实例，使用callback异步回调。<br/> |
| [cancel](arkts-ability-wantagent-cancel-f.md#cancel-2) | 取消WantAgent实例。使用Promise异步回调。<br/> |
| [trigger](arkts-ability-wantagent-trigger-f.md#trigger-1) | 触发WantAgent实例，执行指定的操作（启动Ability、发送公共事件等）。使用callback异步回调。<br/> |
| <!--DelRow-->[triggerAsync](arkts-ability-wantagent-triggerasync-f-sys.md#triggerAsync-1) | 主动触发WantAgent实例，即按照WantAgent实例中已封装的指定操作和参数等信息执行。使用Promise异步回调。<br/>仅当入参agent为本地WantAgent实例时需要申请: ohos.permission.TRIGGER_LOCAL_WANTAGENT permission.<br/> |
| [equal](arkts-ability-wantagent-equal-f.md#equal-1) | 判断两个WantAgent实例是否相等，使用callback异步回调，以此来确定是否是来自同一应用的相同操作。<br/>当两个WantAgent实例由当前用户下的同一应用使用相同的WantAgentInfo信息创建，并且实例未被cancel取消，这两个实例相等。在通知（携带WantAgent实例）场景，通知更新时会比较2个通知中的<br/>WantAgent实例，不相等时会把旧通知的WantAgent实例删除。<br/> |
| [equal](arkts-ability-wantagent-equal-f.md#equal-2) | 判断两个WantAgent实例是否相等，使用Promise异步回调，以此来确定是否是来自同一应用的相同操作。<br/>当两个WantAgent实例由当前用户下的同一应用使用相同的WantAgentInfo信息创建，并且实例未被cancel取消，这两个实例相等。在通知（携带WantAgent实例）场景，通知更新时会比较2个通知中的<br/>WantAgent实例，不相等时会把旧通知的WantAgent实例删除。<br/> |
| [getWantAgent](arkts-ability-wantagent-getwantagent-f.md#getWantAgent-1) | 创建WantAgent，使用callback异步回调。创建成功返回WantAgent对象，创建失败返回空值。<br/> |
| [getWantAgent](arkts-ability-wantagent-getwantagent-f.md#getWantAgent-2) | 创建WantAgent。使用Promise异步回调。创建成功返回WantAgent对象，创建失败返回空值。<br/> |
| [getOperationType](arkts-ability-wantagent-getoperationtype-f.md#getOperationType-1) | 获取一个WantAgent实例的OperationType信息，使用callback异步回调。<br/> |
| [getOperationType](arkts-ability-wantagent-getoperationtype-f.md#getOperationType-2) | 获取一个WantAgent实例的OperationType信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[setWantAgentMultithreading](arkts-ability-wantagent-setwantagentmultithreading-f-sys.md#setWantAgentMultithreading-1) | 开启或者关闭WantAgent多线程传递功能。<br/> |
| <!--DelRow-->[createLocalWantAgent](arkts-ability-wantagent-createlocalwantagent-f-sys.md#createLocalWantAgent-1) | 创建本地WantAgent实例。<br/><br/>&gt; **说明：**<br/>&gt; 本接口创建的本地WantAgent实例仅存储于WantAgent客户端，不受WantAgent服务端管理。使用该本地实例时，需要校验实例，以保证安全性。<br/>&gt; 本地WantAgent实例创建后，触发方法参见[wantAgent.triggerAsync](arkts-ability-wantagent-triggerasync-f-sys.md#triggerAsync-1)接口说明。<br/> |
| <!--DelRow-->[isLocalWantAgent](arkts-ability-wantagent-islocalwantagent-f-sys.md#isLocalWantAgent-1) | 判断WantAgent实例是否为本地实例。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CompleteData](arkts-ability-wantagent-completedata-i.md) | 表示主动触发WantAgent返回的数据。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [WantAgentFlags](arkts-ability-wantagent-wantagentflags-e.md) | 表示WantAgent行为控制标志，用于配置WantAgent的创建和触发行为。<br/> |
| [OperationType](arkts-ability-wantagent-operationtype-e.md) | 表示WantAgent支持的操作类型。<br/> |
| <!--DelRow-->[OperationType](arkts-ability-wantagent-operationtype-e-sys.md) | 表示WantAgent支持的操作类型。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [TriggerInfo](arkts-ability-wantagent-triggerinfo-t.md) | TriggerInfo对象。<br/> |
| [WantAgentInfo](arkts-ability-wantagent-wantagentinfo-t.md) | WantAgentInfo对象。<br/> |
| <!--DelRow-->[LocalWantAgentInfo](arkts-ability-wantagent-localwantagentinfo-t-sys.md) | LocalWantAgentInfo对象。<br/> |

