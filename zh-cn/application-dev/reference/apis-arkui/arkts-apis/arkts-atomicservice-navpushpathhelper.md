# @ohos.atomicservice.NavPushPathHelper(Defines provides a push method for the target page in the routing table.)

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
 ###### 子组件
 无
 ###### 属性
 不支持通用属性。
 ###### 事件
 不支持通用事件


## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [NavPushPathHelper](arkts-arkui-atomicservice-navpushpathhelper-navpushpathhelper-c.md) | 当跳转的目标NavDestination在不同的hsp分包且未被主包依赖时，首次运行原子化服务只会下载安装主包。此时需要使用 NavPushPathHelper先下载安装相应hsp分包，再将指定的NavDestination页面信息入栈或替换当前栈顶页面，从 而使Navigation支持动态加载hsp分包后再跳转。 |

