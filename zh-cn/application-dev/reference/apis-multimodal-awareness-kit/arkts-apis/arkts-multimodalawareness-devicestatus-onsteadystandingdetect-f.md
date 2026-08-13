# onSteadyStandingDetect

## onSteadyStandingDetect

```TypeScript
function onSteadyStandingDetect(callback: Callback<SteadyStandingStatus>): void
```

订阅设备静止姿态感知（支架态）事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-deviceStatus-function onSteadyStandingDetect(callback: Callback<SteadyStandingStatus>): void--><!--Device-deviceStatus-function onSteadyStandingDetect(callback: Callback<SteadyStandingStatus>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SteadyStandingStatus](arkts-multimodalawareness-devicestatus-steadystandingstatus-e.md)&gt; | 是 | 回调函数，用于接收设备静止姿态（支架态）状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited &lt;br&gt; device capabilities. |
| [32500002](../../apis-multimodalawareness-kit/errorcode-deviceStatus.md#32500002-订阅失败) | Subscription failed. |
| [32500001](../../apis-multimodalawareness-kit/errorcode-deviceStatus.md#32500001-服务异常) | Service exception. |

## 示例

```TypeScript
try {
     deviceStatus.onSteadyStandingDetect((data:deviceStatus.SteadyStandingStatus) => {
         console.info('now status = ' + data);
     });
 } catch (err) {
     console.info('on failed, err = ' + err);
 }
```

