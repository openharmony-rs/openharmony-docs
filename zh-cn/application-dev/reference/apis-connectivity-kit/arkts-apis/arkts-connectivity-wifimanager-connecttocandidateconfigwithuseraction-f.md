# connectToCandidateConfigWithUserAction

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## connectToCandidateConfigWithUserAction

```TypeScript
function connectToCandidateConfigWithUserAction(networkId: number): Promise<void>
```

该接口用于应用连接到用户添加的候选网络，并在连接时提示用户进行信任确认。使用Promise异步回调。

- 调用此接口时，系统将提示用户确认是否信任并连接到指定的候选网络。  
- 用户确认是连接过程中的必要步骤，未获得用户信任确认前，连接操作不会执行。  
- 建议在发起连接前先通过startScan接口触发一次Wi-Fi扫描，通过[wifiManager.on('wifiScanStateChange')](arkts-connectivity-wifimanager-on-f.md#onwifiscanstatechange)方法监听到扫描结果刷新后再连接，以提高连接成功率。

> **说明：** 
> 
> 调用[wifiManager.connectToCandidateConfig](arkts-connectivity-wifimanager-connecttocandidateconfig-f.md)连接候选网络时，不会返回用户响应结果。

**起始版本：** 20

**需要权限：** ohos.permission.SET_WIFI_INFO

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | number | 是 | 候选网络配置的ID，ID不能小于0。 |

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
