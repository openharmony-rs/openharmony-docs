# onColorChange（系统接口）

## onColorChange

```TypeScript
function onColorChange(callback: Callback<ColorResponse>, options?: Options): void
```

Subscribe to color sensor data, {@code SensorId.COLOR}.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-function onColorChange(callback: Callback<ColorResponse>, options?: Options): void--><!--Device-sensor-function onColorChange(callback: Callback<ColorResponse>, options?: Options): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ColorResponse](arkts-sensorservice-sensor-colorresponse-i-sys.md)&gt; | 是 | callback color data. |
| options | Options | 否 | Optional parameters specifying the interval at which sensor data is reported, &lt;br&gt; {@code Options}. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

try{
  sensor.onColorChange((data: sensor.ColorResponse) => {
    console.info('Succeeded in getting the intensity of light: ' + data.lightIntensity);
    console.info('Succeeded in getting the color temperature: ' + data.colorTemperature);
  }, { interval: 100000000 });
  setTimeout(() => {
        sensor.offColorChange();
  }, 500);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke onColorChange. Code: ${e.code}, message: ${e.message}`);
}
```

