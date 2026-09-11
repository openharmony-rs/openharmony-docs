# Performance Analysis Kit（性能分析服务）<!--performance-analysis-kit-->

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @mzyan-->
<!--Designer: @liyueric-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

- Performance Analysis Kit简介
- 故障检测<!--fault-analysis-->
  - 简介
  - 崩溃检测<!--crash-detection-->
    - JS Crash（进程崩溃）检测
    - Cpp Crash（进程崩溃）检测
  - AddrSanitizer（地址越界）检测
  - AppFreeze（应用冻屏）检测<!--RP1--><!--RP1End-->
  - 任务超时检测
  - 应用终止检测
  - 通用日志<!--general-log-->
    - 页面切换日志<!--RP2--><!--RP2End-->
- 日志打印<!--hilog-dev-->
  - 使用HiLog打印日志（ArkTS）
  - 使用HiLog打印日志（C/C++）
- 事件订阅<!--hiappevent-->
  - HiAppEvent介绍
  - 使用HiAppEvent订阅事件<!--event-subscription-->
    - 事件订阅简介
    - 事件订阅（ArkTS）
    - 事件订阅（C/C++）
    - 系统事件<!--system-events-->
      - 崩溃事件<!--crash-events-->
        - 崩溃事件介绍
        - 订阅崩溃事件（ArkTS）
        - 订阅崩溃事件（C/C++）
      - 应用冻屏事件<!--freeze-events-->
        - 应用冻屏事件介绍
        - 订阅应用冻屏事件（ArkTS）
        - 订阅应用冻屏事件（C/C++）
      - 应用冻屏告警事件<!--appfreezewarning-events-->
        - 应用冻屏告警事件介绍
        - 订阅应用冻屏告警事件（ArkTS）
        - 订阅应用冻屏告警事件（C/C++）
      - 资源泄漏事件<!--resource-leak-events-->
        - 资源泄漏事件介绍
        - 订阅资源泄漏事件（ArkTS）
        - 订阅资源泄漏事件（C/C++）
      - 地址越界事件<!--address-sanitizer-events-->
        - 地址越界事件介绍
        - 订阅地址越界事件（ArkTS）
        - 订阅地址越界事件（C/C++）
      - 主线程超时事件<!--main-thread-jank-events-->
        - 主线程超时事件介绍
        - 订阅主线程超时事件（ArkTS）
        - 订阅主线程超时事件（C/C++）
      - 任务执行超时事件<!--app-hicollie-events-->
        - 任务执行超时事件介绍
        - 订阅任务执行超时事件（ArkTS）
        - 订阅任务执行超时事件（C/C++）
      - 应用终止事件<!--app-killed-events-->
        - 应用终止事件介绍
        - 订阅应用终止事件（ArkTS）
        - 订阅应用终止事件（C/C++）
      - ArkWeb抛滑丢帧事件<!--scroll-arkweb-fling-jank-events-->
        - ArkWeb抛滑丢帧事件介绍
        - 订阅ArkWeb抛滑丢帧事件（ArkTS）<!--RP3--><!--RP3End-->
  <!--Del-->
  - 事件上报
  <!--DelEnd-->
  - HiAppEvent常见问题
  - 使用FaultLogExtensionAbility订阅事件
- 性能跟踪<!--hitracemeter-->
  - HiTraceMeter介绍
  - 使用HiTraceMeter跟踪性能（ArkTS）
  - 使用HiTraceMeter跟踪性能（C/C++）
  - 查看HiTraceMeter日志
- 分布式调用链跟踪<!--hitracechain-->
  - HiTraceChain介绍
  - 使用HiTraceChain打点（ArkTS）
  - 使用HiTraceChain打点（C/C++）
- 检测模式<!--hichecker-->
  - 使用HiChecker检测问题（ArkTS）
- 系统调试信息获取<!--hidebug-->
  - HiDebug能力概述
  - HiDebug接口使用示例（ArkTS）
  - HiDebug接口使用示例（C/C++）
- 业务线程超时检测<!--hicollie-->
  - 使用HiCollie检测业务线程卡死卡顿问题（C/C++）
  - 使用HiCollie监控函数执行时间超长问题（C/C++）
- 错误管理及应用恢复<!--error-manager-->
  - 错误管理开发指导
  - 应用恢复开发指导
- 应用灰度采集<!--hiretrieval-->
  - HiRetrieval介绍
  - 使用HiRetrieval进行应用灰度采集（ArkTS）
  <!--Del-->
  - HiRetrieval云端功能说明
  <!--DelEnd-->
- Performance Analysis Kit术语<!--RP5--><!--RP5End-->
