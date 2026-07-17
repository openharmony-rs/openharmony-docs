# setDisposedStatus（系统接口）

## 导入模块

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## setDisposedStatus

```TypeScript
function setDisposedStatus(appId: string, disposedWant: Want, callback: AsyncCallback<void>): void
```

设置应用的处置状态。使用callback异步回调。成功返回null，失败返回对应错误信息。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function setDisposedStatus(appId: string, disposedWant: Want, callback: AsyncCallback<void>): void--><!--Device-appControl-function setDisposedStatus(appId: string, disposedWant: Want, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 需要设置处置的应用的appId。<br> appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见[获取应用的appId](../../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。 |
| disposedWant | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 对应用的处置意图。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置处置状态成功，err为null；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700005](../errorcode-bundle.md#17700005-指定的appid为空字符串) | The specified app ID is empty string. |

**示例：**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let appId = "com.example.myapplication_xxxxx";
let want: Want = { bundleName: 'com.example.myapplication' };

try {
  appControl.setDisposedStatus(appId, want, (error: BusinessError, data) => {
    if (error) {
      let message = (error as BusinessError).message;
      console.error('setDisposedStatus failed ' + message);
      return;
    }
    console.info('setDisposedStatus success');
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('setDisposedStatus failed ' + message);
}

```


## setDisposedStatus

```TypeScript
function setDisposedStatus(appId: string, disposedWant: Want): Promise<void>
```

设置应用的处置状态。使用Promise异步回调。成功返回null，失败返回对应错误信息。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function setDisposedStatus(appId: string, disposedWant: Want): Promise<void>--><!--Device-appControl-function setDisposedStatus(appId: string, disposedWant: Want): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 需要设置处置状态的应用的appId。<br> appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见[获取应用的appId](../../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。 |
| disposedWant | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 对应用的处置意图。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700005](../errorcode-bundle.md#17700005-指定的appid为空字符串) | The specified app ID is empty string. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';
import { appControl } from '@kit.AbilityKit';

let appId = "com.example.myapplication_xxxxx";
let want: Want = { bundleName: 'com.example.myapplication' };

try {
  appControl.setDisposedStatus(appId, want)
    .then(() => {
      console.info('setDisposedStatus success');
    }).catch((error: BusinessError) => {
    let message = (error as BusinessError).message;
    console.error('setDisposedStatus failed ' + message);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('setDisposedStatus failed ' + message);
}

```

