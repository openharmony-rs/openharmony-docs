# NetworkSearchRealTimeResult (System API)

```TypeScript
export interface NetworkSearchRealTimeResult
```

Indicates the results of manual network scan

**Since:** 23

<!--Device-radio-export interface NetworkSearchRealTimeResult--><!--Device-radio-export interface NetworkSearchRealTimeResult-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## isFinish

```TypeScript
isFinish: boolean
```

Indicates whether the network search was stop.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-NetworkSearchRealTimeResult-isFinish: boolean--><!--Device-NetworkSearchRealTimeResult-isFinish: boolean-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## networkInfos

```TypeScript
networkInfos: Array<NetworkInformation>
```

the network search results.

**Type:** Array&lt;[NetworkInformation](arkts-telephony-radio-networkinformation-i-sys.md)&gt;

**Since:** 23

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-NetworkSearchRealTimeResult-networkInfos: Array<NetworkInformation>--><!--Device-NetworkSearchRealTimeResult-networkInfos: Array<NetworkInformation>-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.
