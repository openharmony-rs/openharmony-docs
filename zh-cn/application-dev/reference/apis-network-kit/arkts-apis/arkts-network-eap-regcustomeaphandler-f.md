# regCustomEapHandler

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## regCustomEapHandler

```TypeScript
function regCustomEapHandler(netType: int, eapCode: int, eapType: int, callback: Callback<EapData>): void
```

用于指定需要定制化处理的EAP报文类型和对应的处理callback。使用callback异步回调。 系统会将符合条件的EAP报文送入callback函数中供企业应用获取。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

<!--Device-eap-function regCustomEapHandler(netType: int, eapCode: int, eapType: int, callback: Callback<EapData>): void--><!--Device-eap-function regCustomEapHandler(netType: int, eapCode: int, eapType: int, callback: Callback<EapData>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netType | int | 是 | 网络类型，取值为1或2。 <br>netType=1表示WLAN，netType=2表示以太网。 |
| eapCode | int | 是 | 需要进行定制的EAP code，取值为1、2、3、4 。 <br>code=1 Request、 code=2 Response、 code=3 Success、 code=4 Failure。 |
| eapType | int | 是 | 需要进行定制处理的EAP method类型，取值范围[0, 255]。 <br>常用取值包括：eapType=1 Identity，eapType=2 Notification，eapType=3 NAK，eapType=4 MD5-Challenge，eapType=5 OTP（One- Time Password），eapType=6 GTC（Generic Token Card），eapType=13 EAP-TLS，eapType=21 EAP-TTLS，eapType=25 EAP-PEAP， eapType=254 Expanded Types，eapType=255 Experimental use。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[EapData](arkts-network-eap-eapdata-i.md)&gt; | 是 | 回调函数，返回指定的eapCode+eapType的报文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33200008](../errorcode-net-eap.md#33200008-无效的eaptype值) | Invalid eap type |
| [33200009](../errorcode-net-eap.md#33200009-netmanager进程不存在) | netmanager stop |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [33200099](../errorcode-net-eap.md#33200099-程序内部错误) | internal error |
| [33200006](../errorcode-net-eap.md#33200006-无效的网络类型) | Invalid net type |
| [33200007](../errorcode-net-eap.md#33200007-无效的eapcode值) | Invalid eap code |

**示例**

```TypeScript
import {eap} from '@kit.NetworkKit';
let netType = 1;
let eapCode = 1;
let eapType = 25;
let eapData = (eapData:eap.EapData):void => {
  console.info("rsp result", JSON.stringify(eapData));
};

eap.regCustomEapHandler(netType, eapCode, eapType, eapData);
console.info('regCustomEapHandler success');
```

