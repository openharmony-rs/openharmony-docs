# @ohos.arkui.advanced.SwipeRefresherV2

## 导入模块

```TypeScript
import { SwipeRefresherV2 } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [SwipeRefresherV2](arkts-arkui-arkui-advanced-swiperefresherv2-swiperefresherv2-s.md) | SwipeRefresherV2组件用于内容加载，内容加载指获取内容并加载出来，常用于衔接展示下拉加载的内容。 |

## 示例

从API版本26.0.0开始，支持SwipeRefresherV2。如下示例展示SwipeRefresherV2设置参数content为空字符串或不为空、isLoading为true或false时的不同加载效果。

```TypeScript
import { SwipeRefresherV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  build(): void {
    Column() {
      SwipeRefresherV2({
        content: '正在加载中',
        isLoading: true
      })
      SwipeRefresherV2({
        content: '',
        isLoading: true
      })
      SwipeRefresherV2({
        content: '正在加载中',
        isLoading: false
      })
    }
  }
}
```
