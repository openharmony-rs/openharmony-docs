# SwipeRefresher
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @song-song-song-->
<!--Designer: @fenglinbailu-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ac775a54069be1728a015bce61b1790fc26fe1c8 translatedAt=2026-11-03T01:38:30.421Z pushedAt=2026-11-13T01:05:59.881Z nl=1 -->


The swipe refresher is a component used to obtain and load content, typically with a pull-down gesture.

> **NOTE**
>
> - This component and its child components are supported since API version 10. Newly added content in later versions is marked with a superscript to indicate their earliest version.
>
> - The APIs of this module can be used only in the stage model.
>
> - If [universal attributes](ts-component-general-attributes.md) or [universal events](ts-component-general-events.md) are set for **SwipeRefresher**, the compilation toolchain additionally generates a node named **\_\_Common\_\_** and mounts the universal attributes or universal events on **\_\_Common\_\_** instead of directly applying them to **SwipeRefresher** itself. As a result, the universal attributes or universal events set by developers may not take effect or may not behave as expected. Therefore, it is not recommended to set universal attributes and universal events for **SwipeRefresher**.


## Modules to Import

```ts
import { SwipeRefresher } from '@kit.ArkUI';
```

## Child Components

Not supported

## SwipeRefresher

SwipeRefresher({content?: ResourceStr, isLoading: boolean})

Implements the pull-down refresh function. When a user pulls down the page, it triggers a content loading operation, fetching new content from the data source and dynamically displaying it on the page.

**Decorator**: @Component

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Mandatory| Decorator| Description                                                                |
| -------- | -------- | -------- | -------- |--------------------------------------------------------------------|
| content | [ResourceStr](ts-types.md#resourcestr) | No| @Prop | Text displayed when the content is loaded.<br>The default value is an empty string.<br>**NOTE**<br>If the text length exceeds the column width, it will be truncated. The Resource type is supported since API version 20.  |
| isLoading | boolean | Yes | \@Prop | Whether the component is currently loading.<br> true: loading.<br> false: not loading. |

## Example
This example demonstrates how setting the **content** parameter to empty or non-empty strings and toggling the **isLoading** parameter between **true** and **false** affects the loading effect.
```ts
import { SwipeRefresher } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      SwipeRefresher({
        content: 'Loading',
        isLoading: true
      })
      SwipeRefresher({
        content: '',
        isLoading: true
      })
      SwipeRefresher({
        content: 'Loading',
        isLoading: false
      })
    }
  }
}
```

![Snipaste_2023-07-24_11-35-40](figures/Snipaste_2023-07-24_11-35-40.gif)
