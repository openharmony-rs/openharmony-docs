# getDisposedStatusSync（系统接口）

## 导入模块

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## getDisposedStatusSync

```TypeScript
function getDisposedStatusSync(appId: string): Want
```

以同步方法获取指定应用已设置的处置状态。成功返回应用的处置状态，失败抛出对应异常。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

<!--Device-appControl-function getDisposedStatusSync(appId: string): Want--><!--Device-appControl-function getDisposedStatusSync(appId: string): Want-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 要查询的应用的appId。<br> appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见 [获取应用的appId](../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Want](arkts-ability-app-ability-want-want-c.md) | 返回应用的处置状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700005](../errorcode-bundle.md#17700005-指定的appid为空字符串) | The specified app ID is empty string. |

**示例**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let appId: string = "com.example.myapplication_xxxxx";
let want: Want;

try {
  want = appControl.getDisposedStatusSync(appId);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedStatusSync failed ' + message);
}
```

