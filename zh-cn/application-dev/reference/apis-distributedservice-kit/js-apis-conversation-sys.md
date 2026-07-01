# @ohos.distributedSoftbus.conversation
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wangrui7-->
<!--Designer: @yangyang2-->
<!--Tester: @Ytt-test-->
<!--Adviser: @hu-zhiqiong-->

conversation模块通过软总线能力，为Agent提供多设备交互能力。提供基础的Agent互联工具，包括获取设备列表、唤醒设备和发送消息。通过本模块，应用可以获取同一账号下的可信设备，注册监听以接收跨设备消息，并通过会话通道向指定设备发送消息。

> **说明：**
>
> 本模块首批接口从API version 26.1.0开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口为系统接口，仅可在Stage模型下使用。

## 导入模块

```js
import { conversation } from '@kit.DistributedServiceKit';
```

## conversation.getTrustedDevices

getTrustedDevices(): DeviceNodeInfo[]

获取所有可信设备的设备信息。返回所有同账号可信设备列表。

**需要权限**：ohos.permission.DISTRIBUTED_DATASYNC 和 ohos.permission.sec.ACCESS_UDID

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**返回值：**

| 类型                  | 说明               |
| ------------------- | ---------------- |
| [DeviceNodeInfo[]](#devicenodeinfo) | 获取到的设备信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|

**示例：**

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "conversationDemo";

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

向指定设备发送会话数据。通过目标设备的networkId或udid标识目标设备，消息将发送到远端设备指定包名和Ability名的应用。

**需要权限**：ohos.permission.DISTRIBUTED_DATASYNC 和 ohos.permission.sec.ACCESS_UDID

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                       | 必填   | 说明       |
| --------- | ---------------------------------------- | ---- | -------- |
| deviceId  | string  | 是    | 目标设备的networkId或udid。可通过调用[getTrustedDevices()](#conversationgettrusteddevices)获取。  |
| bundleName | string  | 是    | 消息发送目标包名，需与远端设备上已注册会话监听的应用包名一致。  |
| abilityName | string  | 是    | 消息发送目标Ability名，需与远端设备上已注册会话监听的Ability名一致。  |
| msg | ArrayBuffer  | 是    | 要发送的消息内容。  |

**返回值：**

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 401      | Invalid parameter. The deviceId, bundleName, abilityName or msg is invalid or empty.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|
| 2004001  | Remote not support.|
| 2004002  | Duplicate calls, previous call still in progress.|
| 2004003  | Send data failed.|
| 2004004  | Wait remote ack timeout.|

**示例：**

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "conversationDemo";

try {
  let deviceId: string = "device_network_id_or_udid";
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

注册会话监听，接收来自可信设备的消息。注册后，当指定包名和Ability名收到消息时，将调用指定的回调函数。同一包名和Ability名只能注册一个监听器，重复注册将替换之前已注册的监听器。

**需要权限**：ohos.permission.DISTRIBUTED_DATASYNC 和 ohos.permission.sec.ACCESS_UDID

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                       | 必填   | 说明       |
| --------- | ---------------------------------------- | ---- | -------- |
| bundleName  | string  | 是    | 接收消息的包名，需与本应用的包名一致。  |
| abilityName | string  | 是    | 接收消息的Ability名，需与本应用中的Ability名一致。  |
| dataCallback | [DataCallback](#datacallback)  | 是    | 收到消息时的回调函数。  |

**错误码：**

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 401      | Invalid parameter. The bundleName, abilityName or dataCallback is invalid or empty.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|

**示例：**

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "conversationDemo";

try {
  let bundleName: string = "com.example.demo";
  let abilityName: string = "EntryAbility";

  conversation.registerConversationListener(bundleName, abilityName, (networkId: string, msg: ArrayBuffer) => {
    hilog.info(0x0000, TAG, 'received message from networkId = ' + networkId + ', msg length = ' + msg.byteLength);
  });
  hilog.info(0x0000, TAG, 'registerConversationListener success');
} catch (err) {
  hilog.error(0x0000, TAG, 'registerConversationListener errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## conversation.unregisterConversationListener

unregisterConversationListener(bundleName:&nbsp;string,&nbsp;abilityName:&nbsp;string):&nbsp;void

取消注册指定包名和Ability名的会话监听。调用此接口后，应用将不再接收消息。如果之前没有向指定包名和Ability名的应用注册过监听器，此接口返回成功。

**需要权限**：ohos.permission.DISTRIBUTED_DATASYNC 和 ohos.permission.sec.ACCESS_UDID

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                       | 必填   | 说明       |
| --------- | ---------------------------------------- | ---- | -------- |
| bundleName  | string  | 是    | 要取消监听的包名。  |
| abilityName | string  | 是    | 要取消监听的Ability名。  |

**错误码：**

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201      | Permission denied. The application does not have the required permission to access distributed data.|
| 202      | Permission verification failed. A non-system application calls a system API.|
| 401      | Invalid parameter. The bundleName or abilityName is invalid or empty.|
| 801      | Capability not supported.|
| 2000001  | Internal error.|

**示例：**

```ts
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "conversationDemo";

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

设备节点信息，包括networkId、设备名称、设备类型、近场状态和udid。

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

| 名称                    | 类型       |只读   | 可选   | 说明                 |
| ----------------- | ------ | ----  | ---- | ------------------ |
| networkId          | string | 否    |否    | 设备的networkId，在分布式网络中唯一标识一台设备的可变标识符，用于发送消息时的设备寻址。     |
| deviceName           | string | 否    |否   | 设备名称。 |
| deviceTypeId            | int | 否    |否    | 设备类型标识符，表示设备的类别（如手机、平板、电视、穿戴设备等）。 |
| nearby            | boolean | 否    |否    | 设备是否在近场。 |
| udid            | string | 否    |否    | 设备的UDID，唯一标识一台设备，用于发送消息时的设备寻址。 |

## DataCallback

消息接收回调函数类型。

**(networkId: string, msg: ArrayBuffer): void**

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                       | 必填   | 说明       |
| --------- | ---------------------------------------- | ---- | -------- |
| networkId  | string  | 是    | 发送消息的源设备的networkId。  |
| msg | ArrayBuffer  | 是    | 接收到的消息内容。  |
