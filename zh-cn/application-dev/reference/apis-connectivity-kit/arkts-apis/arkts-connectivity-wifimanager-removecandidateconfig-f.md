# removeCandidateConfig

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## removeCandidateConfig

```TypeScript
function removeCandidateConfig(networkId: number): Promise<void>
```

移除候选网络配置，使用Promise异步回调。

- 从系统中删除指定网络ID的Wi-Fi候选配置，清理不再需要的Wi-Fi候选配置，释放系统资源。  
- 只能移除通过[addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md)添加的候选配置，移除后该候选网络将不再被系统自动连接。

**起始版本：** 9

**需要权限：** ohos.permission.SET_WIFI_INFO

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | number | 是 | 网络配置ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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
    let networkId = 0;
    wifiManager.removeCandidateConfig(networkId).then(result => {
      console.info("result:" + JSON.stringify(result));
    }).catch((err:number) => {
      console.error("failed:" + JSON.stringify(err));
    });
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```


<a id="removecandidateconfig-1"></a>

## removeCandidateConfig

```TypeScript
function removeCandidateConfig(networkId: number, callback: AsyncCallback<void>): void
```

移除指定的候选网络配置，使用callback异步回调。

- 从系统中删除指定网络ID的Wi-Fi候选配置，清理不再需要的Wi-Fi候选配置，释放系统资源。  
- 只能移除通过[addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md)添加的候选配置，移除后该候选网络将不再被系统自动连接。

**起始版本：** 9

**需要权限：** ohos.permission.SET_WIFI_INFO

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | number | 是 | 网络配置ID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当操作成功时，error为0。如果error为非0，表示处理出现错误。 |

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
    let networkId = 0;
    wifiManager.removeCandidateConfig(networkId,(error,result) => {
    console.info("result:" + JSON.stringify(result));
    });  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
