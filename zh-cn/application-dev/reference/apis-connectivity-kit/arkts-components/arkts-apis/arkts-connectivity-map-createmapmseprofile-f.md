# createMapMseProfile

## 导入模块

```TypeScript
import { map } from '@kit.ConnectivityKit';
```

## createMapMseProfile

```TypeScript
function createMapMseProfile(): MapMseProfile
```

创建蓝牙消息访问协议中的MSE实例。通过该实例可使用本端作为MSE设备时提供的接口，如：获取和其他设备间的蓝牙消息服务连接状态。适用于蓝牙消息同步、车载蓝牙消息查看等场景。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MapMseProfile](arkts-connectivity-map-mapmseprofile-i-sys.md) | 返回MapMseProfile实例，该实例可用于本端作为MSE设备进行蓝牙消息访问相关操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let mapMseProfile = map.createMapMseProfile();
    console.info('MapMse success');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
