# @ohos.distributedSoftbus.conversation (跨设备唤醒与消息传输)(系统接口)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wangrui7-->
<!--Designer: @yangyang2-->
<!--Tester: @Ytt-test-->
<!--Adviser: @hu-zhiqiong-->

conversation模块基于分布式软总线，为应用提供跨设备交互能力，包括获取可信设备列表、发送和接收会话数据。通过本模块，应用可以获取同一账号下的可信设备，注册监听器以接收跨设备数据，并通过会话通道向指定设备发送数据。适用于需要跨设备协作和多设备数据传递的场景，可降低跨设备交互的开发复杂度。

**起始版本：** 26.1.0

> **说明**：
>
> 本模块接口为系统接口，仅可在Stage模型下使用。

## 导入模块

```js
import { conversation } from '@kit.DistributedServiceKit';
```

## conversation.getTrustedDevices

getTrustedDevices(): DeviceNodeInfo[]

获取所有同账号可信设备信息。典型使用场景包括：跨设备数据发送前查询可用目标设备。

**需要权限**：ohos.permission.DISTRIBUTED_DATASYNC 和 ohos.permission.sec.ACCESS_UDID

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| [DeviceNodeInfo[]](#devicenodeinfo) | 获取到的设备信息列表。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[跨设备唤醒与消息传输错误码](errorcode-conversation.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|

**示例**：

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = 'conversationDemo';

try {
  let devices: conversation.DeviceNodeInfo[] = conversation.getTrustedDevices();
  hilog.info(0x0000, TAG, 'trusted devices count = ' + devices.length);
  for (let device of devices) {
    hilog.info(0x0000, TAG, 'device name = ' + device.deviceName + ', networkId = ' + device.networkId);
  }
} catch (err) {
  hilog.error(0x0000, TAG, 'getTrustedDevices errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## conversation.postConversationData

postConversationData(deviceId:&nbsp;string,&nbsp;bundleName:&nbsp;string,&nbsp;abilityName:&nbsp;string,&nbsp;msg:&nbsp;ArrayBuffer):&nbsp;Promise&lt;void&gt;

向目标设备发送会话数据。目标设备须为同一账号下的可信设备，数据通过分布式软总线会话通道发送，以目标设备的networkId或UDID进行设备寻址，路由至远端设备上与指定包名和Ability名匹配的已注册监听应用。典型使用场景包括：跨设备协同指令发送。

**需要权限**：ohos.permission.DISTRIBUTED_DATASYNC 和 ohos.permission.sec.ACCESS_UDID

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**参数**：

| 参数名       | 类型                                       | 必填   | 说明       |
| --------- | ---------------------------------------- | ---- | -------- |
| deviceId  | string  | 是    | 目标设备的networkId或UDID。可通过调用[getTrustedDevices()](#conversationgettrusteddevices)获取。传入无效值时返回错误码401。  |
| bundleName | string  | 是    | 数据发送目标包名，需与远端设备上通过[registerConversationListener](#conversationregisterconversationlistener)注册会话监听的应用包名一致。不满足此要求时，数据将无法送达目标应用。传入无效或空值时返回错误码401。  |
| abilityName | string  | 是    | 数据发送目标Ability名，需与远端设备上已注册会话监听的Ability名一致。不满足此要求时，数据将无法送达目标应用。传入无效或空值时返回错误码401。  |
| msg | ArrayBuffer  | 是    | 要发送的数据内容，为ArrayBuffer格式的二进制数据，不能为空。数据结构由应用层协议定义。传入空数据或无效数据时返回错误码401。  |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象。resolve表示发送会话数据成功，reject表示发送失败并返回错误信息。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[跨设备唤醒与消息传输错误码](errorcode-conversation.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 401      | Invalid parameter. The deviceId, bundleName, abilityName or msg is invalid or empty.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|
| 2004001  | Remote not supported.|
| 2004002  | Duplicate calls, previous call still in progress.|
| 2004003  | Send data failed.|
| 2004004  | Wait remote ack timeout.|

**示例**：

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = 'conversationDemo';

try {
  let deviceId: string = "device_network_id_or_udid"; // deviceId需通过调用conversation.getTrustedDevices()获取目标设备的networkId或UDID
  let bundleName: string = "com.example.demo";
  let abilityName: string = "EntryAbility";
  let msg: ArrayBuffer = new ArrayBuffer(10);
  let view = new Uint8Array(msg);
  view[0] = 1;

  conversation.postConversationData(deviceId, bundleName, abilityName, msg).then(() => {
    hilog.info(0x0000, TAG, 'postConversationData success');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, TAG, 'postConversationData errCode: ' + err.code + ', errMessage: ' + err.message);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'postConversationData errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## conversation.registerConversationListener

registerConversationListener(bundleName:&nbsp;string,&nbsp;abilityName:&nbsp;string,&nbsp;dataCallback:&nbsp;DataCallback):&nbsp;void

注册会话监听，接收来自同一账号下可信设备的数据。当远端设备通过分布式软总线会话通道发送数据到达本地设备后，软总线将数据分发至与包名和Ability名匹配的已注册回调函数。同一包名和Ability名只能注册一个监听器，重复注册将覆盖之前已注册的监听器。

**配对调用**：需与[unregisterConversationListener](#conversationunregisterconversationlistener)配对使用，在不再需要接收消息时应调用注销监听器以释放资源，未注销可能导致资源持续占用。

**需要权限**：ohos.permission.DISTRIBUTED_DATASYNC 和 ohos.permission.sec.ACCESS_UDID

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**参数**：

| 参数名       | 类型                                       | 必填   | 说明       |
| --------- | ---------------------------------------- | ---- | -------- |
| bundleName  | string  | 是    | 接收数据的包名，需与本应用的包名一致。不满足此要求时，监听器可能无法正确接收数据。传入无效或空值时返回错误码401。  |
| abilityName | string  | 是    | 接收数据的Ability名，需与本应用中的Ability名一致。不满足此要求时，监听器可能无法正确接收数据。传入无效或空值时返回错误码401。  |
| dataCallback | [DataCallback](#datacallback)  | 是    | 收到数据时的回调函数，用于接收跨设备数据。传入无效值时返回错误码401。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[跨设备唤醒与消息传输错误码](errorcode-conversation.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 401      | Invalid parameter. The bundleName, abilityName or dataCallback is invalid or empty.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|

**示例**：

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = 'conversationDemo';

try {
  let bundleName: string = "com.example.demo";
  let abilityName: string = "EntryAbility";

  conversation.registerConversationListener(bundleName, abilityName, (deviceId: string, msg: ArrayBuffer) => {
    hilog.info(0x0000, TAG, 'received message from deviceId = ' + deviceId + ', msg length = ' + msg.byteLength);
  });
  hilog.info(0x0000, TAG, 'registerConversationListener success');
} catch (err) {
  hilog.error(0x0000, TAG, 'registerConversationListener errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## conversation.unregisterConversationListener

unregisterConversationListener(bundleName:&nbsp;string,&nbsp;abilityName:&nbsp;string):&nbsp;void

注销指定包名和Ability名的会话监听。需与[registerConversationListener](#conversationregisterconversationlistener)配对使用，用于注销已注册的会话监听器。同一包名和Ability名只能注册一个监听器，重复注册会覆盖之前的监听器，注销后将移除当前生效的监听器。调用此接口后，应用将不再接收对应包名和Ability名的会话数据。如果之前未注册过指定包名和Ability名的监听器，此接口同样返回成功。

**需要权限**：ohos.permission.DISTRIBUTED_DATASYNC 和 ohos.permission.sec.ACCESS_UDID

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**参数**：

| 参数名       | 类型                                       | 必填   | 说明       |
| --------- | ---------------------------------------- | ---- | -------- |
| bundleName  | string  | 是    | 要取消监听的包名，需与注册监听时使用的包名一致。传入无效或空值时返回错误码401。  |
| abilityName | string  | 是    | 要取消监听的Ability名，需与注册监听时使用的Ability名一致。传入无效或空值时返回错误码401。  |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[跨设备唤醒与消息传输错误码](errorcode-conversation.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 401      | Invalid parameter. The bundleName or abilityName is invalid or empty.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|

**示例**：

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = 'conversationDemo';

try {
  let bundleName: string = "com.example.demo";
  let abilityName: string = "EntryAbility";

  conversation.unregisterConversationListener(bundleName, abilityName);
  hilog.info(0x0000, TAG, 'unregisterConversationListener success');
} catch (err) {
  hilog.error(0x0000, TAG, 'unregisterConversationListener errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## DeviceNodeInfo

设备节点信息，包括networkId、设备名称、设备类型标识符、近场状态和UDID。

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

| 名称                    | 类型       |只读   | 可选   | 说明                 |
| ----------------- | ------ | ----  | ---- | ------------------ |
| networkId          | string | 否    |否    | 设备的networkId，在分布式网络中唯一标识一台设备，用于发送数据时的设备寻址。与UDID互为替代标识，发送数据时可任选其一。     |
| deviceName           | string | 否    |否   | 设备名称。 |
| deviceTypeId            | number | 否    |否    | 设备类型标识符，表示设备的类别，取值为整数（如手机、平板、电视、穿戴设备等对应的类型标识值）。 |
| nearby            | boolean | 否    |否    | 设备是否在近场。true表示设备在近场，false表示设备不在近场。 |
| udid            | string | 否    |否    | 设备的UDID，唯一标识一台设备，用于发送数据时的设备寻址。与networkId不同，UDID为设备的永久唯一标识，不随网络拓扑变化而改变，两者互为替代标识，发送数据时可任选其一。 |

## DataCallback

数据接收回调函数类型。

**(deviceId: string, msg: ArrayBuffer): void**

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**参数**：

| 参数名       | 类型                                       | 必填   | 说明       |
| --------- | ---------------------------------------- | ---- | -------- |
| deviceId  | string  | 是    | 发送数据的源设备的networkId或UDID。  |
| msg | ArrayBuffer  | 是    | 接收到的数据内容，为ArrayBuffer格式的二进制数据，数据格式与发送端发送的数据格式一致，由应用层协议定义。  |
