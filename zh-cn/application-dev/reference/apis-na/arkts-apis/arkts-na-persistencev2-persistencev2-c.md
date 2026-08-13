# PersistenceV2

PersistenceV2具体UI使用说明，详见 PersistenceV2(持久化存储UI状态)。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class PersistenceV2--><!--Device-unnamed-export declare class PersistenceV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## connect

```TypeScript
static connect<T extends object>(
    ttype: Class,
    defaultCreator?: StorageDefaultCreator<T>,
    connectOptions?: BaseConnectOptions<T>
  ): T | undefined
```

将键值对数据储存在应用磁盘中。如果给定的key已经存在于PersistenceV2中，返回对应的值；否则，会通过获取默认值的构造器构造默认值，并返回。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistenceV2-static connect<T extends object>(    ttype: Class,    defaultCreator?: StorageDefaultCreator<T>,    connectOptions?: BaseConnectOptions<T>  ): T | undefined--><!--Device-PersistenceV2-static connect<T extends object>(    ttype: Class,    defaultCreator?: StorageDefaultCreator<T>,    connectOptions?: BaseConnectOptions<T>  ): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ttype | Class | 是 | class type of the stored value. |
| defaultCreator | [StorageDefaultCreator](arkts-na-storagedefaultcreator-t.md)&lt;T&gt; | 否 | the function generating the default value |
| connectOptions | [BaseConnectOptions](arkts-na-persistencev2-baseconnectoptions-i.md)&lt;T&gt; | 否 | additional connect options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | the value of the existing key or the default value. returns undefined when defaultCreator is not set and there is no data with matching type. |

## connect

```TypeScript
static connect<T extends object>(
    ttype: Class,
    key: string,
    defaultCreator?: StorageDefaultCreator<T>,
    connectOptions?: BaseConnectOptions<T>
  ): T | undefined
```

将键值对数据储存在应用磁盘中。如果给定的key已经存在于PersistenceV2中，返回对应的值；否则，会通过获取默认值的构造器构造默认值，并返回。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistenceV2-static connect<T extends object>(    ttype: Class,    key: string,    defaultCreator?: StorageDefaultCreator<T>,    connectOptions?: BaseConnectOptions<T>  ): T | undefined--><!--Device-PersistenceV2-static connect<T extends object>(    ttype: Class,    key: string,    defaultCreator?: StorageDefaultCreator<T>,    connectOptions?: BaseConnectOptions<T>  ): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ttype | Class | 是 | class type of the stored value. |
| key | string | 是 | alias name of the key. |
| defaultCreator | [StorageDefaultCreator](arkts-na-storagedefaultcreator-t.md)&lt;T&gt; | 否 | the function generating the default value |
| connectOptions | [BaseConnectOptions](arkts-na-persistencev2-baseconnectoptions-i.md)&lt;T&gt; | 否 | additional connect options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | the value of the existed key or the default value. returns undefined when defaultCreator is not set and there is no data with matching type and key. |

## globalConnect

```TypeScript
static globalConnect<T extends object>(params: ConnectOptions<T>): T | undefined
```

将键值对数据储存在应用磁盘中。如果给定的key已经存在于PersistenceV2 中，返回对应的值；否则，会通过获取默认值的构造器构造默认值，并返回。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistenceV2-static globalConnect<T extends object>(params: ConnectOptions<T>): T | undefined--><!--Device-PersistenceV2-static globalConnect<T extends object>(params: ConnectOptions<T>): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [ConnectOptions](arkts-na-persistencev2-connectoptions-i.md)&lt;T&gt; | 是 | application-level storage parameters. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | the value of the existed key or the default value |

## keys

```TypeScript
static keys(): string[]
```

获取PersistenceV2中所有的key。 > **说明：** > > key在Array中的顺序是无序的，与key插入到PersistenceV2中的顺序无关。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistenceV2-static keys(): string[]--><!--Device-PersistenceV2-static keys(): string[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | the array of all keys. |

## notifyOnError

```TypeScript
static notifyOnError(callback: PersistenceErrorCallback | undefined): void
```

在持久化失败时调用。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistenceV2-static notifyOnError(callback: PersistenceErrorCallback | undefined): void--><!--Device-PersistenceV2-static notifyOnError(callback: PersistenceErrorCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PersistenceErrorCallback](arkts-na-persistenceerrorcallback-t.md) \| undefined | 是 | 持久化失败时调用。 |

## remove

```TypeScript
static remove(keyOrType: string | Class): void
```

将指定的键值对数据从PersistenceV2里面删除。如果指定的键值不存在于PersistenceV2中，将删除失败。 > **说明：** > > 删除PersistenceV2中不存在的key会打印warn日志警告。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistenceV2-static remove(keyOrType: string | Class): void--><!--Device-PersistenceV2-static remove(keyOrType: string | Class): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyOrType | string \| Class | 是 | 需要删除的key。如果传入的是Class类型，则删除的key为Class类型入参的name。 |

## save

```TypeScript
static save(keyOrType: string | Class): void
```

手动持久化指定的键值对数据。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PersistenceV2-static save(keyOrType: string | Class): void--><!--Device-PersistenceV2-static save(keyOrType: string | Class): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyOrType | string \| Class | 是 | 需要持久化的key；如果指定的是Class类型，持久化的key为Class的name。 |

