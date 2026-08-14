# getDispatchInfo（系统接口）

## getDispatchInfo

```TypeScript
function getDispatchInfo(callback: AsyncCallback<DispatchInfo>): void
```

获取有关dispatch版本的信息。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-freeInstall-function getDispatchInfo(callback: AsyncCallback<DispatchInfo>): void--><!--Device-freeInstall-function getDispatchInfo(callback: AsyncCallback<DispatchInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;DispatchInfo&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)。当函数调用成功，err为undefined，data 为获取到的[DispatchInfo](arkts-ability-dispatchinfo-i-sys.md#DispatchInfo（系统接口）)信息。否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

```TypeScript
import { freeInstall } from '@kit.AbilityKit';

try {
  freeInstall.getDispatchInfo((err, data) => {
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


## getDispatchInfo

```TypeScript
function getDispatchInfo(): Promise<DispatchInfo>
```

获取有关dispatch版本的信息。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-freeInstall-function getDispatchInfo(): Promise<DispatchInfo>--><!--Device-freeInstall-function getDispatchInfo(): Promise<DispatchInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DispatchInfo&gt; | Promise对象，返回[DispatchInfo]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { freeInstall } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  freeInstall.getDispatchInfo().then(data => {
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
try {
  freeInstall.getDispatchInfo().then((data: freeInstall.DispatchInfo) => {
    console.info('Operation succeed:' + JSON.stringify(data));
  }).catch((err: Error) => {
    console.error('Operation failed:' + JSON.stringify(err as BusinessError));
  });
} catch (err) {
  console.error('Operation failed:' + JSON.stringify(err));
}
```

