# getPoliciesSync

## 导入模块

```TypeScript
import { browser } from '@kit.MDMKit';
```

## getPoliciesSync

```TypeScript
function getPoliciesSync(admin: Want, appId: string): string
```

通过appid获取指定浏览器设置的策略。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-browser-function getPoliciesSync(admin: Want, appId: string): string--><!--Device-browser-function getPoliciesSync(admin: Want, appId: string): string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| appId | string | 是 | 应用ID，用于指定浏览器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 浏览器策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

