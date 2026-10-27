# releaseExemptionResource

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## releaseExemptionResource

```TypeScript
function releaseExemptionResource(resourceType: StandbyResourceType, bundleName: string): void
```

释放指定应用的备用资源豁免。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function releaseExemptionResource(resourceType: StandbyResourceType, bundleName: string): void--><!--Device-applicationManager-function releaseExemptionResource(resourceType: StandbyResourceType, bundleName: string): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceType | [StandbyResourceType](arkts-mdm-applicationmanager-standbyresourcetype-e.md) | 是 | 资源类型。 |
| bundleName | string | 是 | 要为其释放资源豁免的应用包名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| [9201002](../errorcode-enterpriseDeviceManager.md#9201002-企业应用安装失败) | The application is not installed. |

**示例**

```TypeScript
import { applicationManager, systemManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 需根据实际情况进行替换
let bundleName: string = 'com.example.test';
let timerId: number = 1;

// 停止并销毁精确定时器，避免资源泄漏
systemManager.stopExactTimer(timerId).then(() => {
  console.info('Succeeded in stopping exact timer.');
  return systemManager.destroyExactTimer(timerId);
}).then(() => {
  console.info('Succeeded in destroying exact timer.');
  // 释放网络豁免
  try {
    applicationManager.releaseExemptionResource(applicationManager.StandbyResourceType.NETWORK, bundleName);
    console.info('Succeeded in releasing exemption resource.');
  } catch (err) {
    console.error(`Failed to release exemption resource. Code is ${err.code}, message is ${err.message}`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to stop or destroy exact timer. Code: ${err.code}, message: ${err.message}`);
});
```
