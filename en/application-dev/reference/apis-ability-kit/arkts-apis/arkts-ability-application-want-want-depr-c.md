# Want

Want is a carrier for information transfer between objects (application components). Want can be used as a parameter of **startAbility** to specify a startup target and information that needs to be carried during startup, for example, **bundleName** and **abilityName**, which respectively indicate the bundle name of the target ability and the ability name in the bundle. When ability A needs to start ability B and transfer some data to ability B, it can use Want a carrier to transfer the data.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [Want/Want](arkts-ability-app-ability-want-want-c.md)

**System capability:** SystemCapability.Ability.AbilityBase

## Modules to Import

```TypeScript
```

## abilityName

```TypeScript
abilityName?: string
```

Name of the ability. If both **bundleName** and **abilityName** are specified in a Want object, the Want object can match a specific ability. The value of **abilityName** must be unique in an application.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [abilityName](arkts-ability-app-ability-want-want-c.md#abilityname)

**System capability:** SystemCapability.Ability.AbilityBase

## action

```TypeScript
action?: string
```

Action to take, such as viewing and sharing application details. In implicit Want, you can define this property and use it together with **uri** or **parameters** to specify the operation to be performed on the data. For details, see [action](arkts-ability-wantconstant-action-depr-e.md#action). For details about the definition and matching rules of implicit Want, see [Matching Rules of Explicit Want and Implicit Want](../../../application-models/explicit-implicit-want-mappings.md).

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [action](arkts-ability-app-ability-want-want-c.md#action)

**System capability:** SystemCapability.Ability.AbilityBase

## bundleName

```TypeScript
bundleName?: string
```

Bundle name.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [bundleName](arkts-ability-app-ability-want-want-c.md#bundlename)

**System capability:** SystemCapability.Ability.AbilityBase

## deviceId

```TypeScript
deviceId?: string
```

ID of the device running the ability. If this field is unspecified, the local device is used.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deviceId](arkts-ability-app-ability-want-want-c.md#deviceid)

**System capability:** SystemCapability.Ability.AbilityBase

## entities

```TypeScript
entities?: Array<string>
```

Additional category information (such as browser and video player) of the ability. It is a supplement to the **action** field for implicit Want. and is used to filter ability types. For details, see [entity](arkts-ability-wantconstant-entity-depr-e.md#entity).

**Type:** Array&lt;string&gt;

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [entities](arkts-ability-app-ability-want-want-c.md#entities)

**System capability:** SystemCapability.Ability.AbilityBase

## flags

```TypeScript
flags?: number
```

How the Want object will be handled. By default, numbers are passed in. For details, see [flags](arkts-ability-wantconstant-flags-depr-e.md#flags).

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [flags](arkts-ability-app-ability-want-want-c.md#flags)

**System capability:** SystemCapability.Ability.AbilityBase

## parameters

```TypeScript
parameters?: { [key: string]: any }
```

Want parameters in the form of custom key-value (KV) pairs. By default, the following keys are carried:

**ohos.aafwk.param.callerPid**: PID of the caller.

**ohos.aafwk.param.callerToken**: token of the caller.

**ohos.aafwk.param.callerUid**: UID in bundleInfo, that is, the application UID in the bundle information.

- **component.startup.newRules**: whether to enable the new control rule.  
- **moduleName**: module name of the caller. No matter what this field is set to, the correct module name will be  
sent to the peer.  
- **ohos.dlp.params.sandbox**: available only for DLP files.

**Type:** { [key: string]: any }

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [parameters](arkts-ability-app-ability-want-want-c.md#parameters)

**System capability:** SystemCapability.Ability.AbilityBase

## type

```TypeScript
type?: string
```

MIME type, that is, the type of the file to open, for example, **'text/xml'** and **'image/*'**. For details about the MIME type definition, see https://www.iana.org/assignments/media-types/media-types.xhtml?utm_source=ld246.com.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [type](arkts-ability-app-ability-want-want-c.md#type)

**System capability:** SystemCapability.Ability.AbilityBase

## uri

```TypeScript
uri?: string
```

URI information to match. If **Uri** is specified in a Want object, the Want object will match the specified URI information, including **scheme**, **schemeSpecificPart**, **authority**, and **path**.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [uri](arkts-ability-app-ability-want-want-c.md#uri)

**System capability:** SystemCapability.Ability.AbilityBase
