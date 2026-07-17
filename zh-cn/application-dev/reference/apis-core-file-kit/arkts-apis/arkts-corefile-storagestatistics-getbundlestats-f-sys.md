# getBundleStats（系统接口）

## 导入模块

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getBundleStats

```TypeScript
function getBundleStats(packageName: string, callback: AsyncCallback<BundleStats>, index?: number): void
```

异步获取应用存储数据的空间大小（单位为Byte），以callback方式返回。

**起始版本：** 9

**需要权限：** ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getBundleStats(packageName: string, callback: AsyncCallback<BundleStats>, index?: int): void--><!--Device-storageStatistics-function getBundleStats(packageName: string, callback: AsyncCallback<BundleStats>, index?: int): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| packageName | string | 是 | 应用包名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<BundleStats> | 是 | 获取指定卷上的应用存储数据的空间大小之后的回调。 |
| index | number | 否 | 分身应用的索引号，默认值为0（表示未分身的主应用）。分身应用索引号在分身创建时默认占用从1开始且当前未被占用的最小索引号，并赋值给该应用的[BundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourceinfo-i-sys.md)的appIndex属性，后续可以通过调用[getBundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourcemanager-getbundleresourceinfo-f-sys.md#getbundleresourceinfo-2)接口获得。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { storageStatistics } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let bundleFlags = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, bundleFlags);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s', JSON.stringify(resourceInfo.label));

  let packageName:string = bundleName;
  let index:number = resourceInfo.appIndex;
  storageStatistics.getBundleStats(packageName, (err: BusinessError, bundleStats: storageStatistics.BundleStats) => {
    if (err) {
      console.error(`getBundleStats failed with err, code is: ${err.code}, message is: ${err.message}`);
    } else {
      hilog.info(0x0000, 'testTag', 'getBundleStats successfully. BundleStats: %{public}s', JSON.stringify(bundleStats));
    }
  }, index);

} catch (err) {
  let message = (err as BusinessError).message;
  console.error(`getBundleResourceInfo failed with err, message is: ${message}`);
}

```


## getBundleStats

```TypeScript
function getBundleStats(packageName: string, index?: number): Promise<BundleStats>
```

异步获取应用存储数据的空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 9

**需要权限：** ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getBundleStats(packageName: string, index?: int): Promise<BundleStats>--><!--Device-storageStatistics-function getBundleStats(packageName: string, index?: int): Promise<BundleStats>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| packageName | string | 是 | 应用包名。 |
| index | number | 否 | 分身应用的索引号，默认值为0（表示未分身的主应用）。分身应用索引号在分身创建时默认占用从1开始且当前未被占用的最小索引号，并赋值给该应用的[BundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourceinfo-i-sys.md)的appIndex属性，后续可以通过调用[getBundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourcemanager-getbundleresourceinfo-f-sys.md#getbundleresourceinfo-2)接口获得。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<BundleStats> | Promise对象，返回指定卷上的应用存储数据的空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { storageStatistics } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let bundleFlags = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, bundleFlags);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s', JSON.stringify(resourceInfo.label));

  let packageName:string = bundleName;
  let index:number = resourceInfo.appIndex;
  storageStatistics.getBundleStats(packageName, index).then((bundleStats: storageStatistics.BundleStats) => {
    hilog.info(0x0000, 'testTag', 'getBundleStats successfully. BundleStats: %{public}s', JSON.stringify(bundleStats));
  }).catch((err: BusinessError) => {
    console.error(`getBundleStats failed with err, code is: ${err.code}, message is: ${err.message}`);
  });

} catch (err) {
  let message = (err as BusinessError).message;
  console.error(`getBundleResourceInfo failed with err, message is: ${message}`);
}

```

