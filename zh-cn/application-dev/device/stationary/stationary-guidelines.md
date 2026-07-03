# Stationary开发指导
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->


## 场景介绍

当应用需要获取当前设备状态时，可以调用Stationary模块，例如：需要判断当前设备处于绝对静止状态或者相对静止状态。

详细的接口介绍请参考[@ohos.stationary (设备状态感知框架)](../../reference/apis-multimodalawareness-kit/js-apis-stationary.md)。

## 设备状态类型参数说明

| 名称 | 描述 |
| -------- | -------- |
| still | 绝对静止。 |
| relativeStill | 相对静止。 |

## 订阅设备状态事件参数说明

| 变量                             | 值    | 说明                                       |
| ------------------------------ | ---- | ---------------------------------------- |
| ENTER         | 1    | 订阅进入事件。   |
| EXIT | 2   | 订阅退出事件。 |
| ENTER_EXIT | 3   | 订阅进入和退出事件。 |

## 返回设备状态参数说明

| 变量                             | 值    | 说明                                       |
| ------------------------------ | ---- | ---------------------------------------- |
| ENTER         | 1    | 返回进入状态。   |
| EXIT | 2   | 返回退出状态。 |

## 接口说明

| 接口名                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| on(activity: ActivityType, event: ActivityEvent, reportLatencyNs: number, callback: Callback&lt;ActivityResponse&gt;): void | 订阅设备状态，结果通过callback返回。 |
| once(activity: ActivityType, callback: Callback&lt;ActivityResponse&gt;): void | 查询设备状态，结果通过callback返回。 |
| off(activity: ActivityType, event: ActivityEvent, callback?: Callback&lt;ActivityResponse&gt;): void | 取消订阅设备状态。                                 |

## 约束与限制

设备需要支持加速度传感器。

目前只提供了算法框架，api接口测试框架的调用返回结果为:data={"type":3,"value":-1};

如需相对静止和绝对静止能力，则具体算法需要开发者自己在device_status/libs/src/algorithm实现，可参考案例如下：

   ```C++
   algoPara_.resultantAcc =
      sqrt((algoPara_.x * algoPara_.x) + (algoPara_.y * algoPara_.y) + (algoPara_.z * algoPara_.z));
   if ((algoPara_.resultantAcc > RESULTANT_ACC_LOW_THRHD) && (algoPara_.resultantAcc < RESULTANT_ACC_UP_THRHD)) {
      if (state_ == STILL) {
         return;
      }
      counter_--;
      if (counter_ == 0) {
         counter_ = COUNTER_THRESHOLD;
         UpdateStateAndReport(VALUE_ENTER, STILL, TYPE_ABSOLUTE_STILL);
      }
   } else {
      counter_ = COUNTER_THRESHOLD;
      if (state_ == UNSTILL) {
         return;
      }
      UpdateStateAndReport(VALUE_EXIT, UNSTILL, TYPE_ABSOLUTE_STILL);
   }
   ```

## 开发步骤

1. 导入模块。

   <!-- @[import_the_stationary_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Stationary/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   import { stationary } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. 订阅绝对静止的进入事件，1秒上报一次。

   <!-- @[stationary_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Stationary/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   let reportLatencyNs = 1000000000; // 单位：纳秒
   try {
     stationary.on('still', stationary.ActivityEvent.ENTER, reportLatencyNs, (data) => {
       console.info('data=' + JSON.stringify(data));
     })
     // ...
   } catch (error) {
     let message = (error as BusinessError).message;
     console.error('stationary on failed:' + message);
   }
   ```

3. 查询绝对静止状态的进入事件。

   <!-- @[stationary_getStatus](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Stationary/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   try {
     stationary.once('still', (data) => {
       console.info('data=' + JSON.stringify(data));
     })
     // ...
   } catch (error) {
     let message = (error as BusinessError).message;
     console.error('stationary once failed:' + message);
   }
   ```

4. 取消订阅绝对静止状态的进入事件。

   <!-- @[stationary_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Stationary/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   try {
     stationary.off('still', stationary.ActivityEvent.ENTER, (data) => {
       console.info('data=' + JSON.stringify(data));
     })
     // ...
   } catch (error) {
     let message = (error as BusinessError).message;
     console.error('stationary off failed:' + message);
   }
   ```
