# @ohos.multimodalAwareness.carAwareness (车辆感知)(系统接口)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @ultimate_lin-->
<!--Designer: @charlie3wx-->
<!--Tester: @fhzs-->
<!--Adviser: @hu-zhiqiong-->

本模块提供车辆感知的系统级能力，包括指向识别、肢体动作识别、车辆状态感知等功能。

**起始版本：** 26.1.0

> **说明：**
> 
> 当前页面仅包含本模块的系统接口，其他公开接口参见 [@ohos.multimodalAwareness.carAwareness (车辆感知)](js-apis-awareness-carAwareness.md)。

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

## CarAwarenessInfo

车辆感知通用结果信息接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | 是 | 否 | 识别结果的时间戳。<br>单位：毫秒。 |
| capability | [Capability](#capability) | 是 | 否 | 对应的感知能力类型。 |
| awarenessEvent | Record\<string, Object\> | 是 | 是 | 感知结果数据键值对，不同能力返回不同字段。<br>- SPATIAL_POINT：包含 object、zone、value、errorCode 等字段<br>- SPATIAL_GESTURE：包含 action 字段 |

## CarAwarenessOptions

车辆感知订阅配置选项接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| parameters | Record\<string, Object\> | 是 | 是 | 自定义感知参数键值对，用于传入特定能力的配置项。 |

## carAwareness.onCarAwareness

onCarAwareness(capability: Capability, callback: Callback<CarAwarenessInfo[]>, options?: CarAwarenessOptions): void

开启车辆感知，订阅车辆感知结果；设备不支持该能力时抛出34000002错误码，可调用getAllCapabilityList查询设备可用能力，通过callback异步返回数据。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| capability | [Capability](#capability) | 是 | 指定订阅的感知能力类型。<br/>**注意**：该参数不能传入 `SpatialMotion`、`RealTimeWeather` 和 `Refueling`，否则会抛出34000002错误码。 |
| callback | Callback\<CarAwarenessInfo[]\> | 是 | 回调函数，用于返回感知结果数据数组。 |
| options | [CarAwarenessOptions](#carawarenessoptions) | 否 | 感知能力的可选配置项。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
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
  carAwareness.onCarAwareness(carAwareness.Capability.SPATIAL_POINT, (dataList: carAwareness.CarAwarenessInfo[]) => {
    hilog.info(DOMAIN, TAG, 'Car awareness data count: %{public}d', dataList.length);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Subscribe car awareness failed, error code: %{public}d', e.code);
}
```

## carAwareness.offCarAwareness

offCarAwareness(capability: Capability, callback: Callback<CarAwarenessInfo[]>, options?: CarAwarenessOptions): void

取消指定订阅类型的车辆感知。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| capability | [Capability](#capability) | 是 | 指定取消订阅的感知能力类型。 |
| callback | Callback\<CarAwarenessInfo[]\> | 否 | 回调函数。传入指定回调则注销对应监听，不传入则注销所有监听。 |
| options | [CarAwarenessOptions](#carawarenessoptions) | 否 | 感知能力的可选配置项。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 34000001 | Service exception. |

**示例：**

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

let awarenessCallback = (dataList: carAwareness.CarAwarenessInfo[]) => {
  hilog.info(DOMAIN, TAG, 'Receive car awareness data');
};

try {
  carAwareness.offCarAwareness(carAwareness.Capability.SPATIAL_POINT, awarenessCallback);
  hilog.info(DOMAIN, TAG, 'Unsubscribe car awareness succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Unsubscribe car awareness failed, error code: %{public}d', e.code);
}
```

## carAwareness.updateSpatialActionEnableStatus

updateSpatialActionEnableStatus(event: number): void

更新空间动作感知的启停状态。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.vehicle.MMA_SPATIALACTION

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| event | number | 是 | 启停状态值。<br>0：结束<br>1：开始<br>取值应为整数。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
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
  carAwareness.updateSpatialActionEnableStatus(1);
  hilog.info(DOMAIN, TAG, 'Enable spatial action succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Update spatial action status failed, error code: %{public}d', e.code);
}
```

## carAwareness.updateSpatialActionZone

updateSpatialActionZone(zone: number): void

更新空间动作感知的音区信息。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.vehicle.MMA_SPATIALACTION

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| zone | number | 是 | 音区编号。<br>3：左后<br>4：右后<br>取值应为整数。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
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
  carAwareness.updateSpatialActionZone(3);
  hilog.info(DOMAIN, TAG, 'Update spatial action zone succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Update spatial action zone failed, error code: %{public}d', e.code);
}
```

## carAwareness.getCarAwareness

getCarAwareness(capability: Capability, options?: CarAwarenessOptions): Promise<CarAwarenessInfo[]>

单次获取指定类型的车辆感知结果。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| capability | [Capability](#capability) | 是 | 指定获取的感知能力类型。 |
| options | [CarAwarenessOptions](#carawarenessoptions) | 否 | 感知能力的可选配置项。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<CarAwarenessInfo[]\> | Promise对象，返回感知结果数据数组。 |

**错误码：**

以下错误码的详细介绍请参见[车辆感知错误码](errorcode-carAwareness.md)。

| 错误码 ID | 错误信息 |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**示例：**

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

carAwareness.getCarAwareness(carAwareness.Capability.CAR_STATUS)
  .then((dataList: carAwareness.CarAwarenessInfo[]) => {
    hilog.info(DOMAIN, TAG, 'Get car awareness data succeed');
  })
  .catch((err: BusinessError) => {
    hilog.error(DOMAIN, TAG, 'Get car awareness failed, error code: %{public}d', err.code);
  });
```