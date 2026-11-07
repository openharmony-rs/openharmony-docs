# 车辆感知开发指导
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @ultimate_lin-->
<!--Designer: @charlie3wx-->
<!--Tester: @fhzs-->
<!--Adviser: @hu-zhiqiong-->

## 概述

carAwareness（车辆感知）模块面向车载应用提供基于摄像头的环境与动作感知能力。

详细的接口介绍请参考[@ohos.multimodalAwareness.carAwareness (车辆感知)](../../reference/apis-multimodalawareness-kit/js-apis-awareness-carAwareness.md)。

## 隔空手势感知开发指导

### 场景介绍

隔空手势感知可获取用户手部在屏幕上的坐标与动作事件，适用于车内无接触操控中控屏幕、互动游戏手势交互等场景。

### 接口说明

| 接口名 | 描述 |
| ------ | ---- |
| onSpatialMotion(callback: Callback\<SpatialMotionInfo\>): void; | 开启隔空手势感知，订阅隔空手势感知结果。 |
| offSpatialMotion(callback?: Callback\<SpatialMotionInfo\>): void; | 关闭隔空手势感知，取消订阅。 |
| getAllCapabilityList(): Promise\<Capability[]\>; | 获取当前设备支持的所有车辆感知能力列表。 |

### 需要权限

使用隔空手势感知时，需要权限：ohos.permission.vehicle.MMA_SPATIALACTION。

具体申请方式请参考[声明权限](../../security/AccessToken/declare-permissions.md)。

```JSON5
"requestPermissions": [
  {
    "name": "ohos.permission.vehicle.MMA_SPATIALACTION",
    // reason和usedScene按需填写
    "reason" : "", // 用于应用上架校验
    "usedScene" : {
        "abilities" : [
          "" // 使用权限的名称
        ],
        "when" : "" // 调用时机
    },
  }
]
```

### 参数说明

**SpatialMotionInfo**


| 参数名 | 类型 | 说明 |
| ------ | ---- | ---- |
| timestamp | number | 识别结果时间戳，单位毫秒 |
| pointX | number | 手部在屏幕上的X轴坐标 |
| pointY | number | 手部在屏幕上的Y轴坐标 |
| event | number | 手势事件类型：<br>-1：无效 <br>0：准备就绪<br> 1：移动<br> 2：点击 |

### 约束与限制

- 依赖后排摄像头，能力不支持时返回34000002指定能力不支持错误码。
- 摄像头被遮挡、用户手势超出识别区域时，无法正常识别。

### 开发步骤

