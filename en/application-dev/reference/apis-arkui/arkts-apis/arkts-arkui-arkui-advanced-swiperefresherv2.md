# @ohos.arkui.advanced.SwipeRefresherV2

## Modules to Import

```TypeScript
import { SwipeRefresherV2 } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [SwipeRefresherV2](arkts-arkui-arkui-advanced-swiperefresherv2-swiperefresherv2-s.md) | The **SwipeRefresherV2** component is used to implement the pull-to-refresh feature. It supports custom loading prompt text and loading state control, and is suitable for scenarios where pull-to-refresh interaction needs to be implemented on a page. |

## Examples

The SwipeRefresherV2 component is supported since API version 26.0.0. The following example demonstrates different loading effects when the content parameter is set to an empty string or a non-empty string, and isLoading is set to true or false.

```TypeScript
import { SwipeRefresherV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  build(): void {
    Column() {
      SwipeRefresherV2({
        content: 'Loading...',
        isLoading: true
      })
      SwipeRefresherV2({
        content: '',
        isLoading: true
      })
      SwipeRefresherV2({
        content: 'Loading...',
        isLoading: false
      })
    }
  }
}
```
