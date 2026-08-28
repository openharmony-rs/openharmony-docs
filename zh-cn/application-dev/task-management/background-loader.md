# 后台加载任务(ArkTS)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

## 概述

### 功能介绍

适用于期望通过后台预先加载应用数据实现优化应用启动体验的场景，系统会根据用户使用习惯、频次以及系统资源（内存、电量）等条件，预先启动应用进程并执行加载回调方法，允许应用在后台执行短时的内容和数据加载。例如：资讯刷新、消息获取、视频缓存等。

### 运行原理

1. 需要启用后台加载任务功能的应用，可在前台启动时向系统注册任务。
2. 任务注册后，系统允许应用查询和删除任务。
3. 系统的后台加载任务管理模块会根据用户使用应用的习惯及系统状态（包括系统可用内存、电池电量、设备温度等）统一决策应用执行后台加载任务时机。应用无法对任务触发时机进行干预。

### 约束与限制

- **数量限制：** 一个应用只能注册一个后台加载任务，任务中只能指定唯一的主用UIAbility。

- **超时：** 系统回调加载任务开始执行时最长运行30秒。如果应用多次超时，系统会禁用该应用，取消后续的任务调度（即使重新注册任务仍然不会再调度了）。

- **禁止执行可感知操作：** 在UIAbility创建阶段和加载任务执行阶段，禁止应用执行音频播放、音频录制、定位、操作闪光灯等可感知行为。如果系统检测到应用存在此类操作，系统会禁用该应用，取消后续的任务调度。


## 接口说明

**表1** 后台加载任务主要接口

以下是后台加载任务开发使用的相关接口，更多接口及使用方式请见[后台加载任务管理](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md)文档。
| 接口名 | 接口描述 |
| -------- | -------- |
| [registerTask(taskInfo: TaskInfo): void](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloaderregisgertask) | 注册后台加载任务。 |
| [unregisterTask(taskInfo: TaskInfo): void](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloaderunregisgertask) | 取消注册后台加载任务。 |
| [getTaskInfo(taskId: number): Promise&lt;TaskInfo&gt;](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloadergettaskinfo) | 查询注册后台加载任务信息（Promise形式）。 |
| [finishTask(taskInfo: TaskInfo): void](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloaderfinishtask) | 通知系统加载任务执行完成。 |

**表2** 后台加载任务需要应用实现的回调接口

