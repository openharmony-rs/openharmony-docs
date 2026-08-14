# getBundleArchiveInfo

## getBundleArchiveInfo

```TypeScript
function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number, callback: AsyncCallback<BundleInfo>): void
```

获取有关HAP中包含的应用程序包的信息，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-bundle-function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number, callback: AsyncCallback<BundleInfo>): void--><!--Device-bundle-function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number, callback: AsyncCallback<BundleInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePath | string | 是 | HAP存放路径，支持当前应用程序的绝对路径和数据目录沙箱路径。 |
| bundleFlags | number | 是 | 用于指定要返回的BundleInfo对象中包含信息的标记。取值范围：参考[BundleFlag说明](arkts-ability-bundle-bundleflag-e.md#BundleFlag)中包信息相关 flag。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[BundleInfo](arkts-ability-bundleinfo-bundleinfo-depr-i.md)&gt; | 是 | 程序启动作为入参的回调函数，返回HAP中包含的应用程序包的信息。 |

## 示例

```TypeScript
import bundle from '@ohos.bundle';

let hapFilePath: string = "/data/storage/el2/base/test.hap";
let bundleFlags: number = 0;

bundle.getBundleArchiveInfo(hapFilePath, bundleFlags, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```


## getBundleArchiveInfo

```TypeScript
function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number): Promise<BundleInfo>
```

获取有关HAP中包含的应用程序包的信息，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-bundle-function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number): Promise<BundleInfo>--><!--Device-bundle-function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number): Promise<BundleInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePath | string | 是 | HAP存放路径。支持当前应用程序的绝对路径和数据目录沙箱路径。 |
| bundleFlags | number | 是 | 用于指定要返回的BundleInfo对象中包含信息的标记。取值范围：参考[BundleFlag说明](arkts-ability-bundle-bundleflag-e.md#BundleFlag)中包信息相关 flag。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[BundleInfo](arkts-ability-bundleinfo-bundleinfo-depr-i.md)&gt; | Returns the BundleInfo object. |

## 示例

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let hapFilePath: string = "/data/storage/el2/base/test.hap";
let bundleFlags: number = 0;

bundle.getBundleArchiveInfo(hapFilePath, bundleFlags)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```

