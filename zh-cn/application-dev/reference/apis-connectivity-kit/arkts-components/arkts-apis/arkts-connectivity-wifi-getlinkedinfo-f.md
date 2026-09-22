# getLinkedInfo

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getLinkedInfo

```TypeScript
function getLinkedInfo(): Promise<WifiLinkedInfo>
```

获取Wi-Fi连接信息。使用Promise异步回调。

> **说明：** 
> 
> 从API version 6开始支持，从API version 9开始废弃。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i.md)&gt; | Promise对象。表示Wi-Fi连接信息。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

wifi.getLinkedInfo((err, data:wifi.WifiLinkedInfo) => {
    if (err) {
        console.error("get linked info error");
        return;
    }
    console.info("get wifi linked info: " + JSON.stringify(data));
});

wifi.getLinkedInfo().then(data => {
    console.info("get wifi linked info: " + JSON.stringify(data));
}).catch((error:number) => {
    console.info("get linked info error");
});
```


<a id="getlinkedinfo-1"></a>

## getLinkedInfo

```TypeScript
function getLinkedInfo(callback: AsyncCallback<WifiLinkedInfo>): void
```

获取Wi-Fi连接信息。使用callback异步回调。

> **说明：** 
> 
> 从API version 6开始支持，从API version 9开始废弃。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i.md)&gt; | 是 | 回调函数。当获取成功时，err为0，data表示Wi-Fi连接信息。如果err为非0，表示处理出现错误。 |

**示例**

参见 [getLinkedInfo](#getlinkedinfo)