以下是后台加载任务回调开发使用的相关接口，更多接口及使用方式请见[后台加载任务管理](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md)文档。
| 接口名 | 接口描述 |
| -------- | -------- |
| [ON_START](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloaderon_start) | 需要实现的执行后台加载任务的方法名，系统通过StartAbilityByCall方法启动应用后，会回调此方法。方法的入参为[backgroundLoader.TaskInfo](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#taskinfo)。 |
| [ON_STOP](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloaderon_stop) | 待应用实现的回调方法名。系统在后台加载任务异常取消时，会回调onStop方法。方法的入参为[backgroundLoader.TaskStopInfo](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#taskstopinfo)。 |


## 开发步骤

后台加载任务的开发步骤分为三步：

1. **实现后台加载任务回调能力：** 定义ON_START和ON_STOP回调函数，并注册到应用主UIAbility的Callee中。

2. **注册后台加载任务：** 调用registerTask接口，将任务注册到后台加载任务管理服务。

3. **完成后台加载任务：** 在ON_START回调中执行加载逻辑后，调用finishTask接口通知系统任务完成。

### 实现后台加载任务回调能力

1. 声明ohos.permission.KEEP_BACKGROUND_RUNNING权限，配置方式请参见[声明权限](../security/AccessToken/declare-permissions.md#声明权限)。

2. 在应用主UIAbility的onCreate生命周期中，导入模块并定义ON_START和ON_STOP回调函数，然后通过Callee注册。

   <!-- @[backgroundLoader_register_callee](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';
   import { backgroundLoader } from '@kit.BackgroundTasksKit';
   import { rpc } from '@kit.IPCKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // 定义ON_START回调，系统调度执行后台加载任务时回调此方法
   function BackgroundLoaderOnStart(pdata: rpc.MessageSequence): rpc.Parcelable {
     console.info('Task started [backgroundLoader.ON_START callback]');
     // TODO: 在此执行应用后台加载的业务逻辑

     // 加载完成后通知系统
     let taskInfo: backgroundLoader.TaskInfo = {
       taskId: pdata.readInt(),
       abilityName: pdata.readString()
     };
     backgroundLoader.finishTask(taskInfo);
     // 返回Parcelable对象
     return new class implements rpc.Parcelable {
       marshalling(dataOut: rpc.MessageSequence): boolean { return true; }
       unmarshalling(dataIn: rpc.MessageSequence): boolean { return true; }
     }();
   }

   // 定义ON_STOP回调，后台加载任务异常取消时回调此方法
   function BackgroundLoaderOnStop(pdata: rpc.MessageSequence): rpc.Parcelable {
     const taskId: number = pdata.readInt();
     const abilityName: string = pdata.readString();
     const stopCode: number = pdata.readInt();
     const stopMessage: string = pdata.readString();
     console.info(`onStop: taskId=${taskId}, stopCode=${stopCode}, message=${stopMessage}`);
     // 返回Parcelable对象
     return new class implements rpc.Parcelable {
       marshalling(dataOut: rpc.MessageSequence): boolean { return true; }
       unmarshalling(dataIn: rpc.MessageSequence): boolean { return true; }
     }();
   }

   export default class EntryAbility extends UIAbility {
     onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
       try {
         // 注册ON_START回调，当后台加载任务启动时触发BackgroundLoaderOnStart
         this.callee.on(backgroundLoader.ON_START, BackgroundLoaderOnStart);
         // 注册ON_STOP回调，当后台加载任务停止时触发BackgroundLoaderOnStop
         this.callee.on(backgroundLoader.ON_STOP, BackgroundLoaderOnStop);
       } catch (error) {
         console.error(`Callee.on catch error, error.code: ${(error as BusinessError).code}, error.message: ${(error as BusinessError).message}`);
       }
     }
   }
   ```

### 注册后台加载任务

1. 导入模块。

   <!-- @[backgroundLoader_include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   import { backgroundLoader } from '@kit.BackgroundTasksKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. 注册后台加载任务。

   <!-- @[backgroundLoader_registerTask](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   const taskInfo: backgroundLoader.TaskInfo = {
     abilityname: 'EntryAbility',
     taskId: 1
   };
   try {
     backgroundLoader.registerTask(taskInfo);
     console.info('registerTask success');
   } catch (err) {
     console.error(`registerTask failed. code is ${(err as BusinessError).code} message is ${(err as BusinessError).message}`);
   }
   ```

3. 取消注册后台加载任务。

   <!-- @[backgroundLoader_unregisterTask](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   const taskInfo: backgroundLoader.TaskInfo = {
     abilityname: 'EntryAbility',
     taskId: 1
   };
   try {
     backgroundLoader.unregisterTask(taskInfo);
     console.info('unregisterTask success');
   } catch (err) {
     console.error(`unregisterTask failed. code is ${(err as BusinessError).code} message is ${(err as BusinessError).message}`);
   }
   ```

4. 查询后台加载任务信息。

   <!-- @[backgroundLoader_getTaskInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   try {
     const taskInfoData = backgroundLoader.getTaskInfo(1);
     console.info(`getTaskInfo result: taskId=${taskInfoData.taskId}, abilityName=${taskInfoData.abilityName}`);
   } catch (err) {
     console.error(`getTaskInfo failed. code is ${(err as BusinessError).code} message is ${(err as BusinessError).message}`);
   }
   ```

5. 完成后台加载任务。

   <!-- @[backgroundLoader_finishTask](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   const taskInfo: backgroundLoader.TaskInfo = {
     abilityname: 'EntryAbility',
     taskId: 1
   };
   try {
     backgroundLoader.finishTask(taskInfo);
     console.info('finishTask success');
   } catch (err) {
     console.error(`finishTask failed. code is ${(err as BusinessError).code} message is ${(err as BusinessError).message}`);
   }
   ```

### 后台加载任务触发功能验证

后台加载任务注册成功之后，需要等到条件满足后才可以执行后台加载任务回调，为了快速验证实现的回调功能是否正确，可以通过以下[hidumper命令](../dfx/hidumper.md)手动触发后台加载任务执行回调。

> **说明：**
>
> - `-s 1901`：指向ResourceSchedule系统服务发送命令（1901为该服务ID）。
> - `-a`：携带附加参数，需用引号包裹，格式为`backgroundLoader 包名 Ability名`，示例中的`com.example.myapplication`和`EntryAbility`需替换为实际值。

```ts
$ hidumper -s 1901 -a 'backgroundLoader com.example.myapplication EntryAbility'

-------------------------------[ability]-------------------------------


----------------------------------ResourceSched----------------------------------
```

## 相关实例

针对后台加载任务的开发，有以下相关示例可供参考：

- [后台加载任务（ArkTS）（API12）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader)
