# getEnterpriseInfo（系统接口）

## getEnterpriseInfo

```TypeScript
function getEnterpriseInfo(admin: Want, callback: AsyncCallback<EnterpriseInfo>): void
```

获取设备管理应用的企业信息。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function getEnterpriseInfo(admin: Want, callback: AsyncCallback<EnterpriseInfo>): void--><!--Device-adminManager-function getEnterpriseInfo(admin: Want, callback: AsyncCallback<EnterpriseInfo>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[EnterpriseInfo](arkts-mdm-adminmanager-enterpriseinfo-i-sys.md)&gt; | 是 | 回调函数，当接口调用成功，err为null，data为设备管理应用的企业信息，否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |

## 示例

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

adminManager.getEnterpriseInfo(wantTemp, (err, result) => {
  if (err) {
    console.error(`Failed to get enterprise info. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting enterprise info, enterprise name : ${result.name}, enterprise description : ${result.description}`);
});
```


## getEnterpriseInfo

```TypeScript
function getEnterpriseInfo(admin: Want): Promise<EnterpriseInfo>
```

获取设备管理应用的企业信息，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function getEnterpriseInfo(admin: Want): Promise<EnterpriseInfo>--><!--Device-adminManager-function getEnterpriseInfo(admin: Want): Promise<EnterpriseInfo>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[EnterpriseInfo](arkts-mdm-adminmanager-enterpriseinfo-i-sys.md)&gt; | Promise对象，返回设备管理应用的企业信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |

## 示例

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

adminManager.getEnterpriseInfo(wantTemp).then((result) => {
  console.info(`Succeeded in getting enterprise info, enterprise name : ${result.name}, enterprise description : ${result.description}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get enterprise info. Code: ${err.code}, message: ${err.message}`);
});
```

