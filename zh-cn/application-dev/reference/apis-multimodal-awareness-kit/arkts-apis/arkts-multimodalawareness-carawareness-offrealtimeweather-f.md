# offRealTimeWeather

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## offRealTimeWeather

```TypeScript
function offRealTimeWeather(callback?: Callback<RealTimeWeatherInfo>): void
```

取消订阅实时天气结果。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.vehicle.MMA_WEATHER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-carAwareness-function offRealTimeWeather(callback?: Callback<RealTimeWeatherInfo>): void--><!--Device-carAwareness-function offRealTimeWeather(callback?: Callback<RealTimeWeatherInfo>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RealTimeWeatherInfo](arkts-multimodalawareness-carawareness-realtimeweatherinfo-i.md)&gt; | 否 | 回调函数。传入指定回调则注销对应监听，不传入则注销所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [34000001](../errorcode-carAwareness.md#34000001-服务异常) | Service exception. |
