# getBundlePackInfo（系统接口）

## getBundlePackInfo

```TypeScript
function getBundlePackInfo(bundleName: string, 
    bundlePackFlag : BundlePackFlag, callback: AsyncCallback<BundlePackInfo>): void
```

基于bundleName和bundlePackFlag来获取bundlePackInfo。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-freeInstall-function getBundlePackInfo(bundleName: string,     bundlePackFlag : BundlePackFlag, callback: AsyncCallback<BundlePackInfo>): void--><!--Device-freeInstall-function getBundlePackInfo(bundleName: string,     bundlePackFlag : BundlePackFlag, callback: AsyncCallback<BundlePackInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| bundlePackFlag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要查询的应用包标志。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;BundlePackInfo&gt; | 是 | [回调函数]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。当函数调用成功，err为undefined，data为获取到的BundlePackInfo信息。否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |

**示例：**

```TypeScript
import { freeInstall } from '@kit.AbilityKit';

let bundleName = 'com.example.myapplication';
let bundlePackFlag = freeInstall.BundlePackFlag.GET_PACK_INFO_ALL;
try {
  freeInstall.getBundlePackInfo(bundleName, bundlePackFlag, (err, data) => {
    if (err) {
      console.error('Operation failed:' + JSON.stringify(err));
    } else {
      console.info('Operation succeed:' + JSON.stringify(data));
    }
  });
} catch (err) {
  console.error('Operation failed:' + JSON.stringify(err));
}
```


## getBundlePackInfo

```TypeScript
function getBundlePackInfo(bundleName: string, bundlePackFlag : BundlePackFlag): Promise<BundlePackInfo>
```

基于bundleName和BundlePackFlag来获取bundlePackInfo。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-freeInstall-function getBundlePackInfo(bundleName: string, bundlePackFlag : BundlePackFlag): Promise<BundlePackInfo>--><!--Device-freeInstall-function getBundlePackInfo(bundleName: string, bundlePackFlag : BundlePackFlag): Promise<BundlePackInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用程序Bundle名称。 |
| bundlePackFlag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要查询的应用包标志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundlePackInfo&gt; | Promise对象，返回BundlePackInfo信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { freeInstall } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.example.myapplication';
let bundlePackFlag = freeInstall.BundlePackFlag.GET_PACK_INFO_ALL;
try {
  freeInstall.getBundlePackInfo(bundleName, bundlePackFlag).then(data => {
    console.info('Operation succeed:' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error('Operation failed:' + JSON.stringify(err));
  });
} catch (err) {
  console.error('Operation failed:' + JSON.stringify(err));
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { freeInstall } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// 开发者需根据实际工程更新bundleName。
let bundleName = 'com.example.myapplication';
let bundlePackFlag = freeInstall.BundlePackFlag.GET_PACK_INFO_ALL;
try {
  freeInstall.getBundlePackInfo(bundleName, bundlePackFlag).then((data: freeInstall.BundlePackInfo) => {
    console.info('Operation succeed:' + JSON.stringify(data));
  }).catch((err: Error) => {
    console.error('Operation failed:' + JSON.stringify(err as BusinessError));
  });
} catch (err) {
  console.error('Operation failed:' + JSON.stringify(err));
}
```

