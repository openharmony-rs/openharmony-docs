# LifecycleApp Switching

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

| API in the [FA Model](ability-terminology.md#fa-model)| Corresponding .d.ts File in the [Stage Model](ability-terminology.md#stage-model)| Corresponding API in the Stage Model|
| -------- | -------- | -------- |
| onShow?():&nbsp;void; | \@ohos.window.d.ts | [on(eventType:&nbsp;'windowStageEvent',&nbsp;callback:&nbsp;Callback&lt;WindowStageEventType&gt;):&nbsp;void;](../reference/apis-arkui/arkts-apis-window-WindowStage.md#onwindowstageevent9)<br>Listens for SHOWN, indicating a switching to the foreground.|
| onHide?():&nbsp;void; | \@ohos.window.d.ts | [on(eventType:&nbsp;'windowStageEvent',&nbsp;callback:&nbsp;Callback&lt;WindowStageEventType&gt;):&nbsp;void;](../reference/apis-arkui/arkts-apis-window-WindowStage.md#onwindowstageevent9)<br>Listens for HIDDEN, indicating a switching to the background.|
| onDestroy?():&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | [onDestroy():&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#ondestroy) |
| onCreate?():&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | [onCreate(want:&nbsp;Want,&nbsp;launchParam:&nbsp;AbilityConstant.LaunchParam):&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate) |
| onWindowDisplayModeChanged?(isShownInMultiWindow:&nbsp;boolean,&nbsp;newConfig:&nbsp;resourceManager.Configuration):&nbsp;void; | There is no corresponding API in the stage model.| No corresponding API is provided.|
| onStartContinuation?():&nbsp;boolean; | There is no corresponding API in the stage model.| In the stage model, an application does not need to detect whether the continuation is successful (detected when the application initiates the continuation request). Therefore, the **onStartContinuation()** callback is deprecated.|
| onSaveData?(data:&nbsp;Object):&nbsp;boolean; | \@ohos.app.ability.UIAbility.d.ts | [onContinue(wantParam: Record&lt;string, Object&gt;):&nbsp;AbilityConstant.OnContinueResult;](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncontinue) |
| onCompleteContinuation?(result:&nbsp;number):&nbsp;void; | application\ContinueCallback.d.ts | [onContinueDone(result:&nbsp;number):&nbsp;void;](../reference/apis-ability-kit/js-apis-inner-application-continueCallback-sys.md#continuecallbackoncontinuedone) |
| onRestoreData?(data:&nbsp;Object):&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | [onCreate(want:&nbsp;Want,&nbsp;launchParam:&nbsp;AbilityConstant.LaunchParam):&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate)<br>[onNewWant(want:&nbsp;Want,&nbsp;launchParam:&nbsp;AbilityConstant.LaunchParam):&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onnewwant)<br>In multiton or singleton mode, the target ability completes data restoration in the **onCreate()** callback. In the callback, **launchParam.launchReason** is used to determine whether it is a continuation-based launch scenario. If it is, the data saved before continuation can be obtained from the **want** parameter.|
| onRemoteTerminated?():&nbsp;void; | application\ContinueCallback.d.ts | [onContinueDone(result:&nbsp;number):&nbsp;void;](../reference/apis-ability-kit/js-apis-inner-application-continueCallback-sys.md#continuecallbackoncontinuedone) |
| onSaveAbilityState?(outState:&nbsp;PacMap):&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | [onSaveState(reason:&nbsp;AbilityConstant.StateType,&nbsp;wantParam&nbsp;:&nbsp;Record&lt;string,&nbsp;Object&gt;):&nbsp;AbilityConstant.OnSaveResult;](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onsavestate) |
| onRestoreAbilityState?(inState:&nbsp;PacMap):&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | [onCreate(want:&nbsp;Want,&nbsp;launchParam:&nbsp;AbilityConstant.LaunchParam):&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate)<br>After an application is restarted, the **onCreate()** callback is triggered. In the callback, **launchParam.launchReason** is used to determine whether it is a self-recovery scenario. If it is, the data saved before the restart can be obtained from the **want** parameter.|
| onInactive?():&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | [onBackground():&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onbackground) |
| onActive?():&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | [onForeground():&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onforeground) |
| onNewWant?(want:&nbsp;Want):&nbsp;void; | \@ohos.app.ability.UIAbility.d.ts | [onNewWant(want:&nbsp;Want,&nbsp;launchParam:&nbsp;AbilityConstant.LaunchParam):&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onnewwant) |
| onMemoryLevel?(level:&nbsp;number):&nbsp;void | \@ohos.app.ability.UIAbility.d.ts | [onMemoryLevel(level:&nbsp;AbilityConstant.MemoryLevel):&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-ability.md#abilityonmemorylevel) |
