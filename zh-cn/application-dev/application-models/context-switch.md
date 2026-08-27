# Context接口切换

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

| FA模型接口 | Stage模型接口对应d.ts文件 | Stage对应接口或字段 | 
| -------- | -------- | -------- |
| getOrCreateLocalDir(callback:AsyncCallback&lt;string&gt;):void;<br/>getOrCreateLocalDir():Promise&lt;string&gt;; | Stage模型无对应接口 | Stage模型应用在应用根目录下没有操作权限，不提供对应接口 |
| verifyPermission(permission:string,options:PermissionOptions,callback:AsyncCallback&lt;number&gt;):void;<br/>verifyPermission(permission:string,callback:AsyncCallback&lt;number&gt;):void;<br/>verifyPermission(permission:string,options?:PermissionOptions):Promise&lt;number&gt;; | \@ohos.abilityAccessCtrl.d.ts | verifyAccessTokenSync(tokenID: number, permissionName: Permissions): GrantStatus;<br/>verifyAccessToken(tokenID: number, permissionName: Permissions): Promise&lt;GrantStatus&gt;; |
| requestPermissionsFromUser(permissions:Array&lt;string&gt;,requestCode:number,resultCallback:AsyncCallback&lt;PermissionRequestResult&gt;):void;<br/>requestPermissionsFromUser(permissions:Array&lt;string&gt;,requestCode:number):Promise&lt;PermissionRequestResult&gt;; | \@ohos.abilityAccessCtrl.d.ts | requestPermissionsFromUser(context: Context, permissionList: Array&lt;Permissions&gt;, requestCallback: AsyncCallback&lt;PermissionRequestResult&gt;) : void;<br/>requestPermissionsFromUser(context: Context, permissionList: Array&lt;Permissions&gt;) : Promise&lt;PermissionRequestResult&gt;; |
| getApplicationInfo(callback:AsyncCallback&lt;ApplicationInfo&gt;):void;<br/>getApplicationInfo():Promise&lt;ApplicationInfo&gt;; | application\Context.d.ts | applicationInfo: ApplicationInfo; |
| getBundleName(callback : AsyncCallback&lt;string&gt;): void;<br/>getBundleName(): Promise&lt;string&gt;; | application\UIAbilityContext.d.ts | abilityInfo.bundleName: string; |
| getDisplayOrientation(callback : AsyncCallback&lt;bundle.DisplayOrientation&gt;): void;<br/>getDisplayOrientation(): Promise&lt;bundle.DisplayOrientation&gt;; | \@ohos.screen.d.ts | readonly orientation: Orientation; |
| setDisplayOrientation(orientation:bundle.DisplayOrientation, callback:AsyncCallback&lt;void&gt;):void;<br/>setDisplayOrientation(orientation:bundle.DisplayOrientation):Promise&lt;void&gt;; | \@ohos.screen.d.ts | setOrientation(orientation: Orientation, callback: AsyncCallback&lt;void&gt;): void;<br/>setOrientation(orientation: Orientation): Promise&lt;void&gt;; |
| setShowOnLockScreen(show:boolean, callback:AsyncCallback&lt;void&gt;):void;<br/>setShowOnLockScreen(show:boolean):Promise&lt;void&gt;; | \@ohos.window.d.ts | setShowOnLockScreen(showOnLockScreen: boolean): void; |
| setWakeUpScreen(wakeUp:boolean, callback:AsyncCallback&lt;void&gt;):void;<br/>setWakeUpScreen(wakeUp:boolean):Promise&lt;void&gt;; | \@ohos.window.d.ts | setWakeUpScreen(wakeUp: boolean): void; |
| getProcessInfo(callback:AsyncCallback&lt;ProcessInfo&gt;):void;<br/>getProcessInfo():Promise&lt;ProcessInfo&gt;; | \@ohos.app.ability.abilityManager.d.ts | getAbilityRunningInfos(callback: AsyncCallback&lt;Array&lt;AbilityRunningInfo&gt;&gt;): void;<br/>getAbilityRunningInfos(): Promise&lt;Array&lt;AbilityRunningInfo&gt;&gt;; |
| getElementName(callback:AsyncCallback&lt;ElementName&gt;):void;<br/>getElementName():Promise&lt;ElementName&gt;; | application\UIAbilityContext.d.ts | abilityInfo.name: string;<br/>abilityInfo.bundleName: string; |
| getProcessName(callback:AsyncCallback&lt;string&gt;):void;<br/>getProcessName():Promise&lt;string&gt;; | \@ohos.app.ability.abilityManager.d.ts | getAbilityRunningInfos(callback: AsyncCallback&lt;Array&lt;AbilityRunningInfo&gt;&gt;): void;<br/>getAbilityRunningInfos(): Promise&lt;Array&lt;AbilityRunningInfo&gt;&gt;; |
| getCallingBundle(callback:AsyncCallback&lt;string&gt;):void;<br/>getCallingBundle():Promise&lt;string&gt;; | Stage模型无对应接口 | Stage模型应用可以使用Want.parameters的ohos.aafwk.param.callerUid参数，获取调用方的应用信息 |
| getFilesDir(callback:AsyncCallback&lt;string&gt;):void;<br/>getFilesDir():Promise&lt;string&gt;; | application\Context.d.ts | filesDir: string; |
| getCacheDir(callback:AsyncCallback&lt;string&gt;):void;<br/>getCacheDir():Promise&lt;string&gt;; | application\Context.d.ts | cacheDir: string; |
| getOrCreateDistributedDir(callback:AsyncCallback&lt;string&gt;):void;<br/>getOrCreateDistributedDir():Promise&lt;string&gt;; | application\Context.d.ts | distributedFilesDir: string; |
| getAppType(callback:AsyncCallback&lt;string&gt;):void;<br/>getAppType():Promise&lt;string&gt;; | application\UIAbilityContext.d.ts | 通过abilityInfo字段的type属性获取<br/>abilityInfo.type: bundleManager.AbilityType; |
| getHapModuleInfo(callback:AsyncCallback&lt;HapModuleInfo&gt;):void;<br/>getHapModuleInfo():Promise&lt;HapModuleInfo&gt;; | application\UIAbilityContext.d.ts | currentHapModuleInfo: HapModuleInfo; |
| getAppVersionInfo(callback:AsyncCallback&lt;AppVersionInfo&gt;):void;<br/>getAppVersionInfo():Promise&lt;AppVersionInfo&gt;; | bundle\bundleInfo.d.ts | readonly name: string;<br/>readonly versionCode: number;<br/>readonly versionName: string; |
| getApplicationContext():Context; | application\Context.d.ts | getApplicationContext(): ApplicationContext; |
| getAbilityInfo(callback:AsyncCallback&lt;AbilityInfo&gt;):void;<br/>getAbilityInfo():Promise&lt;AbilityInfo&gt;; | application\UIAbilityContext.d.ts | abilityInfo: AbilityInfo; |
| isUpdatingConfigurations(callback:AsyncCallback&lt;boolean&gt;):void;<br/>isUpdatingConfigurations():Promise&lt;boolean&gt;; | Stage模型无对应接口 | 在系统环境变化时，应用不会重启，调用onConfigurationUpdated接口通知应用，该接口在FA模型是空实现接口，Stage模型不提供对应接口 |
| printDrawnCompleted(callback:AsyncCallback&lt;void&gt;):void;<br/>printDrawnCompleted():Promise&lt;void&gt;; | Stage模型无对应接口 | 该接口在FA模型是空实现接口，不影响应用功能，Stage模型不提供对应接口 |
