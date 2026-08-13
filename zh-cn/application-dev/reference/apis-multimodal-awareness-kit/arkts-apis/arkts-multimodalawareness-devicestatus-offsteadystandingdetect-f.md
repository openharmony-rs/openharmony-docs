# offSteadyStandingDetect

## offSteadyStandingDetect

```TypeScript
function offSteadyStandingDetect(callback?: Callback<SteadyStandingStatus>): void
```

取消订阅设备静止姿态感知（支架态）事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-deviceStatus-function offSteadyStandingDetect(callback?: Callback<SteadyStandingStatus>): void--><!--Device-deviceStatus-function offSteadyStandingDetect(callback?: Callback<SteadyStandingStatus>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SteadyStandingStatus](arkts-multimodalawareness-devicestatus-steadystandingstatus-e.md)&gt; | 否 | 要注销的回调函数，需与订阅时传入的回调函数一致。若不填，则取消当前监听该事件的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited &lt;br&gt; device capabilities. |
| [32500003](../../apis-multimodalawareness-kit/errorcode-deviceStatus.md#32500003-取消订阅失败) | Unsubscription failed. |
| [32500001](../../apis-multimodalawareness-kit/errorcode-deviceStatus.md#32500001-服务异常) | Service exception. |

## 示例

示例一：取消订阅该客户端订阅设备静止姿态感知（支架态）事件的所有回调。

```TypeScript
try {
  deviceStatus.offSteadyStandingDetect();
} catch (err) {
  console.info('off failed, err = ' + err);
}
```

示例二：取消订阅该客户端订阅设备静止姿态感知（支架态）事件的特定回调。

```TypeScript
import { Callback } from '@ohos.base';
// 定义callback变量
let callback : Callback<deviceStatus.SteadyStandingStatus> = (data : deviceStatus.SteadyStandingStatus) => {
  console.info('now status = ' + data);
};
// 以callback为回调函数，订阅设备静止姿态感知（支架态）事件
try {
  deviceStatus.onSteadyStandingDetect(callback);
} catch (err) {
  console.info('on failed, err = ' + err);
}
// 取消该客户端订阅设备静止姿态感知（支架态）事件的特定回调函数
try {
  deviceStatus.offSteadyStandingDetect(callback);
} catch (err) {
  console.info('off failed, err = ' + err);
}
```

