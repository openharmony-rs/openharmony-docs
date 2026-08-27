# deletePersistentGroup（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## deletePersistentGroup

```TypeScript
function deletePersistentGroup(netId: number): boolean
```

删除指定网络ID的持久P2P群组。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deletePersistentP2pGroup

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netId | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作成功时返回{ |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let netId = 0;
    wifi.deletePersistentGroup(netId);    
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
