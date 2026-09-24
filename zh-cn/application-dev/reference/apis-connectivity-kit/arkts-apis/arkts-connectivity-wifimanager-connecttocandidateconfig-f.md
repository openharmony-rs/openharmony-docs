# connectToCandidateConfig

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## connectToCandidateConfig

```TypeScript
function connectToCandidateConfig(networkId: number): void
```

应用使用该接口连接到自己添加的候选网络。

**起始版本：** 9

**需要权限：** ohos.permission.SET_WIFI_INFO

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | number | 是 | 候选网络配置的ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let networkId = 0; // 候选网络ID，在添加候选网络时生成
    wifiManager.connectToCandidateConfig(networkId);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```


<a id="connecttocandidateconfig-1"></a>

## connectToCandidateConfig

```TypeScript
function connectToCandidateConfig(settings: ConnectSettings): Promise<void>
```

应用使用该接口连接到自己添加的候选网络，支持设置自定义参数。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.SET_WIFI_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| settings | [ConnectSettings](arkts-connectivity-wifimanager-connectsettings-i.md) | 是 | 连接Wi-Fi设置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta功能未打开) | Wi-Fi STA disabled. |
| [2501005](../errorcode-wifi.md#2501005-用户未响应连接请求) | The user does not respond. |
| [2501006](../errorcode-wifi.md#2501006-用户拒绝连接请求) | The user refused the action. |
| [2501007](../errorcode-wifi.md#2501007-参数校验失败) | Parameter validation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let setting:wifiManager.ConnectSettings = { networkId: 0 }; // 候选网络ID，在添加候选网络时生成
    wifiManager.connectToCandidateConfig(setting);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
