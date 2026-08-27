# LifecycleService接口切换
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->


| FA模型接口 | Stage模型接口对应d.ts文件 | Stage模型对应接口 | 
| -------- | -------- | -------- |
| onStart?():&nbsp;void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | onCreate(want:&nbsp;Want):&nbsp;void; |
| onCommand?(want:&nbsp;Want,&nbsp;startId:&nbsp;number):&nbsp;void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | onRequest(want:&nbsp;Want,&nbsp;startId:&nbsp;number):&nbsp;void; |
| onStop?():&nbsp;void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | onDestroy():&nbsp;void; |
| onConnect?(want:&nbsp;Want):&nbsp;rpc.RemoteObject; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | onConnect(want:&nbsp;Want):&nbsp;rpc.RemoteObject; |
| onDisconnect?(want:&nbsp;Want):&nbsp;void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | onDisconnect(want:&nbsp;Want):&nbsp;void; |
| onReconnect?(want:&nbsp;Want):&nbsp;void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | onReconnect(want:&nbsp;Want):&nbsp;void; |
