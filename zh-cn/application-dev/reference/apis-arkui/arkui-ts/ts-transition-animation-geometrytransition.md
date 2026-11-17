# 组件内隐式共享元素转场 (geometryTransition)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @lxl007-->
<!--Adviser: @ge-yafang-->

在视图切换过程中提供丝滑的上下文传承过渡。通用transition机制提供了opacity、scale等转场效果，geometryTransition通过安排绑定的in/out组件（in指新视图、out指旧视图）的frame、position使得原本独立的transition动画在空间位置上发生联系，将视觉焦点由旧视图位置引导到新视图位置。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 从API version 7开始支持，从API version 10开始生效。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - [geometryTransition](ts-transition-animation-geometrytransition.md)必须配合[animateTo](../arkts-apis-uicontext-uicontext.md#animateto)使用才有动画效果，动效时长、曲线跟随[animateTo](../arkts-apis-uicontext-uicontext.md#animateto)中的配置，不支持[animation](ts-animatorproperty.md)动画。

## geometryTransition

geometryTransition(id: string): T

组件内隐式共享元素转场。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 7

**参数：**

| 参数名  | 类型                 | 必填 | 说明                                                     |
| ------- | ------------------------ | ---- | ------------------------------------------------------------ |
| id      | string                   | 是   | 用于设置绑定关系，id置空字符串清除绑定关系避免参与共享行为，id可更换重新建立绑定关系。同一个id只能有两个组件绑定，且分别作为in（新视图）和out（旧视图）两种不同类型角色，不能多个组件绑定同一个id。绑定同一id的组件不能相互嵌套，即一个绑定了该id的组件内部不能再嵌套另一个绑定了相同id的组件，否则会导致转场动画异常。建议在动画结束回调（[onFinish](ts-explicit-animation.md#animateparam对象说明)）中将绑定的id置空，防止在非预期场景（如页面快速连续点击、状态变量变化等）下误触发共享元素转场，下次触发转场前再将id设置回所需值。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## geometryTransition<sup>11+</sup>

ArkTS-Dyn: geometryTransition(id: string, options?: GeometryTransitionOptions): T

ArkTS-Sta: geometryTransition(id: string | undefined, options?: GeometryTransitionOptions): this

组件内隐式共享元素转场。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                 | 必填 | 说明                                                     |
| ------- | ------------------------ | ---- | ------------------------------------------------------------ |
| id      | ArkTS-Dyn: string<br > ArkTS-Sta: string \| undefined                   | 是   | 用于设置绑定关系，id置空字符串清除绑定关系避免参与共享行为，id可更换重新建立绑定关系。同一个id只能有两个组件绑定，且分别作为in（新视图）和out（旧视图）两种不同类型角色，不能多个组件绑定同一个id。当id的值为undefined时，组件内隐式共享元素转场不生效。绑定同一id的组件不能相互嵌套，即一个绑定了该id的组件内部不能再嵌套另一个绑定了相同id的组件，否则会导致转场动画异常。建议在动画结束回调（[onFinish](ts-explicit-animation.md#animateparam对象说明)）中将绑定的id置空，防止在非预期场景（如页面快速连续点击、状态变量变化等）下误触发共享元素转场，下次触发转场前再将id设置回所需值。 |
| options | [GeometryTransitionOptions](#geometrytransitionoptions11) | 否   | 组件内隐式共享元素转场动画参数，需配合[animateTo](../arkts-apis-uicontext-uicontext.md#animateto)使用才有动画效果。<br>默认值为 { follow: false }。                                    |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: T<br > ArkTS-Sta: this | 返回当前组件。 |

## GeometryTransitionOptions<sup>11+</sup>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明                                                   |
| ------ | -------- | -------- | ---- | ------------------------------------------------------------ |
| follow | boolean  | 否 | 是   | 仅用于if范式下标记始终在组件树上的组件是否跟随做共享动画。true代表跟随做共享动画，false代表不跟随做共享动画。<br/>默认值：false |

## 示例

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State isShow: boolean = false;
  @State geometryId: string = 'picture';

  build() {
    Stack({ alignContent: Alignment.Center }) {
      if (this.isShow) {
        // 图片使用Resource资源，需用户自定义
        Image($r('app.media.pic'))
          .autoResize(false)
          .clip(true)
          .width(300)
          .height(400)
          .offset({ y: 100 })
          .geometryTransition(this.geometryId)
          .transition(TransitionEffect.OPACITY)
          // 在打断场景下，即动画过程中点击页面触发下一次转场，如果不加id，则会出现重影
          // 加了id之后，新建的图片会复用之前的图片节点，不会重新创建节点，也就不会有重影问题
          // 加id的规则为加在if和else下的第一个节点上，有多个并列节点则也需要进行添加
          .id('item1')
      } else {
        // geometryTransition此处绑定的是容器，那么容器内的子组件需设为相对布局跟随父容器变化，
        // 套多层容器为了说明相对布局约束传递
        Column() {
          Column() {
            // 图片使用Resource资源，需用户自定义
            Image($r('app.media.icon'))
              .width('100%').height('100%')
          }.width('100%').height('100%')
        }
        .width(80)
        .height(80)
        // geometryTransition会同步圆角，但仅限于geometryTransition绑定处，此处绑定的是容器
        // 则对容器本身有圆角同步而不会操作容器内部子组件的borderRadius
        .borderRadius(20)
        .clip(true)
        .geometryTransition(this.geometryId)
        // transition保证组件离场不被立即析构，可设置其他转场效果
        .transition(TransitionEffect.OPACITY)
        .id('item2')
      }
    }
    .onClick(() => {
      this.geometryId = 'picture';
      this.getUIContext().animateTo({ duration: 1000, onFinish: () => {
        this.geometryId = '';
      } }, () => {
        this.isShow = !this.isShow;
      });
    })
  }
}
```

![geometrytransition](figures/geometrytransition.gif)
