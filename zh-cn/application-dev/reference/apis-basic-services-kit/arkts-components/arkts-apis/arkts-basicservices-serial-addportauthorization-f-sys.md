# addPortAuthorization（系统接口）

## 导入模块

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## addPortAuthorization

```TypeScript
function addPortAuthorization(tokenId: string, deviceId: string): Promise<void>
```

添加应用访问串口的权限。此函数通过将应用的Token ID与串口设备ID关联，建立应用的串口访问权限关系。适用于系统管理类应用为第三方应用授予串口访问权限的场景，如设备管理工具为工业数据采集应用分配串口权限。仅用于会弹出串口授权弹窗的系统应用，在用户授权后，权限信息将持久化存储。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | string | 是 | 被授权应用的Token ID，用于标识被授予串口访问权限的应用。设置后，指定该应用可获得对相应串口设备的访问权限。可通过[bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md)获取。 |
| deviceId | string | 是 | 串口设备ID，用于指定需要授权访问的串口设备。可通过接口[getSerialPortList](arkts-basicservices-serial-getserialportlist-f.md)获取串口设备列表。板载串口取值为portName；USB虚拟串口取值为VID+PID+SN的组合或设备路径（如/dev/ttyUSB0）。设置后，应用将获得对指定串口设备的访问权限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Called by non-system application |
| [35700001](../errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700002](../errorcode-busmanager-serial.md#35700002-参数错误) | Invalid parameter. |
| [35700008](../errorcode-busmanager-serial.md#35700008-权限被拒绝) | Permission denied. |

**示例**

```TypeScript
import {BusinessError} from '@kit.BasicServicesKit';
// 添加串口访问权限
// Token ID 需要通过bundleManager.getBundleInfoForSelf接口获取，此处仅为示例占位符
let tokenId: string = '123456';
let deviceId: string = '/dev/ttyUSB0';
serial.addPortAuthorization(tokenId, deviceId).then(() => {
  console.info('addPortAuthorization success');
}).catch((error: BusinessError) => {
  console.error(`Failed to addPortAuthorization. Code: ${error.code}, message: ${error.message}`);
});
```
