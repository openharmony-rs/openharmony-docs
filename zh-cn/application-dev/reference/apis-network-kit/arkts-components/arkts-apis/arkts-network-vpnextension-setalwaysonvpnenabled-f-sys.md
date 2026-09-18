# setAlwaysOnVpnEnabled（系统接口）

## 导入模块

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## setAlwaysOnVpnEnabled

```TypeScript
function setAlwaysOnVpnEnabled(enable: boolean, bundleName: string): Promise<void>
```

设置设备的启用/禁用always on VPN模式。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_VPN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | always on启用或禁用。true：always on启用；false：always on禁用。 |
| bundleName | string | 是 | 设置了always on vpn的包名，是指三方应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回值的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
