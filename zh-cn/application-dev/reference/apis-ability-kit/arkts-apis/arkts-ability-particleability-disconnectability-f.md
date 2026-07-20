# disconnectAbility

## 导入模块

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
```

<a id="disconnectability"></a>
## disconnectAbility

```TypeScript
function disconnectAbility(connection: number, callback: AsyncCallback<void>): void
```

断开当前ability与指定ServiceAbility的连接。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-particleAbility-function disconnectAbility(connection: number, callback: AsyncCallback<void>): void--><!--Device-particleAbility-function disconnectAbility(connection: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | number | 是 | 表示断开连接的ServiceAbility的ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当断开当前ability与指定ServiceAbility的连接成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

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

particleAbility.disconnectAbility(connId, (err) => {
  console.error(`particleAbilityTest disconnectAbility err: ${JSON.stringify(err)}`);
});

```


<a id="disconnectability-1"></a>
## disconnectAbility

```TypeScript
function disconnectAbility(connection: number): Promise<void>
```

断开当前ability与指定ServiceAbility的连接。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-particleAbility-function disconnectAbility(connection: number): Promise<void>--><!--Device-particleAbility-function disconnectAbility(connection: number): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | number | 是 | 表示断开连接的ServiceAbility的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

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

particleAbility.disconnectAbility(connId).then(() => {
  console.info('disconnectAbility success');
}).catch((error: BusinessError) => {
  console.error(`particleAbilityTest result errCode : ${error.code}`);
});

```

