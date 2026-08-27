# common_ts_ets_api(System API)

## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AppStorage(System API)](arkts-arkui-appstorage-c.md) | AppStorage是与应用进程绑定的全局UI状态存储中心，由UI框架在应用启动时创建，将UI状态数据存储于运行内存，实现应用级全局状态共享。具体UI使用说明，详见 [AppStorage：应用全局的UI状态存储](../../../ui/state-management/arkts-appstorage.md)。 |
| [Environment(System API)](arkts-arkui-environment-c.md) | Environment提供设备环境状态的查询能力，可将系统环境变量（如深浅色模式、语言、字体缩放、布局方向等）注入AppStorage，使应用能够感知和响应设备环境变化。具体UI使用说明，详见 [Environment：设备环境查询](../../../ui/state-management/arkts-environment.md)。 |
| [LocalStorage(System API)](arkts-arkui-localstorage-c.md) | LocalStorage是页面级的UI状态存储，通过@Entry装饰器接收的参数可以在页面内 共享同一个LocalStorage实例。具体UI使用说明，详见[LocalStorage：页面级UI状态存储](../../../ui/state-management/arkts-localstorage.md)。 |
| [PersistentStorage(System API)](arkts-arkui-persistentstorage-c.md) | PersistentStorage提供了UI状态的持久化存储能力，将选定的AppStorage属性持久化到文件中，在应用重启时从文件中恢复这些属性值并写入到AppStorage。具体UI使用说明，详见 [PersistentStorage：持久化存储UI状态](../../../ui/state-management/arkts-persiststorage.md)。 |
| [SubscribedAbstractProperty(System API)](arkts-arkui-subscribedabstractproperty-c.md) | SubscribedAbstractProperty是[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中属性的单/双向同步绑定对象，用于与AppStorage/LocalStorage中的属性建立数据同 步关系。SubscribedAbstractProperty实例需要通过[aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#abouttobedeleted)接口手动释放，以取消同步 关系并无效化实例。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Environment(System API)](arkts-arkui-environment-c-sys.md) | Environment提供设备环境状态的查询能力，可将系统环境变量（如深浅色模式、语言、字体缩放、布局方向等）注入AppStorage，使应用能够感知和响应设备环境变化。具体UI使用说明，详见 [Environment：设备环境查询](../../../ui/state-management/arkts-environment.md)。 |
| [PersistentStorage(System API)](arkts-arkui-persistentstorage-c-sys.md) | PersistentStorage提供了UI状态的持久化存储能力，将选定的AppStorage属性持久化到文件中，在应用重启时从文件中恢复这些属性值并写入到AppStorage。具体UI使用说明，详见 [PersistentStorage：持久化存储UI状态](../../../ui/state-management/arkts-persiststorage.md)。 |
| [SubscribaleAbstract(System API)](arkts-arkui-subscribaleabstract-c-sys.md) | 可订阅抽象类，用于管理所持有的属性集合，提供属性的添加、删除和变更通知能力。 |
| [SubscribedAbstractProperty(System API)](arkts-arkui-subscribedabstractproperty-c-sys.md) | SubscribedAbstractProperty是[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中属性的单/双向同步绑定对象，用于与AppStorage/LocalStorage中的属性建立数据同 步关系。SubscribedAbstractProperty实例需要通过[aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#abouttobedeleted)接口手动释放，以取消同步 关系并无效化实例。 |
| [SyncedPropertyOneWay(System API)](arkts-arkui-syncedpropertyoneway-c-sys.md) | 继承自[SubscribedAbstractProperty\&lt;T\&gt;](arkts-arkui-subscribedabstractproperty-c.md)。用于接收父组件状态值的单向同步，当父组件状态变化时更新自身值。 |
| [SyncedPropertyTwoWay(System API)](arkts-arkui-syncedpropertytwoway-c-sys.md) | 继承自[SubscribedAbstractProperty\&lt;T\&gt;](arkts-arkui-subscribedabstractproperty-c.md)。用于实现父子组件之间的双向状态数据同步。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AbstractProperty(System API)](arkts-arkui-abstractproperty-i.md) | AbstractProperty是AppStorage/LocalStorage中属性的引用，提供读取、修改所引用属性数据及查询属性名的能力。与SubscribedAbstractProperty不同，AbstractProperty 实例无需手动释放。 |
| [EnvPropsOptions(System API)](arkts-arkui-envpropsoptions-i.md) | 用于指定环境变量名称及其默认值的键值对对象，作为[envProps](arkts-arkui-environment-c.md#envprops)参数传入。 |
| [PersistPropsOptions(System API)](arkts-arkui-persistpropsoptions-i.md) | 用于指定持久化属性及其默认值的键值对对象，作为[persistProps](arkts-arkui-persistentstorage-c.md#persistprops)参数传入。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IPropertySubscriber(System API)](arkts-arkui-ipropertysubscriber-i-sys.md) | 属性订阅者接口，定义订阅者需要实现的方法，用于接收属性变化通知和生命周期回调。 |
| [ISinglePropertyChangeSubscriber(System API)](arkts-arkui-isinglepropertychangesubscriber-i-sys.md) | 继承自[IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md)。用于订阅单个属性值的变化，当被订阅的属性发生变化时接收通知。 |
<!--DelEnd-->

<!--Del-->
### 属性（系统接口）

| 名称 | 说明 |
| --- | --- |
| [appStorage(System API)](arkts-arkui-commontsetsapi-p-sys.md) | 应用级全局状态存储实例，提供应用范围内的状态数据存储和访问能力。 |
<!--DelEnd-->
