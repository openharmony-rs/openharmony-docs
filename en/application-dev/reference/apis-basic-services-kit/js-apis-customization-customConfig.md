# @ohos.customization.customConfig (Custom Configurations)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Customization-->
<!--Owner: @liule_123-->
<!--Designer: @sunshine_1984-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

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

**System capability**: SystemCapability.Customization.CustomConfig

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
