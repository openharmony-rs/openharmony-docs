# @ohos.arkui.advanced.SwipeRefresher

## Modules to Import

```TypeScript
import { SwipeRefresher } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [SwipeRefresher](arkts-arkui-arkui-advanced-swiperefresher-swiperefresher-s.md) | The swipe refresher is a component used to obtain and load content, typically with a pull-down gesture. |

## Examples

This example demonstrates how setting the content parameter to empty or non-empty strings and toggling the isLoading parameter between true and false affects the loading effect.

```TypeScript
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
