# Support

系统公共事件是指由系统服务或系统应用发布的事件，订阅这些公共事件需要特定的权限、使用相应的值。

**起始版本：** 9

<!--Device-commonEventManager-export enum Support--><!--Device-commonEventManager-export enum Support-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_LOCKING

```TypeScript
COMMON_EVENT_USER_LOCKING = 'usual.event.USER_LOCKING'
```

表示用户即将被锁定的公共事件的动作。

锁定用户前将会触发事件通知服务发布该系统公共事件，事件携带系统账号ID。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_USER_LOCKING = 'usual.event.USER_LOCKING'--><!--Device-Support-COMMON_EVENT_USER_LOCKING = 'usual.event.USER_LOCKING'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_USER_LOCKED

```TypeScript
COMMON_EVENT_USER_LOCKED = 'usual.event.USER_LOCKED'
```

表示用户锁定完成的公共事件的动作。

完成锁定用户将会触发事件通知服务发布该系统公共事件，事件携带系统账号ID。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_USER_LOCKED = 'usual.event.USER_LOCKED'--><!--Device-Support-COMMON_EVENT_USER_LOCKED = 'usual.event.USER_LOCKED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_CREATED

```TypeScript
COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_CREATED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_CREATED'
```

表示创建系统账号子身份。

系统账号子身份创建成功时，会触发公共事件服务发布该事件，携带系统账号ID和子身份ID。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_CREATED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_CREATED'--><!--Device-Support-COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_CREATED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_CREATED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_DELETED

```TypeScript
COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_DELETED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_DELETED'
```

表示删除系统账号子身份。

系统账号子身份被删除时，触发公共事件服务发布该事件，携带系统账号ID和子身份ID。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_DELETED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_DELETED'--><!--Device-Support-COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_DELETED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_DELETED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHING

```TypeScript
COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHING = 'usual.event.OS_ACCOUNT_SUB_PROFILE_SWITCHING'
```

表示系统账号子身份开始切换。

系统账号子身份开始切换时，触发公共事件服务发布该事件，携带系统账号ID、切换到的子身份ID和切换前的子身份ID。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHING = 'usual.event.OS_ACCOUNT_SUB_PROFILE_SWITCHING'--><!--Device-Support-COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHING = 'usual.event.OS_ACCOUNT_SUB_PROFILE_SWITCHING'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHED

```TypeScript
COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_SWITCHED'
```

表示系统账号子身份切换完成。

系统账号子身份切换完成时，触发公共事件服务发布此事件，携带系统账号ID、切换到的子身份ID和切换前的子身份ID。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_SWITCHED'--><!--Device-Support-COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_SWITCHED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_BOUND

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_BOUND = 'usual.event.DISTRIBUTED_ACCOUNT_BOUND'
```

表示绑定分布式账号。

分布式账号绑定时，会触发公共事件服务发布该事件，携带系统账号ID和子身份ID。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_BOUND = 'usual.event.DISTRIBUTED_ACCOUNT_BOUND'--><!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_BOUND = 'usual.event.DISTRIBUTED_ACCOUNT_BOUND'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_UNBOUND

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_UNBOUND = 'usual.event.DISTRIBUTED_ACCOUNT_UNBOUND'
```

表示已解绑分布式账号。

分布式账号解绑时，会触发公共事件服务发布该事件，携带系统账号ID和子身份ID。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_UNBOUND = 'usual.event.DISTRIBUTED_ACCOUNT_UNBOUND'--><!--Device-Support-COMMON_EVENT_DISTRIBUTED_ACCOUNT_UNBOUND = 'usual.event.DISTRIBUTED_ACCOUNT_UNBOUND'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_CHARGE_TYPE_CHANGED

```TypeScript
COMMON_EVENT_CHARGE_TYPE_CHANGED = 'usual.event.CHARGE_TYPE_CHANGED'
```

表示系统充电类型改变的公共事件的动作。

当系统充电类型改变时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_CHARGE_TYPE_CHANGED = 'usual.event.CHARGE_TYPE_CHANGED'--><!--Device-Support-COMMON_EVENT_CHARGE_TYPE_CHANGED = 'usual.event.CHARGE_TYPE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_DEVICE_IDLE_EXEMPTION_LIST_UPDATED

