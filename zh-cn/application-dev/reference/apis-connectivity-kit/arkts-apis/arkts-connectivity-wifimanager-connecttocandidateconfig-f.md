# connectToCandidateConfig

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## connectToCandidateConfig

```TypeScript
function connectToCandidateConfig(networkId: int): void
```

通过networkId连接到指定的候选热点，只允许连接自己添加的配置。此方法一次连接一个配置。 应用必须在前台运行。

**起始版本：** 23

**需要权限：** ohos.permission.SET_WIFI_INFO

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-wifiManager-function connectToCandidateConfig(networkId: int): void--><!--Device-wifiManager-function connectToCandidateConfig(networkId: int): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | int | 是 | 将要连接的网络ID。networkId的值不能小于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
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


## connectToCandidateConfig

```TypeScript
function connectToCandidateConfig(settings: ConnectSettings): Promise<void>
```

使用连接设置连接到指定的候选热点。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.SET_WIFI_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-wifiManager-function connectToCandidateConfig(settings: ConnectSettings): Promise<void>--><!--Device-wifiManager-function connectToCandidateConfig(settings: ConnectSettings): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| settings | [ConnectSettings](arkts-connectivity-wifimanager-connectsettings-i.md) | 是 | 表示连接设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回用于返回操作结果的Promise对象。 如果操作失败，返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2501006](../errorcode-wifi.md#2501006-用户拒绝连接请求) | The user refused the action. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501007](../errorcode-wifi.md#2501007-参数校验失败) | Parameter validation failed. |
| [2501005](../errorcode-wifi.md#2501005-用户未响应连接请求) | The user does not respond. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta功能未打开) | Wi-Fi STA disabled. |

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

