# getPowerModel

## 导入模块

```TypeScript
import { wifiext } from '@kit.ConnectivityKit';
```

## getPowerModel

```TypeScript
function getPowerModel(): Promise<PowerModel>
```

获取功率模式。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getPowerMode](arkts-connectivity-wifimanagerext-getpowermode-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PowerModel](arkts-connectivity-wifiext-powermodel-e.md)&gt; | 返回当前的WLAN功率模式。返回值小于零表示失败。 |


## getPowerModel

```TypeScript
function getPowerModel(callback: AsyncCallback<PowerModel>): void
```

获取功率模式。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getPowerMode](arkts-connectivity-wifimanagerext-getpowermode-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PowerModel](arkts-connectivity-wifiext-powermodel-e.md)&gt; | 是 | 回调函数。当操作成功时，err为0，data表示功率模式。如果err为非0，表示处理出现错误。 |
