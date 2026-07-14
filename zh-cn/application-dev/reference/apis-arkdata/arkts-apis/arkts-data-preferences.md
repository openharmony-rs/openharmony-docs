# @ohos.data.preferences

用户首选项为应用提供Key-Value键值型的数据处理能力，支持应用持久化轻量级数据，并对其修改和查询。

数据存储采用键值对形式，键为字符串类型，值可为数字、字符串、布尔类型、数组、Uint8Array、object或bigint。

用户首选项的持久化文件存储在[preferencesDir](../../../../application-models/application-context-stage.md#获取应用文件路径)路径下，创建preferences对象
前，需要保证preferencesDir路径可读写。持久化文件存储路径中的[加密等级](../../apis-ability-kit/arkts-apis/arkts-ability-areamode-e.md)会影响文件的可读
写状态，路径访问限制详见[应用文件目录与应用文件路径](../../../../file-management/app-sandbox-directory.md#应用文件目录与应用文件路径)。

> **说明：**
>
> 首选项无法保证进程并发安全，会有文件损坏和数据丢失的风险，不支持在多进程场景下使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [deletePreferences](arkts-arkdata-deletepreferences-f.md#deletepreferences-1) | 从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过name进行参数设置，使用callback异步回调。调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。不支持该接口与其他preference接口并发调用。 |
| [deletePreferences](arkts-arkdata-deletepreferences-f.md#deletepreferences-2) | 从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过Options进行参数设置，使用callback异步回调。调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。不支持该接口与其他preference接口并发调用。 |
| [deletePreferences](arkts-arkdata-deletepreferences-f.md#deletepreferences-3) | 从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过name进行参数设置，使用Promise异步回调。调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。不支持该接口与其他preference接口并发调用。 |
| [deletePreferences](arkts-arkdata-deletepreferences-f.md#deletepreferences-4) | 从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过Options进行参数设置，使用Promise异步回调。调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。不支持该接口与其他preference接口并发调用。 |
| [getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1) | 获取Preferences实例，通过name进行参数设置，使用callback异步回调。应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。 |
| [getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-2) | 获取Preferences实例，通过Options进行参数设置，使用callback异步回调。应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。 |
| [getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-3) | 获取Preferences实例，通过name进行参数设置，使用Promise异步回调。应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。 |
| [getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-4) | 获取Preferences实例，通过Options进行参数设置，使用Promise异步回调。应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。 |
| [getPreferencesSync](arkts-arkdata-getpreferencessync-f.md#getpreferencessync-1) | 获取Preferences实例，此为同步接口。应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。 |
| [isStorageTypeSupported](arkts-arkdata-isstoragetypesupported-f.md#isstoragetypesupported-1) | 判断当前平台是否支持传入的存储模式，此为同步接口。如果当前平台支持传入的存储模式时，该接口返回true；反之，返回false。 |
| [removePreferencesFromCache](arkts-arkdata-removepreferencesfromcache-f.md#removepreferencesfromcache-1) | 从缓存中移除指定的Preferences实例，通过name进行参数设置，使用callback异步回调。应用首次调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)接口获取某个Preferences实例后，该实例会被缓存起来，后续调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。调用此接口移除缓存中的实例之后，再次getPreferences将会重新读取持久化文件，生成新的Preferences实例。调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。若使用[GSKV存储模式](../../../../database/data-persistence-by-preferences.md#gskv存储)，推荐在进程退出时手动调用一次该接口。此操作会将数据缓存页写入磁盘，可一定程度上减少下一次调用getPreferences接口时的耗时。否则，下一次调用getPreferences接口时底层需要进行数据恢复，数据恢复的耗时取决于未写入磁盘的数据缓存页数量。 |
| [removePreferencesFromCache](arkts-arkdata-removepreferencesfromcache-f.md#removepreferencesfromcache-2) | 从缓存中移除指定的Preferences实例，通过Options进行参数设置，使用callback异步回调。应用首次调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)接口获取某个Preferences实例后，该实例会被缓存起来，后续调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。调用此接口移除缓存中的实例之后，再次getPreferences将会重新读取持久化文件，生成新的Preferences实例。调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。若使用[GSKV存储模式](../../../../database/data-persistence-by-preferences.md#gskv存储)，推荐在进程退出时手动调用一次该接口。此操作会将数据缓存页写入磁盘，可一定程度上减少下一次调用getPreferences接口时的耗时。否则，下一次调用getPreferences接口时底层需要进行数据恢复，数据恢复的耗时取决于未写入磁盘的数据缓存页数量。 |
| [removePreferencesFromCache](arkts-arkdata-removepreferencesfromcache-f.md#removepreferencesfromcache-3) | 从缓存中移除指定的Preferences实例，通过name进行参数设置，使用Promise异步回调。应用首次调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)接口获取某个Preferences实例后，该实例会被缓存起来，后续调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。调用此接口移除缓存中的实例之后，再次getPreferences将会重新读取持久化文件，生成新的Preferences实例。调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。若使用[GSKV存储模式](../../../../database/data-persistence-by-preferences.md#gskv存储)，推荐在进程退出时手动调用一次该接口。此操作会将数据缓存页写入磁盘，可一定程度上减少下一次调用getPreferences接口时的耗时。否则，下一次调用getPreferences接口时底层需要进行数据恢复，数据恢复的耗时取决于未写入磁盘的数据缓存页数量。 |
| [removePreferencesFromCache](arkts-arkdata-removepreferencesfromcache-f.md#removepreferencesfromcache-4) | 从缓存中移除指定的Preferences实例，通过Options进行参数设置，使用Promise异步回调。应用首次调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)接口获取某个Preferences实例后，该实例会被缓存起来，后续调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。调用此接口移除缓存中的实例之后，再次getPreferences将会重新读取持久化文件，生成新的Preferences实例。调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。若使用[GSKV存储模式](../../../../database/data-persistence-by-preferences.md#gskv存储)，推荐在进程退出时手动调用一次该接口。此操作会将数据缓存页写入磁盘，可一定程度上减少下一次调用getPreferences接口时的耗时。否则，下一次调用getPreferences接口时底层需要进行数据恢复，数据恢复的耗时取决于未写入磁盘的数据缓存页数量。 |
| [removePreferencesFromCacheSync](arkts-arkdata-removepreferencesfromcachesync-f.md#removepreferencesfromcachesync-1) | 从缓存中移除指定的Preferences实例，通过name进行参数设置，此为同步接口。应用首次调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)接口获取某个Preferences实例后，该实例会被缓存起来，后续调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。调用此接口移除缓存中的实例之后，再次getPreferences将会重新读取持久化文件，生成新的Preferences实例。调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。若使用[GSKV存储模式](../../../../database/data-persistence-by-preferences.md#gskv存储)，推荐在进程退出时手动调用一次该接口。此操作会将数据缓存页写入磁盘，可一定程度上减少下一次调用getPreferences接口时的耗时。否则，下一次调用getPreferences接口时底层需要进行数据恢复，数据恢复的耗时取决于未写入磁盘的数据缓存页数量。 |
| [removePreferencesFromCacheSync](arkts-arkdata-removepreferencesfromcachesync-f.md#removepreferencesfromcachesync-2) | 从缓存中移除指定的Preferences实例，通过Options进行参数设置，此为同步接口。应用首次调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)接口获取某个Preferences实例后，该实例会被缓存起来，后续调用[getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。调用此接口移除缓存中的实例之后，再次getPreferences将会重新读取持久化文件，生成新的Preferences实例。调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。若使用[GSKV存储模式](../../../../database/data-persistence-by-preferences.md#gskv存储)，推荐在进程退出时手动调用一次该接口。此操作会将数据缓存页写入磁盘，可一定程度上减少下一次调用getPreferences接口时的耗时。否则，下一次调用getPreferences接口时底层需要进行数据恢复，数据恢复的耗时取决于未写入磁盘的数据缓存页数量。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Options](arkts-arkdata-options-i.md) | Preferences实例配置选项。 |
| [Preferences](arkts-arkdata-preferences-i.md) | 首选项实例，提供获取和修改存储数据的接口。下列接口都需先使用[preferences.getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)获取到Preferences实例，再通过此实例调用对应接口。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StorageType](arkts-arkdata-storagetype-e.md) | Preferences的存储模式枚举。@link preferences.isStorageTypeSupported}检查当前平台是否支持对应存储模式。&gt;&gt; - 当选择某一模式通过[preferences.getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)接口获取实例后，不允许中途切换模式。&gt;&gt; - 首选项不支持不同模式间数据的迁移，若需将数据从一种模式切换至另一种模式，需通过读写首选项的形式进行数据迁移。&gt;&gt; - 若需要变更首选项的存储路径，不能通过移动或覆盖文件的方式进行，需通过读写首选项的形式进行数据迁移。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ValueType](arkts-arkdata-valuetype-t.md) | 表示支持的值类型。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [MAX_KEY_LENGTH](arkts-arkdata-preferences-con.md#max_key_length) | Key的最大长度限制为1024个字节。 |
| [MAX_VALUE_LENGTH](arkts-arkdata-preferences-con.md#max_value_length) | Value的最大长度限制为16MB。 |

