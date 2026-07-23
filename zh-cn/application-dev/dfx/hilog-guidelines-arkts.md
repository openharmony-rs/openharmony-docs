# 使用HiLog打印日志（ArkTS）

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @suxunquan-->
<!--Designer: @milkbread123-->
<!--Tester: @yufeifei-->
<!--Adviser: @jinqiuheng-->

在应用开发过程中，可在关键代码处输出日志信息。在运行应用后，通过查看日志信息来分析应用执行情况（如应用是否正常运行、代码运行时序、运行逻辑分支是否正常等）。


系统提供不同的API供开发者调用并输出日志信息，即HiLog与Console。两个API在使用时略有差异，本文重点介绍HiLog的用法，Console的具体用法可查看API参考[Console](../reference/common/js-apis-logs.md)。


## 接口说明

HiLog中定义了DEBUG、INFO、WARN、ERROR、FATAL五种日志级别，并提供了对应的方法输出不同级别的日志，接口如下表所示，具体说明可查阅[@ohos.hilog](../reference/apis-performance-analysis-kit/js-apis-hilog.md)。

| 接口名 | 功能描述 | 
| -------- | -------- |
| ArkTS-Dyn: isLoggable(domain: number, tag: string, level: LogLevel) <br>ArkTS-Sta: isLoggable(domain: int, tag: string, level: LogLevel)| 在打印日志前调用该接口，检查指定领域标识、日志标识和级别的日志是否可以打印。 |
| ArkTS-Dyn: debug(domain: number, tag: string, format: string, ...args: any[]) <br>ArkTS-Sta: debug(domain: int, tag: string, format: string, ...args: RecordData[]) | 输出DEBUG级别日志。仅用于应用/服务调试。<br>在DevEco Studio的terminal窗口或cmd里，通过命令“hdc shell hilog -b D”设置可打印日志的等级为DEBUG。 |
| ArkTS-Dyn: info(domain: number, tag: string, format: string, ...args: any[]) <br>ArkTS-Sta: info(domain: int, tag: string, format: string, ...args: RecordData[]) | 输出INFO级别日志。表示普通的信息。 |
| ArkTS-Dyn: warn(domain: number, tag: string, format: string, ...args: any[]) <br>ArkTS-Sta: warn(domain: int, tag: string, format: string, ...args: RecordData[]) | 输出WARN级别日志。表示存在警告。 |
| ArkTS-Dyn: error(domain: number, tag: string, format: string, ...args: any[]) <br>ArkTS-Sta: error(domain: int, tag: string, format: string, ...args: RecordData[]) | 输出ERROR级别日志。表示存在错误。 |
| ArkTS-Dyn: fatal(domain: number, tag: string, format: string, ...args: any[]) <br>ArkTS-Sta: fatal(domain: int, tag: string, format: string, ...args: RecordData[]) | 输出FATAL级别日志。表示出现致命错误、不可恢复错误。 |
| setMinLogLevel(level: LogLevel) | 设置应用日志打印的最低日志级别，用于拦截低级别日志打印。<br>**说明**：从API version 15开始，支持该接口。 | 
| setLogLevel(level: LogLevel, prefer: PreferStrategy) | 设置当前应用程序进程的最低日志级别。可以配置不同的偏好策略。<br>**说明**：从API version 21开始，支持该接口。 | 
| setOutputType(type: OutputType) | 设置hilog的输出类型。可选择不同的日志输出方式。<br/>**说明**：从API版本26.0.0开始，支持该接口。 | 
| ArkTS-Dyn: setOutputTypeByDomainID(type: OutputType, domainIDs: Array&lt;number&gt;, isExclude: boolean) <br/>ArkTS-Sta: setOutputTypeByDomainID(type: OutputType, domainIDs: Array&lt;int&gt;, isExclude: boolean) | 根据domainIDs设置hilog的输出类型。可选择不同的日志输出方式。<br/>**说明**：从API版本26.0.0开始，支持该接口。 |
| getOutputType() | 返回当前hilog的输出类型。<br/>**说明**：从API版本26.0.0开始，支持该接口。 | 
| clean() | 删除沙箱中的所有hilog日志。<br/>**说明**：从API版本26.0.0开始，支持该接口。 | 
| flush() | 将缓存中的日志强制落盘。<br/>**说明**：从API版本26.0.0开始，支持该接口。 | 
| ArkTS-Dyn: getLogFile(latestSeconds: number) <br/>ArkTS-Sta: getLogFile(latestSeconds: int) | 返回指定最近时间段沙箱中的hilog日志文件路径列表。<br/>**说明**：从API版本26.0.0开始，支持该接口。 | 
| getOutputDir() | 返回hilog日志在沙箱中的路径。<br/>**说明**：从API版本26.0.0开始，支持该接口。 | 

