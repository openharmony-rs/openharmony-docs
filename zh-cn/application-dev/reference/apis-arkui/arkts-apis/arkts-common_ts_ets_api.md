# common_ts_ets_api

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AppStorage](arkts-arkui-common-ts-ets-api-appstorage-c.md) | AppStorage具体UI使用说明，详见[AppStorage(应用全局的UI状态存储)](../../../../ui/state-management/arkts-appstorage.md) |
| [Environment](arkts-arkui-common-ts-ets-api-environment-c.md) | Environment具体使用说明，详见[Environment(设备环境查询)](../../../../ui/state-management/arkts-environment.md) |
| [LocalStorage](arkts-arkui-common-ts-ets-api-localstorage-c.md) | LocalStorage具体UI使用说明，详见[LocalStorage(页面级UI状态存储)](../../../../ui/state-management/arkts-localstorage.md) |
| [PersistentStorage](arkts-arkui-common-ts-ets-api-persistentstorage-c.md) | PersistentStorage具体UI使用说明，详见[PersistentStorage(持久化存储UI状态)](../../../../ui/state-management/arkts-persiststorage.md) |
| [SubscribedAbstractProperty](arkts-arkui-common-ts-ets-api-subscribedabstractproperty-c.md) | SubscribedAbstractProperty是[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)中同步的属性。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Environment](arkts-arkui-common-ts-ets-api-environment-c-sys.md) | Environment具体使用说明，详见[Environment(设备环境查询)](../../../../ui/state-management/arkts-environment.md) |
| [PersistentStorage](arkts-arkui-common-ts-ets-api-persistentstorage-c-sys.md) | PersistentStorage具体UI使用说明，详见[PersistentStorage(持久化存储UI状态)](../../../../ui/state-management/arkts-persiststorage.md) |
| [SubscribaleAbstract](arkts-arkui-common-ts-ets-api-subscribaleabstract-c-sys.md) | 定义Subscribale基类。 |
| [SubscribedAbstractProperty](arkts-arkui-common-ts-ets-api-subscribedabstractproperty-c-sys.md) | SubscribedAbstractProperty是[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)中同步的属性。 |
| [SyncedPropertyOneWay](arkts-arkui-common-ts-ets-api-syncedpropertyoneway-c-sys.md) | 继承自[SubscribedAbstractProperty&lt;T&gt;](arkts-arkui-common-ts-ets-api-subscribedabstractproperty-c-sys.md)。用来定义父组件的状态值。 |
| [SyncedPropertyTwoWay](arkts-arkui-common-ts-ets-api-syncedpropertytwoway-c-sys.md) | 继承自[SubscribedAbstractProperty&lt;T&gt;](arkts-arkui-common-ts-ets-api-subscribedabstractproperty-c-sys.md)。用来定义变量状态的值。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AbstractProperty](arkts-arkui-common-ts-ets-api-abstractproperty-i.md) | AbstractProperty是[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)中属性的引用。 |
| [EnvPropsOptions](arkts-arkui-common-ts-ets-api-envpropsoptions-i.md) | 用于指定环境变量名称及其默认值的键值对对象，作为[envProps](arkts-arkui-common-ts-ets-api-environment-c.md#envprops-1)参数传入。 |
| [PersistPropsOptions](arkts-arkui-common-ts-ets-api-persistpropsoptions-i.md) | 用于指定持久化属性及其默认值的键值对对象，作为[persistProps](arkts-arkui-common-ts-ets-api-persistentstorage-c.md#persistprops-1)参数传入。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IPropertySubscriber](arkts-arkui-common-ts-ets-api-ipropertysubscriber-i-sys.md) | 提供属性订阅者的接口。 |
| [ISinglePropertyChangeSubscriber](arkts-arkui-common-ts-ets-api-isinglepropertychangesubscriber-i-sys.md) | 继承自[IPropertySubscriber](arkts-arkui-common-ts-ets-api-ipropertysubscriber-i-sys.md)。用来定义变量。 |
<!--DelEnd-->

