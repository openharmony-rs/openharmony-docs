# addPortAuthorization（系统接口）

## 导入模块

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## addPortAuthorization

```TypeScript
function addPortAuthorization(tokenId: string, deviceId: string): Promise<void>
```

添加应用访问串口端口的权限仅面向串口授权弹窗系统应用开放

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-serial-function addPortAuthorization(tokenId: string, deviceId: string): Promise<void>--><!--Device-serial-function addPortAuthorization(tokenId: string, deviceId: string): Promise<void>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | string | 是 | 被授权应用的tokenId |
| deviceId | string | 是 | 串口设备ID<br>对于板载串口，取值为portName；对于USB虚拟串口，取值为vid+pid+SN拼接。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，无返回结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Called by non-system application |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700002](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700002-参数错误) | Invalid parameter. |
| [35700008](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700008-权限被拒绝) | Permission denied. |

