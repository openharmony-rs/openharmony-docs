# StatusObserver

```TypeScript
type StatusObserver = (sessionId: string, networkId: string, status: string) => void
```

Defines an observer for obtaining the status change of a distributed object.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | Session ID of the distributed data object, with a maximum length of 128 bytes. The value can contain only letters, digits, and underscores (_). |
| networkId | string | Yes | Network ID of the peer device, with a maximum of 255 bytes. The value must be a non- empty string. |
| status | string | Yes | Status of the distributed object. The value can be **online**, **offline**, or **restore.** |
