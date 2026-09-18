# @ohos.net.networkSecurity(网络安全校验)

本模块提供网络安全校验能力。应用可以通过证书校验API完成证书校验功能。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [certVerification](arkts-network-networksecurity-certverification-f.md) | 系统将使用证书管理中的预置CA证书和用户安装的CA证书来校验应用传入的证书。使用Promise异步回调。 |
| [certVerificationSync](arkts-network-networksecurity-certverificationsync-f.md) | 系统将使用证书管理中的预置CA证书和用户安装的CA证书来校验应用传入的证书，使用同步方式返回。 |
| [isCleartextPermitted](arkts-network-networksecurity-iscleartextpermitted-f.md) | 从应用预置network_config.json文件中获取整体明文HTTP是否允许信息，默认允许明文HTTP访问。 |
| [isCleartextPermittedByHostName](arkts-network-networksecurity-iscleartextpermittedbyhostname-f.md) | 从应用预置network_config.json文件中获取按域名明文HTTP是否允许信息，默认允许明文HTTP访问。 |
| [verifyCertChain](arkts-network-networksecurity-verifycertchain-f.md) | 验证服务器证书链并返回排序后的证书链。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CertBlob](arkts-network-networksecurity-certblob-i.md) | 证书数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CertType](arkts-network-networksecurity-certtype-e.md) | 证书编码类型。 |
