# getSupportedPowerModel

## 导入模块

```TypeScript
import { wifiext } from '@kit.ConnectivityKit';
```

## getSupportedPowerModel

```TypeScript
function getSupportedPowerModel(): Promise<Array<PowerModel>>
```

获取支持的功率模式。使用Promise异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getSupportedPowerMode](arkts-connectivity-wifimanagerext-getsupportedpowermode-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[PowerModel](arkts-connectivity-wifiext-powermodel-e.md)&gt;&gt; | Promise对象。表示功率模式。 |


<a id="getsupportedpowermodel-1"></a>

## getSupportedPowerModel

```TypeScript
function getSupportedPowerModel(callback: AsyncCallback<Array<PowerModel>>): void
```

获取支持的功率模式。使用callback异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getSupportedPowerMode](arkts-connectivity-wifimanagerext-getsupportedpowermode-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[PowerModel](arkts-connectivity-wifiext-powermodel-e.md)&gt;&gt; | 是 | 回调函数。当操作成功时，err为0，data表示支持的功率模式。如果err为非0，表示处理出现错误。 |
