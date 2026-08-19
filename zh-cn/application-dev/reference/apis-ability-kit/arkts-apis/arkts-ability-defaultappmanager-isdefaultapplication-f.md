# isDefaultApplication

## 导入模块

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## isDefaultApplication

```TypeScript
function isDefaultApplication(type: string, callback: AsyncCallback<boolean>) : void
```

根据系统已定义的应用类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-data-uniformtypedescriptor.md)类型判断当前应用是否是该类型的默认应用。使用 callback异步回调。

**起始版本：** 23

<!--Device-defaultAppManager-function isDefaultApplication(type: string, callback: AsyncCallback<boolean>) : void--><!--Device-defaultAppManager-function isDefaultApplication(type: string, callback: AsyncCallback<boolean>) : void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要查询的应用类型，取[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md)或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-data-uniformtypedescriptor.md)类型中的值。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | [回调函数](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)，当获取成功时，err为undefined，data为bool值 ，true表示是默认应用，false表示不是默认应用；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

ArkTS-Dyn示例:

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

defaultAppManager.isDefaultApplication(defaultAppManager.ApplicationType.BROWSER, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. IsDefaultApplication ? ' + JSON.stringify(data));
});
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

defaultAppManager.isDefaultApplication(defaultAppManager.ApplicationType.BROWSER, (err: BusinessError | null, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. IsDefaultApplication ? ' + JSON.stringify(data));
});
```


## isDefaultApplication

```TypeScript
function isDefaultApplication(type: string) : Promise<boolean>
```

根据系统已定义的应用类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型判断当前 应用是否是该类型的默认应用。使用Promise异步回调。

**起始版本：** 23

<!--Device-defaultAppManager-function isDefaultApplication(type: string) : Promise<boolean>--><!--Device-defaultAppManager-function isDefaultApplication(type: string) : Promise<boolean>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要查询的应用类型，取[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md)或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-data-uniformtypedescriptor.md)类型中的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回当前应用是否是默认应用，true表示是默认应用，false表示不是默认应用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

ArkTS-Dyn示例:

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

defaultAppManager.isDefaultApplication(defaultAppManager.ApplicationType.BROWSER)
  .then((data) => {
    console.info('Operation successful. IsDefaultApplication ? ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
});
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

defaultAppManager.isDefaultApplication(defaultAppManager.ApplicationType.BROWSER)
  .then((data: boolean) => {
    console.info('Operation successful. IsDefaultApplication ? ' + JSON.stringify(data));
  }).catch((error: Error) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error as BusinessError));
  });
```

