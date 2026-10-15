# removeAllowedPrinterIPAddressesForAccount

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## removeAllowedPrinterIPAddressesForAccount

```TypeScript
function removeAllowedPrinterIPAddressesForAccount(ipAddresses: Array<string>): void
```

从用户级白名单中移除打印机IP地址

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-systemManager-function removeAllowedPrinterIPAddressesForAccount(ipAddresses: Array<string>): void--><!--Device-systemManager-function removeAllowedPrinterIPAddressesForAccount(ipAddresses: Array<string>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ipAddresses | Array&lt;string&gt; | 是 | 打印机IP地址。Each IP address must be in IPv4 format or IPV6 format. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |

**示例**

```TypeScript
import { common, systemManager } from '@kit.MDMKit';

// 需要根据实际情况替换
const ipArray: Array<string> = ['192.1.1.1', '2001:0db8:0000:0000:0000:0000:1428:57ab'];
// 调用本接口前，先查询设备是否支持打印机IP地址策略特性
let isSupported: boolean = common.isFeatureSupported(common.ManagedFeature.PRINTER_IP_ADDRESS_POLICY);
if (isSupported) {
  try {
    systemManager.removeAllowedPrinterIPAddressesForAccount(ipArray);
    console.info('Succeeded in removing the allowed printer IP Addresses for current user.');
  } catch (err) {
    console.error(`Failed to remove the allowed printer IP Addresses for current user. Code is ${err.code}, message is ${err.message}`);
  }
} else {
  console.info('The printer IP address policy feature is not supported.');
}
```
