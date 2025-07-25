# Performance Analysis Kit（性能分析服务）<!--performance-analysis-kit-->

- [Performance Analysis Kit简介](performance-analysis-kit-overview.md)
- 故障检测<!--fault-analysis-->
  - [简介](fault-detection-overview.md)
  - 崩溃检测<!--crash-detection-->
    - [崩溃检测概述](crash-detection-overview.md)
    - [JS Crash（进程崩溃）检测](jscrash-guidelines.md)
    - [Cpp Crash（进程崩溃）检测](cppcrash-guidelines.md)
  - [AddrSanitizer（地址越界）检测](address-sanitizer-guidelines.md)
  - [AppFreeze（应用冻屏）检测](appfreeze-guidelines.md)
  - [任务超时检测](apptask-timeout-guidelines.md)
  - [应用查杀检测](appkilled-guidelines.md)
- 日志打印<!--hilog-dev-->
  - [使用HiLog打印日志（ArkTS）](hilog-guidelines-arkts.md)
  - [使用HiLog打印日志（C/C++）](hilog-guidelines-ndk.md)
- 事件订阅<!--hiappevent-->
  - [HiAppEvent介绍](hiappevent-intro.md)
  - 使用Hiappevent订阅事件<!--event-subscription-->
    - [事件订阅简介](event-subscription-overview.md)
    - [事件订阅（ArkTS）](hiappevent-watcher-app-events-arkts.md)
    - [事件订阅（C/C++）](hiappevent-watcher-app-events-ndk.md)
    - 系统事件<!--system-events-->
      - 崩溃事件<!--crash-events-->
        - [崩溃事件介绍](hiappevent-watcher-crash-events.md)
        - [订阅崩溃事件（ArkTS）](hiappevent-watcher-crash-events-arkts.md)
        - [订阅崩溃事件（C/C++）](hiappevent-watcher-crash-events-ndk.md)
      - 应用冻屏事件<!--freeze-events-->
        - [应用冻屏事件介绍](hiappevent-watcher-freeze-events.md)
        - [订阅应用冻屏事件（ArkTS）](hiappevent-watcher-freeze-events-arkts.md)
        - [订阅应用冻屏事件（C/C++）](hiappevent-watcher-freeze-events-ndk.md)
      - 资源泄漏事件<!--resource-leak-events-->
        - [资源泄漏事件介绍](hiappevent-watcher-resourceleak-events.md)
        - [订阅资源泄漏事件（ArkTS）](hiappevent-watcher-resourceleak-events-arkts.md)
        - [订阅资源泄漏事件（C/C++）](hiappevent-watcher-resourceleak-events-ndk.md)
      - 地址越界事件<!--address-sanitizer-events-->
        - [地址越界事件介绍](hiappevent-watcher-address-sanitizer-events.md)
        - [订阅地址越界事件（ArkTS）](hiappevent-watcher-address-sanitizer-events-arkts.md)
        - [订阅地址越界事件（C/C++）](hiappevent-watcher-address-sanitizer-events-ndk.md)
      - 主线程超时事件<!--main-thread-jank-events-->
        - [主线程超时事件介绍](hiappevent-watcher-mainthreadjank-events.md)
        - [订阅主线程超时事件（ArkTS）](hiappevent-watcher-mainthreadjank-events-arkts.md)
        - [订阅主线程超时事件（C/C++）](hiappevent-watcher-mainthreadjank-events-ndk.md)
      - 任务执行超时事件<!--app-hicollie-events-->
        - [任务执行超时事件介绍](hiappevent-watcher-apphicollie-events.md)
        - [订阅任务执行超时事件（C/C++）](hiappevent-watcher-apphicollie-events-ndk.md)
      - 应用查杀事件<!--app-killed-events-->
        - [应用查杀事件介绍](hiappevent-watcher-app-killed-events.md)
        - [订阅应用查杀事件（ArkTS）](hiappevent-watcher-app-killed-events-arkts.md)
        - [订阅应用查杀事件（C/C++）](hiappevent-watcher-app-killed-events-ndk.md)
  <!--Del-->
  - [事件上报](hiappevent-event-reporting.md)
  <!--DelEnd-->
  - [HiAppEvent常见问题](hiappevent-faq.md)
- 性能跟踪<!--hitracemeter-->
  - [HiTraceMeter介绍](hitracemeter-intro.md)
  - [使用HiTraceMeter跟踪性能（ArkTS）](hitracemeter-guidelines-arkts.md)
  - [使用HiTraceMeter跟踪性能（C/C++）](hitracemeter-guidelines-ndk.md)
  - [查看HiTraceMeter日志](hitracemeter-view.md)
- 分布式调用链跟踪<!--hitracechain-->
  - [HiTraceChain介绍](hitracechain-intro.md)
  - [使用HiTraceChain打点（ArkTS）](hitracechain-guidelines-arkts.md)
  - [使用HiTraceChain打点（C/C++）](hitracechain-guidelines-ndk.md)
- 检测模式<!--hichecker-->
  - [使用HiChecker检测问题（ArkTS）](hichecker-guidelines-arkts.md)
- 系统调试信息获取<!--hidebug-->
  - [HiDebug能力概述](hidebug-guidelines.md)
  - [HiDebug接口使用示例(ArkTS)](hidebug-guidelines-arkts.md)
  - [HiDebug接口使用示例(C/C++)](hidebug-guidelines-ndk.md)
- 业务线程超时检测<!--hicollie-->
  - [使用HiCollie检测业务线程卡死卡顿问题（C/C++）](hicollie-guidelines-ndk.md)
  - [使用HiCollie监控函数执行时间超长问题（C/C++）](hicollie-settimer-guidelines-ndk.md)
- 错误管理及应用恢复<!--error-manager-->
  - [错误管理开发指导](errormanager-guidelines.md)
  - [应用恢复开发指导](apprecovery-guidelines.md)
- [Performance Analysis Kit术语](performance-analysis-kit-terminology.md)
- 命令行工具<!--perform-command-line-utilities-->
  - [hdc](hdc.md)
  - [hilog](hilog.md)
  - [hidumper](hidumper.md)
  - [hitrace](hitrace.md)
  - [hiperf](hiperf.md)
  - [hiprofiler](hiprofiler.md)
  <!--Del-->
  - [hisysevent](hisysevent.md)
  - [uinput](uinput.md)
  <!--DelEnd-->
