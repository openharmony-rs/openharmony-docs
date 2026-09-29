# DownloadableProfile

```TypeScript
export interface DownloadableProfile
```

可下载的配置文件。

**起始版本：** 18

<!--Device-eSIM-export interface DownloadableProfile--><!--Device-eSIM-export interface DownloadableProfile-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

## 导入模块

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## accessRules

```TypeScript
accessRules?: Array<AccessRule>
```

访问规则数组。

**类型：** Array&lt;[AccessRule](arkts-telephony-esim-accessrule-i-sys.md)&gt;

**起始版本：** 18

<!--Device-DownloadableProfile-accessRules?: Array<AccessRule>--><!--Device-DownloadableProfile-accessRules?: Array<AccessRule>-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

## activationCode

```TypeScript
activationCode: string
```

激活码。对于不基于激活码的配置文件，可能为空。

**类型：** string

**起始版本：** 18

<!--Device-DownloadableProfile-activationCode: string--><!--Device-DownloadableProfile-activationCode: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

## carrierName

```TypeScript
carrierName?: string
```

订阅名称。

**类型：** string

**起始版本：** 18

<!--Device-DownloadableProfile-carrierName?: string--><!--Device-DownloadableProfile-carrierName?: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

## confirmationCode

```TypeScript
confirmationCode?: string
```

确认码。

**类型：** string

**起始版本：** 18

<!--Device-DownloadableProfile-confirmationCode?: string--><!--Device-DownloadableProfile-confirmationCode?: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim
