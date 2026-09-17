# ConstraintChangeInfo (System API)

Defines the constraint change information.

**Since:** 23

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## constraint

```TypeScript
constraint: string
```

[Constraint](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md) that has been changed.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## isEnabled

```TypeScript
isEnabled: boolean
```

Enabling state of the changed constraint. The default value is **false**.

The value **true** indicates that the target constraint is enabled, and **false** indicates the opposite.

**Type:** boolean

**Since:** 23

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
