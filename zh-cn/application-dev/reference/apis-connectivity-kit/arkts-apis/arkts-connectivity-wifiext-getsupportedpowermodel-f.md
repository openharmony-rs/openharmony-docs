# getSupportedPowerModel

## 导入模块

```TypeScript
import { wifiext } from '@kit.ConnectivityKit';
```

## getSupportedPowerModel

```TypeScript
function getSupportedPowerModel(): Promise<Array<PowerModel>>
```

获取支持的功率模式。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getSupportedPowerMode](arkts-connectivity-wifimanagerext-getsupportedpowermode-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiext-function getSupportedPowerModel(): Promise<Array<PowerModel>>--><!--Device-wifiext-function getSupportedPowerModel(): Promise<Array<PowerModel>>-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[PowerModel](arkts-connectivity-wifiext-powermodel-e.md)&gt;&gt; | 返回支持的功率模式数组。 |


## getSupportedPowerModel

```TypeScript
function getSupportedPowerModel(callback: AsyncCallback<Array<PowerModel>>): void
```

获取支持的功率模式。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getSupportedPowerMode](arkts-connectivity-wifimanagerext-getsupportedpowermode-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiext-function getSupportedPowerModel(callback: AsyncCallback<Array<PowerModel>>): void--><!--Device-wifiext-function getSupportedPowerModel(callback: AsyncCallback<Array<PowerModel>>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[PowerModel](arkts-connectivity-wifiext-powermodel-e.md)&gt;&gt; | 是 | 回调函数。当操作成功时，err为0，data表示支持的功率模式。如果err为非0，表示处理出现错误。 |

