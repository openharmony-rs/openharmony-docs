# @ohos.multimodalAwareness.carAwareness (车辆感知)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @ultimate_lin-->
<!--Designer: @charlie3wx-->
<!--Tester: @fhzs-->
<!--Adviser: @hu-zhiqiong-->

本模块提供车辆感知能力，包括隔空手势交互、实时天气识别、补能状态识别等功能。

**起始版本：** 26.1.0

## 导入模块

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## Capability

表示车辆感知支持的能力类型枚举。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| SPATIAL_MOTION | 'SpatialMotion' | 隔空手势感知能力，支持识别用户隔空操作屏幕的动作。 |
| SPATIAL_POINT | 'SpatialPoint' | 指向识别能力，支持识别用户指向的车内零部件。<br>**系统接口：** 此枚举成员为系统接口。 |
| SPATIAL_GESTURE | 'SpatialGesture' | 肢体动作感知能力，支持识别用户特定姿势动作。<br>**系统接口：** 此枚举成员为系统接口。 |
| REALTIME_WEATHER | 'RealTimeWeather' | 实时天气感知能力，支持识别车辆当前所处环境的天气状态。 |
| REFUELING | 'Refueling' | 补能识别能力，支持识别车辆加油的开始与结束状态。 |
| CAR_STATUS | 'CarStatus' | 车辆状态感知能力，支持获取车辆相关状态信息。<br>**系统接口：** 此枚举成员为系统接口。 |
| CAR_CFG | 'CarCfg' | 车辆配置感知能力，支持获取车辆配置相关信息。<br>**系统接口：** 此枚举成员为系统接口。 |
| HABIT_RECOMMENDATION | 'HabitRecommendation' | 习惯推荐感知能力，支持基于用户习惯生成推荐。<br>**系统接口：** 此枚举成员为系统接口。 |

## SpatialMotionInfo

隔空手势感知的结果信息接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | 是 | 否 | 识别结果的时间戳。<br>单位：毫秒。 |
| pointX | number | 是 | 否 | 手部在屏幕上的 X 轴坐标。 |
| pointY | number | 是 | 否 | 手部在屏幕上的 Y 轴坐标。 |
| event | number | 是 | 否 | 手势事件类型。<br>-1：无效<br>0：准备就绪<br>1：移动<br>2：点击 |

## carAwareness.onSpatialMotion

onSpatialMotion(callback: Callback\<SpatialMotionInfo\>): void

开启隔空手势感知，订阅隔空手势感知结果；设备不支持该能力时抛出34000002错误码，可调用 getAllCapabilityList查询设备可用能力，通过callback异步返回数据。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.vehicle.MMA_SPATIALACTION

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| callback | Callback\<SpatialMotionInfo\> | 是 | 回调函数，用于返回隔空手势感知数据。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**示例：**

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

