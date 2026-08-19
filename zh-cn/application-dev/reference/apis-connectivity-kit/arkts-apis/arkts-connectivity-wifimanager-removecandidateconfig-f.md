# removeCandidateConfig

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## removeCandidateConfig

```TypeScript
function removeCandidateConfig(networkId: int): Promise<void>
```

移除指定的候选热点配置，只允许移除自己添加的配置。 应用必须在前台运行。

**起始版本：** 23

**需要权限：** ohos.permission.SET_WIFI_INFO

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-wifiManager-function removeCandidateConfig(networkId: int): Promise<void>--><!--Device-wifiManager-function removeCandidateConfig(networkId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | int | 是 | 将要移除的网络ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回结果。 |

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


## removeCandidateConfig

```TypeScript
function removeCandidateConfig(networkId: int, callback: AsyncCallback<void>): void
```

移除指定的候选热点配置，只允许移除自己添加的配置。 应用必须在前台运行。

**起始版本：** 23

**需要权限：** ohos.permission.SET_WIFI_INFO

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-wifiManager-function removeCandidateConfig(networkId: int, callback: AsyncCallback<void>): void--><!--Device-wifiManager-function removeCandidateConfig(networkId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | int | 是 | 将要移除的网络ID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 表示removeCandidateConfig的回调函数。 |

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
    let networkId = 0;
    wifiManager.removeCandidateConfig(networkId,(error,result) => {
    console.info("result:" + JSON.stringify(result));
    });  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

