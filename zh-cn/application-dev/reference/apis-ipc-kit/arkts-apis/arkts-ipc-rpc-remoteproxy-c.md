# RemoteProxy

实现IRemoteObject代理对象。

**继承/实现关系：** RemoteProxy extends [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-rpc-class RemoteProxy extends IRemoteObject--><!--Device-rpc-class RemoteProxy extends IRemoteObject-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## DUMP_TRANSACTION

```TypeScript
static get DUMP_TRANSACTION(): int
```

Indicates the message code for a dump operation.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RemoteProxy-static get DUMP_TRANSACTION(): int--><!--Device-RemoteProxy-static get DUMP_TRANSACTION(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Return vaule indicating the message code for a dump operation. |

## INTERFACE_TRANSACTION

```TypeScript
static get INTERFACE_TRANSACTION(): int
```

Indicates the message code for a transmission.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RemoteProxy-static get INTERFACE_TRANSACTION(): int--><!--Device-RemoteProxy-static get INTERFACE_TRANSACTION(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Return vaule indicating the message code for a transmission. |

## MAX_TRANSACTION_ID

```TypeScript
static get MAX_TRANSACTION_ID(): int
```

Indicates the maximum value of a valid message code. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_This constant is used to check the validity of an operation.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RemoteProxy-static get MAX_TRANSACTION_ID(): int--><!--Device-RemoteProxy-static get MAX_TRANSACTION_ID(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Return vaule indicating the maximum value of a valid message code. |

## MIN_TRANSACTION_ID

```TypeScript
static get MIN_TRANSACTION_ID(): int
```

Indicates the minimum value of a valid message code. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_This constant is used to check the validity of an operation.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RemoteProxy-static get MIN_TRANSACTION_ID(): int--><!--Device-RemoteProxy-static get MIN_TRANSACTION_ID(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Return vaule indicating the minimum value of a valid message code. |

## PING_TRANSACTION

```TypeScript
static get PING_TRANSACTION(): int
```

Indicates the message code for a Ping operation.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-RemoteProxy-static get PING_TRANSACTION(): int--><!--Device-RemoteProxy-static get PING_TRANSACTION(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Return vaule indicating the message code for a Ping operation. |

## addDeathRecipient

```TypeScript
addDeathRecipient(recipient: DeathRecipient, flags: number): boolean
```

注册用于接收远程对象死亡通知的回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [rpc.IRemoteObject#registerDeathRecipient](arkts-ipc-rpc-iremoteobject-c.md#registerdeathrecipient)(recipient:

<!--Device-RemoteProxy-addDeathRecipient(recipient: DeathRecipient, flags: number): boolean--><!--Device-RemoteProxy-addDeathRecipient(recipient: DeathRecipient, flags: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 收件人表示要注册的回调。 |
| flags | number | 是 | 死亡通知标志。保留参数。设置为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：回调注册成功，false：回调注册失败。 |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的addDeathRecipient接口方法新增死亡回调

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
if (proxy != undefined) {
  let deathRecipient = new MyDeathRecipient();
  proxy.addDeathRecipient(deathRecipient, 0);
}
```

## getDescriptor

```TypeScript
getDescriptor(): string
```

获取对象的接口描述符，接口描述符为字符串。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-RemoteProxy-getDescriptor(): string--><!--Device-RemoteProxy-getDescriptor(): string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回接口描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900007](../errorcode-rpc.md#1900007-远端对象通信失败) | communication failed. |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的getDescriptor接口方法获取对象的接口描述符

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

if (proxy != undefined) {
  try {
    let descriptor: string = proxy.getDescriptor();
    hilog.info(0x0000, 'testTag', 'descriptor is ' + descriptor);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    hilog.error(0x0000, 'testTag', 'rpc get interface descriptor fail, errorCode ' + e.code);
    hilog.error(0x0000, 'testTag', 'rpc get interface descriptor fail, errorMessage ' + e.message);
  }
}
```

## getInterfaceDescriptor

```TypeScript
getInterfaceDescriptor(): string
```

查询当前代理对象接口的描述符。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [rpc.IRemoteObject#getDescriptor](arkts-ipc-rpc-iremoteobject-c.md#getdescriptor)()

<!--Device-RemoteProxy-getInterfaceDescriptor(): string--><!--Device-RemoteProxy-getInterfaceDescriptor(): string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前的接口描述符。 |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的getInterfaceDescriptor接口方法查询当前代理对象接口的描述符

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

if (proxy != undefined) {
  let descriptor: string = proxy.getInterfaceDescriptor();
  hilog.info(0x0000, 'testTag', 'descriptor is ' + descriptor);
}
```

## getLocalInterface

```TypeScript
getLocalInterface(interfaceDes: string): IRemoteBroker
```

查询并获取当前接口描述符对应的本地接口对象。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-RemoteProxy-getLocalInterface(interfaceDes: string): IRemoteBroker--><!--Device-RemoteProxy-getLocalInterface(interfaceDes: string): IRemoteBroker-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interfaceDes | string | 是 | 需要查询的接口描述符，其长度应小于40960。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 默认返回Null，标识该接口是一个代理侧接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | check param failed |
| [1900006](../errorcode-rpc.md#1900006-ipc对象权限错误) | Operation allowed only for the remote object. |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的getLocalInterface接口方法查询接口对象

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

if (proxy != undefined) {
  try {
    let broker: rpc.IRemoteBroker = proxy.getLocalInterface("testObject");
    hilog.info(0x0000, 'testTag', 'getLocalInterface is ' + broker);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    hilog.error(0x0000, 'testTag', 'rpc get local interface fail, errorCode ' + e.code);
    hilog.error(0x0000, 'testTag', 'rpc get local interface fail, errorMessage ' + e.message);
  }
}
```

## isObjectDead

```TypeScript
isObjectDead(): boolean
```

指示对应的RemoteObject是否死亡。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-RemoteProxy-isObjectDead(): boolean--><!--Device-RemoteProxy-isObjectDead(): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：对应的对象已经死亡，false：对应的对象未死亡。 |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的isObjectDead接口方法判断当前对象是否已经死亡

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

if (proxy != undefined) {
  let isDead: boolean = proxy.isObjectDead();
  hilog.info(0x0000, 'testTag', 'isObjectDead is ' + isDead);
}
```

## queryLocalInterface

```TypeScript
queryLocalInterface(interface: string): IRemoteBroker
```

查询并获取当前接口描述符对应的本地接口对象。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [rpc.IRemoteObject#getLocalInterface](arkts-ipc-rpc-iremoteobject-c.md#getlocalinterface)(descriptor:

<!--Device-RemoteProxy-queryLocalInterface(interface: string): IRemoteBroker--><!--Device-RemoteProxy-queryLocalInterface(interface: string): IRemoteBroker-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interface | string | 是 | 需要查询的接口描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 默认返回Null，标识该接口是一个代理侧接口。 |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的queryLocalInterface接口获取接口对象

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

if (proxy != undefined) {
  let broker: rpc.IRemoteBroker = proxy.queryLocalInterface("testObject");
  hilog.info(0x0000, 'testTag', 'queryLocalInterface is ' + broker);
}
```

## registerDeathRecipient

ArkTS-Dyn:
```TypeScript
registerDeathRecipient(recipient: DeathRecipient, flags: number): void
```

ArkTS-Sta:
```TypeScript
registerDeathRecipient(recipient: DeathRecipient, flags: int): void
```

注册用于接收远程对象死亡通知的回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-RemoteProxy-registerDeathRecipient(recipient: DeathRecipient, flags: int): void--><!--Device-RemoteProxy-registerDeathRecipient(recipient: DeathRecipient, flags: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要注册的回调。 |
| flags | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 死亡通知标志。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.The number of parameters is incorrect;2.The parameter type does not match;3.The callback used to receive remote object death notifications is empty. |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的registerDeathRecipient接口注册死亡回调

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
if (proxy != undefined) {
  try {
    let deathRecipient = new MyDeathRecipient();
    proxy.registerDeathRecipient(deathRecipient, 0);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    hilog.error(0x0000, 'testTag', 'proxy register deathRecipient fail, errorCode ' + e.code);
    hilog.error(0x0000, 'testTag', 'proxy register deathRecipient fail, errorMessage ' + e.message);
  }
}
```

## removeDeathRecipient

```TypeScript
removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean
```

注销用于接收远程对象死亡通知的回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [rpc.IRemoteObject#unregisterDeathRecipient](arkts-ipc-rpc-iremoteobject-c.md#unregisterdeathrecipient)(recipient:

<!--Device-RemoteProxy-removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean--><!--Device-RemoteProxy-removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要注销的死亡回调。 |
| flags | number | 是 | 死亡通知标志。保留参数。设置为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：回调注销成功，false：回调注销失败。 |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的removeDeathRecipient接口方法去注册死亡回调

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
if (proxy != undefined) {
  let deathRecipient = new MyDeathRecipient();
  proxy.addDeathRecipient(deathRecipient, 0);
  proxy.removeDeathRecipient(deathRecipient, 0);
}
```

## sendMessageRequest

ArkTS-Dyn:
```TypeScript
sendMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption
    ): Promise<RequestResult>
```

ArkTS-Sta:
```TypeScript
sendMessageRequest(
      code: int,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption
    ): Promise<RequestResult>
```

以同步或异步方式向对端进程发送MessageSequence消息。如果为选项设置了异步模式，则发送请求的响应结果立即返回，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则发送请求的响应结 果将在sendMessageRequest返回时返回，回复内容在reply报文里。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-RemoteProxy-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): Promise<RequestResult>--><!--Device-RemoteProxy-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): Promise<RequestResult>-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageSequence对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageSequence对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RequestResult&gt; | Promise对象，返回发送请求的响应结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.The number of parameters is incorrect;2.The parameter type does not match;3.Failed to obtain the passed object instance. |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的sendMessageRequest接口方法发送消息

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let data = rpc.MessageSequence.create();
  let reply = rpc.MessageSequence.create();
  data.writeInt(1);
  data.writeString("hello");
  if (proxy != undefined) {
    proxy.sendMessageRequest(1, data, reply, option)
    .then((result: rpc.RequestResult) => {
      if (result.errCode === 0) {
        hilog.info(0x0000, 'testTag', 'sendMessageRequest got result');
        let num = result.reply.readInt();
        let msg = result.reply.readString();
        hilog.info(0x0000, 'testTag', 'reply num: ' + num);
        hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
      } else {
        hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, errCode: ' + result.errCode);
      }
    }).catch((e: Error) => {
      hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, error: ' + JSON.stringify(e));
    }).finally (() => {
      hilog.info(0x0000, 'testTag', 'sendMessageRequest ends, reclaim parcel');
      data.reclaim();
      reply.reclaim();
    });
  }
} catch (error) {
  hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, error: ' + error);
}
```

## sendMessageRequest

ArkTS-Dyn:
```TypeScript
sendMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption,
      callback: AsyncCallback<RequestResult>
    ): void
```

ArkTS-Sta:
```TypeScript
sendMessageRequest(
      code: int,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption,
      callback: AsyncCallback<RequestResult>
    ): void
```

以同步或异步方式向对端进程发送MessageSequence消息。使用callback异步回调。如果为选项设置了异步模式，则立即收到回调，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，将 在 [sendMessageRequest]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 返回后、服务端处理请求完成时执行回调，回调中可读取[RequestResult]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_获取服务端返回的数据。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-RemoteProxy-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callback: AsyncCallback<RequestResult>    ): void--><!--Device-RemoteProxy-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callback: AsyncCallback<RequestResult>    ): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageSequence对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageSequence对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RequestResult&gt; | 是 | 回调函数。当消息发送成功时，可从RequestResult中读取服务端返回的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.The number of parameters is incorrect;2.The parameter type does not match;3.Failed to obtain the passed object instance. |

## sendRequest

```TypeScript
sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean
```

以同步或异步方式向对端进程发送MessageParcel消息。如果为选项设置了异步模式，则立即返回，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则将在sendRequest返回时收到回 复，回复内容在reply报文里。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 8

**替代接口：** [rpc.IRemoteObject#sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code:

<!--Device-RemoteProxy-sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean--><!--Device-RemoteProxy-sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageParcel对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageParcel对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：发送成功，false：发送失败。 |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的sendRequest接口方法发送消息

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString("hello");
  if (proxy != undefined) {
    let ret: boolean = proxy.sendRequest(1, data, reply, option);
    if (ret) {
      hilog.info(0x0000, 'testTag', 'sendRequest got result');
      let msg = reply.readString();
      hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
    } else {
      hilog.error(0x0000, 'testTag', 'sendRequest failed');
    }
    hilog.info(0x0000, 'testTag', 'sendRequest ends, reclaim parcel');
    data.reclaim();
    reply.reclaim();
  }
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

## sendRequest

```TypeScript
sendRequest(
      code: number,
      data: MessageParcel,
      reply: MessageParcel,
      options: MessageOption
    ): Promise<SendRequestResult>
```

以同步或异步方式向对端进程发送MessageParcel消息。如果为选项设置了异步模式，则发送请求的响应结果立即返回，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则发送请求的响应结果将 在sendRequest返回时返回，回复内容在reply报文里。使用Promise异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [rpc.IRemoteObject#sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code:

<!--Device-RemoteProxy-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption    ): Promise<SendRequestResult>--><!--Device-RemoteProxy-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption    ): Promise<SendRequestResult>-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageParcel对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageParcel对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SendRequestResult&gt; | Promise对象，返回发送请求的响应结果。 |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的sendRequest接口方法发送消息

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString("hello");
  if (proxy != undefined) {
    let a = proxy.sendRequest(1, data, reply, option) as Object;
    let b = a as Promise<rpc.SendRequestResult>;
    b.then((result: rpc.SendRequestResult) => {
      if (result.errCode === 0) {
        hilog.info(0x0000, 'testTag', 'sendRequest got result');
        let num = result.reply.readInt();
        let msg = result.reply.readString();
        hilog.info(0x0000, 'testTag', 'reply num: ' + num);
        hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
      } else {
        hilog.error(0x0000, 'testTag', 'sendRequest failed, errCode: ' + result.errCode);
      }
    }).catch((e: Error) => {
      hilog.error(0x0000, 'testTag', 'sendRequest failed, error: ' + JSON.stringify(e));
    }).finally (() => {
      hilog.info(0x0000, 'testTag', 'sendRequest ends, reclaim parcel');
      data.reclaim();
      reply.reclaim();
    });
  }
} catch (error) {
  hilog.error(0x0000, 'testTag', 'sendRequest failed, error: ' + error);
}
```

## sendRequest

```TypeScript
sendRequest(
      code: number,
      data: MessageParcel,
      reply: MessageParcel,
      options: MessageOption,
      callback: AsyncCallback<SendRequestResult>
    ): void
```

以同步或异步方式向对端进程发送MessageParcel消息。如果为选项设置了异步模式，则立即收到回调，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则将在sendRequest返回时收 到回调，回复内容在reply报文里。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [rpc.IRemoteObject#sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code:

<!--Device-RemoteProxy-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption,      callback: AsyncCallback<SendRequestResult>    ): void--><!--Device-RemoteProxy-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption,      callback: AsyncCallback<SendRequestResult>    ): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageParcel对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageParcel对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SendRequestResult&gt; | 是 | 接收发送结果的回调。 |

## unregisterDeathRecipient

ArkTS-Dyn:
```TypeScript
unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void
```

ArkTS-Sta:
```TypeScript
unregisterDeathRecipient(recipient: DeathRecipient, flags: int): void
```

注销用于接收远程对象死亡通知的回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-RemoteProxy-unregisterDeathRecipient(recipient: DeathRecipient, flags: int): void--><!--Device-RemoteProxy-unregisterDeathRecipient(recipient: DeathRecipient, flags: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要注销的回调。 |
| flags | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 死亡通知标志。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.The number of parameters is incorrect;2.The parameter type does not match;3.The callback used to receive remote object death notifications is empty. |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |

**示例：**

在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// FA模型需要从@kit.AbilityKit导入featureAbility
// import { featureAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let proxy: rpc.IRemoteObject | undefined;
let connect: common.ConnectOptions = {
  onConnect: (elementName, remoteProxy) => {
    hilog.info(0x0000, 'testTag', 'js onConnect called');
    proxy = remoteProxy;
  },
  onDisconnect: (elementName) => {
    hilog.info(0x0000, 'testTag', 'onDisconnect');
  },
  onFailed: () => {
    hilog.info(0x0000, 'testTag', 'onFailed');
  }
};
let want: Want = {
  // 获取服务端包名和ability名称
  bundleName: "com.ohos.server",
  abilityName: "com.ohos.server.EntryAbility",
};

// FA模型使用此方法连接服务
// FA.connectAbility(want,connect);

// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let context: common.UIAbilityContext = this.getUIContext().getHostContext(); // UIAbilityContext
// 建立连接后返回的Id需要保存下来，在解绑服务时需要作为参数传入
let connectionId = context.connectServiceExtensionAbility(want, connect);
```

上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的unregisterDeathRecipient接口方法注销死亡回调

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
if (proxy != undefined) {
  try {
    let deathRecipient = new MyDeathRecipient();
    proxy.registerDeathRecipient(deathRecipient, 0);
    proxy.unregisterDeathRecipient(deathRecipient, 0);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    hilog.error(0x0000, 'testTag', 'proxy unregister deathRecipient fail, errorCode ' + e.code);
    hilog.error(0x0000, 'testTag', 'proxy unregister deathRecipient fail, errorMessage ' + e.message);
  }
}
```

## DUMP_TRANSACTION

```TypeScript
static readonly DUMP_TRANSACTION: number
```

内部指令码，获取IPC服务相关的状态信息。

**类型：** number

**默认值：** 1598311760

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-RemoteProxy-static readonly DUMP_TRANSACTION: number--><!--Device-RemoteProxy-static readonly DUMP_TRANSACTION: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## INTERFACE_TRANSACTION

```TypeScript
static readonly INTERFACE_TRANSACTION: number
```

内部指令码，获取对端接口描述符。

**类型：** number

**默认值：** 1598968902

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-RemoteProxy-static readonly INTERFACE_TRANSACTION: number--><!--Device-RemoteProxy-static readonly INTERFACE_TRANSACTION: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## MAX_TRANSACTION_ID

```TypeScript
static readonly MAX_TRANSACTION_ID: number
```

最大有效指令码。

**类型：** number

**默认值：** 0x00FFFFFF

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-RemoteProxy-static readonly MAX_TRANSACTION_ID: number--><!--Device-RemoteProxy-static readonly MAX_TRANSACTION_ID: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## MIN_TRANSACTION_ID

```TypeScript
static readonly MIN_TRANSACTION_ID: number
```

最小有效指令码。

**类型：** number

**默认值：** 0x1

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-RemoteProxy-static readonly MIN_TRANSACTION_ID: number--><!--Device-RemoteProxy-static readonly MIN_TRANSACTION_ID: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## PING_TRANSACTION

```TypeScript
static readonly PING_TRANSACTION: number
```

内部指令码，用于测试IPC服务是否正常。

**类型：** number

**默认值：** 1599098439

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-RemoteProxy-static readonly PING_TRANSACTION: number--><!--Device-RemoteProxy-static readonly PING_TRANSACTION: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

