# @ohos.bytrace(性能打点)

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


**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 8

**替代接口：** [hiTraceMeter](arkts-hitracemeter.md#@ohos.hiTraceMeter(性能打点))

<!--Device-unnamed-declare namespace bytrace--><!--Device-unnamed-declare namespace bytrace-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [finishTrace](arkts-performanceanalysis-bytrace-finishtrace-f.md#finishTrace) | 标记一个时间片跟踪事件的结束。 |
| [startTrace](arkts-performanceanalysis-bytrace-starttrace-f.md#startTrace) | 标记一个时间片跟踪任务的开始。 如果有多个相同name的任务需要追踪或者对同一个任务要追踪多次，并且这些跟踪任务会同时被执行，则每次调用startTrace的taskId必须不一致。如果 具有相同name的跟踪任务是串行执行的，则taskId可以相同。在下面bytrace.finishTrace的示例中会举例说明。 |
| [traceByValue](arkts-performanceanalysis-bytrace-tracebyvalue-f.md#traceByValue) | 标记预追踪耗时任务的数值变量，该变量的数值会不断变化。traceByValue可独立使用，用于记录某个数值变量的变化轨迹。 |

