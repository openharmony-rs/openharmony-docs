# deleteRdbStore

## Modules to Import

```TypeScript
```

<a id="deleterdbstore1"></a>

## deleteRdbStore

```TypeScript
function deleteRdbStore(context: Context, name: string, callback: AsyncCallback<void>): void
```

Deletes an RDB store. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md)

<!--Device-rdb-function deleteRdbStore(context: Context, name: string, callback: AsyncCallback<void>): void--><!--Device-rdb-function deleteRdbStore(context: Context, name: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context.<br>For details about the application context of the FA model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context.md). <br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context.md). |
| name | string | Yes | Name of the RDB store to delete. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |


<a id="deleterdbstore2"></a>

## deleteRdbStore

```TypeScript
function deleteRdbStore(context: Context, name: string): Promise<void>
```

Deletes an RDB store. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md)

<!--Device-rdb-function deleteRdbStore(context: Context, name: string): Promise<void>--><!--Device-rdb-function deleteRdbStore(context: Context, name: string): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context.<br>For details about the application context of the FA model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context.md). <br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context.md). |
| name | string | Yes | Name of the RDB store to delete. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