try {
  carAwareness.onSpatialMotion((data) => {
    hilog.info(DOMAIN, TAG, 'Spatial motion event: %{public}d', data.event);
    hilog.info(DOMAIN, TAG, 'Point coordinate: (%{public}d, %{public}d)', data.pointX, data.pointY);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Subscribe spatial motion failed, error code: %{public}d', e.code);
}
```

## carAwareness.offSpatialMotion

offSpatialMotion(callback?: Callback\<SpatialMotionInfo\>): void

关闭隔空手势感知，取消订阅隔空手势结果。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.vehicle.MMA_SPATIALACTION

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| callback | Callback\<SpatialMotionInfo\> | 否 | 回调函数。传入指定回调则注销对应监听，不传入则注销所有监听。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |

**示例：**

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

// 注销指定监听
let motionCallback = (data) => {
  hilog.info(DOMAIN, TAG, 'Spatial motion data received');
};

try {
  carAwareness.offSpatialMotion(motionCallback);
  hilog.info(DOMAIN, TAG, 'Unsubscribe spatial motion succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Unsubscribe spatial motion failed, error code: %{public}d', e.code);
}

// 注销所有监听
try {
  carAwareness.offSpatialMotion();
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Unsubscribe all spatial motion failed, error code: %{public}d', e.code);
}
```

## RealTimeWeatherInfo

实时天气感知的结果信息接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | 是 | 否 | 识别结果的时间戳。<br>单位：毫秒。 |
| weather | number | 是 | 否 | 天气状态。<br>-1：无效<br>0：晴/多云<br>1：薄雾<br>2：浓雾<br>3：小雪<br>4：大雪<br>5：小雨<br>6：大雨 |

## carAwareness.onRealTimeWeather

onRealTimeWeather(callback: Callback\<RealTimeWeatherInfo\>): void

开启实时天气感知，订阅实时天气感知结果；设备不支持该能力时抛出34000002错误码，可调用getAllCapabilityList查询设备可用能力，通过callback异步返回数据。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.vehicle.MMA_WEATHER

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| callback | Callback\<RealTimeWeatherInfo\> | 是 | 回调函数，用于返回实时天气感知数据。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**示例：**

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

try {
  carAwareness.onRealTimeWeather((data) => {
    hilog.info(DOMAIN, TAG, 'Current weather status: %{public}d', data.weather);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Subscribe realtime weather failed, error code: %{public}d', e.code);
}
```

## carAwareness.offRealTimeWeather

offRealTimeWeather(callback?: Callback\<RealTimeWeatherInfo\>): void

关闭实时天气感知，取消订阅实时天气结果。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.vehicle.MMA_WEATHER

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| callback | Callback\<RealTimeWeatherInfo\> | 否 | 回调函数。传入指定回调则注销对应监听，不传入则注销所有监听。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |

**示例：**

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

try {
  carAwareness.offRealTimeWeather();
  hilog.info(DOMAIN, TAG, 'Unsubscribe realtime weather succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Unsubscribe realtime weather failed, error code: %{public}d', e.code);
}
```

## RefuelingInfo

补能识别的结果信息接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务 API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | 是 | 否 | 识别结果的时间戳。<br>单位：毫秒。 |
| status | number | 是 | 否 | 加油状态。<br>-1：无效<br>0：空闲（未开始加油）<br>1：开始加油<br>2：加油结束 |

## carAwareness.onRefueling

onRefueling(callback: Callback\<RefuelingInfo\>): void

开启补能感知，订阅补能状态感知结果；设备不支持该能力时抛出34000002错误码，可调用 getAllCapabilityList查询设备可用能力，通过callback异步返回数据。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务 API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**需要权限：** ohos.permission.vehicle.MMA_ENERGYREFILL

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| callback | Callback\<RefuelingInfo\> | 是 | 回调函数，用于返回补能识别数据。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**示例：**

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

try {
  carAwareness.onRefueling((data) => {
    hilog.info(DOMAIN, TAG, 'Refueling status: %{public}d', data.status);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Subscribe refueling failed, error code: %{public}d', e.code);
}
```

## carAwareness.offRefueling

offRefueling(callback?: Callback\<RefuelingInfo\>): void

关闭补能识别感知，取消订阅加油状态结果。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务 API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**需要权限：** ohos.permission.vehicle.MMA_ENERGYREFILL

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| callback | Callback\<RefuelingInfo\> | 否 | 回调函数。传入指定回调则注销对应监听，不传入则注销所有监听。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |

**示例：**

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

try {
  carAwareness.offRefueling();
  hilog.info(DOMAIN, TAG, 'Unsubscribe refueling succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Unsubscribe refueling failed, error code: %{public}d', e.code);
}
```

## carAwareness.getAllCapabilityList

getAllCapabilityList(): Promise<Capability[]>

获取当前设备支持的所有车辆感知能力列表。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<Capability[]\> | Promise对象，返回设备支持的感知能力枚举列表。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 34000001 | Service exception. |

**示例：**

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

carAwareness.getAllCapabilityList()
  .then((list) => {
    hilog.info(DOMAIN, TAG, 'Supported capability list: %{public}s', JSON.stringify(list));
  })
  .catch((err: BusinessError) => {
    hilog.error(DOMAIN, TAG, 'Get capability list failed, error code: %{public}d', err.code);
  });
```