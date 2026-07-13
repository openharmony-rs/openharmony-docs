# 自定义事件拦截
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

为组件提供自定义的事件拦截能力，适用于需要根据事件在控件上按下时的位置、输入源等事件信息动态决定控件HitTestMode属性的场景，用于控制组件的触摸测试和事件响应行为。

>  **说明：**
>
> - 从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。


## onTouchIntercept

onTouchIntercept(callback: Callback\<TouchEvent, HitTestMode\>): T

给组件绑定自定义事件拦截回调。

> **说明：**
>
> 从API version 20开始，该接口支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名        | 类型                    | 必填  | 说明                         |
| ---------- | -------------------------- | ------- | ----------------------------- |
| callback | Callback\<[TouchEvent](ts-universal-events-touch.md#touchevent对象说明), [HitTestMode](ts-appendix-enums.md#hittestmode9)\> | 是 | 自定义事件拦截回调。在做[触摸测试](../../../ui/arkts-interaction-basic-principles.md#触摸测试)时回调此函数。通过返回值设置组件的[HitTestMode](ts-appendix-enums.md#hittestmode9)。使用TouchEvent中的touches属性前，需先校验其是否为空。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## 示例

该示例通过onTouchIntercept修改组件的HitTestMode属性。

```ts
// xxx.ets
@Entry
@Component
struct Index {
  isPolygon(event: TouchEvent) {
    return true;
  }

  build() {
    Row() {
      Column() {
        Text('hello world')
          .backgroundColor(Color.Blue)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            console.info('Text click');
          })
      }
      .width(400)
      .height(300)
      .backgroundColor(Color.Pink)
      .onClick(() => {
        console.info('Column click');
      })
      // 调用onTouchIntercept修改该组件的HitTestMode属性
      .onTouchIntercept((event: TouchEvent) => {
        console.info('OnTouchIntercept + ' + JSON.stringify(event));
        // 使用touches时需要先校验是否为空
        if (event && event.touches) {
          let touches = event.touches;
          for (let i = 0; touches[i] != null; i++) {
            console.info('onTouchIntercept touches:', JSON.stringify(touches[i]));
          }
        }
        // 当满足自定义拦截条件时，返回HitTestMode.None使该组件不参与触摸测试
        if (this.isPolygon(event)) {
          return HitTestMode.None;
        }
        return HitTestMode.Default;
      })
    }
    .width('100%')
  }
}
```
