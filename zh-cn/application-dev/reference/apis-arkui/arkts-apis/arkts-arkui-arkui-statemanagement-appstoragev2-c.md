# AppStorageV2

AppStorageV2具体UI使用说明，详见[AppStorageV2(应用全局的UI状态存储)](docroot://ui/state-management/arkts-new-appstoragev2.md)。

**起始版本：** 12

<!--Device-unnamed-export declare class AppStorageV2--><!--Device-unnamed-export declare class AppStorageV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Binding, ComponentReuse, CustomComponentLifecycleState, ComponentInactive, PersistenceV2, ComponentDisappear, MutableBinding, CustomComponentLifecycleObserver, AppStorageV2, Type, ConnectOptionsCollections, CollectionType, CustomComponentContext, IReusePool, ConnectOptions, UIUtils, ComponentActive, CustomComponentLifecycle, ComponentInit, ComponentAppear, ComponentBuilt, ComponentRecycle, IReusableInfo } from '@kit.ArkUI';
```

<a id="connect"></a>
## connect

```TypeScript
static connect<T extends object>(
    type: TypeConstructorWithArgs<T>,
    keyOrDefaultCreator?: string | StorageDefaultCreator<T>,
    defaultCreator?: StorageDefaultCreator<T>
  ): T | undefined
```

将键值对数据储存在应用内存中。如果给定的key已经存在于[AppStorageV2](docroot://ui/state-management/arkts-new-appstoragev2.md)中，返回对应的值；否则，通过获取默认值的构造器构造默认值，并返回。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorageV2-static connect<T extends object>(
    type: TypeConstructorWithArgs<T>,
    keyOrDefaultCreator?: string | StorageDefaultCreator<T>,
    defaultCreator?: StorageDefaultCreator<T>
  ): T | undefined--><!--Device-AppStorageV2-static connect<T extends object>(
    type: TypeConstructorWithArgs<T>,
    keyOrDefaultCreator?: string | StorageDefaultCreator<T>,
    defaultCreator?: StorageDefaultCreator<T>
  ): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt; | 是 | 指定的类型，若未指定key，则使用type的name作为key。 |
| keyOrDefaultCreator | string \| StorageDefaultCreator&lt;T&gt; | 否 | 指定的key，或者是获取默认值的构造器。默认值为undefined。 |
| defaultCreator | [StorageDefaultCreator](arkts-arkui-storagedefaultcreator-t.md)&lt;T&gt; | 否 | 获取默认值的构造器。默认值为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Returns data if the creation or data acquisition from AppStorageV2 is successful;returns **undefined** otherwise. |

<a id="keys"></a>
## keys

```TypeScript
static keys(): Array<string>
```

获取[AppStorageV2](docroot://ui/state-management/arkts-new-appstoragev2.md)中的所有key。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorageV2-static keys(): Array<string>--><!--Device-AppStorageV2-static keys(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 所有AppStorageV2中的key。 |

<a id="remove"></a>
## remove

```TypeScript
static remove<T>(keyOrType: string | TypeConstructorWithArgs<T>): void
```

将指定的键值对数据从[AppStorageV2](docroot://ui/state-management/arkts-new-appstoragev2.md)里面删除。如果指定的键值不存在于AppStorageV2中，将删除失败。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorageV2-static remove<T>(keyOrType: string | TypeConstructorWithArgs<T>): void--><!--Device-AppStorageV2-static remove<T>(keyOrType: string | TypeConstructorWithArgs<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyOrType | string \| TypeConstructorWithArgs&lt;T&gt; | 是 | 需要删除的key；如果指定的是type类型，删除的key为type的name。 |

