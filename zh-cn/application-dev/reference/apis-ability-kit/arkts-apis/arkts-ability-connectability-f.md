# connectAbility

## connectAbility

```TypeScript
function connectAbility(request: Want, options: ConnectOptions): number
```

将当前ability与指定的ServiceAbility进行连接。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（FA模型）](../../../../application-models/component-startup-rules-fa.md)。
> > 跨应用连接serviceAbility，对端应用需配置关联启动。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | Want | 是 | 表示被连接的ServiceAbility。 |
| options | ConnectOptions | 是 | 连接回调方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 连接的ServiceAbility的ID(ID从0开始自增，每连接成功一次ID加1)。 |

**示例：**

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

let connId = particleAbility.connectAbility(
  {
    bundleName: 'com.ix.ServiceAbility',
    abilityName: 'ServiceAbilityA',
  },
  {
    onConnect: (element, remote) => {
      console.info(`ConnectAbility onConnect remote is proxy: ${(remote instanceof rpc.RemoteProxy)}`);
    },
    onDisconnect: (element) => {
      console.info(`ConnectAbility onDisconnect element.deviceId: ${element.deviceId}`);
    },
    onFailed: (code) => {
      console.error(`particleAbilityTest ConnectAbility onFailed errCode: ${code}`);
    },
  },
);

particleAbility.disconnectAbility(connId).then((data) => {
  console.info(`data: ${data}`);
}).catch((error: BusinessError) => {
  console.error(`particleAbilityTest result errCode: ${error.code}`);
});

```

