# @ohos.data.dataSharePredicates (DataShare Predicates) (System API)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @woodenarow-->
<!--Designer: @woodenarow; @xuelei3-->
<!--Tester: @chenwan188; @logic42-->
<!--Adviser: @ge-yafang-->

You can use **DataSharePredicates** to specify conditions for [updating](js-apis-data-dataShare-sys.md#update), [deleting](js-apis-data-dataShare-sys.md#delete), and [querying](js-apis-data-dataShare-sys.md#query) data when **DataShare** is used to manage data.

The APIs provided by **DataSharePredicates** correspond to the filter criteria of the database. Before using the APIs, you need to have basic database knowledge.

**DataSharePredicates** applies to the following scenario:

- It is used as the search criteria when APIs of the [RDB store](js-apis-data-relationalStore-sys.md) and [KV store](js-apis-distributedKVStore-sys.md) are called. In this scenario, use the corresponding predicate based on the database type.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.data.dataSharePredicates (Data Share Predicates)](js-apis-data-dataSharePredicates.md).



## Modules to Import

```ts
import { dataSharePredicates } from '@kit.ArkData';
```

## DataSharePredicates
Provides methods for setting different **DataSharePredicates** objects. This type is not multi-thread safe. If a **DataSharePredicates** instance is operated by multiple threads at the same time in an application, use a lock for the instance.

### contains

contains(field: string, value: string): DataSharePredicates

Creates a **DataSharePredicates** object to match the data that contains the specified value.

Currently, only RDB store supports this predicate.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| field  | string | Yes  | Column name in the database table.  |
| value  | string | Yes  | Value to match.|

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.contains("NAME", "os");
```

### beginsWith

beginsWith(field: string, value: string): DataSharePredicates

Creates a **DataSharePredicates** object to match the data that begins with the specified value.

Currently, only RDB store supports this predicate.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | ---------------------- |
| field  | string | Yes  | Column name in the database table.    |
| value  | string | Yes  | Start value to match.|

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.beginsWith("NAME", "os");
```

### endsWith

endsWith(field: string, value: string): DataSharePredicates

Creates a **DataSharePredicates** object to match the data that ends with the specified value.

Currently, only RDB store supports this predicate.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | ---------------------- |
| field  | string | Yes  | Column name in the database table.    |
| value  | string | Yes  | End value to match.|

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.endsWith("NAME", "os");
```

### isNull

isNull(field: string): DataSharePredicates

Creates a **DataSharePredicates** object to match the data whose value is null.

Currently, both the RDB store and KV store support this predicate.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| field  | string | Yes  | Column name in the database table.|

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.isNull("NAME");
```

### isNotNull

isNotNull(field: string): DataSharePredicates

Creates a **DataSharePredicates** object to match the data whose value is not null.

Currently, both the RDB store and KV store support this predicate.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| field  | string | Yes  | Column name in the database table.|

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.isNotNull("NAME");
```

### unlike

unlike(field: string, value: string): DataSharePredicates

Creates a **DataSharePredicates** object to match the data that does not match the specified wildcard expression.

Currently, both the RDB store and KV store support this predicate.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | ---------------------- |
| field  | string | Yes  | Column name in the database table.    |
| value  | string | Yes  | Wildcard expression to match.<br>In the expression, '%' represents zero, one, or more digits or characters, and '_' represents a single digit or character. It is case insensitive.|

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.unlike("NAME", "%os%");
```

### glob

glob(field: string, value: string): DataSharePredicates

Creates a **DataSharePredicates** object to match the data that matches the specified wildcard expression.

Currently, only RDB store supports this predicate.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type  | Mandatory| Description                  |
| ------ | ------ | ---- | ---------------------- |
| field  | string | Yes  | Column name in the database table.    |
| value  | string | Yes  | Wildcard expression to match.<br>In the expression, '*' represents zero, one, or more digits or characters, and '?' represents a single digit or character. It is case sensitive.|

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.glob("NAME", "?h*g");
```

### distinct

distinct(): DataSharePredicates

Creates a **DataSharePredicates** object to filter out duplicate data records.

Currently, only RDB store supports this predicate.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose").distinct();
```

### groupBy

groupBy(fields: Array&lt;string&gt;): DataSharePredicates

Creates a **DataSharePredicates** object group the records according to the specified fields.

Currently, only RDB store supports this predicate.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type         | Mandatory| Description                |
| ------ | ------------- | ---- | -------------------- |
| fields | Array&lt;string&gt; | Yes  | Names of the columns by which the records are grouped.|

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.groupBy(["AGE", "NAME"]);
```

### indexedBy

indexedBy(field: string): DataSharePredicates

Creates a **DataSharePredicates** object to list data by the specified index. Before using this API, ensure that the index column exists.

Currently, only RDB store supports this predicate.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| field  | string | Yes  | Name of the index column.|

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.indexedBy("SALARY_INDEX");
```

### prefixKey

prefixKey(prefix: string): DataSharePredicates

Creates a **DataSharePredicates** object to match the data with the specified key prefix.

Currently, only the KVDB supports this **DataSharePredicates** object.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| prefix | string | Yes  | Key prefix to match.|

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.prefixKey("NAME");
```

### inKeys

inKeys(keys: Array&lt;string&gt;): DataSharePredicates

Creates a **DataSharePredicates** object to match the data whose keys are within the given range.

Currently, only the KVDB supports this **DataSharePredicates** object.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type         | Mandatory| Description              |
| ------ | ------------- | ---- | ------------------ |
| keys | Array&lt;string&gt; | Yes  | Array of the keys to match.|

**Return value**

| Type                                       | Description                      |
| ------------------------------------------- | -------------------------- |
| [DataSharePredicates](#datasharepredicates) | **DataSharePredicates** object created.|

**Example**

```ts
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.inKeys(["Lisa", "Rose"]);
```
