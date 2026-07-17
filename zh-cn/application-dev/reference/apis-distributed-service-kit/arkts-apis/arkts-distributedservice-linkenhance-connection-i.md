# Connection

连接对象，提供连接、断连、获取对端设备ID、发送数据、注册/取消注册回调等方法。

**起始版本：** 20

<!--Device-linkEnhance-interface Connection--><!--Device-linkEnhance-interface Connection-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
```

## close

```TypeScript
close(): void
```

业务执行完毕后，任意设备可调用该接口销毁connection对象，释放资源。若需再次与对端设备交互，必须重新创建connection对象并调用`connect()`发起连接。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Connection-close(): void--><!--Device-Connection-close(): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
    if (result.success) {
      connection.close();
    }
  });
  connection.connect();
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## connect

```TypeScript
connect(): void
```

在客户端执行，向服务端设备发起连接，最大连接个数限制为10。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Connection-connect(): void--><!--Device-Connection-connect(): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390204](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390204-连接个数超出限制) | The number of connection exceeds the limit. |
| [32390300](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390300-内部错误) | Internal error. |

**示例：**

客户端设备上的应用在创建Connection对象成功后，调用connect()方法连接目标设备（即服务端）。

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  // 订阅连接结果
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
  });
  // 发起连接
  connection.connect();
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## disconnect

```TypeScript
disconnect(): void
```

业务执行完毕后，双端任意设备可调用该接口断开连接。创建的connection对象仍有效，需要时可调用connect()重新连接。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Connection-disconnect(): void--><!--Device-Connection-disconnect(): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
    if (result.success) {
      connection.disconnect();
    }
  });
  connection.connect();
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## getPeerDeviceId

```TypeScript
getPeerDeviceId(): string
```

获取对端设备的deviceId，作为对端设备的标识符，连接成功后或者被连接成功后调用。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Connection-getPeerDeviceId(): string--><!--Device-Connection-getPeerDeviceId(): string-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 对端设备的deviceId，即对端设备的BLE MAC地址。如果获取失败返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  hilog.info(0x0000, TAG, "peerDeviceId=%{public}s", connection.getPeerDeviceId());
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## off('connectResult')

```TypeScript
off(type: 'connectResult', callback?: Callback<ConnectResult>): void
```

取消connect事件的回调监听，使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Connection-off(type: 'connectResult', callback?: Callback<ConnectResult>): void--><!--Device-Connection-off(type: 'connectResult', callback?: Callback<ConnectResult>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connectResult' | 是 | 事件回调类型，支持的事件为'connectResult'，完成`connect()`调用，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ConnectResult> | 否 | 注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390206](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390206-参数非法) | Invalid parameter. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
  });
  // 取消订阅连接结果
  connection.off('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## off('disconnected')

```TypeScript
off(type: 'disconnected', callback?: Callback<number>): void
```

取消注册disconnected事件的回调监听。连接被动断开或底层异常断开时触发该事件，使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Connection-off(type: 'disconnected', callback?: Callback<number>): void--><!--Device-Connection-off(type: 'disconnected', callback?: Callback<number>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'disconnected' | 是 | 事件回调类型，支持的事件为'disconnected'，连接被动断开或底层异常断开时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<number> | 否 | 注册的回调函数，number为返回的错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390206](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390206-参数非法) | Invalid parameter. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  connection.on('disconnected', (number: number) => {
    hilog.info(0x0000, TAG, 'connection disconnected reason = ' + number);
  });
  // 取消订阅断连通知
  connection.off('disconnected', (number: number) => {
    hilog.info(0x0000, TAG, 'connection disconnected reason = ' + number);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## off('dataReceived')

```TypeScript
off(type: 'dataReceived', callback?: Callback<ArrayBuffer>): void
```

取消dataReceived事件的回调监听，使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Connection-off(type: 'dataReceived', callback?: Callback<ArrayBuffer>): void--><!--Device-Connection-off(type: 'dataReceived', callback?: Callback<ArrayBuffer>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'dataReceived' | 是 | 事件回调类型，支持的事件为'dataReceived'，收到数据时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ArrayBuffer> | 否 | 注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390206](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390206-参数非法) | Invalid parameter. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  // 订阅数据接收通知
  connection.on('dataReceived', (data: ArrayBuffer) => {
    hilog.info(0x0000, TAG, 'recv dataLen = ' + data.byteLength);
  });
  // 取消数据接收通知
  connection.off('dataReceived', (data: ArrayBuffer) => {
    hilog.info(0x0000, TAG, 'recv dataLen = ' + data.byteLength);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## on('connectResult')

```TypeScript
on(type: 'connectResult', callback: Callback<ConnectResult>): void
```

注册connect事件的回调监听，通过回调函数获取连接结果。使用callback进行异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Connection-on(type: 'connectResult', callback: Callback<ConnectResult>): void--><!--Device-Connection-on(type: 'connectResult', callback: Callback<ConnectResult>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connectResult' | 是 | 事件回调类型，支持的事件为'connectResult'，完成`connect()`调用，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ConnectResult> | 是 | 注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390206](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390206-参数非法) | Invalid parameter. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  // 订阅连接结果
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
  });

  // 发起连接
  connection.connect();
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## on('disconnected')

```TypeScript
on(type: 'disconnected', callback: Callback<number>): void
```

注册disconnected事件的回调监听，连接被动断开或者底层异常断开时触发该事件。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Connection-on(type: 'disconnected', callback: Callback<number>): void--><!--Device-Connection-on(type: 'disconnected', callback: Callback<number>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'disconnected' | 是 | 事件回调类型，支持的事件为'disconnected'，连接被动断开或底层异常断开时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<number> | 是 | 注册的回调函数，number为返回的错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390206](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390206-参数非法) | Invalid parameter. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  // 订阅断连通知
  connection.on('disconnected', (number: number) => {
    hilog.info(0x0000, TAG, 'connection disconnected reason = ' + number);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## on('dataReceived')

```TypeScript
on(type: 'dataReceived', callback: Callback<ArrayBuffer>): void
```

注册dataReceived事件的回调监听。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Connection-on(type: 'dataReceived', callback: Callback<ArrayBuffer>): void--><!--Device-Connection-on(type: 'dataReceived', callback: Callback<ArrayBuffer>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'dataReceived' | 是 | 事件回调类型，支持的事件为'dataReceived'，收到数据时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ArrayBuffer> | 是 | 注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390206](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390206-参数非法) | Invalid parameter. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  // 发起连接
  connection.connect();
  // 订阅数据接收通知
  connection.on('dataReceived', (data: ArrayBuffer) => {
    hilog.info(0x0000, TAG, 'recv dataLen = ' + data.byteLength);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## sendData

```TypeScript
sendData(data: ArrayBuffer): void
```

客户端连接成功后，可以向服务端发送数据。服务端接收到连接回调时，也可以向客户端发送数据。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Connection-sendData(data: ArrayBuffer): void--><!--Device-Connection-sendData(data: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 需要发送的数据，最大发送长度为1024字节。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390206](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390206-参数非法) | Invalid parameter. |
| [32390205](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390205-连接状态不可用) | Connection is not ready. |
| [32390300](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390300-内部错误) | Internal error. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
    if (result.success) {
      let len = 1;
      let arrayBuffer = new ArrayBuffer(len); // 创建需要发送的数据
      connection.sendData(arrayBuffer);
      hilog.info(0x0000, TAG, "sendData data connection peerDeviceId=%{public}s", connection.getPeerDeviceId());
      connection.disconnect();
    }
  });
  connection.connect();
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

