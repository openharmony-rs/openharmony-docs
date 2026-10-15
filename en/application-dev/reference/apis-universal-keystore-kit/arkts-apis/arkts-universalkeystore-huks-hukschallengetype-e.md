# HuksChallengeType

```TypeScript
export enum HuksChallengeType
```

Enumerates the types of the challenges generated when a key is used.

**Since:** 9

<!--Device-huks-export enum HuksChallengeType--><!--Device-huks-export enum HuksChallengeType-End-->

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_CHALLENGE_TYPE_CUSTOM

```TypeScript
HUKS_CHALLENGE_TYPE_CUSTOM = 1
```

Custom challenge, which supports only one authentication for multiple keys.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_CUSTOM = 1--><!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_CUSTOM = 1-End-->

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_CHALLENGE_TYPE_NONE

```TypeScript
HUKS_CHALLENGE_TYPE_NONE = 2
```

Challenge is not required.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_NONE = 2--><!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_NONE = 2-End-->

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_CHALLENGE_TYPE_NORMAL

```TypeScript
HUKS_CHALLENGE_TYPE_NORMAL = 0
```

Normal challenge, which is of 32 bytes by default.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_NORMAL = 0--><!--Device-HuksChallengeType-HUKS_CHALLENGE_TYPE_NORMAL = 0-End-->

**System capability:** SystemCapability.Security.Huks.Extension
