# @ohos.arkui.advanced.SwipeRefresher

## 导入模块

```TypeScript
import { SwipeRefresher } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [SwipeRefresher](arkts-arkui-arkui-advanced-swiperefresher-swiperefresher-s.md) | 内容加载指获取内容并加载出来，常用于衔接展示下拉加载的内容。 |

## 示例

展示设置属性content为空字符串及不为空、isLoading为true和false的不同加载效果。

```TypeScript
import { SwipeRefresher } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      SwipeRefresher({
        content: '正在加载中',
        isLoading: true
      })
      SwipeRefresher({
        content: '',
        isLoading: true
      })
      SwipeRefresher({
        content: '正在加载中',
        isLoading: false
      })
    }
  }
}
```
