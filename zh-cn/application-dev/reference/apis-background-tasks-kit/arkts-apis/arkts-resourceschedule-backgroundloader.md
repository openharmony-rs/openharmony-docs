# @ohos.resourceschedule.backgroundLoader

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


**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace backgroundLoader--><!--Device-unnamed-declare namespace backgroundLoader-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [finishTask](arkts-backgroundtasks-backgroundloader-finishtask-f.md#finishTask) | 结束后台加载任务。 |
| [getTaskInfo](arkts-backgroundtasks-backgroundloader-gettaskinfo-f.md#getTaskInfo) | 获取后台预取任务信息。 |
| [registerTask](arkts-backgroundtasks-backgroundloader-registertask-f.md#registerTask) | 注册后台加载任务。 使用 callee.on(ON_START)来接受系统测触发的任务 |
| [unregisterTask](arkts-backgroundtasks-backgroundloader-unregistertask-f.md#unregisterTask) | 取消注册后台加载任务。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [TaskInfo](arkts-backgroundtasks-backgroundloader-taskinfo-i.md) | 任务信息 |
| [TaskStopInfo](arkts-backgroundtasks-backgroundloader-taskstopinfo-i.md) | 停止任务的信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StopCode](arkts-backgroundtasks-backgroundloader-stopcode-e.md) | 枚举停止代码， 用于ON_STOP函数。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [ON_START](arkts-backgroundtasks-backgroundloader-con.md#ON_START) | 监听任务启动的方法 |
| [ON_STOP](arkts-backgroundtasks-backgroundloader-con.md#ON_STOP) | 监听任务结束的方法 |

