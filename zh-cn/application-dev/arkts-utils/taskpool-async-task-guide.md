# TaskPool指定任务并发度场景
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

TaskPool支持使用异步队列来控制任务的并发度，能有效避免资源过载，减少任务阻塞，适用于网络请求、视频流处理和数据库操作等场景。

此处提供使用TaskPool创建[异步队列](../reference/apis-arkts/js-apis-taskpool.md#asyncrunner18)的开发指导，以相机预览流采集数据处理的功能为例。

由于处理过程是一个频繁且耗时的任务，当相机采集速度过快时，将丢弃之前的采集数据，仅保留最新的一帧数据进行处理。

1. 导入需要用到的模块。
   <!-- @[taskpool_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/pages/TaskpoolAsyncLevel.ets) -->   
   
   ``` TypeScript
   // TaskpoolAsyncLevel.ets
   import { taskpool } from '@kit.ArkTS';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { PromptAction } from '@kit.ArkUI';
   ```

2. 定义耗时任务。

   <!-- @[collect_frame](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/pages/TaskpoolAsyncLevel.ets) -->   

3. 创建异步队列并执行采集任务。

   <!-- @[trigger_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/pages/TaskpoolAsyncLevel.ets) -->   
