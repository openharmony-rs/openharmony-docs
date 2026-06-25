# 共享元素转场 (sharedTransition)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

可以通过设置组件的sharedTransition属性将该元素标记为共享元素并设置对应的共享元素转场动效。sharedTransition仅发生在[@ohos.router (页面路由)](../js-apis-router.md)跳转时。

> **说明：**
>
> 从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## sharedTransition

sharedTransition(id: string, options?: sharedTransitionOptions): T

设置共享元素转场动效。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
|      id          |  string         | 是                                         |    两个页面中id值相同且不为空字符串的组件即为共享元素，在页面转场时可显示共享元素转场动效。|
|     options          |  [sharedTransitionOptions](#sharedtransitionoptions)       | 否     |  共享元素转场动画参数。不设置时使用默认转场动画参数。各参数具体默认值参考[sharedTransitionOptions](#sharedtransitionoptions)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
|  T | 返回当前组件。 |

## sharedTransitionOptions

共享元素转场动画参数。

> **说明：**
>
> type为SharedTransitionEffectType.Exchange时motionPath才会生效。
>
> type为SharedTransitionEffectType.Exchange时，效果为对匹配的共享元素产生位置、大小的过渡（可通过配置组件的border观察），不支持内容的过渡效果。例如，Text组件在两个页面上使用不同的fontSize属性值，即绘制内容有大小差异，在sharedTransition动画结束后的最后一帧，Text的fontSize效果会突变为跳转目标页fontSize的效果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称              | 类型      | 只读 |  可选     | 说明                                                     |
| ----------------- | -------------|------- | ------- | --------------------------------------------------------------|
| duration          |     number   |  否  |    是          | 描述共享元素转场动效播放时长。<br>默认值：1000 <br>单位：毫秒<br/>取值范围：[0, +∞) |
| curve             |      [Curve](ts-appendix-enums.md#curve)&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[ICurve](../js-apis-curve.md#icurve9)  | 否 | 是 | 动画曲线。<br/>推荐以Curve或ICurve形式指定。<br/>当类型为string时，为动画插值曲线，取值参考[AnimateParam](./ts-explicit-animation.md#animateparam对象说明)的curve参数。<br/>默认值：Curve.Linear |
| delay          |     number   |  否  |  是         | 延迟播放时间。<br/>取值范围：[0, +∞)<br>默认值：0 <br>单位：毫秒 |
| motionPath          | [MotionPathOptions](./ts-motion-path-animation.md#motionpathoptions)  |  否   |  是        | 运动路径信息。 |
| zIndex          |     number   |  否   |   是           | 设置共享元素在转场动画期间的Z轴堆叠顺序。<br/>取值范围：(-∞, +∞)<br/>默认值：0<br/>数值越大，该共享元素在转场过程中越靠前（显示在上层），越不容易被其他共享元素遮挡。此zIndex仅在共享元素转场动画期间生效，控制共享元素相对于其他同时参与转场的共享元素在Z轴上的堆叠顺序，不参与页面内普通组件的静态布局层级控制（页面内组件的静态布局层级由组件通用属性[zIndex](ts-universal-attributes-z-order.md#zindex)控制）。默认值0表示不额外提升或降低层级，多个未设置zIndex的共享元素之间按系统默认顺序排列。 |
| type           |     [SharedTransitionEffectType](ts-appendix-enums.md#sharedtransitioneffecttype)   |  否  |  是 | 动画类型。<br>默认值：SharedTransitionEffectType.Exchange |


## 示例

  示例代码为点击图片跳转页面时，显示共享元素图片的自定义转场动效。 

```ts
// xxx.ets
@Entry
@Component
struct SharedTransitionExample {

  build() {
    Column() {
      // $r('app.media.ic_health_heart')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.ic_health_heart')).width(50).height(50).margin({ left: 20, top: 20 })
        .sharedTransition('sharedImage', { duration: 800, curve: Curve.Linear, delay: 100 }) 
    }.width('100%').height('100%').alignItems(HorizontalAlign.Start)
    .onClick(() => {
      this.getUIContext().getRouter().pushUrl({ url: 'pages/PageB' })
    })
  }

  pageTransition() {
    PageTransitionEnter({ type: RouteType.None, duration: 0 })
    PageTransitionExit({ type: RouteType.None, duration: 0 })
  }
}
```

```ts
// PageB.ets
@Entry
@Component
struct PageBExample {
  build() {
    Stack() {
      // $r('app.media.ic_health_heart')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.ic_health_heart')).width(150).height(150)
        .sharedTransition('sharedImage', { duration: 800, curve: Curve.Linear, delay: 100 })
    }.width('100%').height('100%')
  }

  pageTransition() {
    PageTransitionEnter({ type: RouteType.None, duration: 0 })
    PageTransitionExit({ type: RouteType.None, duration: 0 })
  }
}
```

![shared](figures/shared.gif)

### 示例2（Text和Button组件的共享元素转场）

该示例演示Text和Button组件作为共享元素时的转场动效。需要注意的是，Text组件在两个页面如果使用了不同的fontSize属性值，sharedTransition动画结束后fontSize效果会突变为目标页的fontSize。

```ts
// xxx.ets
@Entry
@Component
struct SharedTextExample {
  build() {
    Column() {
      Text('Hello World')
        .fontSize(20)
        .fontColor(Color.White)
        .backgroundColor('#317AF7')
        .padding(10)
        .borderRadius(10)
        .margin({ left: 20, top: 20 })
        .sharedTransition('sharedText', { duration: 800, curve: Curve.Linear })
      Button('Click Me')
        .width(100)
        .height(40)
        .margin({ left: 20, top: 20 })
        .sharedTransition('sharedButton', { duration: 800, curve: Curve.Linear })
    }.width('100%').height('100%').alignItems(HorizontalAlign.Start)
    .onClick(() => {
      this.getUIContext().getRouter().pushUrl({ url: 'pages/PageC' })
    })
  }

  pageTransition() {
    PageTransitionEnter({ type: RouteType.None, duration: 0 })
    PageTransitionExit({ type: RouteType.None, duration: 0 })
  }
}
```

```ts
// PageC.ets
@Entry
@Component
struct PageCExample {
  build() {
    Stack() {
      Column() {
        Text('Hello World')
          .fontSize(40)
          .fontColor(Color.White)
          .backgroundColor('#317AF7')
          .padding(20)
          .borderRadius(20)
          .margin({ top: 100 })
          .sharedTransition('sharedText', { duration: 800, curve: Curve.Linear })
        Button('Click Me')
          .width(200)
          .height(60)
          .margin({ top: 50 })
          .sharedTransition('sharedButton', { duration: 800, curve: Curve.Linear })
      }.width('100%').justifyContent(FlexAlign.Start)
    }.width('100%').height('100%')
  }

  pageTransition() {
    PageTransitionEnter({ type: RouteType.None, duration: 0 })
    PageTransitionExit({ type: RouteType.None, duration: 0 })
  }
}
```