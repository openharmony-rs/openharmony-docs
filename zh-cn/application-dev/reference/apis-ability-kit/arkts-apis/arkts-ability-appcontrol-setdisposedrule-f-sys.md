# setDisposedRule（系统接口）

## setDisposedRule

```TypeScript
function setDisposedRule(appId: string, rule: DisposedRule, appIndex?: int): void
```

设置指定应用或分身应用的拦截规则。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function setDisposedRule(appId: string, rule: DisposedRule, appIndex?: int): void--><!--Device-appControl-function setDisposedRule(appId: string, rule: DisposedRule, appIndex?: int): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 要被设置拦截规则应用的appId或appIdentifier。使用appId设置的拦截规则会覆盖使用appIdentifier设置的拦截规则，反之同理。&lt;br/&gt;**说明：**&lt; br/&gt; appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见 [获取应用的appId](../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appid)。&lt;br&gt; [appIdentifier](arkts-ability-bundleinfo-signatureinfo-i.md#SignatureInfo)也是应用的唯一标识，详情信息可参考 [什么是appIdentifier](../../../quick-start/common-problem-of-application.md#什么是appidentifier)，获取方法参见 [获取应用的appIdentifier](../../../quick-start/common-problem-of-application.md#如何获取应用信息中的appidentifier)。 |
| rule | [DisposedRule](arkts-ability-appcontrol-disposedrule-i-sys.md) | 是 | 指示对应用的拦截规则。 |
| appIndex | int | 否 | 表示分身应用的索引，默认值为0。&lt;br&gt; appIndex为0时，表示设置主应用的拦截规则。appIndex大于0时，表示设置指定分身应用的拦截规则。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex is not in the valid range.<br>**适用版本：** 12+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. A non-system application is not allowed to call a system API. |
| [17700005](../errorcode-bundle.md#17700005-指定的appid为空字符串) | The specified app ID is invalid. |

## 示例

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';
import { bundleManager } from '@kit.AbilityKit';

let appId = "com.example.myapplication_xxxxx";
let want: Want = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  abilityName: "EntryAbility"
};
let elementName: bundleManager.ElementName = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  abilityName: "EntryAbility"
};
let rule: appControl.DisposedRule = {
  want: want,
  componentType: appControl.ComponentType.UI_ABILITY,
  disposedType: appControl.DisposedType.BLOCK_APPLICATION,
  controlType: appControl.ControlType.ALLOWED_LIST,
  elementList: [
    elementName
  ],
  priority: 100,
  pageJump: appControl.PageJumpMode.PAGE_JUMP_WINDOW_SHOW
};

try {
  appControl.setDisposedRule(appId, rule, 1);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('setDisposedRule failed ' + message);
}
```

