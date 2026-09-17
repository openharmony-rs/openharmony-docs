# reassociate（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## reassociate

```TypeScript
function reassociate(): boolean
```

重新关联网络。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [reassociate](arkts-connectivity-wifimanager-reassociate-f-sys.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:操作成功， false:操作失败。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    wifi.reassociate();
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
