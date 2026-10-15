# SkillUri

```TypeScript
export interface SkillUri
```

URI matched by Want.

**Since:** 12

<!--Device-unnamed-export interface SkillUri--><!--Device-unnamed-export interface SkillUri-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## host

```TypeScript
readonly host: string
```

Host address of the URI. This parameter takes effect only when **scheme** is specified.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SkillUri-readonly host: string--><!--Device-SkillUri-readonly host: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## linkFeature

```TypeScript
readonly linkFeature: string
```

[Feature type](../../../application-models/app-uri-config.md#description-of-linkfeature) provided by the URI. It is used to implement redirection between applications and exists only in **AbilityInfo**.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SkillUri-readonly linkFeature: string--><!--Device-SkillUri-readonly linkFeature: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## maxFileSupported

```TypeScript
readonly maxFileSupported: number
```

Maximum number of files of a specified type that can be received or opened at a time. The value must be an integer greater than or equal to 0.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SkillUri-readonly maxFileSupported: int--><!--Device-SkillUri-readonly maxFileSupported: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## path

```TypeScript
readonly path: string
```

Path of the URI. This parameter takes effect only when both **scheme** and **host** are specified.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SkillUri-readonly path: string--><!--Device-SkillUri-readonly path: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## pathRegex

```TypeScript
readonly pathRegex: string
```

Regular expression of the path of the URI. This parameter takes effect only when both **scheme** and **host** are specified.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SkillUri-readonly pathRegex: string--><!--Device-SkillUri-readonly pathRegex: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## pathStartWith

```TypeScript
readonly pathStartWith: string
```

Prefix of the path of the URI. This parameter takes effect only when both **scheme** and **host** are specified.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SkillUri-readonly pathStartWith: string--><!--Device-SkillUri-readonly pathStartWith: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## port

```TypeScript
readonly port: number
```

Port number of the URI. This parameter takes effect only when both **scheme** and **host** are specified.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SkillUri-readonly port: int--><!--Device-SkillUri-readonly port: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## scheme

```TypeScript
readonly scheme: string
```

Scheme of the URI, such as HTTP, HTTPS, file, and FTP.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SkillUri-readonly scheme: string--><!--Device-SkillUri-readonly scheme: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## type

```TypeScript
readonly type: string
```

Data type that matches the Want, using the MIME (Multipurpose Internet Mail Extensions) type specification and the [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md) type specification.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SkillUri-readonly type: string--><!--Device-SkillUri-readonly type: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## utd

```TypeScript
readonly utd: string
```

Standard data type of the URI that matches Want. This parameter applies to sharing scenarios.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SkillUri-readonly utd: string--><!--Device-SkillUri-readonly utd: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