```TypeScript
COMMON_EVENT_DEVICE_IDLE_EXEMPTION_LIST_UPDATED = 'usual.event.DEVICE_IDLE_EXEMPTION_LIST_UPDATED'
```

表示待机状态下解除资源使用限制的豁免名单出现变化，触发公共事件发布动作。

待机状态下后台应用程序CPU和网络访问被限制，系统应用可以申请解除资源使用限制，将会触发公共事件服务发布该系统公共事件。

资源包括应用网络访问、Timer使用、WorkScheduler任务使用等。

系统应用可以调用JS API接口申请解除资源使用限制。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_DEVICE_IDLE_EXEMPTION_LIST_UPDATED = 'usual.event.DEVICE_IDLE_EXEMPTION_LIST_UPDATED'--><!--Device-Support-COMMON_EVENT_DEVICE_IDLE_EXEMPTION_LIST_UPDATED = 'usual.event.DEVICE_IDLE_EXEMPTION_LIST_UPDATED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_DISK_VOLUME_STATE_CHANGE

```TypeScript
COMMON_EVENT_DISK_VOLUME_STATE_CHANGE = 'usual.event.data.DISK_VOLUME_STATE_CHANGE'
```

表示系统数据盘卷状态发生变化的公共事件。

当系统数据盘卷在格式化或修复等操作过程中状态发生变化（如操作开始、成功或失败）时，会发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_DISK_VOLUME_STATE_CHANGE = 'usual.event.data.DISK_VOLUME_STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_DISK_VOLUME_STATE_CHANGE = 'usual.event.data.DISK_VOLUME_STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_APP_FIRST_LAUNCH

```TypeScript
COMMON_EVENT_APP_FIRST_LAUNCH = 'usual.event.APP_FIRST_LAUNCH'
```

在应用安装后首次启动时，事件通知服务将触发并发布系统公共事件。

**模型约束：** 此接口仅可在Stage模型下使用。

要订阅此事件，您的应用必须具备ohos.permission.INSTALL_BUNDLE权限（该权限仅系统应用可申请）

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_APP_FIRST_LAUNCH = 'usual.event.APP_FIRST_LAUNCH'--><!--Device-Support-COMMON_EVENT_APP_FIRST_LAUNCH = 'usual.event.APP_FIRST_LAUNCH'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SMS_RECEIVE_COMPLETED

```TypeScript
COMMON_EVENT_SMS_RECEIVE_COMPLETED = 'usual.event.SMS_RECEIVE_COMPLETED'
```

提示短信接收完成。

在设备接收到短信时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.RECEIVE_SMS权限（该权限仅系统应用可申请）

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_SMS_RECEIVE_COMPLETED = 'usual.event.SMS_RECEIVE_COMPLETED'--><!--Device-Support-COMMON_EVENT_SMS_RECEIVE_COMPLETED = 'usual.event.SMS_RECEIVE_COMPLETED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SMS_EMERGENCY_CB_RECEIVE_COMPLETED

```TypeScript
COMMON_EVENT_SMS_EMERGENCY_CB_RECEIVE_COMPLETED = 'usual.event.SMS_EMERGENCY_CB_RECEIVE_COMPLETED'
```

提示紧急小区广播短信接收完成。

在设备接收到紧急小区广播短信时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.RECEIVE_SMS权限（该权限仅系统应用可申请）

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_SMS_EMERGENCY_CB_RECEIVE_COMPLETED = 'usual.event.SMS_EMERGENCY_CB_RECEIVE_COMPLETED'--><!--Device-Support-COMMON_EVENT_SMS_EMERGENCY_CB_RECEIVE_COMPLETED = 'usual.event.SMS_EMERGENCY_CB_RECEIVE_COMPLETED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SMS_CB_RECEIVE_COMPLETED

```TypeScript
COMMON_EVENT_SMS_CB_RECEIVE_COMPLETED = 'usual.event.SMS_CB_RECEIVE_COMPLETED'
```

提示小区广播短信接收完成。

在设备接收到小区广播短信时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.RECEIVE_SMS权限（该权限仅系统应用可申请）

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_SMS_CB_RECEIVE_COMPLETED = 'usual.event.SMS_CB_RECEIVE_COMPLETED'--><!--Device-Support-COMMON_EVENT_SMS_CB_RECEIVE_COMPLETED = 'usual.event.SMS_CB_RECEIVE_COMPLETED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_STK_COMMAND

