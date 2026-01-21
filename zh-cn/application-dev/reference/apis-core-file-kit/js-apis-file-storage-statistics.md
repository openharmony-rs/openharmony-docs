# @ohos.file.storageStatistics (应用空间统计)

该模块提供空间查询相关的常用功能：包括对内外卡的空间查询、对应用分类数据统计的查询、对应用数据的查询等。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import  { storageStatistics } from '@kit.CoreFileKit';
```

## storageStatistics.getCurrentBundleStats<sup>9+</sup>

getCurrentBundleStats(): Promise&lt;BundleStats&gt;

应用异步获取当前应用存储空间大小（单位为Byte），以Promise方式返回。

**系统能力**：SystemCapability.FileManagement.StorageService.SpatialStatistics

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型                                        | 说明                       |
| ------------------------------------------ | -------------------------- |
| Promise&lt;[BundleStats](#bundlestats9)&gt; | Promise对象，返回指定卷上的应用存储空间大小（单位为Byte）。      |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getCurrentBundleStats().then((BundleStats: storageStatistics.BundleStats) => {
  console.info("getCurrentBundleStats successfully:" + JSON.stringify(BundleStats));
}).catch((err: BusinessError) => {
  console.error("getCurrentBundleStats failed with error:"+ JSON.stringify(err));
});
```

## storageStatistics.getCurrentBundleStats<sup>9+</sup>

getCurrentBundleStats(callback: AsyncCallback&lt;BundleStats&gt;): void

应用异步获取当前应用存储空间大小（单位为Byte），以callback方式返回。

**系统能力**：SystemCapability.FileManagement.StorageService.SpatialStatistics

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名    | 类型                                                       | 必填  | 说明                                 |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------ |
| callback | AsyncCallback&lt;[BundleStats](#bundlestats9)&gt;          | 是   | 获取指定卷上的应用存储空间大小之后的回调。        |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getCurrentBundleStats((error: BusinessError, bundleStats: storageStatistics.BundleStats) => {
  if (error) {
    console.error("getCurrentBundleStats failed with error:" + JSON.stringify(error));
  } else {
    // do something
    console.info("getCurrentBundleStats successfully:" + JSON.stringify(bundleStats));
  }
});
```

## storageStatistics.getTotalSize<sup>15+</sup>

ArkTS-Dyn: getTotalSize(): Promise&lt;number&gt;

ArkTS-Sta: getTotalSize(): Promise&lt;long&gt;

获取内置存储的总空间大小（单位为Byte），以Promise方式返回。

**系统能力**：SystemCapability.FileManagement.StorageService.SpatialStatistics

**ArkTS-Dyn起始版本**：15

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型                  | 说明                                                |
| --------------------- | --------------------------------------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;long&gt; | Promise对象，返回内置存储的总空间大小（单位为Byte）。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息       |
| -------- | -------------- |
| 13600001 | IPC error.     |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getTotalSize().then((totalSize: number) => {
  console.info("getTotalSize successfully:" + JSON.stringify(totalSize));
}).catch((err: BusinessError) => {
  console.error("getTotalSize failed with error:"+ JSON.stringify(err));
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
let totalSize: long = 0;
storageStatistics.getTotalSize().then((totalSize) => {
  console.info("getTotalSize successfully:" + totalSize);
}).catch((err: BusinessError):void => {
  console.error("getTotalSize failed with error:"+ JSON.stringify(err));
});
```

## storageStatistics.getTotalSize<sup>15+</sup>

