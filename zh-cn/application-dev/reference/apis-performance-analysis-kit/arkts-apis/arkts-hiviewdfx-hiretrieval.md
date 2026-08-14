# @ohos.hiviewdfx.hiRetrieval

/*
 Copyright (c) 2026 Huawei Device Co., Ltd.
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


**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-declare namespace hiRetrieval--><!--Device-unnamed-declare namespace hiRetrieval-End-->

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getCurrentConfig](arkts-performanceanalysis-hiretrieval-getcurrentconfig-f.md#getCurrentConfig) | 获取当前应用灰度活动配置。 |
| [getLastParticipationTimestamp](arkts-performanceanalysis-hiretrieval-getlastparticipationtimestamp-f.md#getLastParticipationTimestamp) | 查询此设备上次参与应用灰度活动的UNIX时间戳，如果此设备从未参与则返回0。 |
| [init](arkts-performanceanalysis-hiretrieval-init-f.md#init) | 初始化应用灰度模块。多实例应用不支持调用此接口。 |
| [isParticipant](arkts-performanceanalysis-hiretrieval-isparticipant-f.md#isParticipant) | 查询此设备是否正在参与应用灰度活动。 |
| [participate](arkts-performanceanalysis-hiretrieval-participate-f.md#participate) | 设置此设备参与应用灰度活动。调用后向服务器发送参与灰度消息和应用灰度活动配置，服务器标记此设备为可圈选并记录该应用灰度活动配置作为算法参数。 多次调用将更新为最新的应用灰度活动配置。 |
| [quit](arkts-performanceanalysis-hiretrieval-quit-f.md#quit) | 设置此设备退出应用灰度活动，退出后此设备将无法在云端被圈选。 |
| [run](arkts-performanceanalysis-hiretrieval-run-f.md#run) | 若此设备正在参与应用灰度活动（即已调用participate接口且未调用quit接口），则应用灰度模块开始工作，否则调用该接口不会产生任何效果。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [HiRetrievalConfig](arkts-performanceanalysis-hiretrieval-hiretrievalconfig-i.md) | 应用灰度活动配置。 |

