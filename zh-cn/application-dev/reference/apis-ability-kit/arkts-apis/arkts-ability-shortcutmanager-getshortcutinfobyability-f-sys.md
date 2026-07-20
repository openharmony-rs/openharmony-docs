# getShortcutInfoByAbility（系统接口）

## 导入模块

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
```

<a id="getshortcutinfobyability"></a>
## getShortcutInfoByAbility

```TypeScript
function getShortcutInfoByAbility(bundleName: string, moduleName: string, abilityName: string, userId?: number, appIndex?: number): Array<ShortcutInfo>
```

查询指定用户下指定UIAbility的快捷方式信息。

**起始版本：** 24

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or (ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-shortcutManager-function getShortcutInfoByAbility(bundleName: string, moduleName: string, abilityName: string, userId?: int, appIndex?: int): Array<ShortcutInfo>--><!--Device-shortcutManager-function getShortcutInfoByAbility(bundleName: string, moduleName: string, abilityName: string, userId?: int, appIndex?: int): Array<ShortcutInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示应用程序的包名。 |
| moduleName | string | 是 | 表示模块的名称。 |
| abilityName | string | 是 | 表示UIAbility组件的名称。 |
| userId | number | 否 | 表示用户ID，可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)获取。<br/>默认值：调用方所在用户。<br/>取值范围：大于等于0。 |
| appIndex | number | 否 | 表示应用索引。取值范围0~5的整数，取值为0表示主应用，取值1~5表示分身应用的索引。<br/>默认值：0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ShortcutInfo&gt; | Array形式返回指定用户下指定UIAbility的[ShortcutInfo](arkts-ability-shortcutinfo-i-sys.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle is not found. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user id is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The specified app index is invalid. |

**示例：**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请开发者替换为实际要查询的bundleName、moduleName、abilityName、userId和appIndex。
const bundleName = 'com.example.myapplication';
const moduleName = 'application';
const abilityName = 'ApplicationAbility';
let userId = 100;
let appIndex = 0;

try {
  let shortcutInfos: Array<shortcutManager.ShortcutInfo> = shortcutManager.getShortcutInfoByAbility(bundleName, moduleName, abilityName, userId, appIndex);
  console.info('getShortcutInfoByAbility shortcutInfos is' + JSON.stringify(shortcutInfos));
} catch (err) {
  console.error(`getShortcutInfoByAbility errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
}

```

```TypeScript
// 不传入可选参数appIndex
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请开发者替换为实际要查询的bundleName、moduleName、abilityName和userId。
const bundleName = 'com.example.myapplication';
const moduleName = 'application';
const abilityName = 'ApplicationAbility';
let userId = 100;

try {
  let shortcutInfos: Array<shortcutManager.ShortcutInfo> = shortcutManager.getShortcutInfoByAbility(bundleName, moduleName, abilityName, userId);
  console.info('getShortcutInfoByAbility shortcutInfos is' + JSON.stringify(shortcutInfos));
} catch (err) {
  console.error(`getShortcutInfoByAbility errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
}

```

```TypeScript
// 不传入可选参数userId和appIndex
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请开发者替换为实际要查询的bundleName、moduleName和abilityName。
const bundleName = 'com.example.myapplication';
const moduleName = 'application';
const abilityName = 'ApplicationAbility';

try {
  let shortcutInfos: Array<shortcutManager.ShortcutInfo> = shortcutManager.getShortcutInfoByAbility(bundleName, moduleName, abilityName);
  console.info('getShortcutInfoByAbility shortcutInfos is' + JSON.stringify(shortcutInfos));
} catch (err) {
  console.error(`getShortcutInfoByAbility errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
}

```

