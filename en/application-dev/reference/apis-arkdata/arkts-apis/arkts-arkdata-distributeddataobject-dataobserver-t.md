# DataObserver

```TypeScript
type DataObserver = (sessionId: string, fields: Array<string>) => void
```

Defines an observer for obtaining the data change of a distributed object.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | Session ID of the distributed data object, with a maximum length of 128 bytes. The value can contain only letters, digits, and underscores (_). |
| fields | Array&lt;string&gt; | Yes | Changed properties of the distributed data object, with a maximum length of 128 bytes. The value can be customized and must be a non-empty string. |
