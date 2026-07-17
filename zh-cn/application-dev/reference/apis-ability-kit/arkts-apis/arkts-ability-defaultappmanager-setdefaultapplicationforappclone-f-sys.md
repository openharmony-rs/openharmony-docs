# setDefaultApplicationForAppClone（系统接口）

## 导入模块

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## setDefaultApplicationForAppClone

```TypeScript
function setDefaultApplicationForAppClone(type: string, elementName: ElementName, appIndex: number, userId?: number): void
```

以同步方法将分身应用设置为打开相应type类型的默认应用。

**起始版本：** 23

**需要权限：** ohos.permission.SET_DEFAULT_APPLICATION or (ohos.permission.SET_DEFAULT_APPLICATION and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

<!--Device-defaultAppManager-function setDefaultApplicationForAppClone(type: string, elementName: ElementName, appIndex: int, userId?: int): void--><!--Device-defaultAppManager-function setDefaultApplicationForAppClone(type: string, elementName: ElementName, appIndex: int, userId?: int): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要设置的应用类型，支持取值包括：[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md)中的值、[MIMEType](../../../../database/uniform-data-type-list.md#基础类型)类型、或[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型。 |
| elementName | [ElementName](arkts-ability-bundlemanager-elementname-t.md) | 是 | 要设置为默认应用的组件信息，仅使用其中的bundleName、abilityName、moduleName属性，且三个属性必须设置。 |
| appIndex | number | 是 | 表示分身应用的索引。<br>取值范围：1、2、3、4、5。 |
| userId | number | 否 | 表示用户ID，可以通过[getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)获取。<br>默认值：调用方所在用户Id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. A non-system application is not allowed to call a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user id is not found. |
| [17700025](../errorcode-bundle.md#17700025-输入的type无效) | The specified type is invalid. |
| [17700028](../errorcode-bundle.md#17700028-输入的ability与type不匹配) | The specified ability and type do not match. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The specified app index is invalid. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

let appIndex = 1;
try {
  defaultAppManager.setDefaultApplicationForAppClone(defaultAppManager.ApplicationType.BROWSER, {
    // 请开发者替换为实际的bundleName、moduleName和abilityName
    bundleName: "com.example.myapplication",
    moduleName: "module01",
    abilityName: "EntryAbility"
  }, appIndex);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

let userId = 100;
try {
  defaultAppManager.setDefaultApplicationForAppClone(defaultAppManager.ApplicationType.BROWSER, {
    // 请开发者替换为实际的bundleName、moduleName和abilityName
    bundleName: "com.example.myapplication",
    moduleName: "module01",
    abilityName: "EntryAbility"
  }, appIndex, userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

try {
  defaultAppManager.setDefaultApplicationForAppClone("image/png", {
    // 请开发者替换为实际的bundleName、moduleName和abilityName
    bundleName: "com.example.myapplication",
    moduleName: "module01",
    abilityName: "EntryAbility"
  }, appIndex, userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

try {
  defaultAppManager.setDefaultApplicationForAppClone(uniformTypeDescriptor.UniformDataType.AVI, {
    // 请开发者替换为实际的bundleName、moduleName和abilityName
    bundleName: "com.example.myapplication",
    moduleName: "module01",
    abilityName: "EntryAbility"
  }, appIndex, userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

```

