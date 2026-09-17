# @ohos.data.dataSharePredicates(数据共享谓词)

**谓词(DataSharePredicates)** 是开发者通过DataShare查询数据库中的数据所使用的筛选条件，经常被应用在更新数据、删除数据和查询数据中。<br> <br>谓词的接口函数与数据库的筛选条件一一对应，开发者在使用前需了解数据库相关知识。<br> <br>谓词(DataSharePredicates)的使用场景如下：<br> <br>- 用于在媒体文件管理服务作为检索条件使用，参考相册管理模块检索条件[FetchOptions](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchoptions-i.md)。此种场景下，开发者无需关注数据库类型。<br> <!--Del-->

<br>- 用于调用[关系型数据库](../../../reference/apis-arkdata/js-apis-data-relationalStore-sys.md)和[分布式键值数据库](../../../reference/apis-arkdata/js-apis-distributedKVStore-sys.md)系统接口时的检索条件使用。此种场景下，开发者根据使用的数据库类型参考对应的谓词使用方法。

<!--DelEnd-->

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

## 导入模块

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 提供用于不同实现不同查询方法的数据共享谓词。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c-sys.md) | 提供用于不同实现不同查询方法的数据共享谓词。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。 |
<!--DelEnd-->
