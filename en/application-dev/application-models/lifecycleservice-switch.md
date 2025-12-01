# LifecycleService Switching
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->


  | API in the [FA Model](ability-terminology.md#fa-model)| Corresponding .d.ts File in the [Stage Model](ability-terminology.md#stage-model)| Corresponding API in the Stage Model| 
| -------- | -------- | -------- |
| onStart?():&nbsp;void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onCreate(want:&nbsp;Want):&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#oncreate) |
| onCommand?(want:&nbsp;Want,&nbsp;startId:&nbsp;number):&nbsp;void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onRequest(want:&nbsp;Want,&nbsp;startId:&nbsp;number):&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#onrequest) |  |
| onStop?():&nbsp;void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onDestroy():&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#ondestroy) |  |
| onConnect?(want:&nbsp;Want):&nbsp;rpc.RemoteObject; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onConnect(want:&nbsp;Want):&nbsp;rpc.RemoteObject;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#onconnect) |  |
| onDisconnect?(want:&nbsp;Want):&nbsp;void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onDisconnect(want:&nbsp;Want):&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#ondisconnect) |  |
| onReconnect?(want:&nbsp;Want):&nbsp;void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onReconnect(want:&nbsp;Want):&nbsp;void;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#onreconnect) |  |
