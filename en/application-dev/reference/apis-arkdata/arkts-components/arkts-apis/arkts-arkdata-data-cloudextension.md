# @ohos.data.cloudExtension(Device-Cloud Sharing Extension)

The cloudExtension module provides APIs for third-party vendors to implement the device-cloud sharing service. You can use these APIs to share the device data to the server and implement device-cloud data sharing, including sharing and unsharing data, exiting a share,changing the privilege (operation permissions) on the shared data, querying participants by data identifier or invitation code, and confirming or changing a sharing invitation.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createAssetLoaderStub](arkts-arkdata-cloudextension-createassetloaderstub-f-sys.md) | Creates a RemoteObject instance based on an AssetLoader instance. The system uses this object to call the APIs of the AssetLoader instance. This API uses a promise to return the result. |
| [createCloudDBStub](arkts-arkdata-cloudextension-createclouddbstub-f-sys.md) | Creates a RemoteObject instance based on a CloudDB instance. The system uses this object to call the APIs of the CloudDB instance. This API uses a promise to return the result. |
| [createCloudServiceStub](arkts-arkdata-cloudextension-createcloudservicestub-f-sys.md) | Creates a RemoteObject instance based on a CloudService instance. The system uses this object to call the APIs of the CloudService instance. This API uses a promise to return the result. |
| [createShareServiceStub](arkts-arkdata-cloudextension-createshareservicestub-f-sys.md) | Creates a RemoteObject instance based on a ShareCenter instance. The system uses this object to call the APIs of the ShareCenter instance. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AppBriefInfo](arkts-arkdata-cloudextension-appbriefinfo-i-sys.md) | Represents the brief application information. |
| [AppSchema](arkts-arkdata-cloudextension-appschema-i-sys.md) | Represents the application database schema. |
| [AssetLoader](arkts-arkdata-cloudextension-assetloader-i-sys.md) | Provides APIs for uploading and downloading assets. |
| [CloudAsset](arkts-arkdata-cloudextension-cloudasset-i-sys.md) | Represents the cloud asset information. |
| [CloudData](arkts-arkdata-cloudextension-clouddata-i-sys.md) | Represents the cloud data. |
| [CloudDB](arkts-arkdata-cloudextension-clouddb-i-sys.md) | Provides APIs for performing cloud database operations. |
| [CloudInfo](arkts-arkdata-cloudextension-cloudinfo-i-sys.md) | Represents the cloud information. |
| [CloudService](arkts-arkdata-cloudextension-cloudservice-i-sys.md) | Provides APIs for interacting with the cloud sync service. You need to inherit this class and implement APIs of this class. The system calls these APIs to connect to the cloud and use the cloud sync service. |
| [Database](arkts-arkdata-cloudextension-database-i-sys.md) | Represents the database information. |
| [ExtensionValue](arkts-arkdata-cloudextension-extensionvalue-i-sys.md) | Represents additional information about a data record. |
| [Field](arkts-arkdata-cloudextension-field-i-sys.md) | Represents a field in the database. |
| [LockInfo](arkts-arkdata-cloudextension-lockinfo-i-sys.md) | Represents the cloud database lock information. |
| [Result](arkts-arkdata-cloudextension-result-i-sys.md) | Represents the data sharing result. |
| [ServiceInfo](arkts-arkdata-cloudextension-serviceinfo-i-sys.md) | Represents the cloud service information. |
| [ShareCenter](arkts-arkdata-cloudextension-sharecenter-i-sys.md) | Provides APIs for interacting with the sharedCenter service. You need to inherit this class and implement APIs of this class. The system calls these APIs to initiate, cancel, or exit a device-cloud share. |
| [SubscribeId](arkts-arkdata-cloudextension-subscribeid-i-sys.md) | Represents the subscription ID information. |
| [SubscribeInfo](arkts-arkdata-cloudextension-subscribeinfo-i-sys.md) | Represents the subscription information. |
| [Table](arkts-arkdata-cloudextension-table-i-sys.md) | Represents the table information. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ErrorCode](arkts-arkdata-cloudextension-errorcode-e-sys.md) | Enumerates the device-cloud sync states. Use the enum name rather than the enum value. |
| [FieldType](arkts-arkdata-cloudextension-fieldtype-e-sys.md) | Enumerates the types of the fields in a database table. Use the enum name rather than the enum value. |
| [Flag](arkts-arkdata-cloudextension-flag-e-sys.md) | Enumerates the operations that can be performed on a database. Use the enum name rather than the enum value. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [CloudAssets](arkts-arkdata-cloudextension-cloudassets-t-sys.md) | Represents an array of CloudAsset. |
| [CloudType](arkts-arkdata-cloudextension-cloudtype-t-sys.md) | Enumerates the types of the cloud data field. The specific type is determined by the parameter function. |
<!--DelEnd-->
