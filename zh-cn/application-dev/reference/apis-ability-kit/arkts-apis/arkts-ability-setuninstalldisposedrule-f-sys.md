# setUninstallDisposedRule（系统接口）

## setUninstallDisposedRule

```TypeScript
function setUninstallDisposedRule(appIdentifier: string, rule: UninstallDisposedRule, appIndex?: number): void
```

设置指定应用或分身应用的卸载处置规则。

**起始版本：** 15

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appIdentifier | string | 是 | 要设置卸载处置规则的应用的appIdentifier。<br> 如果应用没有appIdentifier可使用appId代替。appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见[获取应用的appId](../../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。 |
| rule | UninstallDisposedRule | 是 | 表示要设置的卸载处置规则。 |
| appIndex | number | 否 | 表示分身应用的索引，默认值为0。<br> appIndex为0时，表示设置主应用的卸载处置规则。appIndex大于0时，表示设置指定分身应用的卸载处置规则。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. A non-system application is not allowed to call a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex is not in the valid range. |
| [17700074](../errorcode-bundle.md#17700074-传入的appidentifier无效) | The specified appIdentifier is invalid. |
| [17700075](../errorcode-bundle.md#17700075-want指定的bundlename与调用方不符) | The specified bundleName of want is not the same with caller. |

**示例：**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let appIdentifier = "com.example.myapplication_xxxxx";
let want: Want = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  abilityName: "EntryAbility"
};
let rule: appControl.UninstallDisposedRule = {
  want: want,
  uninstallComponentType: appControl.UninstallComponentType.EXTENSION,
  priority: 100
};

try {
  appControl.setUninstallDisposedRule(appIdentifier, rule, 1);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('setUninstallDisposedRule failed ' + message);
}

```

