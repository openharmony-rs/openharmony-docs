# StoreConfig

管理关系数据库配置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-relationalStore-interface StoreConfig--><!--Device-relationalStore-interface StoreConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## allowRebuild

```TypeScript
allowRebuild?: boolean
```

指定数据库是否支持异常时自动删除，并重建一个空库空表，默认不自动删除。 true：自动删除。 false：不自动删除。 从API version 12开始，支持此可选参数。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-allowRebuild?: boolean--><!--Device-StoreConfig-allowRebuild?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## autoCleanDirtyData

```TypeScript
autoCleanDirtyData?: boolean
```

指定是否自动清理云端删除后同步到本地的数据，true表示自动清理，false表示手动清理，默认自动清理。 对于端云协同的数据库，当云端删除的数据同步到设备端时，可通过该参数设置设备端是否自动清理。手动清理可以通过 [cleanDirtyData&lt;sup&gt;11+&lt;/sup&gt;](arkts-arkdata-relationalstore-rdbstore-i.md#cleanDirtyData) 接口清理。 从API version 11开始，支持此可选参数。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-autoCleanDirtyData?: boolean--><!--Device-StoreConfig-autoCleanDirtyData?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## cryptoParam

```TypeScript
cryptoParam?: CryptoParam
```

指定用户自定义的加密参数。 当此参数不填时，使用默认的加密参数，见[CryptoParam](arkts-arkdata-relationalstore-cryptoparam-i.md#CryptoParam)各参数默认值。 此配置只有在encrypt选项设置为true或密钥非空时才有效。 从API version 14开始，支持此可选参数。

**类型：** [CryptoParam](arkts-arkdata-relationalstore-cryptoparam-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-cryptoParam?: CryptoParam--><!--Device-StoreConfig-cryptoParam?: CryptoParam-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## customDir

```TypeScript
customDir?: string
```

数据库自定义路径。 **使用约束：** 数据库路径大小限制为128字节，如果超过该大小会开库失败，抛出错误码401，请参见[通用错误码](../../errorcode-universal.md)。 从API version 11开始，支持此可选参数。数据库将在如下的目录结构中被创建：context.databaseDir + "/rdb/" + customDir，其中context.databaseDir是应用沙箱对应 的路径，"/rdb/"表示创建的是关系型数据库，customDir表示自定义的路径。当此参数不填时，默认在本应用沙箱目录下创建RdbStore实例。从API version 18开始，如果同时配置了rootDir参数，将打开或 删除如下路径数据库：rootDir + "/" + customDir + "/" + name。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-customDir?: string--><!--Device-StoreConfig-customDir?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## dataGroupId

```TypeScript
dataGroupId?: string
```

应用组ID，&lt;!--RP1--&gt;暂不支持指定dataGroupId在对应的沙箱路径下创建RdbStore实例。&lt;!--RP1End--&gt; **模型约束：** 此属性仅在Stage模型下可用。 从API version 10开始，支持此可选参数。dataGroupId共享沙箱的方式不支持多进程访问加密数据库，当此参数不填时，默认在本应用沙箱目录下创建RdbStore实例。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StoreConfig-dataGroupId?: string--><!--Device-StoreConfig-dataGroupId?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## enableSemanticIndex

```TypeScript
enableSemanticIndex?: boolean
```

指定数据库是否启用语义索引处理功能。true表示启用语义索引处理功能，false表示不启用。默认为false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-enableSemanticIndex?: boolean--><!--Device-StoreConfig-enableSemanticIndex?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## encrypt

```TypeScript
encrypt?: boolean
```

指定数据库是否加密，默认非加密。数据库创建完成后，此参数不允许直接修改。如需变更数据库加密状态，请调用[rekeyEx](arkts-arkdata-relationalstore-rdbstore-i.md#rekeyEx)接口进行更新操作。 true：加密。 false：非加密。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-encrypt?: boolean--><!--Device-StoreConfig-encrypt?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## isReadOnly

```TypeScript
isReadOnly?: boolean
```

指定数据库是否只读，默认为数据库可读写。 true：只允许从数据库读取数据，不允许对数据库进行写操作，否则会返回错误码801。 false：允许对数据库进行读写操作。 从API version 12开始，支持此可选参数。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-isReadOnly?: boolean--><!--Device-StoreConfig-isReadOnly?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## name

```TypeScript
name: string
```

数据库文件名，也是数据库唯一标识符，不能为空字符串且不能包含路径分隔符/。同一进程禁止创建两个同名的数据库，否则可能导致端端同步、端云同步、静默访问以及密钥备份等功能出现异常。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-name: string--><!--Device-StoreConfig-name: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## persist

```TypeScript
persist?: boolean
```

指定数据库是否需要持久化。true表示持久化，false表示不持久化，即内存数据库。默认为true。 内存数据库不支持加密、backup、restore、跨进程访问及分布式能力，securityLevel属性会被忽略。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-persist?: boolean--><!--Device-StoreConfig-persist?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## pluginLibs

```TypeScript
pluginLibs?: Array<string>
```

配置加载自定义动态库，数组中可传入多个动态库名称，默认值为空数组。具体请见 [pluginLibs的使用约束和示例](../../../reference/apis-arkdata/arkts-apis-data-relationalStore-i.md#pluginlibs的使用约束和示例)。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-pluginLibs?: Array<string>--><!--Device-StoreConfig-pluginLibs?: Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## rootDir

```TypeScript
rootDir?: string
```

指定数据库根路径，默认值为空字符串。 从API version 18开始，支持此可选参数。将从如下目录打开或删除数据库：rootDir + "/" + customDir。通过设置此参数打开的数据库为只读模式，不允许对数据库进行写操作，否则返回错误码801。配置此 参数打开或删除数据库时，应确保对应路径下数据库文件存在，并且有读取权限，否则返回错误码14800010。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-rootDir?: string--><!--Device-StoreConfig-rootDir?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## securityLevel

```TypeScript
securityLevel: SecurityLevel
```

设置数据库安全级别。

**类型：** SecurityLevel

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-securityLevel: SecurityLevel--><!--Device-StoreConfig-securityLevel: SecurityLevel-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## tokenizer

```TypeScript
tokenizer?: Tokenizer
```

指定用户在FTS（Full-Text Search）场景下使用哪种分词器。 当此参数不填时，则在FTS下不支持中文以及多国语言分词，但仍可支持英文分词。 如果用户想使用自定义分词器，可以通过pluginLibs参数进行配置，具体请见 [pluginLibs的使用约束和示例](../../../reference/apis-arkdata/arkts-apis-data-relationalStore-i.md#pluginlibs的使用约束和示例)。

**类型：** [Tokenizer](arkts-arkdata-relationalstore-tokenizer-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-tokenizer?: Tokenizer--><!--Device-StoreConfig-tokenizer?: Tokenizer-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## vector

```TypeScript
vector?: boolean
```

指定数据库是否是向量数据库，true表示向量数据库，false表示关系型数据库，默认为false。 向量数据库适用于存储和处理高维向量数据，关系型数据库适用于存储和处理结构化数据。 当使用向量数据库时，在调用deleteRdbStore接口前，应当确保向量数据库已打开的RdbStore和ResultSet均已成功关闭。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-StoreConfig-vector?: boolean--><!--Device-StoreConfig-vector?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

