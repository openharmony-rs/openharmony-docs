# StorageType

Preferences的存储模式枚举。

> **说明：**  
>  
> - 在选择存储模式前，建议调用[isStorageTypeSupported](arkts-arkdata-preferences-isstoragetypesupported-f.md#isstoragetypesupported-1)检查当前平台是否支持对应存储模式。  
>  
> - 当选择某一模式通过[preferences.getPreferences](arkts-arkdata-preferences-getpreferences-f.md#getpreferences-1)接口获取实例后，不允许中途切换模式。  
>  
> - 首选项不支持不同模式间数据的迁移，若需将数据从一种模式切换至另一种模式，需通过读写首选项的形式进行数据迁移。  
>  
> - 若需要变更首选项的存储路径，不能通过移动或覆盖文件的方式进行，需通过读写首选项的形式进行数据迁移。

**起始版本：** 18

<!--Device-preferences-enum StorageType--><!--Device-preferences-enum StorageType-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## XML

```TypeScript
XML = 0
```

表示[XML存储模式](docroot://database/data-persistence-by-preferences.md#xml存储)，这是Preferences的默认存储模式。

**特点：** 数据以XML格式进行存储。对数据的操作发生在内存中，需要调用[flush](arkts-arkdata-preferences-preferences-i.md#flush-1)接口进行落盘。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-StorageType-XML = 0--><!--Device-StorageType-XML = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## GSKV

```TypeScript
GSKV
```

表示[GSKV存储模式](docroot://database/data-persistence-by-preferences.md#gskv存储)。

**特点：** 数据以GSKV数据库模式进行存储。对数据的操作实时落盘，无需调用[flush](arkts-arkdata-preferences-preferences-i.md#flush-1)接口对数据进行落盘。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-StorageType-GSKV--><!--Device-StorageType-GSKV-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

