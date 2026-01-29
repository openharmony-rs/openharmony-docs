# SwipeRefresher
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fengluochenai-->
<!--Designer: @YanSanzo-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->


The swipe refresher is a component used to obtain and load content, typically with a pull-down gesture.

> **NOTE**
>
> - This component and its child components are supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> - If the **SwipeRefresher** component has [universal attributes](ts-component-general-attributes.md) and [universal events](ts-component-general-events.md) configured, the compiler toolchain automatically generates an additional **__Common__** node and mounts the universal attributes and universal events on this node rather than the **SwipeRefresher** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **SwipeRefresher** component.


## Modules to Import

```
import { SwipeRefresher } from '@kit.ArkUI';
```


## Child Components

Not supported

## SwipeRefresher

SwipeRefresher ({content?: ResourceStr, isLoading: boolean})

**Decorator**: @Component

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name| Type| Mandatory| Decorator| Description                                                                |
| -------- | -------- | -------- | -------- |--------------------------------------------------------------------|
| content | [ResourceStr](ts-types.md#resourcestr) | No| @Prop | Text displayed when the content is loaded.<br>The default value is an empty string.<br>**NOTE**<br>If the text length exceeds the column width, it will be truncated. The Resource type is supported since API version 20.  |
| isLoading | boolean | Yes| \@Prop | Whether content is being loaded.<br> **true**: Content is being loaded.<br> **false**: Content is not being loaded.|

## Events
The [universal events](ts-component-general-events.md) are not supported.

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
