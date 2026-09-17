# AssetLoader (System API)

Provides APIs for uploading and downloading assets.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## download

```TypeScript
download(table: string, gid: string, prefix: string, assets: Array<CloudAsset>): Promise<Array<Result<CloudAsset>>>
```

Downloads assets. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Table name. |
| gid | string | Yes | Unique identifier generated for the data added to the cloud. |
| prefix | string | Yes | Asset prefix information. |
| assets | Array&lt;[CloudAsset](arkts-arkdata-cloudextension-cloudasset-i-sys.md)&gt; | Yes | Assets to download. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;[CloudAsset](arkts-arkdata-cloudextension-cloudasset-i-sys.md)&gt;&gt;&gt; | Promise used to return the asset download result, including the asset IDs and asset hash values. |

**Examples**

```TypeScript
class MyAssetLoader implements cloudExtension.AssetLoader {
  async download(table: string, gid: string, prefix: string, assets: Array<cloudExtension.CloudAsset>): Promise<Array<cloudExtension.Result<cloudExtension.CloudAsset>>> {
    console.info(`download asset loader, table: ${table}, gid: ${gid}, prefix: ${prefix}`);
    let downloadRes = Array<cloudExtension.Result<cloudExtension.CloudAsset>>();
    // ...
    return downloadRes;
  }
}
```

## upload

```TypeScript
upload(table: string, gid: string, assets: Array<CloudAsset>): Promise<Array<Result<CloudAsset>>>
```

Uploads assets. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Table name. |
| gid | string | Yes | Unique identifier generated for the data added to the cloud. |
| assets | Array&lt;[CloudAsset](arkts-arkdata-cloudextension-cloudasset-i-sys.md)&gt; | Yes | Assets to upload. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&lt;[CloudAsset](arkts-arkdata-cloudextension-cloudasset-i-sys.md)&gt;&gt;&gt; | Promise used to return the asset upload result, including the asset IDs and asset hash values. |

**Examples**

```TypeScript
class MyAssetLoader implements cloudExtension.AssetLoader {
  async upload(table: string, gid: string, assets: Array<cloudExtension.CloudAsset>): Promise<Array<cloudExtension.Result<cloudExtension.CloudAsset>>> {
    console.info(`upload asset loader, table: ${table}, gid: ${gid}`);
    let uploadRes = Array<cloudExtension.Result<cloudExtension.CloudAsset>>();
    // ...
    return uploadRes;
  }
    // ...
}
```
