# repeat(Defines Repeat component.)

/*
 Copyright (c) 2024 Huawei Device Co., Ltd.
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


## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RepeatItem](arkts-arkui-repeatitem-i.md) | 数据项类型。 |
| [TemplateOptions](arkts-arkui-templateoptions-i.md) | 当cachedCount值被设置为当前template在容器组件显示区域的最大节点数量时，Repeat会做到最大程度的复用。当容器组件显示区域内没有当前template的节点时，缓存池不会释放，同时应用内存增大。开发者需要根据应用对内 存占用和组件复用效率的需求自行调整，推荐cachedCount值设置为容器组件显示区域内节点个数。需要注意，不建议设置cachedCount小于2，这会导致在快速滑动场景下频繁创建新的节点，从而造成性能劣化。 |
| [VirtualScrollOptions](arkts-arkui-virtualscrolloptions-i.md) | 配置懒加载模式下期望加载的数据项总数、复用能力、数据精准懒加载能力。从API版本26.0.0开始，支持配置内存优化策略。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RepeatMemOptStrategy](arkts-arkui-repeatmemoptstrategy-e.md) | Repeat内存优化策略枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [RepeatArray](arkts-arkui-repeatarray-t.md) | Repeat数据源参数联合类型。 |
| [RepeatInterface](arkts-arkui-repeatinterface-t.md) | Indicates the type of Repeat. |
| [TemplateTypedFunc](arkts-arkui-templatetypedfunc-t.md) |  |

