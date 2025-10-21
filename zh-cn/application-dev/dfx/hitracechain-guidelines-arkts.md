# 使用HiTraceChain打点（ArkTS）

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @qq_437963121-->
<!--Designer: @kutcherzhou1; @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## 接口说明

分布式跟踪接口由HiTraceChain模块提供，详细API请参考[分布式跟踪ArkTS API](../reference/apis-performance-analysis-kit/js-apis-hitracechain.md)。

| 接口名 | 描述 |
| -------- | -------- |
| hiTraceChain.begin(name: string, flags?: number = HiTraceFlag.DEFAULT): HiTraceId | 开始跟踪，并返回创建的HiTraceId。 |
| hiTraceChain.end(id: HiTraceId): void | 结束跟踪。 |
| hiTraceChain.getId(): HiTraceId | 获取跟踪标识。 |
| hiTraceChain.setId(id: HiTraceId): void | 设置跟踪标识。 |
| hiTraceChain.clearId(): void | 清除跟踪标识。 |
| hiTraceChain.createSpan(): HiTraceId | 创建跟踪分支。创建一个HiTraceId，使用当前线程TLS中的chainId、spanId初始化HiTraceId的chainId、parentSpanId，并为HiTraceId生成一个新的spanId，返回该HiTraceId。 |
| hiTraceChain.isValid(id: HiTraceId): boolean | 判断HiTraceId是否有效。<br/>true：HiTraceId有效；false：HiTraceId无效。 |
| hiTraceChain.isFlagEnabled(id: HiTraceId, flag: HiTraceFlag): boolean | 判断HiTraceId中指定的跟踪标志是否已启用。<br/>true：指定的跟踪标志已启用；false：指定的跟踪标志未启用。 |
| hiTraceChain.enableFlag(id: HiTraceId, flag: HiTraceFlag): void | 启用HiTraceId中指定的跟踪标志。 |
| hiTraceChain.tracepoint(mode: HiTraceCommunicationMode, type: HiTraceTracepointType, id: HiTraceId, msg?: string): void | HiTraceMeter跟踪信息埋点。 |


## 开发步骤