ArkTS-Dyn: getTotalSize(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getTotalSize(callback: AsyncCallback&lt;long&gt;): void

获取内置存储的总空间大小（单位为Byte），以callback方式返回。

**系统能力**：SystemCapability.FileManagement.StorageService.SpatialStatistics

**ArkTS-Dyn起始版本**：15

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                        | 必填 | 说明                               |
| -------- | --------------------------- | ---- | ---------------------------------- |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: AsyncCallback&lt;long&gt; | 是   | 获取内置存储的总空间大小之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error.                                                   |
| 13900042 | Unknown error.                                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getTotalSize((error: BusinessError, totalSize: number) => {
  if (error) {
    console.error("getTotalSize failed with error:" + JSON.stringify(error));
  } else {
    // do something
    console.info("getTotalSize successfully:" + totalSize);
  }
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
let error: BusinessError = {};
let totalSize: long = 0;
storageStatistics.getTotalSize((error, totalSize) => {
  if (error) {
    console.error("getTotalSize failed with error:" + JSON.stringify(error));
  } else {
    // do something
    console.info("getTotalSize successfully:" + totalSize);
  }
});
```

## storageStatistics.getTotalSizeSync<sup>15+</sup>

ArkTS-Dyn: getTotalSizeSync(): number

ArkTS-Sta: getTotalSizeSync(): int

同步获取内置存储的总空间大小（单位为Byte）。

**系统能力**：SystemCapability.FileManagement.StorageService.SpatialStatistics

**ArkTS-Dyn起始版本**：15

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型   | 说明                                   |
| ------ | -------------------------------------- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | 返回内置存储的总空间大小（单位为Byte）。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息       |
| -------- | -------------- |
| 13600001 | IPC error.     |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let totalSize = storageStatistics.getTotalSizeSync();
  console.info("getTotalSizeSync successfully:" + JSON.stringify(totalSize));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("getTotalSizeSync failed with error:" + JSON.stringify(error));
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let totalSize = storageStatistics.getTotalSizeSync();
  console.info("getTotalSizeSync successfully:" + JSON.stringify(totalSize));
} catch (err: BusinessError) {
  console.error("getTotalSizeSync failed with error:" + JSON.stringify(err));
}
```

## storageStatistics.getFreeSize<sup>15+</sup>

ArkTS-Dyn: getFreeSize(): Promise&lt;number&gt;

ArkTS-Sta: getFreeSize(): Promise&lt;long&gt;

获取内置存储的可用空间大小（单位为Byte），以Promise方式返回。

**系统能力**：SystemCapability.FileManagement.StorageService.SpatialStatistics

**ArkTS-Dyn起始版本**：15

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型                  | 说明                                                  |
| --------------------- | ----------------------------------------------------- |
|  ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;long&gt;| Promise对象，返回内置存储的可用空间大小（单位为Byte）。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息       |
| -------- | -------------- |
| 13600001 | IPC error.     |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getFreeSize().then((totalSize: number) => {
  console.info("getFreeSize successfully:" + JSON.stringify(totalSize));
}).catch((err: BusinessError) => {
  console.error("getFreeSize failed with error:" + JSON.stringify(err));
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
let totalSize: long = 0;
storageStatistics.getFreeSize().then((totalSize) => {
  console.info("getFreeSize successfully:" + totalSize);
}).catch((err: BusinessError): void => {
  console.error("getFreeSize failed with error:" + JSON.stringify(err));
});
```

## storageStatistics.getFreeSize<sup>15+</sup>

ArkTS-Dyn: getFreeSize(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getFreeSize(callback: AsyncCallback&lt;long&gt;): void

获取内置存储的可用空间大小（单位为Byte），以callback方式返回。

**系统能力**：SystemCapability.FileManagement.StorageService.SpatialStatistics

**ArkTS-Dyn起始版本**：15

**ArkTS-Sta起始版本**：23

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                 |
| -------- | --------------------------- | ---- | ------------------------------------ |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: AsyncCallback&lt;long&gt; | 是   | 获取内置存储的可用空间大小之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error.                                                   |
| 13900042 | Unknown error.                                               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getFreeSize((error: BusinessError, totalSize: number) => {
  if (error) {
    console.error("getFreeSize failed with error:" + JSON.stringify(error));
  } else {
    // do something
    console.info("getFreeSize successfully:" + number);
  }
});
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
let error: BusinessError = {};
let totalSize: long = 0;
storageStatistics.getFreeSize((error: BusinessError, totalSize: number): void => {
  if (error) {
    console.error("getFreeSize failed with error:" + JSON.stringify(error));
  } else {
    // do something
    console.info("getFreeSize successfully:" + totalSize);
  }
});
```

## storageStatistics.getFreeSizeSync<sup>15+</sup>

ArkTS-Dyn: getFreeSizeSync(): number

ArkTS-Sta: getFreeSizeSync(): long

同步获取内置存储的可用空间大小（单位为Byte）。

**系统能力**：SystemCapability.FileManagement.StorageService.SpatialStatistics

**ArkTS-Dyn起始版本**：15

**ArkTS-Sta起始版本**：23

**返回值：**

| 类型   | 说明                                     |
| ------ | ---------------------------------------- |
| ArkTS-Dyn:number<br>ArkTS-Sta: long | 返回内置存储的可用空间大小（单位为Byte）。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息       |
| -------- | -------------- |
| 13600001 | IPC error.     |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let freeSize = storageStatistics.getFreeSizeSync();
  console.info("getFreeSizeSync successfully:" + JSON.stringify(freeSize));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("getFreeSizeSync failed with error:" + JSON.stringify(error));
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let freeSize = storageStatistics.getFreeSizeSync();
  console.info("getFreeSizeSync successfully:" + JSON.stringify(freeSize));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("getFreeSizeSync failed with error:" + JSON.stringify(error));
}
```

## BundleStats<sup>9+</sup>

**系统能力**：SystemCapability.FileManagement.StorageService.SpatialStatistics

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

| 名称      | 类型   | 必填 | 说明           |
| --------- | ------ | --- | -------------- |
| appSize   | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是 | 应用安装文件大小（单位为Byte）。    |
| cacheSize | ArkTS-Dyn: number<br>ArkTS-Sta: long  | 是 | 应用缓存文件大小（单位为Byte）。   |
| dataSize  | ArkTS-Dyn: number<br>ArkTS-Sta: long  | 是 | 应用文件存储大小（除应用安装文件和缓存文件）（单位为Byte）。 |
