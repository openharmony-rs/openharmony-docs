# Ability Kit指南配套示例代码
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @ccllee1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

| 场景分类 | Sample名称 | 语言 | 场景介绍 |
| -------- | -------- | -------- | -------- |
| 后台服务 | [AppServiceExtensionAbility](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/AppServiceExtensionAbility) | ArkTS | 使用AppServiceExtensionAbility组件实现后台服务，演示启动、连接、通信及断开等生命周期管理流程。 |
| 独立进程 | [DynamicIsolationProcess](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/DynamicIsolationProcess) | ArkTS | 使用isolationProcess动态指定进程能力，演示同一HAP中UIAbility实例根据运行时状态动态分配到不同进程。 |
| 独立进程 | [ModuleIsolationProcess](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/ModuleIsolationProcess) | ArkTS | 使用isolationMode配置模块独立进程，演示多HAP应用中不同HAP的UIAbility运行在各自独立进程中。 |
| 独立进程 | [StaticIsolationProcess](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/StaticIsolationProcess) | ArkTS | 使用process字段静态指定进程，演示同一应用中UIAbility通过配置运行到不同独立进程。 |
| 应用启动框架 | [AppStartup](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/AppStartup) | ArkTS | 使用AppStartup框架支持任务异步启动，演示在配置文件中统一设置启动任务执行顺序与依赖关系。 |
| 应用启动框架 | [AppStartupModule](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/AppStartupModule) | ArkTS | 使用AppStartup框架在HSP和HAR中实现跨模块启动任务依赖管理，演示多模块场景下的初始化任务编排。 |
| 应用退出 | [GuideForAppExit](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/GuideForAppExit) | ArkTS | 使用terminateSelf方法和返回键监听实现应用退出，演示UIAbility主动终止与返回键自定义处理场景。 |
| 应用重启 | [restartapp](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/restartapp) | ArkTS | 使用ApplicationContext的restartApp方法重启应用，演示配置变更后重启使新配置生效的场景。 |
| 异常退出原因 | [UnexpExit](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/UnexpExit) | ArkTS | 使用launchParam参数获取上次异常退出的原因和应用状态信息，演示rss、pss等内存数据与退出时间的读取。 |
| 子进程 | [ArkTsChildProcess](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/ArkTsChildProcess) | ArkTS、C/C++ | 使用startChildProcess创建ArkTS子进程，演示Promise回调和callback两种方式及参数传递。 |
| 子进程 | [NativeChildProcessParams](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/NativeChildProcessParams) | ArkTS、C/C++ | 使用Native子进程接口创建支持参数传递的子进程，演示字符串和fd句柄参数的传递。 |
| 子进程 | [KillChildProcess](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/KillChildProcess) | C/C++ | 使用OH_Ability_KillChildProcess接口杀死子进程，演示父进程根据pid终止子进程的方法。 |
| 子进程 | [NativeChildProcessExit](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/NativeChildProcessExit) | C/C++ | 使用回调函数监听子进程退出，演示获取Native子进程异常退出信息的方法。 |
| 子进程 | [NativeChildProcessIpc](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Ability/NativeChildProcessIpc) | C/C++ | 使用Native子进程接口创建支持IPC通信的子进程，演示父子进程间IPC通道的建立。 |
