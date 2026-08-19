# onStreamChange（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## onStreamChange

```TypeScript
function onStreamChange(callback: Callback<int>): void
```

注册WLAN流量改变事件。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_WIFI_CONNECTION

<!--Device-wifiManager-function onStreamChange(callback: Callback<int>): void--><!--Device-wifiManager-function onStreamChange(callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 是 | 状态改变回调函数。返回1：下行流量，2：上行流量，3：双向流量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