```TypeScript
COMMON_EVENT_STK_COMMAND = 'usual.event.STK_COMMAND'
```

（预留事件，暂未支持）提示STK命令。

在发送STK命令时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_STK_COMMAND = 'usual.event.STK_COMMAND'--><!--Device-Support-COMMON_EVENT_STK_COMMAND = 'usual.event.STK_COMMAND'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_STK_SESSION_END

```TypeScript
COMMON_EVENT_STK_SESSION_END = 'usual.event.STK_SESSION_END'
```

（预留事件，暂未支持）提示STK会话结束。

在STK会话结束时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_STK_SESSION_END = 'usual.event.STK_SESSION_END'--><!--Device-Support-COMMON_EVENT_STK_SESSION_END = 'usual.event.STK_SESSION_END'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_STK_CARD_STATE_CHANGED

```TypeScript
COMMON_EVENT_STK_CARD_STATE_CHANGED = 'usual.event.STK_CARD_STATE_CHANGED'
```

（预留事件，暂未支持）提示STK卡状态已更新。

在STK卡状态更新时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_STK_CARD_STATE_CHANGED = 'usual.event.STK_CARD_STATE_CHANGED'--><!--Device-Support-COMMON_EVENT_STK_CARD_STATE_CHANGED = 'usual.event.STK_CARD_STATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_STK_ALPHA_IDENTIFIER

```TypeScript
COMMON_EVENT_STK_ALPHA_IDENTIFIER = 'usual.event.STK_ALPHA_IDENTIFIER'
```

（预留事件，暂未支持）提示STK ALPHA标识符。

在发送STK ALPHA标识符时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_STK_ALPHA_IDENTIFIER = 'usual.event.STK_ALPHA_IDENTIFIER'--><!--Device-Support-COMMON_EVENT_STK_ALPHA_IDENTIFIER = 'usual.event.STK_ALPHA_IDENTIFIER'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SMS_WAPPUSH_RECEIVE_COMPLETED

```TypeScript
COMMON_EVENT_SMS_WAPPUSH_RECEIVE_COMPLETED = 'usual.event.SMS_WAPPUSH_RECEIVE_COMPLETED'
```

（预留事件，暂未支持）提示服务信息短信接收完成。

在设备接收服务信息短信完成时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.RECEIVE_SMS权限（该权限仅系统应用可申请）

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_SMS_WAPPUSH_RECEIVE_COMPLETED = 'usual.event.SMS_WAPPUSH_RECEIVE_COMPLETED'--><!--Device-Support-COMMON_EVENT_SMS_WAPPUSH_RECEIVE_COMPLETED = 'usual.event.SMS_WAPPUSH_RECEIVE_COMPLETED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_OPERATOR_CONFIG_CHANGED

```TypeScript
COMMON_EVENT_OPERATOR_CONFIG_CHANGED = 'usual.event.OPERATOR_CONFIG_CHANGED'
```

提示运营商配置已更新。

在设备运营商配置更新时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_OPERATOR_CONFIG_CHANGED = 'usual.event.OPERATOR_CONFIG_CHANGED'--><!--Device-Support-COMMON_EVENT_OPERATOR_CONFIG_CHANGED = 'usual.event.OPERATOR_CONFIG_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SIM_CARD_DEFAULT_SMS_SUBSCRIPTION_CHANGED

```TypeScript
COMMON_EVENT_SIM_CARD_DEFAULT_SMS_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_SMS_SUBSCRIPTION_CHANGED'
```

提示SIM卡默认短信主卡已更新。

在设备SIM卡默认短信主卡更新时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_SIM_CARD_DEFAULT_SMS_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_SMS_SUBSCRIPTION_CHANGED'--><!--Device-Support-COMMON_EVENT_SIM_CARD_DEFAULT_SMS_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_SMS_SUBSCRIPTION_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SIM_CARD_DEFAULT_DATA_SUBSCRIPTION_CHANGED

```TypeScript
COMMON_EVENT_SIM_CARD_DEFAULT_DATA_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_DATA_SUBSCRIPTION_CHANGED'
```

提示SIM卡默认数据主卡已更新。

在设备SIM卡默认数据主卡更新时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_SIM_CARD_DEFAULT_DATA_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_DATA_SUBSCRIPTION_CHANGED'--><!--Device-Support-COMMON_EVENT_SIM_CARD_DEFAULT_DATA_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_DATA_SUBSCRIPTION_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SIM_CARD_DEFAULT_MAIN_SUBSCRIPTION_CHANGED

