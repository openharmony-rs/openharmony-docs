# particleAbility接口切换
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->


| FA模型接口 | Stage模型接口对应d.ts文件 | Stage模型对应接口 | 
| -------- | -------- | -------- |
| startAbility(parameter:&nbsp;StartAbilityParameter,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void;<br/>startAbility(parameter:&nbsp;StartAbilityParameter):&nbsp;Promise&lt;void&gt;; | application\ServiceExtensionContext.d.ts | startAbility(want:&nbsp;Want,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>startAbility(want:&nbsp;Want,&nbsp;options:&nbsp;StartOptions,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>startAbility(want:&nbsp;Want,&nbsp;options?:&nbsp;StartOptions):&nbsp;Promise&lt;void&gt;;<br/>startServiceExtensionAbility(want:&nbsp;Want,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>startServiceExtensionAbility(want:&nbsp;Want):&nbsp;Promise&lt;void&gt;; |
| terminateSelf(callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>terminateSelf():&nbsp;Promise&lt;void&gt;; | application\ServiceExtensionContext.d.ts | terminateSelf(callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>terminateSelf():&nbsp;Promise&lt;void&gt;; |
| connectAbility(request:&nbsp;Want,&nbsp;options:ConnectOptions&nbsp;):&nbsp;number; | application\ServiceExtensionContext.d.ts | connectServiceExtensionAbility(want:&nbsp;Want,&nbsp;options:&nbsp;ConnectOptions):&nbsp;number; |
| disconnectAbility(connection:&nbsp;number,&nbsp;callback:AsyncCallback&lt;void&gt;):&nbsp;void;<br/>disconnectAbility(connection:&nbsp;number):&nbsp;Promise&lt;void&gt;; | application\ServiceExtensionContext.d.ts | disconnectServiceExtensionAbility(connection:&nbsp;number,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>disconnectServiceExtensionAbility(connection:&nbsp;number):&nbsp;Promise&lt;void&gt;; |
| acquireDataAbilityHelper(uri:&nbsp;string):&nbsp;DataAbilityHelper; | \@ohos.data.dataShare.d.ts<br/>\@ohos.data.fileAccess.d.ts | createDataShareHelper(context:&nbsp;Context,&nbsp;uri:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;DataShareHelper&gt;):&nbsp;void;<br/>createDataShareHelper(context:&nbsp;Context,&nbsp;uri:&nbsp;string):&nbsp;Promise&lt;DataShareHelper&gt;;<br/>createFileAccessHelper(context:&nbsp;Context):&nbsp;FileAccessHelper;<br/>createFileAccessHelper(context:&nbsp;Context,&nbsp;wants:&nbsp;Array&lt;Want&gt;):&nbsp;FileAccessHelper; |
| startBackgroundRunning(id:&nbsp;number,&nbsp;request:&nbsp;NotificationRequest,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>startBackgroundRunning(id:&nbsp;number,&nbsp;request:&nbsp;NotificationRequest):&nbsp;Promise&lt;void&gt;; | \@ohos.resourceschedule.backgroundTaskManager.d.ts | startBackgroundRunning(context:&nbsp;Context,&nbsp;bgMode:&nbsp;BackgroundMode,&nbsp;wantAgent:&nbsp;WantAgent,&nbsp;callback:&nbsp;AsyncCallback):&nbsp;void;<br/>startBackgroundRunning(context:&nbsp;Context,&nbsp;bgMode:&nbsp;BackgroundMode,&nbsp;wantAgent:&nbsp;WantAgent):&nbsp;Promise&lt;void&gt;; |
| cancelBackgroundRunning(callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>cancelBackgroundRunning():&nbsp;Promise&lt;void&gt;; | \@ohos.resourceschedule.backgroundTaskManager.d.ts | stopBackgroundRunning(context:&nbsp;Context,&nbsp;callback:&nbsp;AsyncCallback):&nbsp;void;<br/>stopBackgroundRunning(context:&nbsp;Context):&nbsp;Promise&lt;void&gt;; |
