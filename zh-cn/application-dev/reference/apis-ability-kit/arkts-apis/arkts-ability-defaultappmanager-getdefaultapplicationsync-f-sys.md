# getDefaultApplicationSync（系统接口）

## 导入模块

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## getDefaultApplicationSync

```TypeScript
function getDefaultApplicationSync(type: string, userId?: int): BundleInfo
```

以同步方法根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型获取默认应用信息，使用 BundleInfo返回结果。

**起始版本：** 23

**需要权限：** ohos.permission.GET_DEFAULT_APPLICATION

<!--Device-defaultAppManager-function getDefaultApplicationSync(type: string, userId?: int): BundleInfo--><!--Device-defaultAppManager-function getDefaultApplicationSync(type: string, userId?: int): BundleInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要查询的应用类型，取 [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md)中的值，或者符合媒体类型格式的文件类型，或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型。 |
| userId | int | 否 | 表示用户ID，可以通过 [getOsAccountLocalId接口](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) 获取。默认值：调用方所在用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BundleInfo](arkts-ability-bundleinfo-i.md) | 返回的默认应用包信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700025](../errorcode-bundle.md#17700025-输入的type无效) | The specified type is invalid. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [17700023](../errorcode-bundle.md#17700023-指定的默认应用不存在) | The specified default app does not exist. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

**示例**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

try {
  let data = defaultAppManager.getDefaultApplicationSync(defaultAppManager.ApplicationType.BROWSER)
  console.info('Operation successful. bundleInfo: ' + JSON.stringify(data));
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

try {
  let data = defaultAppManager.getDefaultApplicationSync("image/png")
  console.info('Operation successful. bundleInfo: ' + JSON.stringify(data));
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

try {
  let data = defaultAppManager.getDefaultApplicationSync(uniformTypeDescriptor.UniformDataType.AVI)
  console.info('Operation successful. bundleInfo: ' + JSON.stringify(data));
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};
```

