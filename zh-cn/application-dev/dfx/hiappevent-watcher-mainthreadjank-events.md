# 主线程超时事件介绍

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @rr_cn-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## 简介

当应用的主线程执行耗时任务时，开发者会感知到应用卡顿，但卡顿时间未达到系统设定的[应用冻屏](appfreeze-guidelines.md)时间限制，因此不会生成故障日志。为了更好地定位和分析问题，开发者可以查看[主线程超时事件检测原理](apptask-timeout-guidelines.md#检测原理)，根据生成的[主线程超时事件日志规格](apptask-timeout-guidelines.md#日志规格)，分析主线程任务的执行情况。

## 检测原理

详见[主线程超时检测原理](apptask-timeout-guidelines.md#检测原理)

## 接口说明

开发者可以通过HiAppEvent提供的接口订阅主线程超时事件“hiAppEvent.event.MAIN_THREAD_JANK”，系统检测到主线程超时后，会抓取维测信息。开发者通过HiAppEvent监听主线程超时事件，可以在回调函数中获取主线程超时事件相关信息。

- [订阅主线程超时事件（ArkTS）](hiappevent-watcher-mainthreadjank-events-arkts.md)

- [订阅主线程超时事件（C/C++）](hiappevent-watcher-mainthreadjank-events-ndk.md)

> **说明：**
>
> 主线程超时事件支持在[应用分身](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/app-clone)场景下使用 HiAppEvent 进行订阅，支持在原子化服务场景下使用HiAppEvent 进行订阅，从 API version 22 开始支持在[输入法应用](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/inputmethod-application-guide)场景下使用 HiAppEvent 进行订阅。

## 自定义参数

setEventConfig接口不提供主线程超时结束自动停止采样栈的功能；从API version 22开始，提供configEventPolicy接口，该接口提供主线程超时结束自动停止采样栈的功能。

### setEventConfig接口说明

| 接口名 | 描述 |
| -------- | -------- |
| [setEventConfig(name: string, config: Record&lt;string, ParamType>): Promise&lt;void>](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#hiappeventseteventconfig15) | 设置主线程采样栈参数接口。 |

### setEventConfig接口参数设置说明

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 主线程超时事件名称，此处应为常量hiappevent.event.MAIN_THREAD_JANK。 |
| config | Record&lt;string, ParamType> | 是 | 主线程超时采样栈配置参数。 |

主线程超时采样栈配置参数的定义。

> **注意：**
>
> log_type参数为必选项。
>
> log_type=0或2时，不设置其他参数。
>
> log_type=1时，所有参数均需设置。

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| log_type | string | 是 | 采集MAIN_THREAD_JANK事件日志类型。<br/>log_type=0：默认值，主线程连续两次超时150ms~450ms，采集调用栈；主线程超时450ms，采集trace。<br/>log_type=1：仅采集调用栈。<br/>log_type=2：仅采集trace。 |
| sample_interval | string | 否 | 主线程超时检测间隔和采样间隔。<br/>单位为ms，默认值：150，取值范围为[50, 500]。<br/>系统根据开发者设置的sample_interval进行超时检测判断，并使用该sample_interval作为周期性任务检测的间隔。 |
| ignore_startup_time | string | 否 | 忽略启动时间内的主线程超时检测。单位为s，最小值：3，默认值：10。<br/>线程启动一定时间内，不进行超时检测。一些进程启动时间较长，此时抓全的超时采样栈，分析意义不大。因此，在开发者定义启动时间间隔内，不进行超时检测。 |
| sample_count | string | 否 | 主线程超时采样次数。系统检测到当前主线程执行任务时长达到可采样阈值时，开始周期性采集堆栈，每个间隔采集一次堆栈，共采集sample_count次。<br/>默认值：10次。<br/>最小值：1次，最大值需要结合自定义的sample_interval进行动态计算，计算公式：sample_count &lt;= (2500 / sample_interval - 4)。 |
| report_times_per_app | string | 否 | 同一个应用的PID一个生命周期内，主线程超时采样上报次数。一个生命周期内只能设置一次。<br/>默认值：1次，单位：次。<br/>开发者选项打开，每小时范围：[1, 3]。<br/>开发者选项关闭，每天上报次数范围：[1, 3]。 |

1. sample_count说明：

   （1）2500的含义：根据系统规定，主线程超时事件从检测到上报的时间不可以超过2.5s（即：2500ms）。因此sample_count的设置值不能超过系统按计算公式得出的最大值。

   （2）4的含义：第一次超时间隔检测时间 + 第二次超时间隔（系统提供两次再次发生超时事件的检测机会）时间 + 收集并上报堆栈信息的时间。

   （3）开发者要结合需求场景，进行合理的设置。

2. 参数设置示例
   
   展示setEventConfig接口中log_type分别为0，1，2三种类型：

   （1）log_type=0，用于采样栈或采样trace。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';

   let params: Record<string, hiAppEvent.ParamType> = {
     "log_type": "0"
   };
   hiAppEvent.setEventConfig(hiAppEvent.event.MAIN_THREAD_JANK, params).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Setting default value successfully.`);
   }).catch((err: BusinessError) => {
     hilog.error(0x0000, 'hiAppEvent', `Failed to set default value. Code: ${err.code}, message: ${err.message}`);
   });
   ```

   （2）log_type=1，仅用于采集调用栈。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';

   let params: Record<string, hiAppEvent.ParamType> = {
     "log_type": "1",
     "sample_interval": "100",
     "ignore_startup_time": "11",
     "sample_count": "21",
     "report_times_per_app": "3"
   };
   hiAppEvent.setEventConfig(hiAppEvent.event.MAIN_THREAD_JANK, params).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Successfully set sampling stack parameters.`);
   }).catch((err: BusinessError) => {
     hilog.error(0x0000, 'hiAppEvent', `Failed to set sample stack value. Code: ${err.code}, message: ${err.message}`);
   });
   ```

   （3）log_type=2，仅用于采集trace。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';

   let params: Record<string, hiAppEvent.ParamType> = {
     "log_type": "2"
   };
   hiAppEvent.setEventConfig(hiAppEvent.event.MAIN_THREAD_JANK, params).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Set to only collect trace successfully.`);
   }).catch((err: BusinessError) => {
     hilog.error(0x0000, 'hiAppEvent', `Failed to set only collect trace. code: ${err.code}, message: ${err.message}`);
   });
   ```

### configEventPolicy接口说明

| 接口名 | 描述 |
| -------- | -------- |
| [configEventPolicy(policy: EventPolicy): Promise&lt;void>](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#hiappeventconfigeventpolicy22) | 设置主线程采样栈参数接口。支持超时卡顿结束自动停止采样。 |

### configEventPolicy接口参数设置说明

开发者可以使用上述hiappevent提供的接口，在EventPolicy中配置采样栈接口的参数。

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| mainThreadJankPolicy | MainThreadJankPolicy | 是 | 主线程超时事件配置策略。 |

主线程超时事件配置策略的定义。

> **注意：**
>
> 所有参数均为可选项，不设置时取默认值。
>
> logType=0时，仅需配置autoStopSampling参数，其他参数均取默认值，无需设置。
>
> logType=2时，其他参数均不生效，无需设置。

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| logType | number | 否 | 采集日志的类型。默认值：0。<br/>logType=0：其他选项均取默认值，主线程连续两次超时150ms~450ms，采集调用栈；主线程超时450ms，采集trace。<br/>logType=1：仅采集调用栈，触发检测的阈值用户自定义。<br/>logType=2：仅采集trace。 |
| sampleInterval | number | 否 | 主线程超时检测间隔和采样间隔。单位：毫秒，默认值：150，取值范围：[50, 500]。 |
| ignoreStartupTime | number | 否 | 应用启动期间忽略主线程超时检测的时间。单位：秒，默认值：10，最小值：3。 |
| sampleCount | number | 否 | 主线程超时采样次数。单位：次，默认值：10，最小值：1。<br/>最大值需要结合自定义的sampleInterval进行动态计算，计算公式：sampleCount &lt;= (2500 / sampleInterval - 4)。 |
| reportTimesPerApp | number | 否 | 同一个应用的PID一个生命周期内，主线程超时采样上报次数。一个生命周期内只能设置一次。<br/>默认值：1，单位：次。<br/>每分钟上报次数范围：[1, 3]。 |
| autoStopSampling | boolean | 否 | 主线程超时结束时，是否自动停止采样主线程堆栈。<br/>true: 超时结束或达到设置的采样次数，停止采样。<br/>false：达到设置的采样次数时停止采样。<br/>默认值：false。 |

1. sampleCount说明：

   （1）2500的含义：根据系统规定，主线程超时事件从检测到上报的时间不可以超过2.5s（即：2500ms）。因此sampleCount的设置值不能超过系统按计算公式得出的最大值。

   （2）4的含义：第一次超时间隔检测时间 + 第二次超时间隔（系统提供两次再次发生超时事件的检测机会）时间 + 收集并上报堆栈信息的时间。

   （3）开发者要结合需求场景，进行合理的设置。

2. 参数设置示例

   展示configEventPolicy接口中logType分别为0，1，2三种类型：

   （1）logType=0，用于采样栈或采样trace。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';

   let policy: hiAppEvent.EventPolicy = {
     "mainThreadJankPolicy" : {
       "logType": 0,
       "autoStopSampling": true
     }
   };
   hiAppEvent.configEventPolicy(policy).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Setting default value successfully.`);
   }).catch((err: BusinessError) => {
     hilog.error(0x0000, 'hiAppEvent', `Failed to set default value. Code: ${err.code}, message: ${err.message}`);
   });
   ```

   （2）logType=1，仅用于采集调用栈。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';

   let policy: hiAppEvent.EventPolicy = {
     "mainThreadJankPolicy" : {
       "logType": 1,
       "sampleInterval": 70,
       "ignoreStartupTime": 11,
       "sampleCount": 20,
       "reportTimesPerApp": 3,
       "autoStopSampling": true
     }
   };
   hiAppEvent.configEventPolicy(policy).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Successfully set sampling stack parameters.`);
   }).catch((err: BusinessError) => {
     hilog.error(0x0000, 'hiAppEvent', `Failed to set sample stack value. Code: ${err.code}, message: ${err.message}`);
   });
   ```

   （3）logType=2，仅用于采集trace。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';

   let policy: hiAppEvent.EventPolicy = {
     "mainThreadJankPolicy" : {
       "logType": 2
     }
   };
   hiAppEvent.configEventPolicy(policy).then(() => {
     hilog.info(0x0000, 'hiAppEvent', `Set to only collect trace successfully.`);
   }).catch((err: BusinessError) => {
     hilog.error(0x0000, 'hiAppEvent', `Failed to set only collect trace. code: ${err.code}, message: ${err.message}`);
   });
   ```

### OH_HiAppEvent_SetEventConfig接口说明

| 接口名 | 描述 |
| -------- | -------- |
| [int OH_HiAppEvent_SetEventConfig(const char\* name, HiAppEvent_Config\* config)](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md#oh_hiappevent_seteventconfig) | 设置主线程采样栈参数接口。 |

### OH_HiAppEvent_SetEventConfig接口参数设置说明

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | const char\* | 是 | 主线程超时事件名称，此处为预定义的宏EVENT_MAIN_THREAD_JANK或EVENT_MAIN_THREAD_JANK_V2。|
| config | HiAppEvent_Config\* | 是 | 主线程超时采样栈配置参数，可使用[OH_HiAppEvent_SetConfigItem](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md#oh_hiappevent_setconfigitem)函数设置config参数的配置项。 |

**name为EVENT_MAIN_THREAD_JANK**

接口不提供主线程超时结束自动停止采样栈的功能，config参数作如下配置。

> **注意：**
>
> MAIN_THREAD_JANK_PARAM_LOG_TYPE为必选配置项。
>
> MAIN_THREAD_JANK_PARAM_LOG_TYPE为"0"或"2"时，无其他配置项。
>
> MAIN_THREAD_JANK_PARAM_LOG_TYPE为"1"时，所有配置项均需设置。
>
> 配置项的值均为可转换为整型的字符串字面量或字符指针。

对于API version 21及之前的版本，配置项名称只可使用相关字符串。

对于API version 22及之后的版本，配置项名称可使用预定义的宏及相关字符串。更推荐使用宏，避免开发者手写字符串造成非预期结果。

下文中值的取值范围说明均按转换后的变量类型进行阐述。

| 配置项名称 | 类型 | 必须配置 | 说明 |
| -------- | -------- | -------- | -------- |
| 宏：MAIN_THREAD_JANK_PARAM_LOG_TYPE<br/>字符串：log_type | const char\* | 是 | 采集日志的类型。<br/>值为"0"：默认值，主线程连续两次超时150ms~450ms，采集调用栈；主线程超时450ms，采集trace。<br/>值为"1"：仅采集调用栈。<br/>值为"2"：仅采集trace。 |
| 宏：MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL<br/>字符串：sample_interval | const char\* | 否 | 主线程超时检测间隔和采样间隔。<br/>单位为ms，默认值：150，取值范围为[50, 500]。<br/>系统根据开发者设置的MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL的值进行超时检测判断，并使用该值作为周期性任务检测的间隔。 |
| 宏：MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME<br/>字符串：ignore_startup_time | const char\* | 否 | 忽略启动时间内的主线程超时检测。<br/>单位为s，最小值：3，默认值：10。<br/>线程启动一定时间内，不进行超时检测。一些进程启动时间较长，此时抓全的超时采样栈，分析意义不大。因此，在开发者定义启动时间间隔内，不进行超时检测。 |
| 宏：MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT<br/>字符串：sample_count | const char\* | 否 | 主线程超时采样次数。系统检测到当前主线程执行任务时长达到可采样阈值时，开始周期性采集堆栈，每个间隔采集一次堆栈，共采集MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT次。<br/>默认值：10次。<br/>最小值：1次，最大值需要结合自定义的MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL进行动态计算，计算公式：MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT &lt;= (2500 / MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL - 4)。 |
| 宏：MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP<br/>字符串：report_times_per_app | const char\* | 否 | 同一个应用的PID一个生命周期内，主线程超时采样上报次数。一个生命周期内只能设置一次。<br/>默认值：1次，单位：次。<br/>开发者选项打开，每小时范围：[1, 3]。<br/>开发者选项关闭，每天上报次数范围：[1, 3]。 |

1. MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT说明：

   （1）2500的含义：根据系统规定，主线程超时事件从检测到上报的时间不可以超过2.5s（即：2500ms）。因此MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT的设置值不能超过系统按计算公式得出的最大值。

   （2）4的含义：第一次超时间隔检测时间 + 第二次超时间隔（系统提供两次再次发生超时事件的检测机会）时间 + 收集并上报堆栈信息的时间。

   （3）开发者要结合需求场景，进行合理的设置。

2. 参数设置示例
   
   展示OH_HiAppEvent_SetEventConfig接口中config参数的配置项MAIN_THREAD_JANK_PARAM_LOG_TYPE分别为"0"，"1"，"2"三种类型：

   （1）MAIN_THREAD_JANK_PARAM_LOG_TYPE为"0"时，用于采样栈或采样trace。

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"

   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();    
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "0");
   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK, config);
   if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Setting default value successfully.");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```

   （2）MAIN_THREAD_JANK_PARAM_LOG_TYPE为"1"时，仅用于采集调用栈。

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"
   
   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "1");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL, "100");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME, "11");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT, "21");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP, "3");

   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK, config);
   if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Successfully set sampling stack parameters.");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```

   （3）MAIN_THREAD_JANK_PARAM_LOG_TYPE为"2"时，仅用于采集trace。

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"
   
   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "2");

   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK, config);
   if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Set to only collect trace successfully");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```  

