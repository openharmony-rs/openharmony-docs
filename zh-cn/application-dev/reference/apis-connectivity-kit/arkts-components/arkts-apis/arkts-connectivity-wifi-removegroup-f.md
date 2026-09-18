# removeGroup

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## removeGroup

```TypeScript
function removeGroup(): boolean
```

移除群组。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** removeP2pGroup

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:操作执行成功， false:操作执行失败。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
  wifi.removeGroup();  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
