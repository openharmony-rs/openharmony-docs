# createHfpHfProfile

## 导入模块

```TypeScript
import { hfp } from '@kit.ConnectivityKit';
```

## createHfpHfProfile

```TypeScript
function createHfpHfProfile(): HandsFreeHfProfile
```

创建蓝牙通话音频中的HF实例。通过该实例可使用本端作为HF设备的接口，如：获取和其他设备间的蓝牙通话音频连接状态。典型应用场景包括蓝牙耳机的免提通话功能、车载免提系统等，本端设备作为免提（HF）角色接收和处理通话音频。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HandsFreeHfProfile](arkts-connectivity-hfp-handsfreehfprofile-i-sys.md) | 返回HF实例，可用于获取和其他设备间的蓝牙通话音频连接状态等操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
try {
    let hfProfile = hfp.createHfpHfProfile();
    console.info('hf success');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
