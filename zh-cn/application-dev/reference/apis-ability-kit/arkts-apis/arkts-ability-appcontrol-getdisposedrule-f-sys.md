# getDisposedRule（系统接口）

## 导入模块

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## getDisposedRule

```TypeScript
function getDisposedRule(appId: string, appIndex?: number): DisposedRule
```

获取指定应用或分身应用已设置的拦截规则。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

<!--Device-appControl-function getDisposedRule(appId: string, appIndex?: int): DisposedRule--><!--Device-appControl-function getDisposedRule(appId: string, appIndex?: int): DisposedRule-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 要获取拦截规则的应用的appId或appIdentifier。使用appId设置的拦截规则只能通过appId获取，使用appIdentifier设置的同理。<br/>**说明：**<br/> appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见[获取应用的appId](../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。<br>[appIdentifier](arkts-ability-bundleinfo-signatureinfo-i.md)也是应用的唯一标识，详情信息可参考[什么是appIdentifier](../../../quick-start/common-problem-of-application.md#什么是appidentifier)，获取方法参见[获取应用的appIdentifier](../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appidentifier)。 |
| appIndex | number | 否 | 表示分身应用的索引，默认值为0。<br> appIndex为0时，表示获取主应用的拦截规则。appIndex大于0时，表示获取指定分身应用的拦截规则。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DisposedRule](arkts-ability-appcontrol-disposedrule-i-sys.md) | 对应用的拦截规则。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. A non-system application is not allowed to call a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700005](../errorcode-bundle.md#17700005-指定的appid为空字符串) | The specified app ID is invalid. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex is not in the valid range.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appId = "com.example.myapplication_xxxxx";

try {
  let data = appControl.getDisposedRule(appId, 1);
  console.info('getDisposedRule successfully. Data: ' + JSON.stringify(data));
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedRule failed ' + message);
}

```

