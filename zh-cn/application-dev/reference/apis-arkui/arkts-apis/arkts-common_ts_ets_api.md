# common_ts_ets_api(System API)

/*
 Copyright (c) 2022-2023 Huawei Device Co., Ltd.
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
| [AppStorage](arkts-arkui-appstorage-c.md) | AppStorage是与应用进程绑定的全局UI状态存储中心，由UI框架在应用启动时创建，将UI状态数据存储于运行内存，实现应用级全局状态共享。具体UI使用说明，详见 [AppStorage：应用全局的UI状态存储](../../../ui/state-management/arkts-appstorage.md)。 |
| [Environment](arkts-arkui-environment-c.md) | Environment提供设备环境状态的查询能力，可将系统环境变量（如深浅色模式、语言、字体缩放、布局方向等）注入AppStorage，使应用能够感知和响应设备环境变化。具体UI使用说明，详见 [Environment：设备环境查询](../../../ui/state-management/arkts-environment.md)。 |
| [LocalStorage](arkts-arkui-localstorage-c.md) | LocalStorage是页面级的UI状态存储，通过[@Entry](../../../reference/apis-arkui/arkui-ts/ts-universal-entry.md#entry)装饰器接收的参数可以在页面内 共享同一个LocalStorage实例。具体UI使用说明，详见[LocalStorage：页面级UI状态存储](../../../ui/state-management/arkts-localstorage.md)。 |
| [PersistentStorage](arkts-arkui-persistentstorage-c.md) | PersistentStorage提供了UI状态的持久化存储能力，将选定的AppStorage属性持久化到文件中，在应用重启时从文件中恢复这些属性值并写入到AppStorage。具体UI使用说明，详见 [PersistentStorage：持久化存储UI状态](../../../ui/state-management/arkts-persiststorage.md)。 |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md) | SubscribedAbstractProperty是[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中属性的单/双向同步绑定对象，用于与AppStorage/LocalStorage中的属性建立数据同 步关系。SubscribedAbstractProperty实例需要通过[aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#aboutToBeDeleted)接口手动释放，以取消同步 关系并无效化实例。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Environment](arkts-arkui-environment-c-sys.md) | Environment提供设备环境状态的查询能力，可将系统环境变量（如深浅色模式、语言、字体缩放、布局方向等）注入AppStorage，使应用能够感知和响应设备环境变化。具体UI使用说明，详见 [Environment：设备环境查询](../../../ui/state-management/arkts-environment.md)。 |
| [PersistentStorage](arkts-arkui-persistentstorage-c-sys.md) | PersistentStorage提供了UI状态的持久化存储能力，将选定的AppStorage属性持久化到文件中，在应用重启时从文件中恢复这些属性值并写入到AppStorage。具体UI使用说明，详见 [PersistentStorage：持久化存储UI状态](../../../ui/state-management/arkts-persiststorage.md)。 |
| [SubscribaleAbstract](arkts-arkui-subscribaleabstract-c-sys.md) | 可订阅抽象类，用于管理所持有的属性集合，提供属性的添加、删除和变更通知能力。 |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c-sys.md) | SubscribedAbstractProperty是[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中属性的单/双向同步绑定对象，用于与AppStorage/LocalStorage中的属性建立数据同 步关系。SubscribedAbstractProperty实例需要通过[aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#aboutToBeDeleted)接口手动释放，以取消同步 关系并无效化实例。 |
| [SyncedPropertyOneWay](arkts-arkui-syncedpropertyoneway-c-sys.md) | 继承自[SubscribedAbstractProperty\&lt;T\&gt;](arkts-arkui-subscribedabstractproperty-c.md#SubscribedAbstractProperty（系统接口）)。用于接收父组件状态值的单向同步，当父组件状态变化时更新自身值。 |
| [SyncedPropertyTwoWay](arkts-arkui-syncedpropertytwoway-c-sys.md) | 继承自[SubscribedAbstractProperty\&lt;T\&gt;](arkts-arkui-subscribedabstractproperty-c.md#SubscribedAbstractProperty（系统接口）)。用于实现父子组件之间的双向状态数据同步。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AbstractProperty](arkts-arkui-abstractproperty-i.md) | AbstractProperty是AppStorage/LocalStorage中属性的引用，提供读取、修改所引用属性数据及查询属性名的能力。与SubscribedAbstractProperty不同，AbstractProperty 实例无需手动释放。 |
| [EnvPropsOptions](arkts-arkui-envpropsoptions-i.md) | 用于指定环境变量名称及其默认值的键值对对象，作为[envProps](../../apis-crypto-architecture-kit/arkts-apis/arkts-cryptoarchitecture-cryptoframework-eccsignaturespec-i.md#s)参数传入。 |
| [PersistPropsOptions](arkts-arkui-persistpropsoptions-i.md) | 用于指定持久化属性及其默认值的键值对对象，作为[persistProps](../../apis-crypto-architecture-kit/arkts-apis/arkts-cryptoarchitecture-cryptoframework-eccsignaturespec-i.md#s)参数传入。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | 属性订阅者接口，定义订阅者需要实现的方法，用于接收属性变化通知和生命周期回调。 |
| [ISinglePropertyChangeSubscriber](arkts-arkui-isinglepropertychangesubscriber-i-sys.md) | 继承自[IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md#IPropertySubscriber（系统接口）)。用于订阅单个属性值的变化，当被订阅的属性发生变化时接收通知。 |
<!--DelEnd-->

