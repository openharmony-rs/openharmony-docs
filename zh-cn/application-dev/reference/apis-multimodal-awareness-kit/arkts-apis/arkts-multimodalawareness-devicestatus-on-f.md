# on

## 导入模块

```TypeScript
import { deviceStatus } from '@kit.MultimodalAwarenessKit';
```

## on('steadyStandingDetect')

```TypeScript
function on(type: 'steadyStandingDetect', callback: Callback<SteadyStandingStatus>): void
```

订阅设备静止姿态感知（支架态）事件。建议在不需要时调用off()取消订阅，释放资源。

**起始版本：** 18

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'steadyStandingDetect' | 是 | 事件类型。固定传入'steadyStandingDetect'，表示设备静止姿态（支架态）感知。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SteadyStandingStatus](arkts-multimodalawareness-devicestatus-steadystandingstatus-e.md)&gt; | 是 | 回调函数，用于接收设备静止姿态（支架态）状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited device capabilities. |
| [32500001](../errorcode-deviceStatus.md#32500001-服务异常) | Service exception. |
| [32500002](../errorcode-deviceStatus.md#32500002-订阅失败) | Subscription failed. |

**示例**

```TypeScript
try {
   deviceStatus.on('steadyStandingDetect', (data: deviceStatus.SteadyStandingStatus) => {
      console.info(`succeeded to get status, now status = ${JSON.stringify(data)}`);
   });
} catch (err) {
   console.error(`on failed. Code: ${err.code}, message: ${err.message}`);
}
```