```TypeScript
COMMON_EVENT_SIM_CARD_DEFAULT_MAIN_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_MAIN_SUBSCRIPTION_CHANGED'
```

提示SIM卡默认主卡已更新。

在设备SIM卡默认主卡更新时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_SIM_CARD_DEFAULT_MAIN_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_MAIN_SUBSCRIPTION_CHANGED'--><!--Device-Support-COMMON_EVENT_SIM_CARD_DEFAULT_MAIN_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_MAIN_SUBSCRIPTION_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SET_PRIMARY_SLOT_STATUS

```TypeScript
COMMON_EVENT_SET_PRIMARY_SLOT_STATUS = 'usual.event.SET_PRIMARY_SLOT_STATUS'
```

提示设置SIM卡默认主卡的动作，其状态更新为执行中或已完成。

在设备上设置SIM卡默认主卡时，当执行状态发生变化（比如状态更新到执行中或已完成），将会触发事件通知服务发布该系统公共事件。

**起始版本：** 11

<!--Device-Support-COMMON_EVENT_SET_PRIMARY_SLOT_STATUS = 'usual.event.SET_PRIMARY_SLOT_STATUS'--><!--Device-Support-COMMON_EVENT_SET_PRIMARY_SLOT_STATUS = 'usual.event.SET_PRIMARY_SLOT_STATUS'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_PRIMARY_SLOT_ROAMING

```TypeScript
COMMON_EVENT_PRIMARY_SLOT_ROAMING = 'usual.event.PRIMARY_SLOT_ROAMING'
```

提示SIM卡默认主卡的漫游状态已更新。

在设备SIM卡默认主卡的漫游状态发生变化时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 11

<!--Device-Support-COMMON_EVENT_PRIMARY_SLOT_ROAMING = 'usual.event.PRIMARY_SLOT_ROAMING'--><!--Device-Support-COMMON_EVENT_PRIMARY_SLOT_ROAMING = 'usual.event.PRIMARY_SLOT_ROAMING'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SIM_CARD_DEFAULT_VOICE_SUBSCRIPTION_CHANGED

```TypeScript
COMMON_EVENT_SIM_CARD_DEFAULT_VOICE_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_VOICE_SUBSCRIPTION_CHANGED'
```

提示SIM卡默认语音主卡已更新。

在设备SIM卡默认语音主卡更新时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_SIM_CARD_DEFAULT_VOICE_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_VOICE_SUBSCRIPTION_CHANGED'--><!--Device-Support-COMMON_EVENT_SIM_CARD_DEFAULT_VOICE_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_VOICE_SUBSCRIPTION_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_CELLULAR_DATA_STATE_CHANGED

```TypeScript
COMMON_EVENT_CELLULAR_DATA_STATE_CHANGED = 'usual.event.CELLULAR_DATA_STATE_CHANGED'
```

提示蜂窝数据状态更新。

在设备蜂窝数据状态更新时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_CELLULAR_DATA_STATE_CHANGED = 'usual.event.CELLULAR_DATA_STATE_CHANGED'--><!--Device-Support-COMMON_EVENT_CELLULAR_DATA_STATE_CHANGED = 'usual.event.CELLULAR_DATA_STATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_INCOMING_CALL_MISSED

```TypeScript
COMMON_EVENT_INCOMING_CALL_MISSED = 'usual.event.INCOMING_CALL_MISSED'
```

提示未接来电。

在设备有未接来电时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.GET_TELEPHONY_STATE权限（该权限仅系统应用可申请）

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_INCOMING_CALL_MISSED = 'usual.event.INCOMING_CALL_MISSED'--><!--Device-Support-COMMON_EVENT_INCOMING_CALL_MISSED = 'usual.event.INCOMING_CALL_MISSED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_RADIO_STATE_CHANGE

```TypeScript
COMMON_EVENT_RADIO_STATE_CHANGE = 'usual.event.RADIO_STATE_CHANGE'
```

提示设备modem上下电状态变化。

在设备modem上下电状态变化时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_RADIO_STATE_CHANGE = 'usual.event.RADIO_STATE_CHANGE'--><!--Device-Support-COMMON_EVENT_RADIO_STATE_CHANGE = 'usual.event.RADIO_STATE_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_DOMAIN_ACCOUNT_STATUS_CHANGED

