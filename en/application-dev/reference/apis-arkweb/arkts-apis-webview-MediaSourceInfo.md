# Class (MediaSourceInfo)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhangyao75477-->
<!--Designer: @gzweioh-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5e88740304c5ca66a80c0c55e43d472d9065d48d translatedAt=2026-11-06T11:03:14.035Z pushedAt=2026-11-09T11:17:14.081Z nl=1 -->

MediaSourceInfo is a data class that represents media source information. In web media playback scenarios, the MediaSourceInfo class encapsulates the basic information of a media source, helping applications understand the type, address, and format of the media source. Based on this information, applications can create a custom player and start playback.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The sample effect is subject to the actual device.

## Attributes

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional| Description|
|------|------|------|------|------|
| type<sup>12+</sup> | [SourceType](./arkts-apis-webview-e.md#sourcetype12) | No| No| Type of the media source.|
| source<sup>12+</sup> | string | No| No| Address of the media source.|
| format<sup>12+</sup> | string | No | No | Media source format, which may be empty. The developer needs to determine the format. |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

const mediaInfo: webview.MediaSourceInfo = {
  type: webview.SourceType.URL,
  source: 'https://example.com/video.mp4',
  format: 'mp4'
};
```