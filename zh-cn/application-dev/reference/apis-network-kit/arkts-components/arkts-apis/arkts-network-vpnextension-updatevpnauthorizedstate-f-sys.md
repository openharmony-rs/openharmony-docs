# updateVpnAuthorizedState（系统接口）

## 导入模块

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## updateVpnAuthorizedState

```TypeScript
function updateVpnAuthorizedState(bundleName: string): boolean
```

更新VPN对话框授权信息。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_VPN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用弹框授权的包名，通常指三方应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回值用来判断是否成功更新vpn弹框授权状态。true：成功更新vpn弹框授权状态；false：没有成功更新vpn弹框授权状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
