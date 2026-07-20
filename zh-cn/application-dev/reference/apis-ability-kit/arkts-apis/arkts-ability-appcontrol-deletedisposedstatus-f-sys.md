# deleteDisposedStatus（系统接口）

## 导入模块

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

<a id="deletedisposedstatus"></a>
## deleteDisposedStatus

```TypeScript
function deleteDisposedStatus(appId: string, callback: AsyncCallback<void>): void
```

删除应用的处置状态。使用callback异步回调，成功返回null，失败返回对应错误信息。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function deleteDisposedStatus(appId: string, callback: AsyncCallback<void>): void--><!--Device-appControl-function deleteDisposedStatus(appId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 要删除拦截规则的应用的appId或appIdentifier。使用appId设置的拦截规则只能通过appId删除，使用appIdentifier设置的同理。<br/>**说明：**<br/> appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见[获取应用的appId](docroot://quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。<br>[appIdentifier](arkts-ability-bundleinfo-signatureinfo-i.md)也是应用的唯一标识，详情信息可参考[什么是appIdentifier](docroot://quick-start/common-problem-of-application.md#什么是appidentifier)，获取方法参见[获取应用的appIdentifier](docroot://quick-start/common-problem-of-application.md#如何获取应用信息中的appidentifier)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置处置状态成功时，err返回null；否则回调函数返回具体错误对象。 |

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


<a id="deletedisposedstatus-1"></a>
## deleteDisposedStatus

```TypeScript
function deleteDisposedStatus(appId: string): Promise<void>
```

删除应用的处置状态。使用promise异步回调，成功返回null，失败返回对应错误信息。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function deleteDisposedStatus(appId: string): Promise<void>--><!--Device-appControl-function deleteDisposedStatus(appId: string): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 要删除拦截规则的应用的appId或appIdentifier。使用appId设置的拦截规则只能通过appId删除，使用appIdentifier设置的同理。<br/>**说明：**<br/> appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见[获取应用的appId](docroot://quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。<br>[appIdentifier](arkts-ability-bundleinfo-signatureinfo-i.md)也是应用的唯一标识，详情信息可参考[什么是appIdentifier](docroot://quick-start/common-problem-of-application.md#什么是appidentifier)，获取方法参见[获取应用的appIdentifier](docroot://quick-start/common-problem-of-application.md#如何获取应用信息中的appidentifier)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

