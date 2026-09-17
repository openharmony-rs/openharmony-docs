# @ohos.data.distributedDataObject(Distributed Data Object)

The distributedDataObject module provides basic data object management, including creating, querying, deleting, modifying, and subscribing to data objects, and distributed data object collaboration for the same application among multiple devices. Although this module does not parse user data, you are advised not to transfer sensitive personal data or privacy data due to low-level security of storage path.

**Since:** 8

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## Modules to Import

```TypeScript
import { distributedDataObject } from '@kit.ArkData';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [create](arkts-arkdata-distributeddataobject-create-f.md) | Creates a distributed data object. The object properties support basic types (number, Boolean, and string) and complex types (array and nested basic types). |
| [createDistributedObject](arkts-arkdata-distributeddataobject-createdistributedobject-f.md) | Creates a distributed data object. |
| [genSessionId](arkts-arkdata-distributeddataobject-gensessionid-f.md) | Creates a random session ID. |

### Interfaces

| Name | Description |
| --- | --- |
| [BindInfo](arkts-arkdata-distributeddataobject-bindinfo-i.md) | Represents the information about the joint asset in the RDB store to bind. Currently, only the RDB stores are supported. |
| [DataObject](arkts-arkdata-distributeddataobject-dataobject-i.md) | Provides APIs for managing a distributed data object. Before using any API of this class, use create() to create a DataObject object. |
| [DistributedObject](arkts-arkdata-distributeddataobject-distributedobject-i.md) | Provides APIs for managing a distributed data object. Before using any API of this class, use createDistributedObject() to create a DistributedObject object. |
| [RevokeSaveSuccessResponse](arkts-arkdata-distributeddataobject-revokesavesuccessresponse-i.md) | Represents the information returned by the callback of revokeSave. |
| [SaveSuccessResponse](arkts-arkdata-distributeddataobject-savesuccessresponse-i.md) | Represents the information returned by the callback of save.. |

### Types

| Name | Description |
| --- | --- |
| [DataObserver](arkts-arkdata-distributeddataobject-dataobserver-t.md) | Defines an observer for obtaining the data change of a distributed object. |
| [ProgressObserver](arkts-arkdata-distributeddataobject-progressobserver-t.md) | Defines an observer for obtaining the transfer progress. |
| [StatusObserver](arkts-arkdata-distributeddataobject-statusobserver-t.md) | Defines an observer for obtaining the status change of a distributed object. |
