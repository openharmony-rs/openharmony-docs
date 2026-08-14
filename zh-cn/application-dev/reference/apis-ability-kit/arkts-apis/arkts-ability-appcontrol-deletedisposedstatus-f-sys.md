# deleteDisposedStatus（系统接口）

## deleteDisposedStatus

```TypeScript
function deleteDisposedStatus(appId: string, callback: AsyncCallback<void>): void
```

删除应用的处置状态。使用callback异步回调，成功返回null，失败返回对应错误信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function deleteDisposedStatus(appId: string, callback: AsyncCallback<void>): void--><!--Device-appControl-function deleteDisposedStatus(appId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 要删除拦截规则的应用的appId或appIdentifier。使用appId设置的拦截规则只能通过appId删除，使用appIdentifier设置的同理。&lt;br/&gt; **说明：**&lt;br/&gt; appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见 [获取应用的appId](../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。&lt;br&gt; [appIdentifier](arkts-ability-bundleinfo-signatureinfo-i.md#SignatureInfo)也是应用的唯一标识，详情信息可参考 [什么是appIdentifier](../../../quick-start/common-problem-of-application.md#什么是appidentifier)，获取方法参见 [获取应用的appIdentifier](../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appidentifier)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当设置处置状态成功时，err返回null；否则回调函数返回具体错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700005](../errorcode-bundle.md#17700005-指定的appid为空字符串) | The specified app ID is empty string. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appId = "com.example.myapplication_xxxxx";
try {
  appControl.deleteDisposedStatus(appId, (error: BusinessError, data) => {
    if (error) {
      console.error('deleteDisposedStatus failed ' + error.message);
      return;
    }
    console.info('deleteDisposedStatus success');
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('deleteDisposedStatus failed ' + message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// 开发者需根据实际工程更新appId。
let appId = "com.example.myapplication_xxxxx";
try {
  appControl.deleteDisposedStatus(appId, (error: BusinessError | null, data) => {
    if (error) {
      console.error('deleteDisposedStatus failed ' + error.message);
      return;
    }
    console.info('deleteDisposedStatus success');
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('deleteDisposedStatus failed ' + message);
}
```


## deleteDisposedStatus

```TypeScript
function deleteDisposedStatus(appId: string): Promise<void>
```

删除应用的处置状态。使用promise异步回调，成功返回null，失败返回对应错误信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function deleteDisposedStatus(appId: string): Promise<void>--><!--Device-appControl-function deleteDisposedStatus(appId: string): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 要删除拦截规则的应用的appId或appIdentifier。使用appId设置的拦截规则只能通过appId删除，使用appIdentifier设置的同理。&lt;br/&gt; **说明：**&lt;br/&gt; appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见 [获取应用的appId](../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。&lt;br&gt; [appIdentifier](arkts-ability-bundleinfo-signatureinfo-i.md#SignatureInfo)也是应用的唯一标识，详情信息可参考 [什么是appIdentifier](../../../quick-start/common-problem-of-application.md#什么是appidentifier)，获取方法参见 [获取应用的appIdentifier](../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appidentifier)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700005](../errorcode-bundle.md#17700005-指定的appid为空字符串) | The specified app ID is empty string. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appId = "com.example.myapplication_xxxxx";

try {
  appControl.deleteDisposedStatus(appId)
    .then(() => {
      console.info('deleteDisposedStatus success');
    }).catch((error: BusinessError) => {
      let message = (error as BusinessError).message;
      console.error('deleteDisposedStatus failed ' + message);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('deleteDisposedStatus failed ' + message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// 开发者需根据实际工程更新appId。
let appId = "com.example.myapplication_xxxxx";

try {
  appControl.deleteDisposedStatus(appId)
    .then(() => {
      console.info('deleteDisposedStatus success');
    }).catch((error: Error) => {
      let message = (error as BusinessError).message;
      console.error('deleteDisposedStatus failed ' + message);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('deleteDisposedStatus failed ' + message);
}
```

