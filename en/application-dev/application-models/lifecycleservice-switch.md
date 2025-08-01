# LifecycleService Switching


  | API in the FA Model| Corresponding .d.ts File in the Stage Model| Corresponding API in the Stage Model| 
| -------- | -------- | -------- |
| onStart?(): void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onCreate(want: Want): void;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#oncreate) |
| onCommand?(want: Want, startId: number): void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onRequest(want: Want, startId: number): void;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#onrequest) |  |
| onStop?(): void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onDestroy(): void;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#ondestroy) |  |
| onConnect?(want: Want): rpc.RemoteObject; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onConnect(want: Want): rpc.RemoteObject;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#onconnect) |  |
| onDisconnect?(want: Want): void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onDisconnect(want: Want): void;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#ondisconnect) |  |
| onReconnect?(want: Want): void; | \@ohos.app.ability.ServiceExtensionAbility.d.ts | [onReconnect(want: Want): void;](../reference/apis-ability-kit/js-apis-app-ability-serviceExtensionAbility-sys.md#onreconnect) |  |
