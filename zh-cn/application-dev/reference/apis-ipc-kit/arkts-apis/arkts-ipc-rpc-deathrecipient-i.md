# DeathRecipient

用于订阅远端对象的死亡通知。当被订阅该通知的远端对象死亡时，本端可收到消息，调用[onRemoteDied](#onremotedied)接口。 远端对象死亡可以为远端对象所在进程死亡，远端对象所在设备关机或重启，当远端对象与本端对象属于不同设备时，也可为远端对象离开组网时。

**起始版本：** 23

<!--Device-rpc-interface DeathRecipient--><!--Device-rpc-interface DeathRecipient-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## 导入模块

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## onRemoteDied

```TypeScript
onRemoteDied(): void
```

在成功添加死亡通知订阅后，当远端对象死亡时，将自动调用本方法。

**起始版本：** 7

<!--Device-DeathRecipient-onRemoteDied(): void--><!--Device-DeathRecipient-onRemoteDied(): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
```

## onRemoteDied

```TypeScript
onRemoteDied: OnRemoteDiedFunc
```

接收到远程对象的死亡通知时执行后续操作。

**类型：** [OnRemoteDiedFunc](arkts-ipc-rpc-onremotediedfunc-t.md)

**起始版本：** 23

<!--Device-DeathRecipient-onRemoteDied: OnRemoteDiedFunc--><!--Device-DeathRecipient-onRemoteDied: OnRemoteDiedFunc-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

