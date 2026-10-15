# DisposedRuleConfiguration (System API)

```TypeScript
export interface DisposedRuleConfiguration
```

Describes the configurations for setting disposed rules in batches.

**Since:** 20

<!--Device-appControl-export interface DisposedRuleConfiguration--><!--Device-appControl-export interface DisposedRuleConfiguration-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## appId

```TypeScript
appId: string
```

appId or appIdentifier of the application for which the disposed rule is to be set. appId and appIdentifier can identify the same application. Therefore, for the same application, if the disposed rule is set using appIdentifier, it can overwrite the rule previously set using appId, and vice versa.

**NOTE:** 

appId is the unique identifier of the application, determined by the application bundle name and signature information. For details about how to obtain it, see [Obtaining the appId of an Application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appid-from-application-information).

[appIdentifier](../../../reference/apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo) is also the unique identifier of the application. For detailed information, see [What Is appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier). For details about how to obtain it, see [Obtaining the appIdentifier of an Application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appidentifier-from-application-information).

**Type:** string

**Since:** 20

<!--Device-DisposedRuleConfiguration-appId: string--><!--Device-DisposedRuleConfiguration-appId: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## appIndex

```TypeScript
appIndex: number
```

Index of the application clone. The default value is **0**.

The value **0** means to set the disposed rule for the main application. A value greater than 0 means to set the disposed rule for the application clone with the specified index.

**Type:** number

**Since:** 20

<!--Device-DisposedRuleConfiguration-appIndex: int--><!--Device-DisposedRuleConfiguration-appIndex: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

## disposedRule

```TypeScript
disposedRule: DisposedRule
```

Disposal rule of the application, including the type of the ability to be started during disposal.

**Type:** [DisposedRule](arkts-ability-appcontrol-disposedrule-i-sys.md)

**Since:** 20

<!--Device-DisposedRuleConfiguration-disposedRule: DisposedRule--><!--Device-DisposedRuleConfiguration-disposedRule: DisposedRule-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.
