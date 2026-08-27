# LifecycleApp接口切换

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

| FA模型接口 | Stage模型接口对应d.ts文件 | Stage模型对应接口 |
| -------- | -------- | -------- |
| onShow?():&nbsp;void; | \@ohos.window.d.ts | on(eventType:&nbsp;'windowStageEvent',&nbsp;callback:&nbsp;Callback&lt;WindowStageEventType&gt;):&nbsp;void;<br/>监听SHOWN切到前台状态 |
| onHide?():&nbsp;void; | \@ohos.window.d.ts | on(eventType:&nbsp;'windowStageEvent',&nbsp;callback:&nbsp;Callback&lt;WindowStageEventType&gt;):&nbsp;void;<br/>监听HIDDEN切到后台状态 |
| onDestroy?():&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | onDestroy():&nbsp;void; |
| onCreate?():&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | onCreate(want:&nbsp;Want,&nbsp;launchParam:&nbsp;AbilityConstant.LaunchParam):&nbsp;void; |
| onWindowDisplayModeChanged?(isShownInMultiWindow:&nbsp;boolean,&nbsp;newConfig:&nbsp;resourceManager.Configuration):&nbsp;void; | Stage模型无对应接口 | 暂时未提供对应接口 |
| onStartContinuation?():&nbsp;boolean; | Stage模型无对应接口 | Stage模型上，应用无需感知迁移是否成功（由应用发起迁移请求时感知），onStartContinuation废弃 |
| onSaveData?(data:&nbsp;Object):&nbsp;boolean; | \@ohos.app.ability.UIAbility.d.ts | onContinue(wantParam: Record&lt;string, Object&gt;):&nbsp;AbilityConstant.OnContinueResult; |
| onCompleteContinuation?(result:&nbsp;number):&nbsp;void; | application\ContinueCallback.d.ts | onContinueDone(result:&nbsp;number):&nbsp;void; |
| onRestoreData?(data:&nbsp;Object):&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | onCreate(want:&nbsp;Want,&nbsp;launchParam:&nbsp;AbilityConstant.LaunchParam):&nbsp;void;<br/>onNewWant(want:&nbsp;Want,&nbsp;launchParam:&nbsp;AbilityConstant.LaunchParam):&nbsp;void;<br/>多实例模式Ability迁移目标端在onCreate回调中完成数据恢复，单实例模式应用迁移目标端在onCreate回调中完成数据恢复，回调中通过判断launchParam.launchReason可获取迁移启动的场景，从而可以从Want中获取迁移前保存的数据 |
| onRemoteTerminated?():&nbsp;void; | application\ContinueCallback.d.ts | onContinueDone(result:&nbsp;number):&nbsp;void; |
| onSaveAbilityState?(outState:&nbsp;PacMap):&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | onSaveState(reason:&nbsp;AbilityConstant.StateType,&nbsp;wantParam&nbsp;:&nbsp;Record&lt;string,&nbsp;Object&gt;):&nbsp;AbilityConstant.OnSaveResult; |
| onRestoreAbilityState?(inState:&nbsp;PacMap):&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | onCreate(want:&nbsp;Want,&nbsp;launchParam:&nbsp;AbilityConstant.LaunchParam):&nbsp;void;<br/>应用重启后会触发Ability的onCreate方法，通过判断launchParam.launchReason可获取自恢复的场景，从而可以从Want中获取重启前保存的数据 |
| onInactive?():&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | onBackground():&nbsp;void; |
| onActive?():&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | onForeground():&nbsp;void; |
| onNewWant?(want:&nbsp;Want):&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | onNewWant(want:&nbsp;Want,&nbsp;launchParam:&nbsp;AbilityConstant.LaunchParam):&nbsp;void; |
| onMemoryLevel?(level:&nbsp;number):&nbsp;void | \@ohos.app.ability.UIAbility.d.ts | onMemoryLevel(level:&nbsp;AbilityConstant.MemoryLevel):&nbsp;void; |
