# off

## 导入模块

```TypeScript
import { deviceStatus } from '@kit.MultimodalAwarenessKit';
```

## off('steadyStandingDetect')

```TypeScript
function off(type: 'steadyStandingDetect', callback?: Callback<SteadyStandingStatus>): void
```

取消订阅设备静止姿态感知（支架态）事件，用于应用在退出页面或不再需要监听支架态变化的场景。调用后释放相关资源。

**起始版本：** 18

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'steadyStandingDetect' | 是 | 事件类型。固定传入'steadyStandingDetect'，表示设备静止姿态（支架态）感知。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SteadyStandingStatus](arkts-multimodalawareness-devicestatus-steadystandingstatus-e.md)&gt; | 否 | 要注销的回调函数，需与订阅时传入的回调函数一致。若不填，则取消当前监听该事件的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited<br> device capabilities. |
| [32500001](../errorcode-deviceStatus.md#32500001-服务异常) | Service exception. |
| [32500003](../errorcode-deviceStatus.md#32500003-取消订阅失败) | Unsubscription failed. |