```TypeScript
COMMON_EVENT_DOMAIN_ACCOUNT_STATUS_CHANGED = 'usual.event.DOMAIN_ACCOUNT_STATUS_CHANGED'
```

表示域账号状态发生变化。

域账号认证、删除、令牌更新、令牌失效将会触发事件通知服务发布该系统公共事件，事件携带域账号名、域名、域账号状态等信息。

与这个公共事件相关的接口：removeOsAccount、DomainAccountManager.auth、updateAccountToken, 这些为系统API，具体参看[@ohos.account.osAccount](docroot://reference/js-apis-osAccount.md)。

要订阅此事件，您的应用必须具备ohos.permission.GET_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_DOMAIN_ACCOUNT_STATUS_CHANGED = 'usual.event.DOMAIN_ACCOUNT_STATUS_CHANGED'--><!--Device-Support-COMMON_EVENT_DOMAIN_ACCOUNT_STATUS_CHANGED = 'usual.event.DOMAIN_ACCOUNT_STATUS_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SPECIAL_CODE

```TypeScript
COMMON_EVENT_SPECIAL_CODE = 'common.event.SPECIAL_CODE'
```

提示暗码发送成功。

在设备上发送暗码成功时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_SPECIAL_CODE = 'common.event.SPECIAL_CODE'--><!--Device-Support-COMMON_EVENT_SPECIAL_CODE = 'common.event.SPECIAL_CODE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_AUDIO_QUALITY_CHANGE

```TypeScript
COMMON_EVENT_AUDIO_QUALITY_CHANGE = 'usual.event.AUDIO_QUALITY_CHANGE'
```

提示音频质量发生变化。

在设备音频质量发送变化时，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 10

<!--Device-Support-COMMON_EVENT_AUDIO_QUALITY_CHANGE = 'usual.event.AUDIO_QUALITY_CHANGE'--><!--Device-Support-COMMON_EVENT_AUDIO_QUALITY_CHANGE = 'usual.event.AUDIO_QUALITY_CHANGE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_PRIVACY_STATE_CHANGED

```TypeScript
COMMON_EVENT_PRIVACY_STATE_CHANGED = 'usual.event.PRIVACY_STATE_CHANGED'
```

表示隐私签署结果的公共事件。

隐私弹框场景下，用户点击同意，会发送此事件。

**起始版本：** 11

<!--Device-Support-COMMON_EVENT_PRIVACY_STATE_CHANGED = 'usual.event.PRIVACY_STATE_CHANGED'--><!--Device-Support-COMMON_EVENT_PRIVACY_STATE_CHANGED = 'usual.event.PRIVACY_STATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_PACKAGE_INSTALLATION_STARTED

```TypeScript
COMMON_EVENT_PACKAGE_INSTALLATION_STARTED = 'usual.event.PACKAGE_INSTALLATION_STARTED'
```

当一个包被验证时，由系统包验证者发送。

在设备上指定用户下开始安装应用程序，将会触发事件通知服务发布该系统公共事件。

**起始版本：** 12

<!--Device-Support-COMMON_EVENT_PACKAGE_INSTALLATION_STARTED = 'usual.event.PACKAGE_INSTALLATION_STARTED'--><!--Device-Support-COMMON_EVENT_PACKAGE_INSTALLATION_STARTED = 'usual.event.PACKAGE_INSTALLATION_STARTED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_DYNAMIC_ICON_CHANGED

```TypeScript
COMMON_EVENT_DYNAMIC_ICON_CHANGED = 'usual.event.DYNAMIC_ICON_CHANGED'
```

表示应用动态图标发生变化的公共事件。

在应用的动态图标发生变更时，会发送此公共事件。

**起始版本：** 12

<!--Device-Support-COMMON_EVENT_DYNAMIC_ICON_CHANGED = 'usual.event.DYNAMIC_ICON_CHANGED'--><!--Device-Support-COMMON_EVENT_DYNAMIC_ICON_CHANGED = 'usual.event.DYNAMIC_ICON_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_BUNDLE_RESOURCES_CHANGED

```TypeScript
COMMON_EVENT_BUNDLE_RESOURCES_CHANGED = 'usual.event.BUNDLE_RESOURCES_CHANGED'
```

表示包管理资源数据刷新的公共事件。

在切换语言、切换主题等场景，包管理资源数据刷新完成时，会发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.GET_BUNDLE_RESOURCES权限

**起始版本：** 15

<!--Device-Support-COMMON_EVENT_BUNDLE_RESOURCES_CHANGED = 'usual.event.BUNDLE_RESOURCES_CHANGED'--><!--Device-Support-COMMON_EVENT_BUNDLE_RESOURCES_CHANGED = 'usual.event.BUNDLE_RESOURCES_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_VPN_CONNECTION_STATUS_CHANGED

```TypeScript
COMMON_EVENT_VPN_CONNECTION_STATUS_CHANGED = 'usual.event.VPN_CONNECTION_STATUS_CHANGED'
```

表示VPN连接状态的公共事件。

当VPN连接或者断开时会发送此公共事件。

**起始版本：** 12

<!--Device-Support-COMMON_EVENT_VPN_CONNECTION_STATUS_CHANGED = 'usual.event.VPN_CONNECTION_STATUS_CHANGED'--><!--Device-Support-COMMON_EVENT_VPN_CONNECTION_STATUS_CHANGED = 'usual.event.VPN_CONNECTION_STATUS_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_RESTORE_START

```TypeScript
COMMON_EVENT_RESTORE_START = 'usual.event.RESTORE_START'
```

表示某个应用开始恢复的公共事件。

当数据迁移相关应用拉起备份恢复框架进行恢复任务，某个应用恢复开始时会发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.START_RESTORE_NOTIFICATION权限

**起始版本：** 13

<!--Device-Support-COMMON_EVENT_RESTORE_START = 'usual.event.RESTORE_START'--><!--Device-Support-COMMON_EVENT_RESTORE_START = 'usual.event.RESTORE_START'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_DEFAULT_APPLICATION_CHANGED

```TypeScript
COMMON_EVENT_DEFAULT_APPLICATION_CHANGED = 'usual.event.DEFAULT_APPLICATION_CHANGED'
```

表示文件默认打开应用发生变更的公共事件。

在文件默认打开应用发生变更时，会发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.CHANGE_DEFAULT_APPLICATION权限

**起始版本：** 19

<!--Device-Support-COMMON_EVENT_DEFAULT_APPLICATION_CHANGED = 'usual.event.DEFAULT_APPLICATION_CHANGED'--><!--Device-Support-COMMON_EVENT_DEFAULT_APPLICATION_CHANGED = 'usual.event.DEFAULT_APPLICATION_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SHORTCUT_CHANGED

```TypeScript
COMMON_EVENT_SHORTCUT_CHANGED = 'usual.event.SHORTCUT_CHANGED'
```

表示应用快捷方式发生变化的公共事件。

在应用快捷方式的更改设置完成时（例如调用shortcutManager模块的[setShortcutVisibleForSelf](docroot://apis-ability-kit/js-apis-shortcutManager.md#shortcutmanagersetshortcutvisibleforself)成功时），会发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.MANAGE_SHORTCUTS权限

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_SHORTCUT_CHANGED = 'usual.event.SHORTCUT_CHANGED'--><!--Device-Support-COMMON_EVENT_SHORTCUT_CHANGED = 'usual.event.SHORTCUT_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_CUSTOM_CONFIG_POLICY_UPDATED

```TypeScript
COMMON_EVENT_CUSTOM_CONFIG_POLICY_UPDATED = 'usual.event.CUSTOM_CONFIG_POLICY_UPDATED'
```

表示设备的配置目录层级与系统参数发生变化的公共事件。

在系统对设备的归属区域和漫游区域识别完成后，会对设备的配置目录层级与系统参数进行刷新，刷新完成后会发送此公共事件。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_CUSTOM_CONFIG_POLICY_UPDATED = 'usual.event.CUSTOM_CONFIG_POLICY_UPDATED'--><!--Device-Support-COMMON_EVENT_CUSTOM_CONFIG_POLICY_UPDATED = 'usual.event.CUSTOM_CONFIG_POLICY_UPDATED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_CUSTOM_ROAMING_REGION_UPDATED

```TypeScript
COMMON_EVENT_CUSTOM_ROAMING_REGION_UPDATED = 'usual.event.CUSTOM_ROAMING_REGION_UPDATED'
```

表示设备漫游区域发生变化的公共事件。

在设备注入网络、驻留网络、GPS定位等属性变化时，系统服务会进行漫游区域识别。当识别到漫游区域发生变化，则会更新设备漫游区域参数，在更新完成后会发送此公共事件。

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_CUSTOM_ROAMING_REGION_UPDATED = 'usual.event.CUSTOM_ROAMING_REGION_UPDATED'--><!--Device-Support-COMMON_EVENT_CUSTOM_ROAMING_REGION_UPDATED = 'usual.event.CUSTOM_ROAMING_REGION_UPDATED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SCREEN_SHARE

```TypeScript
COMMON_EVENT_SCREEN_SHARE = 'usual.event.SCREEN_SHARE'
```

表示系统中发生了屏幕共享事件。

这是一个受保护的公共事件，只能由系统发送。

要订阅此事件，您的应用必须具备ohos.permission.RECEIVE_SMS权限（该权限仅系统应用可申请）

**起始版本：** 20

<!--Device-Support-COMMON_EVENT_SCREEN_SHARE = 'usual.event.SCREEN_SHARE'--><!--Device-Support-COMMON_EVENT_SCREEN_SHARE = 'usual.event.SCREEN_SHARE'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_RESTORE_END

```TypeScript
COMMON_EVENT_RESTORE_END = 'usual.event.RESTORE_END'
```

表示某个应用结束恢复的公共事件。

当数据迁移相关应用拉起备份恢复框架进行恢复任务，某个应用恢复结束后会发送此公共事件。

要订阅此事件，您的应用必须具备ohos.permission.RESTORE_END_NOTIFICATION权限（该权限仅系统应用可申请）

**起始版本：** 23

<!--Device-Support-COMMON_EVENT_RESTORE_END = 'usual.event.RESTORE_END'--><!--Device-Support-COMMON_EVENT_RESTORE_END = 'usual.event.RESTORE_END'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_CLOUD_DISK_STATE_CHANGED

```TypeScript
COMMON_EVENT_CLOUD_DISK_STATE_CHANGED = 'usual.event.CLOUD_DISK_STATE_CHANGED'
```

提示云盘同步根已更新。

在同步根更新完成时，将会触发事件通知服务发布该系统公共事件。

要订阅此事件，您的应用必须具备ohos.permission.ACCESS_CLOUD_DISK_INFO权限（该权限仅系统应用可申请）

**起始版本：** 21

<!--Device-Support-COMMON_EVENT_CLOUD_DISK_STATE_CHANGED = 'usual.event.CLOUD_DISK_STATE_CHANGED'--><!--Device-Support-COMMON_EVENT_CLOUD_DISK_STATE_CHANGED = 'usual.event.CLOUD_DISK_STATE_CHANGED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SCREEN_LOCK_EXITING

```TypeScript
COMMON_EVENT_SCREEN_LOCK_EXITING = 'usual.event.SCREEN_LOCK_EXITING'
```

表示锁屏退出的事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_SCREEN_LOCK_EXITING = 'usual.event.SCREEN_LOCK_EXITING'--><!--Device-Support-COMMON_EVENT_SCREEN_LOCK_EXITING = 'usual.event.SCREEN_LOCK_EXITING'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SANDBOX_BUNDLE_ADDED

```TypeScript
COMMON_EVENT_SANDBOX_BUNDLE_ADDED = 'usual.event.SANDBOX_BUNDLE_ADDED'
```

表示设备上已安装新的沙箱应用的公共事件.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_SANDBOX_BUNDLE_ADDED = 'usual.event.SANDBOX_BUNDLE_ADDED'--><!--Device-Support-COMMON_EVENT_SANDBOX_BUNDLE_ADDED = 'usual.event.SANDBOX_BUNDLE_ADDED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

## COMMON_EVENT_SANDBOX_BUNDLE_REMOVED

```TypeScript
COMMON_EVENT_SANDBOX_BUNDLE_REMOVED = 'usual.event.SANDBOX_BUNDLE_REMOVED'
```

表示设备上安装的沙箱应用被卸载的公共事件.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Support-COMMON_EVENT_SANDBOX_BUNDLE_REMOVED = 'usual.event.SANDBOX_BUNDLE_REMOVED'--><!--Device-Support-COMMON_EVENT_SANDBOX_BUNDLE_REMOVED = 'usual.event.SANDBOX_BUNDLE_REMOVED'-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

**系统接口：** 此接口为系统接口。

