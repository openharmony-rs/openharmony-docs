# @ohos.app.ability.abilityManager

AbilityManager模块提供获取、新增、修改Ability相关信息和运行状态信息的能力。

**起始版本：** 23

<!--Device-unnamed-declare namespace abilityManager--><!--Device-unnamed-declare namespace abilityManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAbilityRunningInfos](arkts-ability-abilitymanager-getabilityrunninginfos-f.md) | 获取UIAbility运行时的相关信息。使用Promise异步回调。 |
| [isEmbeddedUIExtensionSupported](arkts-ability-abilitymanager-isembeddeduiextensionsupported-f.md) | 开发者通过调用该接口判断[EmbeddedUIExtensionAbility](../../../application-models/embeddeduiextensionability.md)是否可以在当前设备上使用。 |
| [restartSelfAtomicService](arkts-ability-abilitymanager-restartselfatomicservice-f.md) | 重启当前原子化服务。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [acquireShareData](arkts-ability-abilitymanager-acquiresharedata-f-sys.md) | 系统弹框通过该接口发起原子化服务分享，触发目标UIAbility的 [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare)回调并返回分享数据。使用 callback异步回调。 |
| [acquireShareData](arkts-ability-abilitymanager-acquiresharedata-f-sys.md) | 系统弹框通过该接口发起原子化服务分享，调用到目标UIAbility的onShare，返回分享数据。使用callback异步回调。 |
| [acquireShareData](arkts-ability-abilitymanager-acquiresharedata-f-sys.md) | 系统弹框通过该接口发起原子化服务分享，触发目标UIAbility的 [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare)回调并返回分享数据。使用 Promise异步回调。 |
| [acquireShareData](arkts-ability-abilitymanager-acquiresharedata-f-sys.md) | 系统弹框通过该接口发起原子化服务分享，调用到目标UIAbility的onShare，返回分享数据。使用Promise异步回调。 |
| [clearPreloadedUIExtensionAbilities](arkts-ability-abilitymanager-clearpreloadeduiextensionabilities-f-sys.md) | 清除当前进程中所有已经预加载的[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)实例。使用Promise异步回调。 |
| [clearPreloadedUIExtensionAbility](arkts-ability-abilitymanager-clearpreloadeduiextensionability-f-sys.md) | 清除指定的[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)实例。使用Promise异步回调。 |
| [getAbilityRunningInfos](arkts-ability-abilitymanager-getabilityrunninginfos-f-sys.md) | 获取UIAbility运行相关信息。使用callback异步回调。 |
| [getExtensionRunningInfos](arkts-ability-abilitymanager-getextensionrunninginfos-f-sys.md) | 获取关于运行扩展能力的信息。使用Promise异步回调。 |
| [getExtensionRunningInfos](arkts-ability-abilitymanager-getextensionrunninginfos-f-sys.md) | 获取关于运行扩展能力的信息。使用callback异步回调。 |
| [getForegroundUIAbilities](arkts-ability-abilitymanager-getforegrounduiabilities-f-sys.md) | 获取前台正在运行的应用Ability的信息。使用callback异步回调。 |
| [getForegroundUIAbilities](arkts-ability-abilitymanager-getforegrounduiabilities-f-sys.md) | 获取前台正在运行的应用Ability的信息。使用Promise异步回调。 |
| [getTopAbility](arkts-ability-abilitymanager-gettopability-f-sys.md) | 获取窗口焦点所在的Ability。使用Promise异步回调。 |
| [getTopAbility](arkts-ability-abilitymanager-gettopability-f-sys.md) | 获取窗口焦点所在的Ability。使用callback异步回调。 |
| [isEmbeddedOpenAllowed](arkts-ability-abilitymanager-isembeddedopenallowed-f-sys.md) | 判断是否允许嵌入式拉起[EmbeddableUIAbility](arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md)。使用Promise异步回调。 |
| [notifyDebugAssertResult](arkts-ability-abilitymanager-notifydebugassertresult-f-sys.md) | 将断言调试结果通知应用程序。使用Promise异步回调。 |
| [notifySaveAsResult](arkts-ability-abilitymanager-notifysaveasresult-f-sys.md) | 该接口仅供[DLP](../../apis-data-protection-kit/arkts-apis/arkts-dlppermission.md)（Data Loss Prevention, 数据丢失防护）管理应用使用，其他应用禁止使用，DLP管理应用通过该接口通知沙箱应用 另存为结果。使用callback异步回调。 |
| [notifySaveAsResult](arkts-ability-abilitymanager-notifysaveasresult-f-sys.md) | 该接口仅供[DLP](../../apis-data-protection-kit/arkts-apis/arkts-dlppermission.md)（Data Loss Prevention, 数据丢失防护）管理应用使用，其他应用禁止使用，DLP管理应用通过该接口通知沙箱应用 另存为结果。使用Promise异步回调。 |
| [offAbilityForegroundState](arkts-ability-abilitymanager-offabilityforegroundstate-f-sys.md) | 取消注册Ability启动和退出的观测器。 |
| [offPreloadedUIExtensionAbilityDestroyed](arkts-ability-abilitymanager-offpreloadeduiextensionabilitydestroyed-f-sys.md) | 注销当前进程中预加载的[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)实例的销毁监听。 |
| [offPreloadedUIExtensionAbilityLoaded](arkts-ability-abilitymanager-offpreloadeduiextensionabilityloaded-f-sys.md) | 注销当前进程中预加载的[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)实例的加载监听。 |
| [off_abilityForegroundState](arkts-ability-abilitymanager-offabilityforegroundstate-f-sys.md) | 取消注册Ability启动和退出的观测器。 |
| [onAbilityForegroundState](arkts-ability-abilitymanager-onabilityforegroundstate-f-sys.md) | 注册Ability的启动和退出的观测器。 |
| [onPreloadedUIExtensionAbilityDestroyed](arkts-ability-abilitymanager-onpreloadeduiextensionabilitydestroyed-f-sys.md) | 监听当前进程中预加载的[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)实例的销毁事件。 |
| [onPreloadedUIExtensionAbilityLoaded](arkts-ability-abilitymanager-onpreloadeduiextensionabilityloaded-f-sys.md) | 监听当前进程中预加载的[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)实例的加载事件。 |
| [on_abilityForegroundState](arkts-ability-abilitymanager-onabilityforegroundstate-f-sys.md) | 注册Ability的启动和退出的观测器。 |
| [preloadUIExtensionAbility](arkts-ability-abilitymanager-preloaduiextensionability-f-sys.md) | 预加载指定的[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)并返回预加载UIExtensionAbility实例 的ID。使用Promise异步回调。 |
| [queryAtomicServiceStartupRule](arkts-ability-abilitymanager-queryatomicservicestartuprule-f-sys.md) | 查询嵌入式拉起[EmbeddableUIAbility](arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md)的规则。使用Promise异步回调。 该接口仅在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。 |
| [setResidentProcessEnabled](arkts-ability-abilitymanager-setresidentprocessenabled-f-sys.md) | 常驻进程支持按需启停。 |
| [updateConfiguration](arkts-ability-abilitymanager-updateconfiguration-f-sys.md) | 通过传入修改的配置项来更新配置。使用callback异步回调。 |
| [updateConfiguration](arkts-ability-abilitymanager-updateconfiguration-f-sys.md) | 通过修改配置来更新配置。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceStartupRule](arkts-ability-abilitymanager-atomicservicestartuprule-i-sys.md) | 嵌入式拉起原子化服务的规则。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AbilityState](arkts-ability-abilitymanager-abilitystate-e.md) | Ability的状态，该类型为枚举，可配合[AbilityRunningInfo](arkts-ability-abilityrunninginfo-i.md)返回Ability的状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [UserStatus](arkts-ability-abilitymanager-userstatus-e-sys.md) | 用户操作的断言调试结果，该类型为枚举。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityRunningInfo](arkts-ability-abilitymanager-abilityrunninginfo-t.md) | AbilityRunningInfo二级模块。 |
| [AbilityStateData](arkts-ability-abilitymanager-abilitystatedata-t.md) | AbilityStateData二级模块。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AbilityForegroundStateObserver](arkts-ability-abilitymanager-abilityforegroundstateobserver-t-sys.md) | AbilityForegroundStateObserver二级模块。 |
| [ExtensionRunningInfo](arkts-ability-abilitymanager-extensionrunninginfo-t-sys.md) | ExtensionRunningInfo二级模块。 |
| [PreloadedUIExtensionAbilityDestroyedFn](arkts-ability-abilitymanager-preloadeduiextensionabilitydestroyedfn-t-sys.md) | 预加载[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)被销毁时的回调函数类型。 |
| [PreloadedUIExtensionAbilityLoadedFn](arkts-ability-abilitymanager-preloadeduiextensionabilityloadedfn-t-sys.md) | 预加载[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)被加载时的回调函数类型。 |
<!--DelEnd-->

