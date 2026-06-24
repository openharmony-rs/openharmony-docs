# isDistributedEnabled

## 导入模块

```TypeScript
import { notificationManager } from '@ohos.notificationManager';
```

## isDistributedEnabled

```TypeScript
function isDistributedEnabled(callback: AsyncCallback<boolean>): void
```

查询设备是否支持跨设备协同通知。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 26.0.0

**替代接口：** isDistributedEnabled(deviceType:

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。返回true表示支持跨设备协同通知；返回false表示不支持跨设备协同通知；调用失败返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 26.0.0+ |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [1600010](../../errorcode-universal.md#1600010-Distributed) | Distributed operation failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isDistributedEnabledCallback = (err: BusinessError, data: boolean): void => {
  if (err) {
    console.error(`isDistributedEnabled failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`isDistributedEnabled success ${JSON.stringify(data)}`);
  }
};
notificationManager.isDistributedEnabled(isDistributedEnabledCallback);

```


## isDistributedEnabled

```TypeScript
function isDistributedEnabled(): Promise<boolean>
```

查询设备是否支持跨设备协同通知。使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 26.0.0

**替代接口：** isDistributedEnabled(deviceType:

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示支持跨设备协同通知；返回false表示不支持跨设备协同通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 26.0.0+ |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [1600010](../../errorcode-universal.md#1600010-Distributed) | Distributed operation failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.isDistributedEnabled().then((data: boolean) => {
  console.info(`isDistributedEnabled success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`isDistributedEnabled failed, code is ${err.code}, message is ${err.message}`);
});

```

