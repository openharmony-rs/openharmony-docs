# AssetLoader（系统接口）

提供资产上传下载接口的类。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-cloudExtension-export interface AssetLoader--><!--Device-cloudExtension-export interface AssetLoader-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## download

```TypeScript
download(table: string, gid: string, prefix: string, assets: Array<CloudAsset>): Promise<Array<Result<CloudAsset>>>
```

通过该接口实现资产的下载。使用Promise异步回调。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-AssetLoader-download(table: string, gid: string, prefix: string, assets: Array<CloudAsset>): Promise<Array<Result<CloudAsset>>>--><!--Device-AssetLoader-download(table: string, gid: string, prefix: string, assets: Array<CloudAsset>): Promise<Array<Result<CloudAsset>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 表名。 |
| gid | string | 是 | 数据上云后生成的唯一标记。 |
| prefix | string | 是 | 表示资产下载目录的前缀信息。 |
| assets | Array&lt;CloudAsset&gt; | 是 | 表示需要下载的资产。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Result&lt;CloudAsset&gt;&gt;&gt; | Promise对象，返回资产下载结果，包含资产ID和资产哈希值。 |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import cloudExtension from '@ohos.data.cloudExtension';
export default class MyAssetLoader implements cloudExtension.AssetLoader {
  async download(table: string, gid: string, prefix: string, assets: Array<cloudExtension.CloudAsset>): Promise<Array<cloudExtension.Result<cloudExtension.CloudAsset>>> {
    console.info(`download asset loader, table: ${table}, gid: ${gid}, prefix: ${prefix}`);
    let downloadRes = Array<cloudExtension.Result<cloudExtension.CloudAsset>>();
    // ...
    return downloadRes;
  }
  async upload(table: string, gid: string, assets: cloudExtension.CloudAsset[]): Promise<cloudExtension.Result<cloudExtension.CloudAsset>[]> {
    return [] as cloudExtension.Result<cloudExtension.CloudAsset>[];
  }
}
```

## upload

```TypeScript
upload(table: string, gid: string, assets: Array<CloudAsset>): Promise<Array<Result<CloudAsset>>>
```

通过该接口实现资产的上传。使用Promise异步回调。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-AssetLoader-upload(table: string, gid: string, assets: Array<CloudAsset>): Promise<Array<Result<CloudAsset>>>--><!--Device-AssetLoader-upload(table: string, gid: string, assets: Array<CloudAsset>): Promise<Array<Result<CloudAsset>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 表名。 |
| gid | string | 是 | 表示GID，数据上云后生成的唯一标记。 |
| assets | Array&lt;CloudAsset&gt; | 是 | 表示需要上传的资产。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Result&lt;CloudAsset&gt;&gt;&gt; | Promise对象，返回资产上云的结果，包含资产ID和资产哈希值。 |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import cloudExtension from '@ohos.data.cloudExtension';
export default class MyAssetLoader implements cloudExtension.AssetLoader {
  async upload(table: string, gid: string, assets: Array<cloudExtension.CloudAsset>): Promise<Array<cloudExtension.Result<cloudExtension.CloudAsset>>> {
    console.info(`upload asset loader, table: ${table}, gid: ${gid}`);
    let uploadRes = Array<cloudExtension.Result<cloudExtension.CloudAsset>>();
    // ...
    return uploadRes;
  }
  // ...
  async download(table: string, gid: string, prefix: string, assets: cloudExtension.CloudAsset[]): Promise<cloudExtension.Result<cloudExtension.CloudAsset>[]> {
    return [] as cloudExtension.Result<cloudExtension.CloudAsset>[];
  }
}
```

