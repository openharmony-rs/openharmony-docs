# connectToCandidateConfigWithUserAction

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## connectToCandidateConfigWithUserAction

```TypeScript
function connectToCandidateConfigWithUserAction(networkId: int): Promise<void>
```

通过networkId连接到指定的候选热点，并等待用户响应结果。 只允许连接自己添加的配置。此方法一次连接一个配置。 应用必须在前台运行。

**起始版本：** 23

**需要权限：** ohos.permission.SET_WIFI_INFO

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-wifiManager-function connectToCandidateConfigWithUserAction(networkId: int): Promise<void>--><!--Device-wifiManager-function connectToCandidateConfigWithUserAction(networkId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | int | 是 | 将要连接的网络ID。networkId的值不能小于0。 |

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
    let networkId = 0; // 候选网络ID，在添加候选网络时生成
    wifiManager.connectToCandidateConfigWithUserAction(networkId).then(result => {
      console.info("result:" + JSON.stringify(result));
    }).catch((err:number) => {
      console.error("failed:" + JSON.stringify(err));
    });
  }catch(error){  
    console.error("failed:" + JSON.stringify(error));
  }
```

