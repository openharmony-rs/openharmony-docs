# Want

Want is a carrier for information transfer between objects (application components). A typical scenario is when a UIAbility (for example, UIAbility A) needs to launch another UIAbility (for example, UIAbility B) and pass some data along. In this case, a Want can be used as the medium. For example, in the **want** parameter of the **startAbility** API, you can specify the target ability using the **abilityName** field or include additional data via the **parameters** field.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## Modules to Import

```TypeScript
import { Want } from '@kit.AbilityKit';
```

## abilityName

```TypeScript
abilityName?: string
```

Ability name of the application. It represents the ability name of the target application in the application launch scenario. If both **bundleName** and **abilityName** are specified in a Want object, the Want object can match a specific ability. The value of **abilityName** must be unique in an application.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## action

```TypeScript
action?: string
```

Action to take, such as viewing and sharing application details. In implicit Want, you can define this field and use it together with **uri** or **parameters** to specify the operation to be performed on the data. For details about the definition and matching rules of implicit Want, see [Matching Rules of Explicit Want and Implicit Want](../../../application-models/explicit-implicit-want-mappings.md).

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## bundleName

```TypeScript
bundleName?: string
```

Bundle name of the application. It represents the bundle name of the target application in the application launch scenario.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## deviceId

```TypeScript
deviceId?: string
```

Device ID. It indicates the device ID of the target application in the application launch scenario. If not specified, it defaults to the current device.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## entities

```TypeScript
entities?: Array<string>
```

Additional category information (such as browser and video player) of the ability. It is a supplement to the **action** field for implicit Want. and is used to filter ability types.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## fds

```TypeScript
readonly fds?: Record<string, number>
```

File descriptor (FD). The FD written by the launcher in the application launch scenario is set to this parameter.

This API can be used in atomic services since API version 15.

**Type:** Record&lt;string, number&gt;

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Ability.AbilityBase

## flags

```TypeScript
flags?: number
```

How the Want object will be handled. The value is of the enumeration type [Flags](arkts-ability-wantconstant-flags-e.md). A numeric value should be passed by default.

For example, if the value is 0x00000001 (**wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION**), the receiver is temporarily granted the permission to read the data pointed to by the URI.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## moduleName

```TypeScript
moduleName?: string
```

Module name of the application. It represents the module name of the target application in the application launch scenario.

**NOTE:** 

If the ability belongs to a [HAR](../../../quick-start/har-package.md) module, **moduleName** must be set to the name of the [HAP](../../../quick-start/hap-package.md) or [HSP](../../../quick-start/in-app-hsp.md) module that depends on this HAR.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## parameters

```TypeScript
parameters?: Record<string, Object>
```

List of parameters in the Want object.

1. The values of the following keys are assigned by the system. Manual settings do not take effect, since the
system automatically changes the values to the actual values during data transfer.

- **ohos.aafwk.param.callerPid**: PID of the caller. The value is a string.  
- **ohos.aafwk.param.callerBundleName**: bundle name of the caller. The value is a string.  
- **ohos.aafwk.param.callerAbilityName**: ability name of the caller. The value is a string.  
- **ohos.aafwk.param.callerNativeName**: process name of the caller when the native method is called. The value is  
a string.  
- **ohos.aafwk.param.callerAppId**: appId of the caller. The value is a string.  
- **ohos.aafwk.param.callerAppIdentifier**: appIdentifier of the caller. The value is a string.  
- **ohos.aafwk.param.callerToken**: token of the caller. The value is a string.  
- **ohos.aafwk.param.callerUid**: UID in [BundleInfo](arkts-ability-bundleinfo-i.md), that is,  
the application's UID in the bundle information. The value is a number.  
- **ohos.param.callerAppCloneIndex**: clone index of the caller. The value is of the numeric type.  
- **component.startup.newRules**: enabled status of the new control rule. The value is of the Boolean type.  
- **moduleName**: module name of the caller. The value is a string.  
- **ohos.ability.params.abilityRecoveryRestart**: support for ability restart upon fault recovery. The value is of  
the Boolean type.  
- **ohos.extra.param.key.showMode**: mode to show the atomic service startup. The value is an enumerated value of wantConstant.ShowMode.

**NOTE:** 

In cross-device scenarios, the following fields do not take effect and cannot be used for identity or permission verification: **ohos.aafwk.param.callerPid**, **ohos.aafwk.param.callerToken**, and **ohos.aafwk.param.callerUid**.

2. Certain keys are defined by the system, and their values need to be manually assigned. For details about the
keys and their values, see wantConstant.Params.
3. In addition to the foregoing cases, applications may further agree on the key-value pairs to transfer.

**NOTE:** 

For details about the constants of **Params** in **want**, see [wantConstant](arkts-ability-app-ability-wantconstant.md).

Note that a maximum of 100 KB data that can be transferred by using **WantParams**. If the data volume exceeds 100 KB, transfer data in WriteRawDataBuffer or [uri](../../apis-arkts/arkts-apis/arkts-arkts-uri.md) mode.

The values of **parameters** must be of the following basic data types: String, Number, Boolean, Object, undefined, and null. Functions in an object cannot be transferred.

**Type:** Record&lt;string, Object&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## type

```TypeScript
type?: string
```

MIME type, that is, the type of the file to open, for example, **'text/xml'** and **'image/*'**. For details about the MIME type definition, see [Media Types](https://www.iana.org/assignments/media-types/media-types.xhtml?utm_source=ld246.com).

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## uri

```TypeScript
uri?: string
```

URI, which is used with **type** to specify the data type to be processed in the application launch scenario. If **uri** is specified in a Want, the Want will match the specified URI information, including **scheme**, **schemeSpecificPart**, **authority**, and **path**.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase
