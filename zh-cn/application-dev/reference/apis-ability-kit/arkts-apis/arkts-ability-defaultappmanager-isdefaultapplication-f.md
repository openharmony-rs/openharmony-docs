# isDefaultApplication

## 导入模块

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## isDefaultApplication

```TypeScript
function isDefaultApplication(type: string, callback: AsyncCallback<boolean>) : void
```

根据系统已定义的应用类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-data-uniformtypedescriptor.md)类型判断当前应用是否是该类型的默认应用。使用callback异步回调。

**起始版本：** 9

<!--Device-defaultAppManager-function isDefaultApplication(type: string, callback: AsyncCallback<boolean>) : void--><!--Device-defaultAppManager-function isDefaultApplication(type: string, callback: AsyncCallback<boolean>) : void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要查询的应用类型，取[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md)或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-data-uniformtypedescriptor.md)类型中的值。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，当获取成功时，err为undefined，data为bool值，true表示是默认应用，false表示不是默认应用；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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


## isDefaultApplication

```TypeScript
function isDefaultApplication(type: string) : Promise<boolean>
```

根据系统已定义的应用类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型判断当前应用是否是该类型的默认应用。使用Promise异步回调。

**起始版本：** 9

<!--Device-defaultAppManager-function isDefaultApplication(type: string) : Promise<boolean>--><!--Device-defaultAppManager-function isDefaultApplication(type: string) : Promise<boolean>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要查询的应用类型，取[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md)或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-data-uniformtypedescriptor.md)类型中的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象，返回当前应用是否是默认应用，true表示是默认应用，false表示不是默认应用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

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

