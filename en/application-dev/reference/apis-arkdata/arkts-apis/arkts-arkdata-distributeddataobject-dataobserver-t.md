# DataObserver

```TypeScript
type DataObserver = (sessionId: string, fields: Array<string>) => void
```

Defines the callback used to listen for data changes of a distributed data object.

**Since:** 20

<!--Device-distributedDataObject-type DataObserver = (sessionId: string, fields: Array<string>) => void--><!--Device-distributedDataObject-type DataObserver = (sessionId: string, fields: Array<string>) => void-End-->

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | Session ID of the distributed data object, with a maximum length of 128 bytes. The value can contain only letters, digits, and underscores (_). |
| fields | Array&lt;string&gt; | Yes | Changed properties of the distributed data object, with a maximum length of 128 bytes. The value can be customized and must be a non-empty string. |
