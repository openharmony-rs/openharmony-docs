# isFeatureSupported

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## isFeatureSupported

```TypeScript
function isFeatureSupported(featureId: long): boolean
```

检查设备是否支持指定特性。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function isFeatureSupported(featureId: long): boolean--><!--Device-wifiManager-function isFeatureSupported(featureId: long): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | long | 是 | 表示特性的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 此设备支持指定特性时返回{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2401000](../errorcode-wifi.md#2401000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let featureId = 0;
    let ret = wifiManager.isFeatureSupported(featureId);
    console.info("isFeatureSupported:" + ret);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

