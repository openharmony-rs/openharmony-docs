# getCurrentGroup

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getCurrentGroup

```TypeScript
function getCurrentGroup(): Promise<WifiP2pGroupInfo>
```

获取P2P当前组信息。使用Promise异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[WifiP2pGroupInfo](arkts-connectivity-wifi-wifip2pgroupinfo-i.md)&gt; | Promise对象。表示当前组信息。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

wifi.getCurrentGroup((err, data:wifi.WifiP2pGroupInfo) => {
   if (err) {
       console.error("get current P2P group error");
       return;
   }
  console.info("get current P2P group: " + JSON.stringify(data));
});

wifi.getCurrentGroup().then(data => {
  console.info("get current P2P group: " + JSON.stringify(data));
});
```


## getCurrentGroup

```TypeScript
function getCurrentGroup(callback: AsyncCallback<WifiP2pGroupInfo>): void
```

获取P2P当前组信息。使用callback异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WifiP2pGroupInfo](arkts-connectivity-wifi-wifip2pgroupinfo-i.md)&gt; | 是 | 回调函数。当操作成功时，err为0，data表示当前组信息。如果err为非0，表示处理出现错误。 |

**示例**

参见 [getCurrentGroup](#getcurrentgroup)
