# @ohos.hiTraceMeter(性能打点)

/*
 Copyright (C) 2021 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace hiTraceMeter--><!--Device-unnamed-declare namespace hiTraceMeter-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [finishAsyncTrace](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md#finishAsyncTrace) | 标记一个异步跟踪耗时任务的结束，分级控制跟踪输出。 finishAsyncTrace的level、name和taskId必须与流程开始的[startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md#startAsyncTrace)对应参数值一致。 |
| [finishSyncTrace](arkts-performanceanalysis-hitracemeter-finishsynctrace-f.md#finishSyncTrace) | 标记一个同步跟踪耗时任务的结束，分级控制跟踪输出。 finishSyncTrace的level必须与流程开始的[startSyncTrace()](arkts-performanceanalysis-hitracemeter-startsynctrace-f.md#startSyncTrace)对应参数值一致。 |
| [finishTrace](arkts-performanceanalysis-hitracemeter-finishtrace-f.md#finishTrace) | 标记一个异步跟踪耗时任务的结束。调用成功后，完成该任务的跟踪。 finishTrace的name和taskId必须与流程开始的[startTrace()](arkts-performanceanalysis-hitracemeter-starttrace-f.md#startTrace)对应参数值一致。 从API version 19开始，建议使用[finishAsyncTrace()](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md#finishAsyncTrace)接口（需与 [startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md#startAsyncTrace)接口配套使用）。 |
| [isTraceEnabled](arkts-performanceanalysis-hitracemeter-istraceenabled-f.md#isTraceEnabled) | 判断当前是否开启应用trace捕获。 |
| [registerTraceListener](arkts-performanceanalysis-hitracemeter-registertracelistener-f.md#registerTraceListener) | 注册应用trace捕获开关通知回调，使用callback异步回调。 注册成功后，立即执行一次回调函数，后续回调函数由应用trace捕获开关状态变化触发执行。 回调函数保存在应用进程内，一个进程最多可以注册10个回调函数。若注册的回调包含耗时操作，当回调被执行时，注册或注销行为会被阻塞 （等待回调执行完成）。因此，建议不要在应用主线程中注册或注销包含耗时操作的回调，避免发生应用冻屏。 |
| [startAsyncTrace](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md#startAsyncTrace) | 标记一个异步跟踪耗时任务的开始，分级控制跟踪输出。 如果有多个相同name的任务需要跟踪或者对同一个任务要跟踪多次，并且任务同时被执行，则开发者每次调用startAsyncTrace传入的taskId需不同。 如果具有相同name的任务是串行执行的，则taskId可以相同。具体示例可参考[finishAsyncTrace()](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md#finishAsyncTrace) 中的示例。 |
| [startSyncTrace](arkts-performanceanalysis-hitracemeter-startsynctrace-f.md#startSyncTrace) | 标记一个同步跟踪耗时任务的开始，分级控制跟踪输出。适用于需要跟踪同步代码块执行耗时的场景，能够帮助开发者定位同步操作的耗时问题，优化应用响应 速度。具体示例可参考[finishSyncTrace()](arkts-performanceanalysis-hitracemeter-finishsynctrace-f.md#finishSyncTrace)中的示例。 |
| [startTrace](arkts-performanceanalysis-hitracemeter-starttrace-f.md#startTrace) | 标记一个异步跟踪耗时任务的开始。调用成功后，创建一条异步跟踪记录。 如果有多个相同name的任务需要跟踪或者对同一个任务要跟踪多次，并且任务同时被执行，则开发者每次调用startTrace传入的taskId需不同。 如果具有相同name的任务是串行执行的，则taskId可以相同。具体示例可参考[finishTrace()](arkts-performanceanalysis-hitracemeter-finishtrace-f.md#finishTrace)中的示例。 从API version 19开始，建议使用[startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md#startAsyncTrace)接口（需与 [finishAsyncTrace()](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md#finishAsyncTrace)接口配套使用），以便分级控制跟踪输出与跟踪聚类。 |
| [traceByValue](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md#traceByValue) | 用来标记一个跟踪的整数变量，该变量的数值会不断变化。适用于需要实时监控数值变化（如网络请求次数、缓存命中率、内存占用等）的场景，能够帮助开发者 快速发现异常波动，分析数据趋势。 从API version 19开始，建议使用 [traceByValue](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md#traceByValue)接口，以便分级控 制跟踪输出。 |
| [traceByValue](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md#traceByValue) | 整数跟踪事件，分级控制跟踪输出。用来标记一个预先定义需要跟踪的整数变量名及整数值。 |
| [unregisterTraceListener](arkts-performanceanalysis-hitracemeter-unregistertracelistener-f.md#unregisterTraceListener) | 注销通过registerTraceListener()注册的trace捕获开关通知回调函数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HiTraceOutputLevel](arkts-performanceanalysis-hitracemeter-hitraceoutputlevel-e.md) | 枚举，跟踪输出级别。 低于系统跟踪输出级别阈值的打点将不会生效。log版本阈值为INFO；nolog版本阈值为COMMERCIAL。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [TraceEventListener](arkts-performanceanalysis-hitracemeter-traceeventlistener-t.md) | 定义应用trace捕获开关状态切换时的回调函数类型。 |

