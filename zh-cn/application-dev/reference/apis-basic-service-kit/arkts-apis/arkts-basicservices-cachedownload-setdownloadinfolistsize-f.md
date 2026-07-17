# setDownloadInfoListSize

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## setDownloadInfoListSize

```TypeScript
function setDownloadInfoListSize(size: number): void
```

设置下载信息列表的大小。

- 下载信息列表用于存储预下载信息。  
- 下载信息和url一一对应，每次预下载都会生成一个下载信息，相同url下只会保存最新的下载信息。  
- 使用该接口调整列表大小时，size更新增大，列表中原有的信息不变，更新减小，默认使用“LRU”（最近最少使用）方式清除多余的已缓存信息。

**起始版本：** 20

<!--Device-cacheDownload-function setDownloadInfoListSize(size: long): void--><!--Device-cacheDownload-function setDownloadInfoListSize(size: long): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 设置的下载信息列表大小。取值范围：[0, 8192]，默认为0，表示不会存储任何下载信息。 |

**示例：**

```TypeScript
import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';

try {
  // 设置下载信息列表大小。  
  cacheDownload.setDownloadInfoListSize(2048);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set download information list size. err code: ${err.code}, err message: ${err.message}`);
}

```

