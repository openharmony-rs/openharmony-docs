# @ohos.ability.featureAbility

FeatureAbility模块提供与用户进行交互的Ability的能力，包括启动新的Ability、停止Ability、获取dataAbilityHelper对象、获取当前Ability对应的窗口，连接断连Service等。

**起始版本：** 6

<!--Device-unnamed-declare namespace featureAbility--><!--Device-unnamed-declare namespace featureAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## 导入模块

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [acquireDataAbilityHelper](arkts-ability-featureability-acquiredataabilityhelper-f.md#acquiredataabilityhelper-1) | 获取dataAbilityHelper对象。 |
| [connectAbility](arkts-ability-featureability-connectability-f.md#connectability-1) | 将当前Ability与指定的ServiceAbility进行连接。 |
| [disconnectAbility](arkts-ability-featureability-disconnectability-f.md#disconnectability-1) | 断开与指定ServiceAbility的连接。使用callback异步回调。 |
| [disconnectAbility](arkts-ability-featureability-disconnectability-f.md#disconnectability-2) | 断开与指定ServiceAbility的连接。使用Promise异步回调。 |
| [getContext](arkts-ability-featureability-getcontext-f.md#getcontext-1) | 获取应用上下文。 |
| [getWant](arkts-ability-featureability-getwant-f.md#getwant-1) | 获取要拉起的Ability对应的Want。使用callback异步回调。 |
| [getWant](arkts-ability-featureability-getwant-f.md#getwant-2) | 获取要拉起的Ability对应的Want。使用Promise异步回调。 |
| [getWindow](arkts-ability-featureability-getwindow-f.md#getwindow-1) | 获取当前Ability对应的窗口。使用callback异步回调。 |
| [getWindow](arkts-ability-featureability-getwindow-f.md#getwindow-2) | 获取当前Ability对应的窗口。使用Promise异步回调。 |
| [hasWindowFocus](arkts-ability-featureability-haswindowfocus-f.md#haswindowfocus-1) | 检查Ability的主窗口是否具有窗口焦点。使用callback异步回调。 |
| [hasWindowFocus](arkts-ability-featureability-haswindowfocus-f.md#haswindowfocus-2) | 检查Ability的主窗口是否具有窗口焦点。使用Promise异步回调。 |
| [startAbility](arkts-ability-featureability-startability-f.md#startability-1) | 启动新的Ability。使用callback异步回调。 |
| [startAbility](arkts-ability-featureability-startability-f.md#startability-2) | 启动新的Ability。使用Promise异步回调。 |
| [startAbilityForResult](arkts-ability-featureability-startabilityforresult-f.md#startabilityforresult-1) | 启动一个Ability。使用callback异步回调。启动Ability后，存在如下几种情况：- 正常情况下可通过调用[terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult-1)接口使之终止并且返回结果给调用方。 - 异常情况下比如杀死Ability会返回异常信息给调用方, 异常信息中resultCode为-1。 - 如果被启动的Ability模式是单实例模式, 不同应用多次调用该接口启动这个Ability，当这个Ability调用[terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult-1)接口使之终止时，只将正常结果返回给最后一个调用方, 其它调用方返回异常信息, 异常信息中resultCode为-1。 |
| [startAbilityForResult](arkts-ability-featureability-startabilityforresult-f.md#startabilityforresult-2) | 启动一个Ability。使用Promise异步回调。启动Ability后，存在如下几种情况：- 正常情况下可通过调用[terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult-1)接口使之终止并且返回结果给调用方。 - 异常情况下比如杀死Ability会返回异常信息给调用方, 异常信息中resultCode为-1。 - 如果被启动的Ability模式是单实例模式, 不同应用多次调用该接口启动这个Ability，当这个Ability调用[terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult-1)接口使之终止时，只将正常结果返回给最后一个调用方, 其它调用方返回异常信息, 异常信息中resultCode为-1。 |
| [terminateSelf](arkts-ability-featureability-terminateself-f.md#terminateself-1) | 停止当前的Ability。使用callback异步回调。 |
| [terminateSelf](arkts-ability-featureability-terminateself-f.md#terminateself-2) | 停止当前的Ability。使用Promise异步回调。 |
| [terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult-1) | 停止当前的Ability。使用callback异步回调。如果该Ability是通过调用[startAbilityForResult](arkts-ability-featureability-startabilityforresult-f.md#startabilityforresult-1)接口被拉起的，调用terminateSelfWithResult接口时会将结果返回给调用者，如果该Ability不是通过调用[startAbilityForResult](arkts-ability-featureability-startabilityforresult-f.md#startabilityforresult-1)接口被拉起的，调用terminateSelfWithResult接口时不会有结果返回给调用者。 |
| [terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult-2) | 停止当前的Ability。使用Promise异步回调。如果该Ability是通过调用[startAbilityForResult](arkts-ability-featureability-startabilityforresult-f.md#startabilityforresult-1)接口被拉起的，调用terminateSelfWithResult接口时会将结果返回给调用者，如果该Ability不是通过调用[startAbilityForResult](arkts-ability-featureability-startabilityforresult-f.md#startabilityforresult-1)接口被拉起的，调用terminateSelfWithResult接口时不会有结果返回给调用者。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AbilityStartSetting](arkts-ability-featureability-abilitystartsetting-e.md) | 表示当前Ability对应的窗口属性，abilityStartSetting属性是一个定义为[key: string]: any的对象，key对应设定类型为：AbilityStartSetting枚举类型，value对应设定类型为：AbilityWindowConfiguration枚举类型。使用时通过featureAbility.AbilityStartSetting获取。 |
| [AbilityWindowConfiguration](arkts-ability-featureability-abilitywindowconfiguration-e.md) | 表示当前Ability对应的窗口配置项，使用时通过featureAbility.AbilityWindowConfiguration获取。 |
| [DataAbilityOperationType](arkts-ability-featureability-dataabilityoperationtype-e.md) | 表示数据的操作类型。DataAbility批量操作数据时可以通过该枚举值指定操作类型。 |
| [ErrorCode](arkts-ability-featureability-errorcode-e.md) | 定义启动Ability时返回的错误码。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AppVersionInfo](arkts-ability-featureability-appversioninfo-t.md) | 应用版本信息。 |
| [Context](arkts-ability-featureability-context-t.md) | Context模块。 |
| [ProcessInfo](arkts-ability-featureability-processinfo-t.md) | 进程信息。 |

