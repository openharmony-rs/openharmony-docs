# SwipeRefresher
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fengluochenai-->
<!--Designer: @YanSanzo-->
<!--Tester: @tinygreyy-->
<!--Adviser: @HelloCrease-->


内容加载指获取内容并加载出来，常用于衔接展示下拉加载的内容。

> **说明：**
>
> 该组件及其子组件从 API version 10 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> 该组件不支持在Wearable设备上使用。


## 导入模块

```
import { SwipeRefresher } from '@kit.ArkUI';
```


## 子组件

无

## 属性
不支持[通用属性](ts-component-general-attributes.md)。


## SwipeRefresher

SwipeRefresher ({content?: ResourceStr, isLoading: boolean})

**装饰器类型：**\@Component

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 名称 | 类型 | 必填 | 装饰器类型 | 说明                                                                 |
| -------- | -------- | -------- | -------- |--------------------------------------------------------------------|
| content | [ResourceStr](ts-types.md#resourcestr) | 否 | @Prop | 内容加载时显示的文本。<br/>默认值：空字符串。<br/>**说明**：如果文本大于列宽时，文本被截断。从API version 20开始，支持Resource类型。   |
| isLoading | boolean | 是 | \@Prop | 当前是否正在加载。<br> isLoading为true时，表示正在加载。<br> isLoading为false时，表示未在加载。 |

## 事件
不支持[通用事件](ts-component-general-events.md)。

## 示例
展示设置属性content为空字串及不为空、isLoading为true和false的不同加载效果。
```ts
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

![Snipaste_2023-07-24_11-35-40](figures/Snipaste_2023-07-24_11-35-40.gif)
