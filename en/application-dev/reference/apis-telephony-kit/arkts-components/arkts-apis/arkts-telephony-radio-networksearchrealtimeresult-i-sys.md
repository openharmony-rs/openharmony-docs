# NetworkSearchRealTimeResult (System API)

Indicates the results of manual network scan

**Since:** 23

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

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## networkInfos

```TypeScript
networkInfos: Array<NetworkInformation>
```

the network search results.

**Type:** Array&lt;[NetworkInformation](arkts-telephony-radio-networkinformation-i-sys.md)&gt;

**Since:** 23

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.
