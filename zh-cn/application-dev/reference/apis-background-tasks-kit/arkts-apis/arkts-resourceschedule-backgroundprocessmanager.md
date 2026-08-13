# @ohos.resourceschedule.backgroundProcessManager(后台子进程管控)

/*
 Copyright (c) 2025 Huawei Device Co., Ltd.
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

<!--Device-unnamed-declare namespace backgroundProcessManager--><!--Device-unnamed-declare namespace backgroundProcessManager-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getPowerSaveMode](arkts-backgroundtasks-backgroundprocessmanager-getpowersavemode-f.md#getPowerSaveMode) | 获取进程能效模式。使用Promise异步回调。 |
| [isPowerSaveMode](arkts-backgroundtasks-backgroundprocessmanager-ispowersavemode-f.md#isPowerSaveMode) | 查询进程是否处于能效模式，使用Promise异步回调。 |
| [resetProcessPriority](arkts-backgroundtasks-backgroundprocessmanager-resetprocesspriority-f.md#resetProcessPriority) | 为子进程解压制，即子进程策略恢复为主进程调度策略。若主进程调度策略发生变化，如从后台切至前台等， 子进程会跟随主进程一同变化，等效于执行一次resetProcessPriority动作。使用Promise异步回调。 |
| [setPowerSaveMode](arkts-backgroundtasks-backgroundprocessmanager-setpowersavemode-f.md#setPowerSaveMode) | 设置进程的能效模式，使用Promise异步回调。 当应用满足以下条件时，可以设置自身是否进入能效模式： - 应用未获取系统焦点，未执行音频或界面刷新操作。 - 无法通过框架层获取电源锁。 - 应用需要执行压缩、解压缩、编译等耗时较长的计算任务，不希望这些任务受到显著的CPU资源限制（即被迫进入能效模式）。 |
| [setProcessPriority](arkts-backgroundtasks-backgroundprocessmanager-setprocesspriority-f.md#setProcessPriority) | 设置子进程的压制档位，子进程被压制后可获得的CPU资源将会受到限制。如果主进程调度策略发生变化，如从后台切至前台等，子进程会跟随主进程一同变化，子进程如需继续压制，需要重新调用本接口。使用Promise异步回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PowerSaveMode](arkts-backgroundtasks-backgroundprocessmanager-powersavemode-e.md) | 能效模式。 |
| [ProcessPriority](arkts-backgroundtasks-backgroundprocessmanager-processpriority-e.md) | 子进程压制档位。 |

