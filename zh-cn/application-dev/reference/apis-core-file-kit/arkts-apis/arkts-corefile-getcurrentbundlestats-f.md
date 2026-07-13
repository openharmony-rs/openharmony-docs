# getCurrentBundleStats

## getCurrentBundleStats

```TypeScript
function getCurrentBundleStats(callback: AsyncCallback<BundleStats>): void
```

应用异步获取当前应用存储空间大小（单位为Byte），使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;BundleStats&gt; | 是 | 获取指定卷上的应用存储空间大小之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:Mandatoryparameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

```TypeScript
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


## getCurrentBundleStats

```TypeScript
function getCurrentBundleStats(): Promise<BundleStats>
```

应用异步获取当前应用存储空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleStats&gt; | Promise对象，返回指定卷上的应用存储空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:Mandatoryparameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getCurrentBundleStats().then((BundleStats: storageStatistics.BundleStats) => {
  console.info("getCurrentBundleStats successfully:" + JSON.stringify(BundleStats));
}).catch((err: BusinessError) => {
  console.error("getCurrentBundleStats failed with error:"+ JSON.stringify(err));
});

```

