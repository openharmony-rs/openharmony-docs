# featureAbility接口切换

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @lidongrui-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

| FA模型接口 | Stage模型接口对应d.ts文件 | Stage模型对应接口 | 
| -------- | -------- | -------- |
| getWant(callback:&nbsp;AsyncCallback&lt;Want&gt;):&nbsp;void;<br/>getWant():&nbsp;Promise&lt;Want&gt;; | \@ohos.app.ability.UIAbility.d.ts | launchWant:&nbsp;Want; | 
| startAbility(parameter:&nbsp;StartAbilityParameter,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void;<br/>startAbility(parameter:&nbsp;StartAbilityParameter):&nbsp;Promise&lt;number&gt;; | application\UIAbilityContext.d.ts | startAbility(want:&nbsp;Want,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>startAbility(want:&nbsp;Want,&nbsp;options:&nbsp;StartOptions,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>startAbility(want:&nbsp;Want,&nbsp;options?:&nbsp;StartOptions):&nbsp;Promise&lt;void&gt;; |
| getContext():&nbsp;Context; | \@ohos.app.ability.UIAbility.d.ts | context:&nbsp;UIAbilityContext; |
| startAbilityForResult(parameter:&nbsp;StartAbilityParameter,&nbsp;callback:&nbsp;AsyncCallback&lt;AbilityResult&gt;):&nbsp;void;<br/>startAbilityForResult(parameter:&nbsp;StartAbilityParameter):&nbsp;Promise&lt;AbilityResult&gt;; | application\UIAbilityContext.d.ts | startAbilityForResult(want:&nbsp;Want,&nbsp;callback:&nbsp;AsyncCallback&lt;AbilityResult&gt;):&nbsp;void;<br/>startAbilityForResult(want:&nbsp;Want,&nbsp;options:&nbsp;StartOptions,&nbsp;callback:&nbsp;AsyncCallback&lt;AbilityResult&gt;):&nbsp;void;<br/>startAbilityForResult(want:&nbsp;Want,&nbsp;options?:&nbsp;StartOptions):&nbsp;Promise&lt;AbilityResult&gt;; |
| terminateSelfWithResult(parameter:&nbsp;AbilityResult,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>terminateSelfWithResult(parameter:&nbsp;AbilityResult):&nbsp;Promise&lt;void&gt;; | application\UIAbilityContext.d.ts | terminateSelfWithResult(parameter:&nbsp;AbilityResult,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>terminateSelfWithResult(parameter:&nbsp;AbilityResult):&nbsp;Promise&lt;void&gt;; |
| terminateSelf(callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>terminateSelf():&nbsp;Promise&lt;void&gt;; | application\UIAbilityContext.d.ts | terminateSelf(callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>terminateSelf():&nbsp;Promise&lt;void&gt;; |
| acquireDataAbilityHelper(uri:&nbsp;string):&nbsp;DataAbilityHelper; | \@ohos.data.dataShare.d.ts<br/>\@ohos.data.fileAccess.d.ts | createDataShareHelper(context:&nbsp;Context,&nbsp;uri:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;DataShareHelper&gt;):&nbsp;void;<br/>createDataShareHelper(context:&nbsp;Context,&nbsp;uri:&nbsp;string):&nbsp;Promise&lt;DataShareHelper&gt;;<br/>createFileAccessHelper(context:&nbsp;Context):&nbsp;FileAccessHelper;<br/>createFileAccessHelper(context:&nbsp;Context,&nbsp;wants:&nbsp;Array&lt;Want&gt;):&nbsp;FileAccessHelper; |
| hasWindowFocus(callback:&nbsp;AsyncCallback&lt;boolean&gt;):&nbsp;void;<br/>hasWindowFocus():&nbsp;Promise&lt;boolean&gt;; | \@ohos.window.d.ts | on(eventType:&nbsp;'windowStageEvent',&nbsp;callback:&nbsp;Callback&lt;WindowStageEventType&gt;):&nbsp;void;<br/>监听Active获焦状态 |
| connectAbility(request:&nbsp;Want,&nbsp;options:ConnectOptions&nbsp;):&nbsp;number; | application\UIAbilityContext.d.ts | connectServiceExtensionAbility(want:&nbsp;Want,&nbsp;options:&nbsp;ConnectOptions):&nbsp;number; |
| disconnectAbility(connection:&nbsp;number,&nbsp;callback:AsyncCallback&lt;void&gt;):&nbsp;void;<br/>disconnectAbility(connection:&nbsp;number):&nbsp;Promise&lt;void&gt;; | application\UIAbilityContext.d.ts | disconnectAbility(connection:&nbsp;number,&nbsp;callback:AsyncCallback&lt;void&gt;):&nbsp;void;<br/>disconnectAbility(connection:&nbsp;number):&nbsp;Promise&lt;void&gt;; |
| getWindow(callback:&nbsp;AsyncCallback&lt;window.Window&gt;):&nbsp;void;<br/>getWindow():&nbsp;Promise&lt;window.Window&gt;; | \@ohos.window.d.ts | getLastWindow(ctx:&nbsp;BaseContext,&nbsp;callback:&nbsp;AsyncCallback&lt;Window&gt;):&nbsp;void;<br/>getLastWindow(ctx:&nbsp;BaseContext):&nbsp;Promise&lt;Window&gt;; |
