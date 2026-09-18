# PolicyRules (System API)

Enumerates the profile policy rules.

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## POLICY_RULE_DISABLE_NOT_ALLOWED

```TypeScript
POLICY_RULE_DISABLE_NOT_ALLOWED = 1
```

A profile cannot be disabled after being enabled.

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## POLICY_RULE_DELETE_NOT_ALLOWED

```TypeScript
POLICY_RULE_DELETE_NOT_ALLOWED = 1 << 1
```

The profile cannot be deleted.

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## POLICY_RULE_DISABLE_AND_DELETE

```TypeScript
POLICY_RULE_DISABLE_AND_DELETE = 1 << 2
```

A profile must be deleted immediately after being enabled.

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.