**name为EVENT_MAIN_THREAD_JANK_V2**

从API VERSION 22开始，name可以为EVENT_MAIN_THREAD_JANK_V2，接口提供主线程超时结束自动停止采样栈的功能，config参数作如下配置。

> **注意：**
> 
> 配置项名称为相关预定义的宏。
>
> config的所有配置项均为可选项，不配置或者为空时取默认值。
>
> MAIN_THREAD_JANK_PARAM_LOG_TYPE为"0"时，仅需设置MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING，其他配置项均取默认值，无需设置。
>
> MAIN_THREAD_JANK_PARAM_LOG_TYPE为"2"时，其他配置项均不生效，无需设置。
>
>  MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING为"true"或"false"，转换为布尔类型；其他配置项的值均为可转换为整型的字符串字面量或字符指针。

下文中值的取值范围说明均按转换后的变量类型进行阐述。

| 配置项名称 | 类型 | 必须配置 | 说明 |
| -------- | -------- | -------- | -------- |
| MAIN_THREAD_JANK_PARAM_LOG_TYPE | const char\* | 否 | 采集日志的类型。<br/>值为"0"：默认值，主线程连续两次超时150ms~450ms，采集调用栈；主线程超时450ms，采集trace。<br/>值为"1"：仅采集调用栈。<br/>值为"2"：仅采集trace。 |
| MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL | const char\* | 否 | 主线程超时检测间隔和采样间隔。<br/>单位为ms，默认值：150，取值范围为[50, 500]。<br/>系统根据开发者设置的MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL的值进行超时检测判断，并使用该值作为周期性任务检测的间隔。 |
| MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME | const char\* | 否 | 忽略启动时间内的主线程超时检测。<br/>单位为s，最小值：3，默认值：10。<br/>线程启动一定时间内，不进行超时检测。一些进程启动时间较长，此时抓全的超时采样栈，分析意义不大。因此，在开发者定义启动时间间隔内，不进行超时检测。 |
| MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT | const char\* | 否 | 主线程超时采样次数。系统检测到当前主线程执行任务时长达到可采样阈值时，系统检测到当前主线程执行任务超过采样限制后，开始周期性采集堆栈，每个间隔采集一次堆栈，共采集MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT次。<br/>默认值：10次。<br/>最小值：1次，最大值需要结合自定义的MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL进行动态计算，计算公式：MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT &lt;= (2500 / MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL - 4)。 |
| MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP | const char\* | 否 | 同一个应用的PID一个生命周期内，主线程超时采样上报次数。一个生命周期内只能设置一次。<br/>默认值：1次，单位：次。<br/>开发者选项打开，每小时范围：[1, 3]。<br/>开发者选项关闭，每天上报次数范围：[1, 3]。 |
| MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING | const char\* | 否 | 主线程超时结束时，是否自动停止采样主线程堆栈。<br/>true: 超时结束或达到设置的采样次数，停止采样。<br/>false：达到设置的采样次数时停止采样。<br/>默认值：false。 |

1. MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT说明：

   （1）2500的含义：根据系统规定，主线程超时事件从检测到上报的时间不可以超过2.5s（即：2500ms）。因此MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT的设置值不能超过系统按计算公式得出的最大值。

   （2）4的含义：第一次超时间隔检测时间 + 第二次超时间隔（系统提供两次再次发生超时事件的检测机会）时间 + 收集并上报堆栈信息的时间。

   （3）开发者要结合需求场景，进行合理的设置。

2. 参数设置示例
   
   展示OH_HiAppEvent_SetEventConfig接口中config参数的配置项MAIN_THREAD_JANK_PARAM_LOG_TYPE分别为"0"，"1"，"2"三种类型：

   （1）MAIN_THREAD_JANK_PARAM_LOG_TYPE为"0"时，用于采样栈或采样trace。

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"

   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();    
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "0");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING, "true");
   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK_V2, config);
   if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Setting default value successfully.");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```

   （2）MAIN_THREAD_JANK_PARAM_LOG_TYPE为"1"时，仅用于采集调用栈。

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"
   
   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "1");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_SAMPLE_INTERVAL, "100");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_IGNORE_STARTUP_TIME, "11");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_SAMPLE_COUNT, "21");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_REPORT_TIMES_PER_APP, "3");
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_AUTO_STOP_SAMPLING, "true");

   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK_V2, config);
   if (ret == HIAPPEVENT_SUCCESS) {{
       OH_LOG_INFO(LogType::LOG_APP, "Successfully set sampling stack parameters.");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```

   （3）MAIN_THREAD_JANK_PARAM_LOG_TYPE为"2"时，仅用于采集trace。

   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"

   #undef LOG_TAG
   #define LOG_TAG "testTag"
   
   HiAppEvent_Config* config = OH_HiAppEvent_CreateConfig();
   OH_HiAppEvent_SetConfigItem(config, MAIN_THREAD_JANK_PARAM_LOG_TYPE, "2");

   int ret = OH_HiAppEvent_SetEventConfig(EVENT_MAIN_THREAD_JANK_V2, config);
   if (ret == HIAPPEVENT_SUCCESS) {
       OH_LOG_INFO(LogType::LOG_APP, "Set to only collect trace successfully");
   }
   OH_HiAppEvent_DestroyConfig(config);
   ```  

## 事件字段说明

| 名称 | 类型 | 说明 |
| -------- | -------- | -------- |
| time | number | 事件触发时间，单位为ms。 |
| bundle_version | string | 应用版本。 |
| bundle_name | string | 应用名称。 |
| pid | number | 应用的进程id。 |
| uid | number | 应用的用户id。 |
| begin_time | number | 主线程任务开始时间。 |
| end_time | number | 主线程任务结束时间。 |
| external_log | string[] | 主线程超时日志文件路径。**为避免目录空间超限（参考log_over_limit），导致新生成的日志文件写入失败，日志文件处理完后请及时删除。** |
| log_over_limit | boolean | 生成的主线程超时日志文件与已存在的日志文件总大小是否超过10M上限。true表示超过上限，日志写入失败；false表示未超过上限。 |
| app_start_jiffies_time | number | 开发者可以获取主线程超时事件时，任务执行的开始时间。**触发采样栈，打印开始时间信息。** |
| heaviest_stack | string | 生成的主线程超时日志文件中，打印多次的调用栈。**触发采样栈，打印多次的调用栈信息。** |