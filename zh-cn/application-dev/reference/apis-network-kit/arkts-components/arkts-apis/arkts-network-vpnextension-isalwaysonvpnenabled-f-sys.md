# isAlwaysOnVpnEnabled（系统接口）

## 导入模块

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## isAlwaysOnVpnEnabled

```TypeScript
function isAlwaysOnVpnEnabled(bundleName: string): Promise<boolean>
```

获取always on VPN开关状态。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_VPN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 设置了always on vpn的包名，通常指三方应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示应用alway on vpn开启状态；返回false表示关闭状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
