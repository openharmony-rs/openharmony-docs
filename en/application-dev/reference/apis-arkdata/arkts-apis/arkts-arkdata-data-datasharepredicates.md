# @ohos.data.dataSharePredicates(DataShare Predicates)

**DataSharePredicates** provides a filter object to query data in a database by using **DataShare** APIs. It is often used to update, delete, and query data.

The APIs provided by **DataSharePredicates** correspond to the filter criteria of the database. Before using the APIs, you need to have basic database knowledge.

**DataSharePredicates** applies to the following scenario:

- It is used as a search criterion in the media file management service. For details, see [FetchOptions](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) in the fetch options of the album management. In this scenario, you do not need to pay attention to the database type.

<!--Del-->

- It is used as a search criterion when APIs of the [RDB store](../../../apis-arkdata/js-apis-data-relationalStore-sys.md) and [KV store](../../../apis-arkdata/js-apis-distributedKVStore-sys.md) are called. In this scenario, use the corresponding predicate based on the database type.

<!--DelEnd-->

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

## Modules to Import

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | Provides APIs for setting different **DataSharePredicates** objects. This type is not multi-thread safe. If a **DataSharePredicates** instance is operated by multiple threads at the same time in an application, use a lock for it. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c-sys.md) | Provides APIs for setting different **DataSharePredicates** objects. This type is not multi-thread safe. If a **DataSharePredicates** instance is operated by multiple threads at the same time in an application, use a lock for it. |
<!--DelEnd-->
