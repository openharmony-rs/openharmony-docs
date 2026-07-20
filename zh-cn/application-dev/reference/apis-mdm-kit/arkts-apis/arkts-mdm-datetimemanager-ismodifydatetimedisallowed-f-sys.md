# isModifyDateTimeDisallowed（系统接口）

## 导入模块

```TypeScript
import { dateTimeManager } from '@kit.MDMKit';
```

<a id="ismodifydatetimedisallowed"></a>
## isModifyDateTimeDisallowed

```TypeScript
function isModifyDateTimeDisallowed(admin: Want, callback: AsyncCallback<boolean>): void
```

查询设备是否允许修改系统时间。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [getDisallowedPolicy(admin:](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_DATETIME

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dateTimeManager-function isModifyDateTimeDisallowed(admin: Want, callback: AsyncCallback<boolean>): void--><!--Device-dateTimeManager-function isModifyDateTimeDisallowed(admin: Want, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数，callback方式返回是否禁止修改系统时间策略，true表示禁止修改系统时间，否则表示允许修改系统时间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { dateTimeManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

dateTimeManager.isModifyDateTimeDisallowed(wantTemp, (err, result) => {
  if (err) {
    console.error(`Failed to query modify date time is disallowed or not. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying modify date time is disallowed : ${result}`);
})

```


<a id="ismodifydatetimedisallowed-1"></a>
## isModifyDateTimeDisallowed

```TypeScript
function isModifyDateTimeDisallowed(admin: Want): Promise<boolean>
```

查询设备是否允许修改系统时间。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [getDisallowedPolicy(admin:](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_DATETIME

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dateTimeManager-function isModifyDateTimeDisallowed(admin: Want): Promise<boolean>--><!--Device-dateTimeManager-function isModifyDateTimeDisallowed(admin: Want): Promise<boolean>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。Promise方式返回是否禁止修改系统时间策略，true表示禁止修改系统时间，否则表示允许修改系统时间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { dateTimeManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

dateTimeManager.isModifyDateTimeDisallowed(wantTemp).then((result) => {
  console.info(`Succeeded in querying modify date time is disallowed : ${result}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to query modify date time is disallowed or not. Code is ${err.code}, message is ${err.message}`);
})

```

