# 事件订阅（ArkTS）

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @junjie_shi-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

HiAppEvent提供了事件订阅接口，用于获取应用的事件。

## 接口说明

API接口使用说明，包括参数使用限制和具体取值范围。请参考[@ohos.hiviewdfx.hiAppEvent (应用事件打点)ArkTS API文档](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md)。

**订阅接口功能介绍**：

| 接口名 | 描述 |
| -------- | -------- |
| addWatcher(watcher: Watcher): AppEventPackageHolder | 添加应用的事件观察者。 |
| removeWatcher(watcher: Watcher): void | 移除应用的事件观察者。 |

> **说明**
>
> addWatcher接口涉及I/O操作。在对性能敏感的业务场景中，开发者应根据实际需要确定该接口是在主线程还是在子线程中调用。
>
> 如果选择在子线程中调用addWatcher，需要确保该子线程在整个接口使用周期内不会被销毁，以免影响接口的正常工作。
>
> 可参考[多线程并发概述](../arkts-utils/multi-thread-concurrency-overview.md)，以实现在子线程中调用接口。

**打点接口功能介绍**：

| 接口名 | 描述 |
| -------- | -------- |
| write(info: AppEventInfo, callback: AsyncCallback&lt;void>): void | 应用事件异步打点方法，使用callback方式作为异步回调。 |
| write(info: AppEventInfo): Promise&lt;void> | 应用事件异步打点方法，使用Promise方式作为异步回调。 |

> **说明**
>
> write接口涉及I/O操作，执行时间通常在毫秒级别。因此，开发者应根据实际业务需求，确定该接口是在主线程还是在子线程中调用。
>
> 可参考[多线程并发概述](../arkts-utils/multi-thread-concurrency-overview.md)，以实现在子线程中调用接口。

## 事件订阅开发指导

以订阅崩溃事件（系统事件）和按钮点击事件（应用事件）为例，说明开发步骤。

1. 新建一个ArkTS应用工程，编辑工程中的“entry > src > main > ets  > entryability > EntryAbility.ets”文件，导入所需的依赖模块：

   <!-- @[AppEvent_Crash_Click_ArkTS_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->

``` TypeScript
import { hiAppEvent, hilog } from '@kit.PerformanceAnalysisKit';
```

2. 编辑工程中的“entry > src > main > ets  > entryability > EntryAbility.ets” 文件，在onCreate函数中添加对崩溃事件、按钮点击事件的订阅。

   订阅崩溃事件，采用OnReceive类型观察者的订阅方式，观察者接收到事件后会立即触发OnReceive()回调。编辑“EntryAbility.ets”文件，定义OnReceive类型观察者相关方法：

   <!-- @[AppEvent_Crash_ArkTS_Add_Watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->

   订阅按钮点击事件，采用OnTrigger类型观察者的订阅方式。需满足triggerCondition设置的条件，才能触发OnTrigger()回调。编辑“EntryAbility.ets”文件，定义OnTrigger类型观察者相关方法：

   <!-- @[AppEvent_Click_ArkTS_Add_Watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->

3. 编辑工程中的“entry > src > main > ets  > pages > Index.ets” 文件，导入依赖模块：

   <!-- @[EventSub_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->

4. 编辑工程中的“entry > src > main > ets  > pages > Index.ets” 文件，新增“WatchAppCrash ArkTS&C++”按钮触发崩溃事件；新增“writeEvent ArkTS”按钮，在按钮点击的函数中进行事件打点。示例代码如下：

   触发崩溃事件。

   <!-- @[AppEvent_Crash_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->

   在按钮点击的函数中进行事件打点。

   <!-- @[AppEvent_Click_ArkTS_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->

## 调测验证

1. 点击DevEco Studio界面中的运行按钮，运行应用工程。在应用界面中点击“WatchAppCrash ArkTS&C++”按钮，触发崩溃事件。应用退出后，重新打开应用。

2. 在HiLog窗口搜索“AppEvents”关键字，查看应用处理崩溃事件数据的日志：

   ```text
   AppEvents HiAppEvent success to read event with onReceive callback from ArkTS
   AppEvents HiAppEvent eventName=APP_CRASH
   AppEvents HiAppEvent eventInfo.params.time=1750747995874
   AppEvents HiAppEvent eventInfo.params.bundle_name="com.example.txxxxx"
   AppEvents HiAppEvent eventInfo.params.external_log=
   ["/data/storage/el2/log/hiappevent/APP_CRASH_1750747996042_28962.log"]
   ```

3. 点击DevEco Studio界面中的运行按钮，运行应用工程。在应用界面中点击“writeEvent ArkTS”按钮，触发按钮点击事件并打点。

4. 在HiLog窗口搜索“AppEvents”关键字，查看应用处理按钮点击事件数据的日志：

   ```text
   AppEvents HiAppEvent success to read event with onTrigger callback from ArkTS
   AppEvents HiAppEvent onTrigger: curRow=1, curSize=121
   AppEvents HiAppEvent eventPkg.packageId=0
   AppEvents HiAppEvent eventPkg.row=1
   AppEvents HiAppEvent eventPkg.size=121
   AppEvents HiAppEvent eventPkg.info={"domain_":"button","name_":"click","type_":4,"time_":1750754529033,"tz_":"","pid_":40664,"tid_":40664,"clickTime":100}
   AppEvents writeEvent ArkTS success
   ```
