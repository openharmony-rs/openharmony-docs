# addDeviceConfig

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addDeviceConfig

```TypeScript
function addDeviceConfig(config: WifiDeviceConfig): Promise<number>
```

添加网络配置。使用Promise异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md) | 是 | Wi-Fi配置信息。如果bssidType无指定值，则bssidType默认为随机设备地址类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。表示网络配置ID。 |

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
    let config:wifiManager.WifiDeviceConfig = {
      ssid : "****",
      preSharedKey : "****",
      securityType : 0
    }
    wifiManager.addDeviceConfig(config).then(result => {
      console.info("result:" + JSON.stringify(result));
    }).catch((err:number) => {
      console.error("failed:" + JSON.stringify(err));
    });
  }catch(error){  
    console.error("failed:" + JSON.stringify(error));
  }
```


<a id="adddeviceconfig-1"></a>

## addDeviceConfig

```TypeScript
function addDeviceConfig(config: WifiDeviceConfig, callback: AsyncCallback<number>): void
```

添加网络配置。使用callback异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md) | 是 | Wi-Fi配置信息。如果bssidType无指定值，则bssidType默认为随机设备地址类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当操作成功时，error为0，data为添加的网络配置ID，如果data值为-1，表示添加失败。当操作错误，error为非0值。 |

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
      let config:wifiManager.WifiDeviceConfig = {
        ssid : "****",
        preSharedKey : "****",
        securityType : 0
      }
      wifiManager.addDeviceConfig(config,(error,result) => {
        console.info("result:" + JSON.stringify(result));
      });
    }catch(error){
      console.error("failed:" + JSON.stringify(error));
    }
```
