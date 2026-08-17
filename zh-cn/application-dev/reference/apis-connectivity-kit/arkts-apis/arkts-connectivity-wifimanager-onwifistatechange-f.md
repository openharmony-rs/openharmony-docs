# onWifiStateChange

## onWifiStateChange

```TypeScript
function onWifiStateChange(callback: Callback<int>): void
```

注册WLAN状态改变事件。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function onWifiStateChange(callback: Callback<int>): void--><!--Device-wifiManager-function onWifiStateChange(callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 是 | 状态改变回调函数。返回0：未激活，1：已激活，2：正在激活，3：正在去激活。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

