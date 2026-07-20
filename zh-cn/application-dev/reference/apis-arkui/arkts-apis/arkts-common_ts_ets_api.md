# common_ts_ets_api

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AppStorage](arkts-arkui-appstorage-c.md) | AppStorage具体UI使用说明，详见[AppStorage(应用全局的UI状态存储)](docroot://ui/state-management/arkts-appstorage.md) |
| [Environment](arkts-arkui-environment-c.md) | Environment具体使用说明，详见[Environment(设备环境查询)](docroot://ui/state-management/arkts-environment.md) |
| [LocalStorage](arkts-arkui-localstorage-c.md) | LocalStorage具体UI使用说明，详见[LocalStorage(页面级UI状态存储)](docroot://ui/state-management/arkts-localstorage.md) |
| [PersistentStorage](arkts-arkui-persistentstorage-c.md) | PersistentStorage具体UI使用说明，详见[PersistentStorage(持久化存储UI状态)](docroot://ui/state-management/arkts-persiststorage.md) |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md) | SubscribedAbstractProperty是[AppStorage](docroot://ui/state-management/arkts-appstorage.md)/[LocalStorage](docroot://ui/state-management/arkts-localstorage.md)中同步的属性。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Environment](arkts-arkui-environment-c-sys.md) | Environment具体使用说明，详见[Environment(设备环境查询)](docroot://ui/state-management/arkts-environment.md) |
| [PersistentStorage](arkts-arkui-persistentstorage-c-sys.md) | PersistentStorage具体UI使用说明，详见[PersistentStorage(持久化存储UI状态)](docroot://ui/state-management/arkts-persiststorage.md) |
| [SubscribaleAbstract](arkts-arkui-subscribaleabstract-c-sys.md) | 定义Subscribale基类。 |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c-sys.md) | SubscribedAbstractProperty是[AppStorage](docroot://ui/state-management/arkts-appstorage.md)/[LocalStorage](docroot://ui/state-management/arkts-localstorage.md)中同步的属性。 |
| [SyncedPropertyOneWay](arkts-arkui-syncedpropertyoneway-c-sys.md) | 继承自[SubscribedAbstractProperty<T>](arkts-arkui-subscribedabstractproperty-c-sys.md)。用来定义父组件的状态值。 |
| [SyncedPropertyTwoWay](arkts-arkui-syncedpropertytwoway-c-sys.md) | 继承自[SubscribedAbstractProperty<T>](arkts-arkui-subscribedabstractproperty-c-sys.md)。用来定义变量状态的值。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AbstractProperty](arkts-arkui-abstractproperty-i.md) | AbstractProperty是[AppStorage](docroot://ui/state-management/arkts-appstorage.md)/[LocalStorage](docroot://ui/state-management/arkts-localstorage.md)中属性的引用。 |
| [EnvPropsOptions](arkts-arkui-envpropsoptions-i.md) | 用于指定环境变量名称及其默认值的键值对对象，作为[envProps](arkts-arkui-environment-c.md#envprops-1)参数传入。 |
| [PersistPropsOptions](arkts-arkui-persistpropsoptions-i.md) | 用于指定持久化属性及其默认值的键值对对象，作为[persistProps](arkts-arkui-persistentstorage-c.md#persistprops-1)参数传入。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | 提供属性订阅者的接口。 |
| [ISinglePropertyChangeSubscriber](arkts-arkui-isinglepropertychangesubscriber-i-sys.md) | 继承自[IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md)。用来定义变量。 |
<!--DelEnd-->

