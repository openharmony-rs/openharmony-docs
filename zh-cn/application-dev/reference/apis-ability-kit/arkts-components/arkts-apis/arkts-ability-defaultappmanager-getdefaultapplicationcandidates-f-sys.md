# getDefaultApplicationCandidates（系统接口）

## 导入模块

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## getDefaultApplicationCandidates

```TypeScript
function getDefaultApplicationCandidates(type: ApplicationType, abilityFlags: number, userId?: number): Promise<Array<AbilityInfo>>
```

查询可被设置为指定类型默认应用的应用列表。当前仅支持**BROWSER**类型的查询。未被授予ohos.permission.DEFAULT_WEB_BROWSER权限的应用将从结果中排除。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or (ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md) | 是 | 目标应用类型。详见[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md)。当前仅支持**BROWSER**，传入其它值时返回错误码17700025。 |
| abilityFlags | number | 是 | [Ability flag](arkts-ability-bundlemanager-abilityflag-e.md)，表示要获取的Ability信息。多个标志可使用按位或运算符组合，例如bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT &#124; bundleManager.AbilityFlag.GET_ABILITY_INFO_WITH_PERMISSION，可同时获取默认Ability信息和权限信息。 |
| userId | number | 否 | 表示用户ID，可以通过[getOsAccountLocalId接口](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)获取。默认值：调用方所在用户的用户ID。查询其它用户需要ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AbilityInfo](arkts-ability-abilityinfo-i.md)&gt;&gt; | Promise对象，返回符合要求的全部应用的Ability信息。未被授予ohos.permission.DEFAULT_WEB_BROWSER权限的应用将从结果中排除。若没有符合要求的应用，返回空数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700025](../errorcode-bundle.md#17700025-输入的type无效) | The specified type is invalid. |

**示例**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

defaultAppManager.getDefaultApplicationCandidates(defaultAppManager.ApplicationType.BROWSER, 0).then((data) => {
  console.info('Operation successful. Data: ' + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
});

let userId = 100;
defaultAppManager.getDefaultApplicationCandidates(defaultAppManager.ApplicationType.BROWSER, 0, userId).then((data) => {
  console.info('Operation successful. Data: ' + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
});
```
