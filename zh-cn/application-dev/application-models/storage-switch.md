# Storage接口切换

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

| FA模型接口 | Stage模型接口对应d.ts文件 | Stage模型对应接口 | 
| -------- | -------- | -------- |
| GetStorageOptions | Stage模型无对应接口 | Storage接口功能使用Preferences接口来代替，接口入参已经重新设计 | 
| SetStorageOptions | Stage模型无对应接口 | Storage接口功能使用Preferences接口来代替，接口入参已经重新设计 | 
| ClearStorageOptions | Stage模型无对应接口 | Storage接口功能使用Preferences接口来代替，接口入参已经重新设计 | 
| DeleteStorageOptions | Stage模型无对应接口 | Storage接口功能使用Preferences接口来代替，接口入参已经重新设计 | 
| static&nbsp;get(options:&nbsp;GetStorageOptions):&nbsp;void; | \@ohos.data.preferences.d.ts | get(key:&nbsp;string,&nbsp;defValue:&nbsp;ValueType,&nbsp;callback:&nbsp;AsyncCallback&lt;ValueType&gt;):&nbsp;void;<br/>get(key:&nbsp;string,&nbsp;defValue:&nbsp;ValueType):&nbsp;Promise&lt;ValueType&gt;; |
| static&nbsp;set(options:&nbsp;SetStorageOptions):&nbsp;void; | \@ohos.data.preferences.d.ts | put(key:&nbsp;string,&nbsp;value:&nbsp;ValueType,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>put(key:&nbsp;string,&nbsp;value:&nbsp;ValueType):&nbsp;Promise&lt;void&gt;; |
| static&nbsp;clear(options?:&nbsp;ClearStorageOptions):&nbsp;void; | \@ohos.data.preferences.d.ts | clear(callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>clear():&nbsp;Promise&lt;void&gt;; |
| static&nbsp;delete(options:&nbsp;DeleteStorageOptions):&nbsp;void; | \@ohos.data.preferences.d.ts | delete(key:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;<br/>delete(key:&nbsp;string):&nbsp;Promise&lt;void&gt;; |
