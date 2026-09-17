# getVirtualAddressByHash

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## getVirtualAddressByHash

```TypeScript
function getVirtualAddressByHash(algorithmType: HashAlgorithmType, hashValue: string): string
```

根据已配对设备实际MAC地址的哈希值获取对应的虚拟MAC地址。

当[HashAlgorithmType](arkts-connectivity-connection-hashalgorithmtype-e.md)为HASH_ALGORITHM_SHA256时，应使用大写实际MAC地址通过SHA256算法生成对应的哈希值（十六进制64位），取后32位作为输入，哈希值字母不区分大小写。

**起始版本：** 24

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algorithmType | [HashAlgorithmType](arkts-connectivity-connection-hashalgorithmtype-e.md) | 是 | 哈希算法类型。 |
| hashValue | string | 是 | 哈希值，例如："c10b57deb2e1aafd255596e0d4fd6789"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回与哈希值相对应的设备虚拟MAC地址，例如："XX:XX:XX:XX:XX:XX"，返回地址为大写。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API when the short-range chip is not inserted on 2in1 device. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900015](../errorcode-bluetoothManager.md#2900015-参数格式与规范不一致) | Parameter format mismatch with specification. |
| [2900016](../errorcode-bluetoothManager.md#2900016-设备未配对) | Device unpaired. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Internal system error. For example, IPC error. Detailed error messages can be used to assist in locating the problem. |

**示例**

```TypeScript
// 若查询的真实地址为11:22:33:44:55:AA,
// 对应的64位哈希值为 d2204cb9b6d3d3962cc90fa54130efb4c10b57deb2e1aafd255596e0d4fd6789,
// 当HashAlgorithmType为HASH_ALGORITHM_SHA256时取后32位哈希值
let hashValue: string = "c10b57deb2e1aafd255596e0d4fd6789";
try {
  let addr: string = connection.getVirtualAddressByHash(connection.HashAlgorithmType.HASH_ALGORITHM_SHA256, hashValue);
} catch (err) {
  console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
