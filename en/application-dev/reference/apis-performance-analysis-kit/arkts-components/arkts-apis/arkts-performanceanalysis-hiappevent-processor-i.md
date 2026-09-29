# Processor

```TypeScript
interface Processor
```

Defines a data processor for reporting and managing events. You can customize processor configurations as required.

**Since:** 11

<!--Device-hiAppEvent-interface Processor--><!--Device-hiAppEvent-interface Processor-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## appId

```TypeScript
appId?: string
```

Application ID. It is left empty by default. The length of the input string cannot exceed 8 KB. If the length exceeds 8 KB, the default value is used.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Processor-appId?: string--><!--Device-Processor-appId?: string-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## batchReport

```TypeScript
batchReport?: number
```

Event reporting threshold. When the number of events reaches the threshold, an event is reported. The value must be greater than **0** and less than **1000**. If the value is not within the range, the default value **0** is used and no events are reported.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Processor-batchReport?: int--><!--Device-Processor-batchReport?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## configId

```TypeScript
configId?: number
```

Configuration ID for data processor. The input value must be greater than or equal to **0**. If the input value is less than **0**, the default value 0 is used. If the input value is greater than 0, the value uniquely identifies a data processor with its name.

**Atomic service API**: This parameter can be used in atomic services since API version 12.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Processor-configId?: int--><!--Device-Processor-configId?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## configName

```TypeScript
configName?: string
```

Name of the data processor configuration, which can be loaded from the configuration file. By default, this parameter is left empty. It can contain only letters, digits, underscores (_), and dollar signs ($). It cannot start with a digit and cannot exceed 256 characters.

**Atomic service API**: This parameter can be used in atomic services since API version 20.

**Type:** string

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-Processor-configName?: string--><!--Device-Processor-configName?: string-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## customConfigs

```TypeScript
customConfigs?: Record<string, string>
```

Custom extended parameters. If the input parameter name and value do not meet the specifications, extended parameters are not configured by default. The specifications are as follows:

<br>- A parameter name is a string that contains a maximum of 32 characters, including digits (0 to 9), letters (a to z)(A to Z), underscore (_), and dollar sign ($). It must start with a letter or dollar sign ($) and end with a digit or letter. <br>- A parameter value is a string contains a maximum of 1024 characters. <br>- The number of parameters must be less than 32.

**Atomic service API**: This parameter can be used in atomic services since API version 12.

**Type:** Record&lt;string, string&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Processor-customConfigs?: Record<string, string>--><!--Device-Processor-customConfigs?: Record<string, string>-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## debugMode

```TypeScript
debugMode?: boolean
```

Whether to enable the debug mode. The default value is **false**. The value **true** means to enable the debugging mode, and the value **false** means the opposite.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** boolean

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Processor-debugMode?: boolean--><!--Device-Processor-debugMode?: boolean-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## eventConfigs

```TypeScript
eventConfigs?: AppEventReportConfig[]
```

Event description configuration array that can be reported by the data processor. The default value is an empty array.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** [AppEventReportConfig](arkts-performanceanalysis-hiappevent-appeventreportconfig-i.md)[]

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Processor-eventConfigs?: AppEventReportConfig[]--><!--Device-Processor-eventConfigs?: AppEventReportConfig[]-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## name

```TypeScript
name: string
```

Name of a data processor. The value is string that contains a maximum of 256 characters, including digits (0 to 9), letters (a to z)(A to Z), underscore (_), and dollar sign ($). It must not start with a digit.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Processor-name: string--><!--Device-Processor-name: string-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## onBackgroundReport

```TypeScript
onBackgroundReport?: boolean
```

Whether to report an event when an application switches to the background. The default value is **false**. The value **true** means to report events, and the value **false** means the opposite.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** boolean

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Processor-onBackgroundReport?: boolean--><!--Device-Processor-onBackgroundReport?: boolean-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## onStartReport

```TypeScript
onStartReport?: boolean
```

Whether to report an event when the data processor starts. The default value is **false**. The value **true** means to report events, and the value **false** means the opposite.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** boolean

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Processor-onStartReport?: boolean--><!--Device-Processor-onStartReport?: boolean-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## periodReport

```TypeScript
periodReport?: number
```

Interval for event reporting, in seconds. The input value must be greater than or equal to **0**. If the input value is less than **0**, the default value **0** is used and periodic reporting is not performed.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Processor-periodReport?: int--><!--Device-Processor-periodReport?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## routeInfo

```TypeScript
routeInfo?: string
```

Server location information. It is left empty by default. The length of the input string cannot exceed 8 KB. If the length exceeds 8 KB, the default value is used.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Processor-routeInfo?: string--><!--Device-Processor-routeInfo?: string-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## userIds

```TypeScript
userIds?: string[]
```

Name array of user IDs that can be reported by the data processor. **name** corresponds to the **name** parameter of the [setUserId](arkts-performanceanalysis-hiappevent-setuserid-f.md) API. The default value is an empty array.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** string[]

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Processor-userIds?: string[]--><!--Device-Processor-userIds?: string[]-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## userProperties

```TypeScript
userProperties?: string[]
```

Name array of user properties that can be reported by the data processor. **name** corresponds to the **name** parameter of the [setUserProperty](arkts-performanceanalysis-hiappevent-setuserproperty-f.md) API. The default value is an empty array.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** string[]

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Processor-userProperties?: string[]--><!--Device-Processor-userProperties?: string[]-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
