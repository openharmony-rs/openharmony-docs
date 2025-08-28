# 无障碍悬浮事件

在开启无障碍模式后，Touch事件会转换为无障碍悬浮事件。

>  **说明：**
>
>  - 从API version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>  - 目前仅支持通过开启无障碍模式触发。

## onAccessibilityHover

onAccessibilityHover(callback: AccessibilityCallback): T

开启无障碍模式后，单指触摸绑定该回调的组件时触发该回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名        | 类型                    | 必填  | 说明                          |
| ---------- | -------------------------- | ------- | ----------------------------- |
| callback      | [AccessibilityCallback](#accessibilitycallback) | 是   |  提供开启无障碍模式后的无障碍悬浮回调事件，当开启无障碍模式后，单指触摸绑定该回调的组件时触发该回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## AccessibilityCallback

type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void

提供开启无障碍模式后的无障碍悬浮回调事件类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名              | 类型                                | 必填 | 说明                                                         |
| ------------------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| isHover             | boolean                             | 是   | 表示开启无障碍模式后，手指在组件上触发由Touch事件转换成的无障碍悬浮事件，手指进入时为true，退出时为false。 |
| event | [AccessibilityHoverEvent](#accessibilityhoverevent对象说明) | 是   | 获得AccessibilityHoverEvent对象。                                   |

## AccessibilityHoverEvent对象说明

继承于[BaseEvent](ts-gesture-customize-judge.md#baseevent对象说明8)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称              | 类型       | 必填 | 说明      |
| --------------- | ---------- | ------- | ------- |
| type             | [AccessibilityHoverType](ts-appendix-enums.md#accessibilityhovertype12) | 是 | 无障碍悬浮动作。                |
| x                      | number                         | 是 | 手指位置相对于当前组件左上角的x轴坐标。<br/>单位：vp<br/> |
| y                      | number                         | 是 | 手指位置相对于当前组件左上角的y轴坐标。<br/>单位：vp<br/> |
| windowX                | number                         | 是 | 手指位置相对于应用窗口左上角的x轴坐标。<br/>单位：vp<br/> |
| windowY                | number                         | 是 | 手指位置相对于应用窗口左上角的y轴坐标。<br/>单位：vp<br/> |
| displayX               | number                         | 是 | 手指位置相对于应用屏幕左上角的x轴坐标。<br/>单位：vp<br/> |
| displayY               | number                         | 是 | 手指位置相对于应用屏幕左上角的y轴坐标。<br/>单位：vp<br/> |

## 示例

该示例主要演示通过使用onAccessibilityHover事件，对无障碍模式下的按钮进行设置。

```ts
// xxx.ets
@Entry
@Component
struct OnAccessibilityHoverEventExample {
  @State hoverText: string = 'no hover';
  @State color: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Button(this.hoverText)
        .width(180).height(80)
        .backgroundColor(this.color)
        .onAccessibilityHover((isHover: boolean, event: AccessibilityHoverEvent) => {
          // 通过onAccessibilityHover事件动态修改按钮在是否有鼠标悬浮时的文本内容与背景颜色
          if (isHover) {
            this.hoverText = 'hover';
            this.color = Color.Pink;
          } else {
            this.hoverText = 'no hover';
            this.color = Color.Blue;
          }
        })
    }.padding({ top: 30 }).width('100%')
  }
}
```
