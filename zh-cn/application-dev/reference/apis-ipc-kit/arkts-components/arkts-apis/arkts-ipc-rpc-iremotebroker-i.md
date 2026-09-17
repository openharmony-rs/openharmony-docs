# IRemoteBroker

远端对象的代理持有者。用于获取代理对象。

**起始版本：** 7

**系统能力：** SystemCapability.Communication.IPC.Core

## 导入模块

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## asObject

```TypeScript
asObject(): IRemoteObject
```

需派生类实现，获取代理或远端对象。

**起始版本：** 7

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md) | 如果调用者是RemoteObject对象，则直接返回本身；如果调用者是[RemoteProxy](arkts-ipc-rpc-remoteproxy-c.md)对象，则返回它的持有者[IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';

class TestAbility extends rpc.RemoteObject {
  asObject() {
    return this;
  }
}
let remoteObject = new TestAbility('testObject').asObject();
```

```TypeScript
> 说明：
> 
> 在本文档的示例中，通过this.getUIContext().getHostContext()来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。
```

```TypeScript
上述onConnect回调函数中的proxy对象需要等ability异步连接成功后才会被赋值，然后才可调用proxy对象的asObject接口方法获取代理或远端对象
```
