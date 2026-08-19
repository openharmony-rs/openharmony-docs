# on_SensorId.FUSION_PRESSURE

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## on_SensorId.FUSION_PRESSURE

```TypeScript
function on(type: SensorId.FUSION_PRESSURE, callback: Callback<FusionPressureResponse>,
    options?: Options): void
```

订阅融合压力传感器数据。融合压力传感器用于获取经融合算法处理的压力数据，仅适用于智能手表设备。适用于需要获取手腕压力数据的健康监测场景。调用后，系统会按设定频率通过callback持续上报融合压力数据。

**起始版本：** 22

<!--Device-sensor-function on(type: SensorId.FUSION_PRESSURE, callback: Callback<FusionPressureResponse>,    options?: Options): void--><!--Device-sensor-function on(type: SensorId.FUSION_PRESSURE, callback: Callback<FusionPressureResponse>,    options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.FUSION_PRESSURE | 是 | 传感器类型，该值固定为SensorId.FUSION_PRESSURE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[FusionPressureResponse](arkts-sensorservice-sensor-fusionpressureresponse-i.md)&gt; | 是 | 回调函数，异步上报的传感器数据固定为FusionPressureResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; <br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.FUSION_PRESSURE, (data: sensor.FusionPressureResponse) => {
    console.info('Succeeded in invoking on. fusionPressure: ' + data.fusionPressure);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.FUSION_PRESSURE);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```

