# getDisposedStatus（系统接口）

## 导入模块

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## getDisposedStatus

```TypeScript
function getDisposedStatus(appId: string, callback: AsyncCallback<Want>): void
```

获取指定应用的处置状态。使用callback异步回调，成功返回应用的处置状态，失败返回对应错误信息。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

<!--Device-appControl-function getDisposedStatus(appId: string, callback: AsyncCallback<Want>): void--><!--Device-appControl-function getDisposedStatus(appId: string, callback: AsyncCallback<Want>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 要查询的应用的appId。<br> appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见[获取应用的appId](../../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Want> | 是 | 回调函数。当获取应用的处置状态成功时，err为null，data为获取到的处置状态；否则为错误对象。 |

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

let appId = "com.example.myapplication_xxxxx";

try {
  appControl.getDisposedStatus(appId, (error, data) => {
    if (error) {
      let message = (error as BusinessError).message;
      console.error('getDisposedStatus failed ' + message);
      return;
    }
    console.info('getDisposedStatus success. DisposedStatus: ' + JSON.stringify(data));
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedStatus failed ' + message);
}

```


## getDisposedStatus

```TypeScript
function getDisposedStatus(appId: string): Promise<Want>
```

获取指定应用已设置的处置状态。使用Promise异步回调，成功返回应用的处置状态，失败返回对应错误信息。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

<!--Device-appControl-function getDisposedStatus(appId: string): Promise<Want>--><!--Device-appControl-function getDisposedStatus(appId: string): Promise<Want>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 要查询的应用的appId。<br> appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见[获取应用的appId](../../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Want> | Promise对象，返回应用的处置状态。 |

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

let appId = "com.example.myapplication_xxxxx";

try {
  appControl.getDisposedStatus(appId)
    .then((data) => {
      console.info('getDisposedStatus success. DisposedStatus: ' + JSON.stringify(data));
    }).catch((error: BusinessError) => {
    let message = (error as BusinessError).message;
    console.error('getDisposedStatus failed ' + message);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedStatus failed ' + message);
}

```

