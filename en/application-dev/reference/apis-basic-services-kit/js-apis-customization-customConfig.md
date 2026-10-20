# @ohos.customization.customConfig (Custom Configurations)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Customization-->
<!--Owner: @liule_123-->
<!--Designer: @sunshine_1984-->
<!--Tester: @lpw_work-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=6434f4828830bb8b635fa2906368149a83f0a857 translatedAt=2026-10-09T12:15:50.316Z pushedAt=2026-10-10T06:02:05.494Z -->

This module provides APIs for applications to obtain custom configurations, such as channel IDs.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { customConfig } from '@kit.BasicServicesKit';
```

## customConfig.getChannelId

getChannelId(): string

Obtains a pre-installed channel ID of this application.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Customization.CustomConfig

**Return value**

|  Type |  Description |
| ------ | ----- |
| string | Channel ID obtained.|

**Example**

  ```ts
  import { customConfig } from '@kit.BasicServicesKit';

  let channelId: string = customConfig.getChannelId();
  console.info('app channelId is ' + channelId);
  ```
