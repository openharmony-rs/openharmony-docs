# @ohos.app.ability.appMemoryOptimizer

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

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace appMemoryOptimizer--><!--Device-unnamed-declare namespace appMemoryOptimizer-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [evictFilePages](arkts-ability-appmemoryoptimizer-evictfilepages-f.md#evictFilePages) | 向系统发出释放指定文件的文件页缓存请求，系统会根据当前内存状况决定是否真正执行释放，不保证一定释放成功。 |
| [evictModuleFilePages](arkts-ability-appmemoryoptimizer-evictmodulefilepages-f.md#evictModuleFilePages) | 向系统发出释放指定模块的文件页缓存请求，系统会根据当前内存状况决定是否真正执行释放，不保证一定释放成功。 系统会读取对应模块中的memory_optimizer.json配置文件，获取evictFilePages数组，然后对数组中的文件执行文件页缓存释放操作。 配置文件路径：{模块目录}/src/main/resources/rawfile/memory_optimizer.json 配置文件中evictFilePages数组里的文件名必须以 .so、.hap 或 .hsp 结尾。 |

