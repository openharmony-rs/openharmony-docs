# @ohos.data.sendablePreferences

共享用户首选项为应用提供Key-Value键值型的数据处理能力，支持应用持久化轻量级数据，并对其修改和查询。

数据存储形式为键值对，键的类型为字符串型，值的存储数据类型包括number、string、boolean、bigint以及可序列化的object。

共享用户首选项的持久化文件存储在[preferencesDir](../../../application-models/application-context-stage.md#获取应用文件路径)路径下，创建preferences对象前，需要保证preferencesDir路径可读写。持久化文件存储路径中的[加密等级](../../apis-ability-kit/arkts-apis/arkts-ability-contextconstant-areamode-e.md)会影响文件的可读写状态，路径访问限制详见[应用文件目录与应用文件路径](../../../file-management/app-sandbox-directory.md#应用文件目录与应用文件路径)。

共享用户首选项可以在ArkTS并发实例间（包括主线程、TaskPool&Worker工作线程）传递，传递的行为是引用传递，性能优于普通的[用户首选项](arkts-data-preferences.md)，可参考[Sendable使用场景](../../../arkts-utils/sendable-guide.md)。
> **说明：**  
>  
> 共享用户首选项无法保证进程并发安全，会有文件损坏和数据丢失的风险，不支持在多进程场景下使用。

**起始版本：** 12

<!--Device-unnamed-declare namespace sendablePreferences--><!--Device-unnamed-declare namespace sendablePreferences-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## 导入模块

```TypeScript
import { sendablePreferences } from '@kit.ArkData';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [deletePreferences](arkts-arkdata-sendablepreferences-deletepreferences-f.md#deletepreferences) | 从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。使用Promise异步回调。  调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题。 |
| [getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md#getpreferences) | 获取Preferences实例，使用Promise异步回调。  应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。 |
| [getPreferencesSync](arkts-arkdata-sendablepreferences-getpreferencessync-f.md#getpreferencessync) | 获取Preferences实例，此为同步接口。  应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。 |
| [removePreferencesFromCache](arkts-arkdata-sendablepreferences-removepreferencesfromcache-f.md#removepreferencesfromcache) | 从缓存中移除指定的Preferences实例，使用Promise异步回调。  应用首次调用[getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md#getpreferences)接口获取某个Preferences实例后，该实例会被缓存起来，后续调用[getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md#getpreferences)时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。调用此接口移除缓存中的实例之后，再次getPreferences将会重新读取持久化文件，生成新的Preferences实例。 |
| [removePreferencesFromCacheSync](arkts-arkdata-sendablepreferences-removepreferencesfromcachesync-f.md#removepreferencesfromcachesync) | 从缓存中移除指定的Preferences实例，此为同步接口。  应用首次调用[getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md#getpreferences)接口获取某个Preferences实例后，该实例会被缓存起来，后续调用[getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md#getpreferences)时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。调用此接口移除缓存中的实例之后，再次getPreferences将会重新读取持久化文件，生成新的Preferences实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Options](arkts-arkdata-sendablepreferences-options-i.md) | Preferences实例配置选项。 |
| [Preferences](arkts-arkdata-sendablepreferences-preferences-i.md) | Preferences继承自[ISendable](../../../arkts-utils/arkts-sendable.md#isendable)，可以在ArkTS并发实例间（包括主线程、TaskPool&Worker工作线程）传递，传递的行为是引用传递，提供获取和修改存储数据的接口。  下列接口都需先使用[sendablePreferences.getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md#getpreferences)获取到Preferences实例，再通过此实例调用对应接口。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [MAX_KEY_LENGTH](arkts-arkdata-sendablepreferences-con.md#max_key_length) | Key的最大长度限制为1024个字节。 |
| [MAX_VALUE_LENGTH](arkts-arkdata-sendablepreferences-con.md#max_value_length) | Value的最大长度限制为16MB。 |

