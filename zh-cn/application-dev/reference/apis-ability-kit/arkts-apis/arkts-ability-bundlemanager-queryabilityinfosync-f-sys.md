# queryAbilityInfoSync（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## queryAbilityInfoSync

```TypeScript
function queryAbilityInfoSync(want: Want, abilityFlags: int, userId?: int): Array<AbilityInfo>
```

以同步方法根据给定的want、abilityFlags和userId获取一个或多个AbilityInfo。 获取调用方自身的信息时不需要权限。

**起始版本：** 23

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundleManager-function queryAbilityInfoSync(want: Want, abilityFlags: int, userId?: int): Array<AbilityInfo>--><!--Device-bundleManager-function queryAbilityInfoSync(want: Want, abilityFlags: int, userId?: int): Array<AbilityInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 表示包含要查询的应用Bundle名称的Want。 |
| abilityFlags | int | 是 | 表示指定返回的AbilityInfo所包含的信息，具体取值及不同含义参考[AbilityFlag](arkts-ability-bundlemanager-abilityflag-e-sys.md)。 |
| userId | int | 否 | 表示用户ID，可以通过 [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) 获取，默认值：调用方所在用户，取值范围：大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;AbilityInfo&gt; | Array&lt;AbilityInfo&gt;信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit query. |
| [17700029](../errorcode-bundle.md#17700029-指定的ability被禁用) | The specified ability is disabled. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified userId is invalid. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability is not found. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

**示例**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let userId = 100;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {

  let infos = bundleManager.queryAbilityInfoSync(want, abilityFlags, userId);
  hilog.info(0x0000, 'testTag', 'queryAbilityInfoSync successfully. Data: %{public}s', JSON.stringify(infos));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfoSync failed. Cause: %{public}s', message);
}
```

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  let infos = bundleManager.queryAbilityInfoSync(want, abilityFlags);
  hilog.info(0x0000, 'testTag', 'queryAbilityInfoSync successfully. Data: %{public}s', JSON.stringify(infos));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfoSync failed. Cause: %{public}s', message);
}
```

