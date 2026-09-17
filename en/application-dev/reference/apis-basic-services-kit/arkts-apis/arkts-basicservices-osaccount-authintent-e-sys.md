# AuthIntent (System API)

Enumerates the authentication intents.

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## UNLOCK

```TypeScript
UNLOCK = 1
```

Unlock.

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## SILENT_AUTH

```TypeScript
SILENT_AUTH = 2
```

Silent authentication.

**Since:** 14

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## QUESTION_AUTH

```TypeScript
QUESTION_AUTH = 3
```

Security question authentication.

**Since:** 14

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## ABANDONED_PIN_AUTH

```TypeScript
ABANDONED_PIN_AUTH = 4
```

Abandoned PIN authentication. After a user changes the lock screen password, the old PIN is abandoned. If a user forgets the current password, the user can reset the lock screen password after passing the authentication with the abandoned PIN.

**Since:** 20

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
