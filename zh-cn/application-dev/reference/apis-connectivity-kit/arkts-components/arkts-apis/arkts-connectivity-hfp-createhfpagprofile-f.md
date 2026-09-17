# createHfpAgProfile

## 导入模块

```TypeScript
import { hfp } from '@kit.ConnectivityKit';
```

## createHfpAgProfile

```TypeScript
function createHfpAgProfile(): HandsFreeAudioGatewayProfile
```

创建蓝牙通话音频中的HFP AG实例。通过该实例可使用本端作为HFP AG设备的接口，如：获取和其他设备间的蓝牙通话音频连接状态。典型应用场景包括车载信息娱乐系统的蓝牙通话功能、平板电脑蓝牙通话等，本端设备作为音频网关（AG）角色管理通话音频路由。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HandsFreeAudioGatewayProfile | 返回HFP AG实例，可用于获取和其他设备间的蓝牙通话音频连接状态等操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let hfpAgProfile = hfp.createHfpAgProfile();
    console.info('hfpAg success');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
