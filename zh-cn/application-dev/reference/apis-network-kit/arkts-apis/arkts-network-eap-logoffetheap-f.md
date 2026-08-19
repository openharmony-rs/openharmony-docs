# logOffEthEap

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## logOffEthEap

```TypeScript
function logOffEthEap(netId: int): void
```

该接口用于指定一个以太网卡从EAP已认证状态退出。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

<!--Device-eap-function logOffEthEap(netId: int): void--><!--Device-eap-function logOffEthEap(netId: int): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netId | int | 是 | 以太网卡Id。（传入默认参数-1，系统将自动匹配以太网卡发起EAP认证） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33200010](../errorcode-net-eap.md#33200010-无效的eth状态) | invalid eth state |
| [33200009](../errorcode-net-eap.md#33200009-netmanager进程不存在) | netmanager stop |
| [33200002](../errorcode-net-eap.md#33200002-退出指定netid网卡扩展认证失败) | Log off fail |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [33200099](../errorcode-net-eap.md#33200099-程序内部错误) | internal error |
| [33200001](../errorcode-net-eap.md#33200001-无效的netid值) | Invalid netId |

**示例**

```TypeScript
import {eap} from '@kit.NetworkKit';
let netId = 100;    
try{
  eap.logOffEthEap(netId);
  console.info("logOffEthEap success");
} catch (err) {
  console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```

