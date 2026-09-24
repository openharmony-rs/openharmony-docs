# @ohos.data.preferences(用户首选项)

用户首选项为应用提供Key-Value键值型的数据处理能力，支持应用持久化轻量级数据，并对其修改和查询。

数据存储采用键值对形式，键为字符串类型，值可为数字、字符串、布尔类型、数组、Uint8Array、object或bigint。

用户首选项的持久化文件存储在[preferencesDir](../../../application-models/application-context-stage.md#获取应用文件路径)路径下，创建preferences对象前，需要保证preferencesDir路径可读写。持久化文件存储路径中的[加密等级](../../apis-ability-kit/arkts-apis/arkts-ability-contextconstant-areamode-e.md)会影响文件的可读写状态，路径访问限制详见[应用文件目录与应用文件路径](../../../file-management/app-sandbox-directory.md#应用文件目录与应用文件路径)。

> **说明：** 
> 
> 首选项无法保证进程并发安全，会有文件损坏和数据丢失的风险，不支持在多进程场景下使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## 导入模块

```TypeScript
import { preferences } from '@kit.ArkData';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [deletePreferences](arkts-arkdata-preferences-deletepreferences-f.md#deletepreferences) | 从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过name进行参数设置，使用callback异步回调。 |
| [deletePreferences](arkts-arkdata-preferences-deletepreferences-f.md#deletepreferences-1) | 从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过Options进行参数设置，使用callback异步回调。 |
| [deletePreferences](arkts-arkdata-preferences-deletepreferences-f.md#deletepreferences-2) | 从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过name进行参数设置，使用Promise异步回调。 |
| [deletePreferences](arkts-arkdata-preferences-deletepreferences-f.md#deletepreferences-3) | 从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过Options进行参数设置，使用Promise异步回调。 |
| [getPreferences](arkts-arkdata-preferences-getpreferences-f.md#getpreferences) | 获取Preferences实例，通过name进行参数设置，使用callback异步回调。 |
| [getPreferences](arkts-arkdata-preferences-getpreferences-f.md#getpreferences-1) | 获取Preferences实例，通过Options进行参数设置，使用callback异步回调。 |
| [getPreferences](arkts-arkdata-preferences-getpreferences-f.md#getpreferences-2) | 获取Preferences实例，通过name进行参数设置，使用Promise异步回调。 |
| [getPreferences](arkts-arkdata-preferences-getpreferences-f.md#getpreferences-3) | 获取Preferences实例，通过Options进行参数设置，使用Promise异步回调。 |
| [getPreferencesSync](arkts-arkdata-preferences-getpreferencessync-f.md) | 获取Preferences实例，此为同步接口。 |
| [isStorageTypeSupported](arkts-arkdata-preferences-isstoragetypesupported-f.md) | 判断当前平台是否支持传入的存储模式，此为同步接口。如果当前平台支持传入的存储模式时，该接口返回true；反之，返回false。 |
| [removePreferencesFromCache](arkts-arkdata-preferences-removepreferencesfromcache-f.md#removepreferencesfromcache) | 从缓存中移除指定的Preferences实例，通过name进行参数设置，使用callback异步回调。 |
| [removePreferencesFromCache](arkts-arkdata-preferences-removepreferencesfromcache-f.md#removepreferencesfromcache-1) | 从缓存中移除指定的Preferences实例，通过Options进行参数设置，使用callback异步回调。 |
| [removePreferencesFromCache](arkts-arkdata-preferences-removepreferencesfromcache-f.md#removepreferencesfromcache-2) | 从缓存中移除指定的Preferences实例，通过name进行参数设置，使用Promise异步回调。 |
| [removePreferencesFromCache](arkts-arkdata-preferences-removepreferencesfromcache-f.md#removepreferencesfromcache-3) | 从缓存中移除指定的Preferences实例，通过Options进行参数设置，使用Promise异步回调。 |
| [removePreferencesFromCacheSync](arkts-arkdata-preferences-removepreferencesfromcachesync-f.md#removepreferencesfromcachesync) | 从缓存中移除指定的Preferences实例，通过name进行参数设置，此为同步接口。 |
| [removePreferencesFromCacheSync](arkts-arkdata-preferences-removepreferencesfromcachesync-f.md#removepreferencesfromcachesync-1) | 从缓存中移除指定的Preferences实例，通过Options进行参数设置，此为同步接口。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Options](arkts-arkdata-preferences-options-i.md) | Preferences实例配置选项。 |
| [Preferences](arkts-arkdata-preferences-preferences-i.md) | 首选项实例，提供获取和修改存储数据的接口。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ValueType](arkts-arkdata-preferences-valuetype-t.md) | 表示支持的值类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StorageType](arkts-arkdata-preferences-storagetype-e.md) | Preferences的存储模式枚举。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [MAX_KEY_LENGTH](arkts-arkdata-preferences-con.md#max_key_length) | Key的最大长度限制为1024个字节。 |
| [MAX_VALUE_LENGTH](arkts-arkdata-preferences-con.md#max_value_length) | Value的最大长度限制为16MB。 |
