# onDistanceMeasure（系统接口）

## 导入模块

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## onDistanceMeasure

```TypeScript
function onDistanceMeasure(configParams: DistanceMeasurementConfigParams,
    callback: Callback<DistanceMeasurementResponse>): void
```

订阅测距接口。触发测距算法执行，并返回测距结果。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_SENSING_WITH_ULTRASOUND

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.DistanceMeasurement

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configParams | [DistanceMeasurementConfigParams](arkts-multimodalawareness-spatialawareness-distancemeasurementconfigparams-i-sys.md) | 是 | 测距接口配置参数 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DistanceMeasurementResponse](arkts-multimodalawareness-spatialawareness-distancemeasurementresponse-i-sys.md)&gt; | 是 | 回调函数，返回测距结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited device capabilities. |
| [35100001](../errorcode-spatialAwareness.md#35100001-服务异常) | Service exception. |
| [35100002](../errorcode-spatialAwareness.md#35100002-订阅失败) | Subscription failed. |
| [35100004](../errorcode-spatialAwareness.md#35100004-无效参数) | Parameter invalid. |

**示例**

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
   console.info('call onDistanceMeasure before');
   let configParams: spatialAwareness.DistanceMeasurementConfigParams = {
      deviceList: ["123456"],
      techType: 2,
      reportMode: 0,
      reportFrequency: 340
   };
   console.info('call onDistanceMeasure start');
   try {
      spatialAwareness.onDistanceMeasure(configParams, (data:spatialAwareness.DistanceMeasurementResponse) => {
         console.info(`result = ${data.distance}`);
      });
   } catch (err) {
      console.error(`call onDistanceMeasure failed, Code: ${err.code}, message: ${err.message}`);
   }
```
