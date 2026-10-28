# setLocalHotaDomain

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## setLocalHotaDomain

```TypeScript
function setLocalHotaDomain(domain: string): void
```

设置设备的本地HOTA域。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-systemManager-function setLocalHotaDomain(domain: string): void--><!--Device-systemManager-function setLocalHotaDomain(domain: string): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domain | string | 是 | 要设置的本地HOTA域。取值必须符合域名规则。校验规则如下：1.长度不能超过64个字符。2.不支持IP地址和localhost。3.域需要完整的请求根地址，必须以https://开头。4.域必须匹配以下正则表达式：`^(?:[a-zA-Z0-9](?:[a-zA-Z0-9.-]*[a-zA-Z0-9])?\.)+[a-zA-Z]{2,}$` 5.传递空字符串意味着将域恢复为其默认值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| [9200018](../errorcode-enterpriseDeviceManager.md#9200018-该设备非企业设备) | This device is not an enterprise device. |

**示例**

```TypeScript
import { common, systemManager } from '@kit.MDMKit';

// 需根据实际情况进行替换
let domain: string = "https://www.hotaExample.com";
// 调用本接口前，先查询设备是否支持本机HOTA域名特性
let isSupported: boolean = common.isFeatureSupported(common.ManagedFeature.LOCAL_HOTA_DOMAIN);
if (isSupported) {
  try {
    systemManager.setLocalHotaDomain(domain);
    console.info('Succeeded in setting local HOTA domain.');
  } catch (err) {
    console.error(`Failed to set local HOTA domain. Code is ${err.code}, message is ${err.message}`);
  }
} else {
  console.info('The local HOTA domain feature is not supported.');
}
```
