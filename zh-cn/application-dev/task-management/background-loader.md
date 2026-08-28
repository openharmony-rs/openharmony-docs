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

2. 在应用主UIAbility的onCreate生命周期中，通过Callee注册ON_START和ON_STOP回调函数。

   <!-- @[backgroundLoader_register_callee](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets) -->

   <div class="same-source-code">

   ``` TypeScript
   try {
     // 注册ON_START回调，当后台加载任务启动时触发funCallBack
     this.callee.on(backgroundLoader.ON_START, funCallBack);
     // 注册ON_STOP回调，当后台加载任务停止时触发onStopCallBack
     this.callee.on(backgroundLoader.ON_STOP, onStopCallBack);
   } catch (error) {
     console.error(`Callee.on catch error, error.code: ${error.code}, error.message: ${error.message}`);
   }
   ```

   <p class="same-source-code-link"><a href="https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets?same_code_link_text=backgroundLoader_register_callee" target="_blank" rel="nofollow">EntryAbility.ets</a></p>

   </div>

### 注册后台加载任务

1. 导入模块。

   ``` TypeScript
   import { backgroundLoader } from '@kit.BackgroundTasksKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. 注册后台加载任务。

   <!-- @[backgroundLoader_registerTask](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets) -->

   <div class="same-source-code">

   ``` TypeScript
   const taskInfo: backgroundLoader.TaskInfo = {
     abilityname: abilityname,
     taskId: taskId
   };
   try {
     backgroundLoader.registerTask(taskInfo);
     hilog.info(DOMAIN, 'testTag', 'registerTask successes');
     return 'Success';
   } catch (err) {
     const errMsg = JSON.stringify(err);
     hilog.error(DOMAIN, 'testTag', 'registerTask failed: %{public}s', errMsg);
     return `Failed: ${(err as BusinessError).message ?? errMsg}`;
   }
   ```

   <p class="same-source-code-link"><a href="https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets?same_code_link_text=backgroundLoader_registerTask" target="_blank" rel="nofollow">EntryAbility.ets</a></p>

   </div>

3. 取消注册后台加载任务。

   <!-- @[backgroundLoader_unregisterTask](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets) -->

   <div class="same-source-code">

   ``` TypeScript
   const taskInfo: backgroundLoader.TaskInfo = {
     abilityname: abilityname,
     taskId: taskId
   };
   try {
     backgroundLoader.unregisterTask(taskInfo);
     hilog.info(DOMAIN, 'testTag', 'unregisterTask successes');
     return 'Success';
   } catch (err) {
     const errMsg = JSON.stringify(err);
     hilog.error(DOMAIN, 'testTag', 'unregisterTask failed: %{public}s', errMsg);
     return `Failed: ${(err as BusinessError).message ?? errMsg}`;
   }
   ```

   <p class="same-source-code-link"><a href="https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets?same_code_link_text=backgroundLoader_unregisterTask" target="_blank" rel="nofollow">EntryAbility.ets</a></p>

   </div>

4. 查询后台加载任务信息。

   <!-- @[backgroundLoader_getTaskInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets) -->

   <div class="same-source-code">

   ``` TypeScript
   try {
     const taskInfoData = backgroundLoader.getTaskInfo(taskId);
     const result = `taskId=${taskInfoData.taskId}, abilityName=${taskInfoData.abilityName}`;
     hilog.info(DOMAIN, 'testTag', 'getTaskInfo result: %{public}s', result);
     return result;
   } catch (err) {
     const errMsg = JSON.stringify(err);
     hilog.error(DOMAIN, 'testTag', 'getTaskInfo failed: %{public}s', errMsg);
     return `Failed: ${(err as BusinessError).message ?? errMsg}`;
   }
   ```

   <p class="same-source-code-link"><a href="https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets?same_code_link_text=backgroundLoader_getTaskInfo" target="_blank" rel="nofollow">EntryAbility.ets</a></p>

   </div>

5. 完成后台加载任务。

   <!-- @[backgroundLoader_finishTask](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets) -->

   <div class="same-source-code">

   ``` TypeScript
   const taskInfo: backgroundLoader.TaskInfo = {
     abilityname: abilityname,
     taskId: taskId
   };
   try {
     backgroundLoader.finishTask(taskInfo);
     hilog.info(DOMAIN, 'testTag', 'finishTask successes');
     return 'Success';
   } catch (err) {
     const errMsg = JSON.stringify(err);
     hilog.error(DOMAIN, 'testTag', 'finishTask failed: %{public}s', errMsg);
     return `Failed: ${(err as BusinessError).message ?? errMsg}`;
   }
   ```

   <p class="same-source-code-link"><a href="https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/BackgroundLoader/entry/src/main/ets/entryability/EntryAbility.ets?same_code_link_text=backgroundLoader_finishTask" target="_blank" rel="nofollow">EntryAbility.ets</a></p>

   </div>

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
