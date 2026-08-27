# offDeviceFound

## 导入模块

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## offDeviceFound

```TypeScript
function offDeviceFound(callback?: Callback<ScanResults[]>): void
```

取消订阅星闪扫描结果。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScanResults](arkts-connectivity-scan-scanresults-i.md)[]&gt; | 否 | 回调函数，返回星闪扫描结果数组对象。 填写该参数则取消当前callback订阅。不填写该参数则取消该事件对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
