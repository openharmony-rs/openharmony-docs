# getSupportedPowerMode

## 导入模块

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getSupportedPowerMode

```TypeScript
function getSupportedPowerMode(): Promise<Array<PowerMode>>
```

获取支持的功率模式。

**起始版本：** 9

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[PowerMode](arkts-connectivity-wifimanagerext-powermode-e.md)&gt;&gt; | 返回支持的功率模式列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2701000](../errorcode-wifi.md#2701000-ap扩展模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';

wifiManagerExt.getSupportedPowerMode((err, data: wifiManagerExt.PowerMode[]) => {
    if (err) {
        console.error("get supported power mode info error: ", err);
        return;
    }
    console.info("get supported power mode info: " + JSON.stringify(data));
});
```


## getSupportedPowerMode

```TypeScript
function getSupportedPowerMode(callback: AsyncCallback<Array<PowerMode>>): void
```

获取支持的功率模式。

**起始版本：** 9

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[PowerMode](arkts-connectivity-wifimanagerext-powermode-e.md)&gt;&gt; | 是 | 回调函数。当操作成功时，err为0，data表示支持的功率模式。如果err为非0，表示处理出现错误。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2701000](../errorcode-wifi.md#2701000-ap扩展模块异常) | Operation failed. |

**示例**

参见 [getSupportedPowerMode](#getsupportedpowermode)