> **注意：**
>
> 如果设置的日志级别低于[全局日志级别](hilog.md#查看和设置日志级别)，setMinLogLevel()设置不生效。
>
> debug版本应用下，setMinLogLevel()和setLogLevel()函数均不生效。
### 参数解析

- **domain**：用于指定输出日志所对应的业务领域，取值范围为0x0000~0xFFFF，开发者可以根据需要进行自定义。

- **tag**：用于指定日志标识，可以为任意字符串，建议标识调用所在的类或者业务行为。tag最多为31字节，超出后会截断。不建议使用中文字符，可能出现乱码或者对齐问题。

- **level**：用于指定日志级别。取值见[LogLevel](../reference/apis-performance-analysis-kit/js-apis-hilog.md#loglevel)。

- **prefer**：用于指定偏好策略。取值见[PreferStrategy](../reference/apis-performance-analysis-kit/js-apis-hilog.md#preferstrategy21)。

- **format**：格式字符串，用于日志的格式化输出。日志打印的格式化参数需按照“%{private flag}specifier”的格式打印。

- **type**：hilog的输出类型，取值见[OutputType](../reference/apis-performance-analysis-kit/js-apis-hilog.md#outputtype)。

- **domainIDs**：设置输出类型的domain列表，取值范围为0x0000~0xFFFF。

- **isExclude**：用于决定domainIDs是否对设置的输出类型生效，true表示排除domainIDs列表，仅对非列表中的domain生效，false表示仅对列表中的domain生效。

- **latestSeconds**：距离现在的时间段，单位是秒，取值范围大于0。

  | 隐私标识符（private flag） | 说明 | 
  | -------- | -------- |
  | private | 表示日志打印结果不可见，输出结果为&lt;private&gt;。 | 
  | public | 表示日志打印结果可见，明文显示参数。 | 
  | 无 | 缺省值默认为private，日志打印结果不可见。 | 

  | 格式说明符（specifier） | 说明 | 示例 | 
  | -------- | -------- | -------- |
  | d/i | 支持打印number和bigint类型。 | 123 | 
  | s | 支持打印string、undefined、boolean和null类型。 | "123" | 
  | o/O | 支持打印object、undefined和null类型。<br>从API version 20开始，支持该能力。 | { 'name': "Jack", 'age': 22 } | 

  格式字符串中可以设置多个参数，例如格式字符串为“%{public}s World”，“%{public}s”表示参数类型为string的变参标识，具体取值在args中定义。

  debug应用无隐私管控机制，使用上述任意隐私标识符打印日志，都可明文显示参数。

- **args**：可以为0个或多个参数，是格式字符串中参数类型对应的参数列表。参数的数量、类型必须与格式字符串中的标识一一对应。

> **说明：**
>
> - isLoggable()和具体日志打印接口使用的domain和tag应保持一致。
>
> - isLoggable()使用的level，应和具体日志打印接口级别保持一致。
>
> - isLoggable()返回值：如果指定的domain、tag、level日志可以打印则返回true；否则返回false。
>
>   [debug应用](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-compilation-options-customizing-guide#section192461528194916)：不做日志级别管控，所有级别日志都能够正常打印出来；
>
>   [release应用](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-compilation-options-customizing-guide#section192461528194916)：按照全局日志级别管控，当日志的级别不低于全局日志级别时，才能正常打印出来；
>   调试过程中，可手动修改日志级别，参考：[查看和设置日志级别](hilog.md#查看和设置日志级别)。


## 约束与限制

日志最多打印4096字节，超出限制文本将被截断。


## 开发步骤

在按钮中增加一个单击事件，单击按钮时打印日志。

1. 新建一个工程，选择“Empty Ability”。

2. 工程配置界面中，**Model**选择“Stage”，若无Model选项，则无需配置，默认为“Stage”模型。

   ArkTS-Dyn：**Language Version**选择“ArkTS 1.1”。

   ArkTS-Sta：**Language Version**选择“ArkTS 1.2”。

3. 在**Project**窗口单击entry &gt; src &gt; main &gt; ets &gt; pages，打开工程中的Index.ets文件，添加两个按钮，单击按钮打印日志。

   ArkTS-Dyn示例：
   <!-- @[HiLog_ArkTS](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/PerformanceAnalysisKit/Hilog/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { hilog } from '@kit.PerformanceAnalysisKit';
   // ...
   @Entry
   @Component
   struct Index {
     build() {
       Row() {
         Column() {
           // 添加hilog按钮，以响应用户点击
           Button($r('app.string.HiLogArkTS_Button'))
             .type(ButtonType.Capsule)
             .margin({
               top: 20
             })
             .backgroundColor('#0D9FFB')
             .width('40%')
             .height('5%')
             // 按钮绑定onClick事件，点击时打印日志，注意realse hap包默认无法打印debug级别日志
             .onClick(() => {
               //isLoggable是用来判断，domainID和tag是否满足目前的日志级别打印，建议对返回值进行判断
               let ret = hilog.isLoggable(0xFF00, 'testTag', hilog.LogLevel.INFO);
               if (ret) {
                 hilog.info(0xFF00, 'testTag',
                 'A log with a domainID of 0xFF00 and a label of testTag can print logs at the Info level or higher.');
               }
               hilog.info(0xFF00, 'testTag', '%{public}s World %{public}d', 'hello', 3);
               class Person {
                 constructor(name: string, age: number) {
                   this.name = name;
                   this.age = age;
                 }
                 public name: string;
                 public age:  number;
               }
               let peter: Person = new Person('peter', 15);
               hilog.info(0xFF00, 'testTag', 'peter is %{public}o', peter);
               // 设置应用日志最低打印级别，设置完成后，低于Warn级别的日志将无法打印
               hilog.setMinLogLevel(hilog.LogLevel.WARN);
               hilog.info(0xFF00, 'testTag', 'this is an info level log');
               hilog.error(0xFF00, 'testTag', 'this is an error level log');
               // 设置应用日志PREFER_OPEN_LOG策略的最低打印级别，设置完成后，不低于INFO级别的日志都可打印
               hilog.setLogLevel(hilog.LogLevel.INFO, hilog.PreferStrategy.PREFER_OPEN_LOG);
               hilog.info(0xFF00, 'testTag', 'this is an another info level log');
               hilog.error(0xFF00, 'testTag', 'this is an another error level log');
             })
           // 添加沙箱日志按钮，以响应用户点击
           Button($r('app.string.SandboxLogArkTS_Button'))
             .type(ButtonType.Capsule)
             .margin({
               top: 20
             })
             .backgroundColor('#0D9FFB')
             .width('40%')
             .height('5%')
             // 按钮绑定onClick事件，点击时打印日志，注意realse hap包默认无法打印debug级别日志
             .onClick(() => {
               // 设置日志输出类型SHARE_SANDBOX_WITH_CONSOLE，同时输出公有沙箱和控制台
               hilog.setOutputType(hilog.OutputType.SHARE_SANDBOX_WITH_CONSOLE);
               let lastType = hilog.getOutputType();
               hilog.info(0xFF00, 'testTag', 'current log type:%{public}d', lastType);
               let dir = hilog.getOutputDir();
               hilog.info(0xFF00, 'testTag', 'current log dir:%{public}s', dir);
               hilog.info(0xFF00, 'testTag', 'hilog_info_test');
               hilog.debug(0xFF00, 'testTag', 'hilog_debug_test');
               hilog.warn(0xFF00, 'testTag', 'hilog_warn_test');
               hilog.fatal(0xFF00, 'testTag', 'hilog_fatal_test');
               hilog.error(0xFF00, 'testTag', 'hilog_error_test');
               // 获取沙箱目录中2分钟之内写入过的日志文件
               let logs = hilog.getLogFile(120);
               hilog.info(0xFF00, 'testTag', 'current log files:%{public}s', logs.toString());
               // 将沙箱日志刷入磁盘
               hilog.flush();
             })
   // ...
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```

   ArkTS-Sta示例：
   <!-- @[arkts_static](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/PerformanceAnalysisKit/Hilog_Static/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { Entry, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
   import hilog from '@ohos.hilog'
   
   class Person {
     constructor(name: string, age: number) {
       this.name = name;
       this.age = age;
     }
     public name: string;
     public age:  number;
   }
   
   @Entry
   @Component
   struct Index {
     message: string = 'HiLog ArkTS Static';
     message2: string = 'SandboxLog Static';
   
     build() {
       Row() {
         Column(undefined) {
           // 添加hilog按钮，以响应用户点击
           Button(this.message).backgroundColor('#FFFF00FF')
             .width('40%')
             .height('5%')
             .margin({
               top:20
             })
             .onClick((e: ClickEvent) => {
               let ret = hilog.isLoggable(0xFF00, 'testTag', hilog.LogLevel.INFO);
               if (ret) {
                 hilog.info(0xFF00, 'testTag',
                   'A log with a domainID of 0xFF00 and a label of testTag can print logs at the Info level or higher.');
               }
               hilog.info(0xFF00, 'testTag', '%{public}s World %{public}d', 'hello', 3);
               let peter: Person = new Person('peter', 15);
               hilog.info(0xFF00, 'testTag', 'peter is %{public}o', peter);
               // 设置应用日志最低打印级别，设置完成后，低于Warn级别的日志将无法打印
               hilog.setMinLogLevel(hilog.LogLevel.WARN);
               hilog.info(0xFF00, 'testTag', 'this is an info level log');
               hilog.error(0xFF00, 'testTag', 'this is an error level log');
               // 设置应用日志PREFER_OPEN_LOG策略的最低打印级别，设置完成后，不低于INFO级别的日志都可打印
               hilog.setLogLevel(hilog.LogLevel.INFO, hilog.PreferStrategy.PREFER_OPEN_LOG);
               hilog.info(0xFF00, 'testTag', 'this is an another info level log');
               hilog.error(0xFF00, 'testTag', 'this is an another error level log');
             })
           // 添加沙箱日志按钮，以响应用户点击
           Button(this.message2).backgroundColor('#FFFF00FF')
             .width('40%')
             .height('5%')
             .margin({
               top:20
             })
             .onClick((e: ClickEvent) => {
               // 设置日志输出类型SHARE_SANDBOX_WITH_CONSOLE，同时输出公有沙箱和控制台
               hilog.setOutputType(hilog.OutputType.SHARE_SANDBOX_WITH_CONSOLE);
               let lastType:int = hilog.getOutputType();
               hilog.info(0xFF00, 'testTag', 'current log type:%{public}d', lastType);
               let dir = hilog.getOutputDir();
               hilog.info(0xFF00, 'testTag', 'current log dir:%{public}s', dir);
               hilog.info(0xFF00, 'testTag', 'hilog_info_test');
               hilog.debug(0xFF00, 'testTag', 'hilog_debug_test');
               hilog.warn(0xFF00, 'testTag', 'hilog_warn_test');
               hilog.fatal(0xFF00, 'testTag', 'hilog_fatal_test');
               hilog.error(0xFF00, 'testTag', 'hilog_error_test');
               // 获取沙箱目录中2分钟之内写入过的日志文件
               let logs:string[] = hilog.getLogFile(120);
               hilog.info(0xFF00, 'testTag', 'current log files:%{public}s', logs.toString());
               // 将沙箱日志刷入磁盘
               hilog.flush();
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```

   以输出一条INFO级别的信息为例，表示输出一条普通信息，格式字符串为：

   ```txt
   '%{public}s World %{public}d'
   ```

   其中变参"%{public}s"为公共的字符串，"%{public}d"为公共的整型数。

   如果要输出对象，格式字符串为：

   ```txt
   'peter is %{public}o'
   ```

   其中变参"%{public}o"为公共的对象。

4. 在真机上运行该工程，单击应用/服务界面上的“Next”按钮。

5. 在DevEco Studio的底部，切换到“Log”窗口，设置日志的过滤条件。

   选择当前的设备及进程，日志级别选择Debug，搜索内容设置为“testTag”。此时窗口仅显示符合条件的日志。

   ArkTS-Dyn：点击HiLogArkTS按钮，查看HiLog日志。
   
   ArkTS-Sta：点击HiLogArkTS Static按钮，查看HiLog日志。

   <!--RP3-->
   打印日志结果为：

   ```txt
   08-05 06:32:35.928   10753-10753   A0ff00/testTag                  com.samples.hilog     I     A log with a domainID of 0xFF00 and a label of testTag can print logs at the Info level or higher.
   08-05 06:32:35.928   10753-10753   A0ff00/testTag                  com.samples.hilog     I     hello World 3
   08-05 06:32:35.928   10753-10753   A0ff00/testTag                  com.samples.hilog     I     peter is {"name":"peter","age":15}
   08-05 06:32:35.928   10753-10753   A0ff00/testTag                  com.samples.hilog     E     this is an error level log
   08-05 06:32:35.928   10753-10753   A0ff00/testTag                  com.samples.hilog     I     this is an another info level log
   08-05 06:32:35.928   10753-10753   A0ff00/testTag                  com.samples.hilog     E     this is an another error level log
   ```
   <!--RP3End-->

6. ArkTS-Dyn：点击SandboxLog按钮。
   
   ArkTS-Sta：点击SandboxLog Static按钮。

   搜索内容设置为“testTag”，控制台current log dir打印的即为当前沙箱的路径。

7. 查看沙箱中最新生成的日志文件。

   沙箱日志的内容如下：

   ```txt
   08-05 06:32:35.928 10753 10753 I A0ff00/testTag: current log type:4
   08-05 06:32:35.928 10753 10753 I A0ff00/testTag: current log dir:/data/storage/el2/log/hiapplog
   08-05 06:32:35.929 10753 10753 I A0ff00/testTag: hilog_info_test
   08-05 06:32:35.929 10753 10753 D A0ff00/testTag: hilog_debug_test
   08-05 06:32:35.929 10753 10753 W A0ff00/testTag: hilog_warn_test
   08-05 06:32:35.929 10753 10753 F A0ff00/testTag: hilog_fatal_test
   08-05 06:32:35.929 10753 10753 E A0ff00/testTag: hilog_error_test
   08-05 06:32:35.930 10753 10753 I A0ff00/testTag: current log files:hiapplog.10753.001.20170805-063235.log
   ```

<!--RP1-->
<!--RP1End-->
