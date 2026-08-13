# getCurrentBundleStats

## getCurrentBundleStats

```TypeScript
function getCurrentBundleStats(callback: AsyncCallback<BundleStats>): void
```

应用异步获取当前应用存储空间大小（单位为Byte），使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-storageStatistics-function getCurrentBundleStats(callback: AsyncCallback<BundleStats>): void--><!--Device-storageStatistics-function getCurrentBundleStats(callback: AsyncCallback<BundleStats>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md)&gt; | 是 | 获取指定卷上的应用存储空间大小之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getCurrentBundleStats((error: BusinessError, bundleStats: storageStatistics.BundleStats) => {
  if (error) {
    console.error(`getCurrentBundleStats failed. Code: ${error.code}, message: ${error.message}`);
  } else {
    // do something
    console.info('getCurrentBundleStats successfully:' + JSON.stringify(bundleStats));
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getCurrentBundleStats((error: BusinessError, bundleStats: storageStatistics.BundleStats): void => {
  if (error) {
    console.error(`getCurrentBundleStats failed. Code: ${error.code}, message: ${error.message}`);
  } else {
    // do something
    console.info('getCurrentBundleStats successfully:' + JSON.stringify(bundleStats));
  }
});
```


## getCurrentBundleStats

```TypeScript
function getCurrentBundleStats(): Promise<BundleStats>
```

应用异步获取当前应用存储空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-storageStatistics-function getCurrentBundleStats(): Promise<BundleStats>--><!--Device-storageStatistics-function getCurrentBundleStats(): Promise<BundleStats>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md)&gt; | Promise对象，返回指定卷上的应用存储空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getCurrentBundleStats().then((bundleStats: storageStatistics.BundleStats) => {
  console.info('getCurrentBundleStats successfully:' + JSON.stringify(bundleStats));
}).catch((err: BusinessError) => {
  console.error(`getCurrentBundleStats failed. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getCurrentBundleStats().then((bundleStats: storageStatistics.BundleStats) => {
  console.info('getCurrentBundleStats successfully:' + JSON.stringify(bundleStats));
}).catch((err: BusinessError): void => {
  console.error(`getCurrentBundleStats failed. Code: ${err.code}, message: ${err.message}`);
});
```