1. 导入模块

   <!-- @[carAwareness_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { carAwareness } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. 检测设备是否支持隔空手势能力

   <!-- @[spatialMotion_query](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   async function querySpatialMotionCapability(): Promise<boolean> {
     try {
       const capabilityList = await carAwareness.getAllCapabilityList();
       const isSupported = capabilityList.includes(carAwareness.Capability.SPATIAL_MOTION);
       hilog.info(DOMAIN, TAG, 'Spatial motion supported: %{public}s', isSupported);
       return isSupported;
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to get capability list, error code: %{public}d', err.code);
       return false;
     }
   }
   ```

3. 注册手势感知回调，处理识别结果

   <!-- @[spatialMotion_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   function subscribeSpatialMotion(onUpdate: (data: string) => void): void {
     try {
       carAwareness.onSpatialMotion((motionInfo: carAwareness.SpatialMotionInfo) => {
         const eventType: string = getSpatialMotionEventType(motionInfo.event);
         const dataStr: string = `Event: ${eventType}, Position: (${motionInfo.pointX}, ${motionInfo.pointY})`;
         hilog.info(DOMAIN, TAG, 'Spatial motion event: %{public}d', motionInfo.event);
         hilog.info(DOMAIN, TAG, 'Hand coordinate: (%{public}d, %{public}d)', motionInfo.pointX, motionInfo.pointY);
         onUpdate(dataStr);
       });
       hilog.info(DOMAIN, TAG, 'Succeeded in subscribing spatial motion.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to subscribe spatial motion, error code: %{public}d', err.code);
     }
   }
   ```

4. 取消手势感知订阅

   <!-- @[spatialMotion_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   function unsubscribeSpatialMotion(): void {
     try {
       carAwareness.offSpatialMotion();
       hilog.info(DOMAIN, TAG, 'Succeeded in unsubscribing spatial motion.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to unsubscribe spatial motion, error code: %{public}d', err.code);
     }
   }
   ```

---

## 实时天气感知开发指导

### 场景介绍

实时天气感知可获取车辆当前所处环境的天气状态，适用于根据天气调整车载服务推荐、自动开启雨刮/除雾等场景。

### 接口说明

| 接口名 | 描述 |
| ------ | ---- |
| onRealTimeWeather(callback: Callback\<RealTimeWeatherInfo\>): void; | 开启实时天气感知，订阅实时天气感知结果。 |
| offRealTimeWeather(callback?: Callback\<RealTimeWeatherInfo\>): void; | 关闭实时天气感知，取消订阅。 |

### 需要权限

使用实时天气感知时，需要权限：ohos.permission.vehicle.MMA_WEATHER。

具体申请方式请参考[声明权限](../../security/AccessToken/declare-permissions.md)。

```JSON5
"requestPermissions": [
  {
    "name": "ohos.permission.vehicle.MMA_WEATHER"
  }
]
```

### 参数说明

**RealTimeWeatherInfo**

| 参数名 | 类型 | 说明 |
| ------ | ---- | ---- |
| timestamp | number | 识别结果时间戳，单位毫秒 |
| weather | number | 天气状态：<br>-1：无效<br> 0：晴/多云<br> 1：薄雾<br> 2：浓雾 <br>3：小雪<br> 4：大雪<br> 5：小雨<br> 6：大雨 |

### 约束与限制

- 依赖车外摄像头，车外摄像头不可用时返回能力不支持错误码。
- 仅能识别车辆当前位置的实时天气。

### 开发步骤

1. 导入模块
   <!-- @[carAwareness_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { carAwareness } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. 注册天气感知回调

   <!-- @[realTimeWeather_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   function subscribeWeather(onUpdate: (data: string) => void): void {
     try {
       carAwareness.onRealTimeWeather((weatherInfo: carAwareness.RealTimeWeatherInfo) => {
         const weatherType: string = getWeatherType(weatherInfo.weather);
         hilog.info(DOMAIN, TAG, 'Weather code: %{public}d', weatherInfo.weather);
         onUpdate(weatherType);
       });
       hilog.info(DOMAIN, TAG, 'Succeeded in subscribing realtime weather.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to subscribe realtime weather, error code: %{public}d', err.code);
     }
   }
   ```

3. 取消天气感知订阅

   <!-- @[realTimeWeather_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   function unsubscribeWeather(): void {
     try {
       carAwareness.offRealTimeWeather();
       hilog.info(DOMAIN, TAG, 'Succeeded in unsubscribing realtime weather.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to unsubscribe realtime weather, error code: %{public}d', err.code);
     }
   }
   ```

---

## 补能状态感知开发指导

### 场景介绍

补能状态感知可识别车辆加油的开始与结束状态，适用于自动记录加油时长、匹配生成加油订单，支持原子化服务调用。

### 接口说明

| 接口名 | 描述 |
| ------ | ---- |
| onRefueling(callback: Callback\<RefuelingInfo\>): void; | 开启补能感知，订阅补能状态感知结果。 |
| offRefueling(callback?: Callback\<RefuelingInfo\>): void; | 关闭补能感知，取消订阅。 |

### 需要权限

使用补能状态感知时，需要权限：ohos.permission.vehicle.MMA_ENERGYREFILL。

具体申请方式请参考[声明权限](../../security/AccessToken/declare-permissions.md)。

```JSON5
"requestPermissions": [
  {
    "name": "ohos.permission.vehicle.MMA_ENERGYREFILL"
  }
]
```

### 参数说明

**RefuelingInfo**

| 参数名 | 类型 | 说明 |
| ------ | ---- | ---- |
| timestamp | number | 识别结果时间戳，单位毫秒 |
| status | number | 加油状态：<br>-1：无效 <br>0：空闲<br> 1：开始加油<br> 2：加油结束 |

### 约束与限制

- 依赖车外摄像头，车外摄像头不可用时返回能力不支持错误码。
- 车辆非P挡状态下，状态字段默认返回无效值。

### 开发步骤

1. 导入模块
   <!-- @[carAwareness_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { carAwareness } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. 注册补能状态回调

   <!-- @[refueling_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   function subscribeRefueling(onUpdate: (data: string) => void): void {
     try {
       carAwareness.onRefueling((refuelingInfo: carAwareness.RefuelingInfo) => {
         const statusType: string = getRefuelingStatusType(refuelingInfo.status);
         hilog.info(DOMAIN, TAG, 'Refueling status: %{public}d', refuelingInfo.status);
         onUpdate(statusType);
       });
       hilog.info(DOMAIN, TAG, 'Succeeded in subscribing refueling status.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to subscribe refueling status, error code: %{public}d', err.code);
     }
   }
   ```

3. 取消补能状态订阅

   <!-- @[refueling_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   function unsubscribeRefueling(): void {
     try {
       carAwareness.offRefueling();
       hilog.info(DOMAIN, TAG, 'Succeeded in unsubscribing refueling status.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to unsubscribe refueling status, error code: %{public}d', err.code);
     }
   }
   ```
