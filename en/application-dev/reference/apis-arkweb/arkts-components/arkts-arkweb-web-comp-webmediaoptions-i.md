# WebMediaOptions

```TypeScript
declare interface WebMediaOptions
```

Configures the media policy of the **Web** component, including the audio playback continuation validity period, audio exclusive mode, and more. It is suitable for scenarios where audio playback experience optimization and multi- instance audio management are required, improving media playback stability and user experience.

**Since:** 10

**System capability:** SystemCapability.Web.Webview.Core

## audioExclusive

```TypeScript
audioExclusive?: boolean
```

Whether the audio of multiple Web instances in an app is exclusive.

The value **true** means the audio of multiple Web instances in an app is exclusive, and **false** means the opposite.

Default value: **true**.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## audioSessionType

```TypeScript
audioSessionType?: AudioSessionType
```

Web audio type in the app. The default value corresponds to STREAM_USAGE_MUSIC in the system audio stream type [StreamUsage](../../apis-audio-kit/arkts-apis/arkts-audio-audio-streamusage-e.md). Used to change the mapping between the component audio type and the system audio type, affecting the ArkWeb audio focus policy.

**Type:** [AudioSessionType](arkts-arkweb-web-comp-audiosessiontype-e.md)

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## resumeInterval

```TypeScript
resumeInterval?: number
```

Validity period during which Web audio and video paused by other apps can automatically resume playback, in seconds. Value range: [-2147483648, 2147483647]. The value **0** means no automatic resumption; a value greater than **0** means an attempt to resume within the specified period; a value less than **0** means an attempt to resume within an unlimited period. Due to approximation, this validity period may have an error within one second.

**NOTE:** 

After an HLS video is interrupted, it will automatically resume when returning to the foreground, regardless of this time setting.

Default value: **0**.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
