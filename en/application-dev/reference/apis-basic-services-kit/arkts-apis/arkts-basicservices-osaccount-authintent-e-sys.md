# AuthIntent (System API)

```TypeScript
enum AuthIntent
```

Enumerates the authentication intents.

**Since:** 12

<!--Device-osAccount-enum AuthIntent--><!--Device-osAccount-enum AuthIntent-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## ABANDONED_PIN_AUTH

```TypeScript
ABANDONED_PIN_AUTH = 4
```

Abandoned PIN authentication. After a user changes the lock screen password, the old PIN is abandoned. If a user forgets the current password, the user can reset the lock screen password after passing the authentication with the abandoned PIN.

**Since:** 20

<!--Device-AuthIntent-ABANDONED_PIN_AUTH = 4--><!--Device-AuthIntent-ABANDONED_PIN_AUTH = 4-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## QUESTION_AUTH

```TypeScript
QUESTION_AUTH = 3
```

Security question authentication.

**Since:** 14

<!--Device-AuthIntent-QUESTION_AUTH = 3--><!--Device-AuthIntent-QUESTION_AUTH = 3-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## SILENT_AUTH

```TypeScript
SILENT_AUTH = 2
```

Silent authentication.

**Since:** 14

<!--Device-AuthIntent-SILENT_AUTH = 2--><!--Device-AuthIntent-SILENT_AUTH = 2-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## UNLOCK

```TypeScript
UNLOCK = 1
```

Unlock.

**Since:** 12

<!--Device-AuthIntent-UNLOCK = 1--><!--Device-AuthIntent-UNLOCK = 1-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
