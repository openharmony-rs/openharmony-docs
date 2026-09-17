# AttestResultInfo (System API)

Device attest result information.

@interface AttestResultInfo

**Since:** 9

**System capability:** SystemCapability.XTS.DeviceAttest

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { deviceAttest } from '@kit.BasicServicesKit';
```

## authResult

```TypeScript
authResult: number
```

Result of the device hardware information authentication.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.XTS.DeviceAttest

**System API:** This is a system API.

## softwareResult

```TypeScript
softwareResult: number
```

Result of the device software information authentication.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.XTS.DeviceAttest

**System API:** This is a system API.

## softwareResultDetail

```TypeScript
softwareResultDetail: Array<number>
```

Software result detail array that includes versionId, patchLevel, rootHash and a reserved space.

**Type:** Array&lt;number&gt;

**Since:** 9

**System capability:** SystemCapability.XTS.DeviceAttest

**System API:** This is a system API.

## ticket

```TypeScript
ticket: string
```

Credential sent from the cloud.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.XTS.DeviceAttest

**System API:** This is a system API.
