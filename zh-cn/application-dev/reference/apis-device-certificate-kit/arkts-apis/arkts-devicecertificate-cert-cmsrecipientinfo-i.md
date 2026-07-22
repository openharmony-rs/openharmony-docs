# CmsRecipientInfo

CMS封装数据的接收者信息。
> **说明：**  
>  
> 至少需要设置一个接收者。

**起始版本：** 22

<!--Device-cert-interface CmsRecipientInfo--><!--Device-cert-interface CmsRecipientInfo-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## keyAgreeInfo

```TypeScript
keyAgreeInfo?: CmsKeyAgreeRecipientInfo
```

keyAgree接收者信息。

**类型：** CmsKeyAgreeRecipientInfo

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CmsRecipientInfo-keyAgreeInfo?: CmsKeyAgreeRecipientInfo--><!--Device-CmsRecipientInfo-keyAgreeInfo?: CmsKeyAgreeRecipientInfo-End-->

**系统能力：** SystemCapability.Security.Cert

## keyTransInfo

```TypeScript
keyTransInfo?: CmsKeyTransRecipientInfo
```

keyTrans接收者信息。

**类型：** CmsKeyTransRecipientInfo

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CmsRecipientInfo-keyTransInfo?: CmsKeyTransRecipientInfo--><!--Device-CmsRecipientInfo-keyTransInfo?: CmsKeyTransRecipientInfo-End-->

**系统能力：** SystemCapability.Security.Cert

