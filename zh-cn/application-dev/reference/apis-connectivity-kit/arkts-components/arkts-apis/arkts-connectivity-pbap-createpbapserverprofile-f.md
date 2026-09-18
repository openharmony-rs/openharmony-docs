# createPbapServerProfile

## 导入模块

```TypeScript
import { pbap } from '@kit.ConnectivityKit';
```

## createPbapServerProfile

```TypeScript
function createPbapServerProfile(): PbapServerProfile
```

创建蓝牙电话簿访问协议中的PSE实例。通过该实例可使用本端作为PSE设备的接口，如：获取本端和其他设备间的蓝牙电话簿服务连接状态。典型使用场景包括：车载蓝牙系统访问手机电话簿、跨设备联系人同步等需要本端作为电话簿服务端的场景。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PbapServerProfile](arkts-connectivity-pbap-pbapserverprofile-i-sys.md) | 返回PSE实例。该类继承于[BaseProfile](arkts-connectivity-pbap-baseprofile-t.md)，因此可以使用其父类中的方法。和该实例角色相对应的是PCE角色。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let pbapServerProfile = pbap.createPbapServerProfile();
    console.info('pbapServer success');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
