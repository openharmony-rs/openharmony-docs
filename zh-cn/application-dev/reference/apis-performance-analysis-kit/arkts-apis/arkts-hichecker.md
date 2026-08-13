# @ohos.hichecker

/*
 Copyright (c) 2022 Huawei Device Co., Ltd.
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

<!--Device-unnamed-declare namespace hichecker--><!--Device-unnamed-declare namespace hichecker-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addCheckRule](arkts-performanceanalysis-hichecker-addcheckrule-f.md#addCheckRule) | 添加一条或多条规则到系统，系统根据添加的规则进行检测或反馈，当有相应规则触发时可在hilog中grep HiChecker查看运行信息。 |
| [addRule](arkts-performanceanalysis-hichecker-addrule-f.md#addRule) |  |
| [contains](arkts-performanceanalysis-hichecker-contains-f.md#contains) |  |
| [containsCheckRule](arkts-performanceanalysis-hichecker-containscheckrule-f.md#containsCheckRule) | 当前已添加的规则集中是否包含了某一个特定的规则。如果传入的规则级别为线程级别，则仅在当前线程中进行查询。 |
| [getRule](arkts-performanceanalysis-hichecker-getrule-f.md#getRule) | 获取当前线程规则、进程规则、告警规则的合集。 |
| [removeCheckRule](arkts-performanceanalysis-hichecker-removecheckrule-f.md#removeCheckRule) | 删除一条或多条规则，删除的规则后续将不再生效。 |
| [removeRule](arkts-performanceanalysis-hichecker-removerule-f.md#removeRule) |  |

### 常量

| 名称 | 说明 |
| --- | --- |
| [RULE_CAUTION_PRINT_LOG](arkts-performanceanalysis-hichecker-con.md#RULE_CAUTION_PRINT_LOG) | 告警规则，当有告警时记录日志。 |
| [RULE_CAUTION_TRIGGER_CRASH](arkts-performanceanalysis-hichecker-con.md#RULE_CAUTION_TRIGGER_CRASH) | 告警规则，当有告警时让应用退出。 |
| [RULE_CHECK_ABILITY_CONNECTION_LEAK](arkts-performanceanalysis-hichecker-con.md#RULE_CHECK_ABILITY_CONNECTION_LEAK) | 检测规则，检测是否发生ability泄露。 |
| [RULE_CHECK_ARKUI_PERFORMANCE](arkts-performanceanalysis-hichecker-con.md#RULE_CHECK_ARKUI_PERFORMANCE) | 检测规则，检测arkui性能。 |
| [RULE_THREAD_CHECK_NETWORK_USAGE](arkts-performanceanalysis-hichecker-con.md#RULE_THREAD_CHECK_NETWORK_USAGE) | 检测规则，检测线程是否调用网络耗时接口。 |
| [RULE_THREAD_CHECK_SLOW_PROCESS](arkts-performanceanalysis-hichecker-con.md#RULE_THREAD_CHECK_SLOW_PROCESS) | 检测规则，检测是否有耗时函数被调用。 |

