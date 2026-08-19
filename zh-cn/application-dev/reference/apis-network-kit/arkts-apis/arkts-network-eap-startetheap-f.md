# startEthEap

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## startEthEap

```TypeScript
function startEthEap(netId: int, profile: EthEapProfile): void
```

该接口用于指定一个以太网卡发起EAP认证。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

<!--Device-eap-function startEthEap(netId: int, profile: EthEapProfile): void--><!--Device-eap-function startEthEap(netId: int, profile: EthEapProfile): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netId | int | 是 | 以太网卡Id。（传入默认参数-1，系统将自动匹配以太网卡发起EAP认证） |
| profile | [EthEapProfile](arkts-network-eap-etheapprofile-i.md) | 是 | EAP配置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33200010](../errorcode-net-eap.md#33200010-无效的eth状态) | invalid eth state |
| [33200009](../errorcode-net-eap.md#33200009-netmanager进程不存在) | netmanager stop |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [33200003](../errorcode-net-eap.md#33200003-无效的eth-eap配置) | Invalid profile |
| [33200099](../errorcode-net-eap.md#33200099-程序内部错误) | internal error |
| [33200001](../errorcode-net-eap.md#33200001-无效的netid值) | Invalid netId |

**示例**

```TypeScript
import {eap} from '@kit.NetworkKit';
let netId = 100;
let profile: eap.EthEapProfile = {
  eapMethod: eap.EapMethod.EAP_TTLS,
  phase2Method: eap.Phase2Method.PHASE2_AKA_PRIME,
  identity: "identity",
  anonymousIdentity: "anonymousIdentity",
  password: "password",
  caCertAliases: "caCertAliases",
  caPath: "caPath",
  clientCertAliases: "clientCertAliases",
  certEntry: new Uint8Array([5,6,7,8,9,10]),
  certPassword: "certPassword",
  altSubjectMatch: "altSubjectMatch",
  domainSuffixMatch: "domainSuffixMatch",
  realm: "realm",
  plmn: "plmn",
  eapSubId: 1
};
    
try {
  eap.startEthEap(netId, profile);
  console.info('startEthEap success');
} catch (err) {
  console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```

