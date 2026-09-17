# AdDisplayOptions

Defines the ad display parameters.

**Since:** 11

**System capability:** SystemCapability.Advertising.Ads

## Modules to Import

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## [key: string]

```TypeScript
[key: string]: number | boolean | string | undefined
```

Custom parameter.

- refreshTime: An optional custom parameter for the AutoAdComponent,  
used to control the ad rotation interval. Type number, unit: ms, value range [30000, 120000]. If not set or the value is non-numeric or less than or equal to 0, no rotation occurs, and only the first ad content in the ad response is displayed. Values less than 30000 are set to 30000, and values greater than 120000 are set to 120000.

&lt;!--RP3--&gt;&lt;!--RP3End--&gt;

**Type:** number &#124; boolean &#124; string &#124; undefined

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## audioFocusType

```TypeScript
audioFocusType?: number
```

Scenario type for obtaining audio focus during video playback.

- 0: Obtain focus during both muted and non-muted video playback.  
- 1: Do not obtain focus during muted video playback.  
- 2: Do not obtain focus during either muted or non-muted video playback.  
- The related features that this API depends on are currently not supported for use,  
so the default value is temporarily uncertain.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## customData

```TypeScript
customData?: string
```

Media custom data. Used for the server to notify the media server that a user should be rewarded for interacting with a rewarded video ad, thereby preventing fraudulent behavior (no notification will be sent if not set).

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## mute

```TypeScript
mute?: boolean
```

Whether to mute the ad video playback.

- true: Mute playback.  
- false: Non-mute playback.

If not set, the business logic prevails.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## useMobileDataReminder

```TypeScript
useMobileDataReminder?: boolean
```

Whether to display a pop-up notification to the user when using mobile data to play videos or download apps.

- true: Display pop-up notification.  
- false: Do not display pop-up notification.  
- This parameter depends on the traffic pop-up feature,  
which currently does not support full functionality, so the default value is temporarily uncertain.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## userId

```TypeScript
userId?: string
```

Media custom user ID. Used for the server to notify the media server that a user should be rewarded for interacting with a rewarded video ad, thereby preventing fraudulent behavior (no notification will be sent if not set).

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads
