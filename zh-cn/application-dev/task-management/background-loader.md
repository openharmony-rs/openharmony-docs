 # 延迟任务(ArkTS)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

## 概述

### 功能介绍

适用于期望通过后台预先加载应用数据实现优化应用启动体验的场景，系统会根据用户使用习惯、频次以及系统资源（内存、电量）等条件，预先启动应用进程并执行加载回调方法允许应用在后台执行短时的内容和数据加载。例如：资讯刷新、消息获取、视频缓存等。


### 运行原理


1、需要启用后台加载任务功能的应用，可在前台启动时向系统注册任务。
2、任务注册后，系统允许应用查询和删除任务。
3、系统的后台加载任务管理模块会根据用户使用应用的习惯及系统状态（包括系统可用内存、电池电量、设备温度等）统一决策应用执行后台加载任务时机。应用无法对任务触发时机进行干预。


### 约束与限制

- **数量限制：** 一个应用只能注册一个后台加载任务，任务中只能指定唯一的主用UIAbility。
  
- **超时：** 系统回调加载任务开始执行时最长运行30秒。如果应用多次超时，系统会禁用该应用，取消后续的任务调度（即使重新注册任务仍然不会再调度了）

- **禁止执行可感知操作 ：** 在UIAbility创建阶段和加载任务执行阶段，禁止应用执行音频播放、音频录制、定位、操作闪光灯等可感知行为。如果系统检测到应用存在此类操作，系统会禁用该应用，取消后续的任务调度。


## 接口说明

**表1** 后台加载任务主要接口

以下是后台加载任务开发使用的相关接口，更多接口及使用方式请见[后台加载任务管理](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md)文档。
| 接口名 | 接口描述 |
| -------- | -------- |
| [registerTask(taskInfo: TaskInfo): void](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloaderregisgertask) | 注册后台加载任务。 |
|[unregisterTask(taskInfo: TaskInfo): void](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloaderunregisgertask) | 取消注册后台加载任务。 |
| [getTaskInfo(taskId: int): Promise&lt;TaskInfo&gt;](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloadergettaskinfo) | 查询注册后台加载任务信息。（Promise形式）。 |
|[finishTask(taskInfo: TaskInfo): void](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloaderfinishtask) | 通知系统加载任务执行完成。 |

**表2** 后台加载任务需要应用实现的回调接口

以下是后台加载任务回调开发使用的相关接口，更多接口及使用方式请见[后台加载任务管理](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md)文档。
| 接口名 | 接口描述 |
| -------- | -------- |
| [ON_START](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloaderon_start) | 需要实现的执行后台加载任务的方法名，系统通过StartAbilityBycall方法启动应用后，会回调此方法。方法的入参为[backgroundLoader.TaskInfo](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#taskinfo) |
| [ON_STOP](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#backgroundloaderon_stop) | 待应用实现的回调方法名。系统在后台加载任务异常取消时。会回调onStop方法。方法的入参为[backgroundLoader.TaskStopInfo](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundLoader.md#taskstopinfo)  |


## 开发步骤

后台加载任务的开发步骤分为三步： 

1. 实现后台加载任务的回调ON_START和ON_STOP函数的定义和声明。

2. 向应用程序框架服务注册后台加载任务的回调函数。

3. 向后台加载任务管理服务注册后台加载任务。

### 实现后台加载任务回调能力

1. 需要声明ohos.permission.KEEP_BACKGROUND_RUNNING权限，配置方式请参见[声明权限](../security/AccessToken/declare-permissions.md#声明权限)
2. 在应用现有的主UIAbility中先导入模块，随后定义声明回调函数、注册回调函数、注册后台加载任务。
   ``` TypeScript
    import { UIAbility, AbilityConstant } from '@kit.AbilityKit';
    import { backgroundLoader } from '@kit.BackgroundTasksKit';
  
    export default class TestAppMainUIAbility extends UIAbility {
        onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
            console.info('Callee onCreate is called');
            try {
                // 01.声明后台预取的回调方法，参数名使用后台预取定义好的回调方法
                this.callee.on(backgroundLoader.ON_START, BackgroundPrefetchOnStart);
                this.callee.on(backgroundLoader.ON_STOP, BackgroundPrefetchOnStop);

                // 02.定义后台预取任务的参数
                let taskInfo: backgroundLoader.TaskInfo = {
                    taskId: 1,
                    abilityName: 'TestAppMainUIAbility'
                }

                // 03.注册启动后台预取任务，系统将任务记录持久化保存，用于后续调度
                backgroundLoader.registerTask(taskInfo);
                console.info('registerTask success');
            } catch (error) {
                console.error(`backgroundLoader.registerTask catch error, code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
            }
        }
    }
   ```


### 后台加载任务触发功能验证
后台任务申请成功之后，需要等到条件满足后才可以执行后台加载任务回调，为了快速验证实现的回调功能是否正确，可以通过以下[hidumper命令](../dfx/hidumper.md)手动触发延迟任务执行回调。

   ```ts
   $ hidumper -s 1901 -a 'backgroundLoader com.example.application EntryAbility'

   -------------------------------[ability]-------------------------------


   ----------------------------------ResourceSched----------------------------------
   ```
