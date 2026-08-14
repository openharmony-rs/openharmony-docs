# @ohos.arkui.Prefetcher(Prefetching)

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

### 类

| 名称 | 说明 |
| --- | --- |
| [BasicPrefetcher](arkts-arkui-arkui-prefetcher-basicprefetcher-c.md) | BasicPrefetcher是IPrefetcher的基础实现。它提供了一种智能数据预取算法，以根据屏幕上可见区域的实时变化和预取持续时间的变化来决定应预取哪些数据项。它还可以根据用户的滚动操作来确定哪些预取请求应该被取消。 BasicPrefetcher对象不支持使用JSON序列化。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [IDataSourcePrefetching](arkts-arkui-arkui-prefetcher-idatasourceprefetching-i.md) | 继承自IDataSource。实现该接口，提供具备预取能力的数据源。 |
| [IPrefetcher](arkts-arkui-arkui-prefetcher-iprefetcher-i.md) | 实现此接口以提供预取能力，配合LazyForEach在List、Grid等容器组件滑动浏览时预取数据项，提升用户浏览体验。 |

