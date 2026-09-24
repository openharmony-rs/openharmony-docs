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

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceType | [StandbyResourceType](arkts-mdm-applicationmanager-standbyresourcetype-e.md) | 是 | 资源类型。 |
| bundleName | string | 是 | 要为其释放资源豁免的应用包名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| [9201002](../errorcode-enterpriseDeviceManager.md#9201002-企业应用安装失败) | The application is not installed. |
