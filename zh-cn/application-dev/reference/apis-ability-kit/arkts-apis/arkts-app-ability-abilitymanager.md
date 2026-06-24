# @ohos.app.ability.abilityManager

AbilityManager模块提供获取、新增、修改Ability相关信息和运行状态信息的能力。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[acquireShareData](arkts-ability-abilitymanager-acquiresharedata-f-sys.md#acquireShareData-1) | 系统弹框通过该接口发起原子化服务分享，触发目标UIAbility的<br/>[onShare](@ohos.app.ability.UIAbility:UIAbility.onShare(wantParam: Record&lt;string, Object&gt;))回调并返回分享数据。使用<br/>callback异步回调。<br/> |
| <!--DelRow-->[acquireShareData](arkts-ability-abilitymanager-acquiresharedata-f-sys.md#acquireShareData-2) | 系统弹框通过该接口发起原子化服务分享，触发目标UIAbility的<br/>[onShare](@ohos.app.ability.UIAbility:UIAbility.onShare(wantParam: Record&lt;string, Object&gt;))回调并返回分享数据。使用<br/>Promise异步回调。<br/> |
| <!--DelRow-->[clearPreloadedUIExtensionAbilities](arkts-ability-abilitymanager-clearpreloadeduiextensionabilities-f-sys.md#clearPreloadedUIExtensionAbilities-1) | 清除当前进程中所有已经预加载的[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)实例。使用Promise异步回调。<br/> |
| <!--DelRow-->[clearPreloadedUIExtensionAbility](arkts-ability-abilitymanager-clearpreloadeduiextensionability-f-sys.md#clearPreloadedUIExtensionAbility-1) | 清除指定的[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)实例。使用Promise异步回调。<br/> |
| [getAbilityRunningInfos](arkts-ability-abilitymanager-getabilityrunninginfos-f.md#getAbilityRunningInfos-1) | 获取UIAbility运行时的相关信息。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 如果应用申请了ohos.permission.GET_RUNNING_INFO权限，可以获取所有应用UIAbility的运行信息，否则只能获取当前应用UIAbility的运行信息。<br/> |
| <!--DelRow-->[getAbilityRunningInfos](arkts-ability-abilitymanager-getabilityrunninginfos-f-sys.md#getAbilityRunningInfos-2) | 获取UIAbility运行相关信息。使用callback异步回调。<br/> |
| <!--DelRow-->[getExtensionRunningInfos](arkts-ability-abilitymanager-getextensionrunninginfos-f-sys.md#getExtensionRunningInfos-1) | 获取关于运行扩展能力的信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[getExtensionRunningInfos](arkts-ability-abilitymanager-getextensionrunninginfos-f-sys.md#getExtensionRunningInfos-2) | 获取关于运行扩展能力的信息。使用callback异步回调。<br/> |
| <!--DelRow-->[getForegroundUIAbilities](arkts-ability-abilitymanager-getforegrounduiabilities-f-sys.md#getForegroundUIAbilities-1) | 获取前台正在运行的应用Ability的信息。使用callback异步回调。<br/> |
| <!--DelRow-->[getForegroundUIAbilities](arkts-ability-abilitymanager-getforegrounduiabilities-f-sys.md#getForegroundUIAbilities-2) | 获取前台正在运行的应用Ability的信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[getTopAbility](arkts-ability-abilitymanager-gettopability-f-sys.md#getTopAbility-1) | 获取窗口焦点所在的Ability。使用Promise异步回调。<br/> |
| <!--DelRow-->[getTopAbility](arkts-ability-abilitymanager-gettopability-f-sys.md#getTopAbility-2) | 获取窗口焦点所在的Ability。使用callback异步回调。<br/> |
| <!--DelRow-->[isEmbeddedOpenAllowed](arkts-ability-abilitymanager-isembeddedopenallowed-f-sys.md#isEmbeddedOpenAllowed-1) | 判断是否允许嵌入式拉起[EmbeddableUIAbility](arkts-ability-embeddableuiability-c.md#EmbeddableUIAbility)。使用Promise异步回调。<br/> |
| [isEmbeddedUIExtensionSupported](arkts-ability-abilitymanager-isembeddeduiextensionsupported-f.md#isEmbeddedUIExtensionSupported-1) | 开发者通过调用该接口判断[EmbeddedUIExtensionAbility](../../../../application-models/embeddeduiextensionability.md)是否可以在当前设备上使用。<br/> |
| <!--DelRow-->[notifyDebugAssertResult](arkts-ability-abilitymanager-notifydebugassertresult-f-sys.md#notifyDebugAssertResult-1) | 将断言调试结果通知应用程序。使用Promise异步回调。<br/> |
| <!--DelRow-->[notifySaveAsResult](arkts-ability-abilitymanager-notifysaveasresult-f-sys.md#notifySaveAsResult-1) | 该接口仅供[DLP](../../apis-data-protection-kit/arkts-apis/arkts-dlppermission.md#dlpPermission)（Data Loss Prevention, 数据丢失防护）管理应用使用，其他应用禁止使用，DLP管理应用通过该接口通知沙箱应用<br/>另存为结果。使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 10开始支持，从API version 24开始废弃。<br/> |
| <!--DelRow-->[notifySaveAsResult](arkts-ability-abilitymanager-notifysaveasresult-f-sys.md#notifySaveAsResult-2) | 该接口仅供[DLP](../../apis-data-protection-kit/arkts-apis/arkts-dlppermission.md#dlpPermission)（Data Loss Prevention, 数据丢失防护）管理应用使用，其他应用禁止使用，DLP管理应用通过该接口通知沙箱应用<br/>另存为结果。使用Promise异步回调。<br/> |
| <!--DelRow-->[off](arkts-ability-abilitymanager-off-f-sys.md#off-1) | 取消注册Ability启动和退出的观测器。<br/> |
| <!--DelRow-->[offPreloadedUIExtensionAbilityDestroyed](arkts-ability-abilitymanager-offpreloadeduiextensionabilitydestroyed-f-sys.md#offPreloadedUIExtensionAbilityDestroyed-1) | 注销当前进程中预加载的[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)实例的销毁监听。<br/> |
| <!--DelRow-->[offPreloadedUIExtensionAbilityLoaded](arkts-ability-abilitymanager-offpreloadeduiextensionabilityloaded-f-sys.md#offPreloadedUIExtensionAbilityLoaded-1) | 注销当前进程中预加载的[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)实例的加载监听。<br/> |
| <!--DelRow-->[on](arkts-ability-abilitymanager-on-f-sys.md#on-1) | 注册Ability的启动和退出的观测器。<br/> |
| <!--DelRow-->[onPreloadedUIExtensionAbilityDestroyed](arkts-ability-abilitymanager-onpreloadeduiextensionabilitydestroyed-f-sys.md#onPreloadedUIExtensionAbilityDestroyed-1) | 监听当前进程中预加载的[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)实例的销毁事件。<br/> |
| <!--DelRow-->[onPreloadedUIExtensionAbilityLoaded](arkts-ability-abilitymanager-onpreloadeduiextensionabilityloaded-f-sys.md#onPreloadedUIExtensionAbilityLoaded-1) | 监听当前进程中预加载的[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)实例的加载事件。<br/> |
| <!--DelRow-->[preloadUIExtensionAbility](arkts-ability-abilitymanager-preloaduiextensionability-f-sys.md#preloadUIExtensionAbility-1) | 预加载指定的[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)并返回预加载UIExtensionAbility实例<br/>的ID。使用Promise异步回调。<br/> |
| <!--DelRow-->[queryAtomicServiceStartupRule](arkts-ability-abilitymanager-queryatomicservicestartuprule-f-sys.md#queryAtomicServiceStartupRule-1) | 查询嵌入式拉起[EmbeddableUIAbility](arkts-ability-embeddableuiability-c.md#EmbeddableUIAbility)的规则。使用Promise异步回调。<br/>该接口仅在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。<br/> |
| [restartSelfAtomicService](arkts-ability-abilitymanager-restartselfatomicservice-f.md#restartSelfAtomicService-1) | 重启当前原子化服务。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 当前仅支持以独立窗口方式拉起原子化服务。<br/>&gt;<br/>&gt; - 在调用本接口成功后的3秒内，再次调用本接口、<br/>&gt; [ApplicationContext.restartApp()](arkts-ability-applicationcontext-c.md#restartApp-1)或<br/>&gt; [UIAbilityContext.restartApp()](arkts-ability-uiabilitycontext-c.md#restartApp-1)接口中的任一接口，系统将返回错误码1<br/>&gt; 6000064。<br/> |
| <!--DelRow-->[setResidentProcessEnabled](arkts-ability-abilitymanager-setresidentprocessenabled-f-sys.md#setResidentProcessEnabled-1) | 常驻进程支持按需启停。<br/> |
| <!--DelRow-->[updateConfiguration](arkts-ability-abilitymanager-updateconfiguration-f-sys.md#updateConfiguration-1) | 通过传入修改的配置项来更新配置。使用callback异步回调。<br/> |
| <!--DelRow-->[updateConfiguration](arkts-ability-abilitymanager-updateconfiguration-f-sys.md#updateConfiguration-2) | 通过修改配置来更新配置。使用Promise异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[AtomicServiceStartupRule](arkts-ability-abilitymanager-atomicservicestartuprule-i-sys.md) | 嵌入式拉起原子化服务的规则。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AbilityState](arkts-ability-abilitymanager-abilitystate-e.md) | Ability的状态，该类型为枚举，可配合[AbilityRunningInfo](arkts-ability-abilityrunninginfo-i.md#AbilityRunningInfo)返回Ability的状态。<br/> |
| <!--DelRow-->[UserStatus](arkts-ability-abilitymanager-userstatus-e-sys.md) | 用户操作的断言调试结果，该类型为枚举。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[AbilityForegroundStateObserver](arkts-ability-abilitymanager-abilityforegroundstateobserver-t-sys.md) | AbilityForegroundStateObserver二级模块。<br/> |
| [AbilityRunningInfo](arkts-ability-abilitymanager-abilityrunninginfo-t.md) | AbilityRunningInfo二级模块。<br/> |
| [AbilityStateData](arkts-ability-abilitymanager-abilitystatedata-t.md) | AbilityStateData二级模块。<br/> |
| <!--DelRow-->[ExtensionRunningInfo](arkts-ability-abilitymanager-extensionrunninginfo-t-sys.md) | ExtensionRunningInfo二级模块。<br/> |
| <!--DelRow-->[PreloadedUIExtensionAbilityDestroyedFn](arkts-ability-abilitymanager-preloadeduiextensionabilitydestroyedfn-t-sys.md) | 预加载[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)被销毁时的回调函数类型。<br/> |
| <!--DelRow-->[PreloadedUIExtensionAbilityLoadedFn](arkts-ability-abilitymanager-preloadeduiextensionabilityloadedfn-t-sys.md) | 预加载[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)被加载时的回调函数类型。<br/> |

