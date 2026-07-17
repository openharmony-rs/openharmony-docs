# Server

服务对象，提供启动服务、停止服务、关闭服务、注册/取消注册服务端回调等方法。

**起始版本：** 20

<!--Device-linkEnhance-interface Server--><!--Device-linkEnhance-interface Server-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
```

## close

```TypeScript
close(): void
```

当业务执行完毕，服务端清理资源时，调用close()方法，销毁Server对象，释放相关资源。之后如果再次与对端设备交互，需要重新创建Server对象。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Server-close(): void--><!--Device-Server-close(): void-End-->

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
  let name: string = "demo";
  hilog.info(0x0000, TAG, 'start server name = ' + name);
  let server: linkEnhance.Server = linkEnhance.createServer(name);
  server.start();
  server.close();
} catch (err) {
  hilog.error(0x0000, TAG, 'start server errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## off('connectionAccepted')

```TypeScript
off(type: 'connectionAccepted', callback?: Callback<Connection>): void
```

取消注册connectionAccepted事件的回调监听。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Server-off(type: 'connectionAccepted', callback?: Callback<Connection>): void--><!--Device-Server-off(type: 'connectionAccepted', callback?: Callback<Connection>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connectionAccepted' | 是 | 事件回调类型，支持的事件为'connectionAccepted'，收到对端连接，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<Connection> | 否 | 注册的回调函数。[Connection](arkts-distributedservice-linkenhance-connection-i.md)返回的连接对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390206](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390206-参数非法) | Parameter invalid. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let name: string = "demo";
  hilog.info(0x0000, TAG, 'start server name = ' + name);
  // 使用服务名构造Server
  let server: linkEnhance.Server = linkEnhance.createServer(name);
  server.on('connectionAccepted', (connection: linkEnhance.Connection): void => {
    hilog.info(0x0000, TAG, 'accept new connection');
  });
  // 取消订阅服务接收
  server.off('connectionAccepted', (connection: linkEnhance.Connection): void => {
    hilog.info(0x0000, TAG, 'accept new connection');
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'start server errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## off('serverStopped')

```TypeScript
off(type: 'serverStopped', callback?: Callback<number>): void
```

取消注册serverStopped事件的回调监听。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Server-off(type: 'serverStopped', callback?: Callback<number>): void--><!--Device-Server-off(type: 'serverStopped', callback?: Callback<number>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serverStopped' | 是 | 事件回调类型，支持的事件为'serverStopped'，底层服务异常时触发。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<number> | 否 | 注册的回调函数，number为返回的错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390206](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390206-参数非法) | Parameter invalid. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let name: string = "demo";
  hilog.info(0x0000, TAG, 'start server name = ' + name);
  // 使用服务名构造Server
  let server: linkEnhance.Server = linkEnhance.createServer(name);
  server.on('serverStopped', (reason: number): void => {
    hilog.info(0x0000, TAG, 'serverStopped, reason= ' + reason);
  });
  // 取消订阅服务停止
  server.off('serverStopped', (reason: number): void => {
    hilog.info(0x0000, TAG, 'serverStopped, reason= ' + reason);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'start server errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## on('connectionAccepted')

```TypeScript
on(type: 'connectionAccepted', callback: Callback<Connection>): void
```

创建服务成功后，注册connectionAccepted事件的回调监听，等待对端连接。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Server-on(type: 'connectionAccepted', callback: Callback<Connection>): void--><!--Device-Server-on(type: 'connectionAccepted', callback: Callback<Connection>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connectionAccepted' | 是 | 事件回调类型，支持的事件为'connectionAccepted'，收到对端连接，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<Connection> | 是 | 注册的回调函数。[Connection](arkts-distributedservice-linkenhance-connection-i.md)返回的连接对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390206](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390206-参数非法) | Parameter invalid. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let name: string = "demo";
  hilog.info(0x0000, TAG, 'start server name = ' + name);
  // 使用服务名构造Server
  let server: linkEnhance.Server = linkEnhance.createServer(name);

  // 订阅服务接收事件
  server.on('connectionAccepted', (connection: linkEnhance.Connection): void => {
    hilog.info(0x0000, TAG, 'serverOnCallback = ' + JSON.stringify(connection));
  });
  // 启动服务
  server.start();
} catch (err) {
  hilog.error(0x0000, TAG, 'start server errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## on('serverStopped')

```TypeScript
on(type: 'serverStopped', callback: Callback<number>): void
```

在创建服务成功后，注册serverStopped回调，监听服务异常停止。使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Server-on(type: 'serverStopped', callback: Callback<number>): void--><!--Device-Server-on(type: 'serverStopped', callback: Callback<number>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serverStopped' | 是 | 事件回调类型，支持的事件为'serverStopped'，底层服务异常时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<number> | 是 | 注册的回调函数，number为返回的错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390206](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390206-参数非法) | Parameter invalid. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let name: string = "demo";
  hilog.info(0x0000, TAG, 'start server name = ' + name);
  // 使用服务名构造Server
  let server: linkEnhance.Server = linkEnhance.createServer(name);

  // 订阅服务停止
  server.on('serverStopped', (reason: number): void => {
    hilog.info(0x0000, TAG, 'serverStopped, reason= ' + reason);
  });
  // 启动服务
  server.start();
} catch (err) {
  hilog.error(0x0000, TAG, 'start server errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## start

```TypeScript
start(): void
```

创建服务成功后，需要调用start()开启该服务，方可被客户端连接，最大服务个数为10。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Server-start(): void--><!--Device-Server-start(): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390202](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390202-服务个数超出限制) | The number of servers exceeds the limit. |
| [32390300](../../apis-distributedservice-kit/errorcode-link-enhance.md#32390300-内部错误) | Internal error. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let name: string = "demo";
  hilog.info(0x0000, TAG, 'start server name = ' + name);
  let server: linkEnhance.Server = linkEnhance.createServer(name);
  server.start();
} catch (err) {
  hilog.error(0x0000, TAG, 'start server errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

## stop

```TypeScript
stop(): void
```

使用完服务时，调用`stop`停止服务，停止后可以调用`start`重新开启服务。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Server-stop(): void--><!--Device-Server-stop(): void-End-->

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
  let name: string = "demo";
  hilog.info(0x0000, TAG, 'start server name = ' + name);
  let server: linkEnhance.Server = linkEnhance.createServer(name);
  server.start();
  server.stop();
} catch (err) {
  hilog.error(0x0000, TAG, 'start server errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

