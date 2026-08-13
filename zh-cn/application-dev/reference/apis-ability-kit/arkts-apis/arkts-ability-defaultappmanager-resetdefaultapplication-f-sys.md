# resetDefaultApplication（系统接口）

## resetDefaultApplication

```TypeScript
function resetDefaultApplication(type: string, userId: int, callback: AsyncCallback<void>) : void
```

根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#UniformDataType)类型重置默认应用。使用callback异 步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_DEFAULT_APPLICATION

<!--Device-defaultAppManager-function resetDefaultApplication(type: string, userId: int, callback: AsyncCallback<void>) : void--><!--Device-defaultAppManager-function resetDefaultApplication(type: string, userId: int, callback: AsyncCallback<void>) : void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要重置的应用类型，取 [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)中的值，或者符合媒体类型格式的文件类型，或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#UniformDataType)类型。 |
| userId | int | 是 | 表示用户ID，可以通过 [getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)，当重置默认应用成功时，err返回undefined。否则回调函数返回 具体错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700025](../errorcode-bundle.md#17700025-输入的type无效) | The specified type is invalid. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

let userId = 100;
defaultAppManager.resetDefaultApplication(defaultAppManager.ApplicationType.BROWSER, userId,
  (err: BusinessError, data) => {
    if (err) {
      console.error('Operation failed. Cause: ' + JSON.stringify(err));
      return;
    }
    console.info('Operation successful.');
  });

defaultAppManager.resetDefaultApplication("image/png", userId, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});

defaultAppManager.resetDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, userId,
  (err: BusinessError, data) => {
    if (err) {
      console.error('Operation failed. Cause: ' + JSON.stringify(err));
      return;
    }
    console.info('Operation successful.');
  });
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

// 代码中使用的useId需为应用实际的用户ID。
let userId = 100;
defaultAppManager.resetDefaultApplication(defaultAppManager.ApplicationType.BROWSER, userId, (err, data) => {
  if (err) {
    console.error('resetDefaultApplication failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('resetDefaultApplication successful.');
});

defaultAppManager.resetDefaultApplication("image/png", userId, (err, data) => {
  if (err) {
    console.error('resetDefaultApplication failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('resetDefaultApplication successful.');
});

defaultAppManager.resetDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, userId, (err, data) => {
  if (err) {
    console.error('resetDefaultApplication failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('resetDefaultApplication successful.');
});
```


## resetDefaultApplication

```TypeScript
function resetDefaultApplication(type: string, callback: AsyncCallback<void>) : void
```

根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#UniformDataType)类型重置默认应用。使用callback异 步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_DEFAULT_APPLICATION

<!--Device-defaultAppManager-function resetDefaultApplication(type: string, callback: AsyncCallback<void>) : void--><!--Device-defaultAppManager-function resetDefaultApplication(type: string, callback: AsyncCallback<void>) : void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要重置的应用类型，取 [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)中的值，或者符合媒体类型格式的文件类型，或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#UniformDataType)类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)，当重置默认应用成功时，err返回undefined。否则回调函数返回 具体错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700025](../errorcode-bundle.md#17700025-输入的type无效) | The specified type is invalid. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

defaultAppManager.resetDefaultApplication(defaultAppManager.ApplicationType.BROWSER, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});

defaultAppManager.resetDefaultApplication("image/png", (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});

defaultAppManager.resetDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

defaultAppManager.resetDefaultApplication(defaultAppManager.ApplicationType.BROWSER, (err: BusinessError | null, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});

defaultAppManager.resetDefaultApplication("image/png", (err: BusinessError | null, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});

defaultAppManager.resetDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, (err: BusinessError | null, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful.');
});
```


## resetDefaultApplication

```TypeScript
function resetDefaultApplication(type: string, userId?: int) : Promise<void>
```

根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#UniformDataType)类型重置默认应用。使用Promise异步 回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_DEFAULT_APPLICATION

<!--Device-defaultAppManager-function resetDefaultApplication(type: string, userId?: int) : Promise<void>--><!--Device-defaultAppManager-function resetDefaultApplication(type: string, userId?: int) : Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要重置的应用类型，取 [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md#ApplicationType)中的值，或者符合媒体类型格式的文件类型，或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#UniformDataType)类型。 |
| userId | int | 否 | 表示用户ID，可以通过 [getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取。默认值：调用方所在用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700025](../errorcode-bundle.md#17700025-输入的type无效) | The specified type is invalid. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

let userId = 100;
defaultAppManager.resetDefaultApplication(defaultAppManager.ApplicationType.BROWSER, userId)
  .then((data) => {
    console.info('Operation successful.');
  })
  .catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  });

defaultAppManager.resetDefaultApplication("image/png", userId)
  .then((data) => {
    console.info('Operation successful.');
  })
  .catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  });

defaultAppManager.resetDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, userId)
  .then((data) => {
    console.info('Operation successful.');
  })
  .catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  });
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

// 代码中使用的useId需为应用实际的用户ID。
let userId = 100;
defaultAppManager.resetDefaultApplication(defaultAppManager.ApplicationType.BROWSER, userId)
  .then((data) => {
    console.info('resetDefaultApplication successful.');
  })
  .catch((error: Error) => {
    console.error('resetDefaultApplication failed. Cause: ' + JSON.stringify(error));
  });

defaultAppManager.resetDefaultApplication("image/png", userId)
  .then((data) => {
    console.info('resetDefaultApplication successful.');
  })
  .catch((error: Error) => {
    console.error('resetDefaultApplication failed. Cause: ' + JSON.stringify(error));
  });

defaultAppManager.resetDefaultApplication(uniformTypeDescriptor.UniformDataType.AVI, userId)
  .then((data) => {
    console.info('resetDefaultApplication successful.');
  })
  .catch((error: Error) => {
    console.error('resetDefaultApplication failed. Cause: ' + JSON.stringify(error));
  });
```

