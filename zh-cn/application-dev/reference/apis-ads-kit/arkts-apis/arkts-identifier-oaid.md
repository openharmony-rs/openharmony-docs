# @ohos.identifier.oaid

本模块提供开放匿名设备标识符（Open Anonymous Device Identifier, OAID）的获取和重置能力。

> **说明：**  
>  
> 使用获取开放匿名设备标识符接口，需[向用户申请授权](../../../security/AccessToken/request-user-authorization.md)  
>（默认开启权限）：ohos.permission.APP_TRACKING_CONSENT。

**起始版本：** 10

<!--Device-unnamed-declare namespace identifier--><!--Device-unnamed-declare namespace identifier-End-->

**系统能力：** SystemCapability.Advertising.OAID

## 导入模块

```TypeScript
import { identifier } from '@kit.AdsKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getOAID](arkts-ads-identifier-getoaid-f.md#getoaid-1) | 获取开放匿名设备标识符（OAID）。使用callback异步回调。 |
| [getOAID](arkts-ads-identifier-getoaid-f.md#getoaid-2) | 获取开放匿名设备标识符（OAID）。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [resetOAID](arkts-ads-identifier-resetoaid-f-sys.md#resetoaid-1) | 重置开放匿名设备标识符（OAID）。 |
<!--DelEnd-->

