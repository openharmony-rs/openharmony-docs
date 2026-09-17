# createPanProfile

## 导入模块

```TypeScript
import { pan } from '@kit.ConnectivityKit';
```

## createPanProfile

```TypeScript
function createPanProfile(): PanProfile
```

创建蓝牙PAN实例。通过该实例可使用本端作为NAP设备和PANU设备的接口，如：获取和其他设备间的蓝牙个人局域网服务连接状态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanProfile](arkts-connectivity-pan-panprofile-i.md) | 返回PAN实例。该类继承于[BaseProfile](arkts-connectivity-pan-baseprofile-t.md)，因此可以使用其父类中的方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
try {
    let panProfile : pan.PanProfile= pan.createPanProfile();
    console.info('pan success');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
