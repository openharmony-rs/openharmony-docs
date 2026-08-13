# on_SensorId.BAROMETER

## on_SensorId.BAROMETER

```TypeScript
function on(type: SensorId.BAROMETER, callback: Callback<BarometerResponse>, options?: Options): void
```

订阅气压计传感器数据。气压计传感器用于测量大气压强，适用于海拔估算、天气预报辅助等场景。调用后，系统会按设定频率通过callback持续上报气压数据。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-sensor-function on(type: SensorId.BAROMETER, callback: Callback<BarometerResponse>, options?: Options): void--><!--Device-sensor-function on(type: SensorId.BAROMETER, callback: Callback<BarometerResponse>, options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.BAROMETER | 是 | 传感器类型，该值固定为SensorId.BAROMETER。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;BarometerResponse&gt; | 是 | 回调函数，异步上报的传感器数据固定为BarometerResponse。 |
| options | Options | 否 | 可选参数列表，用于设置传感器上报频率，默认值为200000000ns（即200ms）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |

## 示例

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.BAROMETER, (data: sensor.BarometerResponse) => {
    console.info('Succeeded in invoking on. Atmospheric pressure: ' + data.pressure);
  }, { interval: 100000000 });
  setTimeout(() => {
    sensor.off(sensor.SensorId.BAROMETER);
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```