HiTraceChain在ArkTS中的使用方法参考以下示例，开发者可参考[约束与限制](hitracechain-intro.md#约束与限制)，了解常见的支持与不支持HiTraceChain自动传递的机制。


### async/await和promise/then异步任务中使用HiTraceChain

async/await和promise/then异步任务支持HiTraceChain自动传递，示例结合[应用事件订阅](hiappevent-watcher-app-events-arkts.md)和[HiTraceMeter性能跟踪](hitracemeter-guidelines-arkts.md)，说明分布式跟踪在ArkTS中的使用方法。

1. 在DevEco Studio中新建工程，选择“Empty Ability”，SDK版本选择19及以上（示例工程使用的HiTraceMeter接口从API version 19开始支持），工程的目录结构如下：
   ```txt
   ├── entry
   │   ├── src
   │       ├── main
   │       │   ├── ets
   │       │   │   ├── entryability
   │       │   │   │   └── EntryAbility.ets
   │       │   │   ├── entrybackupability
   │       │   │   │   └── EntryBackupAbility.ets
   │       │   │   └── pages
   │       │   │       └── Index.ets
   ```

2. 编辑“entry &gt; src &gt; main &gt; ets &gt; pages &gt; Index.ets”文件，使用HiTraceChain跟踪异步任务，完整的示例代码如下：

   <!-- @[hitracechain_arkts_sample_code_a](https://gitcode.com/openharmony/applications_app_samples/blob/master//code/DocsSample/PerformanceAnalysisKit/HiTrace/HitraceChain_ArkTS_Sample_A/entry/src/main/ets/pages/Index.ets) -->
   
3. 点击DevEco Studio界面中的运行按钮，运行应用工程。在DevEco Studio Terminal窗口中执行以下命令，捕获10秒内的应用trace，并使用关键字“onClick”过滤示例代码中hiTraceMeter.startSyncTrace和hiTraceMeter.finishSyncTrace生成的trace日志。

   ```shell
   PS D:\xxx\xxx> hdc shell
   $ hitrace -t 10 app | grep onClick
   ```

4. 点击设备上的“clickTime=0”按钮（需在10秒内完成，否则步骤3捕获不到trace数据），触发业务逻辑。

5. 查看运行结果。
   - 设备屏幕上按钮显示“clickTime=1”，表示点击了按钮一次，已触发业务逻辑。
   - 在DevEco Studio Log窗口查看分布式跟踪的相关信息。
      - 示例所有hilog打印均使用了“testTag”，因此可以使用关键字“testTag”过滤日志，查看该业务代码打印的hilog日志。

         ```txt
         06-04 17:46:45.156   55451-55451   C02D33/com.exa...tion/HiTraceC  com.examp...lication  I     [a92ab116052648e 0 0]HiTraceBegin name:testTag: hiTraceChain begin flags:0x01.
         06-04 17:46:45.157   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab116052648e 0 0]promise task
         06-04 17:46:45.158   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab116052648e 0 0]test1_1
         06-04 17:46:45.158   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab116052648e 0 0]test2
         06-04 17:46:45.158   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     hiTraceChain end in main thread
         06-04 17:46:45.158   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab116052648e 3457eff 0]test1_2
         06-04 17:46:45.158   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab116052648e 3457eff 0]test3
         06-04 17:46:45.158   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  E     [a92ab116052648e 1bb5a1b 35d9c46]Random number is too small
         06-04 17:46:45.158   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     hiTraceChain end in promise/then
         06-04 17:46:45.158   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab116052648e 2ddfb70 3457eff]test1_3
         06-04 17:46:45.158   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab116052648e 225a1d9 2ddfb70]then task
         06-04 17:46:45.158   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     hiTraceChain end in async/await
         06-04 17:46:45.163   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab116052648e 3a75cb2 520a92]Succeeded in writing an app event
         06-04 17:46:45.163   55451-55451   A00000/com.exa...ation/testTag  com.examp...lication  I     hiTraceChain end in hiAppEvent
         ```

      - hilog日志前附加的[chainId spanId parentSpanId]格式的信息即为HiTraceId信息，例如[a92ab116052648e 2ddfb70 3457eff]表示跟踪链标识chainId值为a92ab116052648e，分支标识spanId值为2ddfb70，父分支标识parentSpanId值为3457eff。
      - 示例得到的跟踪链标识chainId值为a92ab116052648e，可使用chainId值过滤日志，查看业务完整的调用链hilog日志。
      - promise/then和async/await异步机制都会自动传递HiTraceId，并生成分支标识，例如示例hilog日志中的3457eff、2ddfb70、225a1d9等，均为异步任务自动生成的分支标识。
      - hiTraceChain.end()和hiTraceChain.clear()都可以结束跟踪，跟踪结束后，hilog日志不再携带HiTraceId信息。

   - 在DevEco Studio Terminal窗口查看trace数据，HiTraceChain跟踪开启期间，HiTraceMeter打点得到的trace日志会自动携带HiTraceId信息。

      ```txt
       e.myapplication-55451   (  55451) [010] .... 27164.174417: tracing_mark_write: B|55451|H:[a92ab116052648e,0,0]#onClick|M62|clickTime=1
      ```


### 异步宏任务setInterval和setTimeout中使用HiTraceChain

异步宏任务setInterval和setTimeout不支持HiTraceChain自动传递，以下示例说明如何使用hiTraceChain.getId()、hiTraceChain.setId()接口传递HiTraceId，如何使用hiTraceChain.createSpan()接口创建分支标识，进行分布式跟踪。

1. 在DevEco Studio中新建工程，选择“Empty Ability”，工程的目录结构如下：

   ```txt
   ├── entry
   │   ├── src
   │       ├── main
   │       │   ├── ets
   │       │   │   ├── entryability
   │       │   │   │   └── EntryAbility.ets
   │       │   │   ├── entrybackupability
   │       │   │   │   └── EntryBackupAbility.ets
   │       │   │   └── pages
   │       │   │       └── Index.ets
   ```

2. 编辑工程中的“entry &gt; src &gt; main &gt; ets &gt; pages &gt; Index.ets”文件，使用HiTraceChain跟踪异步任务，完整的示例代码如下：

   <!-- @[hitracechain_arkts_sample_code_b](https://gitcode.com/openharmony/applications_app_samples/blob/master//code/DocsSample/PerformanceAnalysisKit/HiTrace/HitraceChain_ArkTS_Sample_B/entry/src/main/ets/pages/Index.ets) -->
   
3. 点击DevEco Studio界面中的运行按钮，运行应用工程，点击设备上“clickTime=0”按钮，触发业务逻辑。

4. 查看运行结果。
   - 设备屏幕上按钮显示“clickTime=1”，表示点击了按钮一次，已触发业务逻辑。
   - 在DevEco Studio Log窗口查看分布式跟踪的相关信息。
      - 示例所有hilog打印均使用了“testTag”，因此可以使用关键字“testTag”过滤日志，查看该业务代码打印的hilog日志。

         ```txt
         06-05 15:46:04.544   49568-49568   A00000/com.exa...ation/testTag  com.examp...lication  I     HiTraceId is invalid, begin hiTraceChain
         06-05 15:46:04.544   49568-49568   C02D33/com.exa...tion/HiTraceC  com.examp...lication  I     [a92ab34b3c84ea7 0 0]HiTraceBegin name:testTag: hiTraceChain begin flags:0x00.
         06-05 15:46:04.544   49568-49568   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab34b3c84ea7 0 0]HiTraceFlag INCLUDE_ASYNC is enabled
         06-05 15:46:04.544   49568-49568   A00000/com.exa...ation/testTag  com.examp...lication  I     hiTraceChain end in main thread
         06-05 15:46:05.547   49568-49568   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab34b3c84ea7 0 0]Interval 1s: randomNumber is 0.863610
         06-05 15:46:06.548   49568-49568   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab34b3c84ea7 0 0]Interval 1s: randomNumber is 0.365460
         06-05 15:46:07.047   49568-49568   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab34b3c84ea7 3cafdfd 0]setTimeout 2.5s
         06-05 15:46:07.048   49568-49568   A00000/com.exa...ation/testTag  com.examp...lication  I     [a92ab34b3c84ea7 dc842f 3cafdfd]Random number is 0.524236
         ```

      - hilog日志前附加的[chainId spanId parentSpanId]格式的信息即为HiTraceId信息，例如[a92ab34b3c84ea7 dc842f 3cafdfd]表示跟踪链标识chainId值为a92ab34b3c84ea7，分支标识spanId值为dc842f，父分支标识parentSpanId值为3cafdfd。
      - 示例得到的chainId值为a92ab34b3c84ea7，可使用chainId值过滤日志，查看业务完整的调用链hilog日志。
