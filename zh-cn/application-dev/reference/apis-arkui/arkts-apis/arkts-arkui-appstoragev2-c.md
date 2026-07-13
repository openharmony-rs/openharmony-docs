# AppStorageV2

AppStorageV2具体UI使用说明，详见[AppStorageV2(应用全局的UI状态存储)](../../../../ui/state-management/arkts-new-appstoragev2.md)。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## connect

```TypeScript
static connect<T extends object>(
    type: TypeConstructorWithArgs<T>,
    keyOrDefaultCreator?: string | StorageDefaultCreator<T>,
    defaultCreator?: StorageDefaultCreator<T>
  ): T | undefined
```

将键值对数据储存在应用内存中。如果给定的key已经存在于[AppStorageV2](../../../../ui/state-management/arkts-new-appstoragev2.md)中，返回对应的值；否则，通过获取
默认值的构造器构造默认值，并返回。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | TypeConstructorWithArgs&lt;T&gt; | 是 | 指定的类型，若未指定key，则使用type的name作为key。 |
| keyOrDefaultCreator | string \| StorageDefaultCreator&lt;T&gt; | 否 | 指定的key，或者是获取默认值的构造器。默认值为undefined。 |
| defaultCreator | StorageDefaultCreator&lt;T&gt; | 否 | 获取默认值的构造器。默认值为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Returns data if the creation or data acquisition from AppStorageV2 is successful;returns **undefined** otherwise. |

## keys

```TypeScript
static keys(): Array<string>
```

获取[AppStorageV2](../../../../ui/state-management/arkts-new-appstoragev2.md)中的所有key。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 所有AppStorageV2中的key。 |

## remove

```TypeScript
static remove<T>(keyOrType: string | TypeConstructorWithArgs<T>): void
```

将指定的键值对数据从[AppStorageV2](../../../../ui/state-management/arkts-new-appstoragev2.md)里面删除。如果指定的键值不存在于AppStorageV2中，将删除失
败。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyOrType | string \| TypeConstructorWithArgs&lt;T&gt; | 是 | 需要删除的key；如果指定的是type类型，删除的key为type的name。 |

