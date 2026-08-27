# @ohos.identifier.oaid(开放匿名设备标识服务)

本模块提供开放匿名设备标识符（Open Anonymous Device Identifier, OAID）的获取和重置能力。

> **说明：**
> 
> 使用获取开放匿名设备标识符接口，需[向用户申请授权](../../../security/AccessToken/request-user-authorization.md) &gt;（默认开启权限）：ohos.permission.APP_TRACKING_CONSENT。

**起始版本：** 10

**系统能力：** SystemCapability.Advertising.OAID

## 导入模块

```TypeScript
import { identifier } from '@kit.AdsKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getOAID(开放匿名设备标识服务)](arkts-ads-identifier-getoaid-f.md) | 获取开放匿名设备标识符（OAID）。使用callback异步回调。 |
| [getOAID(开放匿名设备标识服务)](arkts-ads-identifier-getoaid-f.md) | 获取开放匿名设备标识符（OAID）。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [resetOAID(开放匿名设备标识服务)](arkts-ads-identifier-resetoaid-f-sys.md) | 重置开放匿名设备标识符（OAID）。 |
<!--DelEnd-->
