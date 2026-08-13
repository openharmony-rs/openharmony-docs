# getBundleStats（系统接口）

## getBundleStats

```TypeScript
function getBundleStats(packageName: string, callback: AsyncCallback<BundleStats>, index?: int): void
```

异步获取应用存储数据的空间大小（单位为Byte），以callback方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getBundleStats(packageName: string, callback: AsyncCallback<BundleStats>, index?: int): void--><!--Device-storageStatistics-function getBundleStats(packageName: string, callback: AsyncCallback<BundleStats>, index?: int): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| packageName | string | 是 | 应用包名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md)&gt; | 是 | 获取指定卷上的应用存储数据的空间大小之后的回调。 |
| index | int | 否 | 分身应用的索引号，默认值为0（表示未分身的主应用）。分身应用索引号在分身创建时默认 占用从1开始且当前未被占用的最小索引号，并赋值给该应用的 [BundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourceinfo-i-sys.md#BundleResourceInfo（系统接口）)的appIndex属性，后续可以通过调用 [getBundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourcemanager-getbundleresourceinfo-f-sys.md#getBundleResourceInfo（系统接口）) 接口获得。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid. |
| 13600008 | No such object. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let bundleFlags = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, bundleFlags);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s', JSON.stringify(resourceInfo.label));

  let packageName:string = bundleName;
  let index:number = resourceInfo.appIndex;
  storageStatistics.getBundleStats(packageName, (err: BusinessError, BundleStats: storageStatistics.BundleStats) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getBundleStats failed with err: %{public}s', JSON.stringify(err));
    } else {
      hilog.info(0x0000, 'testTag', 'getBundleStats successfully. BundleStats: %{public}s', JSON.stringify(BundleStats));
    }
  }, index);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed with err: %{public}s', message);
}
```

ArkTS-Sta示例：

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let bundleFlags = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, bundleFlags);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s', JSON.stringify(resourceInfo.label));
  let packageName:string = bundleName;
  let index:int = resourceInfo.appIndex;
  storageStatistics.getBundleStats(packageName, (err: BusinessError, BundleStats: storageStatistics.BundleStats): void => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getBundleStats failed with err: %{public}s', JSON.stringify(err));
    } else {
      hilog.info(0x0000, 'testTag', 'getBundleStats successfully. BundleStats: %{public}s', JSON.stringify(BundleStats));
    }
  }, index);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed with err: %{public}s', message);
}
```


## getBundleStats

```TypeScript
function getBundleStats(packageName: string, index?: int): Promise<BundleStats>
```

异步获取应用存储数据的空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getBundleStats(packageName: string, index?: int): Promise<BundleStats>--><!--Device-storageStatistics-function getBundleStats(packageName: string, index?: int): Promise<BundleStats>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| packageName | string | 是 | 应用包名。 |
| index | int | 否 | 分身应用的索引号，默认值为0（表示未分身的主应用）。分身应用索引号在分身创建时默认占用 从1开始且当前未被占用的最小索引号，并赋值给该应用的 [BundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourceinfo-i-sys.md#BundleResourceInfo（系统接口）)的appIndex属性，后续可以通过调用 [getBundleResourceInfo] [getBundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourcemanager-getbundleresourceinfo-f-sys.md#getBundleResourceInfo（系统接口）) 接口获得。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[BundleStats](arkts-corefile-storagestatistics-bundlestats-i.md)&gt; | Promise对象，返回指定卷上的应用存储数据的空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid. |
| 13600008 | No such object. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let bundleFlags = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, bundleFlags);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s', JSON.stringify(resourceInfo.label));

  let packageName:string = bundleName;
  let index:number = resourceInfo.appIndex;
  storageStatistics.getBundleStats(packageName, index).then((BundleStats: storageStatistics.BundleStats) => {
    hilog.info(0x0000, 'testTag', 'getBundleStats successfully. BundleStats: %{public}s', JSON.stringify(BundleStats));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getBundleStats failed with err: %{public}s', JSON.stringify(err));
  });

} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed with err: %{public}s', message);
}
```

ArkTS-Sta示例：

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let bundleFlags = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, bundleFlags);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s', JSON.stringify(resourceInfo.label));

  let packageName:string = bundleName;
  let index:int = resourceInfo.appIndex;
  storageStatistics.getBundleStats(packageName, index).then((BundleStats: storageStatistics.BundleStats): void => {
    hilog.info(0x0000, 'testTag', 'getBundleStats successfully. BundleStats: %{public}s', JSON.stringify(BundleStats));
  }).catch((err: BusinessError): void => {
    hilog.error(0x0000, 'testTag', 'getBundleStats failed with err: %{public}s', JSON.stringify(err));
  });

} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed with err: %{public}s', message);
}
```

