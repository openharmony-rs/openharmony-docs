# 设备状态感知开发指导
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @osmanthusblossom-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

DeviceStatus（设备状态感知）模块提供设备状态感知能力，可以获取到设备的状态感知信息，例如：获取设备静止姿态感知状态（支架态）和手机跌落检测状态。

详细的接口介绍请参考[@ohos.multimodalAwareness.deviceStatus (设备状态感知)](../../reference/apis-multimodalawareness-kit/js-apis-awareness-deviceStatus.md)。

## 基本概念

在进行设备状态感知模块的使用前，开发者应了解以下基本概念：

- 支架态

    设备进入支架态指设备静止，且屏幕与水平面角度处于45度-135度。折叠屏手机需处于折叠状态或者完全展开状态。

- 手机跌落检测

    通过传感器感知手机跌落事件，并返回跌落检测状态。正常状态（STATUS_NORMAL）表示设备处于正常握持或放置状态，跌落状态（STATUS_DROPPED）表示设备检测到跌落事件。

## 获取设备静止姿态感知状态（支架态）开发指导

### 场景介绍

开发过程中，需要订阅设备静止姿态（支架态）感知，并且通过订阅时传入的回调函数来获取到当前的状态值。

从API version 18开始，支持获取设备静止姿态（支架态）。

### 约束与限制

设备需要支持加速度计。

### 接口说明

| 接口名                                                       | 描述                                   |
| ------------------------------------------------------------ | -------------------------------------- |
| on(type: 'steadyStandingDetect', callback: Callback&lt;SteadyStandingStatus&gt;): void; | 订阅设备静止姿态（支架态）感知，结果通过callback返回。 |
| off(type: 'steadyStandingDetect', callback?: Callback&lt;SteadyStandingStatus&gt;): void; | 取消订阅设备静止姿态（支架态）感知。                   |

### 开发步骤

1. 导入模块。

   <!-- @[import_the_device_status_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) -->  
   
   ``` TypeScript
   import { deviceStatus } from '@kit.MultimodalAwarenessKit';
   ```
   

2. 订阅设备静止姿态（支架态）感知事件。

   <!-- @[device_status_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) -->  
   
   ``` TypeScript
   try {
     deviceStatus.on('steadyStandingDetect', (data:deviceStatus.SteadyStandingStatus) => {
       console.info('succeed to get status, now status = ' + data);
     });
     // ...
   } catch (err) {
     console.error('on failed, err = ' + err);
     // ...
   }
   ```


3. 取消本客户端订阅的所有设备静止姿态（支架态）感知事件。

   <!-- @[device_status_unsubscribe_all](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) -->  
   
   ``` TypeScript
   try {
     deviceStatus.off('steadyStandingDetect');
     // ...
   } catch (err) {
     console.error('off failed, err = ' + err);
     // ...
   }
   ```



4. 取消订阅设备静止姿态（支架态）感知事件的特定回调。

   <!-- @[device_status_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) -->  
   
   ``` TypeScript
   // 定义callback变量
   let callback : Callback<deviceStatus.SteadyStandingStatus> = (data : deviceStatus.SteadyStandingStatus) => {
     console.info('succeed to get status, now status = ' + data);
   };
   // 以callback为回调函数，订阅设备静止姿态感知（支架态）事件
   try {
     deviceStatus.on('steadyStandingDetect', callback);
     // ...
   } catch (err) {
     console.error('on failed, err = ' + err);
     // ...
   }
   // 取消该客户端订阅设备静止姿态感知（支架态）事件的特定回调函数
   try {
     deviceStatus.off('steadyStandingDetect', callback);
     // ...
   } catch (err) {
     console.error('off failed, err = ' + err);
     // ...
   }
   ```

## 手机跌落检测开发指导

### 场景介绍

应用可以订阅手机跌落检测事件，通过回调函数获取设备的跌落检测状态，并根据业务需要执行相应的保护措施。

### 约束与限制

- 仅支持HarmonyOS 26.1.0及以上版本的设备。
- 仅支持Stage模型。
- 设备需要支持SystemCapability.MultimodalAwareness.DeviceStatus系统能力。不支持手机跌落检测的设备调用接口时，会抛出错误码801。
- 同一回调重复订阅时，会抛出错误码32500002。不再需要监听时，应取消订阅以释放资源。

### 接口说明

| 接口名 | 描述 |
| ---- | ---- |
| onDropDetect(callback: Callback&lt;DropDetectionStatus&gt;): void | 订阅手机跌落检测事件，通过callback返回设备的跌落检测状态。 |
| offDropDetect(callback?: Callback&lt;DropDetectionStatus&gt;): void | 取消订阅手机跌落检测事件。不传入callback时，取消当前客户端订阅的所有跌落检测回调。 |

### 开发步骤

1. 导入模块。

   <!-- @[import_the_device_status_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { deviceStatus } from '@kit.MultimodalAwarenessKit';
   ```

2. 订阅设备跌落检测事件。

   <!-- @[drop_detect_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   try {
     deviceStatus.onDropDetect((data: deviceStatus.DropDetectionStatus) => {
       console.info('succeed to get status, now status = ' + data);
     });
     // ...
   } catch (err) {
     console.error('on failed, err = ' + err);
     // ...
   }
   ```


3. 取消本客户端订阅的所有设备跌落检测事件。

   <!-- @[drop_detect_unsubscribe_all](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   try {
     deviceStatus.offDropDetect();
     // ...
   } catch (err) {
     console.error('off failed, err = ' + err);
     // ...
   }
   ```

4. 取消订阅设备跌落检测事件的特定回调。

   <!-- @[drop_detect_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 定义callback变量
   let callback: Callback<deviceStatus.DropDetectionStatus> = (data: deviceStatus.DropDetectionStatus) => {
     console.info('succeed to get DropDetect status, now status = ' + data);
   };
   // 以callback为回调函数，订阅设备跌落检测事件
   try {
     deviceStatus.onDropDetect(callback);
     // ...
   } catch (err) {
     console.error('on failed, err = ' + err);
     // ...
   }
   // 取消该客户端订阅设备跌落检测事件的特定回调函数
   try {
     deviceStatus.offDropDetect(callback);
     // ...
   } catch (err) {
     console.error('off failed, err = ' + err);
     // ...
   }
   ```