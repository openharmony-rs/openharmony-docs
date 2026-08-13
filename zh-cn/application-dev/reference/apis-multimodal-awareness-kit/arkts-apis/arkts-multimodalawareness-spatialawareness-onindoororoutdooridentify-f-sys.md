# onIndoorOrOutdoorIdentify（系统接口）

## onIndoorOrOutdoorIdentify

```TypeScript
function onIndoorOrOutdoorIdentify(configParams: DistanceMeasurementConfigParams,
    callback: Callback<DoorPositionResponse>): void
```

订阅门内外识别接口。触发门内外识别算法执行，并返回设备在门内还是门外的信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCESS_SENSING_WITH_ULTRASOUND

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-spatialAwareness-function onIndoorOrOutdoorIdentify(configParams: DistanceMeasurementConfigParams,    callback: Callback<DoorPositionResponse>): void--><!--Device-spatialAwareness-function onIndoorOrOutdoorIdentify(configParams: DistanceMeasurementConfigParams,    callback: Callback<DoorPositionResponse>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configParams | [DistanceMeasurementConfigParams](arkts-multimodalawareness-spatialawareness-distancemeasurementconfigparams-i-sys.md) | 是 | 测距接口配置参数 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DoorPositionResponse](arkts-multimodalawareness-spatialawareness-doorpositionresponse-i-sys.md)&gt; | 是 | 回调函数，返回门内外信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to &lt;br&gt; limited device capabilities. |
| [35100004](../../apis-multimodalawareness-kit/errorcode-spatialAwareness.md#35100004-无效参数) | Parameter invalid. |
| [35100002](../../apis-multimodalawareness-kit/errorcode-spatialAwareness.md#35100002-订阅失败) | Subscription failed. |
| [35100001](../../apis-multimodalawareness-kit/errorcode-spatialAwareness.md#35100001-服务异常) | Service exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

## 示例

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
   console.info('call onIndoorOrOutdoorIdentify before');
   let configParams: spatialAwareness.DistanceMeasurementConfigParams = {
      deviceList: ["123456"],
      techType: 2,
      reportMode: 0,
      reportFrequency: 340
   };
   console.info('call onIndoorOrOutdoorIdentify start');
   try {
      spatialAwareness.onIndoorOrOutdoorIdentify(configParams, (data:spatialAwareness.DoorPositionResponse) => {
         console.info('result = ${data.position}');
      });
   } catch (err) {
      console.error('call onIndoorOrOutdoorIdentify failed, errCode = ' + err.code);
   }
```

