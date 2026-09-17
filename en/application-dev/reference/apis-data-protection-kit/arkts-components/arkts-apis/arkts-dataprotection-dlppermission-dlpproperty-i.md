# DLPProperty

Represents the authorization information.

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## actionUponExpiry

```TypeScript
actionUponExpiry?: ActionType
```

Whether the file can be opened after the permission expires (with the editing permission). This parameter is valid only when **expireTime** is not empty. This parameter is left empty by default.

**Type:** [ActionType](arkts-dataprotection-dlppermission-actiontype-e.md)

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## allowedOpenCount

```TypeScript
allowedOpenCount?: number
```

Number of allowed opening times. The default value is **0**. No value range restriction is specified.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## authUserList

```TypeScript
authUserList?: Array<AuthUser>
```

List of users who are authorized to access the DLP file. By default, this parameter is left blank.

**Type:** Array&lt;[AuthUser](arkts-dataprotection-dlppermission-authuser-i.md)&gt;

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## contactAccount

```TypeScript
contactAccount: string
```

Account of the contact. The value contains 1 to 255 bytes. If the value is out of range, error code 401 is thrown.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## countdown

```TypeScript
countdown?: number
```

Validity period for file viewing, in seconds. The default value is 0. After the validity period expires, the file is automatically closed. The value range is [-2&lt;sup&gt;31&lt;/sup&gt;, 2&lt;sup&gt;31&lt;/sup&gt;-1].

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention

## everyoneAccessList

```TypeScript
everyoneAccessList?: Array<DLPFileAccess>
```

Permission granted to everyone. This parameter is left blank by default.

**Type:** Array&lt;[DLPFileAccess](arkts-dataprotection-dlppermission-dlpfileaccess-e.md)&gt;

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## expireTime

```TypeScript
expireTime?: number
```

Timestamp when the file permission has expired. This parameter is left blank by default. The value must be greater than or equal to 0. If the value is out of range, an error code is thrown. Unit: s.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## extensionFields

```TypeScript
extensionFields?: Record<string, Object>
```

Extended attribute of a DLP file. This parameter is left empty by default.

**Type:** Record&lt;string, Object&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention

## fileId

```TypeScript
fileId?: string
```

System account ID. This parameter is left empty by default. The value contains a maximum of 255 bytes. If the value is out of range, error code 401 is thrown.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## offlineAccess

```TypeScript
offlineAccess: boolean
```

Whether the file can be accessed offline. **true**: yes; **false**: no.

**Type:** boolean

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## ownerAccount

```TypeScript
ownerAccount: string
```

Account of the owner who can set the permission. The value contains 1 to 255 bytes. If the value is out of range, error code 401 is thrown.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## ownerAccountID

```TypeScript
ownerAccountID: string
```

Account ID of the owner. The value contains a maximum of 255 bytes. If the value is out of range, error code 401 is thrown.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## ownerAccountType

```TypeScript
ownerAccountType: AccountType
```

Account type of the owner.

**Type:** [AccountType](arkts-dataprotection-dlppermission-accounttype-e.md)

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## waterMarkConfig

```TypeScript
waterMarkConfig?: boolean
```

Whether watermarks are required. **true**: yes; **false**: no. This parameter is left empty by default.

**Type:** boolean

**Since:** 23

**System capability:** SystemCapability.Security.DataLossPrevention
